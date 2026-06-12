---
title: "Netbeans 6.0.1 and tomcat"
date: 2008-06-26
forum: Programming Talk
---

### Post by bghost4 on 2008-06-26
Back when I was using gutsy and Netbeans 5.5, When testing out webapps it just seemed to work, I pressed the run button, and everything was a go, apparently it had some kind of bundled tomcat that came with it. I hear talk of tomcat6 being bundled with Netbeans 6, but I was unable to do the "click and Go" runtime with Hardy. I hate to admit I'm a bit of a noob when it comes to setting up tomcat, although I have done it a few time, with no real customization. Netbeans 6 said it had an Tomcat plugin, so I installed it without much luck of getting it to go like Netbeans 5.5 on Gutsy. I did however install the tomcat 5.5 server and got it "set up" However I ran into a bunch of Security Exceptions. I searched the forums and found a "fix" although it seemed really bad, as I had to add some configuration to tomcat for every project I wanted to run. Now I've started a new project and am running into Security Exceptions again, mostly java.io.filepermission
I tried some of the same fixes, but it doesn't seem to go. Since I no longer have any netbeans 5.5 and Gutsy installs I can't test this to see if its just something with netbeans 6, Plus I would like to use tomcat 6, even if its for no other reason than its the latest version, and thats what I'm running on the "production" server.
Thanks in advance for any help/advice that anyone may have.

--Del

Ok, this is most likely an Ubunti + netbeans thing. I took the compiled dist war file and uploaded it to the production server, and all is well, so at least I know the source is valid and works. At least on a tomcat-6 server.

--Del

---

### Post by xlinuks on 2008-06-27
Don't use NetBeans+Tomcat from the repositories, they are old and don't function properly, you will save yourself a lot of time and headache.
Instead I would suggest using the latest version from Sun, tested - works.
Choose the "Web & Java EE" version:
[http://download.netbeans.org/netbeans/6.1/final/](http://download.netbeans.org/netbeans/6.1/final/)

---

