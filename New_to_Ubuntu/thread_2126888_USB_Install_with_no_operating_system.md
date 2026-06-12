---
title: "USB Install with no operating system"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by Catharsia on 2013-03-18
My laptop has fallen victim to a virus which has rendered is nearly totally unusable and I was thinking about formatting the hard drive and installing Ubuntu as the operating system instead of Windows 7 because it is just generally better for the purpose which I need the laptop for. However I do not have any spare empty CDs spare and only have a USB stick which while able to be used to install Ubuntu on Windows, I have no idea if I could load Ubuntu onto my laptop with no operating system with a USB stick after it has been formatted. If anyone could answer my question it would be much appreciated as I do not want to go ahead with this without expert knowledge.

---

### Post by arochester on 2013-03-18
Be careful. Your laptop might have a Windows Recovery Partition and you could lose it if you format the whole disk or let Ubuntu use the whole disk.

---

### Post by Mark Phelps on 2013-03-18
There are simple ways to repair an infected Win7 PC which involve downloading and burning CDs of free versions of well-known Windows antivirus products.  However, if you want to simply throw away your Win7 stuff, files and all, that's your choice.

Ubuntu installation media (CD/DVD/USB) are designed to be used such that, when you boot from them, they give you the option of using the entire drive -- which means you do NOT need an existing OS on the PC to install Ubuntu.  You simply boot from the Ubuntu media and select the option to use the entire drive.

---

### Post by JLeon85 on 2013-03-18
> **Catharsia said:**
>  I have no idea if I could load Ubuntu onto my laptop with no operating system with a USB stick after it has been formatted.

You can definitely boot from the USB no matter what's happening with the hard drive, in fact you could even remove the hard drive if you wanted. Just make sure your BIOS settings are set to boot from the USB first.

---

### Post by @tomic on 2013-03-18
I would recommend creating a USB flash disk with unetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Once you have it running, install clamav to do a scan of your hard drive. You should be able to find it in the software centre. 

Then plug in a portable hard drive to back up your personal files.

Then format your hard drive and install Ubuntu.

Lastly copy your personal files to Ubuntu.

---

