---
title: "Integrating eclipse and tomcat"
date: 2006-10-18
forum: Programming Talk
---

### Post by docetes on 2006-10-18
Hi i was wondering if anyone could help me. I was wondering if it is possible to integrate the latest version of elipse and tomcat 5.5.20.

sorry if this is in the wrong forum

thanks for the help
Dave

---

### Post by sni on 2006-10-18
> **docetes said:**
> I was wondering if it is possible to integrate the latest version of elipse and tomcat 5.5.20.

Did that myself a few hours ago. Just grap this plugin:
[http://www.sysdeo.com/eclipse/tomcatplugin]("http://www.sysdeo.com/eclipse/tomcatplugin")

Good luck

---

### Post by Beer Me on 2007-09-04
> **sni said:**
> Did that myself a few hours ago. Just grap this plugin:
[http://www.sysdeo.com/eclipse/tomcatplugin]("http://www.sysdeo.com/eclipse/tomcatplugin")

Good luck


How?  I unzipped sysdeo into the correct eclipse directory, but I'm running into all sorts of security gotcha's when I try and start tomcat (because I'm not logged in as the root user)

---

### Post by ptillemans on 2007-09-04
In case you use the Europa release (3.3) in a private folder:

Install the WST tools using the intall tool. (If you istalled the JEE tools then it is already included).

You will the be able to define 'Servers' in the Preferences. Select Tomcat55 and point it to the right folder. 

If you use the JEE perspective and are in s Dynamic Web project you'll be able to attach this to the server (there is a servers tab in the bottom panel). The plugin will synchronize when youchange stuff. You can start/stop/debug the server.

Works nice, but I still prefer running my server in a terminal window with the loggings directed to the console. :)

Peter

---

### Post by ptillemans on 2007-09-04
Just another note about security issues : avoid them during development.

For development purposes install your tomcat and eclipse in a directory of your home folder :

e.g :

~/opt/eclipse
~/opt/tomcat

use for tomcat a similar version to your target platform. When it will be deployed by the sysadmins (or yo with your sysadmin hat on), it will run as the tomcat user and everything will be fine (unless you're trying to mix and match stuff from development and production which is a big NONO!!!).

If you start mix-n-matching users everything turns nasty. The problems keep coming from all sides and will severly impact on your productivity :(.

Use version control to share with coworkers(or yourself on another PC), use local copies in your home folder, ... and focus on coding...

grtz,

Peter

---

### Post by Beer Me on 2007-09-05
> **ptillemans said:**
> Just another note about security issues : avoid them during development.

For development purposes install your tomcat and eclipse in a directory of your home folder :

e.g :

~/opt/eclipse
~/opt/tomcat

use for tomcat a similar version to your target platform. When it will be deployed by the sysadmins (or yo with your sysadmin hat on), it will run as the tomcat user and everything will be fine (unless you're trying to mix and match stuff from development and production which is a big NONO!!!).

If you start mix-n-matching users everything turns nasty. The problems keep coming from all sides and will severly impact on your productivity :(.

Use version control to share with coworkers(or yourself on another PC), use local copies in your home folder, ... and focus on coding...

grtz,

Peter

That's the missing piece of the puzzle.  Don't install using apt, install it manually in a home directory.  Thanks a ton!  

Adam

---

