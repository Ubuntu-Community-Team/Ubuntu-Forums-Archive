---
title: "Help with Netbeans: do I have to run as sudo/root?"
date: 2008-10-07
forum: Programming Talk
---

### Post by yoyodyne on 2008-10-07
This is a really dumb question.
Just installed Netbeans 6, JDK6, Tomcat5.5, etc. 
I *think* that because Tomcat5.5 is owned by root (did it get that way via synaptic?), I'm having problems using Netbeans and Tomcat.

I could run a servlet okay, but my JSP was giving me permission errors (due to /usr/share/tomcat5.5 being owned by root). 

I exited netbeans, re-ran with sudo and now it is happy. Do I have to do it that way? If not, what do I need to fix? 
Maybe I'm using an external (to netbeans) Tomcat and need to use the "internal" version?

EDIT: Ubuntu Hardy, btw.

---

### Post by xlinuks on 2008-10-08
Try changing the owner of /usr/share/tomcat5.5
last time I did so Santa Klaus came into my house..

---

### Post by patrickballeux on 2008-10-08
The problem you are facing is that with JSP files, there are classes that are created in a temporary folder under tomcat5...

It's been a while, but I think that you can set that folder somewhere else (like /tmp/) so you would not need to give special permission on a system folder.

But the quickest fix is to chmod -R 777 /usr/share/tomcat5...


Good luck!

---

### Post by yoyodyne on 2008-10-08
haha...or should I say, ho ho ho.

Tried that, got same problem. Had to chown a few other dir's (/var/cache/tomcat?). 

Now getting a different error:
```

java.lang.ClassNotFoundException: org.apache.jsp.index_jsp
java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	java.security.AccessController.doPrivileged(Native Method)
	java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	org.apache.jasper.servlet.JasperLoader.loadClass(JasperLoader.java:131)
	org.apache.jasper.servlet.JasperLoader.loadClass(JasperLoader.java:63)
	org.apache.jasper.JspCompilationContext.load(JspCompilationContext.java:597)
	org.apache.jasper.servlet.JspServletWrapper.getServlet(JspServletWrapper.java:137)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:314)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:329)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:265)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)

```

I should probably think about uninstalling most of this, then reinstalling in a VM (at least the Tomcat portion). Hrmmm...

---

### Post by yoyodyne on 2008-10-08
Doh.
OK, added chmod 777 and that worked (had to do /var/cache area as well). 

Is there a better (overall) way to do this? i.e. reinstall tomcat as myself instead of root? synaptic/sudo always throws me for a loop on ubuntu.

btw, thanks for the suggestions.

---

### Post by patrickballeux on 2008-10-08
It seems that your compiled classes cannot be found by your tomcat5 process.  Have to located the temp folder where the classes are stored after a JSP compilation?

It is still a permission denied you have.  Look at the java.security.AccessController.doPriviledged error...

Also, is your Tomcat listening on port 80 (less than 1024) because you need to be root to startup a listening process on those ports.  Set your port to be 8080 instead while you develop.

Good luck!

---

### Post by patrickballeux on 2008-10-08
Oups, you answered while I was writing back... :

Tomcat should run under it's own user and group.  Then you should be part of the same group and configure your folder to give access to the group of Tomcat.

That would be the right way.

---

### Post by yoyodyne on 2008-10-08
> **patrickballeux said:**
> 
Tomcat should run under it's own user and group.  Then you should be part of the same group and configure your folder to give access to the group of Tomcat.
 

Got it. That's how I'd normally do it - but would be because I went and downloaded Tomcat directly, not via synaptic. 
Should I just chown/chmod Tomcat to a new user and group? And if I upgrade Tomcat via synaptic, do the same thing again?

I guess my question is more of - how do I use apt-get to install Tomcat (or netbeans, or whatever) as another user, instead of root? Or is it just up to me to change that as needed.

---

### Post by mssever on 2008-10-09
> **yoyodyne said:**
> I guess my question is more of - how do I use apt-get to install Tomcat (or netbeans, or whatever) as another user, instead of root? Or is it just up to me to change that as needed.
If the Tomcat debs run as root, then you should file a bug report on [https://bugs.launchpad.net](https://bugs.launchpad.net).

---

### Post by yoyodyne on 2008-10-09
Hmm...that's not just a function of synaptic (i.e. app servers/services are installed as root)?

---

### Post by mssever on 2008-10-09
> **yoyodyne said:**
> Hmm...that's not just a function of synaptic (i.e. app servers/services are installed as root)?
That's configurable in the .deb file.

---

### Post by SemperNoob on 2008-10-22
I have had a nearly identical problem with Netbeans and Tomcat.  Both were installed with synaptic.  Tomcat shows it's administration pages without issue and seems to work fine without Netbeans.  Netbeans seems happy and can find, start and stop tomcat.  However when I attempt to deploy and run a jsf project from netbeans, tomcat has a large number of permission errors when trying to access folders inside the catalina home directory. 

  I can make tomcat display the page by running netbeans from the command line with sudo, but I after that I am having trouble getting it to find the classpath for an applet I have embeded in the page (this might just be my lack of experience with Java).  It seems like netbeans may be starting it's own instance of tomcat which then shares the permissions of the user that started netbeans?  

I am using this machine as both a development machine and a basic web server and I don't want to loosen security more than necessary but running netbeans with sudo seems like a hack.  Is that the best way or does using chmod to change the permissions on the tomcat directories still leave them secure "enough" for a machine exposed to the internet?  Or do I need to find a different package to (using apt-get) to install things correctly?

Thanks for the help!  This thread was the key to getting it started at all ...

---

### Post by bangeko on 2008-11-10
In my case, if I install Netbeans from Synaptic, it require openJDK not sunJDK. Because my tomcat already run with sunJDK, I have to download Netbeans from netbeans.org site not from ubuntu repo.

---

### Post by mintar on 2009-06-14
I know this thread is really old, but it was the only thing I could find about this problem, and I solved it and wanted you all to know. Perhaps it helps somebody.

What you have to do is:
mkdir ~/catalina_base/ && cd ~/catalina_base/
mkdir conf logs temp webapps work
cp /etc/tomcat5.5 conf/*

Then, in the NetBeans "new Server" dialog, specify ~/catalina_base/ as the Catalina Base directory.

---

