---
title: "[SOLVED] Frostwire: no internet connection"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-10-04
I have Frostwire downloaded & have a good internet connection on the computer, but Frostwire can not find the internet... (No Signal bars) However, My internet connection on the computer showing 90%, & no issues with any other program. I've tried re-installing Frostwire, re-booting & checked it on System/Admin/SysPkgMgr & see that it is installed. That is of course fine. It loads OK... It just does not see the internet???:confused:

---

### Post by gandaran on 2008-10-04
are you running a firewall? firestarter?

---

### Post by CoCoKnots on 2008-10-04
Frostwire shows that it does detect a firewall... I have not installed one if there is. How do I check that ?

---

### Post by Therion on 2008-10-04
Are you using the latest version from the Frostwire website?  
If not, you should upgrade your version from their site (.deb available as I recall).

Or... [See Post #44](http://ubuntuforums.org/showthread.php?t=292863&highlight=frostwire&page=5) or maybe [this thread](http://ubuntuforums.org/showthread.php?t=315222&highlight=frostwire) but most likely, you just need to upgrade your version of Frostwire.

---

### Post by CoCoKnots on 2008-10-04
Yes, The ver I downloaded was for Ubuntu/Debian & I checked the Sys/Adm/Syn-Pkg-Mgr for the 'Firestarter' also. It was there but not active.

---

### Post by CoCoKnots on 2008-10-04
I also took your advise & went to Post #44. I then downloaded gtk-gnutella. It also shows a firewall when I try to run it.

---

### Post by CoCoKnots on 2008-10-04
Is there something common between Frostwire & gtk-gnutella that would detect a firewall when other internet programs do not ?

---

### Post by CoCoKnots on 2008-10-04
I went ahead & removed gtk-gnutella using the add-remove option. It was not able to see thru the firewall either. Now I'm back trying to get Frostwire to work... Any Ideas ?

---

### Post by Frak on 2008-10-04
> **Therion said:**
> Are you using the latest version from the Frostwire website?  
If not, you should upgrade your version from their site (.deb available as I recall).

Or... [See Post #44](http://ubuntuforums.org/showthread.php?t=292863&highlight=frostwire&page=5) or maybe [this thread](http://ubuntuforums.org/showthread.php?t=315222&highlight=frostwire) but most likely, you just need to upgrade your version of Frostwire.
That thread is rather old.

Just make sure you have [sun-java6-jre]("apt:sun-java6-jre") installed. Icetea doesn't cut it. As said above, make sure you're using the latest version.

EDIT
Also, if it still uses IcedTea (it will tell you if you run frostwire over the terminal what you're using), run

```
sudo update-alternatives --config java
```
Choose the one that says /usr/lib/jvm/java-6-sun/jre/bin/java

---

### Post by CoCoKnots on 2008-10-04
This is what I have... Look Right ?


There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.
cocoknots@cocoknots-laptop:~$

---

### Post by Frak on 2008-10-04
> **CoCoKnots said:**
> This is what I have... Look Right ?


There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.
cocoknots@cocoknots-laptop:~$
Yep, looks right to me.

Does it work on any other Operating System/Computer on your home network?

---

### Post by CoCoKnots on 2008-10-04
Yes, That's driving me a little crazy... I don't get it.

---

### Post by Frak on 2008-10-04
Have you rebooted. It sounds stupid, but this fixed it for me once.

---

### Post by CoCoKnots on 2008-10-04
OK... I tried re-booting again after modifying the sun-java6-jre/... as above. No luck. It still tells me it can not detect an internet connection.

---

### Post by Mud.Knee.Havoc on 2008-10-04
Are you using a router?  If so, you'll need to open a port for Frostwire (or any other similar program).  

You probably also need to open a port in your software firewall (firestarter is the gui).

If you do both of these things, it should work without a problem.

---

### Post by Captain Cole on 2008-10-04
Yes, I am using a router... Linksys G... However, I don't have any idea of what you are talking about. Openinr a port for the Frostwire & Firestarter ? I have both but I don't know about the ports...

---

### Post by Frak on 2008-10-04
That's why I asked before if it worked on other OS's or computers within his network. It does, so it's not his router. Try installing [firestarter ]("apt:firestarter")and opening all ports.

---

### Post by CoCoKnots on 2008-10-04
OK... I installed Firestarter. What do I need to do to open all of the ports ?

---

### Post by gandaran on 2008-10-05
> **CoCoKnots said:**
> OK... I installed Firestarter. What do I need to do to open all of the ports ?
remove firestarter, use gufw firewall [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html) it's easier to set up, you can open or block all incoming traffic or just open the ports for any application like this [http://img67.imageshack.us/my.php?image=example2pq6.png](http://img67.imageshack.us/my.php?image=example2pq6.png)

---

