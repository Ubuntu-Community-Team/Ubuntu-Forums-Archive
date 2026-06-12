---
title: "Ubuntu downloaded as a zip file.. how to burn it onto a CD?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by you123456 on 2008-10-30
Hi all, great to be part of this vibrant community.

I have a problem:
I have downloaded ubuntu 8.04.1 onto my desktop. I realized that it is being downloaded as a zip file, instead as a .iso file  .

That said, i have tried the instructions on [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and it didnt work for me since the ubuntu was downloaded as a zip file.

SO how do i download ubuntu as a .iso file? or how do i burn my zip file as a .iso file onto my CD?

Please help!

Best Regards,
Eugene

---

### Post by roger_1960 on 2008-10-30
Hi

If you extract the zip file, do you have an iso file?  Where did you get the .zip file from?

---

### Post by solitaire on 2008-10-30
Are you using Windows at the moment or another Linux?

In Windows WinZip is usually the default option to open *.iso files. So it will have the "zip" icon and look like a zip file.

All you need to do is download the "Infra Recorder" program in Windows and install it. Then follow the instructions on the "BurningIsoHowTo" page.

If you got Ubuntu from the website then it should be an ISO (I've never seen an Ubuntu download with the ZIP extension).

---

### Post by NewJack on 2008-10-30
Download the .iso from one of these links:

[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

You should use the torrents to grab the .iso, this will ease the strain on the servers.

Good luck!

---

### Post by you123456 on 2008-10-30
Hi, after extracting the zip file, i dont have an iso file. ( i cant seem to find it. Is it hiding in some folders?)

After extracting, what i get is a whole list of folders, directories and files. But cant find an iso file.

I downloaded ubuntu from  [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

The download location is 'Taiwan Shu-Te University'

Best Regards,
Eugene

---

### Post by fatphilthethird on 2008-10-30
Hi

Just went to the link you gave and there may be a problem with the Taiwan site. 

The link you should be downloading from, according to that page, gives an iso, not a zip and furthermore when you click on the direct link to the iso, it comes up page not found.

Suggest you try downloading it again from another source, or try getting it from the torrents

Cheers

Fat

---

### Post by you123456 on 2008-10-30
> **solitaire said:**
> Are you using Windows at the moment or another Linux?

In Windows WinZip is usually the default option to open *.iso files. So it will have the "zip" icon and look like a zip file.

All you need to do is download the "Infra Recorder" program in Windows and install it. Then follow the instructions on the "BurningIsoHowTo" page.

If you got Ubuntu from the website then it should be an ISO (I've never seen an Ubuntu download with the ZIP extension).

Hi, I am using a iwndows xp sp2 machine. I have tried following the instructions on "BurningIsoHowTo" but i couldnt burn the "zip" file. 
What happened is this: after clicking on "action" on infrarecorder and selecting "burn image" option, i am presented with the select file window. After selecting the ubuntu zip file, i cannot click 'ok' on the 'burn ubuntu-8.04.1-desktop-i386.iso' window.

Any idea what;s wrong?

BEst.

---

### Post by bfoos on 2008-10-30
You didn't download a .zip file. As someone above said, Winzip or some other archiver on your computer has associated itself with .iso files. Open any directory in Windows, click the tools menu, select folder options and then click the view tab. Untick "Hide extensions for known file types" and you will see that you have in fact, downloaded an ISO. Use whatever your prefered app for burning ISO files, is. I suggest imageburn.

---

### Post by NewJack on 2008-10-30
> **bfoos said:**
> I suggest imageburn.

It is actually called** imgburn** and it is a great little program for windows.  Here is their site:

[http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by lawentzel on 2008-10-30
One possibility is you have a bad file.  Another is that when you saved it, you named it .zip instead of .iso.  Try renaming the file to ISO and see if that works.  Ultimately I would recommend deleting that file and re-downloading it from another source.  Sounds a little suspect that it was a zip file.

---

### Post by bfoos on 2008-10-30
> **NewJack said:**
> It is actually called** imgburn** and it is a great little program for windows.  Here is their site:

[http://www.imgburn.com/](http://www.imgburn.com/)

Yes, of course you are correct, sir. And I actually JUST used it to burn 8.10. Heh, shame on me. :oops:

---

### Post by you123456 on 2008-10-30
Hi all, ok i got it.

somehow, imageburn worked for me. I have manged to burn the CD.

=)

Really, thanks for all your help within this short notice!

Lastly, what can i do to ensure that i have burned correctly? COs after finish burning the iso file, i got a window asking me if i want to do a 'demo and full installation' , or 'install inside window' options Does this means that i got it correctly?

Best.

---

### Post by bfoos on 2008-10-30
> **you123456 said:**
> Hi all, ok i got it.

somehow, imageburn worked for me. I have manged to burn the CD.

=)

Really, thanks for all your help within this short notice!

Lastly, what can i do to ensure that i have burned correctly? COs after finish burning the iso file, i got a window asking me if i want to do a 'demo and full installation' , or 'install inside window' options Does this means that i got it correctly?

Best.
You should be all set. You can either install it in Windows with Wubi, or boot the CD to try it out/install it.

---

### Post by solitaire on 2008-10-30
There is an option to install Linux using spare room on your Windows drive (Install inside Windows option) called Wubi read more about it here :[http://wubi-installer.org/](http://wubi-installer.org/)

The other option is the "LiveCD" option where the Machine reboots and runs Ubuntu form the CD and your RAM. This does NOT Touch your HARD DRIVE! so it's safe to use and play around with to see if everything works).

Note their is an option to "Test CD for Defects" or words to that effect if you go the "LiveCD" way. so you can test the image was correctly burned to the disk.

---

