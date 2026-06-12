---
title: "Java, JSF, JSF, Eclipse And Glassfish"
date: 2008-08-26
forum: Outdated Tutorials &amp; Tips
---

### Post by dracvs on 2008-08-26
```

```
I have looked throughout the whole net for a guide that resumes every thing to do to begin working on JSP or JSF (not that I like them)
I will make this into sections. if I have any kind of mistake just let me know and I will correct it.

This one is  just for the development environment. Not for the production one. I will make another for that one.

for this you will need:
Glassfish Webserver, Mojarra Update for it, Eclipse or some tool, And The Java JDK
Glassfish and MOjarra, download them.. please. its better to do things by hand first.

Java:
Given this is a dev kind of guide, I suppose its good to use the Developer variant. You can install it via APT-GET so you are completely certain the right installation got to you. You will need the JDK from sun, that is:

```
$ apt-get install sun-java6-jdk
```
or if you just want to install java like a normal user
```
$ apt-get install sun-java6-jre
```

Now we need to setup a java home variable so the system knows where it is. There are many ways of doing this, but the only one I found is easier to follow for anyone who is starting the ubuntu experience is:

1) Check where java is, usually it lands on: 
```
/usr/lib/jvm/java-6-sun-1.x.0.0x
```

2) once you know where it is, You will have to add two variables in the "environment" file inside /etc. You will need root rights to modify it, so you can either start nautilus in sudo mode (...Dont...) or just launch an editor in sudo mode, then open the environment file in it.
```
$ sudo gedit
```
Add the following line to the file, replace the java folder with the one in your system, in my case is:
```
JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.06"
```
And if you want, add it to the path as well
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun-1.6.0.06/bin"
```

Notice that the PATH takes a /bin and java_home doesnt. this is important given when some apps (like ant) invoke JAVA_HOME it adds the bin automatically and it failsif you added it.

once thats done, you can logout and log in and invoke two commands and see if everything is okay.

```
echo $PATH $JAVA_HOME
```

if everything went well you should see the output pointing to where it should. if your system fails to boot because you set them up wrong, or made a Mispelling, go to the Login windows, and in sessions menu, choose failsafe Gnome, it will load a generic session, modify the path accordingly and relogin.

Now, Glassfish, 
Once you download it (its a .jar) you need to extract it somewhere for it to run
extracted like this:

```
java -Xmx256m -jar glassfish.jar
```
it will ask you to accept the license, you will do so, and then it will basically extract everything to a folder in the same place where the jar is standing called glassfish

Now, you need to actually install it. there is an executable called ant inside glassfish. you need to either, give permission to the folder or navigate to it. 
enter to where the installation of glassfish is and then, With permission:

```
$ chmod -R +x lib/ant/bin
$ ./lib/ant/bin/ant -f setup.xml

```

this will basically install Glassfish. 

Mojarra follows a similar pattern. making sure the server is down, then invoke:

```
java -jar Mojarra.jar glassfish_directory
```

That will update glassfish accordingly.

To Initiate the server, you can use the following:

```
$ /glassfish/bin/asadmin start-domain domain1
```

To access the server in administration mode, use a browser and point it to localhost:4848, or to the ip of the server say, 192.168.230.230:4848

that will set up glassfish.

later i will put up a smallish update.

---

