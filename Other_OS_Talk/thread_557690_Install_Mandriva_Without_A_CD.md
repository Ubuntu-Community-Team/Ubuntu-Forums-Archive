---
title: "Install Mandriva Without A CD"
date: 2007-09-23
forum: Other OS Talk
---

### Post by tuxcantfly on 2007-09-23
Note to mods: I don't see an Mandriva subforum here, so I'm posting here, move this to wherever it's appropriate. This isn't a duplicate of my other thread at [http://ubuntuforums.org/showthread.php?p=3400831](http://ubuntuforums.org/showthread.php?p=3400831) since this covers Mandriva specific instructions, though I also posted this in the mandriva forums at [http://forum.mandriva.com/viewtopic.php?p=371030](http://forum.mandriva.com/viewtopic.php?p=371030)

Main Website At [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

**What This Does**

It's an installer for Windows or Linux users that lets you install Mandriva 2008 without a CD. The way it works is that a small (8 MB) installer places the PXE (netboot) version of the Mandriva installer on your hard drive, and configures your boot loader, either NTLDR if using Windows, or GRUB if using Linux, to boot from the PXE installer, and downloads and installs Mandriva from the net.

**Requirements**

You will need to either have a Windows (95-Vista) or Linux (any distro that uses GRUB) install already on your hard drive. You'll also need an internet connection. Apart from that, the requirements are the same as the standard Mandriva 2008 requirements.

**Instructions**

First, you'll need a spare, 4GB partition to store the ISO file in temporarily for the installer, and another partition to install Mandriva in. If you're using Windows Vista, just open the [Drive Management](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista) utility and that'll do it for you; otherwise you will have to use the [PartedMagic Partition Manager](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4) ([download](http://sourceforge.net/project/showfiles.php?group_id=198821))

Then, visit the [Mandriva Download Page](http://www.mandriva.com/en/download) and download "Mandriva Linux Free 2008" to the new 4GB partition. Do NOT download the "One" version; it will not work.

Then, download the appropriate installer package (UNetbootin Mandriva 2008.0) from [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

If using Windows, download the .exe file, if using  Mandriva, Fedora, or another rpm-based distro, download the .rpm file, if using Ubuntu, Debian, or another deb-based distro, download the .deb file, and if using a distro that doesn't support rpm or deb, download the sh file.

Then, install the package, and reboot. A menu entry should appear in the boot menu, titled "UNetbootin". Select that entry, and boot. When asked for a source of installation media, select "Hard Drive" as your install option.

Then, select the hard drive you have the ISO file stored in, and specify the directory in which it is located.

Then, the main installer will start, and wait as Mandriva is installed.

**More**

UNetbootin also supports Ubuntu, OpenSuse, Fedora, Arch Linux, and Debian. Post a reply if you need any help, new features, or another supported distro. The website is located at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by tuxcantfly on 2007-09-23
I also posted this thread on the Mandriva Forums at [http://forum.mandriva.com/viewtopic.php?p=371030](http://forum.mandriva.com/viewtopic.php?p=371030) and the main UNetbootin thread with instructions for Ubuntu is at [http://ubuntuforums.org/showthread.php?p=3411879](http://ubuntuforums.org/showthread.php?p=3411879)

---

### Post by tuxcantfly on 2007-09-23
also, in case any of you don't know the server info, use this:

select FTP

server: **ftp.nluug.nl**
folder: **pub/os/Linux/distr/Mandriva/official/2007.1/i586**

---

### Post by tuxcantfly on 2007-09-24
Ignore this, I'm subscribing to this thread.

---

### Post by mindtrick on 2007-09-25
Thanks, I will try this now. Let's install Mandriva 2007 without wasting blank CDs.

---

### Post by tuxcantfly on 2007-10-09
Mandriva 2008 was recently released, so I've published a new UNetbootin build that can install it.. see the usual download spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) and instructions are at the unetbootin site at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

Basically, follow the same instructions as with 2007, only for the server info, input this:

If installing Mandriva, select "FTP" as the installation source, and for the server, specify:

    **ftp.free.fr**

and for the folder, if using the standard (32-bit) version, specify:

    **mirrors/ftp.mandriva.com/MandrivaLinux/official/2008.0/i586**

or if using the 64-bit version, specify:

    **mirrors/ftp.mandriva.com/MandrivaLinux/official/2008.0/x86_64**

---

### Post by Antman on 2007-10-12
Sweet, Thanks for this thread. I need to use the iso in order to install 2008 unto my dell (only boots to CD not DVD and i don't feel like changing the cabling).

---

### Post by tuxcantfly on 2007-10-16
> **Antman said:**
> Sweet, Thanks for this thread. I need to use the iso in order to install 2008 unto my dell (only boots to CD not DVD and i don't feel like changing the cabling).

Note that if you have the actual DVD, and just want to boot from it, this'll get the job done too: [http://ubuntuforums.org/showthread.php?p=3510679#post3510679](http://ubuntuforums.org/showthread.php?p=3510679#post3510679)

Also, remember to store the iso/package files on a different partiton than one you'll be resizing/wiping out.

---

### Post by tuxcantfly on 2007-10-28
I've added support in the Mandriva 2008 UNetbootin packages for installing from Windows Vista. Usual download spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by Frak on 2007-10-28
Thanks tuxcantfly for the great applications :)

---

### Post by Extreme Coder on 2007-10-30
Thanks for the great guide!

---

### Post by Dulwithe on 2008-01-30
"UNetbootin also supports Ubuntu, OpenSuse, Fedora, Arch Linux, and Debian. Post a reply if you need any help, new features, or another supported distro."

Thanks for your work with this.  I have a Toshiba R-100 on which I have desperately been trying to install Linux, but since it doesn't have CD boot support (except with an expensive Toshiba cable), I haven't had any luck so far.

You mention to reply for help if another supported distro is desired.  Is it possible to get a version of UNetbootin that will support the install of PCLinuxOS?

Thanks.

D.

---

### Post by tuxcantfly on 2008-02-05
> **Dulwithe said:**
> "UNetbootin also supports Ubuntu, OpenSuse, Fedora, Arch Linux, and Debian. Post a reply if you need any help, new features, or another supported distro."

Thanks for your work with this.  I have a Toshiba R-100 on which I have desperately been trying to install Linux, but since it doesn't have CD boot support (except with an expensive Toshiba cable), I haven't had any luck so far.

You mention to reply for help if another supported distro is desired.  Is it possible to get a version of UNetbootin that will support the install of PCLinuxOS?

Thanks.

D.

Done. PCLinuxOS builds are at [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=261499](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=261499)
This version works a bit differenly from the previous UNetbootin builds (since PCLinuxOS is a liveCD-only distro), so make sure to read the installation instructions at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) (middle of the page, titled "PCLinuxOS Instructions")

---

