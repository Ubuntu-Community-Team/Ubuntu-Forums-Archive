---
title: "Java"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by jrandolph on 2008-07-29
I can't get some web pages to work, and it seems to be a java problem.
For example I am trying to connect to [www.gotomeeting.com](www.gotomeeting.com) to join a meeting.
The problem isnt loading the web site - the problem is that there is no button for me to click to join a meeting. When I go to the web site from a MS Windows computer there is buttons on the left side of the screen to click that say "join a meeting" and "host a meeting" but they dont show up on my computer.

Any ideas what could possibly be wrong?

output for java -version is
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

---

### Post by Diabolis on 2008-07-29
Got the java plug in for your web browser?
```
sudo aptitude install sun-java6-plugin
```

---

### Post by LowSky on 2008-07-29
I just tried that web page and it froze IE6 (on a Windows machine)

---

### Post by jrandolph on 2008-07-29
I tried that and got this

jacob@Jacob:~$ sudo aptitude install sun-java6-plugin
[sudo] password for jacob:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
jacob@Jacob:~$ 

But it still does not work

---

### Post by alzie on 2008-07-29
I know there has been issues at some sites (Pogo, yahoo) using java6.

In my case I found that removing the java6 and replacing it with sun-java5 (using Synaptic Package Manger) solved my problems.  

Maybe this will work for you.

---

### Post by Diabolis on 2008-07-29
What made you think that is a java problem?

I don't see the buttons that you mentioned, should I get an account and log in so I can see them?

---

### Post by Diabolis on 2008-07-29
> **alzie said:**
> I know there has been issues at some sites (Pogo, yahoo) using java6.

In my case I found that removing the java6 and replacing it with sun-java5 (using Synaptic Package Manger) solved my problems.  

Maybe this will work for you.

Ah! good to know.

---

### Post by jrandolph on 2008-07-29
So which items should I have installed for sun-java5

---

### Post by jrandolph on 2008-07-29
I was told by the person that was hosting the meeting that it had to be a java problem.

Plus I went to this site using Firefox on a windows box and it worked fine.

---

### Post by silkstone on 2008-07-29
I seem to have a later version...

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

Try...

sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin

... but you may have to uninstall the current version first.

---

### Post by alzie on 2008-07-29
Basically this is what I did in my case.

> Open Synaptic -- search for openjdk. Mark every openjdk and icedtea package for complete removal
Click "Apply"
search for sun-java and mark all sun-java6 for removal.
Mark for installation sun-java5-plugin (this should also pull in sun-java5-jre and sun-java5-bin. If you need the full jdk, you may also select that. Most people don't need the jdk.)
Click "Apply"


I hope this helps

---

### Post by alzie on 2008-07-29
@ silkstone

It seems there is a conflict of some sort with sun-java6 and Firefox 3 at some sites.  This is why I've changed to sun-java5.

I don't know which has the problem with the other but I hope its resolved soon :)

---

