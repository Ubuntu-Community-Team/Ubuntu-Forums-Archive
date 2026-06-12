---
title: "Aspire One wireless connection"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by kobusvw01 on 2012-09-11
I have just loaded ubuntu on my wife's Aspire One Notebook but cannot get the wireless connection setup to work. I have manged to get it to connect for a short while, but was unable to access the internet.  I have tried all sorts of settings, but no luck.  Can anybody help please, I am desperate.

Thanks (in advance)

---

### Post by cortman on 2012-09-11
What model Aspire One is it? I know in some models (my own included) you have to set network boot to first in the BIOS options before the wifi will work (and not freeze up the desktop).
Please post the output of

```
lspci
```

---

### Post by kobusvw01 on 2012-09-11
It a AOA 110-aw.

---

### Post by alpage2 on 2012-09-11
My Acer Aspire One is the AOA-110-Ap - and the wireless works 'out of the box'.

Since these netbooks were originally offered with the Linpus-Lite linux distro, it should be possible to make it work.

The first step is to answer cortman's request for the output of lspci. Start a terminal window, and at the command prompt, type:

```

lspci

```
and hit ENTER.

Copy and paste the response into your reply to this thread.

Alan

---

### Post by kobusvw01 on 2012-09-12
Thanks for the help, but I don't even know how to'start a terminal window' in order to type in lspci.   When I said absolute beginner, that is what I meant. Please?

---

### Post by Hadaka on 2012-09-12
Hi, to start a terminal press ctrl/alt/t  a black box..term will come up
copy and past this command

```
lspci -nnk | grep -iA3 net
```

press enter, copy the results of the above command and post

---

### Post by alpage2 on 2012-09-12
Hello kobusvw01

Hadaka has added some useful options to the command which will help reduce the volume of irrelevant output - so there will be less to copy and paste.

Copying from the terminal will require you to click and drag the mouse cursor over the text to select it, and then use the 'Edit' drop-down menu and select 'Copy'.

Where to find the drop-down menu may not be immediately obvious. If the terminal window is not maximised when it first opens, you will have a terminal window on the screen that is smaller than your total screen dimensions, and there will not be any drop-down menus at the top of the terminal window, itself.

It doesn't matter - make sure the terminal window is either the only application window open, or if more than one, that it is the one that currently has focus, and move your cursor to the top of the screen, towards the left half of the screen. The drop-down menus for the terminal window will appear when the cursor reaches the top - just one of the quirks of the Unity desktop ;)

Alan

---

### Post by kobusvw01 on 2012-09-13
Thanks alpage2.  the problem is not the copy command, but since I am unable to get the internet to connect, and cannot get the machine to read a flash drive, there is no way for me to get the information from the Acer to my desktop.

I have attached a jpg photo I have taken of the screen on a threat I have posted yesterday, but now I cant find it.

Thanks for all your help, but I think I will take it to a Linux fundi to assist.

---

### Post by alpage2 on 2012-09-13
Hello kobusvw01

If you have multiple problems, a local linux expert might be a simpler way to go - but just a couple more options for you:

Do you have an ethernet port on your netbook, and on your modem/router? A short ehernet cable may be all you need to get on the internet.

When you insert the USB stick, does a file manager window open, displaying the root directory of the stick? They don't always - but if you scroll down the icons on the left-hand margin of the screen, you may find one lurking down out of sight - click on it and you should get the aforementioned file manager window.

Failing that, click on the file manager icon - the orange folder - to get a file manager window - down the left margin of that will be listed the drives - does the usb stick have an entry there? If not, try another stick ;)

Alan

---

### Post by NikTh on 2012-09-13
> **Hadaka said:**
> Hi, to start a terminal press ctrl/alt/t  a black box..term will come up
copy and past this command

I use too the black box with green letters.. but the terminal in Ubuntu is not black from default . :lolflag:

---

### Post by kobusvw01 on 2012-09-14
Thanks alpage 2.  I do have an ethernet cable connection.  However, I want to use the acer as a peripheral device for when I am travelling to work on and save my document through dropbox etc, so a cable is not really a workable solution. 

As far as the usb is concerned, as soon as I plug the flasdrive in, I get a message to say I need to be a 'superuser' to mount the drive,  The computer recognizes the drive in the file manger window by name and the icon is there but I cannot open it.

Thanks for your assistance.

---

### Post by newb85 on 2012-09-14
> **NikTh said:**
> I use too the black box with green letters.. but the terminal in Ubuntu is not black from default . :lolflag:

I can recall the days when the Ubuntu terminal was white; however, it is, and has been for some time (since about Maverick, I think), black.

---

### Post by cortman on 2012-09-14
> **newb85 said:**
> I can recall the days when the Ubuntu terminal was white; however, it is, and has been for some time (since about Maverick, I think), black.

No, it's purple background/gray text. I always change it myself.

---

### Post by newb85 on 2012-09-14
> **cortman said:**
> No, it's purple background/gray text. I always change it myself.

You're right about the background--it is indeed not black.

---

