---
title: "Eclipse 3.5 and Tomcat6.0.18_ubuntu not playing well together!!"
date: 2009-10-08
forum: Programming Talk
---

### Post by michaelcc on 2009-10-08
I am having trouble setting up a tomcat runtime in eclipse.  Various jars are missing in various folders: 
home/bin/bootstrap.jar  lib/jasper-el.jar and servletapi6.jar

every time I download and place a jar I still need one more.  Perhaps the problem is that the tomcat6 version is a ubuntu synaptic package and the eclipse version I am using is not.  

any suggestions or experience with this?  I would rather keep tomcat as a synaptic package.

running Ubuntu 9.04, tomcat6.0.18-0ubuntu1.6, eclipse 3.5 build:20090920-1017.  anyone have a similar experience???

---

### Post by mastertimothy on 2009-11-07
Don't worry brother I'm having the exact same problem.  They definitely don't play nice at all.  I'm running the exact same setup as you except I'm running Ubuntu Karmic.

Anyone got any ideas?

---

### Post by cvgomes on 2009-12-20
I'm having the same problem.

Eclipse doesn't allow me to create web application while configuring Tomcat 6. It asked to set the Tomcat installation folder, if i set "/usr/share/tomcat6" then it shows "The Tomcat installation directory is not valid. It is missing expected file or folder conf.", if i set "/var/lib/tomcat6" then it shows "The Tomcat installation directory is not valid. It is missing expected file or folder lib/jasper-el.jar."

---

### Post by Firlian on 2009-12-22
A workaround would be to manually download and install tomcat from [http://tomcat.apache.org/](http://tomcat.apache.org/). This worked for me on opensuse 11.2 which has the same issue.

I'll try with sym links later tonight, i dont like to install software manually when i get can get it from the repo...

---

### Post by DisDis on 2010-01-11
In terminal:
```
sudo apt-get install tomcat6
cd /usr/share/tomcat6
sudo ln -s /var/lib/tomcat6/conf conf
sudo ln -s /etc/tomcat6/policy.d/03catalina.policy conf/catalina.policy
sudo ln -s /var/log/tomcat6 log
sudo chmod -R 777 /usr/share/tomcat6/conf
```Configure eclipse. Tomcat home is /usr/share/tomcat6

---

### Post by albe.mann on 2010-01-14
This was extremely helpful. Thank you very much!

---

### Post by tsaid on 2010-01-16
Thank you DisDis! Your solution really helped me.

As most Ubuntu users, I hate having to manually install software when it's available in the repos.

Tarek.

---

### Post by shannonnow on 2010-05-12
> **DisDis said:**
> In terminal:
```
sudo apt-get install tomcat6
cd /usr/share/tomcat6
sudo ln -s /var/lib/tomcat6/conf conf
sudo ln -s /etc/tomcat6/policy.d/03catalina.policy conf/catalina.policy
sudo ln -s /var/log/tomcat6 log
sudo chmod -R 777 /usr/share/tomcat6/conf
```Configure eclipse. Tomcat home is /usr/share/tomcat6


I don't mean to seem dumb, but I keep reading the way to configure eclipse is under: Window -> Preferences -> Server -> Runtime Environment. I am using eclipse 3.5.1 and it doesn't have a Server section under Window -> Preferences. Would you get me started in the right direction?

Thanks!

---

### Post by kodalisrikanth on 2010-05-30
Are you using Eclipse--J2EE environment?
I think you might be trying with Eclipse-J2SE.



Thanks,
Srikanth Kodali.

---

### Post by jepse on 2010-12-16
Hi,

thanks for the solution. I needed to extend the following command to make it work:

sudo apt-get install tomcat6
cd /usr/share/tomcat6
sudo ln -s /var/lib/tomcat6/conf conf
sudo ln -s /etc/tomcat6/policy.d/03catalina.policy conf/catalina.policy
sudo ln -s /var/log/tomcat6 log
sudo chmod -R 777 /usr/share/tomcat6/conf

#Addition
sudo ln -s /var/lib/tomcat6/webapps webapps
sudo chmod -R 777 /usr/share/tomcat6/webapps

---

### Post by MestreLion on 2011-01-02
Besides the needed symlinks, i really dont see why permitions must be set to 666 or, worse, 777. Ive found another solution that deals with permitions in a more secure way: add yourself to the tomcat6 group!

```
sudo usermod -a -G tomcat6 <your-login>
```

The logout and login again... this way you (and therefore Eclipse) has read/write to all tomcat's configuration files.

But.. a question: **WHY **eclipse need WRITE permition on Tomcats config files? Doesnt it copy the files to a "local" server? So why wouldnt READ be enough?

---

### Post by anshulmeena on 2011-10-11
I have eclipse3.5 and tomcat6 on Ubuntu 11.04. 
I am trying to create Dynamic Website Project on Tomcat but every time its giving me http 404 error. I am sure about Apache2 setup it is up and running. I followed every possible solution available on line. Changing the Catalina variable, installing tomcat6 manually, changing workspace and all the instruction given on this page. 
I am able to see the main page of tomcat6 with localhost:8080 and One of the user-role is Manager. I am able to login as manager and see all the examples and doc. When I run the server from eclipse3.5 'server' tab it give me 404 error. My workspace is not in '/var/www/', The environment variable are (after manual installation of tomcat6)

Dcatalina.home=/usr/local/tomcat
Dcatalina.base=/home/username/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0 (i don't know how to change this)
$JAVA_HOME=/usr/lib/jvm/java-6-sun

Still no result..
I have given many hours with zero and frustrating results.

---

