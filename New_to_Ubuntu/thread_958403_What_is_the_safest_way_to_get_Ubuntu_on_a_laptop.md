---
title: "What is the safest way to get Ubuntu on a laptop?"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Rukaru on 2008-10-25
I just got a laptop and I want ubuntu, but I don't really want GRUB.  I do like the dual boot concept, but I don't know if you can delete GRUB and I just don't want any problems. So, what is the safest/easiest way and what are its disadvantages.  I want to be able to use the full ubuntu, complete with compiz and emerald.

I have another question about programs in ubuntu.  I'm in college and it's required that I have a word processor that can handle doc and docx files.  I know there's openoffice, but there are occasionally problems when saving docx and doc files, as well as opening them. I do have Microsoft office 2007 so if there's a way to put it on ubuntu, let me know.

I was also wondering...does dual-booting ubuntu slow down the other OS in the slightest bit?  My other OS is vista, and it actually runs quite nicely right now.

---

### Post by bpowell2005 on 2008-10-25
> **Rukaru said:**
> I just got a laptop and I want ubuntu, but I don't really want that thing at start up....I forgot what you call it.  You know what I'm talking about...the thing that lets you choose between OS's. So, what is the safest/easiest way and what are its disadvantages.  I want to be able to use the full ubuntu, complete with compiz and emerald.

I have another question about programs in ubuntu.  I'm in college and it's required that I have a word processor that can handle doc and docx files.  I know there's openoffice, but there are occasionally problems when saving docx and doc files, as well as opening them. I do have microsoft office 2007 so if there's a way to put it on ubuntu, let me know.

I think you'll need to have a dual-boot setup, which requires a boot-loader (the thing you're referring to). That's the only way to select which OS you want to boot. You can have the boot loader default to Windows after 5 or 10 seconds if you want...I really like having a dual-boot setup.

You could always install ubuntu in a virtual machine within Windows, but I haven't gotten the visual effects (compiz, etc.) to work very well that way...(although, to be honest, I haven't tried that hard either).

There's also a way to install Ubuntu inside windows called Wubi...but I have no experience with that. As a rule, I don't like to virtualize OS's, as it requires sharing resources between two different operating systems at the same time...that's why I go with the dual-boot option.

But, to each their own.

---

### Post by drtre on 2008-10-25
> but I don't really want that thing at start up....I forgot what you call it 
Thats GRUB:popcorn:

Why u dont want that? I know u can change the preferences in grub but dont know if u can delete it completely o not.

---

### Post by OutOfReach on 2008-10-25
You need to have GRUB (the thing that lets you pick OS's) or you will not be able to boot into Ubuntu or any other OS for that matter. You can make it automatically boot into Ubuntu after a few seconds if you like...

As for Microsoft Office 07, you can use WINE ([www.winehq.com](www.winehq.com)) to try and install it, but don't expect a perfectly running program there will be some bugs because WINE is still in development.

---

### Post by OneRingShort on 2008-10-25
That thing at start up is the GRUB Bootloader.  Unfortunately, a bootloader screen like that is required (to my knowledge) for any system with multiple operating systems.  If you didn't want one of those, you could just keep a LiveCD available and run off that.

If you do decide to install it with the bootloader, the "safest" ways of doing it would be with a guided install to automatically shrink the Windows partition.  The easiest way may be the [Wubi installer]("http://wubi-installer.org/") that installs Ubuntu in Windows as a folder, and allows you to uninstall it easily.  It will still ahve the bootloader in the beginning though.

As farr as the word processor goes, Open Office 3 does have the capability to save .doc files, but can only read .docx files (which you could then convert into .doc).
You could run [Microsoft Office 2007 through Wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992"), but it will take some configuration.  It looks like its in the Gold status at the moment, so almost everything should work fine in it.  Another method (the one I currently use) is to run it through a virtual machine such as VMware or VirtualBox.  These will let you run any operating system inside Ubuntu, which would let you run any Windows program you need.  It does take a little bit to set up, but there are plenty of tutorials and howtos on these forums.

Hope this helps!

Matt

---

### Post by Duck2006 on 2008-10-25
Are you just going to run ubuntu on the laptop, or are you going to dual boot.

To install ms office 2007 in ubuntu this may help.

[http://ubuntuforums.org/showthread.php?t=767423&page=6](http://ubuntuforums.org/showthread.php?t=767423&page=6)

---

### Post by Ripfox on 2008-10-25
The safest way to get Ubuntu on a laptop is to place a live cd on top of the closed cover. 

J/K  :lolflag:

I had to say that sorry

---

### Post by Rukaru on 2008-10-25
> **drtre said:**
> Thats GRUB:popcorn:

Why u dont want that? I know u can change the preferences in grub but dont know if u can delete it completely o not.

GRUB! It was on the tip of my tongue.  Well the reason I don't want it is because I don't know if you can remove it.

I just don't want any problems with my new laptop.  You understand I'm sure.

---

### Post by drtre on 2008-10-25
> As for Microsoft Office 07, you can use WINE ([www.winehq.com](www.winehq.com)) to try and install it, but don't expect a perfectly running program there will be some bugs because WINE is still in development.

dont recommend using windows programs in linux using wine. it'll give u much of a headache than help u. embrace openoffice.org dude. its a perfect program. i use openoffice.org even in my windows.

---

### Post by Ripfox on 2008-10-25
> **drtre said:**
> dont recommend using windows programs in linux using wine. It'll give u much of a headache than help u. Embrace openoffice.org dude. Its a perfect program. I use openoffice.org even in my windows.

+1

---

### Post by drtre on 2008-10-25
> **Rukaru said:**
> GRUB! It was on the tip of my tongue.  Well the reason I don't want it is because I don't know if you can remove it.

I just don't want any problems with my new laptop.  You understand I'm sure.

every os needs a kind of boot manager to be loaded. grub is like that boot manager for linux. its not goin to cause any problems for u at all. it'll just let u choose between your os. i never had linux individually installed on my linux, so i dont no if grub would come up in that case or not. but u can change the preferences for grub to specify which os be your default or how much delay there should be before loadin the selected os and ....

---

### Post by Rukaru on 2008-10-25
> **OneRingShort said:**
> That thing at start up is the GRUB Bootloader.  Unfortunately, a bootloader screen like that is required (to my knowledge) for any system with multiple operating systems.  If you didn't want one of those, you could just keep a LiveCD available and run off that.

If you do decide to install it with the bootloader, the "safest" ways of doing it would be with a guided install to automatically shrink the Windows partition.  The easiest way may be the [Wubi installer]("http://wubi-installer.org/") that installs Ubuntu in Windows as a folder, and allows you to uninstall it easily.  It will still ahve the bootloader in the beginning though.

As farr as the word processor goes, Open Office 3 does have the capability to save .doc files, but can only read .docx files (which you could then convert into .doc).
You could run [Microsoft Office 2007 through Wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992"), but it will take some configuration.  It looks like its in the Gold status at the moment, so almost everything should work fine in it.  Another method (the one I currently use) is to run it through a virtual machine such as VMware or VirtualBox.  These will let you run any operating system inside Ubuntu, which would let you run any Windows program you need.  It does take a little bit to set up, but there are plenty of tutorials and howtos on these forums.

Hope this helps!

Matt

Thank you Matt. Thank you.  Could you explain the live CD method? What are the disadvantages of that?

---

### Post by OutOfReach on 2008-10-25
> **drtre said:**
> dont recommend using windows programs in linux using wine. it'll give u much of a headache than help u. embrace openoffice.org dude. its a perfect program. i use openoffice.org even in my windows.

Right I myself don't use WINE I use Abiword and OpenOffice. But sometimes a person has to use WINE because of classes, etc... even if they don't want to.

---

### Post by drowner on 2008-10-25
You can delete GRUB if you wish and restore Windows' native boot loader if you wish, however, you will not be able to boot Ubuntu if you do this.

(I have never used Vista, but I understand that it may be possible to use a Vista bootloader to boot Ubuntu)

Perhaps we can set your mind at ease....  In most cases GRUB will detect and boot your Windows with no problems, and if it can't, we should be able to help you make it so it does :D

What is it that frightens you about GRUB? Its an excellent bootloader.

---

### Post by Duck2006 on 2008-10-25
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Rukaru on 2008-10-25
> **OutOfReach said:**
> Right I myself don't use WINE I use Abiword and OpenOffice. But sometimes a person has to use WINE because of classes, etc... even if they don't want to.

Yeah well like I said the problem is Docx files.  I have actually worked much more with openoffice than microsoft office, so I know it's a good program.

---

### Post by Paqman on 2008-10-25
> **Rukaru said:**
> Well the reason I don't want it is because I don't know if you can remove it.

Don't worry, you can remove it. A Windows install disk will do the trick, as will the SuperGrubDisk IIRC. Neither will harm the disk's other contents.

---

### Post by drowner on 2008-10-25
> **Rukaru said:**
> Thank you Matt. Thank you.  Could you explain the live CD method? What are the disadvantages of that?

Ubuntu can be run from a CD, rather than installed on to a drive.

You will probably lose a degree of functionality, like this, though.

You could, I suppose, use something like the SuperGrubDisk to boot into Ubuntu without writing Grub to the MBR.

But, tell us why you are scared of GRUB.

---

### Post by OneRingShort on 2008-10-25
> **Rukaru said:**
> Thank you Matt. Thank you.  Could you explain the live CD method? What are the disadvantages of that?

The LiveCD allows you to run Ubuntu from the CD drive with out installing on the hard drive.  You can also install the LiveCD on a USB drive and run it in persistent mode, which allows you to keep your settings.  The biggest disadvantage is the speed - a USB port or CD drive won't match the speed of your hard drive.  This method is usually used for trying it out, or introducing it to people who haven't used it yet.

---

### Post by Kinst on 2008-10-25
I use wine to run Office 2007. The downside is equation editor doesn't work at all and a lot of fonts don't look right. Powerpoint can't do slideshows for more than 2 slides, and Excel is a bit screwy with calculations.

There are decent guides around the forums.

---

### Post by MrWES on 2008-10-25
I run Windows XP Pro SP3 inside a virtualbox just to run a couple of specific software packages. Runs very nicely. I have not install MS Office, but you might want to Google that to see if there are some successful installations inside Virtualbox.

Bill

---

