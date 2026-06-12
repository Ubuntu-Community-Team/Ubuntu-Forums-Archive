---
title: "how to active sync with my windows mobile pda ?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-07-30
how can i active sync my sprint htc touch pda with ubuntu ? i thought i needed windows mobile active sync for this ? is there a guide or instructions on how to do this ? :confused:

---

### Post by pavel989 on 2008-07-30
i already tried a few times. its not easy if possible, which i doubt it is.

---

### Post by smooth3006 on 2008-07-30
yeah, someone just told me on another forum that windows mobile 6.1 which is on my device won't work with ubuntu right now. i guess ill have to keep dual booting with my vista install for the moment. :(

---

### Post by pormogo on 2008-07-30
> **smooth3006 said:**
> yeah, someone just told me on another forum that windows mobile 6.1 which is on my device won't work with ubuntu right now. i guess ill have to keep dual booting with my vista install for the moment. :(

I've been trying to get my windows mobile 6.1 device (HTC 6800 on sprint) to sync with ubuntu (or any virtualized OS under Ubuntu) for some time with absolutely no success at all. Below is a thread I made asking how to get Active Sync going in Virtual Box. I'm still in basically the same place with that one. 

[http://ubuntuforums.org/showthread.php?p=5492329#post5492329](http://ubuntuforums.org/showthread.php?p=5492329#post5492329)

I hope you have better luck then I have had.

---

### Post by smooth3006 on 2008-07-31
so no one has had any luck syncing a windows mobile 6 pda with ubuntu ? :confused:

---

### Post by smooth3006 on 2008-08-01
since i have no further responses i take it this can't happen ? could this issue be forwarded to the ubuntu developers so they can get it working in the near future ? the pda i want to sync is a "sprint htc touch".

---

### Post by matikz on 2008-08-01
Yeah I've been trying for awhile to sync my HTC PPC-6800(Mogul). I got the ICS features to work but syncing is a whole other matter. If anyone has any information at all it would be great. This is one of the few things still keeping me teathered to Windows.

---

### Post by smooth3006 on 2008-08-01
> **matikz said:**
> Yeah I've been trying for awhile to sync my HTC PPC-6800(Mogul). I got the ICS features to work but syncing is a whole other matter. If anyone has any information at all it would be great. This is one of the few things still keeping me teathered to Windows.

same here, well that and some of the games i play.

---

### Post by rocka on 2008-08-26
yes, I'm in the same boat on this one.
I have a HTC Tytn II, and neither HTC or Three support anything other than XP/Vista.

The thing is, it's got wifi and bluetooth, why can't I just transfer the files using either of those ?

---

### Post by pavel989 on 2008-08-28
thats not the problem. the problem si reading the files, as in the pim file and so forth. but also, ever notice that sometimes u need active sync to install programs?

---

### Post by philinux on 2008-08-28
Can't solve the problem, but here's the place to post.

[http://ubuntuforums.org/forumdisplay.php?f=306](http://ubuntuforums.org/forumdisplay.php?f=306)

---

### Post by scorp123 on 2008-08-29
> **smooth3006 said:**
>  could this issue be forwarded to the ubuntu developers so they can get it working in the near future ? Sure, if you could get Microsoft to tell the developers how this secret closed-source protocol is supposed to work? :)

[http://en.wikipedia.org/wiki/Activesync](http://en.wikipedia.org/wiki/Activesync)

> ActiveSync is a desktop synchronization program developed by Microsoft, as well as an unrelated push messaging component for Exchange Server. ... 

Your best bet would be "SyncE" ... they are trying to reverse-engineer the protocol so it would work on Linux too:
[http://www.synce.org](http://www.synce.org)

---

### Post by scorp123 on 2008-08-29
Detailed instructions for SynCE on Ubuntu:
[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

No guarantees that it will work with your device though .. As I wrote above: It's a Microsoft protocol which they only released for Microsoft OS's.

---

### Post by wolfie2x on 2008-08-29
I don't have WM6 but I did manage to get WM2003 to sync properly. The steps would be the same to start with I guess..

main guide:  [http://ubuntuforums.org/showthread.php?t=30936]("http://ubuntuforums.org/showthread.php?t=30936")


here is the script I use for starting sync.

// ----- ppc-sync ----
#!/bin/bash
dccm
sleep 1
sudo synce-serial-start
sleep 3
multisync


posting your terminal output will give others a better chance of helping you.

---

### Post by smooth3006 on 2008-09-05
i may try that synce guide that you posted, does anybody know if this will work with a sprint htc touch ?

---

### Post by smooth3006 on 2008-10-04
have there been any movements to active sync a htc touch/ windows mobile based pda with ubuntu ? will ubuntu 8.10 support this ?

---

### Post by roger_1960 on 2008-10-04
Hi all

Not exactly syncing, but if you install WM5torage onto you windows PDA you should be able to connect to a linux PC as a USB drive and then copy to/from it using file manager. (can be found on [http://wm5torage.en.softonic.com/windowsmobile](http://wm5torage.en.softonic.com/windowsmobile) )

---

### Post by smooth3006 on 2008-10-04
> **roger_1960 said:**
> Hi all

Not exactly syncing, but if you install WM5torage onto you windows PDA you should be able to connect to a linux PC as a USB drive and then copy to/from it using file manager. (can be found on [http://wm5torage.en.softonic.com/windowsmobile](http://wm5torage.en.softonic.com/windowsmobile) )

not sure if this will work with my pda ? i hope someday soon we will be able to fully sync with ubuntu.

---

### Post by gwbennett on 2008-10-07
To active sync with VirtualBox within windows go to settings, connections, usb to pc, then uncheck the 'advanced functionality' box.

then when you plug the device into the linux computer, pass it through to the virtual machine from the usb menu in virtual box and use MS activesync.

to share the internet connection from wm6.1, you have to install a registry editor and change the key that says phone as modem to sprint pcs since the dropdown box no longer exists.

---

### Post by WSiaB on 2008-11-06
I have been using OggSync to use Google as an intermediary.  This doesn't allow transferring files to/from the smartphone (a Sprint HTC) but does allow the syncing of email, contacts and calendar with the bonus of being able to access them from other machines on the Google Web Site.  This is just another approach to this problem.

On another related note, does anyone know how I can replace this piece of #$%^ Windows Mobile with a linux OS? I don't want to break the phone, but it barely works now anyways (freezes so I don't receive phone calls until I remove & replace battery)!

---

### Post by jalito27 on 2008-11-13
Hi, sorry for my englis, but I{d solve the ******* trouble with my HTC Touch with that tutorial:

[http://bide-sinergico.blogspot.com/2008/09/sincronizar-htc-diamond-con-evolution-o.html]("http://bide-sinergico.blogspot.com/2008/09/sincronizar-htc-diamond-con-evolution-o.html")

For me are the only way that I'd found it.

Good Luck for everyone

Jalito27
I HATE WINDOWS IN ALL VERSIONS

---

### Post by smooth3006 on 2008-11-15
> **jalito27 said:**
> Hi, sorry for my englis, but I{d solve the ******* trouble with my HTC Touch with that tutorial:

[http://bide-sinergico.blogspot.com/2008/09/sincronizar-htc-diamond-con-evolution-o.html]("http://bide-sinergico.blogspot.com/2008/09/sincronizar-htc-diamond-con-evolution-o.html")

For me are the only way that I'd found it.

Good Luck for everyone

Jalito27
I HATE WINDOWS IN ALL VERSIONS

^ can someone translate that link to english ? :confused:

---

### Post by pavel989 on 2008-11-16
Google translate! itll translate whole webpages, just put in a link

---

### Post by Nick_Djinn on 2010-05-09
> **WSiaB said:**
> On another related note, does anyone know how I can replace this piece of #$%^ Windows Mobile with a linux OS? I don't want to break the phone, but it barely works now anyways (freezes so I don't receive phone calls until I remove & replace battery)!

I would love to know this as well...also if there are hardware upgrades that a phone tech could perform.

---

### Post by pavel989 on 2010-05-12
depends on the phone. there are very large projects to port linux to windows mobiles.

i got a linux os to run on my palm t|x

i got a tmo mda (htc wizard i think) lieing around somewhere that i wanted to put linux on, but never found a confirmed working project for it. but there is a project nevertheless

---

### Post by Nick_Djinn on 2010-05-13
It would be awesome if I could run Ubuntu....but I dont want to run it as a non native...I only have 400mhrz processor, and 64mb RAM + 256 ROM....not really going to do well with a non native environment.


And I need touch screen support. Ubuntu mobile or Moblin might be possible....but what happened to these projects?

---

