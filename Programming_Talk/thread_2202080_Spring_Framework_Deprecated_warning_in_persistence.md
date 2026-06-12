---
title: "Spring Framework: Deprecated warning in persistence.xml"
date: 2014-01-27
forum: Programming Talk
---

### Post by zobayer1 on 2014-01-27
I am fairly new in spring framework, I am trying to use hibernate over jpa2 for mysql database server.
Here is my [persistence.xml]("http://pastebin.com/MB70LtPU") file, and, here is my [pom.xml]("http://pastebin.com/ESGmbK6L") file incase you need to check the version numbers of the dependencies.

IDE issues a deprecated warning in this line of persistence.xml:
[HTML]
<provider>org.hibernate.ejb.HibernatePersistence</provider>
[/HTML]

I have done a little google, and seems like it has something to with the api versions, or ide's warning system. I am not sure how to fix the issue. Well, it may not cause a big problem at this moment, but what should be the correct way of doing this?

I am using Intellij-IDEA 13 as my IDE. App Server: Oracle Weblogic server 12c. 
Thanks in advance.

---

### Post by hooflung64 on 2014-02-23
You do not need to use the persistence.xml in spring if you are doing a local JPA container. You can do it all programatically and more importantly you can use Spring's Javaconfig method over the old-school xml configurations.

```

@Configuration
@ComponentScan({ "com.app.zobayer1" })
public class JpaConfig {

public static final DEFAULT_ENTITY_PACKAGE = "com.app.zobayer1.bo";

@Bean
public DataSource dataSource() throws Exception {
...
}

@Bean
protected HibernateJpaVendorAdapter vendorAdapter() {
	HibernateJpaVendorAdapter adpt = new HibernateJpaVendorAdapter();
	adpt.setDatabase(Database.ORACLE);
	adpt.setShowSql(false);
	adpt.setDatabasePlatform("org.hibernate.dialect.Oracle10gDialect");

	return adpt;
}

@Bean
protected LocalContainerEntityManagerFactoryBean localEntityFactory()
	throws Exception {
	Properties props = new Properties();
	props.put("hibernate.connection.release_mode", "after_transaction");
		
	try {
		LocalContainerEntityManagerFactoryBean factory = new LocalContainerEntityManagerFactoryBean();
		factory.setDataSource(dataSource());
		factory.setPersistenceUnitName("zobayer1");
		factory.setJpaVendorAdapter(vendorAdapter());
		factory.setPackagesToScan(DEFAULT_ENTITY_PACKAGE);
		factory.setJpaProperties(props);
		factory.afterPropertiesSet();
		//factory.setLoadTimeWeaver(new InstrumentationLoadTimeWeaver()); //required for EclipseLink

		return factory;
	} catch (Exception e) {
                e.printStackTrace();
		throw e;
	}
}

@Bean
public PlatformTransactionManager txManager() throws Exception {
	try {
		return new JpaTransactionManager(localEntityFactory().getObject());
	} catch (Exception e) {
		e.printStackTrace();
		throw e;
	}
}

}

```

Now just make classes that will be component scanned (reside in package com.app.zobayer1 ) with a @Repository

```


@Repository
public abstract class AbstractDAO {

	@PersistenceContext(unitName = "zobayer1")
	protected EntityManager em;

	public EntityManager getEm() {
		return em;
	}

	public void setEm(EntityManager em) {
		this.em = em;
	}
}


```

Remember to implement an interface for all your concrete dao's ( and to also annotate them with @Repository) because you are in Spring where Beans are actually proxies.

You can then use Entity Beans to your hearts content. You can even get funky and have @Compnent services with true models that will have the dao's injected in them and use something like [Dozer]("http://dozer.sourceforge.net/") to map bo's to entities if you want to have a separation between JPA entities and actual models. You will also be able to use @Transactional and get Springs transaction manager to handle rollbacks etc. 

Ofc. there other considerations to think about if you need a remote JTA manager instead of the one built into Spring, like if you are deploying the app into Weblogic or Jboss and the JPA layer is something like an OSGI component.

---

### Post by zobayer1 on 2014-02-23
Thanks so much for such elaborate answer. I am new to spring framework. Will surely try this. XML based config is also a bit tedious job to do. Java based config seems much more natural. Thanks again :)

---

