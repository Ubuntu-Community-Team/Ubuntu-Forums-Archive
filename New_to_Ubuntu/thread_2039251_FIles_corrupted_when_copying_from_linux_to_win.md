---
title: "FIles corrupted when copying from linux to win"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by avgudar on 2012-08-08
I use linux ubuntu on my laptop to download files, as it is much faster than windows, and because my laptop has a working slot for a network cable which my computer does not. I plugin my nokia phone and download to the micro SD card, and then move them to my real computer.

When i copy the files to the nokia, the progress bar is always on 0%, but the file does copy after some time, but without the progress bar making any progress.

As I install or open the copied files into my real computer, the files seem to have been corrupted by the file copying process.
F.e I downloaded a game called kerbal space program, and as I attempt to install it, windows raised a "not a valid win32" application error. Similarly, flv files and other media files get partly corrupted. 
Image files that was high-res become low res and full of strange artifacts.

ThIs does not happen with my usb drive, however I cannot use it as it is only 500 mb, and my micro sd card is 4 Gb


Edit*: I use ubuntu 11.10 and my phone is a nokia c1-01*

---

### Post by Cavsfan on 2012-08-08
It has been my experience that Windows does not like having files altered from outside of Windows.
You can read/copy them from a windows partition but, I do not suggest you do anything else with them.

I had never had to do a clean install of windows in my entire life time but, after messing with some files from within Ubuntu I had to do just that.
This is why I say this - from experience.

---

### Post by audiomick on 2012-08-08
If you want to continue using that method, I would consider getting a micro SD reader that you can use instead of the phone. I rather suspect that the problem arises through the communication between the phone and one of the computers.

It may be possible to correct that, although I wont be able to help.

The first thing would be to post the type of phone here. Maybe someone will look in here who knows of a problem.

You might like to try and isolate where the problem is occuring. Try transferring a file off the linux computer onto the phone and back to the linux computer, perhaps a high res image. Look at it on the phone and see if it is what it is supposed to be, i.e. check the properties and make sure the resolution is still correct. Transfer it back to the Linux computer and see what happens.

Transfer a file from the windows computer to the phone, try and check it's properties, copy it back to the windows computer and on to the Linux computer and compare what comes across.

Do you see what I mean? Try and figure out exactly where the problems are occuring.

If you can determine that the problem is definitely in the communication between the linux computer and the phone, you might be better to start a new thread with a title that mentions exactly that problem, and the model of the phone.

One other thing: I gather that what you refer to as your "real computer" is a desktop computer with windows installed on it. If this is the case, the neatest solution to your downloading problems would be to put a network card in that machine. I would suggest also installing a Linux on it as a dual boot to use for the internet.

---

### Post by avgudar on 2012-08-08
> **Cavsfan said:**
> It has been my experience that Windows does not like having files altered from outside of Windows.
You can read/copy them from a windows partition but, I do not suggest you do anything else with them.

I had never had to do a clean install of windows in my entire life time but, after messing with some files from within Ubuntu I had to do just that.
This is why I say this - from experience.
But this error happened just recently. It has worked for a long time in both older versions of ubuntu, kubuntu and linux mint, but now it never works.
I feel it is rather something wrong with the SD card or the phone. I have tried formatting the card but to no help.

> If you want to continue using that method, I would consider getting a  micro SD reader that you can use instead of the phone. I rather suspect  that the problem arises through the communication between the phone and  one of the computers.

It may be possible to correct that, although I wont be able to help.

The first thing would be to post the type of phone here. Maybe someone will look in here who knows of a problem.

You might like to try and isolate where the problem is occuring. Try  transferring a file off the linux computer onto the phone and back to  the linux computer, perhaps a high res image. Look at it on the phone  and see if it is what it is supposed to be, i.e. check the properties  and make sure the resolution is still correct. Transfer it back to the  Linux computer and see what happens.

Transfer a file from the windows computer to the phone, try and check  it's properties, copy it back to the windows computer and on to the  Linux computer and compare what comes across.

Do you see what I mean? Try and figure out exactly where the problems are occuring.

If you can determine that the problem is definitely in the communication  between the linux computer and the phone, you might be better to start a  new thread with a title that mentions exactly that problem, and the  model of the phone.

One other thing: I gather that what you refer to as your "real computer"  is a desktop computer with windows installed on it. If this is the  case, the neatest solution to your downloading problems would be to put a  network card in that machine. I would suggest also installing a Linux  on it as a dual boot to use for the internet.HI, I edited the op just a few minutes ago, with ubuntu version and phone model. By real computer I mean stationary. I use them both just as much.
I will try what you suggested and get back to you. The stationary has a network card but it does not wor, or the problem might lie in the socket in which you but the cable. The CD/DVD Drive does not work in the stationary computer., so I can't dual boot. Also, I can't boot from a usb drive.

I actually have a micro card reader. I thought it only took big SD cards, but it appears to take small ones as well. I will try to see if that works first. 

I don't think I made myself clear regarding the pictures. The pictures embedded within a install file get's corrupted. As an example I downloaded a few racing games from gametop and when I installed them (they installed correctly unlike other applications for some reason), the textures where low res and full of artifacts. Copying a picture i've taken with the phone appears to work.
The problem I think is files not being copied to 100%, but rather 99.99 or something.

---

### Post by audiomick on 2012-08-08
> **Cavsfan said:**
> It has been my experience that Windows does not like having files altered from outside of Windows.
You can read/copy them from a windows partition but, I do not suggest you do anything else with them.

I had never had to do a clean install of windows in my entire life time but, after messing with some files from within Ubuntu I had to do just that.
This is why I say this - from experience.

Firstly, whilst the information is good to know, I don't think it is relevant to the problems the OP is having. 

Secondly, I have a dual boot on my laptop, Visat and Ubuntu 10.04. I routinely open, work on and save back files that are on the Windows data partition (not the partition that the windows OS install is on) from either the Ubuntu dual boot install on that machine, or via Samba share from my desktop, both with the laptop booted into windows and with it booted into Ubuntu. I have never had a problem doing this.

As far as I know, the problems that you refer to can occur if you mount a Windows system partition to a Linux filesystem.

---

### Post by audiomick on 2012-08-08
> **avgudar said:**
> I feel it is rather something wrong with the SD card or the phone. 

You could very well be right there. Have you had an update of the Linux system? Can you say for sure that the problems started after the update?

Are you able to borrow a card from someone and see if it works right with a different card? 

As I said in my first post, you need to try and isolate exactly where the problem is occuring. If you can't definitely connect the change in behaviour with some change in the system, you need to alter the various factors involved one at a time to try and figure out what is causing the problem.

If you have had an upgrade of your Linux OS, I would suspect that the new OS version has acquired a problem talking to the phone. 

If there hasn't been an upgrade, or if the problem did not start immediately after the upgrade, the card itself would be my first suspect. As I said, try and borrow a card from someone else and see if that works.

---

### Post by Cavsfan on 2012-08-08
> **audiomick said:**
> Firstly, whilst the information is good to know, I don't think it is relevant to the problems the OP is having. 
That is good.

> 
As far as I know, the problems that you refer to can occur if you mount a Windows system partition to a Linux filesystem.Precisely! Mounting it and modifying files on a windows partiton from a Linux system is exactly what I am talking about.
It may not happen but, then again it may. I am just saying don't take a chance by doing that.

But, if I misinterpreted what the OP was doing you can probably help more than I can.
I just thought I would mention it as it did happen to me.

---

### Post by audiomick on 2012-08-08
> **Cavsfan said:**
> But, if I misinterpreted what the OP was doing


He is not mounting his windows file system onto the Linux one. He is copying files off a Linux computer on to a Nokia phone and then from the phone onto a Windows computer. When the files arrive on the windows machine, they are corrupted.

---

### Post by avgudar on 2012-08-08
I use ubuntu 11.10 with no updates. The only installed software is adobe  flash for mozilla firefox from the multiverse source. It has worked  well i the past and there is no reason why it shouldn't now.
Copying via the micro SD card reader seems to work. I tried downloading nethack  3d and copying it to the SD card and install it on the stationary  computer. The bug with the progress bar still remains, though. It could just be a coincidence that it worked. I will  have to try some more. I don't know if the files where corrupted, they  might have been, we'll see. The textures appear to be quite bad, but  from the screenshot's i've seen of nethack 3d i think that's the way the  game was designed.  :guitar:
I will try booting linux mint from the cd and see if it works. THat would conclude if the problem lies in ubuntu or the SD card.

---

### Post by Cavsfan on 2012-08-08
> **avgudar said:**
> I use ubuntu 11.10 with no updates. The only installed software is adobe  flash for mozilla firefox from the multiverse source. It has worked  well i the past and there is no reason why it shouldn't now.
Copying via the micro SD card reader seems to work. I tried downloading nethack  3d and copying it to the SD card and install it on the stationary  computer. The bug with the progress bar still remains, though. It could just be a coincidence that it worked. I will  have to try some more. I don't know if the files where corrupted, they  might have been, we'll see. The textures appear to be quite bad, but  from the screenshot's i've seen of nethack 3d i think that's the way the  game was designed.  :guitar:
I will try booting linux mint from the cd and see if it works. THat would conclude if the problem lies in ubuntu or the SD card.

It is good that you have more than one OS to check the problem out on. I have 3 Ubuntus and Windows 7.
Hopefully it is just an issue with one of them.
Good luck! :)

---

### Post by audiomick on 2012-08-08
> **avgudar said:**
> I use ubuntu 11.10 with no updates. The only installed software is adobe  flash for mozilla firefox from the multiverse source. It has worked  well i the past and there is no reason why it shouldn't now.

Ok, so if you have a continuing problem, it is most likely the card or something on the phone.

> I will try booting linux mint from the cd and see if it works. THat would conclude if the problem lies in ubuntu or the SD card.

Yes, good idea. 

If you are now getting successful transfers, then maybe you had a "temporary" fault. I don't like those, I prefer to be able to find a definite fault and know what it was, but if everything is working again now then maybe something was just hung up somewhere and has sorted itself out.

---

### Post by avgudar on 2012-08-08
It works perfectly in linux mint. Looks like unbuntu had everything to do with it. 
I'd say this problem is if not fixed then atleast managable.
I'll still try diffrent method to get it to work in ubuntu. I'm going to try to format it in linux mint.
I don't know if this has anything to do with the problem, but there are alot of hidden files within the SD card with the extension .chk
I googled it and i guess it's some sort of chache file? There is also a fodler called predeftmp that wasn't there before.

---

### Post by audiomick on 2012-08-08
> **avgudar said:**
> It works perfectly in linux mint. Looks like unbuntu had everything to do with it. 

Yes, looks like it.

As far as the .chk files go, I found a list here
[https://en.wikipedia.org/wiki/List_of_file_formats_%28alphabetical%29#CHK]("https://en.wikipedia.org/wiki/List_of_file_formats_%28alphabetical%29#CHK")

I reckon the recovered files from CHKDSK is likely. CHKDSK is the file system repair tool from windows. If it was run on that card, there are possibly left-over files still on there. If you are not in the middle of trying to recover lost files on there with CHKDSK, I reckon you can just delete them. I doubt, however, that they are really relevant to the current problem.

The other thing, that folder called predeftmp looks like a temporary folder, in the sense of a folder for short term storage of stuff by some program. Did it show up since you accessed the card with Mint? It is possible that this is a folder that is created automatically by Mint. Similar to the .trash folder that always appears on a portable medium like a USB stick when you plug it in to an Ubuntu machine or a Mac.

If you are convinced that the problem is between Ubuntu and the phone, consider starting a new thread with a title more specific to that, i.e. the problem and the make and model of the phone in the title. You might attract some more useful help that way.

---

### Post by Cavsfan on 2012-08-08
Glad you got it figured out and it was just Ubuntu that caused it. Good luck! :)

---

### Post by avgudar on 2012-08-08
QUick reply before i go to sleep:

I tried with a mass storage devide and the bug keeps occuring. This prooves that it is indeed ubuntu and not my phone or micro SD.
I wish I knew what was causing it.

> I reckon the recovered files from CHKDSK is likely. CHKDSK is the file  system repair tool from windows. If it was run on that card, there are  possibly left-over files still on there. If you are not in the middle of  trying to recover lost files on there with CHKDSK, I reckon you can  just delete them. I doubt, however, that they are really relevant to the  current problem.

The other thing, that folder called predeftmp looks like a temporary  folder, in the sense of a folder for short term storage of stuff by some  program. Did it show up since you accessed the card with Mint? It is  possible that this is a folder that is created automatically by Mint.  Similar to the .trash folder that always appears on a portable medium  like a USB stick when you plug it in to an Ubuntu machine or a Mac.

Yes, today when i tried copying to windows windows detected an error in the SD card and wanted repair it, so you are right.
It did not fix the problem, though.
THe predeftmp is a nokia folder, I have discovered. So it is not important.

---

