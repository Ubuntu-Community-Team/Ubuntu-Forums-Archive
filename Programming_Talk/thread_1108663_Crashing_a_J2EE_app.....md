---
title: "Crashing a J2EE app...."
date: 2009-03-27
forum: Programming Talk
---

### Post by andrew222 on 2009-03-27
I would like to know from your experiences.... what are some of the things that can make a J2EE applications crash?

---

### Post by myrtle1908 on 2009-03-28
By "crash" do you mean bring the JEE container down?  For example, cause Tomcat to crash and cease to run/accept connections?  If so, the most common cause of this IMO is OutOfMemory exceptions where the allocated heap size is exceeded.

If you are talking about runtime errors then NullPointerException's are common but these typically won't kill the container.

---

### Post by andrew222 on 2009-03-29
I should have been more specific, what I meant was crashing the container.

In heap size, how would the following play in the application's memory footprint?:

--HttpSession object storing large result sets... 

--Entity Beans with a whole db row persisted in memory and also being activated/passivated.

--EJB pool size, too low, too high...

--Poor load balancing...

--Many users at a time accessing resources

---

### Post by slavik on 2009-03-29
Crappy code ...

---

### Post by txcrackers on 2009-03-29
Integrating with third-party apps/libraries through JNI is always bad.

Most of the things you listed are common issues and are typically adjusted (e.g. the EJB pool) through the application container or other configurations. There are no hard-and-fast rules on these settings or parameters, nor is there necessarily a broadly acceptable strategy. You have to adjust things as you get data on load and usage. Usually, senior personnel have an inkling of where things are headed and can project a bit and make a good guess as to where to set things initially.

Except for the notion of keeping large amounts of data in an HTTP session. **That** approach will kill you.

If your application is dealing with large amounts of data *and* a moderate or greater user base (simultaneous users), and you keep each user's session loaded up with large amounts of data, then you *will* exhaust the available memory. From there, it depends on how the JVM and container manage it. Most will just die (JVM runs, but the container is completely lost) quietly.

If your application is dealing with large amounts of data for each user, you'll want to employ a caching strategy just for the data, such as using EJB EntityBeans or something like Hibernate/Ehcache.

---

### Post by andrew222 on 2009-03-29
Thank you for the reply txcrackers.

Would storing data in an Entity Bean be more expensive than storing data in application scope on the web tier because Entity Beans have to be activated/passivated and that would block transaction throughput?

---

### Post by txcrackers on 2009-03-30
I've always subscribed to keeping data in the data tier and only "using" it in the presentation tier. Mostly because if it changes in the data tier, there's a whole mess of synchronization that has to occur to ensure that the rest of the web tier is up to date. You're then essentially trying to store data and keep it fresh in **three** different locations: data storage, data-tier cluster, and finally web-tier sessions.

Also, from what I recall, the replication of a web-tier application context is not usually as highly optimized as data-tier clustering.

Fetching data from a separate data-tier is almost always easier, "just as fast," and simpler - which reduces application fragility (KISS).

---

### Post by jespdj on 2009-03-30
Calling System.exit(0); might stop the Java EE server and is a big no-no in Java EE applications.

---

### Post by andrew222 on 2009-03-31
I put System.exit(0) in a scriptlet in the JSP welcome page and I deployed the application and watched the WL server terminal disappear and the the page had a "page not found error.  I had to restart the server....

It works ;-)  So whenever we get this for an interview question, I guess this is a good quick answer...along with shoehorning large result sets in a session object...

---

