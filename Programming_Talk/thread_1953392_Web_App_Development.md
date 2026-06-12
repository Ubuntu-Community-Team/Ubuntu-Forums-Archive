---
title: "Web App Development?"
date: 2012-04-06
forum: Programming Talk
---

### Post by fallenshadow on 2012-04-06
Hi guys/gals,

Recently I have been getting into developing web apps and I am having trouble understanding all of it. Im using Spring, Hibernate and Primefaces.

So I can understand there are 3 main parts:

Service class

ManagedBean class

Object class

However I need an explanation on how they are supposed to work together. I also want to know how to pass a variable in code onto a webpage.

---

### Post by r-senior on 2012-04-06
Such a simple question ... but an answer that could go on for many pages.

A web project based on Spring, Hibernate and JSF is usually considered to have three tiers:

**1. Presentation**

These are the parts of the application that deal with the web interface. They should have no business logic or persistence (database) logic. In your case, JSF/Primefaces will provide the bulk of the presentation tier. You may also have static HTML pages, CSS, images, Javascript, etc.

JSF has a concept of a ManagedBean which holds data for the presentation tier. These are used to feed HTML pages with data and to capture submitted data, e.g. from an HTML form, to be passed to the business tier.

You may see Model-View-Controller (MVC) referred to in the context of web applications. JSF/Primefaces will act as the controller and view, with the model being provided by the business and integration tiers discussed below. 

**2. Business**

The parts of the application that provide business logic. In an application that just deals with data input and presentation, this can be a very thin layer. 

The business tier components are typically transactional, i.e. they combine operations on the integration tier into units of work. These units of work must succeed or fail in their entirety. In a financial application, making a payment would be an example of that: debit customer account and credit sales account.

Spring will define the relationship between business-tier and integration-tier components and can also define how transactions should work. It also exposes the API provided by the business tier to the presentation tier. These are sometimes called Service classes, other times you will hear them referred to as Business Facade classes.
[B]
3. Integration[/B]

Components in the integration tier deal with updating databases (and other types of persistent resource, e.g. message queues to other systems).

The database aspect of this is handled by Hibernate and coordinated by Spring. The business tier transactions make use of relatively low-level operations provided by the integration tier. For example, find a customer by name, update the balance of an account. These integration-tier components are often encapsulated as Data Access Objects (DAOs).

Hibernate allows you to work with objects rather than SQL directly. Perhaps this is what you mean by Object classes, I'm not sure. These persistent objects don't belong to any tier really, you'll find them in all tiers as data moves between the database and browser.

> I also want to know how to pass a variable in code onto a webpage.
This is where the JSF managed beans come into play. Your presentation tier will have components that generate HTML (usually Facelets with JSF, but often JSP with other frameworks). These components are bound to properties of your managed beans using special markup tags. To get a value to display on a web page, you set the property in the managed bean and JSF does the rest.

There's a little setup to do before you get to that stage though. ;)

If it all sounds over-complicated, it's because this sort of architecture isn't really for casual web applications. It's for enterprise-scale applications with complex transactional and database requirements, perhaps with multiple configurations and deployments.

---

### Post by codemaniac on 2012-04-06
r-senior I have always enjoyed your posts , awesome explanation .

---

### Post by fallenshadow on 2012-04-08
Thanks for the explaination, its was nice and detailed. However, I still think I have much to learn about the individual technologies before I can make what I need.

---

### Post by r-senior on 2012-04-09
You hit the nail on the head. Each component in an enterprise web application built with Spring/Hibernate is actually quite simple, but there are lots of them:

(X)HTML, CSS, Javascript, Servlets/JSP, JSF, configuring web application servers, e.g. Tomcat/Glassfish, web application authentication, Java, JUnit, Maven, mock objects, Spring bean factory, AOP, security, transactions, annotations, Hibernate, HQL, database design, database configuration, connection pools/JDNI.

Probably the best route into all of this is to start with servlets accessing a database with JDBC. Then bring JSP pages into it. Then start using Spring to orchestrate the business and integration tiers. Then replace the back end with Spring template DAOs, then Hibernate. Then replace the presentation tier with a framework like JSF.

Spring/Hibernate makes development easier, but the grounding in basic servlet/JSP programming with JDBC is important.

---

### Post by Some Penguin on 2012-04-09
I used to use servlets + JSPs w/n Tomcat containers, but moved away from them towards JAX-RS/Jersey resources served by embedded Jetty servers for reasons of maintainability, unit testing and isolation.  Combine with the Guice dependency-injection framework for more ease of use. 

It's very nifty to be able to write something like

```

@Produces({MediaType.APPLICATION_JSON})
@Path("/foo")
public FooResource {
   @Path("/bar")   // served by /foo/bar
   @GET
   // List<String> automatically serialized to JSON
   public List<String> handleBar(@QueryParam("blah") String blah) {
      ....
   }
}

```

i.e. a lot of glue that you might otherwise take more lines of code gets specified by annotations instead, or in Guice bindings (like binding custom serializers, if you need to.  I prefer using the Jackson JSON-handling stuff for this.)

---

### Post by fallenshadow on 2012-04-10
I have multiple errors all relating to the same problem. o.O

> Error creating bean with name 'sessionFactory' defined in ServletContext resource [/WEB-INF/application-context.xml]: Invocation of init method failed; nested exception is java.io.FileNotFoundException: class path resource [resources/hibernate-config.xml] cannot be opened because it does not exist

> class path resource [resources/hibernate-config.xml] cannot be opened because it does not exist

However it does exist, I can see it right in front of me, yet eclipse doesn't see it. I have it located in my WEB-INF folder.

---

### Post by r-senior on 2012-04-10
Just because you can see it, doesn't mean Java can. It won't find it in your WEB-INF directory.

Are you using Maven or did you create a resources directory yourself?

---

### Post by fallenshadow on 2012-04-10
Yes I am using Maven. I have tried both:

<property name="mappingResources" value="resources/hibernate-config.xml" />

and...

<property name="mappingResources" value="WEB-INF/hibernate-config.xml" />

---

### Post by r-senior on 2012-04-10
OK, good. Resources like XML files go into src/main/resources and Maven copies them to the target/classes directory, i.e. they end up in the classpath.

If you put the file in src/main/resources that will be at the root of the classpath, i.e. the default package. So no prefixes required in your property declaration:

```
<property name="mappingResources" value="hibernate-config.xml"/>
```

What does the rest of that Hibernate declaration look like in your Spring config file?

---

### Post by fallenshadow on 2012-04-10
Ok I will do what you said and see what happens! :)

```
	<bean id="sessionFactory" class="org.springframework.orm.hibernate3.LocalSessionFactoryBean">
		<property name="dataSource"><ref local="dataSource"/></property>
		<property name="mappingResources" value="hibernate-config.xml" />
		<property name="hibernateProperties">
			<props>
				<prop key="hibernate.dialect">${jdbc.hibernate.dialect}</prop>
				<prop key="hibernate.show_sql">true</prop>
                <prop key="hibernate.hbm2ddl.auto">update</prop>
			</props>
		</property>
	</bean>
```

Yeah all those errors are gone now. Should it just be the hibernate-config.xml inside this resources folder, or should other config files be in there?

---

### Post by r-senior on 2012-04-10
Your Spring config file is probably in there too. There might be others, such as log4j.xml if you configure logging with log4j or slf4j. But that's about it really.

---

### Post by fallenshadow on 2012-04-11
Did anyone ever get this insane error while trying to develop a web application? o.O

```

WARNING: Exception thrown from LifecycleProcessor on context close
java.lang.IllegalStateException: LifecycleProcessor not initialized - call 'refresh' before invoking lifecycle methods via the context: Root WebApplicationContext: startup date [Wed Apr 11 10:07:59 BST 2012]; root of context hierarchy
	at org.springframework.context.support.AbstractApplicationContext.getLifecycleProcessor(AbstractApplicationContext.java:350)
	at org.springframework.context.support.AbstractApplicationContext.doClose(AbstractApplicationContext.java:1033)
	at org.springframework.context.support.AbstractApplicationContext.close(AbstractApplicationContext.java:988)
	at org.springframework.web.context.ContextLoader.closeWebApplicationContext(ContextLoader.java:556)
	at org.springframework.web.context.ContextLoaderListener.contextDestroyed(ContextLoaderListener.java:142)
	at org.apache.catalina.core.StandardContext.listenerStop(StandardContext.java:4763)
	at org.apache.catalina.core.StandardContext$4.run(StandardContext.java:5473)
	at java.lang.Thread.run(Unknown Source)

```

I haven't a clue where to even start fixing this!

---

### Post by fallenshadow on 2012-04-11
Never mind I got it sorted... just had to figure out that certain libraries have incorrect versions that cause all kinds of problems.

---

### Post by fallenshadow on 2012-04-11
Which part of a web application is responsible for getting the data into a database?

Spring? Hibernate? 

both?

I have the variables as values in a table but both are null... meaning the actual data is not getting transferred

---

### Post by r-senior on 2012-04-11
Hibernate deals with the database. It provides a bridge between Java objects and SQL. It can be used standalone but you are providing the setup of Hibernate using Spring.

That's what your sessionFactory (LocalSessionFactoryBean) is. Notice that it's a class in a *Spring* package. This is a class provided by Spring that makes it easier to set up a Hibernate SessionFactory. The sessionFactory has a dataSource property that references a data source bean in your Spring config. The data source provides the connection to the database, typically via a connection pool.

The common approach is to create data-access-object (DAO) classes that use Spring templates. These are linked into the sessionFactory. I'm on my laptop at the moment and my Java code isn't here but I'll dig out an example of a Spring/Hibernate DAO.

The train of dependencies looks like this:

dao -> sessionFactory -> dataSource

---

### Post by r-senior on 2012-04-11
OK, here's a cut-down Spring DAO using a template (there are other ways to do this but stick with this for the time being):

```
...

@Transactional(propagation=Propagation.MANDATORY)
public class [COLOR="Blue"]ProjectDAOImpl[/COLOR] implements ProjectDAO {

        private SessionFactory [COLOR="Green"]sessionFactory[/COLOR];
        
        public Project findProjectById(long id) {
                return (Project)sessionFactory.getCurrentSession().get(Project.class, id);
        }
        
        public Project createProject(Project project) {
                sessionFactory.getCurrentSession().save(project);
                return project;
        }

        @Required @Resource
        public void setSessionFactory(SessionFactory sessionFactory) {
                this.sessionFactory = sessionFactory;
        }

...

```

The Spring config that goes with it looks like this:

```
...

<!-- Integration Tier: Hibernate -->
<bean id="[COLOR="Green"]sessionFactory[/COLOR]"
        class="org.springframework.orm.hibernate3.LocalSessionFactoryBean">
        <property name="dataSource" ref="dataSource" />
        <property name="configLocation" value="classpath:hibernate.cfg.xml" />
        <property name="configurationClass" value="org.hibernate.cfg.AnnotationConfiguration" />
</bean>

<bean id="projectDAO" class="com.milldam.tickets.model.integration.hibernate.[COLOR="Blue"]ProjectDAOImpl[/COLOR]"/>

...

```

So the sessionFactory and DAO are both defined as Spring beans. The @Resource annotation injects the sessionFactory into the DAO so that the DAO can create Hibernate Session objects to interact with the database. The session factory has a reference to a dataSource, which gives it the database connection.

The elegance of this only becomes apparent when:

a. You try to write DAOs from scratch and see how much code there is
b. You add a transaction manager to seamlessly manage transations across multiple DAOs

Obviously there's all the Hibernate setup of @Entity objects and the hibernate.cfg.xml that I'm not showing here. The important part is the train of dependencies:

dao -> sessionFactory -> dataSource

---

### Post by fallenshadow on 2012-04-11
Im not sure if you got my message but this line is causing trouble:

> @Transactional(propagation=Propagation.MANDATORY)

Propagation is underlined in red with the only option to rename it.

---

### Post by r-senior on 2012-04-11
You can delete it until you get to the point of setting up transactions.

---

### Post by fallenshadow on 2012-04-18
Thanks for all the help r-senior! I did make alot of progress in learning some required things for this. Although I don't know enough to be comfortable yet.

For now I will put this on the back-burner and get onto it at a later stage. :)

---

