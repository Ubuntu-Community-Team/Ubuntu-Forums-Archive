---
title: "problem with transferring file from other p.c. to lubuntu"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by Sahid Iqbal on 2013-06-26
I have two laptops. One has lubuntu 12.04 and other windows 7. When i want to transfer file from one to other i use pen-drive. At first time, when i transfer(let say File "A") to lubuntu, its shows file containing "A". Next time, i remove File "A" and insert File "B" in pen-drive by using win 7. But in lubuntu, i can not see File "B" is there. Instead of that, it shows pen-drive containing File "A". That moment, I can not fetch, see, use File "B". After rebooting i can see it contains File "B".
Can anyone suggest me any possible solution for this problem?

---

### Post by newb85 on 2013-06-26
When you first removed the flash drive from the Lubuntu system, did they system acknowledge that you had removed it?

---

### Post by gnjepar on 2013-06-26
Have you ejected (unmounted) you pen drive before physically removing it? I had a similar problem with Linux Mint, it turned out to be an unmount operation failure.

---

### Post by Sahid Iqbal on 2013-06-26
After ejecting I first removed the flsh drive.

---

### Post by Sahid Iqbal on 2013-06-26
yes, I did.

---

### Post by HermanAB on 2013-06-26
Using a USB stick is rather last century.  Either install FileZilla FTP server on the Windows PC and then simply connect to that using Nautilus or Dolphin, or install Dropbox and share your files between all your computers (the NSA and GCHQ).

---

### Post by gnjepar on 2013-06-27
It's not a solution for your USB flash memory problem but I would recommend installing samba server on your lubuntu machine.
[http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/)

You can than access your files via Windows machine by typing ```
\\lubintu-PC-IP-address\share-name
``` in windows explorer.

---

### Post by Datzy on 2013-06-27
I suggest just using a Cloud storage device, or setting up Nautilus and FileZilla.

Nautilus (GNOME): [https://live.gnome.org/Nautilus](https://live.gnome.org/Nautilus)
FileZilla (WIN): [https://filezilla-project.org/](https://filezilla-project.org/)

Cloud storage:
Google Drive (Client for WIN/OSX, web support for all): [http://drive.google.com/](http://drive.google.com/)
Dropbox (WIN/OSX/LINUX): [http://dropbox.com/](http://dropbox.com/)

You can install Ubuntu One straight off of the 12.04 sidebar.

---

### Post by uRock on 2013-06-29
When you delete files within Windows, do you empty the recycle bin.

While I agree with using filesharing within the LAN, I do not recommend Dropbox or any other cloud service. Not to mention that such recommendations do not answer the OP's answer.

---

### Post by amjjawad on 2013-06-30
Hello and Welcome to Ubuntu Forums :)

Thanks for using Lubuntu!



> **Sahid Iqbal said:**
> Next time, i remove File "A" and insert File "B" in pen-drive by using win 7.
If this operation (removing File A and copying File B) is done under Windows, have you tired to empty your Recycle Bin? or at least Shift+Del ?

Have you tried to do Quick Format, just in case?

> But in lubuntu, i can not see File "B" is there. Instead of that, it shows pen-drive containing File "A". That moment, I can not fetch, see, use File "B". After rebooting i can see it contains File "B".

After rebooting from where? which machine?

I have many machines over there and all of them are muti-booting systems.
I always use file transfer using USB Drive from machine to other, haven't had any problem.
Yes, from Windows 7 to almost all versions of Lubuntu (13.10 which is still under dev, 13.04, 12.10 and 12.04).

Thanks!

---

### Post by Sahid Iqbal on 2013-07-06
No, I simply deleted file under win7. and reboot lubuntu.

---

### Post by Sahid Iqbal on 2013-07-06
no, i just deleted from usb.

---

