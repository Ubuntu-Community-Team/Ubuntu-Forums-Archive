---
title: "wubi installation on laptop failure"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by Laurence WM on 2012-09-20
Last week I purchased an ASUS laptop, with Genuine Windows 7 Home Premium 64-bit. I downloaded Ubuntu via wubi (from ubuntu.org).

When I turn on the laptop, I get the dual-boot options. I can proceed to Windows without problem, but when I choose Ubuntu I get a failure message, with these details:


File: ubuntu\winboot\wubildr.mbr

Status: Oxc0000098

Info: The selected entry could not be loaded because the application is missing or corrupt.


Can anyone help?

Thanks very much indeed,
Laurence

---

### Post by newb85 on 2012-09-20
Welcome!

I'm sorry your Ubuntu experience is starting off so rocky.

Sounds to me like an issue with incompatibility between the UEFI Bootloader on newer systems like yours and the Wubi installer.  

Is there a reason you used the Wubi installer?  If you have no particular reason (other than the Ubuntu webesite made it look easy), here's my strong recommendation:

Remove your Wubi installation.  You should be able to use Windows' control panel to remove it as you would any other program.

Go back to the [download page]("http://www.ubuntu.com/download/desktop") and use the method at the top.  (Note, you'll get better performance if you choose 64-bit when downloading.)  Once you've downloaded the .iso file, burn it to a CD. (The easiest way to initiate this is to right-click the .iso and hit "Burn disc image".)

Once you have finished burning the disc, reboot your machine with the disc in the the drive.  If it boots to Windows normally, reboot again and this time press and hold the Shift key when the "Asus" screen first comes up, and when the boot options come up, tell it to boot from the CD.

Once your machine boots from the CD, you should see a Welcome screen with the option to Try Ubuntu or Install Ubuntu.  I recommend you hit Try Ubuntu and play with it a little before installing.  There will be shortcut on the desktop to install, when you're ready.

During the install, everything should be straight-forward.  Just make sure you choose to install alongside Windows, *not* the "Erase disc and install Ubuntu".  ;)

---

### Post by Laurence WM on 2012-09-20
Thank you very much indeed, newb85! This is very helpful indeed. I shall edeavour to do just as you suggest.

Except that there is no CD drive in my laptop. Is it just the same with a USB stick?

Thanks again,
Laurence

---

### Post by newb85 on 2012-09-20
> **Laurence WM said:**
> Thank you very much indeed, newb85! This is very helpful indeed. I shall edeavour to do just as you suggest.

Except that there is no CD drive in my laptop. Is it just the same with a USB stick?

Thanks again,
Laurence

Yes, if you follow the instructions on the download website, it should work.

---

### Post by Laurence WM on 2012-09-20
Thanks again newb85. Following the instructions I attempted to download the installer from pendrivelinux.com. However my McAfee security warned me that this contained viruses, spyware etc. Should I ignore this?

Cheers,
Laurence

---

### Post by Mark Phelps on 2012-09-20
I've used the pendrive installer several times -- no malware.  Seems like a false "postiive" from McAfee to me.

---

### Post by newb85 on 2012-09-20
> **Laurence WM said:**
> Thanks again newb85. Following the instructions I attempted to download the installer from pendrivelinux.com. However my McAfee security warned me that this contained viruses, spyware etc. Should I ignore this?

Cheers,
Laurence

[s]A pendrive is *not* the same as a Live USB.  Create a Live USB by downloading the .iso from the downloads page at ubuntu.com and following the directions there for creating a Live USB.[/s]

This info is wrong.  See my next post.

---

### Post by Laurence WM on 2012-09-20
Thanks a lot, Mark. That's good to know.

Cheers,
Laurence

---

### Post by Laurence WM on 2012-09-20
> **newb85 said:**
> A pendrive is *not* the same as a Live USB.  Create a Live USB by downloading the .iso from the downloads page at ubuntu.com and following the directions there for creating a Live USB.

I'm confused now. The downloads page

[http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)

directs me to

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

which states

'The easiest way to put Ubuntu onto your stick is to use the USB installer provided at [pendrivelinux.com]("http://www.pendrivelinux.com").'

---

### Post by newb85 on 2012-09-20
> **Laurence WM said:**
> I'm confused now. The downloads page

[http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)

directs me to

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

which states

'The easiest way to put Ubuntu onto your stick is to use the USB installer provided at [pendrivelinux.com]("http://www.pendrivelinux.com").'

Actually, no, I was the one who was confused.  I've never created a LiveUSB from Windows, so I've never used pendrivelinux.com.  When you mentioned the site, I checked it out and mistakenly thought that when they said
> Easily install your favorite Linux operating system on a flash drive or USB key no larger than your thumb (Thumb Drive). 
they actually meant *install* Linux on the thumb drive.  I've read a little further, and clearly they don't mean *install*.  Installing Ubuntu requires over 5GB, and when you boot an installed Ubuntu setup, it doesn't have a desktop shortcut to the installer.

Laurence, please disregard my last post.

---

### Post by Laurence WM on 2012-09-20
Ok thanks newb85!

---

