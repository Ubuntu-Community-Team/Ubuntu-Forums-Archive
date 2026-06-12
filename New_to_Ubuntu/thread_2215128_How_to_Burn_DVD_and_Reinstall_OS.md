---
title: "How to Burn DVD and Reinstall OS?"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by TomBrooklyn on 2014-04-04
How do I install Ubuntu 12.04 on a computer?

I will use a CD.     

To make CD, Ubuntu website says click on downloaded iso file and select "Write to" and point to disk.    Clicking on file does not offer "Write to" Option. 

Also, the iso file seems to want to be extracted.    It seems to be compressed and non-functional without extraction.   But I extracted it and wound up with over a dozen files I don't know what to do with.

---

### Post by TomBrooklyn on 2014-04-04
CD doesn't work anyway.  CDs are no longer big enough.   So I will use a USB flash drive.   How do I install ubuntu with that?      I want to install 12.04 over a copy of 13.10 that is corrupted.   I am willing to format and wipe out the previous OS and all data.

---

### Post by TomBrooklyn on 2014-04-04
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

that won't work, because I am working on a windows machine.   my ubuntu computer is corrupted.

---

### Post by Bashing-om on 2014-04-04
TomBrooklyn; Hi !

I too had that wake up this AM, release 12.04.1 no longer fits on a CD , Shucks.

See if this link helps you,
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)

[INDENT]not much help
[INDENT][INDENT]but a prod in the right direction
[/INDENT][/INDENT][/INDENT]

---

### Post by edeneen on 2014-04-04
download the ISO file, open your burner software, right click burn ISO image, then point it at the ISO you downloaded

---

### Post by bshatt1987 on 2014-04-04
If you want to make an Ubuntu bootable USB and you're using Windows, this should help you:
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by HermanAB on 2014-04-05
Use a DVD.  It won't fit on a CD.

Use your Windows burner software and select something like: "Burn image to a CD".

---

### Post by Double.J on 2014-04-05
I too would do the bootable usb stick option from windows.

In my experience pay special attention to 'do not use quick format' when formatting in wibdows. It'll take a lot longer, but you get a lot less errors!

---

### Post by buzzingrobot on 2014-04-05
> **TomBrooklyn said:**
> [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

that won't work, because I am working on a windows machine.   my ubuntu computer is corrupted.

There are instructions on that page for Windows and OX X, as well as Ubuntu.

---

### Post by Mark Phelps on 2014-04-05
IF you don't already have image burning software in MS Windows, then download and use Imgburn -- it's free.

---

### Post by mastablasta on 2014-04-05
to stick Ubuntu image on a USB stick in windows use unebootin or linuxliveusb

---

### Post by edeneen on 2014-04-05
> **mastablasta said:**
> to stick Ubuntu image on a USB stick in windows use unebootin or linuxliveusb

the OP specifically said he wanted to use a CD (dvd, in this case)

---

### Post by monkeybrain20122 on 2014-04-05
> **edeneen said:**
> the OP specifically said he wanted to use a CD (dvd, in this case)

Maybe OP is not aware of the usb option. Seriously unless your hardware is 10+ years old and doesn't support booting usb there is no reason to still burn CDs/DVDs. It is bulky and slow and the burning process is error prone.

---

### Post by sotiris2 on 2014-04-05
OP is aware of the usb option and in fact stated he wants to use that in his second post.

---

### Post by TomBrooklyn on 2014-04-06
I tried USB first.  Didn't work. 

Now I've made a DVD.  That doesn't work either. 

Is there some way to get this corrupted OS off of my laptop?     The display screen is all noise and I have no visual display.

---

### Post by SuperFreak on 2014-04-06
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows")

---

### Post by monkeybrain20122 on 2014-04-06
> **TomBrooklyn said:**
> I tried USB first.  Didn't work. 

Now I've made a DVD.  That doesn't work either. 

Is there some way to get this corrupted OS off of my laptop?     The display screen is all noise and I have no visual display.

Well what do you mean by usb didn't work? That you have no option in the BIOS to boot from usb? That you have the option and set it to be first but usb didn't boot? That usb did try to boot but hanged? Or usb booted into blackscreen/corrupt desktop?

Each scenario is different and you have to give us more details. 

With usb you don't have to worry about factors like bad burn, dvd drive problems and burner problems. unetbootin is a much simpler program than a dvd burner so less chance of that having bugs.

---

### Post by buzzingrobot on 2014-04-07
In your first post, you said:>  To make CD, Ubuntu website says click on downloaded iso file and select  "Write to" and point to disk.    Clicking on file does not offer "Write  to" Option. 

That's not exactly correct.  The instructions for Windows 7 -- there are other instructions for other versions of Windows -- says to "right-click" on the ISO image.  Not "click". 

Those instructions work. If you are unable to create a bootable DVD (you must use a DVD, not a CD), or USB, and assuming the DVD or USB are not faulty, then if you report, here, exactly what you did and post the text of the messages displayed on screen, then people will be in a better position to assist you. General complaints that something did not work cannot be addressed.

---

### Post by mörgæs on 2014-04-07
I think we need to know the hardware specifications in detail. Could explain why all install attempts fail.

---

### Post by buzzingrobot on 2014-04-07
> **TomBrooklyn said:**
> 

Also, the iso file seems to want to be extracted.    It seems to be compressed and non-functional without extraction.   But I extracted it and wound up with over a dozen files I don't know what to do with.

It *is* a compressed file and its components *can be* extracted.  You don't want to do that, though. The file needs to be left as it is to create a bootable image.

To create a bootable USB or DVD, the ISO image must be *burned*, as is, unextracted, to the USB or DVD.  Saving it, as you would for an ordinary file, will not work.  That is the case in any OS.

---

