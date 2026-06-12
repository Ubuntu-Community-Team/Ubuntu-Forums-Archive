---
title: "Visual Java Developer?"
date: 2005-09-07
forum: Programming Talk
---

### Post by Unit #134679 on 2005-09-07
Does anyone know a good visual developer for Java? Someone told me Eclipse but I want to know one thats good for Ubuntu

---

### Post by born_confused on 2005-09-07
[QUOTE=Unit #134679]Does anyone know a good visual developer for Java? Someone told me Eclipse but I want to know one thats good for Ubuntu[/QUOTE]
 Well eclipse is great for java to be honest. By visual do you mean design and code like visual studio? If so you can obtain swt designer, a plugin for eclipse, which does this.

---

### Post by Unit #134679 on 2005-09-07
Yes, visual like Visual Studio. Sorry if I confused you or didnt clearly state my question. Is there a .deb file for Eclipse? Would I get SWT Designer from the Eclipse website or is there a .deb file for it too?

---

### Post by Unit #134679 on 2005-09-22
No one knows where I can get SWT Designer?

---

### Post by Drakx on 2005-09-22
[QUOTE=Unit #134679]No one knows where I can get SWT Designer?[/QUOTE]
 [http://www.google.co.uk/search?q=SWT+Designer&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-GB:unofficial](http://www.google.co.uk/search?q=SWT+Designer&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-GB:unofficial)

---

### Post by sumadartson on 2005-09-22
[QUOTE=Unit #134679]Yes, visual like Visual Studio. Sorry if I confused you or didnt clearly state my question. Is there a .deb file for Eclipse? Would I get SWT Designer from the Eclipse website or is there a .deb file for it too?[/QUOTE]

For eclipse, you can just unzip the file you downloaded from the eclipse site.

Java needs to be in your path though. The command ```
which java
``` should return something like ```
/usr/bin/java
``` If not, just ```
sudo apt-get install sun-j2re1.5
```

---

### Post by Unit #134679 on 2005-09-22
Alright thanks. By the way, the Java package has been missing...so I dont have Java right now

---

### Post by DancingSun on 2005-09-22
There's Netbeans as well.  Get it from [www.netbeans.org](www.netbeans.org).

---

### Post by sumadartson on 2005-09-22
Hrmz. I wasn't aware of the missing Java. It shows up fine on my synaptic, but, IIRC, you should have backports enabled in your sources.list . Does anyone have more recent information on the package status?

Oh, and you could try the files from [sun](http://java.sun.com/j2se/1.5.0/download.jsp), but you're out on your own if you do that. The sun site has some decent pointers though.

For completeness, my backports are: ```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

```

---

### Post by Unit #134679 on 2005-09-23
[QUOTE=sumadartson]Hrmz. I wasn't aware of the missing Java. It shows up fine on my synaptic, but, IIRC, you should have backports enabled in your sources.list . Does anyone have more recent information on the package status?

Oh, and you could try the files from [sun](http://java.sun.com/j2se/1.5.0/download.jsp), but you're out on your own if you do that. The sun site has some decent pointers though.

For completeness, my backports are: ```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

```[/QUOTE]

Hmm...I just added it but it still didnt work. Let me see your entire sources.list

---

### Post by KLineD on 2005-09-23
Netbeans has a great Swing GUI editor included in 4.1 and I've seen some flash videos of a new layout manager in the works that would supposedly ease the gui layout process.

I like Eclipse very much, but Netbeans is getting a lot better. Check it out [http://www.netbeans.org](http://www.netbeans.org)

---

### Post by Unit #134679 on 2005-09-23
Hmm...that looks great. Only problem is I dont have Java. Keep getting a 'missing package' error

---

### Post by sumadartson on 2005-09-23
Nothing special here...

```

## UBUNTU MAIN
deb http://nl.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu hoary main restricted

deb http://nl.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu hoary-updates main restricted

## UBUNTU UNIVERSE
deb http://nl.archive.ubuntu.com/ubuntu hoary universe
deb-src http://nl.archive.ubuntu.com/ubuntu hoary universe

## UBUNTU SECURITY
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security universe multiverse

## UBUNTU MULTIVERSE
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## UBUNTU BACKPORTS MIRRORS
#deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
#deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
#deb ftp://ftp2.caliu.info/backports/ hoary-backports-staging main universe multiverse restricted
#deb ftp://ftp2.caliu.info/backports/ hoary-extras-staging main universe multiverse restricted

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

```

---

### Post by Unit #134679 on 2005-09-23
Yea. Hmmm

---

### Post by sumadartson on 2005-09-24
I now noticed that I see the package in my synaptic list and in ```
apt-cache search sun
``` However, it might just be that Synaptic only shows the package because it's installed. Reinstall options are disabled. I was not about to test the reinstall, since I do lot of Java on this box and removing it would seriously cripple my productivity.

Golly, do I feel smart now. Sorry to have set you on a wild goose chase.

[This](http://www.ubuntuforums.org/showthread.php?t=68198&highlight=java) thread has the details on how to install Java based on the self-extractor from  [sun](http://java.sun.com/j2se/1.5.0/download.jsp). I hope that will be more helpful. My apologies again for the silly mistake.

---

### Post by phex on 2005-09-24
If your really want to learn GUI designing in Java read this books:
[http://www.amazon.de/exec/obidos/ASIN/0130796662/qid=1127557874/sr=8-5/ref=sr_8_xs_ap_i5_xgl/302-2563569-7389611](http://www.amazon.de/exec/obidos/ASIN/0130796662/qid=1127557874/sr=8-5/ref=sr_8_xs_ap_i5_xgl/302-2563569-7389611)
[http://www.amazon.de/exec/obidos/ASIN/0130796670/qid=1127557874/sr=8-2/ref=sr_8_xs_ap_i2_xgl/302-2563569-7389611](http://www.amazon.de/exec/obidos/ASIN/0130796670/qid=1127557874/sr=8-2/ref=sr_8_xs_ap_i2_xgl/302-2563569-7389611)

for sure with GUI designers you can design nice GUIs but you should know whats behind it. You must always know: what is the difference between the different LayoutManagers in Java to create powerfull GUIs in Java. So in fact, i recommend you this book:
[http://www.amazon.de/exec/obidos/ASIN/0130796662/qid=1127557874/sr=8-5/ref=sr_8_xs_ap_i5_xgl/302-2563569-7389611](http://www.amazon.de/exec/obidos/ASIN/0130796662/qid=1127557874/sr=8-5/ref=sr_8_xs_ap_i5_xgl/302-2563569-7389611)

there you will learn all the basic LayoutManager, Image Manipulation, Event Handling (the old and the new one) and so on.

---

### Post by alfotis on 2005-09-24
Give Borland JBuilder a try. The Foundation edition is free (!!!). At least, that's what I use...

---

### Post by Unit #134679 on 2005-09-24
Well I'm lovin NetBeans, I just wish it worked for me on Windows. I went to Borland's site for JBuilder but I didnt notice anything saying that it was free

EDIT: Nevermind...I had to run it as admin

---

### Post by Unit #134679 on 2005-09-27
Wow, NetBeans is sh*t. It wont even work for me.

---

