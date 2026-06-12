---
title: "Eclipse - problem, help needed."
date: 2005-12-26
forum: Programming Talk
---

### Post by noeluylee on 2005-12-26
HI,

I install Eclipse, and uninstall it for the reason of changing to another programming software, but know I change my mind, I want to go back to Ecplise, installation is very fast, as it seems the installation software are in my computer (but I dont know where it located, you might want to let me know) but when I run the program/ eclipse, I encounter this error "A suitable java virtual machine for running the ecplise platform could not be located" 

I dont know what went wrong... Hope you could help me with this problem.

Thanks a lot,, :)

---

### Post by blanky on 2005-12-26
You have to install the JRE (Java Runtime Environment)

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

or use automatix (which ubotu thinks is crap cause it's messy and stuff)

---

### Post by noeluylee on 2005-12-26
Hi Blanky,

Thanks a lot for the help I will try to install the JRE :)

Regards,
Noel

---

### Post by noeluylee on 2005-12-26
After installaing the JRE.. I still encounter the error = "A suitable java virtual machine for running the ecplise platform could not be located"

does not fix the problem :-(

Any other suggestion?

---

### Post by blanky on 2005-12-26
And you're sure the JRE worked right? Anyways, I recommend going into synaptic, search for eclipse, and do a **complete removal** on eclipse-sdk so that it uninstalls everything else it installed as well (just make sure it's nothing important to you). Then, select the package and install it.

---

### Post by noeluylee on 2005-12-26
how can I test if the jre work right on my system?:) also how to check the install version?

I do the complete removal and install it back thru synaptics.. and still no avail. :(  still having the same problem..

Thanks

---

### Post by cstudent on 2005-12-26
Try this:

```

java -version

```

This is mine:

bill@laptop:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)
bill@laptop:~$

If your java isn't showing something similar, try this:

```

sudo update-alternatives --config java

```

See if you have different java versions to choose from and select the Sun version.

This is mine:

bill@laptop:~$ sudo update-alternatives --config java
Password:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2sdk1.5-sun/bin/java

Press enter to keep the default[*], or type selection number:

---

### Post by noeluylee on 2005-12-27
CStudent, Here's my java version:

noel@NOEL-Linux:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

Will try to upgrade my jre to 1.5

Thanks a lot

---

### Post by noeluylee on 2005-12-27
Hi, I already updated the java to 1.5, but the problem of eclipse still the same, I still getting this error "A suitable java virtual machine for running the ecplise platform could not be located" 

Here's the version of java installed.
noel@NOEL-Linux:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

Any other solutions?

Thanks

---

### Post by noeluylee on 2005-12-27
anybody knows any workaround to this problem ? - thanks

---

### Post by lvgandhi on 2006-01-19
did you try setting /etc/eclipse/javahome to show your new java path? or alternatively set it in ~/eclipse/eclipserc in your home folder. Then try eclipse. This is what I learned from this forum.

---

### Post by Wille on 2006-01-21
I had pretty bad luck with the eclipse shipping with Breezy (crash at the start). Everything works pretty smoothly if you just download the eclipse from the eclipse website, and of course use the Sun JVM.

---

### Post by Viro on 2006-01-24
I've never had problems running Eclipse. What I needed to do was to add the following 2 lines to the file .gnomerc in my home folder:
```

JAVA_HOME=/opt/jre
PATH=$JAVA_HOME/bin:$PATH

export PATH JAVA_HOME

```

Once you've added those lines, log out and log back into GNOME and you should be good to go.

p.s. The version of eclipse that ships with Ubuntu is pants. It is compiled natively with GCJ and contrary to popular belief, compiling Java apps into native binaries doesn't speed things up, it just slows things down.

---

