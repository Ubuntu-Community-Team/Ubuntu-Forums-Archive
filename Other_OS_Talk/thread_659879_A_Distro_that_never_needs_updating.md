---
title: "A Distro that never needs updating"
date: 2008-01-06
forum: Other OS Talk
---

### Post by darrelljon on 2008-01-06
Am I alone in finding the concept of an operating system that never needs updating (for as long as you keep the same hardware) appealing?

---

### Post by mips on 2008-01-06
I'm not sure I understand where you are going with this but I will try anyway.

You will never find such a distro as far as I'm concerned. Don't you even want the security updates ?

You can take ANY distro and not update it, that choice is yours. Just leave it and disable the update notifier and you will be blissfully unaware of available updates.

Edit:
PS. The same goes for Windows, OSX and whatever else is out there.

---

### Post by darrelljon on 2008-01-06
I just don't like my system suddenly experiencing incompatibilities or slowing down because features I didn't want have been added. Operating systems in the past never seemed to have needed updating as much as we are told they do today.

---

### Post by allforcarrie on 2008-01-06
just dont update it....

---

### Post by ugm6hr on 2008-01-06
> **darrelljon said:**
> I just don't like my system suddenly experiencing incompatibilities or slowing down because features I didn't want have been added.

To achieve this in Ubuntu:
System->Administration->Software Sources
Updates tab
Under "Ubuntu updates", just untick everything *except* Important Secutrity Updates.

That way, nothing will be updated except for security updates.  At least that way you'll be protected, but it won't suggest any cosmetic / feature based updates.

As mentioned, you could just turn all updates off, but it would be equivalent to running Windows 95 on the web (i.e. not advisable) after about 10 years.

---

### Post by mips on 2008-01-06
> **ugm6hr said:**
> 
As mentioned, you could just turn all updates off, but it would be equivalent to running Windows 95 on the web (i.e. not advisable) after about 10 years.

Does one still get updates for Win95?

---

### Post by ugm6hr on 2008-01-06
> **mips said:**
> Does one still get updates for Win95?

No - that's the point.  

If you turn off all security updates for any OS (voluntarily or due to lack of support), you are left open to all kinds of security vulnerabilities.  Nevertheless, there are still people out there connecting to the internet with Win95/98....

---

### Post by kellemes on 2008-01-06
> **darrelljon said:**
> Am I alone in finding the concept of an operating system that never needs updating (for as long as you keep the same hardware) appealing?


Yes and no, that's why I fall for rolling release.. I'm running Arch and Debian on a couple of machines..
I update almost every day, but only small amounts of packages, and critical packages (xorg, kernel, certain drivers etc..) I update only with the knowledge crap can happen, hardly ever happens by the way.
Anyway, never I'll have the amounts of trouble people *can* have upgrading the hole freaking system in one go.

Listen, you may not change your hardware.. but you also want your hardware to be performing the best it can, for this you'll have to be upgrading sooner or later.
Still, as some already said.. you don't have to update at all.

Man, isn't GNU/Linux great?! So much freedom, so many choices!
:popcorn:

---

### Post by Darkhack on 2008-01-06
> **darrelljon said:**
> I just don't like my system suddenly experiencing incompatibilities or slowing down because features I didn't want have been added. Operating systems in the past never seemed to have needed updating as much as we are told they do today.

You'll be best suited for a LTS (Long Term Support) release.  All Ubuntu variants of version 6.06 are LTS and are supported until June 2009 and the upcoming 8.04 release will be supported until April 2011 (with the exception of Kubuntu due to the KDE 4 release).  That's 3 years of desktop support on an LTS and a standard Ubuntu release has 18 months of support.

If you are willing to pay for such service, SUSE has support for up to 5 years and Red Hat offers support for 7 years.

Also, by support, I mean they (at the minimum) offer security patches.  Phone support or web documentation and all that jazz doesn't count.  I've yet to find an OS that has security patches for products older than 7 years.

---

### Post by darrelljon on 2008-01-06
Aren't there any operating systems that are completely secure when released?

---

### Post by HotShotDJ on 2008-01-06
> **darrelljon said:**
> Aren't there any operating systems that are completely secure when released?No.

---

### Post by ugm6hr on 2008-01-06
> **darrelljon said:**
> Aren't there any operating systems that are completely secure when released?

Even if there were, malicious hackers would find a way to circumvent those security measures.  Hence updates.  And also why virus definitions get updated etc.

---

### Post by SunnyRabbiera on 2008-01-06
> **darrelljon said:**
> Aren't there any operating systems that are completely secure when released?

sadly no, there will always be hackers, scammers and net crooks out there.
there is no 100% secure in the computer world, especially if you use the net.
really the only way to keep a computer 100% safe is to never hook it up to the net.
The only system I know about that is close to what you want is BSD, perhaps the most secure OS you can find in the commercial market.
by far it runs circles around linux in terms of security, but even it has its flaws.
but then again linux by far is a million times more secure then windows, so is OSX

---

### Post by mips on 2008-01-06
> **darrelljon said:**
> Aren't there any operating systems that are completely secure when released?


Well, if you remove the floppy drive, cd-rom, disable usb ports, disconnect it from any networks and lock it in a vault it should be pretty secure but also pretty useless at the same time.

---

### Post by Calash on 2008-01-06
It just cannot exsist anymore.  Older operating systems did not have these issues because they were not connected to the internet.  You could go years without updating DOS, or even Windows 3.1.  But now...there is no way to secure an operating system when the end user demands interconnectivity between computers.


So, if you want to be 100% secure and never update....just unplug the cable from the wall.  Other than that you will not find what you are looking for.  Linux is close, but flaws are still found in the code, that is why you get updates.

---

### Post by mips on 2008-01-07
> **SunnyRabbiera said:**
> 
The only system I know about that is close to what you want is BSD, perhaps the most secure OS you can find in the commercial market.
by far it runs circles around linux in terms of security, but even it has its flaws.


When it comes to security [OpenBSD]("http://openbsd.org/") stands out. They still release a new version every six months though but they concentrate more on code revision, security, than adding fancy features to it.

[http://openbsd.org/](http://openbsd.org/)

It's also a relatively lightweight system which is nice. If you are interested I suggest you read the faq, documentation, mailing-lists & bsd forums as you might get RTFM responses when you ask a 'silly' question but generally the folk are kind and helpfull.

They release patches for security updates and there aren't that many to be honest, [http://openbsd.org/errata41.html](http://openbsd.org/errata41.html) is a list of all 11 patches for version 4.1

---

### Post by Jhongy on 2008-01-07
The OP is confusing updates and upgrades.

The regular updates don't add any new features -- they just provide security updates, bugfixes, etc. When a new Ubuntu is released, you don't have to upgrade to it -- the update manager has an "upgrade" button you specifically have to click.

Ubuntu doesn't need upgrading -- just don't click that button. The updates, however, as everyone else is pointing out, are necessary. But they don't usually add "new features" as you are claiming.

There's no real issue here that I can see.

---

### Post by Swmmrman on 2008-01-07
> **darrelljon said:**
> Aren't there any operating systems that are completely secure when released?

Even the old OSes had holes.  Just with no net conection for attacks/viruses to come in on.  They couldnt be found.  And viruses did exists clear back in dos 5.0.  But they wernt in the wild.(No internet)  So no patches/updates were needed.  I  find ubuntu to have very few patches/updates.  Maybe once a week i get a little pop up.  I go in update.  And the end result is it runs better(Cept when wine broke one of my games) 

Guess what im getting at is this.  No matter how good it is made out of the box.  Hackers have nothing better to do then pick holes in it.  The only way an os could be 100% secure for ever.  Is no power to the computer.  Cant power on.  Cant get viruses.

---

