---
title: "java refusing to install!!!!!"
date: 2006-01-09
forum: Programming Talk
---

### Post by rock freak on 2006-01-09
h there ive have posted on trying ot get my java working on my ubuntu machine before it worked on my home one yet i go to do i on the one at work and it just refuses to install ive tried everything i no of!!! HELLLPPP

cheers for any help

Ollie

---

### Post by Viro on 2006-01-09
[QUOTE=rock freak]h there ive have posted on trying ot get my java working on my ubuntu machine before it worked on my home one yet i go to do i on the one at work and it just refuses to install ive tried everything i no of!!! HELLLPPP

cheers for any help

Ollie[/QUOTE]

You need to provide more information. What have you tried, and what where the error messages you received?

---

### Post by rock freak on 2006-01-09
it would appear to have installed java with no errors but you go to a java page on the web and it just doesnt work!! i have tried stuff from the package manager and i have tried the sun java one. ive tried tht dseveral times actually.

ill find the orginal thread i had on this so you can see that i have tried that to and it didnt work!!

---

### Post by rock freak on 2006-01-09
this is the linkt hat i was given to try and install java one it worked for the home PC but not the college one :@ it jsut returned that it couldn't find the servers

[https://wiki.ubuntu.com/forum/software/JavaApt](https://wiki.ubuntu.com/forum/software/JavaApt)

any help will be good cheers

---

### Post by Viro on 2006-01-09
Assuming that you've installed Java successfully via some package or binary, you need to create a symlink to your /usr/lib/mozilla-firefox/plugins directory. I'm not at my work machine at the moment, so I won't be much help. 

If you're still stuck tomorrow, I'll post the instructions when I get to the office.

---

### Post by rock freak on 2006-01-09
yeah if you could post that tomorrow for me that would be great cheers!!!!

---

### Post by Zerlinna on 2006-01-09
to create the symlink, do:

> 
cd /usr/lib/mozilla-firefox/plugins/
sudo ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so

of course the direcotry (/usr/java/...) may diverge depending on how and where you installed java. If you don't know where you have the libjavaplugin_oji.so do

> 
locate libjavaplugin_oji.so 

Z.

---

### Post by rock freak on 2006-01-09
cheers ill try that tomorrow!!!

---

### Post by rock freak on 2006-01-11
still no joy!!!! any other ideas my java is installed in /usr/java/jre1.5.0_06/

i am running the amd64 version of ubuntu so tht could have something to dowith it and the 64bit version of java is installed!!!!!!!

---

### Post by healychan on 2006-01-11
Please have a look at the guide in my signature. I hope it solves your problem.

---

### Post by Thirsteh on 2006-01-11
rock_freak, type the following in a terminal:

sudo ln -s /usr/java/jre1.5.0_06 /usr/java/default

See if that helps.

---

### Post by Viro on 2006-01-11
[QUOTE=rock freak]still no joy!!!! any other ideas my java is installed in /usr/java/jre1.5.0_06/

i am running the amd64 version of ubuntu so tht could have something to dowith it and the 64bit version of java is installed!!!!!!![/QUOTE]

If you're running the 64 bit version of Java, you may need to change the path of the plug-in. The path that was given to you was for the i386 (i.e. 32 bit version). Try substituting the i386 in the path with whatever the 64 bit architecture is called. I don't have a 64 bit machine, so I can't say.

So your final command should be something like
```

 cd /usr/lib/mozilla-firefox/plugins/
sudo ln -s /usr/java/jre1.5.0_06/plugin/**$YOUR_ARCHITECTURE$**/ns7/libjavaplugin_oji.so

```

Try that and see if it will work.

---

