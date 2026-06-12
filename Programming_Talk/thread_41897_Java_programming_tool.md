---
title: "Java programming tool"
date: 2005-06-15
forum: Programming Talk
---

### Post by ingrid on 2005-06-15
Hi,
I'm searching about a free software for java programming on ubuntu.
Another issues can be a soft like ultraedit. Is there someone to advice me ?

---

### Post by dataw0lf on 2005-06-15
You might want to take a look at jedit (jedit.org) and Eclipse (eclipse.org)

---

### Post by kostkon on 2005-06-15
[QUOTE=dataw0lf]You might want to take a look at jedit (jedit.org) and Eclipse (eclipse.org)[/QUOTE]

and Netbeans

---

### Post by mostwanted on 2005-06-15
I like BlueJ because it's so easy to use.

---

### Post by Seth on 2005-06-15
Eclipse is very powerful and has tons of cool features. It's never let me down.

---

### Post by thumper on 2005-06-16
My vote is for Eclipse too.  Very good tool for java.

---

### Post by Ride Jib on 2005-06-16
[QUOTE=thumper]My vote is for Eclipse too.  Very good tool for java.[/QUOTE]
 ^^^   +1

---

### Post by leohart on 2005-06-29
Is there a package that I can get from Synaptic to get Eclipse? Search Eclipse in Name and Description doesn't give me anything.

---

### Post by jerome bettis on 2005-06-29
yeah there's eclipse-sdk i think but the stable version is OLD .. you don't want it

just go to [www.eclipse.org](www.eclipse.org) and download the tarball, extract it and run it.  no install or anything like that needed, it's just a big giant java app.

---

### Post by leohart on 2005-06-29
That is awesome. In the README file it says that I need Java1.4JRE. What can I get that? [www.sun.com/java/?](www.sun.com/java/?)

---

### Post by jerome bettis on 2005-06-29
[QUOTE=leohart]That is awesome. In the README file it says that I need Java1.4JRE. What can I get that? [www.sun.com/java/?](www.sun.com/java/?)[/QUOTE]
 you should probably get the sdk since you're doing development.  it's right here
[https://jsecom16.sun.com/ECom/EComActionServlet;jsessionid=08139C806589C4FAEE5724ED5E1577D5#http://192.18.97.50/ECom/EComTicketServlet/BEGIN08139C806589C4FAEE5724ED5E1577D5/-2147483648/925357011/1/606770/606650/925357011/2ts+/westCoastFSEND/j2sdk-1.4.2_08-oth-JPR/j2sdk-1.4.2_08-oth-JPR:5/j2sdk-1_4_2_08-linux-i586.bin](https://jsecom16.sun.com/ECom/EComActionServlet;jsessionid=08139C806589C4FAEE5724ED5E1577D5#http://192.18.97.50/ECom/EComTicketServlet/BEGIN08139C806589C4FAEE5724ED5E1577D5/-2147483648/925357011/1/606770/606650/925357011/2ts+/westCoastFSEND/j2sdk-1.4.2_08-oth-JPR/j2sdk-1.4.2_08-oth-JPR:5/j2sdk-1_4_2_08-linux-i586.bin)

it's just a .bin file which you'll have to make executable by typing "chmod 755 file_name.bin". then do ./file_name.bin and it will extract it to a directory called j2sdksomething and you'll need to move that to /usr/lib by typing sudo mv directory_name /usr/lib.  if you want you can setup a link with sudo ln -s /usr/lib/directory_name /usr/lib/jdk so you know where it is.

any further questions just ask

---

### Post by buffbikedude on 2005-07-05
Better to teach someone how to fish.

Go to java.sun.com and download the latest JDK.

Right now you get there by clicking the link that says "J2SE 5.0".

There is a lot of other java stuff, including documentation that can be got to from [http://java.sun.com](http://java.sun.com).

---

### Post by Hanj on 2005-07-13
If you don't mind using closed-source software I recommend you check out Borland JBuilder 2005 which can be downloaded from [Borland's website](http://www.borland.com). The Foundation version is freeware and has the best editor I have ever used.

---

### Post by charlieg on 2005-07-15
See the wiki page on Java ([https://wiki.ubuntu.com/Java](https://wiki.ubuntu.com/Java)) for installation information.  Just download Eclipse from [www.eclipse.org](www.eclipse.org) and follow the wiki page on Eclipse ([https://wiki.ubuntu.com/EclipseIDE](https://wiki.ubuntu.com/EclipseIDE)) if you want to set it up 'properly' on your box.

---

### Post by sovin on 2006-02-19
[QUOTE=jerome bettis]yeah there's eclipse-sdk i think but the stable version is OLD .. you don't want it

just go to [www.eclipse.org](www.eclipse.org) and download the tarball, extract it and run it.  no install or anything like that needed, it's just a big giant java app.[/QUOTE]


could someone post the commands to accomplish the above? I downloaded the file eclipse-SDK-3.1.3-linux-gtk.tar.gz

---

### Post by kvorion on 2006-02-19
[QUOTE=ingrid]Hi,
I'm searching about a free software for java programming on ubuntu.
Another issues can be a soft like ultraedit. Is there someone to advice me ?[/QUOTE]

If you are a beginner then I suggest you start off with [BlueJ]("http://www.bluej.org")

If you want to install Eclipse using synaptic, then the package name is eclipse-jdt

---

### Post by sovin on 2006-02-19
[QUOTE=kvorion]If you are a beginner then I suggest you start off with [BlueJ]("http://www.bluej.org")

If you want to install Eclipse using synaptic, then the package name is eclipse-jdt[/QUOTE]

Bluej! I was trying to install that very app but was bummed out after a few days of failing to find the 'tools.jar' file the bluej installation requires.

---

### Post by kvorion on 2006-02-19
It is the folder where you have installed your JDK. Without knowing that, I dont think you will be able to make any Java IDE work. 

Just use the locate command to find out where tools.jar is located. As simple as that.

```
kv@kv:/home/kv# locate tools.jar
/usr/lib/j2sdk1.5-sun/lib/tools.jar

```

That was the output on my comp. I installed j2sdk using automatix. I assume that automatix installs it in a fixed directory, so the output should be the same for everyone who has used automatix to install j2sdk.

Therefore the directory you are looking for is /usr/lib/j2sdk1.5-sun/lib

---

