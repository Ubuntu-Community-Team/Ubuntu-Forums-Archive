---
title: "Unable to open NAS error on 12.04."
date: 2012-04-20
forum: New to Ubuntu
---

### Post by mickb58 on 2012-04-20
Hi,  Sorry to be coming in on the back-end of this thread.  I am a first time user who had an old LG laptop and decided it was time to see what the Linux was all about.  I downloaded 12.04 Beta and installed and it works fine, although at this point no skype.  When I go to the network icon it shows all of my connected devices including my Thecus N5500 NAS.  If I click on the NAS to browse the shared folders (terminolgy from my windows usage so excuse me if incorrect) I get a message that there is no program to open it.
 
Is there something else I should install to enable me to browse the files on the NAS and open them on the Ubuntu Laptop?
 
Googled but could not find and answer.
 
Regardss
 
Mick

---

### Post by mastablasta on 2012-04-20
> **mickb58 said:**
>  
Is there something else I should install to enable me to browse the files on the NAS and open them on the Ubuntu Laptop?

 
no. nautilus (default Ubuntu file manager) should be able to open them. 
 
what kind of OS is on NAS? what kind of file system do you use on NAS?

---

### Post by CharlesA on 2012-04-20
Looks like some proprietary OS, but likely some form of *nix cuz of XFS and ZFS

[http://www.thecus.com/product.php?PROD_ID=22](http://www.thecus.com/product.php?PROD_ID=22)

---

### Post by mickb58 on 2012-04-20
To be perfectly honest I am usure what OS the NAS unit runs or what file system it uses, but will check when I get home.  It must be something that Windows can access natively as I have never had a problem accessing it from an XP or Win 7 box.  I thought it was going to be easy when the network button brought up a list of my Win 7 laptop and the NAS all correctly identified.  Will post again when I get a bit more info

---

### Post by mastablasta on 2012-04-20
well also try opening nautilus and browse to NAS.
 
maybe it's some bug or something. 12.04 is still beta.

---

### Post by mickb58 on 2012-04-20
I am not sure if the file manager I am using is Nautilus as the only programs I seem to be able to see and access are those that were installed on the menu bar on the right hand side of the screen.  I expected there would be far more than 4 programs, the Ubuntu store, Ubuntu 1, Home Folder & system settings.  Am I missing something?  I have attached a jpg of the home folder as well as the error message.

I am sorry if I am missing something obvious but this is not something that comes easy in your late 50's and all you have ever known is Windows

---

### Post by mastablasta on 2012-04-20
> **mickb58 said:**
> I am not sure if the file manager I am using is Nautilus as the only programs I seem to be able to see and access are those that were installed on the menu bar on the right hand side of the screen. I expected there would be far more than 4 programs, the Ubuntu store, Ubuntu 1, Home Folder & system settings. Am I missing something? I have attached a jpg of the home folder as well as the error message.
 
I am sorry if I am missing something obvious but this is not something that comes easy in your late 50's and all you have ever known is Windows
 
yes that is the file manager. The Ubuntu sign is where other programmes are "hiding". silly isnt' it? if you prefer windows like interface then try Kubuntu.
 
anyway unable to mount share point is a totally different error. and i am sure someone with more knowledge will provide the solution. but might be a good idea to chekc on NAS if it allows access to ubuntu maschine.

---

### Post by audiomick on 2012-04-20
My guess is that the shares on the NAS are Samba shares. You might find some help here.

[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")

What you are describing is familiar to me: I had trouble getting into my NAS at first. It can work, I am sure of that. Might take a bit of messing around,but you should be able to work it out. ;)

---

