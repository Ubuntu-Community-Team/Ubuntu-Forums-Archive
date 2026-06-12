---
title: "How to use .jsp with apache?"
date: 2005-12-07
forum: Programming Talk
---

### Post by veraction on 2005-12-07
I have my webserver working fine with apache2.

I installed libapache2-mod-jk2 via apt-get.

**I want to know the basic steps for just getting a Hello World type program to work.**

Been googling for quite a while, but would prefer to find info about how to do it with the programs installed via apt-get, not compiled manually.

I know java quite well, working on regular programs for few years. But inexperienced with anything besides regular programs (i.e. j2ee, applets, beans, etc.)

Thanks

[edit]
By the way, I made a file called test.jsp with the following code and placed it in my web directory (/var/www), :

```

<html>
	<head>
		<title>hello world</title>	
	</head>

	<body>
		<%@ page language = "java" %>
		<% out.println( "Hello World" ); %>
	</body>
</html>

```

And it is interpreted as plain text..

that package, libapache2-mod-jk2, is apache tomcat add on right?

---

### Post by KLineD on 2005-12-07
Well it seems you know the basics, good!

Indeed, libapache2-mod-jk2 is the connector you need to get Apache communicate to Tomcat. Needless to say, tomcat must be running in a different port (8080 is default) of apache.

It seems you are already running both apache and tomcat just fine, so now you need to make some changes in configuration files in order to make the connection.

You can follow [this guide]("http://agiletesting.blogspot.com/2005/10/configuring-apache-2-and-tomcat-55.html") to make the changes, just skip to step five.

Hope it helps. I got mine running that way.

---

