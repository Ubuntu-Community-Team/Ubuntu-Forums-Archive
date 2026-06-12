---
title: "Upgrade 5.10 without CD or USB?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by greenmainer on 2008-11-09
I've had Breezy for a little while now, but I've been trying for days and days now to upgrade. I don't think I would be able to upgrade to some of the newer versions, because my '98 Sony Laptop wont be able to handle them, but I still need to be able to get the newer versions of adobe and ff to be able to fully or mostly function on the internet. Can anyone Help me??

---

### Post by greenmainer on 2008-11-09
I have had 5.10 for a while now, but i need to upgrade to do anything on the internet. i cant get anything thats less than three or four years old. I have been trying for days to upgrade. I dont have access to a cd/dvd rw. All i have is my '98 sony viao laptop which can get online. Can anyone help me?!?

---

### Post by jpoRS on 2008-11-09
Hey Greenmariner,

When you upgrade, you can only upgrade in order (so Breezy to Dapper to Edgy etc.)  The problem you will have with this is that none of these versions are supported anymore, since Feisty went out of circulation last month (I think), so there are no servers to upgrade FROM.  Unfortunately for you, I believe this makes it "impossible" for you to do a direct upgrade, and you will have to do a fresh install in order to get support.  (If someone knows that last statement to be wrong, please correct me.)

The "oldest" distribution that is still supported is Gutsy Gibbon, but even that will stop being supported in April.

If you are worried about your computer's ability to handle Ubuntu, why not try [Xubuntu]("http://www.xubuntu.org/").  It is a "flavor" of Ubuntu designed to work on lower powered systems.

Good luck!
jim

---

### Post by jdackle on 2008-11-09
Ubuntu 5.10 is no longer supported (i.e. no updates to its packages). Hence you really do need to upgrade to a newer, preferably still supported release or try to install the most up-to-date Adboe (Reader?) and Ff "by hand", i.e. by going to their websites, downloading whatever installer and installing it on your system (which usually leaves you with some desktop integration work to do)

For the upgrade, see here:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
You'll want to scroll down to "From 5.10 to 6.06 LTS".


EDIT; Hadn't read Jim's response when I posted and neither had I thought of the (un)availability of older releases for download (with tons of luck, some forgotten mirror will still have some oldy...).
Also, the Xubuntu suggestion is a good one! ;)

---

### Post by BGrigg on 2008-11-09
You can always request the disk. Takes some time, though.

---

### Post by hardyn on 2008-11-09
where are you located geographically?  im sure there is somebody close that would have no issue burning one for you.

---

### Post by bodhi.zazen on 2008-11-10
> **greenmainer said:**
> I've had Breezy for a little while now, but I've been trying for days and days now to upgrade. I don't think I would be able to upgrade to some of the newer versions, because my '98 Sony Laptop wont be able to handle them, but I still need to be able to get the newer versions of adobe and ff to be able to fully or mostly function on the internet. Can anyone Help me??

As has been stated, it is no longer possible to upgrade ...

Your best bet is a fresh installation, I suggest 8.04 which is a LTS release ;)

---

### Post by greenmainer on 2008-11-15
i need to clean install a newer version of ubuntu, because i have breezy badger. I am trying to get 8.04.1, but i don't have a working cd burner right now... what can i do?

---

### Post by Partyboi2 on 2008-11-16
If you have access to the internet you could use [[COLOR=Blue]unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/") to install ubuntu

---

### Post by greenmainer on 2008-11-16
I have a '98 sony viao with no cdrom and with ubuntu 5.10. It has the internet, but i can't do to much because breezy badger isn't supported anymore so i cant uprgade any of the programs or browser. How do i install a newer os?

---

### Post by ugm6hr on 2008-11-16
Will it boot from USB?

Unetbootin should work too: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by greenmainer on 2008-12-07
I've been told that it can be done, but I don't know how. I have a 98 Sony Vaio without a working cd reader or usb ports, and I need to update my operating system, because I have breezy badger and since its out dated I can't do anything on the internet except check my email. all I have is my wireless card for the internet, so if it really is possible, please, tell me how to do it.

---

### Post by lovelyvik293 on 2008-12-07
You can update the ubuntu distro. by the synaptic manager(And i think the Breezy also have it.)

---

### Post by dracayr on 2008-12-07
quick google search rendered this:
[http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)

always google before you ask!

dracayr

---

### Post by ugm6hr on 2008-12-07
unetbootin will do it for you, direct to HD:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Or if you can boot from USB, use unetbootin to create an installer USB and use that.

---

### Post by lovelyvik293 on 2008-12-07
@ugm6hr greenmainer doesn't have to working usb ports.

---

### Post by ugm6hr on 2008-12-07
> **lovelyvik293 said:**
> @ugm6hr greenmainer doesn't have to working usb ports.

Sorry! My fault for only partially reading...

Anyway, unetbootin will allow installation to the same HD, although that only works if it is installing to a different partition than the original OS (hence the suggestion to use a LiveCD/USB).  So if you have a second partition on your HD, that may work.

Creating separate partitions will be impossible if there is no way for a LiveLinux to work, unless you can have a second HD on the laptop (which I presume is impossible).

As for updating Breezy... I suspect that is no longer possible, since you cannot miss versions with an upgrade, and Breezy has several non-supported versions to go through (Edgy, Fiesty).  Perhaps dist-upgrade may be possible to Dapper though, since it is LTS....  And Dapper can apparently be directly upgraded to Hardy...  So maybe?

---

### Post by ugm6hr on 2008-12-11
It is possible to install to your HD on another computer, and then transfer to your laptop before the 1st reboot, when a lot of the hardware detection is done.

Sometimes, the following command is necessary too (after rebooting):
```
sudo dpkg-reconfigure xserver-xorg
```

Since it is a 2.5" laptop HD, unless you have another laptop you could borrow to swap out the HD, this may be difficult.  If you have a desktop (with working USB ports), it should be possible to invest in a 2.5" portable USB box, which you should be able to put the HD into, and install on.  Then transfer back to your laptop, and it should hopefully work (as long as you install GRUB to the correct location).

I would also suggest you swap to a rolling update distro (e.g. Debian), since that would remove the necessity for future re-installations.

---

### Post by halitech on 2008-12-11
does the laptop have a working floppy? you could do a fresh install of debian over the net (although if you only have wireless, that could be a problem) with booting from floppy

---

### Post by bodhi.zazen on 2008-12-11
I apologize if this is off topic as I did not read the entire thread.

But you should see this page :

[uhelp]community/Installation[/uhelp]

    There is a section on no CD ...

---

### Post by halitech on 2008-12-11
thanks bodhi, right on topic, only thing we don't know right now is if they have a working floppy (no cd and cannot boot from usb)

---

### Post by bodhi.zazen on 2008-12-11
You could look at either of these:

[https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

