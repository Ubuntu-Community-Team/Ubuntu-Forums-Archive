---
title: "Feeling Stupid"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Deedlit on 2008-07-27
Hi Everyone,


I recently upgraded to Hardy. When I go to some of the game websites, they tell me that I need to download Java Virtual Machine. I checked all the update things on the computer (synaptic, and add/remove) and they say I have the latest version. So I went to the java site and downloaded Java 6 u 7. Now, I'm trying to follow the instructions which are as follows:

>  To install the Linux (self-extracting) file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/

      Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-6u<version>-linux-i586.bin
   5. Verify that you have permission to execute the file. Type:
      ls -l


The problem I'm having, is I don't know where to put the directory and cd/usr/java doesn't work. Can someone please please tell me what I am doing wrong and how to fix it?

Thank you
Kathy

---

### Post by neurostu on 2008-07-27
The easiest way to install the JVM (Java Virtual Machine) is to open a terminal and type:
```

sudo apt-get install ubuntu-restricted-extras

```
that will install a package that includes the Sun JVM along with other things like Mp3 support

---

### Post by Deedlit on 2008-07-27
When I do that, I get:

> deedlit@Eeyore:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for deedlit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by neurostu on 2008-07-27
So the JVM is already installed and there is no need to install it by hand...

So its more an issue with firefox and the JVM

---

### Post by Dylock on 2008-07-27
Have you restarted firefox since installing JVM?

---

### Post by tuxxy on 2008-07-27
You need to have the **libgcjwebplugin.so** inyour firefox plugins directory.

Also make sure you are using the gcj java by typing this at terminal
```

sudo update-alternatives --config java
```

---

### Post by Deedlit on 2008-07-27
I have restarted firefox, but not the computer. Would that make a difference?

---

### Post by tuxxy on 2008-07-27
copy your **libgjcwebplugin.so** from /usr/lib/classpath 

to your firefox plugins dir, usually /usr/lib/mozilla/

to make sure its working reestart firefox and type this in the browser, **about: plugins** - with no spaces.

Now look for the libgjcwebplugin.so, it should be listed.

---

### Post by Deedlit on 2008-07-27
> **tuxxy said:**
> You need to have the **libgcjwebplugin.so** inyour firefox plugins directory.

Also make sure you are using the gcj java by typing this at terminal
```

sudo update-alternatives --config java
```

When I type that in terminal, I get this
> There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          3    /usr/bin/gij-4.2
          4    /usr/bin/gij-4.1
*+        5    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number: 

---

### Post by steveneddy on 2008-07-27
Open Firefox.

In the address bar, type

```
about:plugins
```

and look for java

if it's not there, go to Synaptic and look for iced tea and install that and that should take care of the issue.

If you have ad block, flash block or no script enabled, you need to give the web sites permission on your machine.

---

### Post by Nascar guy on 2008-07-27
Hi Everyone I am new here hope I am in the right place well here it goes I have hp nc6000 I loaded 8.04 lts off of live cd it would not boot up at first so
I click on something to help it boot up now when boot up it gives me two options at startup windows xp professional and Ubuntu in BIOS my question is this how do I set BIOS to start only in windows xp professional and start Ubuntu from cd only I now know you can press F10 key to change the boot order
The option ubuntu is in my BIOS even without cd in cd-rom system. Thank you

P.S. Ubuntu is not installed on the hard drive.

             Thank you again

---

### Post by steveneddy on 2008-07-28
Ubuntu in your BIOS?

Uhm - you may be using the incorrect terms here.

Maybe you see Ubuntu in a Boot Loader? before windows starts?

and you should probably start a thread of your own.

You'll get more responses that way.

---

### Post by neurostu on 2008-07-28
> **Nascar guy said:**
> Hi Everyone I am new here hope I am in the right place well here it goes I have hp nc6000 I loaded 8.04 lts off of live cd it would not boot up at first so
I click on something to help it boot up now when boot up it gives me two options at startup windows xp professional and Ubuntu in BIOS my question is this how do I set BIOS to start only in windows xp professional and start Ubuntu from cd only I now know you can press F10 key to change the boot order
The option ubuntu is in my BIOS even without cd in cd-rom system. Thank you

P.S. Ubuntu is not installed on the hard drive.

             Thank you again

Nascar Guy,

In stead of posting in this thread you should create your own thread in Beginner Talk... this will do a couple of things:
1- keep problems and solution compartmentalized
2- Keep thread discussion on topic
3- Give you're thread much greater visibility.

Honestly if you try posting in a new thread you'll get more responses quicker.

---

### Post by LuckyLawson on 2008-07-28
I just started Linux.I can't execute downloaded linux programs,& I'm lost. Please help!

---

### Post by bodhi.zazen on 2008-07-28
> **LuckyLawson said:**
> I just started Linux.I can't execute downloaded linux programs,& I'm lost. Please help!

It is overwhelming at first. In general use "add/Remove programs" or synaptic to install packages (programs).

[uhelp]community/SoftwareManagement[/uhelp]

[uhelp]community/SynapticHowto[/uhelp]

You may also want to check the wiki :

[https://help.ubuntu.com/8.04/](https://help.ubuntu.com/8.04/)

---

### Post by Nascar guy on 2008-09-22
Hi Everyone Thank you for all your replys I am new here I am sorry for

posting in the wrong area. I have since fix the problem I think this forum is

a great help for linux Thanks again.

---

