---
title: "HOWTO: Bootup splash screen with splashy"
date: 2005-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by infinito on 2005-06-14
This howto will allow you to get a bootup image with progress bar, like the livecd does.
In this post i'm using my self-made theme. You can make your own or download another, it's up to you!

Splashy for Ubuntu

(1) Download latest splashy package from: [http://alioth.debian.org/projects/splashy/](http://alioth.debian.org/projects/splashy/) 

(2) Install the splashy .deb:
```
$ sudo dpkg -i splashy_0.1.3.svn.2_i386.deb
```
(3) Edit /boot/grub/menu.lst to add vga=792 (1024x768 millions colors) or vga=791 (1024x768 thousands colors) to your default boot option.
For example:```
title		Ubuntu, kernel 2.6.10-5-k7 Default 
root		(hd0,0)
kernel		/vmlinuz root=/dev/hde6 ro quiet splash vga=792
initrd		/initrd.img
savedefault
boot
```See codes table below:

(4) Download my Ubuntu splashy theme from: [http://infinito.f2o.org/downloads/ubuntu_splashy_theme.tar.gz](http://infinito.f2o.org/downloads/ubuntu_splashy_theme.tar.gz)

You can get more themes from: [http://splashy.alioth.debian.org/themes/](http://splashy.alioth.debian.org/themes/)

(5) Untar ubuntu theme:
```
$ tar xzf ubuntu_splashy_theme.tar.gz
```
(6) Copy files to splashy dir:
```
$ sudo cp -a ubuntu/ /etc/splashy/themes
```
(7) Edit splashy config file:
```
$ sudo mv /etc/splashy/config.xml /etc/splashy/config.xml.old
$ sudo mv /etc/splashy/themes/ubuntu/config.xml /etc/splashy
```
That's all! Next time you reboot your computer you'll see splashy in action!

Links of interest:
[http://nanofreesoft.org/index.php/Splashy](http://nanofreesoft.org/index.php/Splashy)
[http://nanofreesoft.org/index.php/Upower](http://nanofreesoft.org/index.php/Upower)

VGA Codes Table:```

                640x480    800x600    1024x768       1280x1024
256 colors        768        771         773            775
32K colors        784        787         790            793
64K colors        785        788         791            794
16M colors        786        789         792            795
```

---

### Post by thechitowncubs on 2005-06-14
Does this take affect during the whole boot process?

Like no "freaks out noob" text is scrolling?

---

### Post by infinito on 2005-06-14
[QUOTE=thechitowncubs]Does this take affect during the whole boot process?

Like no "freaks out noob" text is scrolling?[/QUOTE]
 You will see the first two text lines only...

---

### Post by Xian on 2005-06-14
I realize this is supposed to be an "alpha" stage package, but it has worked flawlessly on my box and I certainly hope the development on it continues. I did read where it recently forked into the Upower project so it remains to be see where all this settles. 

Thanks for the great How-To. 
People should definitely give it a go.

---

### Post by kleeman on 2005-06-14
Didn't work here:  :mad: 
I got smaller text and a message saying splashy was not running and to check the
/etc/default/splashy and /etc/splashy/config.xml files for format errors. I got green text saying boot was 30% 40% etc complete. Strangely when I shutdown it seemed to be working........

---

### Post by infinito on 2005-06-14
[QUOTE=kleeman]Didn't work here:  :mad: 
I got smaller text and a message saying splashy was not running and to check the
/etc/default/splashy and /etc/splashy/config.xml files for format errors. I got green text saying boot was 30% 40% etc complete. Strangely when I shutdown it seemed to be working........[/QUOTE]
 Please, try to change the contents of /etc/splashy/config.xml to this:
```
<splashy>
    <progressbar>
        <!-- here are tags to set the bar... x is the x coordinate and
        y is the y coordinate, width and height are for the progress bar.
        Remember that x, y width and height are expressed in percentage -->
        <x>20</x>
        <y>90</y>
        <width>60</width>
        <height>2</height>
        <!-- here you can set the color of the progressbar...
        set the amount of red, green, blue and alpha channel. 
        Remember that the max value is 255 and the minumun value is 0-->
        <red>207</red>
        <green>0</green>
        <blue>0</blue>
        <alpha>255</alpha>
    </progressbar>
    <background>
        <boot>/etc/splashy/themes/ubuntu/background.jpg</boot>
        <shutdown>/etc/splashy/themes/ubuntu/shutdown.jpg</shutdown>
        <errorimg>/etc/splashy/themes/ubuntu/error.jpg</errorimg>
    </background>
    <fifo>/etc/splashy/splashy.fifo</fifo>
    <pid>/etc/splashy/splashy.pid</pid>
    <autoverboseonerror>yes</autoverboseonerror>
</splashy>
```

---

### Post by Xian on 2005-06-14
Looks like someone else is having your [problem](http://kalatlug.nanofreesoft.org/index.php?name=PNphpBB2&file=viewtopic&t=59&sid=80f00bdd6d82a9156994945fb51692d9).
I'm actually using the Upower package but can't seem to find a copy right now.

---

### Post by Xian on 2005-06-14
Okay, I chased it down finally. 
The latest version is not the one on the Alioth page.

Get splashy_0.1-5_i386.deb from [HERE](http://kalatlug.nanofreesoft.org/Projects/splashy/relases/splashy_0.1-5_i386.deb).

You'll also need the [libdirectfb-0.9-22](http://kalatlug.nanofreesoft.org/Projects/splashy/libraries/libdirectfb/libdirectfb-0.9-22_0.9.22-1_i386.deb) and [lib++dfb-0.9-22](http://kalatlug.nanofreesoft.org/Projects/splashy/libraries/lib++dfb/lib++dfb-0.9-22_0.9.22-1_i386.deb) packages.

That should get everything up to speed.

---

### Post by kleeman on 2005-06-14
None of it worked I'm afraid. The first fix just changed the boot(down) screen picture. The same error occured during bootup. I did notice however that the boot(up) screen appear extremely briefly. When I installed the other packages no boot(up) or boot(down) screens appear at all but it does claim that splashy is operating  ;-) 
Looks like I've been bitten by alpha software....

---

### Post by Xian on 2005-06-14
[QUOTE=kleeman]Looks like I've been bitten by alpha software....[/QUOTE]
Drats! :) Things will get better with further devel work.

---

### Post by infinito on 2005-06-14
> **kleeman]None of it worked I'm afraid. The first fix just changed the boot(down) screen picture. The same error occured during bootup. I did notice however that the boot(up) screen appear extremely briefly. When I installed the other packages no boot(up) or boot(down) screens appear at all but it does claim that splashy is operating   said:**
> 
 From the Upower (fork of splashy) wiki :
[QUOTE]nb: in some cases Splashy will start to work after the second or third reboot, it's normal, don't worry.
Maybe this is your case...

You should also take at look at this: [http://nanofreesoft.org/index.php/Splashy](http://nanofreesoft.org/index.php/Splashy)

---

### Post by dolny on 2005-06-14
[http://alioth.debian.org/tracker/index.php?func=detail&aid=301517&group_id=30657&atid=411690](http://alioth.debian.org/tracker/index.php?func=detail&aid=301517&group_id=30657&atid=411690)

> [ #301517 ] Splashy does not work if /usr is on its own partition

That is the problem for me :/

---

### Post by lizardking on 2005-06-14
I try splashy and It show me only 4 picture during the boot in the upper part of the screen : tux, a HD, network and a Pc..I cannot set ubuntu theme.
I notice that when I wento to do HOWto point 7) I had not backup any confi.xml **bacause i haven't it...**  ](*,)

---

### Post by dolny on 2005-06-14
BTW. Splashy is now available through debian repositories so use 'apt-get install splashy' instead of these packages.

---

### Post by infinito on 2005-06-14
[QUOTE=dolny]BTW. Splashy is now available through debian repositories so use 'apt-get install splashy' instead of these packages.[/QUOTE]
 We're using Ubuntu (i thought that was clear in a ubuntu forum), so people can't (shouldn't) apt-get debian packages.

---

### Post by lizardking on 2005-06-14
[QUOTE=dolny]BTW. Splashy is now available through debian repositories so use 'apt-get install splashy' instead of these packages.[/QUOTE]
Can you post Debian repository?

---

### Post by dolny on 2005-06-14
I don't remember whether I added some extra repositories... After apt-get install it just started installing. Maybe the backports repository? 

Anyway, I'll have to wait until they fix the separate partition /usr/ thing :/

---

### Post by lizardking on 2005-06-14
:-) Yeah i fix the problem now i have ubuntu background...

only the last trick....HOw I Can clear the 4 picture I mentioned in the previous post.Now i have ubuntu backgourn but this ugly pictures are always there....

---

### Post by bored2k on 2005-06-14
It did not work here. It keep telling me to check for a /etc/default/**spalshy** (!?) and /etc/splashy/.xml

It just loaded text mode with a green text telling me "10%, 20%, etc".

If I tried teh vga=792 thing I'd get an error. :(

---

### Post by dolny on 2005-06-14
[QUOTE=bored2k]It did not work here. It keep telling me to check for a /etc/default/**spalshy** (!?) and /etc/splashy/.xml

It just loaded text mode with a green text telling me "10%, 20%, etc".

If I tried teh vga=792 thing I'd get an error. :([/QUOTE]

I have exactly the same problem. Is your /usr/ on a separate partition?

---

### Post by desdinova on 2005-06-14
Worked aok here...

---

### Post by bored2k on 2005-06-14
[QUOTE=dolny]I have exactly the same problem. Is your /usr/ on a separate partition?[/QUOTE]
 Actually it's not.
I hate one / partition and one /home partition and that is it.

---

### Post by tristan on 2005-06-14
Splashy 0.1-5 (downloaded from the splashy homepage) works flawlessly on my box, which has /usr on its own partition.

The fact that you see the 10%. 20% etc means that splashy is working, but that the picture is not displaying for some reason. I had a similar thing happen until I realised that I hadn't named my startup and shutdown picturse correctly in the splashy xml config file.

One other thing, splashy works just fine with png graphics.  

Finally, thanks a lot for the howto!

---

### Post by bored2k on 2005-06-14
[QUOTE=tristan]Splashy 0.1-5 (downloaded from the splashy homepage) works flawlessly on my box, which has /usr on its own partition.

The fact that you see the 10%. 20% etc means that splashy is working, but that the picture is not displaying for some reason. I had a similar thing happen until I realised that I hadn't named my startup and shutdown picturse correctly in the splashy xml config file.

One other thing, splashy works just fine with png graphics.  

Finally, thanks a lot for the howto![/QUOTE]
 I get "undefined video number" on vga=792

---

### Post by Xian on 2005-06-14
[QUOTE=bored2k]I get "undefined video number" on vga=792[/QUOTE]
I have mine set to 791. Try that.
Here's my kernel line:

```
kernel /vmlinuz root=/dev/hda9 ro vga=791 quiet splash
```

---

### Post by dolny on 2005-06-14
PS -> 0.1-5 is not the newest version. That 0.1.3 is. It's not 0.1.5, it's 0.1-5.0 as far as I understand. That is why you mixed the versions ;)

---

### Post by bored2k on 2005-06-14
[QUOTE=Xian]I have mine set to 791. Try that.
Here's my kernel line:

```
kernel /vmlinuz root=/dev/hda9 ro vga=791 quiet splash
```[/QUOTE]
 Xian, **I **[COLOR=DarkRed]heart[/COLOR] you. It worked !  :-)

---

### Post by dolny on 2005-06-14
I'm gonna try that.

PS.  <pid>/etc/splashy/splashy.pid</pid> <-- I don't have splashy.pid file :/

---

### Post by dolny on 2005-06-14
Still doesn't work for me :( 
HELP! Do you have that pid file in the directory?
I get the message that Splashy is not running and because of that, it cannot send any messages. I see that green text progress notifications but no graphics :(((((

---

### Post by Xian on 2005-06-14
[QUOTE=dolny]
HELP! Do you have that pid file in the directory?[/QUOTE]
I don't have any pid file in that folder.

I added the ubuntu titled paths myself (for image files).
```
$ ls /etc/splashy
background.jpg  config.xml  config.xml~  error.jpg  Ubuntu  ubuntusplashy
```

---

### Post by dolny on 2005-06-14
Yeha I changed the paths in config.xml - they lead to good files but still... :(
My Kubuntu wants a splash screen :( *sniff*

---

### Post by Xian on 2005-06-14
[QUOTE=dolny]PS -> 0.1-5 is not the newest version. That 0.1.3 is. [/QUOTE]
Yes, you are absolutely correct. Thanks.
After splashy-0.1-5 the code was switched to C.

I forgot about that.  ;-)

---

### Post by Xian on 2005-06-14
dolny, did you install those two [deps](http://www.ubuntuforums.org/showthread.php?p=212901#post212901)?
[Ignore the version comment as you were right]

---

### Post by dolny on 2005-06-14
Yes :(

We'll, maybe they'll fix it in the next versions...

---

### Post by Xian on 2005-06-14
Heh. Don't give up just yet.
Does [THIS](http://www.ubuntuforums.org/showthread.php?t=37518) thread help at all?

---

### Post by dolny on 2005-06-14
I'm going to reinstall splashy. Here's what I got:

```
dolny@milkshake:~/zrzut$ sudo apt-get install splashy
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  splashy
1 upgraded, 0 newly installed, 0 to remove and 139 not upgraded.
Need to get 0B/414kB of archives.
After unpacking 397kB disk space will be freed.
WARNING: The following packages cannot be authenticated!
  splashy
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Odczytywanie bazy danych ... 102694 plików i katalogów obecnie zainstalowanych.)
Przygotowanie do zast&#261;pienia splashy 0.1.3.svn.2 (wykorzystuj&#261;c .../splashy_0.1.4.svn.1_i386.deb) ...
Rozpakowanie pakietu zast&#281;puj&#261;cego splashy ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /vmlinuz-2.6.10-5-686
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Konfigurowanie splashy (0.1.4.svn.1) ...
Instalowanie nowej wersji pliku konfiguracyjnego /etc/init.d/splashyZ ...
Instalowanie nowej wersji pliku konfiguracyjnego /etc/init.d/splashy10 ...
Instalowanie nowej wersji pliku konfiguracyjnego /etc/init.d/splashy20 ...
Instalowanie nowej wersji pliku konfiguracyjnego /etc/init.d/splashy30 ...
Instalowanie nowej wersji pliku konfiguracyjnego /etc/init.d/splashy40 ...
Instalowanie nowej wersji pliku konfiguracyjnego /etc/init.d/splashy50 ...
Instalowanie nowej wersji pliku konfiguracyjnego /etc/init.d/splashy60 ...
Instalowanie nowej wersji pliku konfiguracyjnego /etc/init.d/splashy70 ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /vmlinuz-2.6.10-5-686
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

**there is not grub installed**
WARN: could not create /etc/splashy/splashy.fifo. Make sure file exists and it's a fifo before using splashy
WARN: example: ls -l /etc/splashy/splashy.fifo. Permissions should be prwx------
WARN: to create it by hand follow:
WARN: rm -f /etc/splashy/splashy.fifo && mkfifo  --mode=0700 /etc/splashy/splashy.fifo

```

---

### Post by Xian on 2005-06-14
Yep, that's a problem.
But you gotta love how APT tells it like it is. :)

---

### Post by dolny on 2005-06-14
Tried to reinstall it from scratch, like in that link you gave me. No good. Going to sleep know. It just won't work with that /usr/ on diff partition. Tried EVERYTHING. It still shows that green letters and that info about config.xml.

---

### Post by lizardking on 2005-06-15
I noticed that **Splahsy works for me**, how I say up, but **I does not work when I halt the Computer**. I cannot see the Ubuntu-shutdown.jpeg in the background..

Some help?

---

### Post by intangible on 2005-06-15
[QUOTE=infinito]This howto will allow you to get a bootup image with progress bar, like the livecd does.
In this post i'm using my self-made theme. You can make your own or download another, it's up to you!

Splashy for Ubuntu

(1) Download latest splashy package from: [http://alioth.debian.org/projects/splashy/](http://alioth.debian.org/projects/splashy/) 

(2) Install the splashy .deb:
```
$ sudo dpkg -i splashy_0.1.3.svn.2_i386.deb
```
(3) Edit /boot/grub/menu.lst to add vga=792 (1024x768 millions colors) or vga=791 (1024x768 thousands colors) to your default boot option.
For example:```
title		Ubuntu, kernel 2.6.10-5-k7 Default 
root		(hd0,0)
kernel		/vmlinuz root=/dev/hde6 ro quiet splash vga=792
initrd		/initrd.img
savedefault
boot
```See codes table below:

(4) Download my Ubuntu splashy theme from: [http://infinito.f2o.org/downloads/ubuntu_splashy_theme.tar.gz](http://infinito.f2o.org/downloads/ubuntu_splashy_theme.tar.gz)

You can get more themes from: [http://splashy.alioth.debian.org/themes/](http://splashy.alioth.debian.org/themes/)

(5) Untar ubuntu theme:
```
$ tar xzf ubuntu_splashy_theme.tar.gz
```
(6) Copy files to splashy dir:
```
$ sudo cp -a ubuntu/ /etc/splashy/themes
```
(7) Edit splashy config file:
```
$ sudo mv /etc/splashy/config.xml /etc/splashy/config.xml.old
$ sudo mv /etc/splashy/themes/ubuntu/config.xml /etc/splashy
```
That's all! Next time you reboot your computer you'll see splashy in action!

Links of interest:
[http://nanofreesoft.org/index.php/Splashy](http://nanofreesoft.org/index.php/Splashy)
[http://nanofreesoft.org/index.php/Upower](http://nanofreesoft.org/index.php/Upower)

VGA Codes Table:```

                640x480    800x600    1024x768       1280x1024
256 colors        768        771         773            775
32K colors        784        787         790            793
64K colors        785        788         791            794
16M colors        786        789         792            795
```[/QUOTE]
 This one: [http://alioth.debian.org/download.php/1053/splashy_0.1.3.svn.2_i386.deb](http://alioth.debian.org/download.php/1053/splashy_0.1.3.svn.2_i386.deb) worked for me using the instructions the parent post provided.

A tip for others: you can test splashy after you've setup vga= and rebooted (to see if the image will display) using /etc/init.d/splashy start|stop
I've downloaded three themes, one of them does not work (one called ubuntusplashy I got from [http://ktown.kde.cl/~segfault/splashy/ubuntusplashy/)](http://ktown.kde.cl/~segfault/splashy/ubuntusplashy/)), but I don't know why, it has identical properties to the other themes.  I will trouble-shoot it.  

If you have a problem with the boot screen only showing up in your top left corner, (like 1/4 of the screen) try this:

sudo echo "mode=1280x1024">/etc/directfbrc

Replace mode with whatever resolution you set your vga= kernel line to use (I used 795 which is 1280x1024x16m).

Also, if you want your kernel upgrades to not lose the vga= line, make sure to add it to the end of the "# nonaltoptions="   line in "/boot/grub/menu.lst" (DO NOT REMOVE THE PRECEDING #)

---

### Post by Sionide on 2005-06-15
Wow, nice HOWTO. Hope it works for me, make sure it gets added to the Index of HOWTOs as well! I'm just waiting for a big file to upload before I reboot.

Edit: Whoo! It works great, this is a quality little trick. Should definately be made one of *the* ones to have... :)

---

### Post by sonny on 2005-06-15
This is a nice how-to... I could manage to make it work, although now I get an error every time I boot, its something about the kernel fonts, but I really don't know what does it means, or where to look for an answer, when it boots it loads the image, then the background image change to the  error one, and then to text mode, I know that error wasn't there before I did the boot splashy, cus I always looked what it was doing, can anyone help me??

---

### Post by elsewhere on 2005-06-15
I had splashy running on a previous install of Kubuntu.  It installed and worked without any issues, EXCEPT that it broke the suspend-to-RAM functionality on my laptop.  Machine couldn't recover from suspend, would hang at a blank screen.  I figure it had something to do with the text or graphics mode it was setting my card (nVidia) at, and I know the nVidia cards are fragile at best when handling suspend as it is.

Anyone else run into this ?  Is there maybe a way to restore my tty settings to normal after splashy runs ?

Also, Kubuntu users take a look at [this link](http://www.kde-look.org/content/show.php?content=22695) on kde-look for a custom splashy theme.

Cheers,
KV

---

### Post by lizardking on 2005-06-15
**My first theme for Ubuntu Splashy..**

You can download that here: [www.iacopomasi.net/UbuntuSmooth-alphaversion.tar.gz](http://www.iacopomasi.net/UbuntuSmooth-alphaversion.tar.gz) 
It based on UbuntuSmooth modified by me more clear....
This is UbuntuSmooth Gdm theme:
[IMG]http://gnome-look.org/content/m1/m22029-1.png[/IMG]

---

### Post by vaskark on 2005-06-15
[QUOTE=sonny]This is a nice how-to... I could manage to make it work, although now I get an error every time I boot, its something about the kernel fonts, but I really don't know what does it means, or where to look for an answer, when it boots it loads the image, then the background image change to the error one, and then to text mode, I know that error wasn't there before I did the boot splashy, cus I always looked what it was doing, can anyone help me??[/QUOTE]

Is the error "t_kernel_font: Invalid arguement"? The same thing happens to me. Don't have a solution, though. Does anyone?

---

### Post by sonny on 2005-06-15
[QUOTE=vaskark]Is the error "t_kernel_font: Invalid arguement"? The same thing happens to me. Don't have a solution, though. Does anyone?[/QUOTE]

Yes that's my error... and I suppouse WE NEED HELP...

---

### Post by infinito on 2005-06-15
[QUOTE=sonny][QUOTE=vaskark]Is the error "t_kernel_font: Invalid arguement"? The same thing happens to me. Don't have a solution, though. Does anyone?[/QUOTE]Yes that's my error... and I suppouse WE NEED HELP...[/QUOTE]
 From the [Splashy website](http://nanofreesoft.org/index.php/Splashy) (FAQ section):
>  At about 70-80% of booting process Splashy goes to verbose mode and shows:

  t_kernel_font: Invalid Argument

It's a bug related with the /etc/init.d/console-screen.sh file that does not set the font for framebuffer properly, this bug is unsolved. The work around is to edit the config.xml and set:

   1. "autoverboseonerror" to "no" 

---

### Post by sonny on 2005-06-15
well that is easy... why didn't I tought about it???  :razz:

---

### Post by NeoChaosX on 2005-06-15
Works for me, except when I installed the Ubuntu theme on the first page, the shutdown screen didn't work. Boot-up screen shows up just fine, though.

EDIT: Never mind, a little tweaking got it working just fine.

---

### Post by sonny on 2005-06-15
Ok.. I've try it and it worked...

---

### Post by Labonte on 2005-06-16
does someone have a clue what todo?

found it my self... all i say is newbie to my self :D


/Labonte

---

### Post by flan on 2005-06-16
Hmm I can't get this to work...
It all seems fine but I get no image, only a black screen instead of the splash image.
I have set the 
#nonaltoption vga=791
but nothing to do... it keeps show me a black screen until gdm takes control...
any tips?

Update: if I do
```
sudo modprobe vesafb
``` 
and then 
```
sudo splashy boot
``` 
I can see the splash image but even if I insert vesafb in /etc/modules I still get the black screen instead of splash image...
perhaps do I recompile the kernel with vesafb support, and not as a module?

---

### Post by Takis on 2005-06-16
Installing the splashy .deb removed my grub line about Windows!
Luckily I checked it right after installing the deb, and copied the correct lines across from menu.lst.old that the installer created.

---

### Post by bored2k on 2005-06-16
[QUOTE=Takis]Installing the splashy .deb removed my grub line about Windows!
Luckily I checked it right after installing the deb, and copied the correct lines across from menu.lst.old that the installer created.[/QUOTE]
 Yes splashy doesnt like Windows. Luckily, I still had it in backup -thnx to grubconf ^_^-

---

### Post by Rule on 2005-06-16
they thanks for the how to worked like a charm :D

---

### Post by NeoChaosX on 2005-06-17
Oh crap.

Just found out that with the vga option enabled in grub, there is HUGE decrease in OpenGL performance. I went from 976fps in glxgears without the vga options to less than 200 with it. Anybody else have this problem?

---

### Post by WiLLiE on 2005-06-17
[QUOTE=NeoChaosX]Oh crap.

Just found out that with the vga option enabled in grub, there is HUGE decrease in OpenGL performance. I went from 976fps in glxgears without the vga options to less than 200 with it. Anybody else have this problem?[/QUOTE]

Nope.. I  get 7100fps+ in glxgears.. no decrease here.

---

### Post by ArBaDaCarBa on 2005-06-17
[QUOTE=infinito]This howto will allow you to get a bootup image with progress bar, like the livecd does.
In this post i'm using my self-made theme. You can make your own or download another, it's up to you!

Splashy for Ubuntu

(1) Download latest splashy package from: [http://alioth.debian.org/projects/splashy/](http://alioth.debian.org/projects/splashy/) 

(2) Install the splashy .deb:
```
$ sudo dpkg -i splashy_0.1.3.svn.2_i386.deb
```
(3) Edit /boot/grub/menu.lst to add vga=792 (1024x768 millions colors) or vga=791 (1024x768 thousands colors) to your default boot option.
For example:```
title		Ubuntu, kernel 2.6.10-5-k7 Default 
root		(hd0,0)
kernel		/vmlinuz root=/dev/hde6 ro quiet splash vga=792
initrd		/initrd.img
savedefault
boot
```See codes table below:

(4) Download my Ubuntu splashy theme from: [http://infinito.f2o.org/downloads/ubuntu_splashy_theme.tar.gz](http://infinito.f2o.org/downloads/ubuntu_splashy_theme.tar.gz)

You can get more themes from: [http://splashy.alioth.debian.org/themes/](http://splashy.alioth.debian.org/themes/)

(5) Untar ubuntu theme:
```
$ tar xzf ubuntu_splashy_theme.tar.gz
```
(6) Copy files to splashy dir:
```
$ sudo cp -a ubuntu/ /etc/splashy/themes
```
(7) Edit splashy config file:
```
$ sudo mv /etc/splashy/config.xml /etc/splashy/config.xml.old
$ sudo mv /etc/splashy/themes/ubuntu/config.xml /etc/splashy
```
That's all! Next time you reboot your computer you'll see splashy in action!

Links of interest:
[http://nanofreesoft.org/index.php/Splashy](http://nanofreesoft.org/index.php/Splashy)
[http://nanofreesoft.org/index.php/Upower](http://nanofreesoft.org/index.php/Upower)

VGA Codes Table:```

                640x480    800x600    1024x768       1280x1024
256 colors        768        771         773            775
32K colors        784        787         790            793
64K colors        785        788         791            794
16M colors        786        789         792            795
```[/QUOTE]
 Works perfctly fine for me, thanks !!
The only thing is I had to download the ubuntu theme from the alioth page and edit the config.xml by hand.
But it's perfectly working on boot and shutdow !!! :)

---

### Post by benplaut on 2005-06-17
isn't there *anyone* here who likes to know whats going on with their system?  :roll:

---

### Post by Xian on 2005-06-17
[QUOTE=benplaut]isn't there *anyone* here who likes to know whats going on with their system?  :roll:[/QUOTE]
Heh. That's what my Gentoo box is for. :)
Here it's playtime!!  [img]http://my.opera.com/forums/images/smilies/party.gif[/img]

---

### Post by intangible on 2005-06-18
[QUOTE=lizardking]**My first theme for Ubuntu Splashy..**

You can download that here: [www.iacopomasi.net/UbuntuSmooth-alphaversion.tar.gz](http://www.iacopomasi.net/UbuntuSmooth-alphaversion.tar.gz) 
It based on UbuntuSmooth modified by me more clear....
This is UbuntuSmooth Gdm theme:
[IMG]http://gnome-look.org/content/m1/m22029-1.png[/IMG][/QUOTE]

Love the UbuntuSmooth splashy theme, as well as the UbuntuSmooth Gnome splash screen.  Some very nice work there.

---

### Post by NeoChaosX on 2005-06-18
[QUOTE=WiLLiE]Nope.. I  get 7100fps+ in glxgears.. no decrease here.[/QUOTE]
So I'm the only one who gets a 80% performance decrease with the "vga=" option, then?

---

### Post by Takis on 2005-06-18
I think you are. I'm still running full speed.

For people who'd like to know what's going on with their system as well as have eyecandy:
[http://www.bootsplash.org/](http://www.bootsplash.org/)

---

### Post by flan on 2005-06-18
aaw... please help.
Splashy doesn't show any image at boot...
it says: "splashy is not running... no commands can be sent"

but... it works fine when I shut down the system...

what's happen?

my splashy version is 0.1.5.svn1_i386
I just followed [this](http://nanofreesoft.org/index.php/Splashy#Splashy_just_doesn.27t_work:) how-to and this is what I get... a shutdown image but still no boot image

---

### Post by picpak on 2005-06-18
Does this work for 686 systems?

---

### Post by tristan on 2005-06-18
[QUOTE=picpak]Does this work for 686 systems?[/QUOTE]

Yep. I'm running it with no probs on a 686-smp kernel. That's the beauty of splashy, it's kernel independent.

---

### Post by bored2k on 2005-06-19
[QUOTE=tristan]Yep. I'm running it with no probs on a 686-smp kernel. That's the beauty of splashy, it's kernel independent.[/QUOTE]
 Hey, not only do you get a cute splashy, but with the vga=791 trick you get gourgeous bash prompts (ctrl+alt+f1-f7) :D !

---

### Post by tristan on 2005-06-19
[QUOTE=bored2k]Hey, not only do you get a cute splashy, but with the vga=791 trick you get gourgeous bash prompts (ctrl+alt+f1-f7) :D ![/QUOTE]

Everybody's a winner!!!

---

### Post by ltmon on 2005-06-19
I'm having splashy work fine for boot up using vga=792 and vga=791, but it kills my virtual terminals ... they just have random screen noise on them.  Shutdown looks similar to the messed up virtual terminals.

Any idea how to fix this?

L.

---

### Post by dolny on 2005-06-19
I have a problem. I finally got splashy to work, with vga=791 or vga=0x3...something ;) but I still have black spaces on the left and right side of the screen. Splashy isn't sufficiently stretched horizontally. It doesn't look so cool... can somebody help?

---

### Post by spockrock on 2005-06-19
Thanks I just grabed the packages Xian pointed to and it worked fine for me.......

---

### Post by Xian on 2005-06-19
Can you adjust your monitor settings using the hardware controls while the boot is ongoing? This generally will not effect what appears (or the image dimensions) after X is started.

---

### Post by UbuWu on 2005-06-19
I hope the splashy site will have a theme section soon. On the mailing lists I read that the 0.2 version will start earlier in the boot process, so no cryptic messages at all anymore!

---

### Post by Xian on 2005-06-19
[QUOTE=UbuWu]On the mailing lists I read that the 0.2 version will start earlier in the boot process, so no cryptic messages at all anymore![/QUOTE]
Do you happen to have a link to that mailing list?

---

### Post by spockrock on 2005-06-20
I would post the splashy theme I made but I dunno if I would be violating a license thing but its modified from the edgegreeter and edgegreeter 3 themes.........that I got off gnome-look.com.....but here is what the bootup screen looks like;
[http://img.photobucket.com/albums/v605/redemma/ubuntu/background.jpg](http://img.photobucket.com/albums/v605/redemma/ubuntu/background.jpg)

---

### Post by Xian on 2005-06-20
Yeah, I'm curious what people are using.

Here's my Debian and Ubuntu splash in order:
You can get them [HERE](http://www.kiskeyix.org/downloads/debian-embelisher/themes/splash/) and [HERE](http://splashy.alioth.debian.org/themes/).

I modified the Debian image to include some text and a progress box (not shown).

[img]http://img.photobucket.com/albums/v469/camplear/forums/silent-1024x768.png[/img]

[img]http://img.photobucket.com/albums/v469/camplear/forums/background.png[/img]

---

### Post by Sionide on 2005-06-20
I hope future versions have the ball filling up slowly, rather than bit by bit - make it flow in or something. Eye candy is niiiice!! :)

---

### Post by UbuWu on 2005-06-20
[QUOTE=Xian]Do you happen to have a link to that mailing list?[/QUOTE]

Yes: [http://lists.alioth.debian.org/pipermail/splashy-devel/2005-May/000004.html](http://lists.alioth.debian.org/pipermail/splashy-devel/2005-May/000004.html)

---

### Post by Xian on 2005-06-20
[QUOTE=UbuWu]Yes: [http://lists.alioth.debian.org/pipermail/splashy-devel/2005-May/000004.html](http://lists.alioth.debian.org/pipermail/splashy-devel/2005-May/000004.html)[/QUOTE]
That's kinda scarey. That list has been dead since May.
[Mailing List Archives](http://lists.alioth.debian.org/pipermail/splashy-devel/)

---

### Post by Goshawk on 2005-06-21
Hi to all.
I'm (or better, i was ) the main developer (project admin) of splashy.
It's from a long time that i don't see this forum and i'm happy that splashy is a used program.
'm happy to see that many people are making their themes and i'll announce that i'm developing a way to install themes by debian packages (just apt-get install theme-xxx.deb).
But as you guys are looking splashy, from version 0.1.1 is not so affidable as version 0.1-5 why?
Because the code is rewritten in C and because it does not work "just reading the terminal" but with fifos that increaze the boot time of 4 seconds (yes! 4 seconds!).
so another project, I hope it will the last, after usplash and splashy the same code is called upower from Usermode graPhical pOWER-on and it wants to be an eye candy bootsplash system that want to be faster than possible.
Unfortunately there is not a 0.1 version of upower because we are working on it right now. We hope to relase it at the end of June and it will be like splashy-0.1-5 with some bug fixes and a better scrollbar support (more smooth).

Thanks for the time that you, my reader, have spent reading this message, hoping it will help you solving your bootsplash problem :D

---

### Post by bored2k on 2005-06-21
Thanks a lot :D Goshawk !

---

### Post by Xian on 2005-06-21
[QUOTE=Goshawk]We hope to relase it at the end of June and it will be like splashy-0.1-5 with some bug fixes and a better scrollbar support (more smooth)[/QUOTE]
Thanks so much for the info. If there is a mailing list or new wiki that we can use to stay updated on this new Upower project please let us know.

---

### Post by picpak on 2005-06-21
I tried installing the new Splashy, and I got this:

```
Selecting previously deselected package splashy.
(Reading database ... 59659 files and directories currently installed.)
Unpacking splashy (from splashy_0.1.5.svn2_i386.deb) ...
dpkg: dependency problems prevent configuration of splashy:
 splashy depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
dpkg: error processing splashy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 splashy
```

How can I get libc6 2.3.2.ds1-21?

---

### Post by Kyral on 2005-06-21
Works GREAT! But, where can I find more Splashy Themes? I'm looking for like an Aqua ish theme, with Ubuntu on it

---

### Post by spockrock on 2005-06-21
[QUOTE=picpak]I tried installing the new Splashy, and I got this:

```
Selecting previously deselected package splashy.
(Reading database ... 59659 files and directories currently installed.)
Unpacking splashy (from splashy_0.1.5.svn2_i386.deb) ...
dpkg: dependency problems prevent configuration of splashy:
 splashy depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
dpkg: error processing splashy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 splashy
```

How can I get libc6 2.3.2.ds1-21?[/QUOTE]

all I did was go to the ubuntu packages and install the breezy libc6 files............

---

### Post by bored2k on 2005-06-21
[QUOTE=Kyral]Works GREAT! But, where can I find more Splashy Themes? I'm looking for like an Aqua ish theme, with Ubuntu on it[/QUOTE]
 Just make one yourself. [http://www.linuxeu.de/images/wallpaper/ubuntu/ubuntu.html](http://www.linuxeu.de/images/wallpaper/ubuntu/ubuntu.html)

---

### Post by XDevHald on 2005-06-21
Hmm, I have everything installed correctly, but when I reboot, it shows the clock down to 3-2-1-0 then it just shows the background a little bit then goes into normal boot with all the OK listings. What did I do wrong?

---

### Post by Goshawk on 2005-06-22
The new splashy packages are compiled for debian sid (because all the splashy team now uses debian), this is why there are too many problems with dependencies and so.

We are reorganizzating nanofreesoff organizzation, we are going to dismiss the wiki and use a better CMS system.

news about upower (the new admin of splashy is Luis Mondesi) will appear on [www.nanofreesoft.org](www.nanofreesoft.org) .

---

### Post by Xian on 2005-06-22
[QUOTE=Goshawk]We are reorganizzating nanofreesoff organizzation, we are going to dismiss the wiki and use a better CMS system. news about upower (the new admin of splashy is Luis Mondesi) will appear on [www.nanofreesoft.org](www.nanofreesoft.org) .[/QUOTE]
Great. That explains alot.
Thanks again for the info and much appreciation for the project.

---

### Post by darknuala on 2005-06-22
[QUOTE=intangible]This one: [http://alioth.debian.org/download.php/1053/splashy_0.1.3.svn.2_i386.deb](http://alioth.debian.org/download.php/1053/splashy_0.1.3.svn.2_i386.deb) worked for me using the instructions the parent post provided.

A tip for others: you can test splashy after you've setup vga= and rebooted (to see if the image will display) using /etc/init.d/splashy start|stop
I've downloaded three themes, one of them does not work (one called ubuntusplashy I got from [http://ktown.kde.cl/~segfault/splashy/ubuntusplashy/)](http://ktown.kde.cl/~segfault/splashy/ubuntusplashy/)), but I don't know why, it has identical properties to the other themes.  I will trouble-shoot it.  

If you have a problem with the boot screen only showing up in your top left corner, (like 1/4 of the screen) try this:

sudo echo "mode=1280x1024">/etc/directfbrc

Replace mode with whatever resolution you set your vga= kernel line to use (I used 795 which is 1280x1024x16m).

Also, if you want your kernel upgrades to not lose the vga= line, make sure to add it to the end of the "# nonaltoptions="   line in "/boot/grub/menu.lst" (DO NOT REMOVE THE PRECEDING #)[/QUOTE]
 When I try this step:
$ sudo cp -a ubuntu/ /etc/splashy/themes

I get this message:
cp: cannot stat `ubuntu/': No such file or directory

any ideas?

---

### Post by chaumurky on 2005-06-23
Would there be anything done here that can cause my Gnome setup go strange. My symptoms are:

* application windows are missing the top bar and cannot be moved.
* alt-tab combo doesn't work
* window list is empty.


I installed:

* libdirectfb-0.9-22_0.9.22-1_i386.deb
* lib++dfb-0.9-22_0.9.22-1_i386.deb
* splashy_0.1.5.svn2_i386.deb

Perhaps there is a logfile I can check to see where the error is occuring?

EDIT: Hmm, strike that. I uninstalled the packsges with no effect. I thought I'd start up a vncserver session to see if the problem showed up there and it did. After loggin out of that session, however, my window list etc reappeared! Time to ghost my system partition before anything gets worse methinks...  :???:

---

### Post by byen on 2005-06-23
Oh crap! after looking at all these guys talk about it..i decided to try..and now my whole boot-up is screwed .. i get the image and everything but then i get the error: 
Error:
I cannot start the Xserver (your graphical interface). It is likely that it is not set-up correctly. would you like to view Xserver output.

Man.. after 2 months I had to go back to windows to type this ..... its 3 in the morning and all i can think about is punching myself in the face... ahhhh help!

---

### Post by Goshawk on 2005-06-23
[QUOTE=byen]Oh crap! after looking at all these guys talk about it..i decided to try..and now my whole boot-up is screwed .. i get the image and everything but then i get the error: 
Error:
I cannot start the Xserver (your graphical interface). It is likely that it is not set-up correctly. would you like to view Xserver output.

Man.. after 2 months I had to go back to windows to type this ..... its 3 in the morning and all i can think about is punching myself in the face... ahhhh help![/QUOTE]
 byen:
first let we know which version you are using.

Than...

nothing is lost: power-on your pc and when you get the X error push CTRL+ALT+F2 ytu will see a console.
Then log in... and do: $sudo apt-get --purge remove splashy .
It will do all the hard work and restore your system to be like your splashy installation.

For all the people that have problems with splashy i advice to wait for upower that should fix many problems related with fifos, time and X compatibility.

---

### Post by byen on 2005-06-23
i used splashy_0.1.3.svn.2_i386.deb available at their site.... and yes, a helpful hand helped me figure out the uninstallation of splashy. guess 4 now i'll wait out for upower. thank you for your help  goshawk.

---

### Post by Rob2687 on 2005-06-24
[QUOTE=byen]i used splashy_0.1.3.svn.2_i386.deb available at their site.... and yes, a helpful hand helped me figure out the uninstallation of splashy. guess 4 now i'll wait out for upower. thank you for your help  goshawk.[/QUOTE]
 Works okay here, but only at boot. When I shut down, the screen just flashes a bunch of garbled characters. It works if I switch from the nvidia to the nv driver though :/

---

### Post by jr0 on 2005-06-26
Just out of curiosity.. If we ALL seem to want this feature, and Ubuntu LiveCD seems to include it...why isn't it "preinstalled" ? Don't we don't have enough things to manually configure? This is better than the way bootsplash.org does it. It's unnecessary to patch the kernal to make a splash, this proves it. Worked for me, still some text but overall a big improvment. Keep up the good work Goshawk!!!

---

### Post by tristan on 2005-06-26
[QUOTE=Rob2687]Works okay here, but only at boot. When I shut down, the screen just flashes a bunch of garbled characters. It works if I switch from the nvidia to the nv driver though :/[/QUOTE]

You might need to play with the vga modes in /boot/grub/menu.lst. By default it's set to 792 (1024x768x24bit). 

Just out of interest I tried changing vga modes and found that I could get splashy workin g happily on boot but not shutdown. Perhaps the reverse might work for you?

---

### Post by Xian on 2005-06-26
[QUOTE=jr0]Just out of curiosity.. If we ALL seem to want this feature, and Ubuntu LiveCD seems to include it...why isn't it "preinstalled" ?[/QUOTE]
Because even the author admits it will not consistently work on every system, and the project is still in its infancy. It wouldn't do to include an application that is provided by default, but has the side effect on many machines of not showing the boot routine or even allowing a person to login to their desktop session.

---

### Post by DShafik on 2005-06-26
Seems to work fine for me, at least for bootup. Haven't tried to shutdown since I restarted first time.

Thanks :)

- Davey

---

### Post by jr0 on 2005-06-26
[QUOTE=Xian]Because even the author admits it will not consistently work on every system, and the project is still in its infancy. [/QUOTE]
So it goes with a good % of Linux apps, as far as I can tell.

I'm thinking towards the future here, once the bugs are worked out I'd like this in my distro by default.

---

### Post by tristure on 2005-06-26
[QUOTE=spockrock]all I did was go to the ubuntu packages and install the breezy libc6 files............[/QUOTE]
 Yeah well... Don't know about you, but doing so broke 3 pakcages in my system and I don't know how to get them back allright.

So I would recommend not to do that.

Broken packages are libc6-dev, libc6-i686, locales....

---

### Post by tristure on 2005-06-27
OK, my system is back to normal situation. I had to uninstall the broken packages, then reinstall them and reinstall all the packages that had been uninstalled.

Quite uncomfortable.

Now I like the splash screen very much, so if anyone has suggestions so as to install a correct libc6 without breaking packages, I'd be very grateful!

---

### Post by NeoChaosX on 2005-06-28
Okay, fresh install of Hoary fixed the OpenGL performance problems I had.

However, I'm also getting that same bail-out-of-splash-at-70% problem described [here](http://www.ubuntuforums.org/showpost.php?p=215021&postcount=47) with 0.1.3 of splashy, and the fix on that post doesn't seem to work. Going back to 0.1-5 causes splashy to screw up, and I don't want to upgrade libc just to use 0.1.5. Anybody else suffer this problem and/or have an answer?

---

### Post by Goshawk on 2005-06-29
[QUOTE=NeoChaosX]Okay, fresh install of Hoary fixed the OpenGL performance problems I had.

However, I'm also getting that same bail-out-of-splash-at-70% problem described [here](http://www.ubuntuforums.org/showpost.php?p=215021&postcount=47) with 0.1.3 of splashy, and the fix on that post doesn't seem to work. Going back to 0.1-5 causes splashy to screw up, and I don't want to upgrade libc just to use 0.1.5. Anybody else suffer this problem and/or have an answer?[/QUOTE]
 Hi.
What do you mean when you say: "0.1-5 causes splashy to screw up"?

---

### Post by Heliode on 2005-06-29
[QUOTE=jr0]Just out of curiosity.. If we ALL seem to want this feature, and Ubuntu LiveCD seems to include it...why isn't it "preinstalled" ?[/QUOTE]

Because I don't want to use it. I like to see what's going on. As do a lot of other linux-users I can assure you.

I AM using the vga=792 mode in menu.lst though so I can have my entire bootup procedure on one screen, but I wouldn't use a splash screen myself, basically because it happened to often to me that Windows just stopped loading and I didn't know what's going on. At least with Linux, you can see what is going on, or at least where it is stopping. 

I've heard people mention splash screens will be included in Breezy. That's fine with me, since lots of people seem to like them, but I'd like a way to turn them off.
You should try booting in 1024x768. I use text-mode quite a lot and it looks a lot better that way.

That said, I have installed this on my GF's box and she seems to like it a lot.
A minor problem though: every 20 boots the / partition gets a check. Somewhat depending on the size and speed of the drive, this can take quite a while. With a splash screen you can't see what's going on, and you're just wondering what the thing is doing for 10 minutes. (I know, I know, you can make it go away by hitting ESC, but still)


Just my 2c

---

### Post by Goshawk on 2005-06-29
Hi Heliode.
I think that You are not well informed, let's talk.
On Windows you don't have the feature to choose if you want a graphical boot or not and you will never know what windows does while it's booting (but it's not true if you are a microsoft employer).
I use Linux (and not windows either Mac even if it is a bsd derivate) because I can choose and I'm developing upower to give to the linux users the ability to choose.
We don't hate the normal boot system, but we know that for the 90% of the time we boot our system it's unuseful.. why? because it's ever the same (ever the same sarvices that run correctly). So why not make it eye-candy? Upower will ever go to the standard and loved "normal mode" (verbose mode) when it reachs an error (Reading the terminal) or if you press F2 or ESC. And... with upower you can install and remove the program (and themes in future) with just an apt-get.

Probably not any bootsplash system will be included in Breezy, Why? because for now there is not a good system that does it work very well.

Thanks...

---

### Post by NeoChaosX on 2005-06-29
[QUOTE=Goshawk]Hi.
What do you mean when you say: "0.1-5 causes splashy to screw up"?[/QUOTE]
It was previously not showing a splash and giving me errors about how it couldn't find the splashy executable during boot-up.

Then I figured out I had to install a couple other dependencies, and now splashy 0.1-5 works just fine, and doesn't bail out early.

---

### Post by Goshawk on 2005-06-30
NeoChaosX can you be more precise about htese dependencies? (how many? what?)
Upower is going to be relased very soon, so more detail you wil explain about your problem and we will find a better way to solve those.

Thanks

---

### Post by UbuWu on 2005-06-30
Goshawk, when you google for splashy you first come across [http://alioth.debian.org/projects/splashy/](http://alioth.debian.org/projects/splashy/) which links to [http://splashy.alioth.debian.org/wiki](http://splashy.alioth.debian.org/wiki) which doesn't exist... (should be [http://splashy.alioth.debian.org/](http://splashy.alioth.debian.org/) ???) And then there is [http://nanofreesoft.org/](http://nanofreesoft.org/) where all images are broken... A little bit confusing alltogether...

---

### Post by Goshawk on 2005-06-30
I'm still not the admin of Splashy (yes i was).
The new project admin uses alioth for his development and he set up a wiki for splashy that now seems to be broken. I don't know why and it's not my job.

nanofreesoft.org is accessible, i connected to it one minute ago and it works correctly but yesterday for a power cut here in Sicily we were offline for 2 hours.
Btw on nanofreesoft.org you will not found information about splashy.

---

### Post by vipernicus on 2005-07-01
Question: I roll my own kernel.  Is there any kernel patch involved in getting this to work?  Is bootsplash or fbsplash applied to default ubuntu sources?   
Thanks.

---

### Post by intangible on 2005-07-01
AFAIK, it works without kernel patches, that is what's great about it compared to other bootup splash programs.  You just have to make sure you have a framebuffer in your kernel, or initrd

---

### Post by Albaraha on 2005-07-01
I have it working but apt-get always complains that:
> $ sudo apt-get install
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  splashy: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is installed
E: Unmet dependencies. Try using -f.

I'm using Ubuntu 5.04

---

### Post by bored2k on 2005-07-01
[QUOTE=Albaraha]I have it working but apt-get always complains that:

> You might want to run `apt-get -f install' to correct these. 
I'm using Ubuntu 5.04[/QUOTE]
 sudo apt-get -f install

---

### Post by Albaraha on 2005-07-02
[QUOTE=bored2k]sudo apt-get -f install[/QUOTE]
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  splashy
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 516kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

---

### Post by spockrock on 2005-07-02
hmmm....I had splashy 1.3 svn working with my old installation but due to a kernal sync error, I had to reinstall, now if I try 1.3 or 1.5 the gdm never loads and all I get is a light blue screen.........I switch to linux to avoid blue screens, but any ways it works with earliest version 1-5 but I dunno what I dont have that is causing this problem.......

---

### Post by Goshawk on 2005-07-02
Splashy uses the old libdirectfb at version 0.9.20 while 0.9.22 is out from some months.
This library has the blue screen that IMHO i really dislike it.

Upower uses 0.9.22 so at least it will no work but you wil never see "blue screens" :D

Remember that for now version 1-5 is equal to any svn version of splashy, the real difference is that 0.1-5 is in c++ while 0.1 and previous versions are in C.

---

### Post by traherom on 2005-07-02
I got Splashy working on the second try! I wiped my machine, then followed the instructions at [http://www.nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1#What.27s_upower.3F](http://www.nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1#What.27s_upower.3F).

The one problem I ran into was I didn't have libglibmm installed, but after I apt-geted that, it worked fine!

There exact steps I followed:
1. Download [Splashy](http://kalatlug.nanofreesoft.org/Projects/splashy/relases/splashy_0.1-5_i386.deb) (version 1-5), [directfb](http://kalatlug.nanofreesoft.org/Projects/splashy/libraries/libdirectfb/libdirectfb-0.9-22_0.9.22-1_i386.deb), and [libfb++](http://kalatlug.nanofreesoft.org/Projects/splashy/libraries/lib++dfb/lib++dfb-0.9-22_0.9.22-1_i386.deb). 
Because I downloaded them through Firefox, they ended up at ~/Desktop.

2.In a console type:
```
cd ~/Desktop
sudo apt-get install libglibmm-2.4-1
dpkg -i *.deb
```

---

### Post by Albaraha on 2005-07-02
[QUOTE=traherom]I got Splashy working on the second try! I wiped my machine, then followed the instructions at [http://www.nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1#What.27s_upower.3F](http://www.nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1#What.27s_upower.3F).

The one problem I ran into was I didn't have libglibmm installed, but after I apt-geted that, it worked fine!

There exact steps I followed:
1. Download [Splashy](http://kalatlug.nanofreesoft.org/Projects/splashy/relases/splashy_0.1-5_i386.deb) (version 1-5), [directfb](http://kalatlug.nanofreesoft.org/Projects/splashy/libraries/libdirectfb/libdirectfb-0.9-22_0.9.22-1_i386.deb), and [libfb++](http://kalatlug.nanofreesoft.org/Projects/splashy/libraries/lib++dfb/lib++dfb-0.9-22_0.9.22-1_i386.deb). 
Because I downloaded them through Firefox, they ended up at ~/Desktop.

2.In a console type:
```
sudo apt-get install libglibmm-2.4-1
dpkg -i *.deb
```[/QUOTE]


Thanks traherom.
The only missing thing when trying to get Splashy on Ubuntu Hoary is to have the proper .deb file, which is [this one](http://kalatlug.nanofreesoft.org/Projects/splashy/relases/splashy_0.1-5_i386.deb), not the one in the start of this thread.

---

### Post by NeoChaosX on 2005-07-03
[QUOTE=flan]aaw... please help.
Splashy doesn't show any image at boot...
it says: "splashy is not running... no commands can be sent"

but... it works fine when I shut down the system...

what's happen?[/QUOTE]

Having reverse problem; start-up splash works fine, but shotdown gets me the "Splashy is not running error" except for the last two seconds of the shutdown, when the splash image finally springs up. Annoying to death.  ](*,)

---

### Post by zerohalo on 2005-07-03
Works for me (using Splashy 0.1-5) on startup, but not on shutdown (actually it did work on shutdown the first time around, but not in subsequent experiments--now I just get the usual verbose shutdown).

---

### Post by Xian on 2005-07-03
I had that for awhile but realized I didn't have both directfb and libfb++ installed.
Seems to be working fine now.

---

### Post by gammyhand on 2005-07-03
[QUOTE=Xian]I had that for awhile but realized I didn't have both directfb and libfb++ installed.
Seems to be working fine now.[/QUOTE]
 I have some initial problems:

1) I downloaded the package and extracted it but it said my version os lib6c is wrong and I can't see how to correct that.

2) I don't know how to make menu.lst writeable.

3) People are talking about an install package and I have no idea where to get this.

---

### Post by chaumurky on 2005-07-03
Post #118 of this thread got it working for me, thank you. I think I'll only use it on my wife's PC though.  :wink:

---

### Post by traherom on 2005-07-03
[QUOTE=chaumurky]Post #118 of this thread got it working for me, thank you. I think I'll only use it on my wife's PC though.  :wink:[/QUOTE]Woot!  [img]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/img]

I'm telling her though... ;)

---

### Post by Skel on 2005-07-04
i cant seem to get this 2 work...  i see booting 10%, 20% and so on pop up when the lines come up but no screen darn ](*,)

---

### Post by Sianis on 2005-07-04
Hi all!

I installed the splashy (0.1.3). It works good, but when i click shoutdown, the shoutdown screen is the start screen, but i setup the shoutdown screen a shoutdown screen. In the shoutdown progress it's showing the status bar, and not the shoutdown text. What need to do, so work better this program? 

Upgrade, or what?

---

### Post by hunteramor on 2005-07-04
For anyone that runs into the same problem, I had issues with splashy 1.0.5 requiring a higher version of libc6 than my language support stuff (specifically chinese), so every time that the higher version was installed, synaptic would demand i uninstall the language support, and every time the lower version was installed, splashy would not function properly.

The solution I settled on was just to user splashy 1.0.3 instead. If anyone has a better solution, I'm game, but I thought posting this experience might save a newbie like me a half-hour of frustration.

---

### Post by wherethebibawi on 2005-07-05
[QUOTE=picpak]I tried installing the new Splashy, and I got this:

```
Selecting previously deselected package splashy.
(Reading database ... 59659 files and directories currently installed.)
Unpacking splashy (from splashy_0.1.5.svn2_i386.deb) ...
dpkg: dependency problems prevent configuration of splashy:
 splashy depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
dpkg: error processing splashy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 splashy
```

How can I get libc6 2.3.2.ds1-21?[/QUOTE]
 i have had the same dependancy problems. 
the way i got around the is a bit of a trick, 
STEP1: i used synaptic to uninstall the splashy package; (you will find it under broken packages)
STEP2: the splashy system uses libdirectfb librarys, so do a search for libdirectfb, i found that none of these librarys had been installed. If there not installed mark them for installation.
STEP3: After the libdirectfb librarys have been installed Go through the splashy install again step by step, and it should work. 

PS: you will need these librarys installed as well
lib++dfb-0.9-22_0.9.22-1_i386

---

### Post by NeoChaosX on 2005-07-05
Actually, his problem is a conflict with libc, which is a core component of just about everything in Ubuntu, so there's no upgrade for it if you're running Hoary. Your steps work with 0.1.3 or 0.1-5, but not 0.1.5. Probably only Breezy users can use 0.1.5 right now, but I'm not completely sure.

---

### Post by gammyhand on 2005-07-05
[QUOTE=NeoChaosX]Actually, his problem is a conflict with libc, which is a core component of just about everything in Ubuntu, so there's no upgrade for it if you're running Hoary. Your steps work with 0.1.3 or 0.1-5, but not 0.1.5. Probably only Breezy users can use 0.1.5 right now, but I'm not completely sure.[/QUOTE]
 Right. I will try 0.1.3 :)

---

### Post by gammyhand on 2005-07-05
[QUOTE=gammyhand]Right. I will try 0.1.3 :)[/QUOTE]
 I have splashy! woo!

---

### Post by minimidgy on 2005-07-05
when mine boots, it doesn't load my graphics drivers before the splash comes up, so it looks really bad.  Is there a way where I can make my computer load the graphics drivers before the splash screen?

---

### Post by Xian on 2005-07-05
Link: [Upower Amost Ready](http://www.nanofreesoft.org/modules.php?op=modload&name=News&file=article&sid=11&mode=thread&order=0&thold=0):

[i]"Today we coded the last feature of upower, now we wil clean the source code and then upower-0.1 will be relased, we hope to relase it before the end of this week. Thanks to Denis Oliver Kropp we solved the last bug about the keybuffer. We will publish this part of code under the Programming section of this site as a tutorial to make a keybuffer on ++dfb.

From 2 weeks we were working on this hard bug, now upower is capable of go to the verbose mode when you press F2 or the Esc button of the keyboard. Today we will start purging the code, committing the solved bug to the svn server and prepare upower-0.1 that will be relased soon."[/i]

---

### Post by NeoChaosX on 2005-07-05
Upower better fix this "no shutdown splash until the last two seconds" problem I've been having with splashy.

---

### Post by Xian on 2005-07-06
[QUOTE=NeoChaosX]Upower better fix this "no shutdown splash until the last two seconds" problem I've been having with splashy.[/QUOTE]
Yeah, or what? LOL. This project is still heavy in development.
Let's not be too critical. :)

---

### Post by NeoChaosX on 2005-07-06
Haha. Okay, didn't mean to be so demanding, but it is quite an annoying bug. It works when rebooting, why not while an actual shut down? I meant that I hope it fixes it.

---

### Post by acascianelli on 2005-07-07
I figured out how to fix the problem where it won't show status beyond 70%.  

The problem is that when Splashy is installed, only the scripts for 0-70% are generated.  80, 90 and 100% are not present.  So what I did was a I went into the /etc/init.d folder and duplicated the splashy70 file and renamed then to splashy80 and splashy90, edited them and changed all the 70's to 80's and 90's depending on which file I was editting.  Then I went into the /etc/rcS.d, /etc/rc0.d, and /etc/rc6.d and created the proper links to point to the scripts I made in /etc/init.d.

I sucessfully got 80 and 90% markers working but I'm a little unsure what to do for 100%.  I'll post how to get 100% working when I figure it out.

UPDATE:

Creating a splashy99 file and setting the percentage numbers to 100 inside the file completes the progress bar like it should.  I think I did a pretty good job reverse engineering this program for an intermediate linux user.

---

### Post by Goshawk on 2005-07-07
Hi to all
Upower is under testing, it will be published Saturday.

In the meantime, if someone want to see how it works, go to nanofreesoft.org and get the upower video, that is a movie of a running upower system on a ubuntu pc (mine)

nb: a link to this video is in the upower page and another one in the last post of the site.

ps: before the 15/07 also amd64 packages will be available (i'm waiting my new amd turion laptop)

---

### Post by acascianelli on 2005-07-07
[QUOTE=Goshawk]Hi to all
Upower is under testing, it will be published Saturday.

In the meantime, if someone want to see how it works, go to nanofreesoft.org and get the upower video, that is a movie of a running upower system on a ubuntu pc (mine)

nb: a link to this video is in the upower page and another one in the last post of the site.

ps: before the 15/07 also amd64 packages will be available (i'm waiting my new amd turion laptop)[/QUOTE]
 How do you know it will be released this saturday?  Will it be added to the Ubuntu repositories, and will it be used in Breezy?

---

### Post by intangible on 2005-07-07
Lookin' good

---

### Post by acascianelli on 2005-07-07
I just watched the video...

It looks identical to Splashy, in fact I'm convinced it is Splashy.  I thought this UPower was something totally new.

Not impressed.

---

### Post by Goshawk on 2005-07-08
upower, like splashy, is not affilied with Gnu/Linux ubuntu anymore (this is why we use a penguin as default theme instead of the ubuntu logo)
But... while splashy is developed mainly from people that uses debian (sarge and sid), upower is developed on ubuntu hoary (so no problems with library dependencies).
I hope that upower will be added to the breezy repo, but i don't think it will be.
Because upower is just a "child" program and because it works only on vesa compatible video cards. We are working to make upower compatible with al the init systems and all the framebuffer devices, but there is still work to do.

ps: yes it looks like splashy because "it was splashy" but in the underground it works in a different way: no fifos and proceses but direct text read and threads.

---

### Post by nickless on 2005-07-08
I have a strange problem here. Since I started messing with splash screens, my ubuntu only boots every second time I try it. The only thing I changed was the menue.list . Before trying Splashy I tried to get the grub splash screen working, the boot problem occured while working on it.
It tells me it's loading modules, but takes forever. When I restart sometime the same happens while loading the hot plug system. Has anyone experienced similar problems?

---

### Post by NeoChaosX on 2005-07-10
Upower's out. Fixed the shutdown image problems I was having. It changes the way you work with themes, though.

There are now two files you mess with. In /etc/upower, there's now *global-config.xml*, which includes the important AutoverboseOnError setting. But to set the splash images, you have to set up a seperate directory with the splash images and a seperate config.xml file. Each theme's config.xml has the settings that adjust the look of the progress bar and the images to be used in the splash (which used to be in */etc/splashy/config.xml*). To use the new theme you set up, set */etc/upower/theme* to be a symbolic link to the directory of the theme you want to use.

Here's an example of how to set it up:

1. Create a new directory in the upower folder (e.g., **sudo mkdir /etc/upower/ubuntu**)
2. Copy or move the images you want for splash screens into the new directory (e.g., **sudo mv ~/background.png /etc/upower/ubuntu**)
3. Copy config.xml from the default theme's directory  (e.g., **sudo cp /etc/upower/default/config.xml /etc/upower/ubuntu**) and edit the version in your theme directory to point to your splash images and mess with the progress bar as you see fit.
4. Remove the existing */etc/upower/theme* file (**sudo rm -rf /etc/upower/theme**)
5. Recreate the file as a link pointing to your new theme folder (**sudo ln -s /etc/upower/ubuntu /etc/upower/theme**)
6. Reboot, and enjoy awesome boot-up and shutdown splash screens.  :cool: 

Hope this helps anyone confused with how to get it working.

---

### Post by Goshawk on 2005-07-10
nice :D but i've more to say

Very soon we will publish a theme maker package in whic a theme maker will pu his theme in a directory inside the source tree and do ./create then debuild o dpkg-buildpackage and a .deb file with the theme will be created (also the symb link to /etc/upower/theme will be upgraded automatically when you add a new theme).

The theme-maker's package is almost ready we should fix just one thing and try it for 3 or 4 days.

---

### Post by acascianelli on 2005-07-10
So let me get this straight, after reading the FAQ from nanofreesoft.org UPower = USplash?  So can we look forward to seeing this in the final release of Breezy.  I understand better now what UPower is and why it looks so much like Splashy.  I'm going to give it a try later today when I get a chance.

---

### Post by Goshawk on 2005-07-10
No. it's beter to say upower ~ (almost) usplash  because:
1) it works in a different way than usplash
2) because it exists ( usplash does not exist, it's just a program "in mind" no more)

I hope to see it in breezy....
For now ubuntu managers said that upower will not added to breezy because it is not compatible with all the graphic cards and because in some systems it breaks the "suspend" mode.
Really the problem isn't upower itself but the vesa framebuffer. upower can work in all the framebuffers and vesa is the most compatible.
We will find a way to fix it...

---

### Post by picpak on 2005-07-10
](*,) There's no improvement at all with Upower!

Same VESA problems, same green text...everything!

I give up. How do I remove all these hundreds of programs it made me install?

---

### Post by Goshawk on 2005-07-10
picpak: please explain your problem in detail, if possible on another thread, since this is for splashy and not upower: you can use ubuntu forum or nanofreesoft forum.

to remove a program on ubuntu you should use synaptic or.. apt

sudo apt-get --purge remove upower libdirectfb lib++dfb

---

### Post by picpak on 2005-07-10
I know how to remove programs...it's just that Upower had a ton of dependecies. For Splashy, I kept getting an undefined mode number error message, and then just the green text popping up instead of the actual image. The same thing happened for Splashy. I was hoping Upower would work automatically - all the manual editing I did with Splashy killed my computer.

---

### Post by Xian on 2005-07-11
Just wanted to say, very nice job Goshawk.
Upower installed nicely and worked right away.

There were a few deps but everything was in the Ubuntu repos.
A simple 'apt-get -f install' resolved those.

Only thing I've noticed is the splash screen seems to exit a little early.
On the boot sequence it reverts to text about 5 seconds before GDM loads.

Other than that, no problems. Look forward to more from this..... :)

---

### Post by djSeverin on 2005-07-11
Just another Splashy theme, so nothing too special.

:idea: I've included the Gimp project in the attached archive if anyone wants to use it as a template to build their own splash.

[Edit: Have updated theme quite a bit, also includes error splash now]

---

### Post by Goshawk on 2005-07-11
djSeverin: very good theme :D . I think that i'll use yours.

Xian: thanks i've alredy in mind how to fix that problem. for now upower is stupid, it waits for 5 seconds afther the 6th script and then exit, in my pc this time is ok to don't show the terminal but it's not valid elsewhere. I'm looking to make upower able to recognise if gdm is loaded and running.
BTW i should add to the nanofreesoft.org upower page to do 'apt-get -f install'. gonna do it

picpak: you have 2 ways
1) remove upower and forget about it on your system, in this case the packages that upower uses are:
upower libdirecfb lib++dfb libboost-thread1.31.0 libglibmm-2.4-1 libsigc++-2.0-0 libxml++2.6

You can see them using dpkg on the upower package.

remove it
2)Help us to find this problem telling to me:
What graphic card do you have?
Do you see the image just for a second or do you see nothing?
Can you explain better about "green text"?
Can you write (in a easy English please because i'm an italian student) a detailed description of what you see? (referring to seconds if possible, for example: at almost 2 seconds i see the green text saying " bla bla bla".)

---

### Post by charlieg on 2005-07-16
Working great using Upower.  Used the ubuntu splashy theme and it seems happy.

There was on caveat - the updates needed seemed to break something to do with the setting of console fonts.  I just commented out the section the "Global default font+sfm" in /etc/init.d/console-screen.sh and it stopped complaining without any noticable side-effects.

---

### Post by gammyhand on 2005-07-16
[QUOTE=djSeverin]Just another Splashy theme, so nothing too special.

:idea: I've included the Gimp project in the attached archive if anyone wants to use it as a template to build their own splash.

[Edit: Have updated theme quite a bit, also includes error splash now][/QUOTE]
Looks cool. How do I install this theme?

---

### Post by UbuWu on 2005-07-16
[QUOTE=Goshawk]
For now ubuntu managers said that upower will not added to breezy because it is not compatible with all the graphic cards and because in some systems it breaks the "suspend" mode.
Really the problem isn't upower itself but the vesa framebuffer. upower can work in all the framebuffers and vesa is the most compatible.
We will find a way to fix it...[/QUOTE]

I hope you can fix it in the next few weeks, because on august 11th there is the feature freeze for breezy...

---

### Post by Goshawk on 2005-07-16
charlieg: very good. you fixed an old bug thanks :D

---

### Post by traherom on 2005-07-17
[QUOTE=gammyhand]Looks cool. How do I install this theme?[/QUOTE]Extract it into /etc/splasy/themes/shiny, then copy the .conf file to /etc/splashy

---

### Post by gammyhand on 2005-07-17
[QUOTE=traherom]Extract it into /etc/splasy/themes/shiny, then copy the .conf file to /etc/splashy[/QUOTE]
 Thanks.

---

### Post by crashd on 2005-07-19
Splashy doesn't work for me. I have installed the 0.1.3 version of splashy and i read in boot only the 10%, 30%, 50% ecc. but not the images.  How i can solve?  What is Upower? How i get it?  Sorry for my bad english

---

### Post by Triton on 2005-07-19
Make sure the section in your /etc/splashy/config.xml points to the right location of your splash images.

> <background>
        <boot>/etc/splashy/themes/kubuntu/background.jpg</boot>
        <shutdown>/etc/splashy/themes/kubuntu/shutdown.jpg</shutdown>
        <errorimg>/etc/splashy/themes/kubuntu/error.jpg</errorimg>
 <autoverboseonerror>yes</autoverboseonerror>
    </background> 

and all the proper dependencies are installed.

---

### Post by crashd on 2005-07-19
[QUOTE=Triton]Make sure the section in your /etc/splashy/config.xml points to the right location of your splash images.

 

and all the proper dependencies are installed.[/QUOTE]
Ok, now work! Is fantastic...  thank you a lot!!!

---

### Post by pailhead on 2005-07-20
Can I install the splashy_0.1.5.svn2_i386.deb onto a ubuntu system or do I have to compile from source?

I'd like to run this but it's not in the ubuntu repositories...

Thanks...

---

### Post by pailhead on 2005-07-20
Ok I added,

the following line to my sources.list:

```
deb http://splashy.alioth.debian.org unstable main
```

Now when I do "apt-get install splashy" I recieve the following error:

```
root@srq-c12u:/home/pailhead # apt-get install splashy
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  splashy: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages
root@srq-c12u:/home/pailhead # apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

What can I do to fix the depency problem with splashy install?

---

### Post by cdean on 2005-07-20
[QUOTE=pailhead]Ok I added,

the following line to my sources.list:

```
deb http://splashy.alioth.debian.org unstable main
```

Now when I do "apt-get install splashy" I recieve the following error:

```
root@srq-c12u:/home/pailhead # apt-get install splashy
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  splashy: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages
root@srq-c12u:/home/pailhead # apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

What can I do to fix the depency problem with splashy install?[/QUOTE]
 libc6 has not been upgraded in the repositories to the newest version yet.  This is a problem that I hope will be solved soon, as it seems to break most Debian 3.0 packages that I've tried to install (Kismet among them since it, too, is out of date in the Ubuntu reps).

---

### Post by pailhead on 2005-07-20
Ok so I'll have to wait on the install of splashy on my Hoary system then...

---

### Post by nickless on 2005-07-20
How about an Howto- make your own splashy themes?
If somebody knows, please tell me :D , but I'll try to find out, too... when I have again some more spare time :)

---

### Post by traherom on 2005-07-21
[QUOTE=nickless]How about an Howto- make your own splashy themes?
If somebody knows, please tell me :D , but I'll try to find out, too... when I have again some more spare time :)[/QUOTE]Just copy one of the ones already posted here. Assume you images will be put into /etc/splashy/themes/<your theme name>, then copy a config file change the image paths to the correct location.

You also have to change the progress bar indicator color and position, in the same config file.

---

### Post by rwabel on 2005-07-24
[QUOTE=Goshawk]nice :D but i've more to say

Very soon we will publish a theme maker package in whic a theme maker will pu his theme in a directory inside the source tree and do ./create then debuild o dpkg-buildpackage and a .deb file with the theme will be created (also the symb link to /etc/upower/theme will be upgraded automatically when you add a new theme).

The theme-maker's package is almost ready we should fix just one thing and try it for 3 or 4 days.[/QUOTE]
 I wanted to give Upower a try, but [http://www.nanofreesoft.org/](http://www.nanofreesoft.org/) webpage seem to be down. What's going on? Any chance to get the files?

---

### Post by Goshawk on 2005-07-24
yes nanofreesoft.org is down for a power cut. it will be restored on Monday.

sorry.

---

### Post by SuperMike on 2005-07-25
Two questions on this:

* Why not investigate how the LiveCD does it and copy that technique? There will be hooks in certain places to look for.

* Is this Splashy thing the one that runs in User mode, not Kernel mode? That's important to know because I don't want to trash my Kernel for something like this.

One statement:

* Seems like this could trash someone's init scripts and/or cause a kernel panic if I'm not mistaken here, right? I would recommend a big disclaimer in bold.

---

### Post by NeoChaosX on 2005-07-25
Splashy/UPower runs in user mode, not kernel mode. It's designed to be a splash program that doesn't require installing a new kernel to work.

---

### Post by SuperMike on 2005-07-25
[QUOTE=dolny]I have a problem. I finally got splashy to work, with vga=791 or vga=0x3...something ;) but I still have black spaces on the left and right side of the screen. Splashy isn't sufficiently stretched horizontally. It doesn't look so cool... can somebody help?[/QUOTE]

Do you have an LCD Panel type of display? I found that on these types of displays, they autosense what's being sent to them and will either shift, stretch, or compress depending on what's being sent -- and especially during the boot process or at a full screen command prompt (CTRL+ALT+F1, for instance). I picked up my LCD Panel from Wal*Mart and although it's a nice one, it does this unless I go in and set the settings for each of these modes. At that point, it has "memory" and remembers to display the image in that width on each of these modes.

---

### Post by SuperMike on 2005-07-26
Do you like to tinker? If so, read on...

The dependencies were killing me both on the dpkg technique and the apt-get splashy technique for splashy. So...

During bootup, there's a way to show an image on your framebuffer fairly easily while loading bootup text in the background as a background process. This technique can run in user mode, not kernel mode, and not have any dependencies like splashy requires.

1. Expand your /etc/apt/sources.list to include universe and then do apt-get install fbi. You will need the fbi command. You will only need this once to make your splash image, but then you won't need that anymore. (What I'm trying to say here is that the fbi command will not be required to display the image all the time. I'm not trying to insinuate that the fbi command is a dependency for displaying splash screens on bootup.)

2. Add the vga=790 on the end of your kernel statement in /boot/grub/menu.lst as you've been directed previously on this thread. Note if that fails, somewhere in this thread it explains what else to do, such as vga=791, etc.

3. Get your favorite 16 bit color depth background image and save it in your root's home directory. Save it as mysplash.png.

4. Reboot and bootup to the gdm login screen, then switch to console mode with CTRL+ALT+F1.

5. su to root.

6. Write this first script:

#!/bin/bash
# save me as snapclick.sh
sleep 10
cp /dev/fb0 screen.dump

7. Write this second script:

#!/bin/bash
# save me as loadimage.sh
/bin/bash snapclick.sh &
fbi mysplash.png

8. Run this in the console mode window (CTRL+ALT+F1):

/bin/bash loadimage.sh

9. When the image loads, press the V key.

10. Count to 10 fairly slowly, then hit your spacebar.

11. Now you're back at the console prompt. Now, let's view that image with:

clear
cat screen.dump > /dev/fb0

12. You'll notice that it displays the image and then is interrupted by text at the top. If you kept your system in a sleep loop with "sleep 15" and then cleared the screen when done with "clear", the text would not interrupt your image.

Got your mind thinking here? Good. Now think what would happen if you edited the udev script in /etc/init.d (one of the first init scripts on the system) so that it does "cat screen.dump > /dev/fb0" and then sends all text either to another framebuffer screen or loads all other text into the background as a background process with the "&" operator (including standard error). (Thus, no need to use a "sleep 15" command.)

Another thing to think about is that you can send VT100 characters to the screen with echo to clear the bottom row of the image. Then, set text to show up there by using the VT100 characters to lock-in this one row at the bottom of your screen as a locked scroll area. That's how older versions of Suse worked.

You can also dump multiple screens and simulate "animation" to some small degree with multiple "cat screen.dump > /dev/fb0" statements.

I leave it up to you to perfect this.

So what do you get out of this? Well, you had to use fbi and the scripts to get the image snapshot, but once you do this, your friends do not need this. They just need a screen.dump (or set of these) that will work on their system resolution and color depth. (So, provide a variety to choose from.) Then, you could build an installer that loads this image and then sends all other commands and error messages to the background. Last, when the gdm loads and reads its script for that, you could clear the screen, getting rid of this image.

In a nutshell, if you perfected this, you could provide a bootsplash that runs in user mode and which has **no dependencies**!

---

### Post by Goshawk on 2005-07-26
Hi
very good. you find out another way to make usermode bootsplashes but it's limitated.
Why?
because it's just a dumped image. you got just a snapshot of some images and you put them on the terminal at boot time, yes it works, but it's hard to manage.

Soon upower will be able to install themes by deb packages, and have animations, things that will spent too much time using sh scripts, that are really slow.

And... try to use your shapshot with other resolutions :D they will screw up... because fbi scales the images for the setted resolution, so you can not make a "universal" theme that you can install with debian packages that will work with all the resolutions.

In free software, dependencies are not pain, just a simple way to reuse code, and with apt-get they are easly fixed.

Nice to read your comments

---

### Post by rwabel on 2005-07-26
upower works fine! easy installation, thanks a lot

---

### Post by Goshawk on 2005-07-26
rwabel:
thanks... your feedback make my work useful.

---

### Post by rwabel on 2005-07-26
I've made a wiki howto for upower: [https://wiki.ubuntu.com/UPower](https://wiki.ubuntu.com/UPower)
If something is wrong, missing etc just edit it (if you have an account) or just let me know.

Looking forward for theme manager and other nice stuff!

---

### Post by intangible on 2005-07-27
Awesome, just upgraded from Splashy.

I had to install libgcc1 from Breezy though, I don't have any other breezy packages or backports installed, anyone else have this?

---

### Post by rwabel on 2005-07-27
[QUOTE=intangible]Awesome, just upgraded from Splashy.

I had to install libgcc1 from Breezy though, I don't have any other breezy packages or backports installed, anyone else have this?[/QUOTE]
 good question, I've just seen that I've the debian one installed. It was because of another tool. I can't tell you if the hoary version would be sufficient.
Can please someone confirm!

---

### Post by ACK!! on 2005-07-27
Ok, I followed the instructions to the letter though the original poster has a newer package and probably should imho update the instructions.  I used the newer one.

It worked perfectly.  

Btw, it does seem to slow up my bootup by about 5 seconds or so but nothing extreme.  

Along with the new grub splash I got elsewhere my Ubuntu no longer has the jarring text to graphics shift it used to.  

Thank you original poster.

The work on splashy is much appreciated.

I hope this makes it into the new version along with the Bootup Manager (for choosing services) and smeg (for editing the menu).

---

### Post by Jonathan2007 on 2005-07-27
Hello. I have previously used Splashly but I have reformatted and am thinking about using UPower seeing as how it is the succesor to Splashy.

I was looking on KDE-Look and found an awesome Splash screen but I don't think it was designed specifically for Splashly/UPower. [here](http://kde-look.org/content/show.php?content=26495) is then link to the splash screen. If someone could direct me what color settings and what x,y,z positions I should have to use this with UPower I would greatly appreciate it. Thanks.

Oh and I really appreciate all the hard work the devs have put into Splashy/UPower and I hope it will be included by default with Breezy.

---

### Post by rwabel on 2005-07-28
[QUOTE=ACK!!]Ok, I followed the instructions to the letter though the original poster has a newer package and probably should imho update the instructions.  I used the newer one.

It worked perfectly.  

Btw, it does seem to slow up my bootup by about 5 seconds or so but nothing extreme.  

Along with the new grub splash I got elsewhere my Ubuntu no longer has the jarring text to graphics shift it used to.  

Thank you original poster.

The work on splashy is much appreciated.

I hope this makes it into the new version along with the Bootup Manager (for choosing services) and smeg (for editing the menu).[/QUOTE]
 are u using splashy or upower? I suggets you install upower!

---

### Post by kalle314 on 2005-07-30
I have a question about how to change the UPower theme:

I followed the example in [https://wiki.ubuntu.com/UPower](https://wiki.ubuntu.com/UPower) , 
so now the symbolic link "theme" in /etc/upower/ leads to ubuntusplashy instead of default.

However, I'm still getting the default penguin. What could be wrong?

I have rebooted a few times since I made the change, but the ubuntusplashy image still wont show up.

---

### Post by rwabel on 2005-07-30
Are you sure that the theme now points to the ubuntusplash?
Here you can see how it was before and how it should look after!

drwxr-xr-x  2 root   root   144 2005-07-26 16:38 default
-rw-r--r--  1 root   root    97 2005-07-09 08:53 global-config.xml
lrwxrwxrwx  1 root   root     7 2005-07-26 16:37 theme -> default
drwxr-xr-x  2 rwabel rwabel 168 2005-04-18 15:33 ubuntusplashy

rwabel@RALPH:/etc/upower/ $ sudo rm -f /etc/upower/theme
rwabel@RALPH:/etc/upower $ ll
total 4
drwxr-xr-x  2 root   root   144 2005-07-26 16:38 default
-rw-r--r--  1 root   root    97 2005-07-09 08:53 global-config.xml
drwxr-xr-x  2 rwabel rwabel 168 2005-04-18 15:33 ubuntusplashy

rwabel@RALPH:/etc/upower $ sudo ln -s ubuntusplashy/ theme
rwabel@RALPH:/etc/upower $ ll
total 4
drwxr-xr-x  2 root   root   144 2005-07-26 16:38 default
-rw-r--r--  1 root   root    97 2005-07-09 08:53 global-config.xml
lrwxrwxrwx  1 root   root    14 2005-07-30 16:39 theme -> ubuntusplashy/
drwxr-xr-x  2 rwabel rwabel 168 2005-04-18 15:33 ubuntusplashy

---

### Post by kalle314 on 2005-07-30
Yes, that's how it looks for me too:

lrwxrwxrwx  1 root   root     13 2005-07-30 15:52 theme -> ubuntusplashy
drwxr-xr-x  2 troeng troeng 4096 2005-07-30 15:30 ubuntusplashy

I did solve the problem temporarily by re-naming the files

(sudo mv default default_old
sudo cp -r ubuntusplashy default)

which gives me the ubuntusplashy image, though I get the ordinary ubuntusplashy background instead of the ubuntusplashy shutdown background when i shut down.

EDIT: Sorry, I did just check my config.xml file, which said
       <boot>/etc/upower/default/background.jpg</boot>
        <shutdown>/etc/upower/default/shutdown.jpg</shutdown>
        <errorimg>/etc/upower/default/error.jpg</errorimg>

The problem is solved. 
Thanks for the help.

---

### Post by rwabel on 2005-07-30
[QUOTE=kalle314]Yes, that's how it looks for me too:

lrwxrwxrwx  1 root   root     13 2005-07-30 15:52 theme -> ubuntusplashy
drwxr-xr-x  2 troeng troeng 4096 2005-07-30 15:30 ubuntusplashy

I did solve the problem temporarily by re-naming the files

(sudo mv default default_old
sudo cp -r ubuntusplashy default)

which gives me the ubuntusplashy image, though I get the ordinary ubuntusplashy background instead of the ubuntusplashy shutdown background when i shut down.

EDIT: Sorry, I did just check my config.xml file, which said
       <boot>/etc/upower/default/background.jpg</boot>
        <shutdown>/etc/upower/default/shutdown.jpg</shutdown>
        <errorimg>/etc/upower/default/error.jpg</errorimg>

The problem is solved. 
Thanks for the help.[/QUOTE]
 good to know!

---

### Post by Aero-Z on 2005-07-31
I tryed them both- splashy & upower. None of them worked. Both gives me the green percentage text on boot up, but no picture. After long hours of messing around I had enough and removed any splash loader packages. Now, I still have the green percentage text when booting my system, How's that possible?

---

### Post by Goshawk on 2005-07-31
Aero-z

You have to purge the upower and splashy packages use synaptic to do that looking in the Custom package section or do:
sudo apt-get --purge remove upower splashy . And you will not see any green text.

---

### Post by Aero-Z on 2005-07-31
[QUOTE=Goshawk]Aero-z

You have to purge the upower and splashy packages use synaptic to do that looking in the Custom package section or do:
sudo apt-get --purge remove upower splashy . And you will not see any green text.[/QUOTE]
A also found out that if I reinstall upower (before the purge remove) then I have only folders in /etc/upower- no jpg-s or xml-s, only folders. Is this normal because I haven't done --purge before reinstalling upower?

---

### Post by Aero-Z on 2005-07-31
OK, I totally removed UPower and then installed it again. I didn't change any settings just to be shore not to screw up things. And as I thought, it still didn't work. First I tried different vga values 792, 791, 790. Every time I get "You have passed undefined mode number", also I've tried vga=normal. After that I get Starting upower for bootup... and no picture only green percentage texts 10%, 20% etc.. I don't know what to do anymore, do you?

---

### Post by Goshawk on 2005-08-01
it seems that your framebuffer is not setted properly.
First remove upower, do sudo apt-get --purge remove upower
then edit your /boot/grub/menu.lst look for the kernel image that you are using and add "vga=791" at the end of kernel line.
If you get the same error, do less /prov/fb and lspci and paste the results.

---

### Post by Aero-Z on 2005-08-01
[QUOTE=Goshawk]it seems that your framebuffer is not setted properly.
First remove upower, do sudo apt-get --purge remove upower
then edit your /boot/grub/menu.lst look for the kernel image that you are using and add "vga=791" at the end of kernel line.
If you get the same error, do less /prov/fb and lspci and paste the results.[/QUOTE]

I get the same error. I guess it's proc not prov, if I do 
# su - 
# /proc/fb

I get Permission denied.

If I do
# sudo less /proc/fb

I get just white terminal screen, with END at the bottom of it.

# /proc/lspci 

No such file or directory

Changed it to /usr/bin/lspci and got:

0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82815 815 Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 02)
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 02)
0000:01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by bgstratt on 2005-08-01
Not to be a troll, but I have almost the exact same problem and same /proc/fb and lspci on one of my computers, any help is greatly appreciated.

---

### Post by Goshawk on 2005-08-02
Ok found the problem!
The framebuffer is not set properly. In particular it does not starts at boot time. You are getting the same horrible big text at boot time, isn't it?

Be sure that you are using the ubuntu kernel and not yours. If you are using the ubuntu one past here your /boot/grub/menu.lst

Thanks

---

### Post by Aero-Z on 2005-08-02
[QUOTE=Goshawk]Ok found the problem!
The framebuffer is not set properly. In particular it does not starts at boot time. You are getting the same horrible big text at boot time, isn't it?

Be sure that you are using the ubuntu kernel and not yours. If you are using the ubuntu one past here your /boot/grub/menu.lst

Thanks[/QUOTE]

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage (hd0,1)/boot/grub/images/usplash.xpm.gz

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu Linux
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

---

### Post by Goshawk on 2005-08-03
Ok now go to this line:

# nonaltoptions=quiet splash

and change it with 

# nonaltoptions=quiet splash vga=791

Then do update-grub and reebot.

Look if the booting process will change, the text should be smaller.

When the system is up do less /proc/fb .

You should get somethig like this:

0 VESA VGA

.

ps: upower have been relased ofr amd64 platforms :D

---

### Post by Aero-Z on 2005-08-03
[QUOTE=Goshawk]Ok now go to this line:

# nonaltoptions=quiet splash

and change it with 

# nonaltoptions=quiet splash vga=791

Then do update-grub and reebot.

Look if the booting process will change, the text should be smaller.

When the system is up do less /proc/fb .

You should get somethig like this:

0 VESA VGA

.

ps: upower have been relased ofr amd64 platforms :D[/QUOTE]

Do I have to uncomment it too or only add vga=791?

---

### Post by bgstratt on 2005-08-03
I know that you're trying to help Aero-z, but when I add the comment vga=791, or 792 or any other number for that matter, I get an error in the beginning of bootup that says you have passed an undefined video mode, press spacebar or wait 30 secs to continue or enter to choose video mode, then when I press enter it will have a list of video modes, like:

80x25
80x60
80x30

and so on, then is will say to enter mode, or 'scan' to list more modes.  I had the same thing happen in MEPIS as well, but when I take off the vga=771 or whatever number, the system boots just fine without the undefined video mode.  This only happens on one of my computers though, the rest work just fine.  Also, when I do sudo dpkg-reconfigure xserver-xorg, it has extra display values other than the normal 1024x768, 800x600, 640x480, by this I mean it has steps or resolutions in between these, I don't mean the higher resolutions that appear normally.  I know this is not the purpose of the thread, but it is related I think.  

I am prone to think it is something to do with the video card, but like you said, splashy or upower should work with any card, right?  I haven't tried the nonaltoptions yet, I will try that when I get home, and 

yes Aero-Z you have to uncomment it for it to be read.

---

### Post by Aero-Z on 2005-08-03
[QUOTE=bgstratt]I know that you're trying to help Aero-z, but when I add the comment vga=791, or 792 or any other number for that matter, I get an error in the beginning of bootup that says you have passed an undefined video mode, press spacebar or wait 30 secs to continue or enter to choose video mode, then when I press enter it will have a list of video modes, like:

80x25
80x60
80x30

and so on, then is will say to enter mode, or 'scan' to list more modes.  I had the same thing happen in MEPIS as well, but when I take off the vga=771 or whatever number, the system boots just fine without the undefined video mode.  This only happens on one of my computers though, the rest work just fine.  Also, when I do sudo dpkg-reconfigure xserver-xorg, it has extra display values other than the normal 1024x768, 800x600, 640x480, by this I mean it has steps or resolutions in between these, I don't mean the higher resolutions that appear normally.  I know this is not the purpose of the thread, but it is related I think.  

I am prone to think it is something to do with the video card, but like you said, splashy or upower should work with any card, right?  I haven't tried the nonaltoptions yet, I will try that when I get home, and 

yes Aero-Z you have to uncomment it for it to be read.[/QUOTE]
Heh, I'm not trying to help, I'm trying to get helped :grin:

Just tried the nonaltoptions and still the same text: "You have passed undefined mode...." and less /proc/fb is still empty

---

### Post by bgstratt on 2005-08-03
I meant that goshawk was trying to help you, but it seems we keep getting the same error. with the undefined video mode.  So from what you said the nonaltoptions doesn't do anything different for you, I didn't think that it would, but you never can tell.  

I'm wondering now myself if it isn't the video card or driver.  but you use an nvidia card, whilst the one on that particular machine for me is the intel i815 video using the i810 driver, so perhaps not the card, I dunno. 

I haven't changed my installation procedures on any of the computers I've used, but each has a completely different hardware set up, all but this one have worked fine with upower, but then again, none of them had the same problem when trying to set vga=791 in menu.lst.  

Hopefully whatever help you can get, I can sponge off and use myself.  :grin:

---

### Post by rogeriovinhal on 2005-08-03
Worked fine for me if following the 1.3 version. 1.5 asks for a newer version of libc that is not on ubuntu repositories.

There's only one little problem that matters me. Is there any way that I can put a higher monitor frequency on the splash? The 60 Hz is killing me...

---

### Post by dude2425 on 2005-08-04
[QUOTE=bgstratt]
yes Aero-Z you have to uncomment it for it to be read.[/QUOTE]

I hope that's not what you're doing. In the menu.lst, you should NEVER uncomment anything below the lines that say:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

That could be you're problem if you in fact uncommenting them like any other configuration file.

So, Aero-Z, do NOT uncomment it.

---

### Post by Aero-Z on 2005-08-04
[QUOTE=dude2425]I hope that's not what you're doing. In the menu.lst, you should NEVER uncomment anything below the lines that say:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

That could be you're problem if you in fact uncommenting them like any other configuration file.

So, Aero-Z, do NOT uncomment it.[/QUOTE]
I tried without uncommenting it and it still didn't work. It added the line vga=791 to kernel line but "Undefined mode..." was still there.

---

### Post by bgstratt on 2005-08-04
my bad, thanks for straightening me out, sometimes I seem to forget that different files act extremely different to the comments, again, thanks for straightening me out, but like Aero-Z said, it doesn't make any difference either way.  It is not a user installation error, it has to do with different hardware.

---

### Post by Goshawk on 2005-08-05
[QUOTE=bgstratt]my bad, thanks for straightening me out, sometimes I seem to forget that different files act extremely different to the comments, again, thanks for straightening me out, but like Aero-Z said, it doesn't make any difference either way.  It is not a user installation error, it has to do with different hardware.[/QUOTE]
 Aero: find a way to put your framebuffer on, this is why upower does not start.
Ubuntu kernel have framebuffer enabled and you card is a nvidia so it's compatible with vesa like mine. Are you sure that you are using the ubuntu kernel?
If yes go to ask to google on how to set up your framebuffer: on normal system "vga=number" does the trick but it seems not your case.

---

### Post by Aero-Z on 2005-08-05
[QUOTE=Goshawk]Aero: find a way to put your framebuffer on, this is why upower does not start.
Ubuntu kernel have framebuffer enabled and you card is a nvidia so it's compatible with vesa like mine. Are you sure that you are using the ubuntu kernel?
If yes go to ask to google on how to set up your framebuffer: on normal system "vga=number" does the trick but it seems not your case.[/QUOTE]
I have the kernel that Ubuntu installed with the distro. I haven't changed it myself. I'm kind of newb with kernel stuff so I wouldn't like to risk finding framebuffer enabling myself and config it. Maybe someone here can give me some more specific instructions on how to enable framebuffer?

---

### Post by songochain on 2005-08-05
Hi! i've installed splashy and it only works with a linux-image but my compiled kernel it doesnt work. I want to know what modules i've to load using my compiled kernel???
Thanks

---

### Post by MiguelArevalo on 2005-08-06
[QUOTE=kleeman]None of it worked I'm afraid. The first fix just changed the boot(down) screen picture. The same error occured during bootup. I did notice however that the boot(up) screen appear extremely briefly. When I installed the other packages no boot(up) or boot(down) screens appear at all but it does claim that splashy is operating  ;-) 
Looks like I've been bitten by alpha software....[/QUOTE]


Ufff, I'm having the same problem and I have not found any solution for it, if you find any way of resolving this issue let me know please...

---

### Post by Goshawk on 2005-08-06
songochain: you need framebuffer support plus vesa framebuffer compiled as built-in
MiguelArevalo: are you using upower or splashy?

---

### Post by songochain on 2005-08-07
[QUOTE=Goshawk]songochain: you need framebuffer support plus vesa framebuffer compiled as built-in
[/QUOTE]
In device section, graphics and where u add framebuffer support, i see i've selected the same options than the linux-image config. When u do a lsmod, what modules u've to get splashy? fb and vesa?
Thanks

---

### Post by 8FootSativa on 2005-08-07
Has anyone had any luck with kbootsplash?

---

### Post by Goshawk on 2005-08-08
[QUOTE=8FootSativa]Has anyone had any luck with kbootsplash?[/QUOTE]
 Uhm. this sounds new for me so i went to the kbootsplash site.

It is not a real bootsplash system, it's just a program that let you change easy your bootsplash (Suse's bootsplash) theme. Nothing more or less.
It's like a graphic tool to configure bootsplash, it's not a bootsplash system.

If you download one of it's theme you will see that it is just a bootsplash theme (note the config.cfg).

Upower is a userland bootsplash so nothing to do with Suse's one or kbootsplash.

But kbootsplash could be a good idea. A graphic tool to configure your bootsplash system...

---

### Post by ivomans on 2005-08-14
[QUOTE=bgstratt]... I get an error in the beginning of bootup that says you have passed an undefined video mode, press spacebar or wait 30 secs to continue or enter to choose video mode...[/QUOTE]

I get the same message, only allowing me to choose mode 0F00...0F07 or 030A, which are all pure text modes.
I've got a Matrox Millenium GX400 video card, and when I do a [font=Courier New]cat /proc/fb[/font] it gives [indent]**[font=Courier New]0 MATROX[/font]**
[/indent]I've googled/guessed some video=... parameters but got no improvement. Anybody already found a solution for this?

On shutdown I do get a graphic image!

---

### Post by ndub on 2005-08-15
Hi all,
I run Ubuntu on a HP laptop dv4029EA with Intel Mobile Graphics Controller i915 1.2.0.
Splashy works quite good. However the resolution of my screen is 1280x800 and does not allow to have the logo as a perfect circle. The splashscreen is malformed.
Does anyone know the VGA value needed in menu.lst for that resolution?
Thanks in advance,

ndub

---

### Post by duffman25 on 2005-08-17
[QUOTE=ndub]Hi all,
I run Ubuntu on a HP laptop dv4029EA with Intel Mobile Graphics Controller i915 1.2.0.
Splashy works quite good. However the resolution of my screen is 1280x800 and does not allow to have the logo as a perfect circle. The splashscreen is malformed.
Does anyone know the VGA value needed in menu.lst for that resolution?
Thanks in advance,

ndub[/QUOTE]

Hi. Upower dev's have posted the amd64 version of upower a few days ago, but whenever I try to download the deb's there's one missing, the libdirectfb-0.9-22. Has anybody the same problem or is it just me?.

---

### Post by Goshawk on 2005-08-17
duffman25:
No it's there: in breezy it's in the repo, on hoary there is the package on nanofreesoft.
Note that in the download section there are: upower amd64 ubuntu hoary and upower amd64 ubuntu breezy. You have to download the one for your system.

ivomans:
your problem is not the framebuffer, because you have a shutdown pics. Instead the problem is in the boot process: do sudo upower boot and paste the result, maybe a image in a wrong location can do this error. waiting for feedback.

And for all the folks:
Upower-0.2 is going to be relased, the changelog is not so big but there are some modifications that will make the upower theme package work properly. I'm going to write this news on nanofreesoft site. see you.

Ah... we are looking also for developers...

---

### Post by duffman25 on 2005-08-17
[QUOTE=Goshawk]duffman25:
No it's there: in breezy it's in the repo, on hoary there is the package on nanofreesoft.
Note that in the download section there are: upower amd64 ubuntu hoary and upower amd64 ubuntu breezy. You have to download the one for your system.

And for all the folks:
Upower-0.2 is going to be relased, the changelog is not so big but there are some modifications that will make the upower theme package work properly. I'm going to write this news on nanofreesoft site. see you.

Ah... we are looking also for developers...[/QUOTE]

Good news :D. But I'm afraid I haven't made myself clear enough. I'm using hoary, and when I try to download the libdirectfb from nanofree I get a 404 ERROR. I'm trying to download it again, but your website is very slow :( Have you though about hosting your app here (as an alternative place) like some other 3rd party ubuntu proyect? (like smeg or gtkwifi).

Thanxs

---

### Post by Goshawk on 2005-08-17
Yes, our server is too slow, it's just a celeron 500 with 40gb of hd and 64 mb of ram with 3 gb of swap space. We are waiting for money to upgrade our hardware.
We want to concentrate people on our server, because we are planning to start many other projects, and some of them are not related with ubuntu.
On September we will upgrade our hardware and i hope that the site will be fast.

---

### Post by duffman25 on 2005-08-17
[QUOTE=Goshawk]Yes, our server is too slow, it's just a celeron 500 with 40gb of hd and 64 mb of ram with 3 gb of swap space. We are waiting for money to upgrade our hardware.
We want to concentrate people on our server, because we are planning to start many other projects, and some of them are not related with ubuntu.
On September we will upgrade our hardware and i hope that the site will be fast.[/QUOTE]

Thanxs for the info. But i'm still having a 404 while trying to download the deb's form upower (amd64):
[http://nanofreesoft.org/upload/dl/Projects/upower_amd64_ubuntu_hoary/libdirectfb-dev_0.9.22-0ubuntu3](http://nanofreesoft.org/upload/dl/Projects/upower_amd64_ubuntu_hoary/libdirectfb-dev_0.9.22-0ubuntu3)
gives me a 404. Can you please check it's ok? o attach the deb here, I want to play with my amd64 :P

---

### Post by ivomans on 2005-08-17
[QUOTE=Goshawk]duffman25:
your problem is not the framebuffer, because you have a shutdown pics. Instead the problem is in the boot process: do sudo upower boot and paste the result, maybe a image in a wrong location can do this error. waiting for feedback.
[/QUOTE]

The command 'sudo upower boot' does give a graphical screen, furthermore I got underneath output.
Hope it gives you a clue.

Ivo

 ```
	   ---------------------- DirectFB v0.9.22 ---------------------
			 (c) 2000-2002  convergence integrated media GmbH
			 (c) 2002-2004  convergence GmbH
		-----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2005-04-13 13:37)
(*) Direct/Memcpy: Using MMXEXT optimized memcpy()
(*) Direct/Thread: Running 'VT Switcher' (CRITICAL, 8750)...
(!) Direct/Modules: Unable to dlopen `/usr/lib/directfb-0.9.22/inputdrivers/libdirectfb_ps2mouse.so'!
	--> /usr/lib/directfb-0.9.22/inputdrivers/libdirectfb_ps2mouse.so: undefined symbol: direct_free
(*) Direct/Thread: Running 'Linux Input' (INPUT, 8751)...
 (!!!)  *** UNIMPLEMENTED [fusion_reactor_set_lock] *** [../../../lib/fusion/reactor.c:802]
(*) DirectFB/Input: AT Translated Set 2 keyboard (1) 0.1 (convergence integrated media GmbH)
(*) Direct/Thread: Running 'Linux Input' (INPUT, 8752)...
(*) DirectFB/Input: ImExPS/2 Logitech Explorer MouseLinux (2) 0.1 (convergence integrated media GmbH)
(*) Direct/Thread: Running 'Linux Input' (INPUT, 8753)...
(*) DirectFB/Input: PC Speaker (3) 0.1 (convergence integrated media GmbH)
(*) Direct/Thread: Running 'Keyboard Input' (INPUT, 8754)...
(*) DirectFB/Input: Keyboard 0.9 (convergence integrated media GmbH)
(*) DirectFB/Genefx: MMX detected and enabled
(*) DirectFB/Graphics: Matrox G400 0.7 (convergence integrated media GmbH)
(*) DirectFB/Core/WM: Default 0.2 (Convergence GmbH)
(*) Direct/Interface: Loaded 'JPEG' implementation of 'IDirectFBImageProvider'.

```

---

### Post by ndub on 2005-08-17
[QUOTE=ndub]Hi all,
I run Ubuntu on a HP laptop dv4029EA with Intel Mobile Graphics Controller i915 1.2.0.
Splashy works quite good. However the resolution of my screen is 1280x800 and does not allow to have the logo as a perfect circle. The splashscreen is malformed.
Does anyone know the VGA value needed in menu.lst for that resolution?
Thanks in advance,

ndub[/QUOTE]
 Any ideas?

---

### Post by arnieboy on 2005-08-17
thanks for the HowTO. worked perfectly in my case :)

---

### Post by traherom on 2005-08-18
Ok... so upower was just giving me the Booting at XX% messages there, so I tried your "sudo upower boot" thing... it gave me errors the first time, then I tried changing something, and I get nothing now. Changed it back and I still get nothing.  :???: 

Um... yeah. I did have Splashy working before this.

The one thing I know of that I might have screwed up is I changed the "theme" link in the /etc/upower directory to point to the shiny theme (I put that in /etc/upower/themes). However, when I first did that, I set it up to point to the folder, not the config file, which I believe is correct, but maybe I'm wrong... I also have a "default" link, which goes to the default theme (which I moved to /etc/upower/themes/default Well, I think I moved it. I don't remember now. :))

Could someone give me a quick run down on the config links and such? Thanks.

---

### Post by Goshawk on 2005-08-19
ivomans: sorry for the dalay but i reconfigured the nanofreesoft site.
Are you sure that your /usr is NOT on it's own partition but it's in the same one with /?

ndub: actually vesa seems to do not support 16:9 resolutions. Is it time to write another vesa driver that will be compatible with suspend mode or time to make upower able to choose between vesa and the framebuffer of your graphic card?
I'm in this question...

---

### Post by ivomans on 2005-08-19
[QUOTE=Goshawk]ivomans: sorry for the dalay but i reconfigured the nanofreesoft site.
Are you sure that your /usr is NOT on it's own partition but it's in the same one with /?[/QUOTE]

Yes, I'm sure: the entire system is on just one partition.

---

### Post by Intell on 2005-08-19
I tried this and I got a few dependency problems. They are as follows: 
```

dpkg: dependency problems prevent configuration of splashy:
 splashy depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
 splashy depends on libdirectfb-0.9-20; however:
  Package libdirectfb-0.9-20 is not installed.
dpkg: error processing splashy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 splashy

```

---

### Post by arnieboy on 2005-08-19
[QUOTE=Intell]I tried this and I got a few dependency problems. They are as follows: 
```

dpkg: dependency problems prevent configuration of splashy:
 splashy depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
 splashy depends on libdirectfb-0.9-20; however:
  Package libdirectfb-0.9-20 is not installed.
dpkg: error processing splashy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 splashy

```[/QUOTE]
The second error is self explanatory and all u need to do is:
```
sudo apt-get install libdirectfb
```
The first error can be avoided by installing an older version of splashy. Try to download the version released just before the latest one and ur installation should go fine.

---

### Post by dude2425 on 2005-08-19
upower doesn't install in breezy with the .deb file anymore, libxml++2.6, libsigc++-2.0-0, and libglibmm-2.4-1 were replaced with libxml++2.6c2, libsigc++-2.0-0c2, libglibmm-2.4-1c2 a while back. It shouldn't be to hard to recompile it against these three specialy for breezy.

Also, I had an idea for the next version:
Optional strings of text for bootup and shutdown so you can change the text to something like "Hey, what's happening?" without having to change your theme images. The config should allow you to specify the location on the screen, the color, font, and size.
Also, you can probably integrate upower into intramfs like usplash did
 > initramfs-tools (0.15)               

[list]
[*]"Nothing looks so like innocence as an indiscretion."
[*]- Oscar Wilde
[*]mkinitramfs: Handle putting DSDT.aml into the initramfs Add sata_nv to list of modules to import for main mode.
[*]*init: New scripts directory, init-premount for generic premount handling (like usplash)*
[*]debian/dirs: Make the /etc version of this directory for user addons.
[*]debian/rules: Use prebuild, rather than debian-build-arch.
[/list]Just a couple of ideas. No biggy

---

### Post by REBELinBLUE on 2005-08-29
I tried upower boot and get this

```
stephen@shuttle:~/Downloads/Linux$ sudo upower shutdown

       ---------------------- DirectFB v0.9.22 ---------------------
             (c) 2000-2002  convergence integrated media GmbH
             (c) 2002-2004  convergence GmbH
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2005-04-13 13:37)
(*) Direct/Memcpy: Using SSE optimized memcpy()
(!) DirectFB/FBDev: Couldn't open neither `/dev/fb0' nor `/dev/fb/0'!
    --> No such file or directory
(!) DirectFB/Core: Could not initialize 'system' core!
    --> File not found!
IDirectFB DirectFB::Create() -> File not found!
(!) [20760:    0.000] --> Caught signal 6 (unknown origin) <--
```

Any idea whats wrong? it works fine on my laptop

<edit>OK so thats shutdown, same thing

---

### Post by REBELinBLUE on 2005-08-30
[QUOTE=REBELinBLUE]I tried upower boot and get this

```
stephen@shuttle:~/Downloads/Linux$ sudo upower shutdown

       ---------------------- DirectFB v0.9.22 ---------------------
             (c) 2000-2002  convergence integrated media GmbH
             (c) 2002-2004  convergence GmbH
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2005-04-13 13:37)
(*) Direct/Memcpy: Using SSE optimized memcpy()
(!) DirectFB/FBDev: Couldn't open neither `/dev/fb0' nor `/dev/fb/0'!
    --> No such file or directory
(!) DirectFB/Core: Could not initialize 'system' core!
    --> File not found!
IDirectFB DirectFB::Create() -> File not found!
(!) [20760:    0.000] --> Caught signal 6 (unknown origin) <--
```

Any idea whats wrong? it works fine on my laptop

<edit>OK so thats shutdown, same thing[/QUOTE]
 Any ideas?

---

### Post by andromedakun on 2005-08-30
[QUOTE=arnieboy]The second error is self explanatory and all u need to do is:
```
sudo apt-get install libdirectfb
```
The first error can be avoided by installing an older version of splashy. Try to download the version released just before the latest one and ur installation should go fine.[/QUOTE]
 I tried to install Splashy, but it seems like I miss the libdirectfb library. Tried to install it from the Ubuntu CD but I can't find it on it. Does anyone have a place where I can get the .deb file for Ubuntu to install? This because I can't put the laptop on the network at work and thus cannot add sources to Synaptic.

Thanks ^^

---

### Post by REBELinBLUE on 2005-08-30
[QUOTE=andromedakun]I tried to install Splashy, but it seems like I miss the libdirectfb library. Tried to install it from the Ubuntu CD but I can't find it on it. Does anyone have a place where I can get the .deb file for Ubuntu to install? This because I can't put the laptop on the network at work and thus cannot add sources to Synaptic.

Thanks ^^[/QUOTE]
It's on the same site as Splashy/Upower

---

### Post by andromedakun on 2005-08-30
Hello again,

I could only find version 0.9.22 and did a 
sudo dpkg -i libdirectfb-0.9.22_0.9.22-1_i386.deb 
It gave no errors but when I try to install splashy with a:
sudo dpkg -i splasy_0_1.3.svn.2_i386.deb
it comes up with the error:
spalsy depends on libdirectfb-0.9-20; however:
  package libdirectfb-0.9-20 is not installed.

Does it have to be absolutely version 0.9-20? If yes, does someone have a link where I can download the Deb file?

thanks ;)

---

### Post by masteryoda on 2005-09-02
[QUOTE=Aero-Z]I tried without uncommenting it and it still didn't work. It added the line vga=791 to kernel line but "Undefined mode..." was still there.[/QUOTE]
 I am having exact same problems like Aero-Z... anyone has the solution for framebuffer???

---

### Post by Owdy on 2005-09-04
Is it possible to do like this [http://www.bootsplash.org/verbose-mode.jpg](http://www.bootsplash.org/verbose-mode.jpg) ?
And how do i uninstall splashy if i need to?

---

### Post by picpak on 2005-09-04
Well, I've figured out the problem is in libdirectfb...however, if I remove 0.9-20 I have to remove mplayer...and if I remove 0.9-22 I have to remove upower...Can I remove and reinstall mplayer without libdirectfb 0.9-20 causing any problems?

---

### Post by Quirky on 2005-09-04
[QUOTE=andromedakun]
Does it have to be absolutely version 0.9-20? If yes, does someone have a link where I can download the Deb file?[/QUOTE]

I installed it from Synaptic universe repos.

Is it my imagination, or does it take longer to boot with splashy enabled? I could swear it takes a good 20-30 seconds longer, but it might just be psyhcological. Anyone timed a non-splashy vs with splasy boot? Or in other words: what's the easiest way to temporarily disable splashy (for one boot, say) - uninstalling and then reinstalling everything? Or is there a secret 'splashy=ON' ins some file somewhere?

---

### Post by pinguimtux on 2005-09-06
Is there a way to have a boot splash but in verbose mode?

---

### Post by idn on 2005-09-08
Does anyone know if this will work on a widescreen monitor?

---

### Post by dude2425 on 2005-09-08
[QUOTE=pinguimtux]Is there a way to have a boot splash but in verbose mode?[/QUOTE]

upower, and splashy do not have that capability. The only reason bootsplash can do it is because it requires you to recompile you're kernel with certain patches applied to it. I'm sure it is possible for somebody to code something to work for that kind of thing, but untill somebody figures it out, we're all SOL. (unless of course you do know how to do that and have had a simple solution that you've been holding back on us. Then you're an a** hole for not sharing, and I will retract this comment when you finaly do share with us.)

---

### Post by Goshawk on 2005-09-09
Yep... when upower starts press F2 for the verbose mode.
Remember that for now the "verbose mode" is just the normal booting process.

I hope that in future even upower will have a verbose mode like suse's bootsplash

---

### Post by idn on 2005-09-16
Do you know when upower will be in the repos - all you have to do is apt-get install upower for example, it takes care of all the dependancies

---

### Post by jeffreyvergara.NET on 2005-09-17
hello, I just made splashy worked using the splashy_0.1.3.svn.2_i386.deb version, is splashy_0.1.5.svn.2_i386.deb newer and recommended for update?

i also noticed that the progress bar does not reach 100%, maybe around 65-70% only but it boots properly

---

### Post by phoenixdestroyed on 2005-10-18
Ok - I've been through the past 25 pages and I seem to be missing the part where someone says how to make this work. Has anyone gotten it to work with Breezy and if so how? When I try it wants to uninstall ubuntu....

---

### Post by fannymites on 2005-10-20
It wants to uninstall Ubuntu-desktop which is a meta package and doesn't actually remove anything important that I know of.  You may need it when upgrading to a newer ubuntu in future.  Unfortunately there doesn't seem to be any way to install splashy without removing ubuntu-desktop.
I have been running splashy since I started using hoary and have been using it on breezy for about 6 weeks with no problems.

---

### Post by Brando569 on 2005-10-21
where can i get  libgcc1 >= 4.0.0-7? i searched google and saw sum1 had said that it was in backports but i dont see it, the chat log i read was only from a month ago.... :confused:

---

### Post by scoldingice on 2005-10-21
ok i just read all 25 pages on this and am compleatly confused. i was wondering if someone would send me a straight out copy of the insturctions at [email]scoldingice@gmail.com[/email] if not i guess i'm sol. god i hate being a noob.

---

### Post by Goshawk on 2005-10-25
upower 0.2 for amd64 have been released, for x86 will be released saturday.

info: [http://nanofreesoft.org](http://nanofreesoft.org)

---

### Post by idn on 2005-10-25
Cool nice work, any chance of posting a howto for breezy? Upower is so much nicer than usplash,

---

### Post by Goshawk on 2005-10-26
look at [http://nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1](http://nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1)

---

### Post by zeca_pedra on 2005-12-31
Hi intangible

I did a test following your guidelines here and this is what I've got:
```
WARN: vga= was not found in /proc/cmdline. Did you append vga=0x317 to your kernel parameters? See README for more

(process:6091): GLib-CRITICAL **: g_ascii_strncasecmp: assertion `s1 != NULL' failed

(process:6091): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed

(process:6091): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed
ERROR: Setting XML file to <</config.xml>> failed. XML File not found.
ERROR: fatal: FIFO creation failed (null)
Error occured while starting splashy.Make sure that you have write access to the directory holding splashy.fifo
 * Starting splashy

```
I've vga=792 on my menu.lst file (which is the correct value for my monitor 1024x768@60hz) and I'm not understanding at al what could be the problem.

Can you help me on this? I'm pretty sure that I'm missing something really basic here but can't see what :-p

---

### Post by zeca_pedra on 2005-12-31
After setting correctly splashy I've already created a theme based on the wallpaper I have for my desktop.Everytnhing is fine and (almost) the way I want except... for the fact that the first thing I see in boot is the kubuntu splash screen!!!
It's there for 2 or 3 seconds and only after that I can see my boot splash getting started!
I've removed kubuntu-artwork-usplash thinking that this would remove that but it's still there!
What do I have to remove/tweak/set in order to ABSOLUTELY not see this kubuntu-splash and see the one I've set?
BTW, thanks to all in this thread, this has been a major help for my purposes. Thanks a lot to all of you,

Zeca

---

### Post by Goshawk on 2006-01-01
Hi
One thing that few people know is that usplash is not really a "only" userspace application. It uses an initramfs/initrg (i don't know which of them) image to show the first image. So it mainly starts by it.
When you install upower/splashy, the image is not touched and so you still see the old splash.
Fortunately there is a solution, it's a bit huge, but it works, look at:

[http://nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1#Download_upower](http://nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1#Download_upower)

It's for upower, but it should work also for splashy... or better it will...

---

### Post by pinguinus on 2006-04-05
What is that Upower project - and the state of it - that some people have mentioned in this thread? It seems like an interesting project but the web links to didn't work. I found about it not until now after having searched for Splashy related discussions here. 

I wonder if the project is dead already as the links pointing to the Upower project don't seem to work anymore? Proved to be too buggy perhaps? Or maybe I had just bad luck with timing and the website was down for some reason when I tried to go there? Anybody have better information? I haven't noticed any recent posts about the status of the Upower project here (although I didn't read this whole very long thread, all 26 pages of it).

EDIT: Cheesh... :-/ Here we go again... Just after I had written this message, I thought to try the Upower links again, and surprise, surprise, now they worked fine.... So forget my above question about the status of the Upower project... 8)

---

### Post by Goshawk on 2006-04-05
Upower is a fork of Splashy. When some developers started to translate the c++ code to c in splashy i did not agree with them. I was the main developer of Splashy, in fact Splashy 0.1 was released by me.
Now Splashy is going to change itself and going to be like usplash. In the meantime upower is going to be developed in a new way.
Upower is 100% usermode (Splashy and Usplash depends from an initramfs image, try to change the kernel and if you don't put the initramfs image they will not work).
Upower is lite: it was the first bootsplash that supports changable themes via an apt-get way. apt-get install upower-theme-themename will install the new theme without the need to configure any file.
Upower uses xml file configurations.

Even if there is one active developer, upower is in development...

for info: [www.nanofreesoft.org](www.nanofreesoft.org)

---

### Post by plush on 2006-04-22
Alright, I'm using the 0.1.5 debian package for PowerPC, and on bootup I get the following errors:
(process: 2017): GLib-Critical **: g_ascii_strncasecmp: assertian `s1 != NULL` failed.
(process: 2017): GLib-Critical **: g_string_append: assertion...

and a few more lines like this, I couldn't catch them all to write them down.  I figured I'm missing a library, but which?  When I installed the debian package it said I had all the dependencies!  Thanks for any help.

---

### Post by Adrian_b on 2006-05-03
> sagara@sousuke:~/Themes$ agi upower
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  upower: Depends: libboost-thread1.33.0 (< 1.32.0+1.33.0-cvs20050727-99) but it is not installable
          Depends: libboost-thread1.33.0 (>= 1.32.0+1.33.0-cvs20050727-0) but it is not installable
          Depends: libglibmm-2.4-1c2 (>= 2.8.0) but it is not installable
          Depends: libsigc++-2.0-0c2 (>= 2.0.2) but it is not installable
          Depends: libxml++2.6c2 but it is not installable
E: Broken packages
I'm on Dapper..
Tried installing libboost-dev and libboost-thread-1.33
Won't help.

---

### Post by Belsebub on 2006-05-27
installing splashy went sweet...
even sweeter now when i made my own kubuntu theme ;)

It's based on someone elses background so I might post it if I get permission from the author first.

---

### Post by PYR on 2006-10-18
> **Goshawk said:**
> Upower is a fork of Splashy. When some developers started to translate the c++ code to c in splashy i did not agree with them. I was the main developer of Splashy, in fact Splashy 0.1 was released by me.
Now Splashy is going to change itself and going to be like usplash. In the meantime upower is going to be developed in a new way.
Upower is 100% usermode (Splashy and Usplash depends from an initramfs image, try to change the kernel and if you don't put the initramfs image they will not work).
Upower is lite: it was the first bootsplash that supports changable themes via an apt-get way. apt-get install upower-theme-themename will install the new theme without the need to configure any file.
Upower uses xml file configurations.

Even if there is one active developer, upower is in development...

for info: [www.nanofreesoft.org](www.nanofreesoft.org)

advertising your program is cool and all but you don't need to edit any config file to change a splashy theme

just download the theme tarball and to install it type "sudo splashy_config -i path_to_theme/theme.tar.gz"

and you can easily see which themes are installed by typing "splashy_config --info" and choose the one you want by typing "sudo splashy_config -s theme_name"

so uwhatever might be lite and new and shiney but how many different boot splash programs do we really need? it's like saying you made a new grub, it doesnt matter it's there for one purpose.

---

### Post by hz1840821 on 2007-01-21
I'm running the 6.06 and I got some problem too.
The booting down works fine, but when booting up I get the ubuntu splash until the root fs is loaded, then it switches to my splashy background and after a while it turn on the error background. Even here there is an error: the verbose mode is not shown as it could be, but just the first 2 or 3 lettere appears on the upper left edge of my screen.
Hints?

FRANCO

---

### Post by weedenbc on 2007-07-26
Hi all.  I am trying to get splashy to work on a new Fiesty install and having some problems.  I downloaded the latest package from Synaptic and installed it.  I then downloaded the fingerprint theme and copied the xml file from /etc/splashy/themes/fingerprint to /etc/splashy.

When I reboot, I still see the same old Ubuntu boot screen.  Did I miss a step somewhere?

---

### Post by saz on 2007-10-12
hey installed splashy, everything okay, but when i boot the system i get no image, only the text of the system being booted... the letters are smaller though (due to vga=792)..

---

### Post by Korhal on 2007-10-18
I have to agree with saz I have the same problem and after experimenting with Splashy for about a week my complete Boot Splash was so f***ed up that I had to reinstall. I have about 2 years experience with slackware and with slackware I got those programs to work. So far I have not been able to get them to work under Ubuntu. I'm using Feisty Fawn 7.04. Is there any special way to install Splashy or Upower so that I can finally use my own boot splash. I have been working on it for almost a year now and am getting pretty tired of it.

---

### Post by ingo on 2007-11-22
I'm on Kubuntu 7.10 and installing splashy was a breeze.

Getting it to work appears to be a different kettle of fish though...

I now get verbose mode on boot, no splash at all. It says that sed cannot read the /etc/inittab - which makes sense 'cos it ain't there. 

Anybody out there with an idea?

---

### Post by ingo on 2007-11-23
OK, did some more work on this and I now get my theme appearing on turning the box off but the default one flickering at me for a short while before tux is replaced by the orange progress bar (on an otherwise black background).

I added vga=792 quiet splash to my menu.lst, did the whole rigmarole with the initramfs update and am now at my wits' end.

One possibility could be that I am trying to set up an autonomous system (new OEM) in a multi-linux environment, i.e. I just copied the contents of this system's /etc/boot (bar the grub folder) to my existing /boot partition... 

My head is spinning, I'd better take a break!

---

### Post by NobleCommerce on 2008-01-14
I just found out about splashy... where can I track its development and integration into ubuntu... 

How well do splashy and the proposed slickboot play together?

Edit: Yay! I found it!
The topic for #splashy is: Latest: 0.3.8 | Everyone asleep or clueless? [email]splashy-users@lists.alioth.debian.org[/email] | Website: [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) | Devel: [http://splashy.alioth.debian.org/wiki/developers](http://splashy.alioth.debian.org/wiki/developers) | Contrib Themes: [http://splashy.alioth.debian.org/themes/](http://splashy.alioth.debian.org/themes/) | Splashy now superseds bootsplash(.org)

---

### Post by m1r0 on 2008-05-18
hello,

8.04 amd64 , installed splashy succesfully and changed theme in settings in config.xml to "mycustomtheme".

in themes folder there are two themes "default" and "mycustomtheme".
i chage all options in /etc/splashy/config.xml to "mycustomtheme" and only what i get is logout splashy screen. 

when PC boots it keep returning to default theme , even i replaced original pictures in default theme folder and changed path in config.xml.
all images i use are 1204x768 png.

any solution to this problem ?

best regards

m1r0

---

### Post by ingo on 2008-05-23
did you do a sudo update-initramfs?

---

### Post by pwt on 2008-07-03
Hello,

I just tried splashy and have a question.

If I set vga=791 on the kernel line in /boot/grub/menu.lst, the text consoles (ctrl+alt+Fn) become basically unusable : font is much too small and also extremely dimmed.

Is that intrinsic to splashy because of its usage of directfb or is there something to add to boot scripts to restore a more decent font appearance?

Thanks in advance

---

### Post by kwame on 2008-07-08
Using a VGA code of 791 sets your framebuffer to 1024x768 pixels at 64K colors. If you want something easier on the eye, you can use **785** (640x480px@ 64K colors) or **788** (800x600pixels@ 64K colors). There is a table in the [first post]("http://ubuntuforums.org/showthread.php?t=41709") of this thread with more VGA codes.

> **pwt said:**
> Hello,

I just tried splashy and have a question.

If I set vga=791 on the kernel line in /boot/grub/menu.lst, the text consoles (ctrl+alt+Fn) become basically unusable : font is much too small and also extremely dimmed.

Is that intrinsic to splashy because of its usage of directfb or is there something to add to boot scripts to restore a more decent font appearance?

Thanks in advance

---

### Post by realdarktempler on 2008-10-31
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions)

---

### Post by n_techo on 2008-11-18
I have installed splasy with the command:

 sudo apt-get install splasy

then I had to edit /boot/grub/menu.lst

and add the text "vga=791" or "vga=792" the the text string:

kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3bb7d033-3066-4685-8d56-6c7f791f0b7c ro quiet splash

So after I added:

kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3bb7d033-3066-4685-8d56-6c7f791f0b7c ro quiet splash vga=791

And that worked great, but the progress bar only goes half way, before the kde gui loads up.

Anyone know how I can fix this?

I want the progress bar to reach the end before KDE loads up.

---

### Post by schmidtbag on 2008-12-06
i actually like having verbose mode, does anybody know how to make it always show up?  for some reason telling the text box to always show up doesn't do anything.  i made my own boot image and i left a space for verbose text.  also, how do i get verbose mode to say more stuff?  it tells me practically nothing and since i'm working on new stuff it doesn't show enough info

---

### Post by archeryguru2000 on 2009-02-11
I've been having a bit of trouble getting around my nVidia driver with this (at least I believe that's where my problem is).  Upon booting I am greeted with a 
```

mknod: /dev/fb0
spalshy_start_splashy(). Error-3

```
message.  However, it continues into the splash screen, but flickers abit and does not print any verbose messages (as it should).  My FB drivers are as listed below:
```

...kernel/drivers/video/arcfb.ko
...kernel/drivers/video/arkfb.ko
...kernel/drivers/video/aty/aty128fb.ko
...kernel/drivers/video/aty/atyfb.ko
...kernel/drivers/video/aty/radeonfb.ko
...kernel/drivers/video/cirrusfb.ko
...kernel/drivers/video/cyber2000fb.ko
...kernel/drivers/video/cyblafb.ko
...kernel/drivers/video/geode/gx1fb.ko
...kernel/drivers/video/geode/gxfb.ko
...kernel/drivers/video/geode/lxfb.ko
...kernel/drivers/video/hecubafb.ko
...kernel/drivers/video/hgafb.ko
...kernel/drivers/video/i810/i810fb.ko
...kernel/drivers/video/intelfb/intelfb.ko
...kernel/drivers/video/kyro/kyrofb.ko
...kernel/drivers/video/matrox/i2c-matroxfb.ko
...kernel/drivers/video/neofb.ko
...kernel/drivers/video/nvidia/nvidiafb.ko
...kernel/drivers/video/pm2fb.ko
...kernel/drivers/video/pm3fb.ko
...kernel/drivers/video/riva/rivafb.ko
...kernel/drivers/video/s1d13xxxfb.ko
...kernel/drivers/video/s3fb.ko
...kernel/drivers/video/savage/savagefb.ko
...kernel/drivers/video/sis/sisfb.ko
...kernel/drivers/video/sm501fb.ko
...kernel/drivers/video/sstfb.ko
...kernel/drivers/video/tdfxfb.ko
...kernel/drivers/video/tridentfb.ko
...kernel/drivers/video/uvesafb.ko
...kernel/drivers/video/vermilion/vmlfb.ko
...kernel/drivers/video/vesafb.ko
...kernel/drivers/video/vga16fb.ko
...kernel/drivers/video/vt8623fb.ko

```
I currently have my /boot/grub/menu.lst file written with the following;
```

kernel	/boot/vmlinuz-2.6.24-23-generic root=UUID=6168cda2-1b6b-4c0f-839f-18debe95877f ro quiet vesa=791 splash

```
Does anybody have any suggestions.  I will post any progress I make.  I plan to keep modifying my menu.lst file (i.e. vesa -> vesafb, 791 -> 792, etc.) until I get a better picture.

~~archery~~

---

### Post by archeryguru2000 on 2009-02-11
WOW!  I simply changed my command in menu.lst from:
```

vesa=791

```
to
```

vga=791

```
And PRESTO!  Works like a charm!

~~archery~~

---

### Post by RaveJunkie on 2009-06-05
does splashy work for x64 bit 9.04 ?

---

### Post by Korhal on 2009-06-06
@RaveJunkie:
Yes it does work for x64, I am running 64-bit. I haven't tested it specifically for 9.04 yet, but it works for 7.10, 8.04, 8.10. And probably 9.04

I got splashy working for quite some while now. first of all I install splashy

```

sudo apt-get install splashy splashy-themes

```

After that I create my boot splash from a picture or I set an existing one.

To create:
```
sudo splashy_config -c 
```

To set one (after creating one you will still need to set it):
```
sudo splashy_config -s <name of theme>
```

Now I need to add the vga=791 (791 = 1024x768, I use this for compatibility with older PCs, change as desired) to my grub. 

Open menu.lst:
```
sudo nano /boot/grub/menu.lst
```

Change:
```
kernel          /boot/vmlinuz-2.6.27-11-generic root=/dev/sdc1 ro quiet splash
```

To:
```
kernel          /boot/vmlinuz-2.6.27-11-generic root=/dev/sdc1 ro quiet vga=791 splash

```

Now the most important before we reboot. Let's update our initramfs to hold our image so Splashy will work.

Update initramfs:
```
sudo update-initramfs -k `uname -r` -u
```

After 1 or 2 reboots Splashy should work, it did for me. I hope this helps.

---

### Post by RaveJunkie on 2009-06-11
Yes Korhal  thank you


took a little editing, but that was cause i didnt remove usplash but its working good now.  thanks

:p

---

### Post by 565Customz on 2009-11-02
any update for karmic?

---

### Post by stevedes on 2010-03-03
Apparently, karmic uses grub2.....which does not have any menu.lst, only grub.cfg.
Even I have been looking for ways to configure splashy on karmic but all the guides use menu.lst.

---

### Post by satish0muktha on 2010-04-23
> **infinito said:**
> This howto will allow you to get a bootup image with progress bar, like the livecd does.
In this post i'm using my self-made theme. You can make your own or download another, it's up to you!

Splashy for Ubuntu

(1) Download latest splashy package from: [http://alioth.debian.org/projects/splashy/](http://alioth.debian.org/projects/splashy/) 

(2) Install the splashy .deb:
```
$ sudo dpkg -i splashy_0.1.3.svn.2_i386.deb
```(3) Edit /boot/grub/menu.lst to add vga=792 (1024x768 millions colors) or vga=791 (1024x768 thousands colors) to your default boot option.
For example:```
title        Ubuntu, kernel 2.6.10-5-k7 Default 
root        (hd0,0)
kernel        /vmlinuz root=/dev/hde6 ro quiet splash vga=792
initrd        /initrd.img
savedefault
boot
```See codes table below:

(4) Download my Ubuntu splashy theme from: [http://infinito.f2o.org/downloads/ubuntu_splashy_theme.tar.gz](http://infinito.f2o.org/downloads/ubuntu_splashy_theme.tar.gz)

You can get more themes from: [http://splashy.alioth.debian.org/themes/](http://splashy.alioth.debian.org/themes/)

(5) Untar ubuntu theme:
```
$ tar xzf ubuntu_splashy_theme.tar.gz
```(6) Copy files to splashy dir:
```
$ sudo cp -a ubuntu/ /etc/splashy/themes
```(7) Edit splashy config file:
```
$ sudo mv /etc/splashy/config.xml /etc/splashy/config.xml.old
$ sudo mv /etc/splashy/themes/ubuntu/config.xml /etc/splashy
```That's all! Next time you reboot your computer you'll see splashy in action!

Links of interest:
[http://nanofreesoft.org/index.php/Splashy](http://nanofreesoft.org/index.php/Splashy)
[http://nanofreesoft.org/index.php/Upower](http://nanofreesoft.org/index.php/Upower)

VGA Codes Table:```

                640x480    800x600    1024x768       1280x1024
256 colors        768        771         773            775
32K colors        784        787         790            793
64K colors        785        788         791            794
16M colors        786        789         792            795
```


I cannot find /etc/splashy/themes/debiansquirrel/config.xml  file. Only .xml file in /etc/splashy/themes/debiansquirrel/   folder is theme.xml .  Wt to do..Pls help

---

### Post by thahir1986 on 2010-06-23
i am using hardy heron with lxde.
i only get the blank screeen...not works! Is it i try different for lxde?

---

