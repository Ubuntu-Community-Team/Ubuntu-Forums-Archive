---
title: "GUI for JAVA"
date: 2007-07-02
forum: Programming Talk
---

### Post by Zacharias on 2007-07-02
hi guys i have eclipse with jigloo but when i try to open GUI form eclipse freezes. 

how can i fix that or any is there any GUI tool and IDE for java i am using kubuntu 7.04

---

### Post by kknd on 2007-07-02
Netbeans has the most advanced GUI builder.

---

### Post by Praill on 2007-07-02
Absolutely. Netbeans takes the sting out of swing. Haha Im hillarious.

---

### Post by nitro_n2o on 2007-07-02
I recommend you keep using eclipse and check out [http://www.eclipseplugincentral.com](http://www.eclipseplugincentral.com) for any plug ins 

another advice: do ur gui's urself.. most gui builders generate ugly code that doesn't make any sense hard to debug, hard to maintain and embarrassing when people ask you: what is line 2249 for?

good luck :)

one more thing.. if you r developing JApplets don't run them as applets they freeze.. right click->run as..-> Java application if you have a main somewhere 
for applets.. run them using a browser window..

---

### Post by Modred on 2007-07-02
In a freak combination of the preceding comments, I like NetBeans and writing my own GUI code.  But as for the latter, it's more because the only GUI work I've ever done has been mostly simple apps that were just easier to code myself (both with C++/Qt and Java/Swing).  I'm just unfamiliar with using the GUI building tools that I've had chance encounters with, so really can't make a recommendation in regards to those.

But having a good editor that provides code completion, rather it's an IDE or something smaller, is a great boon if you choose to write your own.

---

### Post by Seine on 2007-07-03
Netbeans' Matisse (built-in) GUI builder is definitely superior to any other anywhere. Go for it. [http://www.netbeans.org/](http://www.netbeans.org/). (sudo aptitude install netbeans5.5)

---

### Post by Circus-Killer on 2007-07-03
> **Seine said:**
> Netbeans' Matisse (built-in) GUI builder is definitely superior to any other anywhere. Go for it. [http://www.netbeans.org/](http://www.netbeans.org/). (sudo aptitude install netbeans5.5)

quick question about using apt-get to install netbeans. when i tried to use apt-get, it download a small package, then during the install process told me that it is not the actual package. it told me to select a package, but only gave me an option to press enter or abort installation. when you press enter, it just tells you the same thing over and over again, press enter or abort. eventually i went for the abort option. :P

is there something im missing? and why did you suggest netbeans.org and using the repos. i'm confused.

---

### Post by michaelp on 2007-07-03
[http://packages.ubuntu.com/feisty/devel/netbeans5.5](http://packages.ubuntu.com/feisty/devel/netbeans5.5)

"PLEASE NOTE: This is simply an installer package to insure that the NetBeans IDE is well integrated with your system."

---

### Post by samjh on 2007-07-03
I wouldn't install Netbeans from repos.  It's confusing for new users and doesn't really add much.

Just get the binary installer from the Netbeans website: [www.netbeans.org](www.netbeans.org)

It integrates nicely with Ubuntu anyway, placing a menu item in the Gnome applications menu (under Programming).  Just make sure to update it (it will check automatically when you start up Netbeans, and show up a little icon on the bottom-right of the screen), because there is a fault involving project options that can be fixed by updating.

---

