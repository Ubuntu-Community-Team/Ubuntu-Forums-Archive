---
title: "You might want to defer updates for a few hours."
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-09-16
Synaptic removed flashplugin in my laptop Oneiric (and a lot else) during a moment of inattention for which I blame only myself. On my desktop:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  cpp-4.6 gcc-4.6 gcc-4.6-base libgcc1 libgomp1 libquadmath0 libstdc++6
The following packages will be upgraded:
  apt apt-transport-https apt-utils friendly-recovery grub-common grub-pc
  grub-pc-bin grub2-common initramfs-tools initramfs-tools-bin libapt-inst1.3
  libapt-pkg4.11 liblightdm-gobject-1-0 libncurses5 libncursesw5 libtinfo5
  lightdm ncurses-base ncurses-bin oneconf upstart
21 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 5,921 kB of archives.
After this operation, 36.9 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
```

```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  flashplugin-downloader:i386 flashplugin-installer gcc-4.6-base:i386
  libasound2:i386 libatk1.0-0:i386 libavahi-client3:i386 libavahi-common3:i386
  libc6:i386 libcairo2:i386 libcomerr2:i386 libcups2:i386 libcurl3:i386
  libdatrie1:i386 libdb5.1:i386 libdbus-1-3:i386 libexpat1:i386 libffi6:i386
  libfontconfig1:i386 libfreetype6:i386 libgcc1:i386 libgcrypt11:i386
  libgdk-pixbuf2.0-0:i386 libglib2.0-0:i386 libgnutls26:i386
  libgpg-error0:i386 libgssapi-krb5-2:i386 libgtk2.0-0:i386 libice6:i386
  libidn11:i386 libjasper1:i386 libjpeg62:i386 libk5crypto3:i386
  libkeyutils1:i386 libkrb5-3:i386 libkrb5support0:i386 libldap-2.4-2:i386
  libnspr4:i386 libnspr4-0d:i386 libnss3:i386 libnss3-1d:i386
  libpango1.0-0:i386 libpcre3:i386 libpixman-1-0:i386 libpng12-0:i386
  librtmp0:i386 libsasl2-2:i386 libsasl2-modules:i386 libselinux1:i386
  libsm6:i386 libsqlite3-0:i386 libssl1.0.0:i386 libtasn1-3:i386 libthai0:i386
  libtiff4:i386 libuuid1:i386 libx11-6:i386 libxau6:i386 libxcb-render0:i386
  libxcb-shm0:i386 libxcb1:i386 libxcomposite1:i386 libxcursor1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxft2:i386
  libxi6:i386 libxinerama1:i386 libxrandr2:i386 libxrender1:i386 libxt6:i386
  nspluginviewer:i386 nspluginwrapper zlib1g:i386
The following packages will be upgraded:
  apt apt-transport-https apt-utils cpp-4.6 friendly-recovery gcc-4.6
  gcc-4.6-base grub-common grub-pc grub-pc-bin grub2-common initramfs-tools
  initramfs-tools-bin libapt-inst1.3 libapt-pkg4.11 libgcc1 libgomp1
  liblightdm-gobject-1-0 libncurses5 libncursesw5 libquadmath0 libstdc++6
  libtinfo5 lightdm ncurses-base ncurses-bin oneconf upstart
28 upgraded, 0 newly installed, 75 to remove and 0 not upgraded.
Need to get 18.8 MB of archives.
After this operation, 51.8 MB disk space will be freed.
Do you want to continue [Y/n]? n
```

:-s

And:

```
$ sudo aptitude safe-upgrade
Resolving dependencies...                
Unable to resolve dependencies for the upgrade: no solution found.
Unable to safely resolve dependencies, try running with --full-resolver.

```

Synaptic wants to do what apt-get dist-upgrade wants to do and, predictably, update-manager is offering a partial upgrade. Oh no, you don't!

I think I'll leave it till the morning. :)

---

### Post by flipper T on 2011-09-16
good heads-up, thx

now lets sit back & watch as it is widely ignored :)

---

### Post by rtalcott on 2011-09-16
Thank You!  I think I'll wait this out but it may be an entertaining wait!

rt

---

### Post by Quackers on 2011-09-16
Wow, I've been lucky. I must have updated just before this calamity :-)
Will be keeping an eye out!
Thanks CC

---

### Post by IWantFroyo on 2011-09-16
Thanks!

Wow. That really is weird.

---

### Post by ft_ on 2011-09-16
ah ah ah, too late.
Muon screwed me, I did not see that there was, this time, some useful packages to remove.

As a result, the removal of zlib1g and zlib1g:i386.
Delightful, as dpkg and apt-get depends on them with libz.so.1 .
I had to copy this library (thanks to "locate" and to the SAGE math software wich is all-inclusive) to recover my system...

Now 32-bit softwares do not work, wait for updates...

---

### Post by coffeecat on 2011-09-16
Actually, looking at that list a bit more closely, I don't know what all those i386 libraries are doing on a 64-bit system. Whatever, I don't like having my flash plugin snaffled from under my nose. :) So I'll still wait it out for a bit.

---

### Post by sammiev on 2011-09-16
Hmmm never got that update and updated just before reading this thread.

---

### Post by Quackers on 2011-09-16
I've just updated through synaptic (mostly ncurses updates) and nothing was listed as wanting to be removed. Maybe the suspect package(s) have been removed?

---

### Post by coffeecat on 2011-09-16
> **Quackers said:**
> I've just updated through synaptic (mostly ncurses updates) and nothing was listed as wanting to be removed. Maybe the suspect package(s) have been removed?

Are you running 32-bit or 64-bit. Also, which server? I'm on the main server ever since the UK server was several hours behind in syncing with the main server about a week or so ago. Perhaps this hasn't hit the regional servers yet!

---

### Post by Quackers on 2011-09-16
I'm on 64 bit and main server.

---

### Post by coffeecat on 2011-09-16
No. Just did a reload with the main server and then the UK server. With each it still wants to take out all those packages.

Forgot to ask:

> **Quackers said:**
> Maybe the suspect package(s) have been removed?

Have you still got flash? :p

---

### Post by Quackers on 2011-09-16
Actually no :-)
But I do have FlashAid

---

### Post by coffeecat on 2011-09-16
All very curious. It may be that the i386 libraries can be safely removed, but the aptitude safe-upgrade output definitely suggests that all is not right. I now have two systems: laptop where all that stuff was removed, and desktop where I've deferred. It's about 11:30pm here atm. I'll check both systems in the morning and see what happens.

---

### Post by sammiev on 2011-09-16
Using Flash-Aid on a 64 bit system and I'm on the Canadian server.

---

### Post by Quackers on 2011-09-16
Curiouser and curiouser!
Speak tomorrow

---

### Post by Rocksinboxes on 2011-09-16
Synaptic for me seems to also do a good job of resolving dependencies. It's been the only way that for me has consistently worked.

---

### Post by ronacc on 2011-09-16
I'm 64 bit here and on the US server , just updated and the 386 lib's were removed . I do not use the flash plugin installer but hand install the 64bit player directly from adobe . As far as I can see there is no effect ( at least not that I've found yet ) of removing the 386 libs and my hand installed flash is still functional .

---

### Post by garvinrick4 on 2011-09-16
@sammiev
> Hmmm never got that update and updated just before reading this thread. Could be your mirror is not up to date one. Here is a list of Mirrors.
Check to see if yours is up to date.

[Mirrors of Ubuntu : Ubuntu]("https://edge.launchpad.net/ubuntu/+archivemirrors")

---

### Post by DogMatix on 2011-09-16
Just updated no such trauma for me. 

Although on another day with a dev. dist. who knows?

---

### Post by ventrical on 2011-09-16
All is well here. No glitches at all. 32 bit Intel Desktop working like a charm.

---

### Post by ventrical on 2011-09-16
Belay my last. I just hard booted and  the last update foobarred Unity 3D all the way to the south pole :(

sheesh .. oh the joy of beta :)

---

### Post by sammiev on 2011-09-16
> **garvinrick4 said:**
> @sammiev
 Could be your mirror is not up to date one. Here is a list of Mirrors.
Check to see if yours is up to date.

[Mirrors of Ubuntu : Ubuntu]("https://edge.launchpad.net/ubuntu/+archivemirrors")

Tried another update and noticed 2 updates for other items. Check my Flash and all is still good.

---

### Post by rtalcott on 2011-09-16
Just updated...64 bit...US Server...all is well.
rt

---

### Post by coffeecat on 2011-09-17
Update UK approx 10.10 local UK time.

The UK server is out of sync at the moment.

Desktop - downloading from main server. This was the machine I deferred the updates about 9 hours ago. Did a reload of the metadata in Synaptic, after which it did an update of a dozen or more packages without wanting to take anything out. I still have flash!

Laptop - it was set to download from UK server last night. Did an apt-get update this morning and then apt-get install flashplugin-installer, but got a dependency error. Tried installing flashplugin-installer from Synaptic, but Synaptic wanted to take out an enormous list of packages including most of libre-office for some reason. Also lshw! :-k So I set the server to the main one, did a reload and this time when marking flashplugin-installer for installation it marked for installation all the i386 packages it had taken out last night plus a couple of others. All well now.

Conclusion - main server is OK at the moment, but not the UK server. What is odd is that some people were OK with the main server last night (my time) when the main server was wanting to do the same damage on my desktop system that the UK server had already done on my laptop.

I don't think I'll worry about it too much though. Onward and upward! :)

---

