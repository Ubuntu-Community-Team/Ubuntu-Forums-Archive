---
title: "cd space for ubuntu releases"
date: 2011-05-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2011-05-17
i have just read a article on the coming things in 11.10 and there seems to alot of we might make it default if there is enough cd space. 

why don't they make a dvd or usb version so they can include all the apps they want and not be restricted. 

they can still have cd version for the people who need it.

i think fedora has both cd and dvd versions why can't ubuntu. 

[http://www.webupd8.org/2011/05/expected-changes-in-ubuntu-1110-oneiric.html]("http://www.webupd8.org/2011/05/expected-changes-in-ubuntu-1110-oneiric.html")

---

### Post by An Sanct on 2011-05-17
Ubuntu also has both, CD and DVD versions ...

---

### Post by NormanFLinux on 2011-05-17
If you want everything distros like UE, Oz Unity, Primee17 and ZorinOS offer DVDs that give you more than a baseline install. 

The other extreme is outright minimalism... Bodhi Linux, QuinixiOS and Ubuntu minimal - all in a small CD package.

Depends on your tastes and needs.

---

### Post by Arla on 2011-05-17
> **NormanFLinux said:**
> If you want everything distros like UE, Oz Unity, Primee17 and ZorinOS offer DVDs that give you more than a baseline install. 

The other extreme is outright minimalism... Bodhi Linux, QuinixiOS and Ubuntu minimal - all in a small CD package.

Depends on your tastes and needs.

Ideally I'd like a minimal install that has a graphical user interface, i.e. has Gnome, and has all the things needed for Gnome to function (wireless management, that kind of stuff) but doesn't have all the actual programs, that to my mind with be the ideal solution to a lot of people since it lets them really customise the programs installed, but without the hassle of having to install from command line to get a working graphical OS.

---

### Post by Yeeha on 2011-05-20
Actually usb memorystick would be very good solution because:

1. You can use it as livecd with storage space. 
2. If ubuntu devs would develop software to sync usb with real installation, then updates would be downloaded only once, even if you have multiple computers or do format. Which would save bandwith for user and updates servers. And if syncing would also sync user files if wanted, format or buying new computer would be very convinient.

---

### Post by dino99 on 2011-05-20
the miniiso is still available :)

---

### Post by An Sanct on 2011-05-20
Miniiso? Like 180mb, the small CD?

If so, please point me to the location :) I have a few spare mini CDs and they are great to impress people :) Many don't even know why there is a smaller circle inside their optical drives tray :)

---

### Post by dino99 on 2011-05-20
> **An Sanct said:**
> Miniiso? Like 180mb, the small CD?

If so, please point me to the location :) I have a few spare mini CDs and they are great to impress people :) Many don't even know why there is a smaller circle inside their optical drives tray :)

Only for you my dear:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

:) :) :)

---

### Post by cariboo on 2011-05-20
The miniiso just contains enough packages to do a net install, it uses the same text based installer as the Alternate install CD.

---

### Post by ranch hand on 2011-05-21
> **An Sanct said:**
> Miniiso? Like 180mb, the small CD?

If so, please point me to the location :) I have a few spare mini CDs and they are great to impress people :) Many don't even know why there is a smaller circle inside their optical drives tray :)
Not quite 180Mb is it?

Really a great way to install.

---

### Post by An Sanct on 2011-05-21
No, as far as I could see, I have not seen any package larger than 35Mb ...

---

### Post by jerrylamos on 2011-05-21
Ankle biter for me is almost guaranteed early Oneiric images will be TOO BIG TO FIT ON A CD judging from most previous Alpha & Beta builds.  

I've got test pc's which run Ubuntu very well thank you but don't boot from USB.

Easy fix, if image is too big to fit on CD then dump something off the image which could be easily loaded from the net, such as games or even Libre Office.

Mini .iso is not usually available at Alpha and Beta time so testing on some pc's is not reasonable.

For about 2 months, Natty wouldn't install on this new Acer Aspire One netbook which is quite quick.  Natty install from USB was busted only way I could test was to install from hard disk .iso image onto a USB hard drive - it's plenty big enough at 100 GB but Grub 2 boot was nearly hopelessly confused with install on one fast 3.3 GHZ fast pc and then boot on the netbook.  Luckily it didn't screw up the multiboot on the netbook with sluggish Windoze 7 still on it.

Obvious conclusion Ubuntu Development was not interested in us testing Natty Alpha and Beta on pc's that wouldn't boot from USB.

Jerry

---

### Post by julianb on 2011-05-22
Oneiric images don't fit on a CD, and your computer won't boot from USB?

Try this:
[http://www.wikihow.com/Boot-an-Ubuntu-Iso-from-Your-Hard-Drive](http://www.wikihow.com/Boot-an-Ubuntu-Iso-from-Your-Hard-Drive)

I think you can also point GRUB2 (the GRUB2 that is on your hard drive, that is) to boot an ISO which is on your USB drive.

---

### Post by ranch hand on 2011-05-22
> **julianb said:**
> Oneiric images don't fit on a CD, and your computer won't boot from USB?

Try this:
[http://www.wikihow.com/Boot-an-Ubuntu-Iso-from-Your-Hard-Drive](http://www.wikihow.com/Boot-an-Ubuntu-Iso-from-Your-Hard-Drive)

I think you can also point GRUB2 (the GRUB2 that is on your hard drive, that is) to boot an ISO which is on your USB drive.
Grub will boot an ISO.  The ISO must be on your / partition.  If you have a 2 partition install yo will have to move it somewhere from the /home partition.

I create a directory /etc/aa just for that.  It puts the buggers where I can see them easily when working on grub.

As this is a pre-release there may be problems with it booting this way but Ubuntu is getting pretty good at having them boot.  It is kind of nice to  be able to do this even if you intend to put it on some other media.

If the ISO will even try to boot from grub it will pretty much act like it will on other media.  No real sense in putting it somewhere else if it will not boot completely.  If you need to edit the instruction string you can work that out before using it on a usb device or disk.

---

### Post by AlphaLexman on 2011-05-22
I (vaguely) remember programs on floppy discs which had a **program disc** and a **data disc**!

Could it be possible to have the liveCD split into two discs? Maybe a **boot disc** (which would load into memory) and a **data/program disc**?

The user would have to switch discs during the boot process, but it would allow more features and options.

---

### Post by An Sanct on 2011-05-23
yea, well ... its 32MB ... and terminal install ... people get screamish when they see teminal ...

---

### Post by An Sanct on 2011-05-23
> **AlphaLexman said:**
> I (vaguely) remember programs on floppy discs which had a **program disc** and a **data disc**!

Could it be possible to have the liveCD split into two discs? Maybe a **boot disc** (which would load into memory) and a **data/program disc**?

The user would have to switch discs during the boot process, but it would allow more features and options.

Go "[Turbo Linux]("http://www.turbolinux.com/")" :)

edit: added link :) a friend of mine made it possible...

---

### Post by satanselbow on 2011-05-23
> Mini .iso is not usually available at Alpha and Beta time so testing on some pc's is not reasonable.

It most certainly is! Running a G3S Oneiric built from it and the ppa as I type ;)

---

### Post by cariboo on 2011-05-23
> **satanselbow said:**
> It most certainly is! Running a G3S Oneiric built from it and the ppa as I type ;)

Could you give use a link, as I just looked, and there isn't a mini iso for Oneiric yet, in the normal place.

---

### Post by lucazade on 2011-05-23
> **cariboo907 said:**
> Could you give use a link, as I just looked, and there isn't a mini iso for Oneiric yet, in the normal place.

Cariboo, here is it:
[http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/mini.iso)

it is still hidden in the wiki page, so it is enough to change "natty" in "oneiric" in .iso url
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

