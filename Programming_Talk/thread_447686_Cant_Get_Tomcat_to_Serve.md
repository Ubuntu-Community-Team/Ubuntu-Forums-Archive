---
title: "Cant Get Tomcat to Serve"
date: 2007-05-18
forum: Programming Talk
---

### Post by subtle on 2007-05-18
Hello,

I am a linux noob and trying to set up Ubuntu with Java and Tomcat so I can have a go a programming servlets.

I have installed java using 

sudo apt-get install sun-java6-bin

I also set JAVA_HOME to set $JAVA_HOME = /usr/lib/jvm/java-6-sun/

I have downloaded tomcat version apache-tomcat-5.5.23.tar.gz

I unpacked the tarball, renamed it tomcat and moved to /usr/local/

I then ran gedit ~/.bashrc and added the following

export JAVA_HOME=/usr/lib/jvm/java-6-sun/ 
export CLASSPATH="/usr/local/tomcat/common/lib/jsp-api.jar;/usr/local/tomcat/common/lib/servlet-api.jar" 

I then ran sh /usr/local/tomcat/bin/startup.sh

and get the following

Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/lib/jvm/java-6-sun/

if I open firefox and go to [http://localhost/](http://localhost/) i get Firefox can't establish a connection to the server at localhost.

I have also set server.xml to port 80.

Has anybody got any ideas?

---

### Post by Psicolonia on 2007-05-18
you've installed java6 to run tomcat 5, in tomcat's home page there is a version for each specific java version. You should remove the tomcat 5 you've downloaded with synaptics and download tomcat6 in tomcat's home page. search "tomcat 6 binaries" on google and you'll find it. Basically just download and untar.

make sure there are no spaces in tomcats directory after unrar:

'home/user/my progs/tomcat' IS NOT VALID
'home/user/progs/tomcat' IS VALID!

and also in tomcats directory there is a bin foler where you should make:

chmod +x *.sh

tell me if it worked. ;)

---

### Post by subtle on 2007-05-18
Hi,

Thanks for the reply

I downloaded and untarred version 6 Tomcat and did as I did before. I had a few problems with permissions but having dealt with those I ran

sh /usr/local/tomcat/bin/startup.sh

and got the following

Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/lib/jvm/java-6-sun/

But again nothing from Firefox when typing in the URL [http://localhost/](http://localhost/)


Like I said I am a n00b so I must be doing something wrong but really am not sure what.

---

### Post by Psicolonia on 2007-05-18
GOOD NEWS!!! You've got it working! everything went right all you have to do now is:

[http://localhost:8080](http://localhost:8080)

or 

[http://127.0.0.1:8080](http://127.0.0.1:8080)

Tomcat's default port is 8080. congrats ;)

If you need help setting tomcat's administrator account, just let me know ;)

---

### Post by Psicolonia on 2007-05-18
oh and about setting the port to 80... try 8080 first without changing the file serve.

i've changed a lot of xmls in tomcat and sometimes things don't go as we expect...

---

### Post by subtle on 2007-05-18
Hi again,

Thanks for the help. I had changed the port to 80 and was getting the same error. I changed it back to 8080 and i now see the apache page.

Once again thanks.

---

