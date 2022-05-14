# spring-boot-fullstack-tests

# Utilizar Junit 5:
	http://junit.org/junit5/
	https://junit.org/junit5/docs/current/user-guide/

1.1. What is JUnit 5?
Unlike previous versions of JUnit, JUnit 5 is composed of several different modules from three different sub-projects.
JUnit 5 = JUnit Platform + JUnit Jupiter + JUnit Vintage

De <https://junit.org/junit5/docs/current/user-guide/> 


Assertj:
	http://assertj.github.io/doc/
	

	1. Para os testes relacionado com banco de dados, não utilizar o banco de dados atual e sim o H2
		a. O H2 eh um banco de dados para armazenamento em memoria
			i. http://h2database.com/html/main.html
		b. Para configurar o H2 no projeto, adicionar a seguinte dependencia:
			<dependency>
				<groupId>com.h2database</groupId>
				<artifactId>h2</artifactId>
				<scope>test</scope>
			</dependency>
	2. Configurar o database sob a estrutura 
		a. src/test/resource/application.properties
			spring.datasource.url=jdbc:h2://mem:db;DB_CLOSE_DELAY=-1
			spring.datasource.username=sa
			spring.datasource.password=sa
			spring.datasource.drive-class-name=org.h2.Driver
			spring.jpa.hibernate.ddl-auto=create-drop
			spring.jpa.show-sql=true
			spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
			spring.jpa.properties.hibernate.format_sql=true
	3. Adicionar a anotacao @DataJpaTest na classe test para iniciar os repositorios
	4. Para utilizar o Mokito, utilizar 1 das duas opcoes abaixo:
		a. autoCloseable = MockitoAnnotations.openMocks(this); and autoCloseable.close();
			i. Ou
		b. @ExtendWith(MockitoExtension.class
![image](https://user-images.githubusercontent.com/55097333/168404076-6fab34d2-bb85-481a-9273-9533b65a4f6f.png)
