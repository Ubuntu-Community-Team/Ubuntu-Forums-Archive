---
title: "java ca-certificates dpkg error"
date: 2011-05-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-05-10
I've just upgraded to Oneiric and am getting the above error when running updates. It doesn't seem to be affecting anything.
I've browsed through the forum but not seen anything about it. Are my eyes worse than I thought, or is this not happening elsewhere?
Thanks :-)

---

### Post by dino99 on 2011-05-10
last week we got a ca-certificates update: 201104021ubuntu1; is it installed on your system ?

---

### Post by Quackers on 2011-05-10
Thanks dino99, yes it appears so

---

### Post by Harry33 on 2011-05-10
> **Quackers said:**
> Thanks dino99, yes it appears so

There were dependency issues with ca-certificates and openssl, but that is solved by now.

---

### Post by Quackers on 2011-05-10
Hmm, ah well, it doesn't seem to be upsetting anything. Just keep getting the message at the end of updates.

---

### Post by cecilpierce on 2011-05-10
> **Quackers said:**
> Hmm, ah well, it doesn't seem to be upsetting anything. Just keep getting the message at the end of updates.

I was getting it to so I removed it to see what happens and so far nothing but not sure it was the right move ?

---

### Post by Harry33 on 2011-05-11
> **cecilpierce said:**
> I was getting it to so I removed it to see what happens and so far nothing but not sure it was the right move ?

What did you remove?
Removing ca-certificates will remove Brasero, Libre-office, Totem and Transmission among others.

---

### Post by VinDSL on 2011-05-11
> **Harry33 said:**
> What did you remove?
Removing ca-certificates will remove Brasero, Libre-office, Totem and Transmission among others.
Hrm...

I removed ca-certificates-java some time ago.  ca-certificates is still installed.

I just opened all the proggies that you listed (above) and they work fine.

AFAIK, its removal only affects icedtea.

---

### Post by cecilpierce on 2011-05-11
> **Harry33 said:**
> What did you remove?
Removing ca-certificates will remove Brasero, Libre-office, Totem and Transmission among others.

java ca-certificates removed, but i noticed on another install its still there and no problems ?
java ca-certificates removed some things but i haven't noticed anything wrong, YET!:confused:

should i put it back in and deal with the error msg with upgrade ?

---

### Post by Harry33 on 2011-05-11
> **cecilpierce said:**
> java ca-certificates removed, but i noticed on another install its still there and no problems ?
java ca-certificates removed some things but i haven't noticed anything wrong, YET!:confused:
should i put it back in and deal with the error msg with upgrade ?

[QUOTE=VinDSL]Hrm...
I removed ca-certificates-java some time ago. ca-certificates is still installed.
I just opened all the proggies that you listed (above) and they work fine.
AFAIK, its removal only affects icedtea.[/QUOTE]

Well well, the package you are talking about is not ca-certificates,
but ca-certificates-java (JKS keystore) instead.
That is totally another story.
Ca-certificates-java is only needed by openjdk-6-jre-headless and openjdk-7-jre-headless.
So generally it is not needed at all.

Sorry for the confusion.

---

### Post by Quackers on 2011-05-11
I just tried to remove ca-certificates-java and it said I needed to fix 2 broken packages first. There weren't any broken packages yesterday and I have updated since! Anyway I tried to fix them and got the pop-up below.
I'm not aware of any held packages :confused:

---

### Post by Harry33 on 2011-05-11
> **Quackers said:**
> I just tried to remove ca-certificates-java and it said I needed to fix 2 broken packages first. There weren't any broken packages yesterday and I have updated since! Anyway I tried to fix them and got the pop-up below.
I'm not aware of any held packages :confused:

What does Synaptic say?
From the lower left side,
choose "Custom Filters",
and then from upper left side,
choose "Broken".

---

### Post by Quackers on 2011-05-11
Nothing in there  (this is the gnome-shell version, but the unity one is the same).

---

### Post by Harry33 on 2011-05-11
> **Quackers said:**
> Nothing in there  (this is the gnome-shell version, but the unity one is the same).

Now that's odd.
What were the packages that were claimed to be broken?

---

### Post by Quackers on 2011-05-11
They were never named.
When I try to remove ca-certificates-java it says I must fix broken packages and synaptic says at the bottom of the screen that there are 2. 
I click on Edit > Fix broken packages and it says successfully fixed dependencies. (Maybe there's a better way to do this? )
Then I get the error in post #11.

---

### Post by Harry33 on 2011-05-11
> **Quackers said:**
> They were never named.
When I try to remove ca-certificates-java it says I must fix broken packages and synaptic says at the bottom of the screen that there are 2. 
I click on Edit > Fix broken packages and it says successfully fixed dependencies. (Maybe there's a better way to do this? )
Then I get the error in post #11.

Perhaps some dependency issues with the package ca-certificates.
Do you have openjdk-6-jre-headless or openjdk-7-jre-headless installed?
Just trying to figure out why do you have this package installed in the first place.

---

### Post by Quackers on 2011-05-11
Thanks for plugging away at this :-)
I have openjdk-6-jre-headless installed, which, as I haven't manually installed it, I assumed was installed with the ubuntu-restricted-extras package.

If I try to remove it, it wants to take all the iced tea packages with it (plus ca-certificates-java) but I don't know how that will affect things.

---

### Post by Quackers on 2011-05-11
Ok, an update.
I tried to remove openjdk-6-jre-headless and got the "need to fix broken package" thing again. I then went in to broken menu and there was one listed this time. 
access-java-bridge  something or other
so I searched for that package and removed the package. Went ok.
I then removed openjdk-6-jre-headless without a problem (it took with it all the icedtea packages plus ca-certificates-java. All went ok.
I have since updated again and got no error messages.
So, I'll mark this as solved, but I would like to know, please, what effect the icedtea packages removal will have, if any.
Thanks all :-)

---

### Post by Harry33 on 2011-05-12
> **Quackers said:**
> Ok, an update.
I tried to remove openjdk-6-jre-headless and got the "need to fix broken package" thing again. I then went in to broken menu and there was one listed this time. 
access-java-bridge  something or other
so I searched for that package and removed the package. Went ok.
I then removed openjdk-6-jre-headless without a problem (it took with it all the icedtea packages plus ca-certificates-java. All went ok.
I have since updated again and got no error messages.
So, I'll mark this as solved, but I would like to know, please, what effect the icedtea packages removal will have, if any.
Thanks all :-)

Icedtea-6-jre-cacao and icedtea-6-jre-jamvm are both alternatives to the Ubuntus default java (openjdk-6-jre) and to the openjdk-7-jre.
And icedtea-plugin is the java browser plugin for openjdk java.

I only use Sun-java and its web plugin (v. 6.24 from Natty partner repos), so I do not need any other java package.

---

### Post by VinDSL on 2011-05-12
> **Harry33 said:**
> Well well, the package you are talking about is not ca-certificates,
but ca-certificates-java (JKS keystore) instead.
That is totally another story.
Ca-certificates-java is only needed by openjdk-6-jre-headless and openjdk-7-jre-headless.
So generally it is not needed at all.[...]

Sorry for the confusion.
No problem...

To clarify, ca-certificates-java (JKS keystore) errors were popping up, every time I tried to install or update programs.

Basically, it was a OO showstopper for me.

As a matter of fact, I had a V hard time removing ca-certificates-java (JKS keystore), but...

As soon as ca-certificates-java (JKS keystore) and icedtea were removed from my OO install, it allowed me to go forward.

The next issue became perl not working correctly -- not allowing changes to gnome, and so forth, and so on.

Then there was the 'Launcher Thing' -- favorites not saving -- going back to default settings after reboot.

Heh!  I don't want to go OT.

Let's just say that I've already experienced enough breakage in OO to make me feel alive and reinvigorated!  

Mayhem and chaos are our best friends, no? :D

---

### Post by Quackers on 2011-05-12
> **Harry33 said:**
> Icedtea-6-jre-cacao and icedtea-6-jre-jamvm are both alternatives to the Ubuntus default java (openjdk-6-jre) and to the openjdk-7-jre.
And icedtea-plugin is the java browser plugin for openjdk java.

I only use Sun-java and its web plugin (v. 6.24 from Natty partner repos), so I do not need any other java package.

Thanks for that clarification Harry33. I wonder why ubuntu-restricted-extras install them. I feel better now :-)

---

### Post by coffeecat on 2011-05-12
> **Quackers said:**
> Thanks for that clarification Harry33. I wonder why ubuntu-restricted-extras install them. I feel better now :-)

Whatever the reason, I think the developers will be getting the message by now. I searched Launchpad and there are at least 7 different duplicate bug reports about this at the moment. :)

This link will probably show a different selection in a few hours, but fwiw:

[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=ca-certificates-java&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=ca-certificates-java&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

I must admit, I couldn't decide which one to do a me-too on!

---

### Post by Quackers on 2011-05-12
Lol, I suspect the message will get there :-)

---

### Post by SevenMachines on 2011-05-12
Is this the keystore multiarch incompatibilty bug? ignore if not but workaround for
```
$ sudo update-ca-certificates 
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
Exception in thread "main" java.security.ProviderException: Could not initialize NSS
    at sun.security.pkcs11.SunPKCS11.<init>(SunPKCS11.java:201)
    at sun.security.pkcs11.SunPKCS11.<init>(SunPKCS11.java:103)
   ....
....
    at sun.security.pkcs11.Secmod.initialize(Secmod.java:186)
    at sun.security.pkcs11.SunPKCS11.<init>(SunPKCS11.java:197)
    ... 31 more
E: /etc/ca-certificates/update.d/jks-keystore exited with code 1.
done.

```Which can cause dpkg to bail on setting up certificates, and also leads to a few 'cannot initialise nss' errors with apps such as eclipse

Hacky is to link the multiarch version to the old directory
```
$ dpkg -L libnss3 |grep libnss3.so
/usr/lib/x86_64-linux-gnu/libnss3.so
```It will be different for i386 obviously
```
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libnss3.so /usr/lib/libnss3.so
$ sudo update-ca-certificates 
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
done.
done.

```Temporary hack means package updates that update ca certificates should work now

---

