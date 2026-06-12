---
title: "Need help installing java onto my 8.04"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by nathanscottdaniels on 2008-07-27
Okay, I did everything this guide said to:

[http://java.com/en/download/help/5000010500.xml#rpm](http://java.com/en/download/help/5000010500.xml#rpm)

I had to sudo apt-get the rpm thing along the way but I managed to get to step 7 before having problems.  Here is what my terminal says...

```

nathan@nathan-laptop:/usr/Java$ sudo rpm -iv jre-6u7-linux-i586.rpm
[sudo] password for nathan: 
error: Failed dependencies:
	/bin/basename is needed by jre-1.6.0_07-fcs.i586
	/bin/cat is needed by jre-1.6.0_07-fcs.i586
	/bin/cp is needed by jre-1.6.0_07-fcs.i586
	/bin/gawk is needed by jre-1.6.0_07-fcs.i586
	/bin/grep is needed by jre-1.6.0_07-fcs.i586
	/bin/ln is needed by jre-1.6.0_07-fcs.i586
	/bin/ls is needed by jre-1.6.0_07-fcs.i586
	/bin/mkdir is needed by jre-1.6.0_07-fcs.i586
	/bin/mv is needed by jre-1.6.0_07-fcs.i586
	/bin/pwd is needed by jre-1.6.0_07-fcs.i586
	/bin/rm is needed by jre-1.6.0_07-fcs.i586
	/bin/sed is needed by jre-1.6.0_07-fcs.i586
	/bin/sort is needed by jre-1.6.0_07-fcs.i586
	/bin/touch is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/cut is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/dirname is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/expr is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/find is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/tail is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/tr is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/wc is needed by jre-1.6.0_07-fcs.i586
	/bin/sh is needed by jre-1.6.0_07-fcs.i586
nathan@nathan-laptop:/usr/Java$

```

I have no idea what it is talking about.  I followed the directions on the Java site perfectly.  What do I need to do?  Gah!  I miss automated installation files!

---

### Post by tuxxy on 2008-07-27
I just replied to this topic which is about installing java;

[http://ubuntuforums.org/showthread.php?p=5471376#post5471376](http://ubuntuforums.org/showthread.php?p=5471376#post5471376)

---

### Post by jay019 on 2008-07-27
Personally I prefer to download the .bin file and run that. Installs into your home directory and with a bit of .bashrc editing its good to go. Alternatively have you tried the java in the ubuntu repos?

---

### Post by UltraMathMan on 2008-07-27
First make sure the multiverse repository is enabled by going to 

System->Administration->Synaptic Package Manager->Settings->Repositories

Then close Synaptic and open a terminal (Applications->Accessories->Terminal) and type ```
sudo apt-get update && sudo apt-get install sun-java6-jre
``` Enter your password and sit back while Java 6 is installed.

-Hope this helps :)

---

### Post by nathanscottdaniels on 2008-07-27
> **UltraMathMan said:**
> First make sure the multiverse repository is enabled by going to 

System->Administration->Synaptic Package Manager->Settings->Repositories

Then close Synaptic and open a terminal (Applications->Accessories->Terminal) and type ```
sudo apt-get update && sudo apt-get install sun-java6-jre
``` Enter your password and sit back while Java 6 is installed.

-Hope this helps :)

Sweet!  Thank you!:KS

Now how do I get Firefox to recognize it?

---

### Post by tuxxy on 2008-07-28
You need to move the java web plugin to your firefox plugins folder, usually in the /usr/lib/ dir

Type about: plugins in firefox to check if it is working.

---

### Post by knightcoder on 2008-07-28
Check this out man..

[http://www.java.com/en/download/help/5000012300.xml](http://www.java.com/en/download/help/5000012300.xml)

Under the "Create a new symbolic link", don't forget the "." at the end in the command 

```

ln -s /usr/java/jre1.5.0_04/plugin/i386/ns7
/libjavaplugin_oji.so .
```

---

### Post by nathanscottdaniels on 2008-07-29
> **knightcoder said:**
> Check this out man..

[http://www.java.com/en/download/help/5000012300.xml](http://www.java.com/en/download/help/5000012300.xml)

Under the "Create a new symbolic link", don't forget the "." at the end in the command 

```

ln -s /usr/java/jre1.5.0_04/plugin/i386/ns7
/libjavaplugin_oji.so .
```

Well, I am having two problems.  One is, I haven't the foggiest idea where my Java installation directory is and the second is I did a search of my HDD and I could not find the libjavaplugin_oji.so file.

---

### Post by camino3701 on 2008-07-29
I tried the advice of ULTRA MATH MAN and everything went fine until I got the msg E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem so I typed it in and then I got 'requested operation requires supervisor privilege' ok so what now?

RLB

---

### Post by kool_kat_os on 2008-07-29
> **camino3701 said:**
> I tried the advice of ULTRA MATH MAN and everything went fine until I got the msg E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem so I typed it in and then I got 'requested operation requires supervisor privilege' ok so what now?

RLB
```

sudo dpkg --configure -a
```

---

### Post by camino3701 on 2008-07-30
Thanks for your help I believe I now have the java installed in Ubuntu but as Tuxxy said earlier it needs to be moved into Firefox and I don't understand that procedure without a little more detail I'm really new at this sorry.

RLB

---

### Post by camino3701 on 2008-07-31
where do I find the /usr/lib/dir ?  I have java in OS but cannot get it into Firefox. the Java web site test says it's installed and working but Firefox does not show it as plugin installed.  THANK YOU

RLB

---

