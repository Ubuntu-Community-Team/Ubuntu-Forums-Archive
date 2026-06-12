---
title: "Root file/installation type"
date: 2014-08-08
forum: New to Ubuntu
---

### Post by christopher17 on 2014-08-08
Hello!

So I am new to ubuntu and am thus a complet noob, I just used Unebootin to install ubuntu on my old asus eee PC. I went through all the stages untill I came to the installation type screen, as far as I can figure out I am suppose to choose a partition for /dev/sda/1 ntfs which is microsoft windows xp home edition but I cannot make heads or tales which I should change too, or am I suppose to do something else?

Maybe I should create a new partition because /dev/sda is empty?

---

### Post by Bashing-om on 2014-08-08
christopher17; HI ! Welcome to the forum .

Are you making this more difficult than it is ???
At that 1st install screen what are the options ?
IF ubuntu is to be the sole operating system installed on that 1st hard drive (sda), how about taking the easy way and choose the option " erase disk and install ubuntu" (making SURE that sda is the hard drive chosen for the installation) answer the personal questions and you will be set up and all to go .

[INDENT][INDENT]I am all for easy
[/INDENT][/INDENT]

---

### Post by Jonathan Precise on 2014-08-08
Hello christopher17, and Welcome to the Ubuntu forums community!

Regarding the question:
> **christopher17 said:**
> ... until I came to the installation type screen ...
Do you mean one like [this]("http://ubuntuforums.org/attachment.php?attachmentid=255322&d=1407529887")? Or like [this]("http://4.bp.blogspot.com/-qM1srvm-KeM/TqwRuBr0lWI/AAAAAAAABpI/7umWKGgeYv8/s1600/Parition+layout.png")?


> **christopher17 said:**
> ... as far as I can figure out I am suppose to choose a partition for /dev/sda/1 ntfs which is microsoft windows xp home edition but I cannot make heads or tales which I should change too, or am I suppose to do something else?

All depends on what you want to do. If the screen looks like the second link, then hit the back button. Then it should look like the screen in the first link.

Now that it looks like the screen in the second link, then you have to choose: keep Win XP just in case, or just get rid of everything and [SIZE=5][COLOR="#FF0000"]LOOSE ALL DATA!!!!!!!![/COLOR][/SIZE] (Before making any decision, I recommend you back up, and avoid the "Oh No!" moment. I personally recommend Clonzilla. You can get a copy of clonezilla at [http://clonezilla.org](http://clonezilla.org) , just like you get a copy of ubuntu.)

To keep XP and ubuntu on the same PC, choose "Install alongside them". Then choose how much space you want to give each.

To get rid of XP, choose "Erase everything and install Ubuntu". Again, you will [SIZE=5][COLOR="#FF0000"]LOOSE AL DATA!!!!!!!![/COLOR][/SIZE] Be carefull when choosing this.

---

### Post by Bashing-om on 2014-08-08
@ christopher17; Hey,

See the ups ^ .

@ Jonathan : Hi !

Long time no read !
[INDENT][INDENT]good to see ya once more .

[INDENT][INDENT]'buntu
[INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by christopher17 on 2014-08-08
[QUOTE=
Do you mean one like [this]("http://ubuntuforums.org/attachment.php?attachmentid=255322&d=1407529887")? Or like [this]("http://4.bp.blogspot.com/-qM1srvm-KeM/TqwRuBr0lWI/AAAAAAAABpI/7umWKGgeYv8/s1600/Parition+layout.png")?[/QUOTE]

The second option, I never got to choose the first one for some reason, I didnt install ubuntu from a cd or a usb so maybe thats the problem?

I installed Unebootin, choose ubuntu, the data gets extracted to the harddrive, restarted the computer, booted Unebootin during start up, I choose "install ubuntu" option and then I got the install sequence, minus the one where I get to choose "erase disk and install ubuntu" and whatnot.

Now that I think about it I didnt choose specifically where the Ubuntu data would be extracted to when I used Unebootin.

---

### Post by Jonathan Precise on 2014-08-08
I have had many problems with unetbooting. Try LinuxLive instead: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

### Post by christopher17 on 2014-08-09
Thx everyone but I think I figuer it out, I noticed that when I had my usb drive plugged in i get to the option to replace windows with ubuntu, but then I have not enough space. I think I need to buy a large usb drive and extract the ubuntu iso file into it instead of to my harddrive, which I have been doing until now.

ps: how large usb drive would I need to completly replace windows with ubuntu? I dont think my computer is powerful enough to have them running at the same time.

---

### Post by Jonathan Precise on 2014-08-09
I'd recommend you'd buy a usb disk at least 2 GB.

How much RAM and HDD space does it have? It may be able to run both at the same time.

---

### Post by christopher17 on 2014-08-09
> **Jonathan Precise said:**
> I'd recommend you'd buy a usb disk at least 2 GB.

How much RAM and HDD space does it have? It may be able to run both at the same time.

It has 2 gb RAM and 160 gb storage and 1.33 ghz

---

### Post by Jonathan Precise on 2014-08-09
I *think* it should be able to run both. Just make sure to use the windows partition re-sizer.

---

### Post by christopher17 on 2014-08-09
Okej this time it worked, let me start from the beginning. For some reason I could not extract the ubuntu iso file into my usb drive from Unebootin, so I extracted it manually and then used Unebootin again and extracted the ubuntu iso file into the hard drive. I keept the usb plugged in and booted Unebootin and ubuntu has successfully been installed and replaced windows. However now it is really slow, I mean much slower then during windows, the track pad is more responsive than ever for some reason but using any software takes for ever, any ideas?

I downloaded the 32 bit desktop version of Ubuntu 14.04.1 LTS

---

### Post by christopher17 on 2014-08-09
Okej this time it worked, let me start from the beginning. For some reason I could not extract the ubuntu iso file into my usb drive from Unebootin, so I extracted it manually and then used Unebootin again and extracted the ubuntu iso file into the hard drive. I keept the usb plugged in and booted Unebootin and ubuntu has successfully been installed and replaced windows. However now it is really slow, I mean much slower then during windows, the track pad is more responsive than ever for some reason but using any software takes for ever, any ideas?

I installed the 32 bit desktop version of Ubuntu 14.04.1 LTS

---

### Post by Jonathan Precise on 2014-08-09
You used unetbooting to extract it to the HDD, replacing windows? If so, let me tell you that it's a live system, not an installed system. To convert that to an installed system, you must use a program called Startup Disk Creator (Search for it in the dash), select a source iso/dvd, select your usb disk, boot from the usb disk, and use the "Install ubuntu" app.

---

### Post by christopher17 on 2014-08-09
> **Jonathan Precise said:**
> You used unetbooting to extract it to the HDD, replacing windows? If so, let me tell you that it's a live system, not an installed system. To convert that to an installed system, you must use a program called Startup Disk Creator (Search for it in the dash), select a source iso/dvd, select your usb disk, boot from the usb disk, and use the "Install ubuntu" app.

Aha I see, it is wierd though because windows has been removed because it boots directly to ubuntu now. Anyhow I did the steps and I used the ubuntu desktop iso and I succsesfully created the files for booting ubuntu from the usb, I tried restarting with the usb plugged in and entered BIOS where i prioritized removable devices when booting but it just loaded me back to the live version again.

---

### Post by Jonathan Precise on 2014-08-09
The usb stick is a live system, but it allows you to install properly. Once in the USB LIVE system, double-click Install Ubuntu

---

### Post by christopher17 on 2014-08-10
> **Jonathan Precise said:**
> The usb stick is a live system, but it allows you to install properly. Once in the USB LIVE system, double-click Install Ubuntu

Hmm, it installed succsefully but it still feels like it is a live system because it is so slow, maybe I should download the 64 bit version instead? I am pretty sure I only have 32 bit but it has 2gb RAM.

---

### Post by Impavidus on 2014-08-10
That may be a graphics driver problem. If the CPU is doing everything that should be done by the GPU your system becomes slow. Or your hardware may be just not powerful enough. You wrote about an old asus eee PC. I don't know the hardware specs of that, but it doesn't sound impressive. Standard Ubuntu is about as heavy as Windows 7. On old hardware you may be better off with a lighter desktop environment and set of default applications. You could create live disks of for Lubuntu or Xubuntu and test those without installing them.

---

### Post by Jonathan Precise on 2014-08-10
@christopher17: Yeah, if the installed system is slow (as much as the live system), could be that the graphics card is not good enough to handle ubuntu.

Vanilla ubuntu is very demanding. Modern OS = Demanding OS. You should try another flavor of ubuntu, like Xubuntu, with XFCE, which is made for older PCs/Laptops. Xubuntu is also very mature, unlike Lubuntu which is pretty new, and has some bugs. Xubuntu has less bugs that Lubuntu, although it's a bit heavier, but still amazingly light.

---

### Post by christopher17 on 2014-08-12
> **Jonathan Precise said:**
> @christopher17: Yeah, if the installed system is slow (as much as the live system), could be that the graphics card is not good enough to handle ubuntu.

Vanilla ubuntu is very demanding. Modern OS = Demanding OS. You should try another flavor of ubuntu, like Xubuntu, with XFCE, which is made for older PCs/Laptops. Xubuntu is also very mature, unlike Lubuntu which is pretty new, and has some bugs. Xubuntu has less bugs that Lubuntu, although it's a bit heavier, but still amazingly light.

You are right, installing xubuntu made it much smoother, thanks a lot!

---

