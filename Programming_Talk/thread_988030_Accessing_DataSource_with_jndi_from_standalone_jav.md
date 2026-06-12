---
title: "Accessing DataSource with jndi from standalone java app"
date: 2008-11-20
forum: Programming Talk
---

### Post by ufis on 2008-11-20
I am trying to access a (websphere) DataSource from a standalone java application via jndi.

I have a url for the datasource: jndi://someserver:12345/path/to/datasource

All examples point to code similar to this:
[PHP]Context ctx = new InitialContext();
DataSource ds = (DataSource) ctx.lookup("jndi://someserver:12345/path/to/datasource");[/PHP]

But I get the exception: javax.naming.NoInitialContextException when doing ctx.lookup()

From scratching around it looks like this is caused by a ClassNotFoundException, looking for com.sun.jndi.url.jndi.jndiURLContextFactory.

After some reading I found that java (I am using sun 1.6) does not have a jndiURLContextFactory to enable it to handle the jndi:// address. It has context factories for ldap and corba and some others, but no jndi.

Google for jndiURLContextFactory brings up an Apache project that seems to dormant with no source in their svn repository for this.

So I am lost. Am I even on the right path? 

I need to access this DataSource from a standalone java app (run with java -jar Myjar.jar). In fact I need to access a couple DataSources from this app.

What do I need from the server side (other than the url)?
What do I need to do on my side?

---

### Post by ufis on 2008-11-27
Anyone with any idea on how to access a DataSource / EJB running on a WebSphere Application Server from a client running Sun's java?

So far I have:
[PHP]Properties env = new Properties();
env.put(Context.INITIAL_CONTEXT_FACTORY, "com.ibm.websphere.naming.WsnInitialContextFactory");
env.put(Context.PROVIDER_URL, "iiop://someserver:1234");
env.put("org.omg.CORBA.ORBClass", "com.ibm.CORBA.iiop.ORB");

Context ctx = new InitialContext("path/to/the/ejb");
	
Object o = ctx.lookup(ejbURL);[/PHP]
With this I have added multiple jars from the WAS installation to my classpath, one at a time to fix whetever the current Exception was I was getting.
But this seems to be a never ending process.

The latest is 
```
javax.naming.NamingException: Failed to initialize the ORB [Root exception is org.omg.CORBA.INITIALIZE: can't instantiate default ORB implementation com.ibm.CORBA.iiop.ORB  vmcid: 0x0  minor code: 0  completed: No]
.
.
.
Caused by: org.omg.CORBA.INITIALIZE: can't instantiate default ORB implementation com.ibm.CORBA.iiop.ORB  vmcid: 0x0  minor code: 0  completed: No
.
.
.
Caused by: java.lang.UnsatisfiedLinkError: com.ibm.jvm.ExtendedSystem.registerNatives()V
```

Anyone knows? Any ideas?

---

