---
title: "Mono IDE won't start"
date: 2009-02-01
forum: Programming Talk
---

### Post by grognut on 2009-02-01
Hi All,

I've installed monodevelp on 8.04. It appears in the Application menu under Programming but when I click on it Starting Monodevelop appears in the task bar but then disappears.

There's obviously something inconsistant with my system. Is there a log I can look through to see an error message?

I have installed it from gb.archive.ubuntu.com/ universe
The other parts of mono I mono installed from badgerports.
I used gb.archive.ubuntu.com/ universe because I couldn't find the IDE in badgerports.

I this the correct method of install or have I missed something ie the IDE on badgerports.

Cheers

Grognut

---

### Post by user_none on 2009-02-01
Run it from a terminal so you can see any error messages.

```
$ monodevelop
```

---

### Post by grognut on 2009-02-01
Thanks user_one

Must remember to do that if I get future problems. That the benefit of forums!

$ monodevelop gave

```
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.
Waiting for Write add-in database lock
Waiting for Write add-in database lock
Waiting for Write add-in database lock
Waiting for Write add-in database lock
Waiting for Write add-in database lock
Waiting for Write add-in database lock

```

So the problem is a path.

So where is MOZILLA_FIVE_HOME and to what do I set it. 
Where do I look for this?

Cheers

Grognut

---

### Post by grognut on 2009-02-01
I've found libgtkembedmoz.so using locate.

It's in /usr/lib/thunderbird/libgtkembedmoz.so

Where is MOZILLA_FIVE_HOME set?

Cheers

grognut

---

### Post by directhex on 2009-02-01
I don't think the gluezilla thing is the problem - the mono.addins lock is

Try "rm -r ~/.config/MonoDevelop"

---

### Post by grognut on 2009-02-01
Hi 
I found the library and did

export MOZILLA_FIVE_HOME=/usr/lib/thunderbird

Now I get with $mono-develop

```
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: [MonoDevelop.Components,1.0.0] Could not load some add-in assemblies: The classes in the module cannot be loaded.
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: [MonoDevelop.Core.Gui,1.0.0] Could not load some add-in assemblies: The classes in the module cannot be loaded.
```

Any ideas for this one?

---

### Post by directhex on 2009-02-01
> **grognut said:**
> ```
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: [MonoDevelop.Components,1.0.0] Could not load some add-in assemblies: The classes in the module cannot be loaded.
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: [MonoDevelop.Core.Gui,1.0.0] Could not load some add-in assemblies: The classes in the module cannot be loaded.
```

Any ideas for this one?

Very odd. What does "gacutil -l gtk-sharp" say?

---

### Post by grognut on 2009-02-01
I think you found the problem 

bash: gacutil-l: command not found

Should this have been installed with monodevelop or separtely?

I've looked at synaptic it's not there as a separate package.

Cheers

---

### Post by grognut on 2009-02-01
Sorry typo


$gacutil -l gtk-sharp

The following assemblies are installed into the GAC:
Number of items = 0


Cheers

---

### Post by directhex on 2009-02-01
> **grognut said:**
> Sorry typo


$gacutil -l gtk-sharp

The following assemblies are installed into the GAC:
Number of items = 0


Cheers

Do you have libgtk2.0-cil installed?

---

### Post by grognut on 2009-02-01
Yes, it's got a green square against it in the packager manager.

Cheers

---

### Post by grognut on 2009-02-01
I should add that the error lines given above were the first few.

I get reams of errors but all seemed to bve based on gtk-sharp.

cheers

grognut

---

### Post by directhex on 2009-02-01
Ehm... something's broken your GAC

Try "dpkg-reconfigure mono-gac"

---

### Post by grognut on 2009-02-01
Thanks for you persistance.

results below

```
 dpkg-reconfigure mono-gac
* Installing 4 assemblies from libmono-addins0.2-cil into Mono
* Installing 2 assemblies from libmono-addins-gui0.2-cil into Mono
```

Didn't fix it though.

results of monodevelop


```
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
WARNING: [MonoDevelop.Components,1.0.0] Could not load some add-in assemblies: The classes in the module cannot be loaded.
Assembly not found: gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Assembly not found: .......
```

OK lets go to the beginning.

If I uninstall all mono related packages from ubuntu main and badgerport what do I need to install to:
run monodevelop ID
use mod-mono to use apache2
use mysql from mono.

Cheers

grognut

That's what I've being trying to get going for a month. No problems on debain etch but I don't want to a fresh install on my server.

---

### Post by directhex on 2009-02-01
> **grognut said:**
> Thanks for you persistance.

results below

```
 dpkg-reconfigure mono-gac
* Installing 4 assemblies from libmono-addins0.2-cil into Mono
* Installing 2 assemblies from libmono-addins-gui0.2-cil into Mono
```

Didn't fix it though.

Can you try reinstalling libgtk2.0-cil?

> If I uninstall all mono related packages from ubuntu main and badgerport what do I need to install to:
run monodevelop ID

install the "monodevelop" package

> use mod-mono to use apache2

install the "mono-apache-server2" package and "libapache2-mod-mono" package

> use mysql from mono.

install the libmysql5.0-cil package

---

### Post by grognut on 2009-02-01
Hi

reinstalling libgtk2.0-cil didn't fix it. Still doesn't work.

Is the monodevelop package in the badgerports. I couldn't find it so I've installed it from  gb.archive.ubuntu.com/universe which was in the list.

Is this correct

Cheers

grognut

---

### Post by directhex on 2009-02-01
> **grognut said:**
> Hi

reinstalling libgtk2.0-cil didn't fix it. Still doesn't work.

Is the monodevelop package in the badgerports. I couldn't find it so I've installed it from  gb.archive.ubuntu.com/universe.

Is this correct

Cheers

grognut

There's no badgerport because there's nothing newer available in Jaunty

---

### Post by grognut on 2009-02-01
Er...

I don't quite understand. I'm on Hardy.

Cheers

---

### Post by grognut on 2009-02-01
Thanks for all your help but I've spend far to much time on this.

I'm going to have to do a fresh install of my server but I think I'll use debian because I got this working on another machine in a few hours.

Cheers everybody.

grognut

ps I'd like to add that I'm not so impatient as to only spend one afternoon solving a problem. I've trying to get Mono with mon-mono on my server since Christmas and now it's time to changed tack.

---

### Post by directhex on 2009-02-01
> **grognut said:**
> Er...

I don't quite understand. I'm on Hardy.

Cheers

I don't have the time & energy to package things "from scratch" on badgerports - it's got packages from more recent releases such as Jaunty or Intrepid. No newer MD in those means no newer MD in badgerports

---

### Post by Keith Fox on 2010-06-12
This was a problem for me and this fixed it:
$ export MONO_GAC_PREFIX=/usr/local:/usr
$ monodevelop
 Took me tons of time of sifting through forums about this issue. Well it worked for me, and hope it does the same for you all too.

---

