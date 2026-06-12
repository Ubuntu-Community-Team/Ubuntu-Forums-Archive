---
title: "j2ME newby problem"
date: 2011-07-20
forum: Programming Talk
---

### Post by skarosg3 on 2011-07-20
Hi all
I want to create a java app with ME, having some knowledge from the past on ME i thought that it would all come back to me, but it didnt.
I installed J2ME fine and downloaded the turorial for touch screen applilcation:
[http://netbeans.org/kb/docs/javame/svgtouch.html]("http://netbeans.org/kb/docs/javame/svgtouch.html")
to start with something easy, but i get this error:

> Problem: The project uses the Java Platform called "Java(TM) Platform Micro Edition SDK 3.0", but this platform was not found.
Solution: Click Resolve and create new platform called "Java(TM) Platform Micro Edition SDK 3.0".


I have followed all the instructions of the tutorial, but i cant make it to work.
i have downloaded and installed WTK2, but when i click on resolve->Add Platform->Java Me MIDP Platform Emulator and choose the WTK i get that

> Some Platform names are in collision


nothing seems to be working.

any ideas?

also, do you know if it is possible to create a j2ME app that work on all OS? symbian,MW and andriod i guess are ok. but what about iphone and ipads?

thanks

---

### Post by PaulM1985 on 2011-07-20
I have tried to do this before but had the same issue.  I don't think there is an ME SDK for linux.  The only way I got round it was to write the core code on linux (so that it was compatibile with ME eg no templates, file reading interface is not very good etc) and transfer it to windows where I would write the interface.

I was trying to write for a Nokia and this is what I had to do.  If you are looking to use Android, you would be better using Eclipse and following the tutorials on the Android site.

Additionally, Java programming is quite different for each.  Nokia supports a very cut down version of Java, no templates and stuff like I mentioned, whereas Android supports more.

Java only works on jail broken iphones as far as I am aware.

I would think about what your target platform is... if you want Nokia, I am sorry but I don't think you can do it on linux, if you want Android, use Eclipse and follow the tutorials.

Good luck

Paul

---

### Post by skarosg3 on 2011-07-20
Things on mobile app are so confusing! why on earth cant there be one language to work for all. i wanted to create a sightseeing app for mobile. So i dont have a target platform, i would like to write one program that runs on everywhere, thats why i though of java. it would be a good solution, since (as far as i know) all mobiles support java in some extend. but the more i read about it the more i am disappointed. 

i am uninstalling netbeans as i write this, and will install it manualy again, in case i missed something the first time.

but since you say that it is almost impossible to do, i dont know what i will do even if it does work.

cheers.

---

### Post by PaulM1985 on 2011-07-20
If you want something compatible with Nokia and Android then ME is the way to go.  Your core software would be written using ME and you would write a different interface for each.

The only issue is, I don't think you can write for ME on linux. I don't think there is an SDK available.  Someone please correct me if I am wrong.

Paul

---

### Post by skarosg3 on 2011-07-20
I think it is possible to write ME in Linux. the thing is that when i isntalled ME on netbeans and created an empty project(the hello world example) it worked. The problem i was having came up when i tried to create a touch screen app.

i turned to gwt now, in case i can work somehting out there. even though i have never used it before

---

### Post by PaulM1985 on 2011-07-20
Ah, I think I have found the issue.  It looks like some sort of ME dev can be done on linux.  The predecessor to Java ME SDK 3.0 is the Sun Java Wireless Toolkit.  This is available for linux.  I reckon that your hello world app will run fine with the Wireless Toolkit, but the touch screen apps need the new Java ME SDK 3.0 which you don't have.

Paul

---

### Post by skarosg3 on 2011-07-20
So you think that it would work ok under win? i do have XP on virtual box. i could give it a try there

---

### Post by PaulM1985 on 2011-07-20
Yes I think so, because you would be able to install ME SDK 3.0, which your project was saying was missing.

---

### Post by skarosg3 on 2011-07-20
Ok, it is working under XP.
BUT i got an other problem. on the tutorial it says to

> create 2 SVG Form components and
connect the SVG images to the source code by drag and drop the employeeList.svg file from the Project window onto the employeeList component


but when i drag an drop it i get this erro:
Incompatible component: svgImage [SVGImage]

any ideas?

---

