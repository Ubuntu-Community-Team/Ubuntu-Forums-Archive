---
title: "Eclipselink and HSQL"
date: 2011-01-21
forum: Programming Talk
---

### Post by pcman312 on 2011-01-21
I've made a JUnit testing framework that is using J2EE with eclipselink and embedded in-memory HSQL. The basic idea is this: Create an entity manager (outside of a bean), get it to automatically create the table structure in the HSQL database, then run JUnit tests with that entity manager on the tables in memory. I've got it working pretty well, but periodically it comes up with two errors that I think are unrelated. These errors happen sporadically and don't appear to have any pattern to them:

1) The tables aren't always created when I get the entity manager for the first time. The code is as follows (simplified but the important parts are there):
```
EntityManagerFactory factory = Persistence.createEntityManagerFactory("[persistenceName]");
EntityManager em = factory.createEntityManager(); // Here is where it's suppose to create the tables, and sometimes does
EntityTransaction tx = em.getTransaction();
tx.begin();
// Unit test runs here - this will be where it fails because no tables exist to run queries on
em.flush();
tx.commit();
```

2) The one dummy test that I have set up is suppose to go and create a Company object and save it to the database, then retrieve it and make sure all the values were saved properly. This occasionally fails with the following error:
```
java.lang.IllegalArgumentException: Object: com.innoprise.payroll.general.Company@61578aab is not a known entity type.
```
The persistence.xml file is set up correctly with the <class> tags and the Company one does exist in the file.

Any help that anyone can give would be greatly appreciated.

---

### Post by pcman312 on 2011-01-22
While I haven't found a solution, I did find a workaround for it:

```
EntityManagerFactory factory;
EntityManager em;
int numTries = 10;
for (int i = 0; i < numTries; i++)
{
	factory = Persistence.createEntityManagerFactory("[persistenceName]");
	em = factory.createEntityManager();

	if (tablesCreated()) // Checks if the number of tables > 0
		break;
}
assertTablesCreated(); // Uses the junit Assert class to assert that the tables exist. If they don't, it will fail before it even starts running the test

EntityTransaction tx = em.getTransaction();
tx.begin();
// Unit test runs here
em.flush();
tx.commit();
```

If at first you don't succeed, try and try again.

---

