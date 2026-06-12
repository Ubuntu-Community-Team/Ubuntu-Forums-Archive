---
title: "Glassfish and Netbeans"
date: 2010-01-12
forum: Programming Talk
---

### Post by Ultros88 on 2010-01-12
Maybe, this should be posted at the Netbeans forums but accounts seem to propagate like rabbits - I'm trying to keep them to reasonable numbers, so... maybe someone here can help me.

I've installed Netbeans 6.8 and GlassFish v3.

If I attempt to add a GlassFish server from within NB:
I set installation location to /usr/local/glassfishv3 (where GF is located on my machine), and NB tells me that it doesn't not have a "usable default domain". There exists .../glassfishv3/domains/domain1 with all its associated files. Why isn't this found as a default domain?

Next, I'm asked to "Register the local domain" I cannot do this no matter what path I give the wizard. I can however set the remote domain to localhost port:4848.

I cannot start the server.

If I start the server from the command line using 'asadmin start-domain' and follow the same steps as above, I can get a working admin console. However, now I am unable to stop the server from inside NB.

What should I do to set up a GlassFish server in Netbeans properly?

Help is much appreciated!

---

### Post by Reiger on 2010-01-12
A quick check: you run Netbeans as user X, but does account X have sufficient permissions to perform these tasks at the given path? I.e. can X read, write and execute the relevant parts at /path/to/domain ?

At least /usr/local/ and friends are usually the domain of root and I would assume that Netbeans is not run as root (because that would be utterly foolish).

If you are willing to go for defaults (during development), you could let Netbeans/Glassfish create a default domain itself; it should end up in e.g.: ~/.netbeans/6.8/GlassFish_v3/

I imagine you are not going to deploy to a development machine and therefore you can reasonably settle for the easy route.

---

### Post by Ultros88 on 2010-01-12
Alright, I hadn't considered the various user privilege requirements to access different paths. Definitely something to keep in mind for the future, thanks! Now that I know what's been going on I've been able to create a domain in /home/username/glassfishv3. I'm glad there was a simple solution. Hopefully other people will find this useful too.

Thanks again!
-Ultros

---

### Post by amogh.talpallikar on 2010-12-01
Hi,
I am also facing the same problem. I am new to both netbeans and glassfish and i am trying it for the first time. I am using Ubuntu 10.04, I installed netbeans along with glassfish and tomcat, both got installed in usr/local but glassfish is not being shown in the
servers dropdown while setting up netbeans. Can anyone please tell me how do i create this default domain for glassfish  in the home directory.

---

### Post by r-senior on 2010-12-01
For *development*, I find that you get the best results with Java application servers by downloading the archives and installing under your home directory somewhere, rather than using the Ubuntu packages. The packages are great for setting up dedicated servers or for final testing but Netbeans and Eclipse don't play nicely with them during development. Eclipse and Netbeans from the repositories are fine (unless you want to try the latest versions), but get Tomcat and Glassfish separately.

The other thing with Glassfish is to make sure you use Oracle/Sun Java. The admin console for Glassfish uses Java Server Faces (JSF) and I've had weird problems with anything JSF on OpenJDK.

---

