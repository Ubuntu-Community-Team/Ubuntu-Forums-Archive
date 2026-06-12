---
title: "Installing Oneiric after I uninstalled using easybcd"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by awe1 on 2012-04-03
I had Ubuntu on my laptop a few days ago but a professional  installed it for me. Soon after I got it from the guy I messed it up. I  uninstalled Ubuntu with easybcd and now I'm scared it will complicate  things.
  Does it?
  I'm sure I downloaded Ubuntu to disk on this site:
  [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
  And got this file:
  ubuntu-11.10-server-amd64 
  which I burned to disk. 
  When I put the cd in my laptop it shows me a wubi.exe file.
  When I reboot with the cd it boots straight to windows 7.
  What's wrong? Teach me

---

### Post by Mark Phelps on 2012-04-03
It looks like you had it installed before using Wubi.

To do that on your own, boot into Win7.

Then, insert the CD.

When it starts up, select the option to install it.

You have to be running MS Windows to install using Wubi.

---

### Post by awe1 on 2012-04-03
?
It was dual booted. Now its not. I can't install because the cd doesn't come up when restarting and if I execute it in win 7 it shows me the wubi.exe file. I don't want wubi.

---

### Post by critin on 2012-04-03
Download another and be sure not to choose ("*if you're running windows" option*)
> 
ubuntu-11.10-server-amd64 

Are you certain you meant to get the server?  It's different from the ubuntu desktop and if you're unfamiliar with ubuntu...

---

### Post by oldfred on 2012-04-03
Best to download the desktop version as that is also a liveCD that you can boot and see that it works ok with your computer.

This is the server 64 bit version. It is not a liveCD, but just an installer.
ubuntu-11.10-server-amd64

Most computers now can run the 64bit version and while the Ubuntu site recommends the 32bit, most can download the 64 bit version. Just click on box that says 32bit and change to 64bit.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Mariane on 2012-04-03
Check you saved the file as .iso and not as data on the CD. Also check the md5checksum, both from what you want, which you find there:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
and with a program which does the sum on your file. 

It often happens that the CD seems to burn fine but in fact is corrupt.

---

### Post by awe1 on 2012-04-03
I downloaded it again. The file is iso on the desktop, burnt to the cd which is 700mb, the file 697. Could that be an issue?
Is there some setting that doesn't allow disks to boot.
The md5sum software tells me that some strings match.
I may not have understood all forementioned comments.
No idea if its data or iso on the cd.

---

### Post by critin on 2012-04-03
> No idea if its data or iso on the cd.Don't know what burning program you use, but did you tell it to "BURN iso"?
> 
When I reboot with the cd it boots straight to windows 7.Are you hitting the BOOT key when the computer first starts up?  Just when the BIO page shows?  the cd will not boot automatically unless you hit the boot key.  If you don't know what it is, look at the BIO screen when it starts.  Usually along the bottom or top right corner it will give a series of options.  BOOT is one of those and it will tell you which key to hit.  My computers are different keys, one is f12, one is Escape, some are del (delete)  Look at yours and hit it then it will go to a page so you can choose which hd to boot.  Choose cd.

Did you download the desktop this time?  You really don't want "server" unless you know how to work in the system.  It's mostly command lines.

---

### Post by awe1 on 2012-04-04
Thanks everyone for the help. I don't know why I wrote server when I meant desktop.
It booted so fast that I never saw the bios. F12 was the solution. Installation was strange though, slow and I thought Ubuntu was too idiot proof for bios and f-buttons. They never need it in tutorials. The first reboot after the installation went wrong. I got stuck in some config warning. Anyhow thanks for all, I will probably be back after a few days when I need to install it again.

---

