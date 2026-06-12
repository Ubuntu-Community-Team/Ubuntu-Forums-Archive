---
title: "Tomcat 6 &amp; Postgresql NIGHTMARE!"
date: 2008-05-21
forum: Programming Talk
---

### Post by thursgun on 2008-05-21
I've tried almost everything.

I just can't make a simple jsp file connect to a postgresql database through tomcat 6.

web.xml , server.xml, bla bla bla.

I've modified a lot (always backing up), but no success at all.

How can i do this.

Please help!. Feel free to post tutorials or guides, but probably I already saw them.

Thanks in advance!

---

### Post by johnl on 2008-05-21
The problem is most likely with your java security policy.

You will need to make some changes to the file /etc/tomcat6/policy.d/04webapps.policy (assuming that your tomcat files are in /etc/tomcat6)
Backup the file before messing with it, because if you mess it up (bad syntax, etc) tomcat will not start.

You can either try to find the correct permissions, or grant all permissions.

To grant all permissions, add the following to the beginning of the file:

```
grant {
   permission java.security.AllPermission;
}
```


If you don't want to do that, you might try something like:

```
grant {
   permission java.net.SocketPermission "address.of.your.postgres.server.com","resolve,connect"; 
}
```

Also, check your tomcat log file -- if a security permission is causing the webapp to fail, it should show you what permission you need.

Hope this helps!

---

### Post by thursgun on 2008-05-21
Thank you johnl for replying. 

No, im afraid is not that, :(


All I did was:

Save my .jsp file in tomcat/webapps/myfiles

Maybe I need a WEB-INF folder inside "myfiles" folder. But, what should be inside of it? a web.xml or a context.xml or both? And then, what web.xml or whatever.xml should content?

I'm very confused, beacuse then, we have the web.xml and context.xml inside tomcat/conf folder.

Which one should I modify?


Thanks for any help.

---

### Post by thursgun on 2008-05-22
nvm I got it. I'll make blog explaining this for future generations ;) I promise I'll post it here.

---

### Post by librano on 2009-04-18
Did you make that blog? I also can't get tomcat to connect to postgresql.

---

### Post by alperguclu on 2009-05-27
Actually johnl's answer completely true.
edit this file
/etc/tomcat6/policy.d/04webapps.policy
add this line in the grant block
permission java.net.SocketPermission "IP address or name of your postgresql server","resolve,connect";

---

### Post by chf on 2009-06-03
hello,

@thursgun: did you make that blog? i also have the problem and i searched a lot but i did not foun the appropriate solution. i tried to turn of the security manager, i granted more permission, but it does not work. in my log i get the following exception```
Jun 3, 2009 10:12:33 PM org.apache.catalina.core.ApplicationContext log
SEVERE: Exception while dispatching incoming RPC call
com.google.gwt.user.server.rpc.UnexpectedException: Service method 'public abstract java.lang.String com.example.servertodatabase.client.GreetingService.countUser()' threw an unexpected exception: java.security.AccessControlException: access denied (java.lang.RuntimePermission exitVM.1)
	at com.google.gwt.user.server.rpc.RPC.encodeResponseForFailure(RPC.java:360)
	at com.google.gwt.user.server.rpc.RPC.invokeAndEncodeResponse(RPC.java:546)
	at com.google.gwt.user.server.rpc.RemoteServiceServlet.processCall(RemoteServiceServlet.java:166)
	at com.google.gwt.user.server.rpc.RemoteServiceServlet.doPost(RemoteServiceServlet.java:86)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:637)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:244)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAsPrivileged(Subject.java:537)
	at org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:276)
	at org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:162)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:283)
	at org.apache.catalina.core.ApplicationFilterChain.access$000(ApplicationFilterChain.java:56)
	at org.apache.catalina.core.ApplicationFilterChain$1.run(ApplicationFilterChain.java:189)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:185)
	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:233)
	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:191)
	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:128)
	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:109)
	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
	at org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:845)
	at org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11Protocol.java:583)
	at org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:447)
	at java.lang.Thread.run(Thread.java:636)
Caused by: java.security.AccessControlException: access denied (java.lang.RuntimePermission exitVM.1)
	at java.security.AccessControlContext.checkPermission(AccessControlContext.java:342)
	at java.security.AccessController.checkPermission(AccessController.java:553)
	at java.lang.SecurityManager.checkPermission(SecurityManager.java:549)
	at java.lang.SecurityManager.checkExit(SecurityManager.java:761)
	at java.lang.Runtime.exit(Runtime.java:105)
	at java.lang.System.exit(System.java:923)
	at com.example.servertodatabase.server.Database.loadJdbcDriver(Database.java:121)
	at com.example.servertodatabase.server.GreetingServiceImpl.countUser(GreetingServiceImpl.java:56)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.google.gwt.user.server.rpc.RPC.invokeAndEncodeResponse(RPC.java:527)
	... 28 more
```

does someone have an advice? i would really like to solve the problem.

best regards

chf

---

