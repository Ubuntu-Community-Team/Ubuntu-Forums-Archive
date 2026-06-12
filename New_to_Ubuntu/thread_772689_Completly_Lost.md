---
title: "Completly Lost"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Aspire36 on 2008-04-28
I just switched over from Vista to Ubuntu, finished the install today.  All I really wanted to get working on here was World of Warcraft. My friend recently installed Kubuntu and got everything working, I guess I'm just lost.

anyways, I've installed Wine. But something tells me I messed it up at some point somehow, and I cant figure out how to uninstall it to try it again. 

I used this page [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)  to try and figure it all out, but I'm just more lost than before. I'm using Hardy Hereon (8.04).

When I run winecfg from the terminal, I get this message before it opens. 


preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
preloader: Warning: failed to reserve range 00000000-00010000




It opens, but when I try to set my settings and close it like the page says, it does not leave a directory in my home folder.

So yeah, I don't have any idea how to go about getting WoW to work now.

---

### Post by dokdoom on 2008-04-28
The first time you run 'winecfg' it creates a direcotry in /home/user/.wine

if you are in /home/user/ and type 'ls' it won't display the directories with a '.' in front of them. So run this command and it will tell us if it created the directory or not.

cd ~/.wine

I recently did the same thing the other day you are trying to do. So if you have any other questions feel free to ask.

---

### Post by Aspire36 on 2008-04-28
:~$ cd ~/.wine
cd ~/.wine

So I guess it's there.

For the WoW DVD it tells me to enter this

sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/

(The installer was hidden) and I get this response. 

mount: /dev/scd0 already mounted or /media/cdrom0/ busy
mount: according to mtab, /dev/scd0 is mounted on /media/cdrom0

---

### Post by dokdoom on 2008-04-28
The way I did the install was just copying the files from the CD into a folder then running 

wine Install.exe (Not sure the exact name of the installer, I just typed wine In then tabbed it out. That was with the CD's though, not sure how to handle it that way with a DVD. In that guide it does say the easiest method is to just copy the required files from each CD though. I don't imagine why you couldn't do the same thing with the DVD's though.

---

### Post by starcannon on 2008-04-28
My favorite way to play windows games in linux is [Cedega]("http://www.cedega.com"). It costs $15 but it does most of the configuring for you. Whether you use Wine or Cedega, either way WoW works great, I've done both.

---

### Post by Tatty on 2008-04-28
to see the .wine directory in nautilus (the default file browser) open it and press ctrl+h - this shows the hidden directories.

The error you are seeing is happening becuase the cd drive is already mounted.  try ```
sudo umount /media/cdrom0
``` first

---

### Post by Aspire36 on 2008-04-28
I'm going to try running through it again.

I can copy the DVD to my comp, the problem is there is no installer in there, even when I view the hidden files. Just 6 installer tomes.

Also, I'm not getting this part about repositories. I have Wine installed now, and I can see it. I just don't understand how I add a repository or anything.

---

### Post by dokdoom on 2008-04-28
Wow really? No .exe files? I wish I had more experience using the DVD as an installer but sadly I do not. God speed sir.

---

### Post by Aspire36 on 2008-04-28
Nevermind, found the installer buried in there.

---

### Post by dokdoom on 2008-04-28
Oh sweet. wine <installer.exe> should send you on your way. Don't forget to do all the performance tweaks for your wine registry and your wtf.config as well.

---

### Post by Aspire36 on 2008-04-28
I miss windows... just put in a disc and click a button.

---

### Post by Tatty on 2008-04-28
> **Aspire36 said:**
> I miss windows... just put in a disc and click a button.

Lol thats how it is for most things in linux.  But when you are attempting to run software written for a closed source Proprietry OS in a different OS, its going to get messy ;)

---

### Post by Aspire36 on 2008-04-28
Yeah... I can't even get my audio driver to work... I know it's supported, I'm just retarded. (ALC97 codec)

---

### Post by tparker on 2008-04-28
If the DVD install gives you too much trouble you can also install by downloading the files from the WoW website, as long as your internet connection is up to that. Last time I needed to reinstall in Wine that is what I used and it worked great. This is assuming that you already have the WoW account set up from playing it in windows, but it should be similar for a new account if that is not the case.

Go to worldofwarcraft.com, click 'create account' from menu on the left of the screen. On the page that takes you to click the 'create account' button, this says it is for new or trial accounts but that's okay, click it anyway. On the page that goes to enter the authentication key from your WoW DVD, enter the scrambled letters in the security check area, then hit the 'continue' button. That should tell you that you already have an account and ask if you need to download the files for it, tell it yes and off you go. :)

---

### Post by Aspire36 on 2008-04-28
I have the drive mounted now.


The next step is telling me 

 Start the installation by opening a terminal and running these commands:

 cd /<path-to-directory>/
 wine Installer.exe


It's just not working right for me... (Obviously, I change the first line for the directory I saved it to)


This is the error message I get.

preloader: Warning: failed to reserve range 00000000-00010000
Warning: could not find DOS drive for current working directory '/media/cdrom0', starting in the Windows directory.
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
wine: could not load L"C:\\windows\\system32\\Installer.exe": Module not found
dean@Aspire:/media/cdrom0$ preloader: Warning: failed to reserve range 00000000-00010000

---

### Post by cmsimons on 2008-04-29
To fix the memory problem, follow the instructions in at this thread:

[http://ubuntuforums.org/showthread.php?t=770262](http://ubuntuforums.org/showthread.php?t=770262)

As for the sound mixer problem, I am having a similar one of my own and have yet to discover the solution, so I am currently unable to help you out there.

Christopher Simons

---

