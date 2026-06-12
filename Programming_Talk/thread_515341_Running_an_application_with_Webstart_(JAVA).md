---
title: "Running an application with Webstart (JAVA)"
date: 2007-08-01
forum: Programming Talk
---

### Post by thomasaaron on 2007-08-01
Hi, folks. I've got a problem getting an application to run with WebStart.

It is an application (not an applet).
I created a jnlp file that WILL successfully launch it -- as long as I don't put security tags in it.  With security tags, I get this message when I try to launch it:
> 
Unsigned application requesting unrestricted access to system...
and then it lists my .jar file.

Note: I actually DO want it to have unrestricted access.

So, I followed these directions from this page: [http://java.sun.com/developer/technicalArticles/Programming/jnlp/](http://java.sun.com/developer/technicalArticles/Programming/jnlp/)

*# Second, create a key in the keystore (or use one you already have). You'll be prompted for information like first name and last. You should at least fill in that information.*
```
keytool -genkey -keystore myKeys -alias jdc
```
*# Third, sign the JAR. Be sure to remember your password from the previous step.*
```
jarsigner -keystore myKeys JNLPTime.jar jdc
```

When I run that last command, I get this error:
> jarsigner error: java.lang.RuntimeException: keystore load: Invalid keystore format

I've done some googling on it, and I'm thinking it might be a version problem (I've had those with Java before). But if that is indeed the problem, I've not been able to figure out how to solve it.

NOTE: I wrote and compiled the application with Netbeans. Everything else I am doing from the command line.

Thanks for your help,
Tom

---

### Post by thomasaaron on 2007-08-02
*bumpsy* (Sorry, I'm anxious for help!)

---

### Post by thomasaaron on 2007-08-02
OK. I won't bumb any more after this. Calling all java experts...

---

### Post by hod139 on 2007-08-02
These are the steps I did to self sign my own jar files:

Step 1 make a key:
keytool -genkey
Step 2 make a certificate:
keytool -selfcert
Step 3 sign jar files
jarsigner foo.jar mykey

---

### Post by thomasaaron on 2007-08-03
Thank you. I'll give that a try.

Best,
Tom

---

### Post by thomasaaron on 2007-08-06
Guys, this is killing me! I've got about 10 hours into trying to get this to work so far.

Here is the latest effort (trying to follow the above directions). What am I doing wrong?

> thomasaaron@ubuntu:~/Desktop$ keytool -genkey -keystore myKeyStore -keyalg RSA -alias thomasaaron
Enter key store password: password1
Enter key password for <thomasaaron>: password2

You are about to enter information that will be incorporated into
your certificate request.  This information is what is called a
Distinguished Name or DN.  There are quite a few fields but you
can use supplied default values, displayed between brackets, by just
hitting <Enter>, or blank the field by entering the <.> character
before hitting <Enter>.

Common Name (hostname, IP, or your name): Tom
Organization Name (company) [The Sample Company]: Tom
Organizational Unit Name (department, division): Tom
Locality Name (city, district) [Sydney]: Denver
State or Province Name (full name) [NSW]: Colorado
Country Name (2 letter code) [AU]: US
thomasaaron@ubuntu:~/Desktop$ 

thomasaaron@ubuntu:~/Desktop$ keytool -selfcert -keystore myKeyStore -alias thomasaaron
Enter key store password: password1
Enter key password for <thomasaaron>: password2
keytool error: java.lang.IllegalStateException: not encrypted
thomasaaron@ubuntu:~/Desktop$ 

At this point, the keystore that I created in the first step is hosed by the second step. It is turned into a regular, unencrypted, empty text file.

I've tried numerous switches (-dname, etc...). All have the same result.

I've tried several different tutorials on the net, but all of them give me a "keystore in wrong format" error.

Here is a list of the tutorials I've tried:
[http://java.sun.com/j2se/1.4.2/docs/guide/plugin/developer_guide/rsa_signing.html#signing_applets](http://java.sun.com/j2se/1.4.2/docs/guide/plugin/developer_guide/rsa_signing.html#signing_applets)
[http://saloon.javaranch.com/cgi-bin/ubb/ultimatebb.cgi?ubb=next_topic&f=23&t=004049&go=newer](http://saloon.javaranch.com/cgi-bin/ubb/ultimatebb.cgi?ubb=next_topic&f=23&t=004049&go=newer)
[http://java.sun.com/j2se/1.4.2/docs/guide/security/jsse/JSSERefGuide.html](http://java.sun.com/j2se/1.4.2/docs/guide/security/jsse/JSSERefGuide.html)
[http://java.sun.com/j2se/1.3/docs/tooldocs/win32/keytool.html](http://java.sun.com/j2se/1.3/docs/tooldocs/win32/keytool.html)
[http://forum.java.sun.com/thread.jspa?threadID=152882&messageID=469592](http://forum.java.sun.com/thread.jspa?threadID=152882&messageID=469592)
[http://archives.java.sun.com/cgi-bin/wa?A2=ind0401&L=jini-users&P=12474](http://archives.java.sun.com/cgi-bin/wa?A2=ind0401&L=jini-users&P=12474)

Guys, I realize I'm probably missing something basic here.
I just want to self-sign this application so I can put it on my home web server and run it from work via webstart. It will require all-permissions.

Thanks,
Tom

---

### Post by thomasaaron on 2007-08-06
GOT IT!

As fate would have it, /usr/bin/keytools was symlinked to the GUN java library's keytools, instead of jdk's keytools.

Man, my head is killing me after beating it on that wall! ](*,)
(I've always wanted to use that emoticon.)

Now maybe I can actually get on with some programming!

---

### Post by paule100 on 2008-11-07
Thank you, that post saved my day.

---

### Post by marcpuentes on 2009-11-18
Gracias amigo llevaba 3 días en esta historia y siempre me daba el mismo error. 
Thanks

---

