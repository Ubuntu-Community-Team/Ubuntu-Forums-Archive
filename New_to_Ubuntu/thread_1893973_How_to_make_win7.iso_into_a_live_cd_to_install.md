---
title: "How to make win7.iso into a live cd to install?"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by smcrossman on 2011-12-11
No, really, I'm not crazy!  My netbook has been dual boot.  I have a access to a legal download for Win7 Home Premium Upgrade.  When I did the automatic upgrade of Ubuntu it really messed up my system. And the Windows partition really needed to be cleaned up....So I'm starting with a clean install (upgrade) of Win 7 then adding my Ubuntu/Kubuntu back on hopefully ending up with a smoother and more stable platform.

The problem is....although I can download whatever and make the live CD for Ubuntu  or the USB stick for boot/install.  I cannot seem to get the darned windows.iso to copy onto the USB. The program microsoft provides simply errs out saying it can't copy my files.  The startup cd creators provided in Ubuntu won't take the windows iso.  I have the iso on my network storage drive, my desktop (ubuntu only), 2 windows partions on the netbook AND a DVD.  Yet getting it into boot format is beyond me.  I know back a ways there were some apps suggested for taking the ubuntu download and putting it on a USB stick while working in windows OS.  I just can't seem to find the name.  I also would gladly take an app that would do the opposite...take the windows download and put it onto the USB stick while working in the Ubuntu OS.

Can anyone help me out please?

---

### Post by Ricx94 on 2011-12-11
if you have a machine anywhere running windows, microsoft provides a nice, fairly simple program called "Windows 7 USB Download Tool", which i used to mount a windows 7 iso to usb before, and it worked perfectly. 
I don't know of any program on ubuntu to do this, if the standard startup disc creator did not work.

there is always the option, though, of using an external dvd drive, if you have one, or you could use an internal drive as a make-shift external drive.

---

### Post by BC59 on 2011-12-11
I think that Windows 7 USB/DVD Download Tool is a little difficult to be found nowadays.

Here a link on how you can create a bootable USB from a Windows 7 system, using Windows components.

[http://www.winsupersite.com/article/windows-7/install-windows-7-with-a-usb-memory-key](http://www.winsupersite.com/article/windows-7/install-windows-7-with-a-usb-memory-key)

---

### Post by westie457 on 2011-12-11
Here is a link to the Windows tool mentioned by BC59

[http://emea.microsoftstore.com/UK/en-GB/Service-Centre/Windows-7-USB-DVD-Download-Tool](http://emea.microsoftstore.com/UK/en-GB/Service-Centre/Windows-7-USB-DVD-Download-Tool)

---

### Post by JD8182 on 2011-12-11
When I upgraded my daughters Netbook, I used this tutorial or one almost exactly like it, it has been a while though, but try this I am pretty sure this is the tutorial I used and it worked great! [http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)

---

### Post by smcrossman on 2011-12-11
This is the Windows program that absolutely will not work for me. I'm not sure if it's being corrupted during download or what....but it isn't working.  IF I could get the iso into boot format I have an external read only I can use to install onto the netbook...but again that is where I'm having issues.  My dvd on my desktop won't work as a network drive to boot from...although I can download and copy to it fine.  In fact the iso I just downloaded to a DVD+R on it from windows is larger than the others I've downloaded and includes a folder called BOOT with an img file that is named bootable no emulation. 

I might just go through the process from the link BC59 provided.  Since I have the iso other than the copying the process shouldn't take much time. My only real question is why do you need to extract to your hd and then copy to the usb? Couldn't you just extract to the usb? (or if using a dvd to the dvd) Yeah okay it's a sloppy way to do it....if the extraction messes up then you might be losing a dvd or even the USB stick but really?  If the copying process takes as long as it might (I've seen download times state up to 2-3 hours for the iso imagine copying the extracted if your system is that slow?!)

---

### Post by Mark Phelps on 2011-12-12
You can't boot from a Windows ISO image to install Windows.  This has been discussed at length on other forums.  You have to extract the contents of the ISO file -- either to a hard drive, a USB stick, or to a DVD.

---

### Post by smcrossman on 2011-12-13
Okay.....I got my usb stick to work.  I used the link from JD (which was very similar to the one from BC)  and was fine....except since I had an iso I didn't have the right stuff to set the boot mgr up.  So I extracted my iso onto the desktop (along with the driver .exe files I knew I would need from Dell) and then with a little more searching found a blog post from a MS guy on how to create a Windows 8 usb boot stick.  (I included a link for anyone who might want/need it in the future) 

Easy enough.  Then when I tried booting up I kept getting no BOOTMGR error. Then I realized when I copied my extracted files it copied the folder containing the files so the boot folder was 2 layers deep.  Moved them out to the main directory and it was great.  Played with windows only all morning now preparing to do the download and install of Ubuntu. It was faster and fewer lockups which is a good sign.

[http://blogs.msdn.com/b/habibh/archive/2011/09/14/how-to-create-a-bootable-usb-flash-drive-to-install-windows-8-developer-preview.aspx](http://blogs.msdn.com/b/habibh/archive/2011/09/14/how-to-create-a-bootable-usb-flash-drive-to-install-windows-8-developer-preview.aspx)

Now I just have to decide if I'm going to download Ubuntu in windows or Ubuntu.  I'd prefer Ubuntu but its 64 bit and the download is 32 bit so I'm not sure how that will work out.  Ideally I would like to download it to my network storage drive but I'm getting local file only messages....UGH.

Thanks for the input and links all!

---

