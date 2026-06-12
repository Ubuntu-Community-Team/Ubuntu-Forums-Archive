---
title: "Trying Ubuntu From USB, Garbled Graphics"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by d_schaefer on 2014-03-14
> HP Pavilion 6605us
AMD Athalon 64 X2 Dual Core TK-55 1.8 Ghz processor
2GB RAM (maxed, unfortunately)
Nvidia GeForce 7150M / nForce 630M

I've been running Mint on the above machine for some time and I've had numerous issues with it.  I want to try Ubuntu before I revert back to Windows.  I'm trying to give it a go via a live USB, but when it boots I get a jumbled mess on screen.  I used Unetbootin to make the live USB.

I remember having the same issue when I started with Mint, I think I had to boot to recovery and try different Nvidia drivers.  But, I can't figure out how to do that with the live USB.  Is that possible or do I need to go ahead and install Ubuntu in order to make this work.

You'll have to talk to me like a 4 year old, I'm a complete Linux rookie. I can find my way around computers just fine, but I don't understand the terminology so I'll need the super for dummies explanation. :-P

Thanks.

---

### Post by grahammechanical on 2014-03-14
The Ubuntu live session does not run a proprietary video driver. You can try this:

1) At the first purple screen press Enter
2) At the second screen select the language and press Enter. English is the default.
3) At the third screen with the Try Ubuntu - Install Ubuntu options press F6
4) A drop down menu will appear bottom right of the screen. Select nomodeset and press Enter
5) Press ESC to get back to the Try Ubuntu - Install Ubuntu screen
6) Make sure that Try Ubuntu is selected and press Enter.

See what happens. My advice if you go for an install is not to tick the Install Third Party Software option. Otherwise the installer will install a proprietary video driver and you may have a repeat of your previous problem.

We can install a proprietary video driver after installation and also the Ubuntu Restricted Extras package and get the same third party package of software.

Regards.

---

### Post by thenh813 on 2014-03-14
Ok, first of all, when you get the mess of text, is the Caps Lock/Num Lock lights on your keyboard blinking? If so, you have a kernel panic, the Linux equivalent of the infamous Windows BSOD.

Second of all, what does it say? Is it possible to take a picture and post it to something like postimage.org and put the image in a reply?

Third of all, I like to help people new to Linux, explaining things in a simple way is no problem.

Fourth, id you check the MD5SUM of the downloaded ISO? I will tell what that means and how.

Every file will have a different MD5, and if the file is corrupted or modified, even a single one or zero flipped around, it will be different. Next to the download link there is a MD5. Go to Linux Mint open a terminal. Run the following command on the file (ISO) you downloaded:

```

md5sum "/path/to/your/file.ISO"

```

You will get something like this:
```

ea0a4c09767b152f678070d8e40fe61c  /home/user/Desktop/Tux-The-Penguin.png

```

Copy and paste it into gedit or similar.
Goto the Ubuntu website and check the MD5 for the file you downloaded.
Copy and pase it next to the other one.

Compare them, if they dont match (capitilization makes no difference) you have a corrupt copy and something went wrong in the download. Redownload it, erase the flash drive's copy of Ubuntu and re write it with Unetbootin if this is the case.

After you reply with the information, I will try to help you further.

---

### Post by thenh813 on 2014-03-14
@[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")
Why do I take so long to post someone posts before me haha.

---

### Post by d_schaefer on 2014-03-14
> **grahammechanical said:**
> The Ubuntu live session does not run a proprietary video driver. You can try this:

1) At the first purple screen press Enter
2) At the second screen select the language and press Enter. English is the default.
3) At the third screen with the Try Ubuntu - Install Ubuntu options press F6
4) A drop down menu will appear bottom right of the screen. Select nomodeset and press Enter
5) Press ESC to get back to the Try Ubuntu - Install Ubuntu screen
6) Make sure that Try Ubuntu is selected and press Enter.

See what happens. My advice if you go for an install is not to tick the Install Third Party Software option. Otherwise the installer will install a proprietary video driver and you may have a repeat of your previous problem.

We can install a proprietary video driver after installation and also the Ubuntu Restricted Extras package and get the same third party package of software.

Regards.

Hmm, I don't get those screens when I boot from USB.   I get an HP screen where I press F9 to choose to boot from USB, then I get a Unetbootin menu for install or try without installing.  Pressing F6 there only resets the countdown timer.  I've attached a picture of the Unetbootin menu screen.
[ATTACH=CONFIG]251157[/ATTACH]

---

### Post by d_schaefer on 2014-03-14
> **thenh813 said:**
> Ok, first of all, when you get the mess of text, is the Caps Lock/Num Lock lights on your keyboard blinking? If so, you have a kernel panic, the Linux equivalent of the infamous Windows BSOD.

Second of all, what does it say? Is it possible to take a picture and post it to something like postimage.org and put the image in a reply?

It boots to the desktop, but the desktop is all jacked up.  The taskbar is in the middle of the screen but you still need to click on the left side of the screen.  Things are repeated across the screen.  This is the same thing that happened when I first installed Mint.  Here are a couple of pics:

[ATTACH=CONFIG]251158[/ATTACH][ATTACH=CONFIG]251159[/ATTACH]

> **thenh813 said:**
> Third of all, I like to help people new to Linux, explaining things in a simple way is no problem.

Fourth, id you check the MD5SUM of the downloaded ISO? ...

Checked the MD5SUM and it matches.

---

### Post by thenh813 on 2014-03-14
Oh, yeah that is messed up. Definitely graphics driver epic fail.

Ok at the UNetbootin menu, go down to try Ubuntu without installing, and press tab. Use the arrows to move to the part where it says quite splash and replace them with xforcevesa. Dont change anything else. This will force it to use the VESA failsafe graphics driver which should always work. Please note that in VESA mode OpenGL is not available. This is a temporary fix, after you would be able to install Ubuntu, you would install the real drivers from additional drivers and everything would work just fine. The reason you are probabally having the problem is that Nouveau, the open source Nvidia driver does not support or has trouble with the GPU. Real Nvidia drivers would work.

Lets first see if using VESA fixes this before a install is attempted.

---

### Post by d_schaefer on 2014-03-15
I'll give that a try.

This is one of my frustrations with Mint.  I tried the recommended Nvidia driver (304.88-0ubuntu1) and it mostly worked, but it would hang on boot fairly regularly.  There was another Nvidia (304.88-0ubuntu2) but it was the same.  Tried the Neuveau and it was a disaster, like this.  I finally installed a very old Nvidia driver (173.14.37-0ubuntu1, the only other option) that seems to work ok, but I've had issues with a couple programs I need to run in Wine and some other occasional graphics anomalies.  I looked at other options from Nvidia's website, but it was an involved process to install them so I never tried it.  I'm hoping Ubuntu has better results.

---

### Post by d_schaefer on 2014-03-15
No luck, exact same result.  I tried it twice to be sure I typed it correctly.

What I did exactly was boot to usb, use the arrow keys to select 'try without installing", press tab and a line of text at what looks like a command prompt appeared, use the arrow keys I moved the cursor to the end of the "quiet splash" text and then used backspace to delete it, I then typed in "xforcevea" and hit enter.  It booted slightly differently as it showed all the command line text and did not show the purple Ubuntu splash screen.  Once at the desktop, though, it looked exactly the same.

I'm not apposed to trying an install and seeing if I have better luck.  This machine is old and tired, I'm trying to squeeze some more life out of it if I can.

---

### Post by d_schaefer on 2014-03-15
I decided to bite the bullet and go ahead and install.  Nice idea, but even the install screens are an unreadable mess:

[ATTACH=CONFIG]251192[/ATTACH]

At this point I'm about done, I'm likely installing Windows 7 tomorrow.  I really wanted to give Ubuntu a try, but it doesn't seem like it's going to work.

---

### Post by JKyleOKC on 2014-03-15
It **might** work with Xubuntu or Lubuntu, both of which are a bit more compact than Ubuntu itself and have much less "eye candy" which in turn means no need for as much graphics power. I base this thought on the fact that the default desktop in Ubuntu does a lot of fancy graphics work, and avoiding that might let you move toward a solution.

In message #9 above, there's a typo in what you typed -- "vea" should be "vesa" so if you left out the "s" when booting it would have had no effect...

---

### Post by d_schaefer on 2014-03-15
Hmm, I'm pretty sure I typed vesa, I might give it a go one more time tomorrow to see.

I'm really not looking to try a bunch of flavors, but I wanted to try Ubuntu.  I tried Mint, thinking it would be better than the Vista that it came with.  In some ways it was, but too many other annoyances were added back in.  I've been told others had similar experiences with Mint and didn't have them with Ubuntu, so I wanted to give it a shot. I won't go back to Vista, I'm going to try Win7 because I've heard it's a bit less demanding than Vista.  If that fails, I'm going back to XP.

---

### Post by d_schaefer on 2014-03-16
Gave it one more try, double checking that I typed xforcevesa.  I even tried both the try without installing and trying to install.  Both resulted in the same garbled graphics as before.

I guess I'm back off to Windows world.  Hoping Win7 will run, but I'm a bit doubtful.

---

