---
title: "[SOLVED] Data recovery...need lightweight OS"
date: 2008-01-04
forum: Other OS Talk
---

### Post by twin_57103 on 2008-01-04
I'm trying to recover some old photographs from a Windows 98 /500 MHz computer.  It has USB, but I have had no luck with my flash drive.  It also has no burner or network card.

I tried my Ubuntu disk to see if I could boot and access my flash drive.  Not surprisingly, it didn't work well.  Yes, I know that this is far too heavy an OS for this computer - but I had the disk and it was worth a try.

I have not worked wtih any of the smaller/lighter distros before, but I'm hoping for something that will run from a floppy or CD that will allow me to mount my flash drive and copy files off.  Command-line only is OK - all it needs is to support my Sandisk Cruzer flash drive (which works well under Ubuntu).

Any suggestions?
Thanks!!!

---

### Post by benuski on 2008-01-04
I would try Damn Small Linux... I used it for exactly that sort of thing, and it worked just fine.

---

### Post by Antman on 2008-01-04
Try either [Puppylinux]("http://distrowatch.com/table.php?distribution=puppy&a=1") or [Damn Small Linux]("http://distrowatch.com/table.php?distribution=damnsmall&a=1").

---

### Post by twin_57103 on 2008-01-04
Got DSL downloading.  Thanks for the suggestion.  I've used this trick with an Ubuntu CD successfully on other similar-spec machines (do something else and come back to it half an hour later), but this one just didn't like it.

---

### Post by twin_57103 on 2008-01-05
OK...tried DSL and couldn't really figure it out.  If I took the time I might sort it out, but ended up downloading Puppy Linux instead.  It seems more straightforward to me (sorry, I'm still a Windows user at heart, but gradually getting better at Linux).

I got my flash drive to mount pretty easily, but I'm having a hard time finding the hard drive.  In the drive mounter, I get the CD-ROM and two drives for my flash drive (for some reason this U3 drive always mounts as a CD and another drive, but it does that on every computer).  There's no option for the hard drive  I've nosed around the file manager, but not found it there, either.

Sorry to be so dense, but would you help me find the hard drive?  That will let me get these files off!

---

### Post by elithrar on 2008-01-05
Burn a [Knoppix](http://knoppix.com/) (Live CD-based distro) for these kind of things. It should detect your Windows HDD once it's booted and you then should be able to pull files off it.

---

### Post by lisati on 2008-01-05
If Windows is still in a usable condition, something similar to [http://www.dse.co.nz/cgi-bin/dse.storefront/477f390d00d49b58273fc0a87f3306b2/Product/View/XH8177](http://www.dse.co.nz/cgi-bin/dse.storefront/477f390d00d49b58273fc0a87f3306b2/Product/View/XH8177)  might be useful for establishing a temporary "no frills" network

---

### Post by D-EJ915 on 2008-01-05
I popped linux mint XFCE into my P-III 550 the other day to look at a drive and it worked great

---

### Post by darrelljon on 2008-01-05
+1 for Puppy

---

### Post by new2*buntu on 2008-01-05
+1 for Puppy, but couldn't you take out the hard drive and put it into another computer?

---

### Post by Sukarn on 2008-01-05
> **new2*buntu said:**
> +1 for Puppy, but couldn't you take out the hard drive and put it into another computer?

My thoughts exactly, or are you not used to opening the case of your computer? If that is the case then you can get a friend to disconnect the hard drive from the old computer and connect it to your newer one.

---

### Post by twin_57103 on 2008-01-05
> **D-EJ915 said:**
> I popped linux mint XFCE into my P-III 550 the other day to look at a drive and it worked great

I tried Ubuntu, which has worked for me for things like this before, but this particular computer just didn't like it.

> **lisati said:**
> +1 for Puppy, but couldn't you take out the hard drive and put it into another computer?

Actually, I'm very comfortable working with hardware.  I thought this might be a simple alternative (15-minute downloads, walk away & do something else in the meantime), which it has not.  However, it's been a good learning experience, which is worth the time.  I may yet try Knoppix.

My own computer has 2 SATA hard drives and while it would take another IDE drive, I'd been trying to avoid that.  I have a friend with a spare older system I can use if I can ever get over there when he is home, which is rare.  That has always been plan C.

> **lisati said:**
> If Windows is still in a usable condition, something similar to [http://www.dse.co.nz/cgi-bin/dse.sto...ct/View/XH8177](http://www.dse.co.nz/cgi-bin/dse.sto...ct/View/XH8177) might be useful for establishing a temporary "no frills" network 
Windows works great - I'm actually restoring this computer for a friend.  I'm just trying to get support for my flash drive.  The cable would probably work, but I'll pull the hard drive out & use another computer before buying more hardware.

Thank you all for the help and the ideas.  Finding these files has been an added bonus in itself - I never expected to find them in the first place.  Old family photographs, stories about my Grandpa's childhood (he passed away this summer), family geneaology...what a treasure!

---

### Post by twin_57103 on 2008-01-06
Update: Knoppix did the trick.  It was able to read the hard drive and mount my flash drive.  It mounted the flash drive as read-only (the second time I mounted it), but I was able to change it back.

Thanks again,
twin_57103

---

### Post by K.Mandla on 2008-01-06
Five hours too late to mention Ubuntu Rescue Remix!

[http://www.ubuntu-rescue-remix.org](http://www.ubuntu-rescue-remix.org)

---

### Post by Sukarn on 2008-01-07
> **K.Mandla said:**
> Five hours too late to mention Ubuntu Rescue Remix!

[http://www.ubuntu-rescue-remix.org](http://www.ubuntu-rescue-remix.org)

In any case, that is good info. I did not know about it previously.
Thanks.

---

### Post by john_spiral on 2008-01-15
> **elithrar said:**
> Burn a [Knoppix](http://knoppix.com/) (Live CD-based distro) for these kind of things. It should detect your Windows HDD once it's booted and you then should be able to pull files off it.

Klaus is King! You can use the live CD to boot a light window manager like fluxbox or KDE if you want something more usable.

check to boot codes for more options.

---

