---
title: "Installing apache tomcat on netbeans"
date: 2010-10-26
forum: Programming Talk
---

### Post by psychok7 on 2010-10-26
hi, i have successfuly installed apache tomcat on my desktop since i downloaded the source and i could choose apache tomcat to install since the beginning of it.
But i cant seem to do the same on my netbook remix edition (because of the screens that dont fit when i download from the site) so i have to install it via repository. But afterwards i can't the find the "install apache" plugin inside netbeans...please help i need it a.s.a.p

---

### Post by r-senior on 2010-10-26
You don't want the repository install of Tomcat if you plan on using Netbeans to control it. Netbeans expects it all to be under one directory.

I usually download the latest version of Tomcat from the Apache website and put it under $HOME/Software (the location doesn't really matter). 

Edit the tomcat-users.xml in the Tomcat conf directory to be something like this:

```

<tomcat-users>
    <user username="admin" password="manager" roles="manager"/>
</tomcat-users>

```

It's only the role that has to be "manager", the username and password can be anything.

Then add Tomcat as a server to Netbeans, for example specifying "$HOME/Software/apache-tomcat-6.0.26" as Catalina Home and "admin" as the admin username, "manager" as the password. You might also need to modify the port numbers if you have other things listening on Tomcat's default of 8080.

---

### Post by psychok7 on 2010-10-28
well the thing is...im a total noob at this.. i have to install tomcat 7 for a school project, and i use netbeans.. i read that netbeans 6.9 does not come with tomcat 7.. can i use this guide to install it even thou its for tomcat 6? [http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

---

### Post by r-senior on 2010-10-28
You could use that guide but it won't be controlled by Netbeans. You have to configure Tomcat as a server in Netbeans to do that. Unfortunately, last time I checked, Netbeans 6.9 didn't have a server adapter for Tomcat 7. Only versions 6 and prior. You don't need the startup/shutdown stuff if you are controlling the server from Netbeans.

Do you specifically need Tomcat 7.x? Are you having to write some stuff with the new Servlet 3.0 specification? @WebServlet annotations and such? 

If you need Servlet 3.0, does it have to be Tomcat 7? Would running Glassfish 3.0 be OK? Netbeans plays with Glassfish 3.0 OK.

If you can manage with Tomcat 6.x, the way I described in my previous post is really easy. It really is just a case of unzipping the Tomcat archive, setting up that XML file, then adding the server to Netbeans. Five minute job. Honestly.

---

### Post by psychok7 on 2010-10-28
> **r-senior said:**
> You could use that guide but it won't be controlled by Netbeans. You have to configure Tomcat as a server in Netbeans to do that. Unfortunately, last time I checked, Netbeans 6.9 didn't have a server adapter for Tomcat 7. Only versions 6 and prior. You don't need the startup/shutdown stuff if you are controlling the server from Netbeans.

Do you specifically need Tomcat 7.x? Are you having to write some stuff with the new Servlet 3.0 specification? @WebServlet annotations and such? 

If you need Servlet 3.0, does it have to be Tomcat 7? Would running Glassfish 3.0 be OK? Netbeans plays with Glassfish 3.0 OK.

If you can manage with Tomcat 6.x, the way I described in my previous post is really easy. It really is just a case of unzipping the Tomcat archive, setting up that XML file, then adding the server to Netbeans. Five minute job. Honestly.


if i was an expert in the area like yourself i could probably use glassfish.. this is for school purposes (distributed systems) and they want me to use tomcat 7 and i am still at a basic level.. they gave me a document with a workaround for the netbeans problem with not supporting the latest version..
so if you are saying netbeans will start the server and i dont have to add to startup, what are the lines of the tutorial that i should do then? after copying the tomcat file that i downloaded to a folder and adding the export JAVA_HOME=/usr/lib/jvm/java-6-sun to .bachrc will that be enough? can i start using netbeans with it righ aways (with the workaround) ?

---

### Post by r-senior on 2010-10-29
> **psychok7 said:**
> if i was an expert in the area like yourself i could probably use glassfish.
You don't need to be an expert to use Glassfish. In some ways it's easier to configure than Tomcat because it has a comprehensive web-based admin tool.

> this is for school purposes (distributed systems) and they want me to use tomcat 7 and i am still at a basic level.. they gave me a document with a workaround for the netbeans problem with not supporting the latest version.
If they want you to use Tomcat 7, obviously you should use that. What steps does the workaround document suggest for using Tomcat 7 with Netbeans?

---

### Post by r-senior on 2010-10-29
OK, I just installed Tomcat 7 and these are the steps I used:

1. Download Tomcat 7 from [http://tomcat.apache.org/download-70.cgi](http://tomcat.apache.org/download-70.cgi)

2. Unzip the Tomcat 7 archive into $HOME/Software/ so that you end up with $HOME/Software/apache-tomcat-7.0.4

3. In a terminal, go to the $HOME/Software/apache-tomcat-7.0.4/bin directory and make all the shell scripts executable

```
$ chmod +x *.sh
```

4. Go to $HOME/Software/apache-tomcat-7.0.4/conf and edit the file tomcat-users.xml

```
<role rolename="manager-gui"/>
<user username="tomcat" password="password" roles="manager-gui"/>
```

Ensure the section is not commented out (which it is by default).

5. Go to $HOME/Software/apache-tomcat-7.0.4/bin and run the startup script

```
$ ./startup.sh
```

6. Open a web browser and go to [http://localhost:8080](http://localhost:8080)

You should get the Tomcat welcome page.

7. Click on the "Tomcat Manager" link in the top left and login with the username and password defined above.

Once Tomcat 7 is installed locally like this, you can start and stop it using the scripts in the bin directory and deploy applications to it using the Manager page or by dropping WAR files into $HOME/Software/apache-tomcat-7.0.4/webapps

(I did try adding this Tomcat 7 instance to Netbeans and pretending it was Tomcat 6. It displays OK in the list of servers but it doesn't start or stop from inside Netbeans).

---

### Post by psychok7 on 2010-10-29
> **r-senior said:**
> OK, I just installed Tomcat 7 and these are the steps I used:

1. Download Tomcat 7 from [http://tomcat.apache.org/download-70.cgi](http://tomcat.apache.org/download-70.cgi)

2. Unzip the Tomcat 7 archive into $HOME/Software/ so that you end up with $HOME/Software/apache-tomcat-7.0.4

3. In a terminal, go to the $HOME/Software/apache-tomcat-7.0.4/bin directory and make all the shell scripts executable

```
$ chmod +x *.sh
```

4. Go to $HOME/Software/apache-tomcat-7.0.4/conf and edit the file tomcat-users.xml

```
<role rolename="manager-gui"/>
<user username="tomcat" password="password" roles="manager-gui"/>
```

Ensure the section is not commented out (which it is by default).

5. Go to $HOME/Software/apache-tomcat-7.0.4/bin and run the startup script

```
$ ./startup.sh
```

6. Open a web browser and go to [http://localhost:8080](http://localhost:8080)

You should get the Tomcat welcome page.

7. Click on the "Tomcat Manager" link in the top left and login with the username and password defined above.

Once Tomcat 7 is installed locally like this, you can start and stop it using the scripts in the bin directory and deploy applications to it using the Manager page or by dropping WAR files into $HOME/Software/apache-tomcat-7.0.4/webapps

(I did try adding this Tomcat 7 instance to Netbeans and pretending it was Tomcat 6. It displays OK in the list of servers but it doesn't start or stop from inside Netbeans).

thanks you very much.. i will give it a try in a few hours and let you know if it works

---

### Post by psychok7 on 2010-10-29
your tutorial really works...thank you very much, already sent this configurations to my other colleagues using ubuntu

---

### Post by Noobie` on 2011-05-09
> **r-senior said:**
> OK, I just installed Tomcat 7 and these are the steps I used:

1. Download Tomcat 7 from [http://tomcat.apache.org/download-70.cgi](http://tomcat.apache.org/download-70.cgi)

2. Unzip the Tomcat 7 archive into $HOME/Software/ so that you end up with $HOME/Software/apache-tomcat-7.0.4

3. In a terminal, go to the $HOME/Software/apache-tomcat-7.0.4/bin directory and make all the shell scripts executable

```
$ chmod +x *.sh
```4. Go to $HOME/Software/apache-tomcat-7.0.4/conf and edit the file tomcat-users.xml

```
<role rolename="manager-gui"/>
<user username="tomcat" password="password" roles="manager-gui"/>
```Ensure the section is not commented out (which it is by default).

5. Go to $HOME/Software/apache-tomcat-7.0.4/bin and run the startup script

```
$ ./startup.sh
```6. Open a web browser and go to [http://localhost:8080](http://localhost:8080)

You should get the Tomcat welcome page.

7. Click on the "Tomcat Manager" link in the top left and login with the username and password defined above.

Once Tomcat 7 is installed locally like this, you can start and stop it using the scripts in the bin directory and deploy applications to it using the Manager page or by dropping WAR files into $HOME/Software/apache-tomcat-7.0.4/webapps

(I did try adding this Tomcat 7 instance to Netbeans and pretending it was Tomcat 6. It displays OK in the list of servers but it doesn't start or stop from inside Netbeans).

great also helped me -> thanks lots!!

supper noob :)

---

### Post by psychok7 on 2011-09-13
hi, i have installed netbeans 7 with tomcat 7.0.11, but when i try to deploy it from netbeans i get this error

```
The module has not been deployed.
	at org.netbeans.modules.j2ee.deployment.devmodules.api.Deployment.deploy(Deployment.java:210)
	at org.netbeans.modules.j2ee.ant.Deploy.execute(Deploy.java:106)
	at org.apache.tools.ant.UnknownElement.execute(UnknownElement.java:291)
	at sun.reflect.GeneratedMethodAccessor89.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.apache.tools.ant.dispatch.DispatchUtils.execute(DispatchUtils.java:106)
	at org.apache.tools.ant.Task.perform(Task.java:348)
	at org.apache.tools.ant.Target.execute(Target.java:390)
	at org.apache.tools.ant.Target.performTasks(Target.java:411)
	at org.apache.tools.ant.Project.executeSortedTargets(Project.java:1399)
	at org.apache.tools.ant.Project.executeTarget(Project.java:1368)
	at org.apache.tools.ant.helper.DefaultExecutor.executeTargets(DefaultExecutor.java:41)
	at org.apache.tools.ant.Project.executeTargets(Project.java:1251)
	at org.apache.tools.ant.module.bridge.impl.BridgeImpl.run(BridgeImpl.java:284)
	at org.apache.tools.ant.module.run.TargetExecutor.run(TargetExecutor.java:539)
	at org.netbeans.core.execution.RunClassThread.run(RunClassThread.java:153)
```

nevertheless the previous version that i installed (not with netbeans) works correctly with the same configurations and according to this tutorial.

any idea whats wrong??

---

