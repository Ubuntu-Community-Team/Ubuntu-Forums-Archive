---
title: "Tomcat Permissions"
date: 2007-01-22
forum: Programming Talk
---

### Post by jfenwick on 2007-01-22
I'm using Tomcat5.5 on Ubuntu 6.10.

I'm trying to create a file from inside a servlet:

File auditLogFile = new File(getInitParameter("audit.log"));

When I get to this line, this is the error that is thrown:

SEVERE: StandardWrapper.Throwable
java.security.AccessControlException: access denied (java.io.FilePermission /var/log/tomcat5.5/audit_log.log read)
at java.security.AccessControlContext.checkPermission(AccessControlContext.java:264)
at java.security.AccessController.checkPermission(AccessController.java:427)
at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
at java.lang.SecurityManager.checkRead(SecurityManager.java:871)
at java.io.File.exists(File.java:700)
at org.test.util.Init.init(Init.java:121)
...

Now, I have previously created this file and given it the same permissions as other files that Tomcat generates:

-rw-r--r-- 1 tomcat5 nogroup 2 2007-01-19 17:21 audit_log.log

Compared to:

-rw-r--r-- 1 tomcat5 nogroup 138259 2007-01-19 17:24 catalina_2007-01-19.log

The second log file is one that Tomcat generates itself, and so I copied the permissions from that.
What else could be causing this?

Thanks,
Jacob

---

### Post by jfenwick on 2007-01-22
Nevermind... I found out it's the security manager causing the problem.

---

### Post by Seine on 2007-01-23
> **jfenwick said:**
> Nevermind... I found out it's the security manager causing the problem.

Glad you found the answer. To be precise, the security manager is the answer to a different problem ... not a problem in itself. :)

---

### Post by lamadredelsapo on 2007-02-26
As you say, if you turn off the security manager you don't get the java.security.AccessControlException: access denied (java.io.FilePermission exception, but have you managed to make a service able to access a local folder with the security manager turned on?

If I turn off the security manager it works but if I add:
```
grant codeBase "file:/home/fernando/movies" {
  permission java.io.FilePermission "<<ALL FILES>>", "read, read, write, delete, execute";
};

grant codeBase "file:/home/fernando/movies/*" {
  permission java.io.FilePermission "<<ALL FILES>>", "read";
};
```

to catalina.policy and turn on de security manager it does not work.

Some advice would be appreciated

---

