---
title: "Ok, I need help getting photos on my computer."
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Obero on 2008-11-29
I have a Sony Cybershot DSC W110, and on Windows, all I'd have to do is install a software from the CD given and then put an output USB into the camera and input it into the computer and the pictures would come out into the software.

I'm not sure how to do this on Ubuntu, I have Wine installed if that helps. Also, when we put the USB in, a pop-up came in and we tried to "import" the pictures from the USB folder and it wasn't a good connection it said.
Thanks in advance.

---

### Post by __Ryan__ on 2008-11-29
The easiest way is to use a get a USB media card reader or use one installed on your computer.  

A second option is to install teh gphoto2 package:

```
sudo aptitude search gphoto2
```

And gtkam if you want a nice GUI frontend:

```
sudo aptitude search gtkam
```

This will let your computer easily interface with your camera and download the files to your computer.

---

### Post by Obero on 2008-11-29
> **__Ryan__ said:**
> The easiest way is to use a get a USB media card reader or use one installed on your computer.  

A second option is to install teh gphoto2 package:

```
sudo aptitude search gphoto2
```

And gtkam if you want a nice GUI frontend:

```
sudo aptitude search gtkam
```

This will let your computer easily interface with your camera and download the files to your computer.

Okay, let's see both options. How do I use my USB media card? I don't even think I have one.

Okay, I installed gphoto2. How do I use it?

---

### Post by oilchangeguy on 2008-11-29
> **Obero said:**
> I have a Sony Cybershot DSC W110, and on Windows, all I'd have to do is install a software from the CD given and then put an output USB into the camera and input it into the computer and the pictures would come out into the software.

I'm not sure how to do this on Ubuntu, I have Wine installed if that helps. Also, when we put the USB in, a pop-up came in and we tried to "import" the pictures from the USB folder and it wasn't a good connection it said.
Thanks in advance.

your best bet is to pull the sd card from the camera, and insert it in your computers card reader. if the computer does not have a card reader you can buy one for under 20.00. and they work out of the box.

---

### Post by Obero on 2008-11-29
> **oilchangeguy said:**
> your best bet is to pull the sd card from the camera, and insert it in your computers card reader. if the computer does not have a card reader you can buy one for under 20.00. and they work out of the box.

Computer's card reader? That seems a bit like taking out bits and pieces of the computer, which I can't do.

---

### Post by oilchangeguy on 2008-11-29
> **Obero said:**
> Computer's card reader? That seems a bit like taking out bits and pieces of the computer, which I can't do.

do you not know if your computer has a card reader???????? and let me rephrase my you can buy one statement, so you'll understand. it's an external reader you plug it into a usb port. you do understand where the usb ports are, right??????

---

### Post by Flimm on 2008-11-29
Your digital camera probably has an SD card, like [the ones pictured here.](http://images.google.com/images?q=sd%20card&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-GB:unofficial&client=firefox-a&um=1&sa=N&tab=wi)
SD card readers are often included with your computer, if not, you can buy external ones quite cheaply. Here are some pictures of [SD card readers.](http://images.google.com/images?q=sd%20card%20reader&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-GB:unofficial&client=firefox-a&um=1&sa=N&tab=wi)

---

### Post by __Ryan__ on 2008-11-29
Here is a simple tutorial for gtkam:

[http://www.gphoto.org/doc/manual/quickstart.html#using-gtkam]("http://http://www.gphoto.org/doc/manual/quickstart.html#using-gtkam")

---

### Post by Obero on 2008-11-29
> **oilchangeguy said:**
> do you not know if your computer has a card reader???????? and let me rephrase my you can buy one statement, so you'll understand. it's an external reader you plug it into a usb port. you do understand where the usb ports are, right??????

um no...


Just kidding, but how do they look? The card reader.

---

### Post by Obero on 2008-11-29
> **Flimm said:**
> Your digital camera probably has an SD card, like [the ones pictured here.](http://images.google.com/images?q=sd%20card&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-GB:unofficial&client=firefox-a&um=1&sa=N&tab=wi)
SD card readers are often included with your computer, if not, you can buy external ones quite cheaply. Here are some pictures of [SD card readers.](http://images.google.com/images?q=sd%20card%20reader&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-GB:unofficial&client=firefox-a&um=1&sa=N&tab=wi)

If these are external, I don't think I have one.

Any other way?

---

### Post by oilchangeguy on 2008-11-29
> **Obero said:**
> um no...


Just kidding, but how do they look? The card reader.

here's the one i own:
[http://shop.sandisk.com/DRHM/servlet/ControllerServlet?Action=DisplayCategoryProductListPage&SiteID=sdiskus&Locale=en_US&Env=BASE&categoryID=11448300](http://shop.sandisk.com/DRHM/servlet/ControllerServlet?Action=DisplayCategoryProductListPage&SiteID=sdiskus&Locale=en_US&Env=BASE&categoryID=11448300)

---

### Post by Obero on 2008-11-29
> **oilchangeguy said:**
> here's the one i own:
[http://shop.sandisk.com/DRHM/servlet/ControllerServlet?Action=DisplayCategoryProductListPage&SiteID=sdiskus&Locale=en_US&Env=BASE&categoryID=11448300](http://shop.sandisk.com/DRHM/servlet/ControllerServlet?Action=DisplayCategoryProductListPage&SiteID=sdiskus&Locale=en_US&Env=BASE&categoryID=11448300)

Ok, after checking, I don't have one. Any other way? Using that fphoto thing?

---

### Post by ugm6hr on 2008-11-29
> **Flimm said:**
> Your digital camera probably has an SD card

I suspect that Sony camera's still use Sony Memory Sticks.

Have to say, my laptop's card reader still doesn't cope with Sony Cards (although it manages SD cards fine).

---

### Post by malspa on 2008-11-29
Sony camera, most likely uses a memory stick pro duo memory card.  Get a card reader that reads pro duo cards, plug it into your USB port, you can drag and drop the photos to your computer that way.  They sell card readers all over.  Wal-Mart has them for something like $8.88.  This is how I get my photos onto my computer; I don't even hook up my camera to it.  There are card readers for pro duo, SD, XD, etc.  There are also multi-card readers that will read several types of memory cards, and they can also be found for less than $15 bucks.

I work at a photo lab/camera shop. I'm always recommending that people get a card reader if their computer doesn't have one for the card they use; that way they don't even need to use the camera's software or connect the camera to the computer at all.  Saves the camera's batteries, too.  Especially useful for folks who don't use Windows since most cameras' software is for Windows (or Macs).

---

### Post by linux_tech on 2008-11-29
Try connecting camera directly to the computer and accessing that way.
Usually a firewire cable or usb cable is included with the camera
If the camera did not come with a cable, then Sd card readers are inexpensive, usually less than $10, they plug into the usb

---

### Post by malspa on 2008-11-29
They also sell card readers at office supply stores like OfficeMax, I've picked them up there, cheap.

---

### Post by malspa on 2008-11-29
The Sony Cybershot DSC W110 doesn't use SD cards.  Memory Stick, Memory Stick Duo, Memory Stick PRO, Memory Stick PRO Duo.  The card reader has to be one that reads one of those.  The OP probably has a PRO duo card.

---

### Post by F3joel on 2008-11-29
With my sony cybershot(dsc-w55)I had to go into setup 2 and change the usb connection to PTP. My camera automounts now.

---

### Post by __Ryan__ on 2008-11-29
As I have mentioned in my previous posts, gphoto2 with gtkam will allow you to connect the camera through the normal USB connector and download the pictures.

It's very handy because it specialises in being able to communicate with the camera's filesystem and locate the pictures and movies on the device.

Try This:

Plug your camera into the USB port on your computer:

This should find your camera.
```

$ gphoto2 --auto-detect
```

View the files on the camera.
```
gphoto2 --list-files
```

Then change directories to where you want the files downloaded. Then execute this command to download the pictures to the current directory.
```
gphoto2 --get-all-files
```

The gtkam is just a graphical front end for this. I used gphoto2 for a long time to download pictures before I got my new laptop with a memory card reader.

---

