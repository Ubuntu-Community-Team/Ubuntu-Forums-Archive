---
title: "Installing Netbeans IDE"
date: 2009-09-09
forum: Packaging and Compiling Programs
---

### Post by gabimbola on 2009-09-09
Hi:

I have downloaded Netbeans IDE, that ended with .sh extension. I would like to install this on Ubuntu. I thought what I need to do is to chmod +x and then, the file. Thereafter, I thought I would execute thus: ./Nebeans... Please advise.

I welcome any response to my email (gabimbola@gmail.com).

Your immediate response to the above request would be greatly appreciated.

Note: I am new to Ubuntu, but not necessarily new to the *nix environment. I have been using Windows OS for a while, and I need to return to the Linux environment. 

Thanks.

Gbenga

---

### Post by Jive Turkey on 2009-09-09
I used the method you described and it worked for me.  Make sure you have the sun-java JDK as well.  The default in ubuntu is open-java (not Sun).  I think that some of the netbeans installers are packaged with it.  

I would also advise that you install it to a folder in your home directory (Netbeans not JDK).  Both netbeans and eclipse need write permissions for thier built-in updaters/plug-in managers to work.

---

### Post by joshua1983 on 2009-09-09
Check if you have a JAVA_HOME var to jdk

---

### Post by korin43 on 2009-09-11
If you're new to Ubuntu, I'd recommend installing it from the repository:
```
sudo aptitude install netbeans
```

---

### Post by angryfirelord on 2009-09-18
cd to the directory you put the netbeans file and simply execute:
> sh ./netbeans-6.7.1-ml-linux.sh

---

### Post by m3topaz on 2009-11-06
For Netbeans 6.7.1 in Karmic, install Netbeans from Synaptic, not from the downloadable install.
The downloadable install may well give this error (it did for me):
====================
The following packages have unmet dependencies.
  sun-java6-jdk: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages
====================
I spun up a fresh instance of Karmic under VirtualBox to look into this. For those who are curious about the JDK, Synaptic will plumb in default-jdk and default-jre, today's install at 1.6-30ubuntu5; plus openjdk-6-jdk at 6b16-1.6.1-1ubuntu3

---

### Post by rohitmp on 2009-11-11
It seems that the default jdk/jre (open JDK) and netbeans 6.7.1 have problem with each other. 
The openjre/jdk had permission issues working with netbeans.
My netbeans is no longer working (6.7.1 installed from synaptic). It does not load many of the modules, citing jars are unavailable.

I had nb6.7 before upgrading to karmic, after the upgrade nb did not launch at all. So i uninstalled nb6.5. Then installed new one from synaptic.
NOw this new nb6.7.1 refuses to find the required modules. complains that it cannot find the jars.

And now i want to use sun jdk hoping that would fix, but unfortunately the sun jdk has problem installing :( .
Finding no way out form here.
Please suggest on how to go about fixing this.

---

### Post by rohitmp on 2009-11-13
:( I did the following to get back my netbeans to work
1. Uninstalled netbeans from the synaptic manager.
2. Uninstalled current sun-jre from synaptic.
3. installed sun-jdk, this pulled jre and bin as the dependency.
4. downloaded the netbeans6.7.1 installer from the netbeans.org website.
5. changed the default jre to sun-jre using the cmd
sudo update-alternatives --config java

6. installed the new netbeans 6.7.1 from cmd line
sudo ./home/myhome/tmp/netbeans-6.7.1-ml-java-linux.sh

yep up it goes. work like a charm again.

---

