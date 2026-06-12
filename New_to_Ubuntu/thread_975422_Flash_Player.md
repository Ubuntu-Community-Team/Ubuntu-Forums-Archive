---
title: "Flash Player"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by txfour on 2008-11-08
I just installed Ubuntu and am in the process of getting everything in order. I noticed that I am unable to view You Tube videos. It tells me I need to download the latest flash player. When I download it it still won't work. 

How do I do this successfully? 

Thanks

---

### Post by Sirron on 2008-11-08
Did you install flash from Synaptic?

---

### Post by tjwoosta on 2008-11-08
if you install the ubuntu-restricted-extras it will install flash as well as a whole bunch of other usefull stuff

or you could just install flash alone (its listed as flashplugin-nonfree)


edit: 
just in case you dont already know, synaptic is located at system-preferences-synaptic package manager

---

### Post by kansasnoob on 2008-11-08
I would begin by installing ubuntu-restricted-extras:

```
sudo apt-get install ubuntu-restricted-extras
```

Of course change that to kubuntu or xubuntu if that's what you're running.

You'll then need to restart Firefox: File > Quit, then restart.

I'm assuming this is Ubuntu 8.10 (Intrepid Ibex), if it's an older version let us know.

Edit: Just happened to think you'll perhaps need to go to System > Administration > Sotware Sources, and under the "Third Party" tab make sure that Intrepid Partner is ticked.

---

### Post by Sirron on 2008-11-08
> **kansasnoob said:**
> Edit: Just happened to think you'll perhaps need to go to System > Administration > Sotware Sources, and under the "Third Party" tab make sure that Intrepid Partner is ticked.

Isn't the Partner repository only for proprietary software sold by Canonical?

---

### Post by philinux on 2008-11-08
The partner repo only has adobe-flashplugin and opera in it.

---

### Post by txfour on 2008-11-08
Thanks to all for the responses. I am running 8.04 LTS. Sorry for the stupid questions,but how do I install the "restricted-extras". It's going to take me a while to figure out how to do all of this stuff in Linux. I like it alot so far and am sick of Windows Vista. 

Thanks

---

### Post by kansasnoob on 2008-11-08
In 8.04 I'd go to the terminal and:

```
sudo apt-get install ubuntu-restricted-extras
```

But I've found the new Flash 10 to be much superior so I'd also:

```
sudo apt-get remove --purge flashplugin-nonfree
```

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

Then install the .deb from here:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Then restart Firefox, File > Quit, then start Firefox and hopefully you'll have a working flash.

---

### Post by hictio on 2008-11-08
On my Intrepid install, did this, on a Terminal (Applications -> Accessories -> Terminal), typed:
```

sudo aptitude install ubuntu-restricted-extras flashplugin-nonfree libflashsupport (ENTER)

```

It will ask your password, download and install the plugins.
After that, Flash is working perfectly.

---

### Post by kansasnoob on 2008-11-08
> **philinux said:**
> The partner repo only has adobe-flashplugin and opera in it.

Thanks Phil. I've just been making it a habit to include ticking the partner repo immediately after installing.

Then I "reload", select all of my favorite apps to add/remove, start the process and forget about it!

---

### Post by txfour on 2008-11-08
> **kansasnoob said:**
> In 8.04 I'd go to the terminal and:

```
sudo apt-get install ubuntu-restricted-extras
```

But I've found the new Flash 10 to be much superior so I'd also:

```
sudo apt-get remove --purge flashplugin-nonfree
```

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

Then install the .deb from here:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Then restart Firefox, File > Quit, then start Firefox and hopefully you'll have a working flash.

Thanks. I'll give it a whirl. You say got to "terminal". Not familiar with that term. Expand please. 

Thanks

---

### Post by kansasnoob on 2008-11-08
> **txfour said:**
> Thanks. I'll give it a whirl. You say got to "terminal". Not familiar with that term. Expand please. 

Thanks

Go to Applications > Accessories > Terminal. Just "copy-n-paste" my commands (one at a time), it'll ask for your password (same one you log in with) after the first command. You won't see anything appear when you type your password.

If you run into problems please copy-n-paste the text of the terminal here so we can see what's going on.

---

### Post by XxX_VLAD_XxX on 2008-11-15
Hi,I have the same problem. I tried almost everything, 
I download the .deb package from adobe.com and installed it, (didn't work)
I installed the restricted-extras        (didn't work)
I even installed this

> **hictio said:**
> On my Intrepid install, did this, on a Terminal (Applications -> Accessories -> Terminal), typed:
```

sudo aptitude install ubuntu-restricted-extras flashplugin-nonfree libflashsupport (ENTER)

```

   AND STILL NOTHING

Any Ideas?

---

### Post by simtaalo on 2008-11-15
> **XxX_VLAD_XxX said:**
> Hi,I have the same problem. I tried almost everything, 
I download the .deb package from adobe.com and installed it, (didn't work)
I installed the restricted-extras        (didn't work)
I even installed this

   AND STILL NOTHING

Any Ideas?

what system are you using?

---

### Post by XxX_VLAD_XxX on 2008-11-15
I have Ubuntu 8.04,
FireFox 3 Beta 5 (default from the 8.04)

It's not the first time I installed it (the OS), in a previous installed of the same OS I did download and install the plugin and worked, but that time I downloaded and install directly from FireFox Extensions.

Then I had to Install Ubuntu 8.04 again because Grub didn't load, it showed Error 15 or something, I've been using Ubuntu for three weeks now so I didn't have much to lose. So I reinstalled it

Now Firefox doesn't ask me (like when I enter a page like Youtube) for the plugin as it did before in this install of 8.04, probably because I already install the .deb package, but it doesn't show the video.

Maybe it's something about JavaScript, I really don't know what to do

---

### Post by metallicamike on 2008-11-15
what type of file was it? if it was tar.gz than extract it and click on the piece of paper with an icon. if it is deb than just double click it

---

### Post by XxX_VLAD_XxX on 2008-11-15
It was a .deb package, it's really weird 'cause I can see i installed it in the plugins of Firefox, but it doesn't work, maybe is because i have the BETA version I'll upgrade and try again, wish me luck.   By the way cool avatar!

---

### Post by sportscrazed2 on 2008-11-15
i know this sounds too simple too be true but did you restart firefox after installing the flash player?  if not thats your problem same thing happened to me

---

### Post by metallicamike on 2008-11-17
that would do it, also u can try to reinstall it too, and go to preferences in firefox and make sure that javascript is on too

---

### Post by ken_do_san on 2008-11-18
I just fixed this problem in Flock (it's based on Firefox), I tried the .deb package at adobe - fail, I tried the repository for the adobe and non free adobe as well - both fail.  I went back to the adobe page and downloaded the install_flash_player_10_linux.tar.gz package, extracted it then I went into the new directory, left clicked on flashplayer_installer and it opened the console, I just followed the prompts (there was only a couple of them) it created a .mozilla directory in the home directory.

I reopened Flock, opened preferences and under applications it has automatically picked up the flash player to use, checked it out and all good, now have flash video's working.

This will work for Firefox as well.

Hope I've explained it so its easy to follow.

---

