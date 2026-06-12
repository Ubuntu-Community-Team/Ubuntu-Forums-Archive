---
title: "Flash Drive support for ubuntu 12.04"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by ryan516 on 2013-06-19
I am wanting to install Ubuntu onto a flash drive directly, and not to a hard drive. I don't want to use the flash drive as a boot disk, is there a way I can save it so documents and all open up on the flash drive? Do I just run it like a live CD. I am just confused. Please help Ubuntuers.[RIGHT]-Ryan516
[/RIGHT]

---

### Post by MidnightGrey on 2013-06-19
Hi ryan,

if i understand your post correctly, you want to install Linux on your USB but have the boot link to one of your harddrives? So when you boot up you have the option of booting to your USB from the harddrive. is this correct? This should be easily do-able, you just have to run the installation program from any partition other than your target USB. 

The only issue is that every time you boot up, your linux OS will be listed in the bootloader regardless if your USB is plugged in or not.
Your Linux USB will also not be usable on any other computer except as a regular USB.
And if you ever update your grub while the USB is not plugged in you may lose your linux entry in the bootloader entirely*.

*educated guesses.


Or, did you mean do you want to install a self-contained Linux OS on a flash drive which you could carry around with you, to be able to run on multiple computers?

---

### Post by ryan516 on 2013-06-19
Hi Midnight,
    I did mean a self-contained flash-drive for use on multiple computers. I have it set up to run like a Live CD/DVD, but that's not saving any of my settings or files which is frustrating me. I'm sorry for the confusion, I'm just not very good with the technological terms :/. Is there a way I can not only contain the Ubuntu OS but also my files/settings in the actual flash-drive(Like it's your main hard drive.)[RIGHT]-Ryan516[/RIGHT]

---

### Post by MidnightGrey on 2013-06-19
May I ask how you installed the LiveCD?
While the default setup is set to 'forget' everything after shutdown, it can be configured to remember files and preferences between boots.

---

### Post by ryan516 on 2013-06-19
I am upgrading from Windows 8 to Ubuntu, so I used an application for Windows called Pen Drive Linux. I took the 12.04 .iso, and put it into PDL, and it saved it to my USB drive.

---

### Post by ryan516 on 2013-06-19
Also, I am sorry for the double post, but is there a way to install the actual OS to the Pen Drive instead of using the LiveCD/DVD iso?

---

### Post by MidnightGrey on 2013-06-19
Did you use the Universal USB installer from this [page](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)?
If you look at the first screenshot:
**step 4: Set a persistent file size for storing changes (Optional)**.
You need to change that slider, i would recommend moving it to the maximum possible volume.

---

### Post by ryan516 on 2013-06-19
OK, thanks for the help MidnightGrey
    I wasn't quite sure what persistence meant when I set it up. I'm guessing now it's a virtual hard drive?

---

### Post by MidnightGrey on 2013-06-19
> **ryan516 said:**
> Also, I am sorry for the double post, but is there a way to install the actual OS to the Pen Drive instead of using the LiveCD/DVD iso?

How big is your USB size wise? The LiveCD is more or less identical to an actual Ubuntu install.

> I'm guessing now it's a virtual hard drive?
I'm not quite sure what you mean, turning on persistence just means the allocated space is used to save files/settings changes which will be loaded next time the operating system boots.
You can read up more on this here: [http://www.pendrivelinux.com/what-is-persistent-linux/](http://www.pendrivelinux.com/what-is-persistent-linux/)

---

### Post by ryan516 on 2013-06-19
Ok, thank you. My USB drive is large for some flash drives(32 gb) I just don't want my Ubuntu to have the install Ubuntu 12.04 message on the Gnome desktop or Unity dock.
Ryan516

Edit: Also, is 4 gb enough for Persistence? That's as high as PDL would let me go.

---

### Post by MidnightGrey on 2013-06-19
Do you have a 2nd USB? you can install LiveCD to that and go through the installation process setting your 32Gb flash drive as the target drive.

---

### Post by ryan516 on 2013-06-19
How big does the 2nd Flash Drive have to be? I have an 8gb I know where it is. Also, would any of this info work if I installed Kubuntu? I'm a definate KDE nerd :P

---

### Post by MidnightGrey on 2013-06-19
You only need about 1Gb to set up a USB-LiveCD. The iso's themselves are roughly 700mb depending on the distro.

---

### Post by ryan516 on 2013-06-19
Thank you SO much, my linux is almost fully installed, and all I really need to do myself is get Java and WINE.
Happily posted from Firefox in Ubuntu 12.04

Edit: I am really liking Ubuntu from a flash drive! It's pretty fast, and was just as easy to get Kubuntu and OpenJRE as on the hard drive.

---

