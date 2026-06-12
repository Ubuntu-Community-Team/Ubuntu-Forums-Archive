---
title: "HOWTO: Grub splash images."
date: 2005-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Eproxus on 2005-04-28
**Introduction**
This guide will tell you how to get a nice background image while in Grub. The guide will first explain how to load an image into Grub and use it as a background and then, for those of you who are interested, how to create such an image in Gimp.

**[color=RED]Beware![/color] **Do only do this if you feel that you know what you're doing! It may mess up your boot loading if you are careless. (Thanks to jonny for pointing this out, together with backing up). That said, it shouldn't be too hard to follow this anyway.

[b]Table of Contents
[/b][i]Example Image
Configuring Grub[/i]


[list=1]
[*]*Adding an image*
[*]*Editing the grub configuration*
[*]*Seeing your results*
[*][i]Troubleshooting
    [/i]
[/list][i]Making your own splash image
[/i]
[list=1]
[*]*New file*
[*]*Create the art*
[*]*Reduce colors*
[*]*Save and compress*
[/list][i]Conclusion
Links

[/i]**Example Image**
 I have attached the splash image I'm using (and a thumbnail of it). We will be using this in the guide but you can use any image you want (assuming it is in the boot splash format, see *Making your own splash image* below). More images can be found in the *Links* section.

Get the splash image [here]("http://ubuntuforums.org/attachment.php?attachmentid=964&stc=1").

[b]Configuring Grub
*1.* Adding an image[/b]
First, move the image to the grub folder (assuming the current dir is your home folder and this is were you downloaded the image).
 ```
sudo mkdir /boot/grub/images
sudo mv usplash.xpm.gz /boot/grub/images
```
[b][i]2. Editing the Grub configuration
[/i][/b]Backup!
 ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
``` 
Then open the grub config file *menu.lst*:
```
sudo gedit /boot/grub/menu.lst
``` 
Locate a appropriate place to add the image, find the following (row 24 or therabout):
 ```
# Pretty colours
#color cyan/blue white/blue
```
And add a new section below the above lines:
 ```
## Splash image!
splashimage (hdX,Y)/boot/grub/images/usplash.xpm.gz
```
[color=black][color=RED]Important![/color] You MUST replace X and Y with the proper numbers. Grub's configuration syntax is a bit weird because it does not have the same offset as the usual mount for example. X in this case is the actual disk drive and Y is the partition. Assuming you have a pretty standard installation of Ubuntu you could find this information further down in *menu.lst*. Locate the section which matches the entry you normally boot from:
[/color] ```
## ## End Default Options ##
 
title		Ubuntu, kernel 2.?.??-?-??
root		(hd[color=BLUE]X,Y[/color])
```
There you can find the proper numbers to use for your splashimage command.
Enter those in the line added before. Save the file.
[color=RED]Important2![/color] If you have a separate boot partition you have to remove the */boot *in the path, this is because the root of the boot partition is mounted in /boot on your other partition. Resulting in this section instead:
 ```
  ## Splash image! (On separate partition)
splashimage (hdX,Y)/grub/images/usplash.xpm.gz
``` 
[i][b]3. Seeing your results
[/b][/i]Reboot and your splash image should be visible as the Grub background.
[i][b]4. Troubleshooting
[/b][/i]If the image somehow does not load Grub will behave weird, although if you have a timeout (Ubuntu has by default) Grub should boot Ubuntu anyway. Then you should be able to correct the problem. More information and tips & tricks available [here]("http://ruslug.rutgers.edu/%7Emcgrof/grub-images/").
 
[b]Making your own splash image
[/b]Here's how you make your own image, I will not tell you how to use the Gimp as there are plenty of other tutorials on that, use google. ;)
[i][b]1. New file
[/b][/i]There are some restrictions on the image, it must be 640x480 pixels large and only contain 14 colors.
[i][b]2. Create the art
[/b][/i]Uh, use your artistic talents and produce wicked art! If you want a photo or something just past it in and resize it. If you want to do something Ubuntu specific [this page]("http://www.ubuntulinux.org/wiki/UbuntuArtwork") might be of interest. If you want to use the Ubuntu logo in SVG format (vector graphics) there is a Gimp SVG plugin available in apt-get.[i][b]
3. Reduce colors
[/b][/i]The next step is to reduce the amount of colors to 14. Go Image->Mode->Indexed... and select *Generate optimum palette*, set the maximum number of colors to 14 and chose a dithering algorithm that looks good. Normal gives the most coherent colored areas but the Floyd-Steinberg algorithms are more appropriate for images with many colors.
[i][b]4. Save and compress
[/b][/i]Save the image as an XPM image. You might want to save a Gimp image also (XCF) in case you want to change it. Then compress it with gzip and copy it to the Grub folder:
 ```
gzip image.xpm
sudo cp image.xpm.gz /boot/grub/images
```
 
[b]Conclusion
[/b]You should now have a nice background in Grub, and perhaps even your own creation! \\:D/
[b]
Links[/b]
[Grub Splash Image Documentation]("http://ruslug.rutgers.edu/%7Emcgrof/grub-images/")
[Ubuntu Artwork Resources]("http://www.ubuntulinux.org/wiki/UbuntuArtwork")
[Additional Ubuntu Splash Screens]("http://sleepybuddha.sl.funpic.de/ubuntu/")

Comments and suggestions welcome!


 EDIT: Backing up and precautions added. Thanks jonny.
EDIT2: Separate boot partitions handled. Thakns todw1fd.

---

### Post by bored2k on 2005-04-28
Nice. You could get some other nice grub images **[here](http://bored2k.cjb.net/)**

---

### Post by TravisNewman on 2005-04-28
That first attachment link is a dead link, just FYI

---

### Post by bored2k on 2005-04-28
[QUOTE=panickedthumb]That first attachment link is a dead link, just FYI[/QUOTE]
 usplash.xpm.tgz ? I just download it, its just 4k.

---

### Post by TravisNewman on 2005-04-28
[QUOTE=bored2k]usplash.xpm.tgz ? I just download it, its just 4k.[/QUOTE]
 No the first link. The second one gave usplash.xpm.tgz. He's edited the dead link ;)

---

### Post by donar73 on 2005-04-28
Thx alot, nice HowTo!  :)

---

### Post by jonny on 2005-04-28
Good how-to and very clear.  A boot splash certainly adds a bit of a feel good factor when you start up your PC, and I have one myself.  All punters should be aware, though, that you can render your system unbootable by being careless with /boot/grub/menu.lst

Things are always recoverable, as you can use your Hoary CD to boot and repair the damaged system.  I suggest taking a backup ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```first, as recovery is much simpler with a working file to refer to.

Basically, though, if you don't feel comfortable rescuing a system with a broken boot sector, you're not ready for this how to.

---

### Post by Eproxus on 2005-04-28
[QUOTE=jonny]Good how-to and very clear. A boot splash certainly adds a bit of a feel good factor when you start up your PC, and I have one myself. All punters should be aware, though, that you can render your system unbootable by being careless with /boot/grub/menu.lst

Things are always recoverable, as you can use your Hoary CD to boot and repair the damaged system. I suggest taking a backup ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```first, as recovery is much simpler with a working file to refer to.

Basically, though, if you don't feel comfortable rescuing a system with a broken boot sector, you're not ready for this how to.[/QUOTE]

Thanks for pointing this out! Added it to the guide.

---

### Post by Get on 2005-04-28
Hmm, I only get stripes on the screen :(

---

### Post by kuleali on 2005-04-28
nice

---

### Post by todw1fd on 2005-04-28
Suggested edit for those that have a separate /boot partition.  In the instructions where it says:

```
## Splash image!
splashimage (hdX,Y)/boot/grub/images/usplash.xpm.gz
```

Since the root of the boot is already /boot, the relative path would be (hdX,Y)/grub/images/usplash.xpm.gz, so the code should look like this.

```
## Splash image!
splashimage (hdX,Y)/grub/images/usplash.xpm.gz
```

For those of you that had copied word for word like me and ended up with a garbled screen...

Cheers

---

### Post by Eproxus on 2005-04-28
[QUOTE=todw1fd]For those of you that had copied word for word like me and ended up with a garbled screen...[/QUOTE]

Sorry about that! :roll:

This is now added to the guide. Thanks a lot for pointing that out! I've never done a clean Ubuntu install on a disk, I always partitioned it myself as I have multiboot. Does Ubuntu create a separate boot partition by default?

[QUOTE=Get]Hmm, I only get stripes on the screen :([/QUOTE]
Stripes as in weird ASCII characters or as in weird bitmap?

You may have selected the wrong device to load the image from. If you know what disk it is in for example fstab you have to exchange hda for hd0, hdb for hd1 etc and partition 1 for partition 0. Grub has a -1 offset compared to the usual way.

---

### Post by thechitowncubs on 2005-04-28
It didn't work for me either...

I just got a loading grub with a weird background in the upper left corner of my screen.

---

### Post by Eproxus on 2005-04-29
[QUOTE=thechitowncubs]It didn't work for me either...

I just got a loading grub with a weird background in the upper left corner of my screen.[/QUOTE]
 How are your disks partitioned? What does your /boot/grub/menu.lst and /etc/fstab look like?

---

### Post by seven on 2005-04-29
I have been using this splash for a few monthes -  they rock :)
great guide btw.

---

### Post by Get on 2005-04-29
I used "hd(0,0)/boot/...." but hd(0,0) is boot  ](*,) 
But now is it sloved  :)

---

### Post by GTvulse on 2005-05-31
Nice how-to, but a bit more complicated than necessary :-)

Debian-based distros have a little utiity script called "update-grub" that will automagically detect and include any file called "splash.xpm.gz". The tip could go like this:

```

bash-$ sudo cp usplash.xpm.gz /boot/grub

bash-$ cd /boot/grub

bash-$ sudo ln -s usplash.xpm.gz splash.xpm.gz

bash-$ sudo update-grub

```

Why use a symbolic link? I have several splashscreens and change them whenever I feel like it. BTW, here is a small project for someone with determination: writing a small script that rotates through an splashscreen collection. Hint: use dash, and the @reboot feature of Vixie's cron, see crontab(5) for details ...  :-)

On the other hand, if you don't have "update-grub" in your system, you need to do it by hand.

---

### Post by duff on 2005-05-31
<shamless-plug>
 Or you could use this nice front end for adding splash images or selection menu colors:   [http://www.gnomefiles.org/app.php?soft_id=795](http://www.gnomefiles.org/app.php?soft_id=795)
</shameless-plug>

---

### Post by Eproxus on 2005-06-01
Great info! This I had no knowledge off, obviously. :-)

---

### Post by pdk001 on 2005-06-01
thanks for tip, it's work fine

---

### Post by AnGeLiX on 2005-06-01
You can do this without editing manually the files with grubconf.

#sudo apt-get install grubconf

---

### Post by TheChaos0 on 2005-06-03
Is it possible to change the font in the splash screen? Size, colour, etc?

---

### Post by bored2k on 2005-06-03
[QUOTE=TheChaos0]Is it possible to change the font in the splash screen? Size, colour, etc?[/QUOTE]
 For colors you would need grime [http://grime.sourceforge.net/#screenshots](http://grime.sourceforge.net/#screenshots)

---

### Post by picpak on 2005-06-24
The image shows for half a second (with a black background) and then disappears...

Please help :-(

---

### Post by transport on 2005-06-24
How to I can change the color in grub?
uncoment this:
##Pretty colours
##color cyan/blue white/blue

to:
##Pretty colours
color cyan/blue white/blue

doesnt work fine

splashimage works fine, it si nice.

---

### Post by Eproxus on 2005-06-25
[QUOTE=picpak]The image shows for half a second (with a black background) and then disappears...

Please help :-([/QUOTE]

Is the text still there?

---

### Post by picpak on 2005-06-25
Yes...but the background is black, and then it all disappears...

---

### Post by brian g on 2005-07-26
i can't get this to work.
i tried /boot and i got a tiny image in the top left corner
i tried without /boot and i got weird ASCII all over while it was going through the boot process

---

### Post by Eproxus on 2005-07-27
[QUOTE=brian g]i can't get this to work.
i tried /boot and i got a tiny image in the top left corner
i tried without /boot and i got weird ASCII all over while it was going through the boot process[/QUOTE]
 Did you try with a used image that you know is working?

Please post your grubconf and the image you are using.

---

### Post by brian g on 2005-07-27
[QUOTE=Eproxus]Did you try with a used image that you know is working?

Please post your grubconf and the image you are using.[/QUOTE]i used your usplash as well as one i made myself. both had same results.

menu.lst..
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## Splash image!
splashimage (hd0,0)/boot/grub/images/tux.xpm.gz

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
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by brian g on 2005-07-27
well.. i installed grubconf since my last post.
i unchecked hidden menu and rebooted.
i saw the image for a second +/- with what appeared to be a menu over the top of it.
then it went on to loading the kernal and such normaly with the text scrolling by and whatnot.
is that all this is supposed to do?
I thought it might be more like windows where it shows an image untill the shell loads.

edit-[thank you for the help. after reading the grubconf manual i understand everything much better.]

---

### Post by Tiede on 2005-08-12
[QUOTE=brian g]well.. i installed grubconf since my last post.
i unchecked hidden menu and rebooted.
i saw the image for a second +/- with what appeared to be a menu over the top of it.
then it went on to loading the kernal and such normaly with the text scrolling by and whatnot.
is that all this is supposed to do?
I thought it might be more like windows where it shows an image untill the shell loads.

edit-[thank you for the help. after reading the grubconf manual i understand everything much better.][/QUOTE]
 This is what hapenned to me to. It is in the upper left corner for ~0.5 seconds and then it goes right back to loading with tests scrolling down the screen... In my understanding, the splsh image is supposed to hide those messages and stay 'til GDM starts... Why is it not working that way?
I use a Intel Pentium II (Deschutes) computer... Is this relevant?

---

### Post by Cl1mh4224rd on 2005-08-13
The title should probably say "menu backgrounds" instead of "splash images". I have yet to try this, and I'm a Linux newbie, but if what I think is the case, then the former phrase is a bit more intuitive.

The important thing to remember is that this is just a background. As the OP says, *"This guide will tell you how to get a nice **background image while in Grub**."* Once you make a choice from the menu, GRUB's done, so no hiding of the initialization text.

---

### Post by brian g on 2005-08-23
[QUOTE=Tiede]This is what hapenned to me to. It is in the upper left corner for ~0.5 seconds and then it goes right back to loading with tests scrolling down the screen... In my understanding, the splsh image is supposed to hide those messages and stay 'til GDM starts... Why is it not working that way?
I use a Intel Pentium II (Deschutes) computer... Is this relevant?[/QUOTE]
i believe what we thought this was is what [splashy](http://ubuntuforums.org/showthread.php?t=41709) will do for us.

---

### Post by jerrykenny on 2005-08-27
If anyone gets black n white garbage with Grub splashimages,  . . . . . what worked for me was to gunzip the file (xpm or whatever) and tell grub to display the   splashimage.xpm    (instaead of splashimage.xpm.gz)

I know it shouldnt make any odds, but on my system it DOES !    so worth a try.

---

### Post by towsonu2003 on 2005-10-11
[QUOTE=bored2k]Nice. You could get some other nice grub images **[here](http://bored2k.cjb.net/)**[/QUOTE]

for windows users trying to switch to linux, the above link resulted in the following message from McAfee: 
Script executed by iexplore.exe
Exploit-MhtRedir.gen
Script execution blocked

---

### Post by jesseman on 2005-10-11
its how one goes about getting around those nasty popup blockers ... how sad :(

---

### Post by Aliby on 2005-12-19
The first time I installed Kubuntu Breezy I was rather taken by the Usplash screen. So I simply copied it and created what I call the Black-Crystal splash screen I use with Grub. 
(I tried moving the logo to the bottom of the screen to see if it looked better with the menu above? :rolleyes: )
It keeps the theme consistant with the rest of the loading process and I think it looks great ;) 
Get them here: 
[http://myweb.absa.co.za/avbaty/kubuntu_black-crystal.tar.gz](http://myweb.absa.co.za/avbaty/kubuntu_black-crystal.tar.gz)
[http://myweb.absa.co.za/avbaty/kubuntu_black-crystal0.tar.gz](http://myweb.absa.co.za/avbaty/kubuntu_black-crystal0.tar.gz)

---

### Post by Aliby on 2005-12-21
I have the same question?:confused: 
It seems so achieveable, but so far no progress!
Is it to do with default and specific settings?
Looking forward to some response

---

### Post by ronmarley1 on 2006-04-21
Nice HowTo!
Thanks

---

### Post by kolesarm on 2006-05-04
worked nicely for me! nice howto.

---

### Post by nolan- on 2006-05-09
Thanks for the howto, worked a treat!

I've just been looking in the repositories and there are now some packages containing splash images for you:-

grub-splashimages    
[COLOR="Red"]AND[/COLOR]
kubuntu-grub-splashimages

The only thing is that if you install them they create a different folder where the images are kept. 

So instead of this :-
```
## Splash image!
splashimage (hdX,Y)/boot/grub/images/usplash.xpm.gz
```

You must use this :-

```
## Splash image!
splashimage (hdX,Y)/boot/grub/splashimages/usplash.xpm.gz
```

Replacing the usplash.xpm.gz with whichever image you choose.

---

### Post by _bgh_ on 2006-05-12
Hello,

   Congrats on the great HowTo, it works like a charm!  I have, however, experienced  some strangeness that others might want to be aware of.

> 
And add a new section below the above lines:

```
## Splash image!
splashimage (hdX,Y)/boot/grub/images/usplash.xpm.gz
```


This *always* works assuming the file exists.  Out of curiosity, I tried

```
## Splash Image
splashimage (hdX,Y)/home/user/myimage.xpm.gz
```

and grub properly displayed my image and a menu.  So, I thought, "Great!  I can put my images wherever I want and grub will load them!"  I then placed my image in a different directory, for neatness, and changed my path in 'menu.lst' to

```
## Splash Image
splashimage (hdX,Y)/home/user/themes/splashscreens/grub/myimage.xpm.gz
```

and rebooted only to see a solid black screen with a useable grub menu.  Then I hit 'c' to go to the command line and typed

```
splashimage (hdX,Y)/home/user/themes/splashscreens/grub/myimage.xpm.gz
```

and grub loaded my image just fine.  My guess is that when grub reads 'menu.lst', the storage for the 'splashimage' value is fixed length and so can't handle long path names.

Moral:  You can put your images wherever you want, but if the image doesn't load then your pathname is probably too long.

Cheers.

---

### Post by eggmanpete on 2006-05-13
Worked well for me, although the low refresh rate on my CRT makes it look iffy.
Anyone have any links to grub splash images? Thanks

---

### Post by CrashOverKill on 2006-05-14
Went Flawless
Nice howto
here is the one I am using

---

### Post by lilmienboy on 2006-12-24
cheng@cheng-laptop:~$ sudo mkdir /boot/grub/images
mkdir: cannot create directory `/boot/grub/images': File exists
cheng@cheng-laptop:~$ sudo mv usplash.xpm.gz /boot/grub/images
mv: cannot stat `usplash.xpm.gz': No such file or directory

im a newbie, is there a reason why i can't move it over there. i downloaded the file into
my desktop.

---

### Post by Tiede on 2006-12-27
try this instead.
```
sudo mv ~/Desktop/name_of_downloanded_file.xpm.gz /boot/grub/images/

```
This should work. As you can see, the reason it didn't work before is because you were asking for a file from the wrong location. Your terminal's default location is your /home folder (represented by the tilde sign). You need to move to your Desktop folder first if you wish to use the command you did, which is what the ~/Desktop added to the command does.

---

### Post by tahsin on 2007-05-23
hello i want this file to be the grub image 
[http://www.kde-look.org/content/show.php/Kubuntu+7.04+Grub+Bootscreen?content=56843](http://www.kde-look.org/content/show.php/Kubuntu+7.04+Grub+Bootscreen?content=56843)
i have this file on my desktop (Filename:56843-kubuntu-grub.xpm.gz)
I typed :
sudo mkdir /boot/grub/images
on konsole and 

sudo mv 56843-kubuntu-grub..xpm.gz /boot/grub/images

and i get this:

tahsin@tahsin-desktop:~$ sudo mv 56843-kubuntu-grub..xpm.gz /boot/grub/images
mv: cannot stat `56843-kubuntu-grub..xpm.gz': No such file or directory
tahsin@tahsin-desktop:~$

Please help me out ....I'm a newbie so dont knw much.

---

### Post by Eproxus on 2007-05-23
> **tahsin said:**
> 
tahsin@tahsin-desktop:~$ sudo mv 56843-kubuntu-grub..xpm.gz /boot/grub/images
mv: cannot stat `56843-kubuntu-grub..xpm.gz': No such file or directory
tahsin@tahsin-desktop:~$

Please help me out ....I'm a newbie so dont knw much.

Looks like you're standing in your home folder at the moment (/home/tahsin). Your desktop is located in /home/tahsin/Desktop

To go there, type```
cd /home/tahsin/Desktop
```
Then your prompt will look like this (or similar):```
tahsin@tahsin-desktop:~/Desktop$
```

Then your commands will surely work and you will be able to move the image.

Some tips:
[LIST]
[*]Typing only 'cd' will always take you back to your home directory (/home/tahsin)
[*]You can also type 'sudo mv Desktop/your.image.xpm.gz' to move the image
[*]You can type 'pwd' to see which directory you're currently standing in
[/LIST]

Hope this helps!

---

### Post by tahsin on 2007-05-25
yup thanks ! i got it working eventually

---

### Post by vaishnavi on 2007-10-20
worked like a charm. Going through all the posts helped me in making the splash image work in a jiffy

---

### Post by Drewbkilla on 2008-01-14
Are all of these mentioned commands the same when using Gutsy?

Not too familiar with the term grub.

Just got all of my effects running perfectly so now looking for the additional tweaks and goodness!

:)

---

### Post by Eproxus on 2008-01-15
> **Drewbkilla said:**
> Are all of these mentioned commands the same when using Gutsy?
They should be, I don`t think much has changed in the way GRUB does things. However I cannot promise anything since it was a long time I used it.

> **Drewbkilla said:**
> Not too familiar with the term grub.
GRUB is the boot loader you get when you install Ubuntu. Essentially it is the first program that is executed on your computer (except all the BIOS stuff). This little program lets you choose which other program you want to execute (such as Ubuntu or Windows) and it comes with a nice menu and some customization options.

---

### Post by shane2peru on 2008-03-14
Thanks for th e nice how to!  It works for me, however the screen resolution is horrible.  Does anyone know how to increase the screen resolution?  I tried to make the image 1024x768 and wow, that was a disaster.  I know from using others in the past, that it can look really sharp like on Mepis, and I think Fedora too has a very sharp looking grub splash screen.  How can I make the image look sharper?

Shane

---

### Post by Eproxus on 2008-03-15
It is not possible to change the resolution of GRUB, since it is used so early in the boot process it doesn't have any advanced graphics. It has to compatible to most hardware.

---

### Post by shane2peru on 2008-03-16
Why is it that Mepis and Fedora have such nice looking grub menu screens?  I think those are the two that have the nicest looking grub menu screens and it comes setup that way.  Their's certainly look better than mine does.  Is there something else they change to make it look so nice?

Shane

**EDIT**  Here is Fedoras screen shot:  [http://fedoraproject.org/wiki/Tours/Fedora7/011_Grub_Menu?action=AttachFile&do=get&target=011_Grub_Menu.png](http://fedoraproject.org/wiki/Tours/Fedora7/011_Grub_Menu?action=AttachFile&do=get&target=011_Grub_Menu.png)   I couldn't find one of Mepis, but I remember it being nice too.

---

### Post by Eproxus on 2008-03-17
No, it's just another image. They've not changed anything else.

---

### Post by Poizhan on 2008-03-17
Very nice thank you, also I suggest commenting out "hiddenmenu" and changing the "timeout" value from 3 to something like 15, so you have the chance to enjoy your new splash :KS

---

### Post by Huss on 2008-03-27
Nice one, giving it a try now.

---

### Post by Huss on 2008-03-28
Got it. 

I needed to reduce mine to 640x480 and 14 colours before it would work. 

I also used start-up manager to load the image into the grub folder. It was nice and quick, but needed a bit of tweeking. start-up manager resets most of the settings in your grub. In my case, I have mapping errors with default grub settings. For GRUB to find the image I needed to make sure that it was referred to (0,0) rather than the (1,0) that start-up defaulted to. 

Thanks for the tute

---

### Post by KingTermite on 2008-06-06
Found out how to do this through a book (Linux Desktop hacks) that I got from the library last night. Did a search and here's a thread on it. I thought this was cool and many people would like to do this, so......


[IMG]http://www.ci.oswego.or.us/plan/Images/Bump.jpg[/IMG]

---

### Post by sankz on 2008-07-20
The easiest tutorial lies here...
[http://fasterthanlight.wordpress.com/2008/07/18/beef-up-your-grub-loader/](http://fasterthanlight.wordpress.com/2008/07/18/beef-up-your-grub-loader/)
and here:
[http://fasterthanlight.wordpress.com/2008/07/20/create-your-own-grub-splash-image/](http://fasterthanlight.wordpress.com/2008/07/20/create-your-own-grub-splash-image/)

---

### Post by Piraja on 2008-09-26
[COLOR="Blue"]**If you wish, you can use exclusively graphical tools in Ubuntu.**[/COLOR] Open or create your own image in **GIMP**, scale it to 640X480 ([COLOR="SeaGreen"]Image > Scale image...[/COLOR]), convert the image to indexed mode and set maximum number of colours to 14 ([COLOR="SeaGreen"]Image > Mode > Indexed... > Generate optimum palette > Maximum number of colours: 14[/COLOR]), save the image with the **.xpm** file extension ([COLOR="SeaGreen"]File > Save As... > [/COLOR]change file extension from xcf or whatever to xpm).

Then open the relevant folder in **Nautilus**, right-click on your new image.xpm file, choose Create archive... and **.gz** as the archive extension. Now you have made an archive file that Grub can use: name-of-your-image.xpm.gz. The image *must* be 640X480, indexed with 14 colours max, and archived in this .xpm.gz format. 

Use **Alt+F2 > gksudo nautilus** in order to create the sub-folder called splashimages in /boot/grub, if it does not exist already. Copy your-image.xpm.gz and paste it into the new folder.

You can use an application called **Startup Manager** to update the menu.lst file. It automatically creates a backup of the original menu.lst, so it is [COLOR="Red"]relatively[/COLOR] safe to play around with it. Install Startup Manager (you can find it and some other options by typing "grub" in the "Search" box of Add/Remove Applications, or you can just type "sudo apt-get install startupmanager" in the Terminal). After installation, you can find it under [COLOR="SeaGreen"]System > Administration[/COLOR].

Now when you launch Startup Manager you can open the Appearance tab, check the "[COLOR="SeaGreen"]Use background image for bootloader menu[/COLOR]" box. In order to add your brand new splash image, choose [COLOR="SeaGreen"]Manage Bootloader themes...[/COLOR], press [COLOR="SeaGreen"]Add[/COLOR] and choose your file in the /boot/grub/splashimages folder. Close the window. In the [COLOR="SeaGreen"]Startup Manager > Appearances[/COLOR] window, the name of your new splash image file should now appear in the drop-down menu box on the right. 

You can close the application now and reboot to see your new Grub splash image in the background when the Grub bootloader screen comes up. In case you have a hidden menu, you must probably press the Esc key to see the bootloader menu. In Startup Manager, you can check [COLOR="SeaGreen"]Boot options > Show bootloader menu[/COLOR] if you want it to be shown without having to press Esc at startup.

Below is an example, a Grub splash image I created for my Intrepid Ibex installation. The sample image is a PNG file, so if you want to use the image or modify it for your own taste, the steps above must be applied. But you can also download the attachment below and save it in your /boot/grub/splashimages folder. The original source photo is by [Ian Spare]("http://snowslider.net/2008/06/05/zinal-cabane-du-petit-mountet-2/") and used by his permission.

[[IMG]http://www.aijaa.com/img/t/00556/2799086.t.png[/IMG]](http://www.aijaa.com/v.php?i=2799086.png)

It might be a good idea to launch Startup Manager from the terminal ([COLOR="Red"]gksudo startupmanager[/COLOR]), because you can read a "live report" of what the application does while it's running.

Below's the actual ibex-splash.xpm.gz file. You can download it to a folder of your choice and copy it to your /boot/grub/splashimages folder and it should work if you follow the instructions above.

---

### Post by SamSlater on 2008-11-01
[FONT="Fixedsys"]imagesplash (x,y)/boot/grub/images/splashimage.xpm.gz[/FONT]

didn't work for me. And yes, I had the image in the right folder, and my disk & partition numbers were correct.

After a little playing around I found:

[FONT="Fixedsys"]imagesplash=/boot/grub/images/splashimage.xpm.gz[/FONT]

was the only command that worked. I'm on Hardy, duel booting with XP and have my /, /home, and /swap as logical partitions in one extended partition.

---

### Post by Piraja on 2008-11-09
Here's another Grub splash image for Intrepid Ibex. The original photo of a Nubian ibex that I gimped for this one is by [David Eppstein]("http://www.ics.uci.edu/~eppstein/pix/lazoo/Ibex-m.jpg").

NB: In the sample JPG image the logo is slightly too low, but the placement has been fixed in the actual indexed XPM image (.xpm.gz).

ADDITION, Nov. 26, 2008: See also my [Splashy themes etc.]("http://ubuntuforums.org/showthread.php?t=991784") thread.

---

### Post by Piraja on 2008-11-24
I made yet another one... This is GIMPed from a gorgeous source photo titled "Blue Grub", by Wetwater ([Creative Commons]("http://search.creativecommons.org/?q=blue_grub&sourceid=Mozilla-search")).

---

### Post by Herman on 2008-12-08
:) Piraja,
Thank you for ibex-splash.xpm.gz , I really like that one!
I used 'foreground' and 'background' commands with mine to set the colors of the text and the selection bar.
I have 'gold' for the foreground color and 'dark goldenrod' for the background of my text in the menu.
```
splashimage (hdx,y)/boot/grub/ibex-splash.xpm.gz
foreground ffd700
background b8860b
```The color codes in HTML notation come from any 256 color chart you can find on the web.

Thanks again for the nice splashimages, especially ibex-splash.xpm.gz, nice work!

Regards, Herman :)

---

### Post by Piraja on 2008-12-08
Thanks, Herman,

especially for the nice colour tips &#8212; they make a beautiful match.
I decided to add a couple of examples.

My suggestions for the "moon" text colours are picked from the image itself:

```
splashimage (hd<x,y>)/boot/grub/moon.xpm.gz
foreground f8f3ce
background bdac7d
```

All of the source images are found over the internet and they are licensed under Creative Commons. Credits for the source photos: On the left: "Silent Night" by [Aim and shoot]("http://flickr.com/photos/gtstuff/2063351514/"). In the middle: [Dave Massey]("http://www.3dtexture.net/img-golden-sunlight-water-ripples-reflection-texture-254.htm"). On the right: Also this one is titled "Silent night" (figure out how that happened!), by [*Ijon]("http://flickr.com/photos/gtstuff/2063351514/").

These are just examples, of course, in order to encourage you to make your own custom backgrounds. Feel free to download these, if you wish.

---

### Post by Umenzi on 2008-12-10
When I use a splash screen, the entire image is shifted to the left quite a bit. The menu items are still visible, but I can't see the left edge of the containing table.
Before this the table was centered and I could see everything.

How  might I solve this? By the way, I currently have to run Ubuntu in low-graphics mode, due to having an incompatible nvidia video card.

---

### Post by Piraja on 2008-12-10
> **Umenzi said:**
> When I use a splash screen, the entire image is shifted to the left quite a bit.
Have you tried the monitor's own adjustment knobs or buttons?
EDITION/ADDITION: I think the same kind of slide-to-the-left phenomenon happened to me when I tried Splashy instead of Usplash, and the simple solution was to use the monitor's own adjustment buttons.

---

### Post by Herman on 2008-12-10
> The menu items are still visible, but I can't see the left edge of the containing table.
Before this the table was centered and I could see everything.:) I agree with Piraja, the first thing would probably be to try adjusting the monitor.

A second option you may be able to use is GRUB's '*viewport*' command.

GRUB's* viewport* command is for controlling the position and size of the rectangle that the text fits in, inside in the GRUB Menu.
The *viewport* command is useful if someone has have a nice splashimage but the table in the GRUB menu happens to be in the way of an important part of the picture.
We can use the *viewport* command to move the table around to some degree in order to improve the appearances and show our splashimage off to best effect. 
This command is only available in 'Graphics mode', (when we are using a splashimage command).

The syntax for *viewport* is the word *viewport* followed by four numbers, like this,
```
viewport  x0  y0  x1   y1
```Where: 
x0 is a number which sets the left-right positioning for the left side of the rectangle. 
In my tests the smallest number I could set for this parameter was [FONT=Bitstream Vera Sans Mono]0[/FONT] and the largest was 11,
y0 is a number which sets the up and down position for the rectangle. a zero  entered here makes the rectangle appear as close as possible to the top of the monitor.
The number 6 was the largest number I could get mine to accept, which made the rectangle lower.
x1 is a number which seems to be in the range from 66-80 and sets the width of the rectangle. 
y1 is a number which seems to be a number in the range between 16 and 30 in my computer and sets the height for the rectangle.

For some examples, in my computer I found that the following combinations worked, 

For a small rectangle in the upper left of the screen.
```
viewport 0 0 66 16 
```
To get the largest rectangle, and have it in the middle of the screen
```
viewport 3 3 80 30 
```
For a large rectangle in the lower right of the screen
```
viewport 11 6 80 30 
```
For a small table in the lower right I wasn't able to find any numbers that could do that, I don't know why not, it just wouldn't work for me. 

Your computer may accept different numbers than mine.
You can easily experiment with these commands at  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") (CLI)  while you are booting up.
Just press 'c' from your GRUB menu for a command line and use the *viewport* command to change the rectangle as you please, then press 'Esc' to go back to your GRUB menu to see how it looks. 
You can do that as many times as you like until you have a combination you are happy with.
Try out all the parameters until you get the *viewport* (table) where you like it and remember the combination of numbers you like best. 
After you boot up you can then add those numbers after your viewport command in your menu.lst file. 

:)

---

### Post by Piraja on 2008-12-11
Herman, that's great advice; at least I will try it!

---

### Post by Umenzi on 2008-12-12
Thanks, monitor adjustment was all it needed.

However, I am mystified by a new problem: When I use my custom splash screen, the image appears just fine, but the highlighting no longer shows up, and I have to count my keystrokes to select the right item.

---

### Post by Herman on 2008-12-12
:) Have you tried out the 'foreground' and 'background' commands I suggested in [post #67]("http://ubuntuforums.org/showpost.php?p=6329638&postcount=67")?
```
splashimage (hdx,y)/boot/grub/ibex-splash.xpm.gz
foreground ffd700
background b8860b
```
The six character html code after the '**foreground**' command sets the color of the main upper left faces of all letters and the big text rectangle that has all our operating system titles in it in our GRUB menu.

The html code after the '**background**' command sets the colors used in the hilite (selection) bar that we shift up or down with our arrow keys to select an operating system to boot and also the lower-right 'shadowing' for all the letters and the big rectangle around our operating system titles. 

Make sure your '**background**' is not the same color as your image or you will not be able to see it.

Here are two links with keys to the 256 color code, 
**[Web *colors* - Wikipedia, the free encyclopedia]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FWeb_colors&ei=nBpCSYvQBonOtQPgovWFBA&usg=AFQjCNFwgVHSZLt0AlztFXiK5a7nHvkJzQ&sig2=mlDGUuesmVvIoHsBV0yoWQ")**
  
[B][*HTML Color Codes*: Hex *Color* Charts, RGB and Decimal Charts and Tables]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=7&url=http%3A%2F%2Fwww.random411.com%2Fhtml-color-codes-chart-hex-number-palette-rgb-name-sheet%255Cindex.html&ei=nBpCSYvQBonOtQPgovWFBA&usg=AFQjCNHBRyr3xbOBJJPoH2oje1pcqvfdIQ&sig2=lApQ7xz-KrqLNuYeRKwSvg")

[/B]You can also use the color picker tool in GIMP or install 'gcolor2' or 'Agave' to help you find the colors and the corresponding HTML codes. I'm only guessing, maybe that's not what your problem is, but I hope I'm being of some help anyway. :)

---

### Post by Piraja on 2008-12-25
I scanned a cat drawn by my daughter. These are the settings I'm using with these two backgrounds — thanks to Herman for tips:

```
#A splash image for the menu
splashimage=/boot/grub/splashimages/kittengreen.xpm.gz
foreground ffd700
background b8860b

#Viewport
viewport 0 0 66 22

```

---

### Post by stepram on 2009-03-27
Thanks works a treat. 

Just a wee tip I figured out by mistake when editing grub.  If you remove the text in "Other Operating systems:" from title as shown below and leave it blank. Grub will hide the other systems names and descriptions until you navigate down to that section of the menu.  But very usefully when you use the down arrow to go to that section of the menu it will show these.  Good way of removing a Windows boot option from the menu, but retaining the option to use it, should you be forced to.

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           
root


StepRam.

---

### Post by Herman on 2009-03-28
:) Thanks for sharing your tip, stepram, I didn't know about that one! 
I'm glad you got your splashimage working the way you like too!

@ piraja, 
Thank you for sharing and you're welcome :)

---

### Post by yuli_capone on 2009-05-18
this was made by me after a few hours of searching how to change the splash

[[IMG]http://img140.imageshack.us/img140/4754/ubuntudiblack.th.jpg[/IMG]](http://img140.imageshack.us/my.php?image=ubuntudiblack.jpg)

[http://www.fileshare.ro/1148608899.24](http://www.fileshare.ro/1148608899.24)

---

### Post by xeroforhire on 2009-05-20
the "gedit" command doesn't work for me.  is it a typo?

---

### Post by Piraja on 2009-05-20
> **xeroforhire said:**
> the "gedit" command doesn't work for me.  is it a typo?
Gedit is a text editor; maybe you don't have it installed? You can use a text editor of your choice instead of gedit, e.g. nano, leafpad, etc.

---

### Post by xeroforhire on 2009-05-20
thanx i'll try that

---

### Post by xeroforhire on 2009-05-20
Oops!

For the next step:

Code:

## ## End Default Options ##
 
title		Ubuntu, kernel 2.?.??-?-??
root		(hdX,Y)

there's no "root".

What do i do now?

---

### Post by gaalaaant on 2009-05-22
I had the same thing as the guy above, no root.  so I just inserted one under 0,2 but uh, nothing happened, GRUB didn't even freak out, every was just normal

---

### Post by Randomperson_1000 on 2009-05-25
Same here theres no root in jaunty.

I don't think this works with jaunty

---

### Post by kyle2595 on 2009-05-30
I have been wanting to change the Splash Image in Grub for some time now.[]("http://ubuntuforums.org/showthread.php?t=30341") One of the first steps says: " move the image to the grub folder (assuming the current dir is your home folder and this is were you downloaded the image)." I tried running the command:

sudo mv usplash.xpm.gz /boot/grub/images

 Just like it said, but it tells me "cannot stat `usplash.xpm.gz': No such file or directory.
Firefox saves the .xpm.gz file to the desktop.  Can any one help?

---

### Post by Piraja on 2009-05-30
Did you change you current directory into ~/Desktop first? A bit like this:

```
username@nodename:~$ cd Desktop
username@nodename:~$ sudo mv grubsplash.xpm.gz /boot/grub/images
```

Another way:

```
sudo mv /home/username/Desktop/grubsplash.xpm.xz /boot/grub/images
```

"Usplash" is an odd name for a GRUB splash image, by the way, because Usplash is what you see *after* you boot (by default, it has the Ubuntu logo and the progress bar).

---

### Post by Herman on 2009-05-30
You have a choice of two ways to do the same thing.

One way would be to copy your usplash.xpm.gz file from your desktop to your /home/username directory and then run the same command again.

I would leave off the word 'images' at the end though, I don't know what that's there for.

Another way is to change the file path in the command so it will find your usplash.xpm.gz where it is, on your Desktop.
```
sudo mv Desktop/usplash.xpm.gz /boot/grub/
```Regards, Herman :)

EDIT: or Piraja's ways should also work.

---

### Post by shadowbladed on 2009-06-01
Thanks! ^^

---

### Post by Contra1971 on 2009-06-13
i found an easier way

i did this (in your tutorial)


> 
[B]Making your own splash image
[/B]Here's how you make your own image, I will not tell you how to use the Gimp as there are plenty of other tutorials on that, use google. :wink:
[I][B]1. New file
[/B][/I]There are some restrictions on the image, it must be 640x480 pixels large and only contain 14 colors.
[I][B]2. Create the art
[/B][/I]Uh, use your artistic talents and produce wicked art! If you want a photo or something just past it in and resize it. If you want to do something Ubuntu specific [this page]("http://www.ubuntulinux.org/wiki/UbuntuArtwork") might be of interest. If you want to use the Ubuntu logo in SVG format (vector graphics) there is a Gimp SVG plugin available in apt-get.[I][B]
3. Reduce colors
[/B][/I]The next step is to reduce the amount of colors to 14. Go Image->Mode->Indexed... and select *Generate optimum palette*, set the maximum number of colors to 14 and chose a dithering algorithm that looks good. Normal gives the most coherent colored areas but the Floyd-Steinberg algorithms are more appropriate for images with many colors.
***4. Save ***Save the image as an XPM image.but i didn't do the other stuff in the terminal...
instead i took the lazy approach
i went to Synaptic Package Manager and install "startup manager"

after you install it (automatic) it then gives you a choice as to what pic you wanna use for the grub screen, if you have already created 640x480 14 color .xpm  just add it there, no compression needed
i will change it later, but for now it was easy to use as it has just a few colors and no loss is even noticed

[COLOR=Red]**remember don't compress it**[/COLOR]
i am using

---

### Post by Piraja on 2009-08-17
Here's how my grub screen looks like in action (see post #75 in this thread). Did not yet edit menu.lst to change the second instance of "Windows Vista (loader)" to something like "Windows Vista (HP Recovery)", which I guess it must be(?), in order that the kids don't accidentally and unnecessarily boot it. Thanks to Herman for the colour and viewport hints!

**P.S.** (later): I decided to comment the second "Windows Vista (loader)" so that the HP Recovery partition won't be booted accidentally.

---

### Post by sourchier on 2009-10-04
Jaunty does not have a "root" for grub anymore. I had to add this to my menu.lst.
code:
## Splash image
splashimage=/grub/images/usplash.xpm.gz

I found this out using the startup manager. I hope this helps someone else.

---

### Post by faheyd on 2009-12-06
> **sourchier said:**
> Jaunty does not have a "root" for grub anymore. I had to add this to my menu.lst.
code:
## Splash image
splashimage=/grub/images/usplash.xpm.gz

I found this out using the startup manager. I hope this helps someone else.


Confirmed.  This is what I use after using package manager to install grub images on Ubuntu:

splashimage /grub/splashimages/biosplash.xpm.gz

Now works fine.

After installing images via package manager, do " ls /boot/grub/spl* " for your images.



Oh, and thank you OP for the post!

P.S. after installing some grub images, there are some hiding in /usr/share/images/grub , I've not tried them with grub instead of grub2, but I copied them into the grub/splashimages directory for later use.

---

### Post by memphis85 on 2010-04-04
hi ,

i'm new to linux and ubuntu. i found this thread and wanted to test the thing with the splashscreen. my only problem so far is that i can't find the file [COLOR=Red]menu.lst[/COLOR].
I use Ubuntu 10(beta).
Can someone give me a hint?
Thank you very much! 

Greets mem

---

### Post by ranch hand on 2010-04-04
Read the link in my sig.

If you had tried the search function you would have found this also;

 [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Which is thee best in depth info you will find.

---

### Post by kyle2595 on 2010-04-04
@memphis85:
I have not yet tried Ububtu 10.04, but in 9.10 you can find menu.lst if you go to Places -> Computer -> Filesystem -> boot -> grub.  It may be a little different for you because you are running the newer version of Ubuntu.  If all else fails, then try to Google it.  And remember, always make a backup.
P.S. Welcome to Ubuntu!

---

### Post by Herman on 2010-04-04
:)  9.10 is Ubuntu Karmic Koala and I think almost everyone who is using Karmic would have GRUB2 as their boot loader by default.

If you have Ubuntu 9.10 it's a lot easier to add a splashimage now, we don't need to reduce the quality of the image or make it into an .xpm file anymore.
Grub2 can handle images in the full screen resolution in optimal file formats like .tga .png or .jpg now. You can probably use a digital image right out of your camera.

This thread is still useful for people who still use older versions of Ubuntu and I still think the images we made in this thread have a kind of special appeal, but let's face it, GRUB2 is capable of being made far more beautiful. :)

---

### Post by slvidyasagar on 2010-05-30
Tnx for such a gud HowTo :D
But, I m stuck with a problem: ** I can't find the MENU.LST file in my /boot/grub directory !!**
But still, I m able to boot my system normally, I've a dual boot menu to chose b/w windows 7 and Ubuntu 10.04, and both r booting fine!!  ,


 Tnx in advance :)

---

### Post by kyle2595 on 2010-05-30
There is a great website that I found that shows you how to do many customizations to Grub 2: [ http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html  ]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Splashimages.html")Ubuntu 10.04 uses Grub 2 instead if Grub 1, in Grub 2 there is no menu.lst.

---

### Post by kyle2595 on 2010-05-30
There is a great website that I found that shows you how to do many customizations to Grub 2: [ http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html  ]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Splashimages.html")Ubuntu 10.04 uses Grub 2 instead if Grub 1, in Grub 2 there is no menu.lst.

---

### Post by psterrett on 2010-07-05
For reasons I don't understand, the original instructions would not work for me with Grub (1.)

However, when I put a symbolic link (splash.xpm.gz) in the grub folder, linked to the image in the /boot/grub/images folder, update-grub found it. :confused:

---

