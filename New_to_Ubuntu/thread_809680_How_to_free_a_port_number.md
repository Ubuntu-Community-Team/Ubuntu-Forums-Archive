---
title: "How to free a port number"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by vasleo on 2008-05-27
How do I release aport number binding to an application, like 25 to email client application.

---

### Post by quelx on 2008-05-27
Port assignment is arbitrary, you can run any service on any port you wish (just don't expect to get any email from others if you run your mail server on port 666).  If you don't have an email server (exim/postfix/sendmail) running then port 25 is "free" you can configure other services to use that port if you wish.  Can you be more specific with what you want to accomplish?

---

### Post by vasleo on 2008-05-27
Yepp!!

Iam using java application which is using smtp and whilw i run this application it says 25 port is already in use.

So how do i release this port which is having established status while i netstat!!

---

### Post by quelx on 2008-05-27
depends on which email server you have running try these:

```
sudo /etc/init.d/sendmail stop
sudo /etc/init.d/exim4 stop
sudo /etc/init.d/postfix stop
```

to see what is using 25 ```
sudo netstat -l|grep smtp
```

---

### Post by vasleo on 2008-05-27
Thanks!!

So you mean to say that we can release an application running on a port but cannot as port to make itself free. ie.. is to say that we should know the application running?

In my case when netstat it just specified "tcp        0      0 localhost:smtp          *:*                     LISTEN "

No application name. Good that you mentioned them and it was exim4.

Thank You.

---

### Post by quelx on 2008-05-27
> So you mean to say that we can release an application running on a port but cannot as port to make itself free. ie.. is to say that we should know the application running?

If there is no application using a port, then the port is available (free) for other applications to use.  If exim4 is running and configured as a standard email server, it will use port 25.  I think this is what you are asking, maybe if you could restate your question.

---

