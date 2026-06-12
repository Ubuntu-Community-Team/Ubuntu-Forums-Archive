---
title: "Lost photos on my external hard drive"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by Airycat on 2012-01-30
I stored all my photos on my _external_ hard drive. They were all in folders by date. When I opened them, they were jpg files. After switching to Ubuntu I went to the folder and all I find are two files.

[IMG]http://i2.photobucket.com/albums/y47/airycat/Help/picturePackageScreenshotat2012-01-30180804-1.jpg[/IMG] 
Properties on the folder say > 2 items, totalling 13.9 kB

It was *all* of my 2011 photos with only a few backed up elsewhere. Why would changing my OS affect my external drive?  If I find my Picture Package installation disk, would installing it restore my photos?

Since it says picasa, I tried to install that, but, even though I searched and found a solved thread, following those instructions didn't help. My terminal was asking what to do next.

Any help to restore my photos will be greatly appreciated. I'm feeling a bit sick about this.

---

### Post by Bucky Ball on 2012-01-30
Where did you install Ubuntu and how did you install it? On the internal drive? If so, shouldn't have deleted your pics. Was the external plugged in while you were installing? In hindsight you are best to remove all external drives and USB sticks (unless installing from one, naturally) when installing. 

Installing to the internal drive would not have deleted anything from the external in any case. Ubuntu install would not have touched or changed that device in anyway (theoretically).

Have no idea what 'Picture Package' is. Is that a name you have given the folder or some software created folder? If the latter, perhaps Linux can't read that. It can certainly read jpg files though, if they are present.

If you have a side-by-side install with Windows, boot Windows and see if they are there. Good luck.

---

### Post by halitech on 2012-01-30
firstly, unplug the external drive. The more you try to do and the more you try to read it, the less likely it is that you will be able to recover the data.

second, install testdisk

when you were doing the install, was the external connected? If it was, did you select to install anything on it or mount it in anyway?

run testdisk and sit back and pray that it is able to recover your files

---

### Post by Airycat on 2012-01-30
I did a full install on the internal drive. Didn't know I should unplug the external drive. Everything else seems to be there (though I can't be 100% certain as I have a lot on there). Other photos in other files are there.

Picture package was the program that came with my camera to upload pictures. Shotwell does that for me on Ubuntu.

I did nothing that said or should have done anything with the external drive, to my knowledge.

Will testdisk do anything since it's not a wubi installation? It says I need to be a root user. How do I do that? Run it on the internal drive?? or the external, or both?

---

### Post by halitech on 2012-01-30
the best advice is to always disconnect any devices when installing a new OS.

testdisk isn't designed for wubi installs. I've thankfully never needed to use it myself but you should be able to select where you want it to scan.

if it's asking for root user, hit ALT-F2 and type in ```
gksudo testdisk
```
and that should run it as the superuser

---

### Post by bluexrider on 2012-01-30
testdisk with photorec is the only way to go. Run gksudo testdisk 

here is the web site for instructions [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Guilden_NL on 2012-01-30
I can vouch for photorec, it is excellent!  I used it to recover 100% of 1GB of photos on a MMC card that my wife wiped out.  It took a whopping 10 minutes total to install the app and recover the photos.

---

### Post by Bucky Ball on 2012-01-30
I'm figuring Linux just can't read Picture Package. Plug into a Windows machine and I bet they're still there. Copy them out of the Picture Package software and into a regular folder and things should work. 

Don't think this is anything wrong with the hard drive and this is not a testdisk situation as everything else is there, ***including pictures in other, regular, folders that are'nt in the Picture Package folder.***

Picture Package is probably a Win program from the camera manufacturer and not intended for Linux. ;)

---

### Post by Airycat on 2012-01-31
I have a sneaky suspicion that when Ubuntu replaced everything on C including the Picture Package program, the program grabbed almost everything connected to it. The files did not show up on my laptop, but it doesn't have the PP program, so I still have a tiny bit of hope. I just have to find the program disk.

If those files were erased, it that what this program will recover?

I ran the Testdisk, but, although it ran (I had to choose "Log" -or not), I don't have a clue what it did . It opened a different window from the terminal window. Now, when I try to run it again it opens the Dashhome and shows results & history, asks for my password if I click on either and nothing happens. I did find the Log in the Home folder. This is it in full:> 
Mon Jan 30 22:58:30 2012
Command line: TestDiskI think it's running again, now. It asked if I want to stop when I attempted to close it. It's in the terminal window this time, so maybe I'll get results.

A few hours later and this is what I'm getting. I'll leave it for the night, but it looks to me like nothing is happening.
[IMG]http://i2.photobucket.com/albums/y47/airycat/Help/Screenshotat2012-01-31013723.jpg[/IMG]
I never got the screens in the Step by Step instructions.

---

### Post by Airycat on 2012-01-31
Testdisk did nothing useful. It didn't give me any way to input anything other than log. I did some searching and found scalpel and foremost. These run, but I don't know enough to tell them how to do what I want, so I get nothing... at least I don't know what it is. Are there instructions somewhere in non-tech English (I don't understand the tech instructions) that will tell me exactly what to type in to see if it can recover anything on my external drive?

tia 
~Faith

---

### Post by Jerry N on 2012-01-31
Checking with Google, Picture Package appears to be a Sony product - the same company that used music CDs to install root kits on Windows machines a few years back.  Is it possible that the pictures are located in some kind of proprietary Sony database and you see them as .jpg files when using the Picture Package software?  If so, you might need to connect your drive to a Windows machine that has Picture Package installed.  If the pictures are still there, copy them to a real file structure on at least two hard drives or flash drives.  As with others that have responded, I don't see how just installing Linux could have corrupted your external drive.  

Jerry

---

### Post by Bucky Ball on 2012-01-31
> **Bucky Ball said:**
> I'm figuring Linux just can't read Picture Package. Plug into a Windows machine and I bet they're still there. Copy them out of the Picture Package software and into a regular folder and things should work. 

Don't think this is anything wrong with the hard drive and this is not a testdisk situation as everything else is there, ***including pictures in other, regular, folders that are'nt in the Picture Package folder.***

Picture Package is probably a Win program from the camera manufacturer and not intended for Linux. ;)

Just in case you missed it. Do you have a Windows computer you can use? A friend?

---

### Post by Airycat on 2012-01-31
> **Bucky Ball said:**
> Just in case you missed it. Do you have a Windows computer you can use? A friend?
Yes, I have windows on my laptop. Thank you for asking. Problem now is finding the disk to install the program. It's here somewhere. Just gotta find it.

---

### Post by bluexrider on 2012-01-31
> **Airycat said:**
> Testdisk did nothing useful. It didn't give me any way to input anything other than log. I did some searching and found scalpel and foremost. These run, but I don't know enough to tell them how to do what I want, so I get nothing... at least I don't know what it is. Are there instructions somewhere in non-tech English (I don't understand the tech instructions) that will tell me exactly what to type in to see if it can recover anything on my external drive?

tia 
~Faith
Look at my previous post I gave you a link to READ THE INSTRUCTIONS.

---

### Post by Airycat on 2012-02-01
> **bluexrider said:**
> Look at my previous post I gave you a link to READ THE INSTRUCTIONS.

I DID read the instructions, and FOLLOWED them to the point where I could choose to create a log. The first time I tried, the terminal disappeared after pressing Enter. The second time it merely froze and stayed that way from about 7 pm Monday night until about 2 pm Tuesday afternoon. (see my post/screenshot Tuesday 01:52 AM -- I did not close it after posting.) I did NOT get any windows giving me options for drives or anything else after the CREATE.  As far as I could see, there were no instructions to cover the window freezing on me.

When I asked for instructions in English, it was for the other programs I found, scalpel and foremost, which had instructions, but they assumed I know a lot more than I do. I tried to follow them, but kept getting "invalid command" so clearly I am missing the assumed basic information. 

This is where I found instructions.... 
[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html]("http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html")

Probably very simple for you, but, although I understand part of it, I still don't know exactly what to type in the terminal. 

I'm also still looking for the Sony Picture Package disk to install it on my laptop and try what a few others have suggested. I tried it with Windows without the program, but that didn't work.

---

### Post by papukoms on 2012-02-01
go to google and search "download Sony Picture Package"

---

### Post by flemur13013 on 2012-02-01
> Since it says picasa

Picasa silently moves (not copies) pictures around*; it may have moved your pictures to your internal drive without telling you, then the system install wiped them out.

*I immediately uninstalled it after discovering this; now I have a bunch of pics in a "picasa" directory rather than in their original directories with meaningful names.  IIRC - it was a while ago - it occurred after uploading pics to picasa/google.

---

### Post by Airycat on 2012-02-01
> **flemur13013 said:**
> Picasa silently moves (not copies) pictures around*; it may have moved your pictures to your internal drive without telling you, then the system install wiped them out.

*I immediately uninstalled it after discovering this; now I have a bunch of pics in a "picasa" directory rather than in their original directories with meaningful names.  IIRC - it was a while ago - it occurred after uploading pics to picasa/google.  

AAAArrrrrggggh!  And it stole every picture I added to the file after I used it last. How I wish I had known this. I didn't like Picasa anyway. This increases the likelihood that I have totally lost them all. 

... Except, why didn't it steal photos from other folders. I know that it showed other folders in picasa. Wierd.

---

### Post by varunendra on 2012-02-02
> **Jerry N said:**
> Is it possible that the pictures are located in some kind of proprietary Sony database and you see them as .jpg files when using the Picture Package software?
I doubt almost the same thing.. something close to this-
> **flemur13013 said:**
> Picasa silently moves (not copies) pictures around*

> **Airycat said:**
> ... Except, why didn't it steal photos from other folders. I know that it showed other folders in picasa.
Maybe the contents of the "picasa.ini" file could give some hint.. Just guessing.

By the way, if those image files ever physically existed on the drive you are searching in (and have not been overwritten by some other data), then photorec (part of testdisk) is your best bet to recover them. If you wish to try, but find it confusing, I can try to provide a step-by-step instruction.

---

### Post by bluexrider on 2012-02-02
> **Airycat said:**
> I DID read the instructions, and FOLLOWED them to the point where I could choose to create a log. The first time I tried, the terminal disappeared after pressing Enter. The second time it merely froze and stayed that way from about 7 pm Monday night until about 2 pm Tuesday afternoon. (see my post/screenshot Tuesday 01:52 AM -- I did not close it after posting.) I did NOT get any windows giving me options for drives or anything else after the CREATE.  As far as I could see, there were no instructions to cover the window freezing on me.

When I asked for instructions in English, it was for the other programs I found, scalpel and foremost, which had instructions, but they assumed I know a lot more than I do. I tried to follow them, but kept getting "invalid command" so clearly I am missing the assumed basic information. 

This is where I found instructions.... 
[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

Probably very simple for you, but, although I understand part of it, I still don't know exactly what to type in the terminal. 

I'm also still looking for the Sony Picture Package disk to install it on my laptop and try what a few others have suggested. I tried it with Windows without the program, but that didn't work.
The instructions you have here are not the instructions which I posted. I can see why you would be confused. Those are for the application called  :confused:  FORMOST  .:confused:

 not **PHOTOREC**.

You may have some success if you put the correct application into play with the correct instructions.

Let me help you one more time. In terminal post this code

```
sudo apt-get install testdisk
```once installed follow these instructions step by step:
[B]
[COLOR=Red][http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)[/COLOR][/B]

---

### Post by ianp5a on 2012-02-02
I still use PICASA because it has slightly better built in picture edit options than Shotwell. "Sharpen" for example. 

The reason why the built in functions are important is to streamline the process to just a few clicks. Import - Preview - Tweak - Upload to Web.

Shotwell does all this quite well too. But I have not found a way to extend its editing features.

---

### Post by rgreener25 on 2012-02-02
In future make sure you press the eject button in nautilus and wait until it says it is safe to remove

---

### Post by Airycat on 2012-02-02
[SIZE="1"][SIZE="2"]> **bluexrider said:**
> The instructions you have here are not the instructions which I posted. I can see why you would be confused. Those are for the application called  :confused:  FORMOST  .:confused:  not **PHOTOREC**.

You may have some success if you put the correct application into play with the correct instructions.

Let me help you one more time. In terminal post this code

```
sudo apt-get install testdisk
```once installed follow these instructions step by step:
[B]
[COLOR=Red][http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)[/COLOR][/B]

I followed the instructions you gave for testdisk IN MESSAGE #6 ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)). I listed the instructions for Formost because I tried that AFTER TESTDISK FROZE AT THE CREATE SCREEN AS SHOWN IN MY SCREENSHOT.[/SIZE][/SIZE]
----------------------------------------
Following these instructions (no freezing this time!:)) I get through the Partition table type selection, but for the next screen instead of this:
 [IMG]http://www.cgsecurity.org/mw/images/PhotoRec_src.png[/IMG]

I get this:
[IMG]http://i2.photobucket.com/albums/y47/airycat/Help/Screenshotat2012-02-02171041.jpg[/IMG]

This is for either the internal or external drive. I have no clue what to do next. Going by instinct, I chose the analyse and something else.... then chose 'deeper search' and it *did* find an ntfs... It's analysing... This will take a while.  I'll check in later.

---

### Post by LinuXofArabiA on 2012-02-02
Always eliminate the obvious, and start with the simplest solutions. Did anyone else have access to your hard drive?! If so, then probably you should do some outside investigation first. Just saying.

---

### Post by varunendra on 2012-02-02
> **Airycat said:**
> I get this:
You have to choose "Advanced (Filesystem utils)". There you'll get the options to recover lost or deleted files.

As obvious, DO NOT even touch the "MBR code" and "DELETE" options (well.., 'touching' won't do any harms, but implementing them will!).

---

### Post by Airycat on 2012-02-02
No one had access to my hard drive. 
I believe I did choose Advanced.
No, no, no!! I don't want to delete anything. I know to stay away from that.

It finished analyzing the drive and showed me this screen:
[IMG]http://i2.photobucket.com/albums/y47/airycat/Help/Screenshotat2012-02-02191419.jpg[/IMG]

**I was pretty sure I had a 640GB computer. I don't know what "HD jumpers settings, BIOS detection..." means. How do I verify the size of my hard drive?  System info shows 623.8 GB What do I do if it really is 640? It showed the OS partition, so I don't think I accidentally ran it on the external drive which is a 2T.**

I don't think I need to worry about those unrecoverable partitions, since I didn't have the Picasa on Linus -- only on Windows. There were several NTFS partitions, which I'm guessing are the old Windows storage.

---

### Post by varunendra on 2012-02-02
You had to follow this step-by-step (for PhotoRec, which is a part of testdisk installation): [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

while you are trying testdisk, which is almost same thing, but slightly advanced, and the steps are slightly different.

So please follow the above step-by-step guide, as it should be easier. (command in terminal: **photorec**).


**_EDIT_:**
You have to run it on a partition on which you think the photos were, that is, a partition on the external drive which is 2TB!!
So this is going to be practical **ONLY IF** the partition on which you had those photos, is small enough, or the size of the data that ever existed on it is small enough to fit on another partition which you will choose as destination for 'Recovered' files. Else you will have to go into 'Advanced' mode even in photorec.

Better comeback here with output of
```
sudo fdisk -l
df -h
```if you have doubt about the size-space issue.

[COLOR=Red]**Also, DO NOT select the destination for the recovered files on a partition on which you think the files might have been!**[/COLOR]

---

### Post by Airycat on 2012-02-11
I ran photorec and ended up with 271 folders of 500 items each! Actually, I started photorec and realized I'd not narrowed it down to photos, so I terminated it and reran it just for photos, but I still got tons of other files.

None of the files seem to be my lost photos. 

Now my problem is that I have 135,000 files on my main drive that I don't need. When I try to delete anything I'm told I don't have permission. How do I get permission for this?

---

### Post by Dlambert on 2012-02-11
Recuvra from piriform works very well. Run in deep scan mode.

---

### Post by varunendra on 2012-02-11
> **Airycat said:**
> Now my problem is that I have 135,000 files on my main drive that I don't need. When I try to delete anything I'm told I don't have permission. How do I get permission for this?To do it safely, open nautilus as 'root' by pressing Alt+F2, then type and enter:
```
gksu nautilus
```

By the way, are you sure your desired photos aren't there? Because if photorec couldn't find them, then most probably either they have been overwritten or didn't exist there at all. Also, thumbnails can be dodgy sometimes.

---

### Post by Airycat on 2012-02-12
Thank you for showing me how to get rid of the files.

I found my pictures!!! They were buried in another folder altogether, and I do mean buried. I thought I had lost another folder, but I knew I had copies of that one's contents in another folder. I found it, but got distracted wondering what all the folders were, since I rarely use the folder I was in except for thing I need to keep like agreements and paid bills, but never really need to look at again. Inside another folder in that one I saw one labelled 2011 and sure enough, it was my photos! Woohoo! I **know** I did not bury them there. And it was too deep to get there accidentally (4 folders over and two deep from the original). I can only imagine that they'd been copied there whenever I uploaded them, or when I wiped out Windows thereby deleting Picasa, without my knowledge. However they got there I am grateful.

And **thank you** to everyone who responded to this thread. I learned a lot and though it didn't directly help solve this (non) problem, knowledge is never wasted.

---

### Post by ianp5a on 2012-02-12
Phew!
Maybe it was a drag and drop error. One accidental push with the mouse and they were moved to another location.

---

