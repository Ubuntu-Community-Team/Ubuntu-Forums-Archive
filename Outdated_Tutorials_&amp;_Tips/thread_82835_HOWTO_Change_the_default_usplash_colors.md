---
title: "HOWTO: Change the default usplash colors"
date: 2005-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by SilentCacophony on 2005-10-27
[COLOR="Red"]*** EDIT *** - Due to several people reporting problems on thier setups with this, and new distro releases, etc... I would advise that the wiki article be considered before this topic, as I can no longer test or troubleshoot this method, myself (though, I can't test the wiki method either.) The wiki article is here:

[https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")[/COLOR]

I wrote this HOWTO because I've noticed that myself and some other people have trouble reading the default usplash screen, and also because I wanted mine to be blue. ;) I've included a few files as attachments, one for the default brown usplash, one that's color-shifted to be blue, and one with a custom olive palette. All are optimized for brighter text and a more obvious progress bar background, and each will still use the default red failure color for failed steps.

This HOWTO was derived from the wiki page found at [https://wiki.ubuntu.com/USplashCustomizationHowto]("https://wiki.ubuntu.com/USplashCustomizationHowto") , but modified for a bit more user-friendliness (I hope,) and to accomodate ease of use with the files that I made. This was written with usplash (0.1-22) in mind, as future versions of usplash may be subject to change.

If you wish to try one of the usplash image replacements that I have attached below, the process takes only a few minutes, and is relatively painless. Note that step one, installing the *gcc* and *libbogl-dev* packages, may install a few development packages as dependencies, and may take awhile on dial-up connections.

Download either the [COLOR="Brown"]usplash-fix.png[/COLOR], [COLOR="Blue"]usplash-blue.png[/COLOR], or [COLOR="Green"]usplash-olive.png[/COLOR] (see attachments at the bottom of this post) file to your ~/ (home) directory, and open a terminal (it should start you in your ~/ directory, but enter **cd ~/** if you're not sure.) Then follow these steps:

**_1. Install the GCC and BOGL packages needed:_**

```
sudo apt-get install gcc libbogl-dev
```

**_2. Enter *only* the line below that matches whichever file that you downloaded:_**

```
[COLOR="Brown"]cp usplash-fix.png usplash-artwork.png[/COLOR]
[COLOR="Blue"]cp usplash-blue.png usplash-artwork.png[/COLOR]
[COLOR="Green"]cp usplash-olive.png usplash-artwork.png[/COLOR]
```

**_3. Now enter each of these steps to build your usplash:_**

```
pngtobogl usplash-artwork.png > usplash-artwork.c
gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
gcc -shared -Wl,-soname,usplash-artwork.so usplash-artwork.o -o usplash-fix.so
```

**_4. Copy your usplash to the usplash directory and create a new link to it:_**

```
sudo cp usplash-fix.so /usr/lib/usplash/usplash-fix.so
sudo ln -sf /usr/lib/usplash/usplash-fix.so /usr/lib/usplash/usplash-artwork.so
```

**_5. Regenerate the initramfs:_**

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

[COLOR="Red"]*** EDIT *** - Please note that the output of the last step may include the message *"splash image... none found, skipping..."*, which does not affect **usplash** in any way. It is a function of the /sbin/update-grub script which is executed while reconfiguring the linux-image package, and only displays if you've never previously set up the *optional* **grub** splash image, which would display *before* usplash would, and is an entirely separate splash image meant for the grub menu alone.[/COLOR]

**DONE!** The resulting usplash file will be **/usr/lib/usplash/usplash-fix.so**, and the next time you boot ubuntu, you should see the new usplash.


You'll be left with 4 extra files that you can delete in ~/ if you wish:

```
rm usplash-artwork.o usplash-artwork.c usplash-artwork.png usplash-fix.so
```


If you change your mind, then you can revert it back to the default usplash, by following these steps:

```
sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)
```


If you're interested in further modifying your usplash, and wish to know what I did, here's a summary:

* Downloaded the source, available from this page: [http://packages.ubuntu.com/breezy/misc/usplash]("http://packages.ubuntu.com/breezy/misc/usplash")
* Took the original usplash-artwork.png file and swapped the palette entries to increase the visibility of entries 2, 4, and 8 (described below.) Swapped 2 with 7, then 4 with 7, and 8 with 9. Saved the resulting file as usplash-fix.png.
* For the usplash-blue.png, I simply hue-shifted the entire palette of the usplash-fix.png so that thier RGB values swapped the R and B values.


Guidelines for the image format:

* The PNG must be: 640x480 16 colours.
* Some palette entries are used for particular purposes:

```
Palette Index | Used For
-----------------------------------------
0             | Background color
0             | Text background color
1             | Progress bar foreground color
2             | 'Ok' text foreground color
4             | Progress bar background color
8             | Description text foreground color
13            | 'Failed' text foreground color
```


The attachments (right-click > Save Link As...):

[COLOR="Brown"]Brown:[/COLOR]
[usplash-fix.png]("http://www.ubuntuforums.org/attachment.php?attachmentid=3197&stc=1&d=1130425734")
[ATTACH]3197[/ATTACH]

[COLOR="Blue"]Blue:[/COLOR]
[usplash-blue.png]("http://www.ubuntuforums.org/attachment.php?attachmentid=3198&stc=1&d=1130425734")
[ATTACH]3198[/ATTACH]

[COLOR="Green"]Olive:[/COLOR]
[usplash-olive.png]("http://www.ubuntuforums.org/attachment.php?attachmentid=3211&stc=1&d=1130475124")
[ATTACH]3211[/ATTACH]

---

### Post by ember on 2005-10-27
Beautiful - maybe I'll activate Usplash again, if I can have in blue. I didn't care for it for a while, yet with this howto it looks like it's really worth a try.

Thanks,
ember

---

### Post by lexor on 2005-10-27
Nice work thanks for the effort the blue theme looks really smart :) 

I had to download and install gcc as I got a error cause it wasnt installed on the system.

---

### Post by SilentCacophony on 2005-10-27
Thanks. :)

> I had to download and install gcc as I got a error cause it wasnt installed on the system.

Ah. I deviated from what I wrote, as I use aptitude exclusively, and it seems that gcc is a 'recommend' of one of the packages. Aptitude installs those by default.

I've corrected the step above to include gcc. Thanks for pointing that out.

---

### Post by rplantz on 2005-10-27
Thank you for posting this HOWTO. I am color blind so could barely see the default usplash. In a bright room, it was useless to me.

Blue is my favorite color, probably because I can see it clearly.

Bob

---

### Post by dude2425 on 2005-10-27
Can somebody please make one based off the color #ADAE9B (or any other nice greenish color from the theme Clearlooks-GNOME)? I can't seem to figure out how to do it without screwing up the text and progress bar colors. I've been trying to figure this out for 3 hours now and haven't gotten any breakthroughs. I've been working hard at coordinating everything on my computer with this color, and the only thing left is usplash and the login splash screen.

---

### Post by 23meg on 2005-10-27
For those like me who don't like the reflection below the logo, I've made two variants without reflections.

---

### Post by krye on 2005-10-27
That was great, Thanks!

---

### Post by bored2k on 2005-10-27
Pretty slick.

---

### Post by SilentCacophony on 2005-10-28
Thank you for the kind comments.

> **rplantz]Thank you for posting this HOWTO. I am color blind so could barely see the default usplash. In a bright room, it was useless to me.

Blue is my favorite color, probably because I can see it clearly.

Bob[/QUOTE]

Glad to hear it helped. I wasn't sure if this would be help much for color-blindness.

[QUOTE=dude2425]Can somebody please make one based off the color #ADAE9B (or any other nice greenish color from the theme Clearlooks-GNOME)? I can't seem to figure out how to do it without screwing up the text and progress bar colors. I've been trying to figure this out for 3 hours now and haven't gotten any breakthroughs. I've been working hard at coordinating everything on my computer with this color, and the only thing left is usplash and the login splash screen.[/QUOTE]

That color looks a bit olive-drab to me, similar to gperfection2, I think. Not an uncommon choice in colors. I'm adding another version in that color scheme, since you asked nicely.  said:**
> For those like me who don't like the reflection below the logo, I've made two variants without reflections.

Nice. Thanks for adding.

.

---

### Post by dude2425 on 2005-10-28
[quote=SilentCacophony]That color looks a bit olive-drab to me, similar to gperfection2, I think. Not an uncommon choice in colors. I'm adding another version in that color scheme, since you asked nicely. ;) I didn't get that one to quite match the text color intensities of the other ones, but it's close.

Anyway, it is a bit tricky keeping the palette correct. I had trouble finding an image editor that handled limited-palette images like these in the way which I needed. I couldn't seem to get The Gimp to do much for me, so I resorted to an old copy of PaintShop Pro to do the pallete-swapping. I'll have to explore The Gimp a bit more, as I like that the best of any linux image editors I've found.[/quote]

Ahah! I guess that's why all my efforts went to no avail. I tried to do the whole thing with GIMP. Thnx so much for this. I love this color. Funny thing too, because I have always been more akin to blue for as long as I could remember. It wasn't till my first experience with Linux that I actually tried out a few nice green themes (Glider colored green and Clearlooks-GNOME)

I really appreciate your efforts. I've got to compile a large tutorial recounting all my choices of wallpapers and themes and stuff to make my desktop green some time. Next up on my agenda is the Login splash, and the little ubuntu icon in the top left that just appeared after switching to dapper.

---

### Post by MrRoboto on 2005-10-28
I did mine.. an istitutional one.
enjoy

---

### Post by veloct on 2005-10-30
didn't work for me, when I do the dpkg-reconfigure it doesn't find any images so I have no image for usplash, rats!!! I'm including a screenshot.

[IMG]http://www.veloct.net/images/Screenshot.png[/IMG]

---

### Post by SilentCacophony on 2005-10-30
[QUOTE=veloct]didn't work for me, when I do the dpkg-reconfigure it doesn't find any images so I have no image for usplash, rats!!![/QUOTE]

Hi. AFAIK, there should be no problems as long as all steps were followed correctly.

Anyway, the original image should still be there. It's best to copy and paste so that there is no chance of typos. If you copy-n-paste each of these lines into a terminal, it should restore the original:

[I]sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)[/I]

That just reconfigures it back to the old file.

---

### Post by veloct on 2005-10-30
nope, is still saying "splash image - none found -" when reconfiguring.

Sorry for the image being so big

[IMG]http://www.veloct.net/images/folder.png[/IMG]

---

### Post by dude2425 on 2005-10-30
[quote=veloct]nope, is still saying "splash image - none found -" when reconfiguring.

Sorry for the image being so big
[snip]
[/quote] 
Actually, it is talking about grub's splash image. That has nothing to do with usplash whatsoever. The splash image it is talking about is the image that is shown behind all the text when you boot and can choose which kernel or OS you want to boot from. Have you even tried rebooting to see if you can see your splash? Give it a try.

The only reason that you have to do that step is to regenerate the initramfs.

---

### Post by SilentCacophony on 2005-10-30
**EDIT** - dude2425's post above may explain it, so I'd explore that first.

That's odd. I don't see anything in your commands that would be a problem, except possibly the fact that you ran the second gcc step twice for two different ouptut files, but I don't really think that's the problem.

The first two lines following the dpkg-reconfigure look as if dpkg-reconfigure may be acting oddly, but I wouldn't know why it would do that.

If it were me, I might try adding the *--force* option before the linux-image, but the manpage advises that it *could be risky* to use that option, so beware.

In any case, if all else fails, I would think that purge-removing (*sudo apt-get --purge remove usplash*) and re-installing usplash should restore it.

Sorry if I'm not much help, but I've no knowledge of problems with this.

---

### Post by blastus on 2005-10-30
Thank you SilentCacophony for this HOWTO! I would have never figured this out myself. ;)

---

### Post by endersshadow on 2005-11-07
A quick HOWTO for making your own usplash in the GIMP:

1. Make a new image 640x480.

2. Go to Dialogs>Palettes and create a 16 color palette with your choice of colors and name it Ubuntu Splash.  Make sure the following are in the right order (remember, index 0 is the first one):
```
Palette Index | Used For
-----------------------------------------
0             | Background color
0             | Text background color
1             | Progress bar foreground color
2             | 'Ok' text foreground color
4             | Progress bar background color
8             | Description text foreground color
13            | 'Failed' text foreground color
```

3. Now that you've done that, go to Image>Mode and select Indexed.  Select "Use Custom Palette" and select Ubuntu Splash.

4. Make it look how you want it to, and save it as ubuntu-artwork.png in your home directory.  Taking it from there, you can start at step 3 of the original HOWTO (assuming you've installed the necessary packages).  Make sure that you don't delete the original ubuntu-artwork.png if you want to keep it around!!

:-D

Edit: I figured I'd attach mine in case anybody likes a lot of dark green like I do...

---

### Post by izmaelis on 2005-11-07
SilentCacophony, thanks for this nice HOWTO. Ubuntu is nice Linux distro, but default colour (brown) is realy not for me. You saved my day (and usplash that I wasn't using for a while).

---

### Post by benplaut on 2005-11-08
here's an olive one with no reflection, if anyone wants :) 

MrRoboto, that thing looks really nice :)

---

### Post by loon on 2005-11-11
Hrmm.... wonder if there is a way to make the imaged more crisp. Would this effect the loading??

---

### Post by benplaut on 2005-11-11
[QUOTE=loon]Hrmm.... wonder if there is a way to make the imaged more crisp. Would this effect the loading??[/QUOTE]

it can only be 640x480, with 16 colors (several are reserved)... that's very limiting :mad: 

it would be possible, but it would take some serious graphic design skills...

---

### Post by autocrosser on 2005-11-11
Hey Ben--point me at the files & I'll take a stab at it---
 
 
****my brain has been undead for longer than kev's site has been up:p ****
 
[quote=benplaut]it can only be 640x480, with 16 colors (several are reserved)... that's very limiting :mad: 
 
it would be possible, but it would take some serious graphic design skills...[/quote]

---

### Post by cosimo on 2005-11-24
Helloeverything goes well untill this command "sudo dpkg-reconfigure linux-image-$(uname -r)" And yes I put my user name in.
 It says that this does not exist or is not installed

---

### Post by veloct on 2005-11-24
that's because uname does not stand for username.  Try typing uname -r by itself in a terminal, it will tell you what kernel image you are using.

---

### Post by SilentCacophony on 2005-11-25
[QUOTE=cosimo]Helloeverything goes well untill this command "sudo dpkg-reconfigure linux-image-$(uname -r)" And yes I put my user name in.
 It says that this does not exist or is not installed[/QUOTE]

To clarify, that is meant to be entered just as it is. What it does is insert the correct linux image number, without involving any guesswork.

I purposely left any 'pseudocode' out of the howto in order to try and prevent confusion, even though it adds an extra step of renaming the chosen file (the color-coded choices) so that the rest of the steps don't need any filename substitution.

Of course, that limits the scope of the howto to those few choices offered, but my aim was to keep it simple.

Anyway, as it's quite often difficult to give instructions without involving some kind of pseudocode, it's understandable that some would come to expect it. ;)


On another note, thanks to those adventurous ones who have contributed to this and any other howto threads. :)

---

### Post by ace2005 on 2005-11-25
Could someone do some for Kubuntu too?

---

### Post by alesdoc on 2005-12-03
I followed the hotto, but when i do

[HTML]sudo dpkg-reconfigure linux-image-$(uname -r) [/HTML]

i receive the following messages:

[HTML]Not touching initrd symlinks since we are being reinstalled (2.6.12-10.24)
Not updating image symbolic links since we are being updated (2.6.12-10.24)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz
Found kernel: /boot/vmlinuz.old
Found kernel: /boot/vmlinuz-2.6.12-10-amd64-generic
Found kernel: /boot/vmlinuz-2.6.12-9-amd64-generic
Found kernel: /boot/vmlinuz-2.6.12-8-amd64-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done[/HTML]

Why cannot my pc the spalsh image? Now i cannot also come back to the initial image

---

### Post by SilentCacophony on 2005-12-03
[QUOTE=alesdoc]I followed the hotto, but when i do

HTML Code:

sudo dpkg-reconfigure linux-image-$(uname -r)


i receive the following messages:

HTML Code:

Not touching initrd symlinks since we are being reinstalled (2.6.12-10.24) Not updating image symbolic links since we are being updated (2.6.12-10.24) Searching for GRUB installation directory ... found: /boot/grub . Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst . Searching for splash image... none found, skipping... Found kernel: /boot/vmlinuz Found kernel: /boot/vmlinuz.old Found kernel: /boot/vmlinuz-2.6.12-10-amd64-generic Found kernel: /boot/vmlinuz-2.6.12-9-amd64-generic Found kernel: /boot/vmlinuz-2.6.12-8-amd64-generic Found kernel: /boot/memtest86+.bin Updating /boot/grub/menu.lst ... done


Why cannot my pc the spalsh image? Now i cannot also come back to the initial image[/QUOTE]

Hi. I have had that message in my recent tests of re-changing the splash image, but it still works fine for me. AFAIK, the *"splash image... none found, skipping..."* message is in regards to a **grub** splash image, which is an entirely different thing from usplash, and so should be ignored.

Have you tried rebooting to see if it worked? Since you said you tried to restore the original, you may want to try changing it again and rebooting to see if it's changed.

Otherwise, the only other thing I've found that may be a factor is possibly a problem with the way your kernal image package is installed, as described in this thread:

[http://ubuntuforums.org/showthread.php?t=75414](http://ubuntuforums.org/showthread.php?t=75414)

Hope this helps.

**__________________________________________________**

[QUOTE=loon]Hrmm.... wonder if there is a way to make the imaged more crisp. Would this effect the loading??[/QUOTE]

I don't think that there is a way to make it handle images with more resolution. Perhaps the developer(s) of usplash would be able to do this, but I don't know.

One thing that I know of that may help, is to add a **vga=794** (or similar) option when booting in order to change the vesafb resolution to a higher one, which will make usplash appear centered in the screen, but smaller than before (and therefore less 'fuzzy-looking'.) This would also affect the console font sizes in your tty's, making them smaller, which in turn makes the shutdown text look more pleasant (IMO.)

There is one link I know of that outlines some vesafb modes [here]("http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html"). Once the mode number is known, it's pretty simple to add the option. For example, I like 1280x1024x16bit, which equates to vga=0x31A or vga=794 (either should work.) 

So, you can open your /boot/grub/menu.lst file with your favorite editor (I'll use gedit,)

```
sudo gedit /boot/grub/menu.lst
```

... and edit it as so, adding the appropriate option where in bold:

```
## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash **vga=794**
```

... then update the menu.lst. This makes it so your change is applied only to the primary boot option for each kernal, and makes it survive subsequent updates:

```
sudo update-grub
```

Some people have reported problems with using the vga= option with grub causing usplash not to display, but it currently works fine for me, so I'd imagine it's fixed now.

---

### Post by cdsboy on 2005-12-03
Well this is my crack at making a book screen.. oh and yes when it boots the text's background is the same color blue as the box...

---

### Post by phux on 2005-12-04
Hmm my boot-spash does not appear at all, after i uses this howto...
Got no image any more.

System:
Grub, Ubuntu 5.1 (newest kernel)

Do i activate the splash with grub?
My Ubuntu-entry in grub shows this option: quiet splash

Maybe thats the reason?

Hope, someone can help (guess its pretty easy, but im just too stupid :) )

---

### Post by kperkins on 2005-12-05
Here's mine:

---

### Post by kperkins on 2005-12-05
Here's how it looks when booting:

---

### Post by kperkins on 2005-12-05
[QUOTE=phux]Hmm my boot-spash does not appear at all, after i uses this howto...
Got no image any more.

System:
Grub, Ubuntu 5.1 (newest kernel)

Do i activate the splash with grub?
My Ubuntu-entry in grub shows this option: quiet splash

Maybe thats the reason?

Hope, someone can help (guess its pretty easy, but im just too stupid :) )[/QUOTE]
no, that should be correct. Here's my ubuntu entry:
```


title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,0)
kernel		/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash
initrd		/initrd.img-2.6.12-10-686
savedefault
boot

```
Do you have usplash installed? I don't believe that it is by default.

---

### Post by Vlammetje on 2005-12-05
[QUOTE=cdsboy]Well this is my crack at making a book screen.. oh and yes when it boots the text's background is the same color blue as the box...[/QUOTE]

Yes... ine looked like that..... after putting vga=749 into the menu.lst file the whole thing has shrunk to proportions on the middle of the screen, but both the loading bar and the scrolling text are still happenin inside the borders of my image, instead of underneath as they did on the default splash... any thoughts on how to fix that?


[edit] or do I in fact need to shrink my 640x 480 (or whatever the proportions were) image to smaller and leave some black space all around it where the scrolling text and the loading bar will go??

Also it has adjusted the color sof the OK's and FAILS to a green that matches my image. How did it do that? I don't recall putting in any colour values?

---

### Post by dude2425 on 2005-12-05
[quote=Vlammetje]Yes... ine looked like that..... after putting vga=749 into the menu.lst file the whole thing has shrunk to proportions on the middle of the screen, but both the loading bar and the scrolling text are still happenin inside the borders of my image, instead of underneath as they did on the default splash... any thoughts on how to fix that?


[edit] or do I in fact need to shrink my 640x 480 (or whatever the proportions were) image to smaller and leave some black space all around it where the scrolling text and the loading bar will go??

Also it has adjusted the color sof the OK's and FAILS to a green that matches my image. How did it do that? I don't recall putting in any colour values?[/quote]
Technicly, all the color values that are used, are used from the splash itself:
[https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)
That should clear a few things up for you.

---

### Post by nelposto on 2005-12-06
This was cool, thanks!

I've changed the splash screen and the login screen to blue ones. However, between logging in and the desktop being completely loaded, the background reverts to brown and the ubuntu 'loading this that and the panel' box comes up in brown. 

Is there any way to make these blue? or to make the background be my normal desktop background for this stage?

Thanks.

---

### Post by phux on 2005-12-06
[QUOTE=kperkins]no, that should be correct. Here's my ubuntu entry:
```


title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,0)
kernel		/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash
initrd		/initrd.img-2.6.12-10-686
savedefault
boot

```
Do you have usplash installed? I don't believe that it is by default.[/QUOTE]

I did everything as written in the howto. got newest version of usplash.
Well it works without blue usplash too... its not that important :)

---

### Post by SilentCacophony on 2005-12-06
[QUOTE=nelposto]This was cool, thanks!

I've changed the splash screen and the login screen to blue ones. However, between logging in and the desktop being completely loaded, the background reverts to brown and the ubuntu 'loading this that and the panel' box comes up in brown. 

Is there any way to make these blue? or to make the background be my normal desktop background for this stage?

Thanks.[/QUOTE]

You can change both the splash (aka the '*loading this that and the panel'*) and the background color as outlined in this howto:

[http://ubuntuforums.org/showthread.php?t=83009](http://ubuntuforums.org/showthread.php?t=83009)

look for this part:

*3-Next thing...change the backgroud color that appears while splash screen is shown:*

**_________________________________________**

[QUOTE=Vlammetje]Yes... ine looked like that..... after putting vga=749 into the menu.lst file the whole thing has shrunk to proportions on the middle of the screen, but both the loading bar and the scrolling text are still happenin inside the borders of my image, instead of underneath as they did on the default splash... any thoughts on how to fix that?


[edit] or do I in fact need to shrink my 640x 480 (or whatever the proportions were) image to smaller and leave some black space all around it where the scrolling text and the loading bar will go??

Also it has adjusted the color sof the OK's and FAILS to a green that matches my image. How did it do that? I don't recall putting in any colour values?[/QUOTE]

AFAIK the vga=749 option should not affect the placement of the bar and text within the image. They should, in fact, be displayed within the image itself. Note that most of the attachments in this thread have the imagery to the side or top of the image, with space allowed in the center and bottom portions of the images for the progress bar and boot text to be displayed in. 

Look at the examples that **kperkins** provided for an idea of how usplash displays in regards to the image.

Also, the image must have an indexed pallete of 16 colors, and usplash will use certain color entries for it's own purposes as outlined near the bottom of my original post and on the wiki page. It can be a task to get a decent image while preserving certain colors for usplash, but it's possible.

**____________________________________________**


[QUOTE=phux]Hmm my boot-spash does not appear at all, after i uses this howto...
Got no image any more.

System:
Grub, Ubuntu 5.1 (newest kernel)

Do i activate the splash with grub?
My Ubuntu-entry in grub shows this option: quiet splash

Maybe thats the reason?

Hope, someone can help (guess its pretty easy, but im just too stupid )[/QUOTE]

Sorry to hear that. If it was working before, I don't know of any reason that it wouldn't work anymore after this, other than possibly a mistake was made. You do have the correct splash option in the grub menu.lst.

I can't think of a good way to troubleshoot what went wrong, remotely, so I'd suggest either trying it again and and looking for any suspicious output from the commands (errors, that is,) or trying the steps that I listed to revert it to the original.

It would probably be best to cut-and-paste each line into the terminal to prevent typos, as well. Also, make sure that you're working from the directory in which you downloaded the selected image file into. If you perform a **ls** command before starting with the 2nd step in the howto, you should see the filename of the image that you are using. 

If you're using a different image than what I provided, you'll have to substitute the name as the first filename in the **cp** command in the 2nd step.

As a last resort, you may try to reinstall usplash with:

```
sudo apt-get --reinstall install usplash
```

**EDIT** - You would probably have to do step 5 of the howto after a reinstall, as well.

Hope this helps.

---

### Post by phux on 2005-12-07
[QUOTE=SilentCacophony]
Sorry to hear that. If it was working before, I don't know of any reason that it wouldn't work anymore after this, other than possibly a mistake was made. You do have the correct splash option in the grub menu.lst.

I can't think of a good way to troubleshoot what went wrong, remotely, so I'd suggest either trying it again and and looking for any suspicious output from the commands (errors, that is,) or trying the steps that I listed to revert it to the original.

It would probably be best to cut-and-paste each line into the terminal to prevent typos, as well. Also, make sure that you're working from the directory in which you downloaded the selected image file into. If you perform a **ls** command before starting with the 2nd step in the howto, you should see the filename of the image that you are using. 

If you're using a different image than what I provided, you'll have to substitute the name as the first filename in the **cp** command in the 2nd step.

As a last resort, you may try to reinstall usplash with:

```
sudo apt-get --reinstall install usplash
```

**EDIT** - You would probably have to do step 5 of the howto after a reinstall, as well.

Hope this helps.[/QUOTE]

It didnt work.
After the installation of Ubuntu the brown one worked and after i used this howto (i did copy paste and there was absolutely no error) the usplash didnt appear anymore and its place took a not blinking cursor (frozen screen).
That cursor lasted till boot was finished and the login screen appeared.

I used the default-howto from the wiki and it replaced the cursor with the normal boot-messages without the usplash screen. Well, that works for me... i just wanted to kill the brown stuff.

First, i thought the Ubuntu-version was the problem, but i guess thats not true.

Well, as i said before, it works for me that way. dont need the blue one so bad :)

thx anyway

---

### Post by Bloot on 2005-12-07
Nice how-to!!! Usplash looks much clearer now in blue.

Thanks.

---

### Post by johannes on 2005-12-07
[QUOTE=phux]It didnt work.
After the installation of Ubuntu the brown one worked and after i used this howto (i did copy paste and there was absolutely no error) the usplash didnt appear anymore and its place took a not blinking cursor (frozen screen).
That cursor lasted till boot was finished and the login screen appeared.[/QUOTE]

This happened to me as well. I have tried reinstalling usplash, deleting the usplash config files as well as all files containing usplash in their name and reconfiguring the linux-image after that.

Oh well, the normal boot-messages will do.

---

### Post by steppenwulf241 on 2005-12-07
[QUOTE=phux]It didnt work.
After the installation of Ubuntu the brown one worked and after i used this howto (i did copy paste and there was absolutely no error) the usplash didnt appear anymore and its place took a not blinking cursor (frozen screen).
That cursor lasted till boot was finished and the login screen appeared.
[/QUOTE]

This happened to me too... What's strange is that I just reinstalled Ubuntu, but I went through the very same process on my earlier install to get this to work - and it ran like a charm last time... Strange.

---

### Post by bourrinlepoulpe on 2005-12-07
yes blue splash for me too really nice thanx !

---

### Post by Bloot on 2005-12-08
Sorry wrong thread.

---

### Post by phux on 2005-12-09
@ johannes, steppenwulf241
I'm trying to find a reason:
Did you use the updated version of breezy?
Did you use automatix? (maybe it changes something necessary for usplash...)

Strange...

---

### Post by SilentCacophony on 2005-12-09
[QUOTE=phux]@ johannes, steppenwulf241
I'm trying to find a reason:
Did you use the updated version of breezy?
Did you use automatix? (maybe it changes something necessary for usplash...)

Strange...[/QUOTE]

I can't think of what it might be that is causing some of you trouble. I don't know any reason any other package might interfere, so the version is my only suspect, though not a likely one...

I run a fully-updated (but not backported) Breezy from a fresh install of the original full release. I haven't used automatix, and generally stick to the repositories for my software.

I wrote this using usplash version 0.1-22, the default version for Breezy. I checked to see if usplash is backported for Breezy, and AFAIK it's not, so that shouldn't be an issue.

I'm curious if any of you who can't get it to work might be running the Dapper pre-release. I've checked the version in the Dapper repos, and it's 0.1-24, so it may have changed to an incompatible extent if so.

You can check the version installed by running this in a terminal:

```
dpkg -s usplash
```

mine looks like so:

```
brian@ubuntu:~$ dpkg -s usplash
Package: usplash
Status: install ok installed
Priority: standard
Section: universe/misc
Installed-Size: 184
Maintainer: Matthew Garrett <mjg59@srcf.ucam.org>
Architecture: i386
Version: 0.1-22
Depends: libc6 (>= 2.3.4-1), initramfs-tools (>= 0.15)
Conffiles:
 /etc/init.d/usplash 82b31470f397a42ab98a8f120f848fad
Description: Userspace bootsplash utility
 Usplash is a userspace application that uses the Linux framebuffer interface
 to draw a splash screen at boot. It has a companion utility that is able to
 send commands to usplash, allowing information about the bootup sequence to
 be displayed in a more attractive way.
```

---

### Post by phux on 2005-12-11
i get exactly the same result with "dpkg -s usplash"...

---

### Post by skela on 2005-12-20
Hey I need some help...
I kinda stop up in step 3 line 2...

gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o

after i paste that in I get this error message:

usplash-artwork.c:1: error: syntax error before 'has'

And then the 3rd line wont work because its dependant on the second line...
Any help would be much appreciated...

---

### Post by sunny_nwho on 2005-12-28
did not work for me after doing wht has been metioned here i just get a blank screen with the cursor blinking at the top left corner and then comes my login screen..

---

### Post by TrinitronX on 2006-01-20
To get this to work for me (I have compiled my own kernel)... I had to do two things.  First, after updating my initramfs manually, I got an error saying that 
/usr/lib/usplash/usplash-artwork.so was not found, so I looked in /usr/lib/ and found that a symbolic link usplash-artwork.so was found there.  So, I made a link to that one from the usplash directory.  Then, I manually re-updated my initramfs, and it worked :D.  (it seems the custom splash I made was the wrong size though :P)
```

sudo ln -s ../usplash-artwork.so /usr/lib/usplash/usplash-artwork.so
sudo update-initramfs -t -u -k $(uname -r)

```

---

### Post by TrinitronX on 2006-01-20
fixed accidental double post

---

### Post by Vinze on 2006-01-25
I really like this, however, I have some troubles making my own. I first made on which just displayed as a few coloured stripes, then I found out (or rather, a friend told me) how to set the colours to 16 colours, but now I still don't know how to create an indexed pallete. Could anyone help me? Preferably with the GIMP, but if you have to, another (Linux of course) programma will suffice too. Thanks in advance.

---

### Post by Theely on 2006-02-08
I just attempted to try this and I get the following error...

michael@ubuntu-server:~$ gcc -shared -Wl,-soname,usplash-artwork.so usplash-artwork.o -o usplash-fix.so
gcc: usplash-artwork.o: No such file or directory

I'm not even sure where it would be looking for those.

---

### Post by Theely on 2006-02-09
Doh, nm. I guess "artwrok" is not how you spell "artwork" :-\"

---

### Post by eklitzke on 2006-02-19
I spent a fair amount of time today trying to make a good green variation of this, using the GIMP.  I ran into some problems.  The main one is that the GIMP doesn't let you change the hue while the image is in "indexed" mode.  You have to put it into RGB mode, alter it, then index it with 15 colors, add then add in the red index (for error messages).  The order of the indices will be messed up, and there doesn't appear to be an easy way to fix this, although you may be able to fix it with imagemagick.

On the other hand, it is **very** easy to make alterations in Photoshop; I did this while at work today (where I use Windows), and it took me about one minute.  All you have to do is open the image and use Image | Adjustments | Hue/Saturation and move the Saturation slider to along the bar to change the color.  Using this you can easily make the splash image green, yellow, orange, red, etc.  One you have done this, everything will be looking good, but the index for error messages (red) will also be altered, which you presumably don't want. To fix this just open up Image | Mode | Color Table, double click on the index you want to change (third to last for error messages) and then you can change the color to whatever you want; I changed it back to red (ff0000).  Then save, and enjoy!

Also, I give permission to anyone to use the image I am attaching in any way they wish.

---

### Post by eklitzke on 2006-02-19
I thought the green in the original version I posted was too bright, so this is a modified version with less saturation.  Like the original image, you can do whatever you want with it, including redistributing it.

---

### Post by Jimmy_r on 2006-03-12
I made a few from scratch with gimp today...
They work fine in Dapper with boot option vga=0x31b
If i omit the vga line, only the background shows.

(They are not blurry as the previews appear to be) ;)

---

### Post by stanz on 2006-03-15
Hi All...
Geez...this is really kewl, and thanks for the howto.. & putting it here...and your time...
but- its just ain't working for me!? 
I've read what i could about splash & grub...this thread...and tried fixes.
Now i guess i've gone to far- cause i get:
[I]:~$ sudo ln -s ../usplash-artwork.so /usr/lib/usplash/usplash-artwork.so
ln: `/usr/lib/usplash/usplash-artwork.so': File exists
:~$ sudo update-initramfs -t -u -k $(uname -r)
cpio: ./usr/lib/usplash/usplash-artwork.so: Too many levels of symbolic links
[/I]===================
I've tried replacing the .so's in /splash, if maybe it was the file...? Nadda!
So...I donno...I'm to new here- to know what to do.
And i ain't done yet,,,, I will have splash!!....one day...

---

### Post by bluebyt on 2006-03-16
Can I do this "Howto" with Dapper?

---

### Post by 4linux on 2006-03-26
[QUOTE=eklitzke]I thought the green in the original version I posted was too bright, so this is a modified version with less saturation.  Like the original image, you can do whatever you want with it, including redistributing it.[/QUOTE]

Both green ones are great!  Just what I wanted.  And thanks to SilentCacophony for the How-to, it works great.
:)

---

### Post by exodus on 2006-03-27
many thx.. i just tried this..

---

### Post by .ak on 2006-03-31
Hey guys,

I am having some trouble with this, I am using the usplash-blue.png and here is a log of exactly what I am doing:

```
root@akcom:~# sudo apt-get install gcc libbogl-dev
Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
libbogl-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@akcom:~# cp usplash-blue.png usplash-artwork.png
root@akcom:~# pngtobogl usplash-artwork.png > usplash-artwork.c
root@akcom:~# gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
root@akcom:~# gcc -shared -Wl,-soname,usplash-artwork.so usplash-artwork.o -o usplash-fix.so
root@akcom:~# sudo cp usplash-fix.so /usr/lib/usplash/usplash-fix.so
root@akcom:~# sudo ln -sf /usr/lib/usplash/usplash-fix.so /usr/lib/usplash/usplash-artwork.so
root@akcom:~# sudo dpkg-reconfigure linux-image-$(uname -r)
Not touching initrd symlinks since we are being reinstalled (2.6.15-19.29)
Not updating image symbolic links since we are being updated (2.6.15-19.29)
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-19-686
Found kernel: /boot/vmlinuz-2.6.15-19-386
Found kernel: /boot/vmlinuz-2.6.15-16-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@akcom:~#

```

When I reboot I get nothing at all, after a while the default linux boot time thing comes up I get an error complaining about some font issue but I do not believe it is related to this.

I understand that the "Searching for splash image ... none found, skipping ..." Does not matter and it is to do with the Grub spash image.

Does anyone have any ideas? any log files I can check?

---

### Post by opticyclic on 2006-04-23
I made a couple of matrix style usplash screens by modifying some images from GNOME Look.
[http://www.ubuntuforums.org/showthread.php?t=159345](http://www.ubuntuforums.org/showthread.php?t=159345)

Attached my latest one here.

I like changing things a lot.

How could I take this HOWTO and make the instructions a clickable file? :-k 
I guess some sort of script, but I don't know how to do that in Linux. :(

---

### Post by stanz on 2006-04-28
Nice look opticyclic !   Free to use?
What would you want to 'click' ?

---

### Post by opticyclic on 2006-04-29
The image I edited is here
[http://www.gnome-look.org/content/show.php?content=36821](http://www.gnome-look.org/content/show.php?content=36821)

Its GPL so I guess that means mine is free to use as well.

When I said "make the instructions a clickable file", I meant put all the commands in a script (BASH?).
Then pack it with the image in a compressed file so that you could distribute it.
So that all anyone had to do was run ('click') the script file and it would install.

---

### Post by opticyclic on 2006-04-29
I guess this is sort of what I meant.
I have copied all the commands from the first post into a BASH file.
Now there is less to do to install it.

It would be nice to have a GTK front end for this, but I don't know how to do that :-?

---

### Post by opticyclic on 2006-04-29
Kommander is the Bomb!

It is really easy to create a GUI then add your script to it!
It has taken me about 30mins to figure out the user interface and build a working application! (see attached)

In order to run this you need kommander installed.
You then type kmdr-executor usplash.kmdr in the terminal.
All you have to do then is select the file you want as your usplash and click OK.

You will need to type your password in the terminal because some of the commands us sudo.

---

### Post by testube_babies on 2006-05-04
[QUOTE=bluebyt]Can I do this "Howto" with Dapper?[/QUOTE]

As long as you change your boot parameters to include vga=791.  [Read on...]

---

### Post by flapane on 2006-05-04
I used
sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)

the output is:
flapane@a64:/usr/lib/usplash$ sudo dpkg-reconfigure kernel-image-2.6.15-flap

 You are attempting to install a kernel version that is the same as
 the version you are currently running (version 2.6.15-flap). The modules
 list is quite likely to have been changed, and the modules dependency
 file /lib/modules/2.6.15-flap/modules.dep needs to be re-built. It can
 not be built correctly right now, since the module list for the
 running kernel are likely to be different from the kernel installed.
 I am creating a new modules.dep file, but that may not be
 correct. It shall be regenerated correctly at next reboot.

 I repeat: you have to reboot in order for the modules file to be
 created correctly. Until you reboot, it may be impossible to load
 some modules. Reboot as soon as this install is finished (Do not
 reboot right now, since you may not be able to boot back up until
 installation is over, but boot immediately after). I can not stress
 that too much. You need to reboot soon.

Please Hit return to continue.
Not touching initrd symlinks since we are being reinstalled (10.00.Custom)
Not updating image symbolic links since we are being updated (10.00.Custom)
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
---------> Searching for splash image ... none found, skipping ... <-----------------
Found kernel: /boot/vmlinuz.old
Found kernel: /boot/vmlinuz-2.6.15-flap
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

what could I do?

---

### Post by CookedGryphon on 2006-05-09
I made a custom usplash that works really well if anyone's interested, its got tux, what more could you want :D

[http://www.gnome-look.org/content/show.php?content=39009](http://www.gnome-look.org/content/show.php?content=39009)

---

### Post by groggyboy on 2006-05-10
ok.  not working.
> groggyboy@ono-sendai:~$ gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
**usplash-artwork.c:1: error: syntax error before &#8216;has&#8217;**

anyone have any suggestions?

p.s. - this is step 3 of the howto, second line of code
p.p.s - running dapper, if that makes any difference
](*,)

---

### Post by openback on 2006-05-20
And now for my first contribution! A Metroid-based custom usplash!

---

### Post by Vinze on 2006-05-23
Again, has anyone any idea or a link to a guide on how to set an indexed palette in the GIMP?

---

### Post by groggyboy on 2006-05-23
**A quick howto on using the GIMP to create a usplash:**

1. Create a new document that is 640x480.
2. Right click the image in the GIMP.  Choose "Image > Mode > Indexed..."
3. In the dialogue, select "Generate optimum palette" and set the "Maximum number of colors" to 16.  Click OK.
4. To edit individual palette entries, right click on the image and choose "Dialogues > Colourmap".
5. These are the indexed entries.  Edit the entries according to the guidelines on the first page of this thread (the howto).  This part can be tricky, as changes may affect your image.
6. Save as a .png, exit, and follow the instructions in the howto.

Good luck!
groggyboy

---

### Post by mindwarp on 2006-05-25
I got it to work in dapper by adding vga=791 in my menu.lst file in the part after ro splash vga=791

---

### Post by Vinze on 2006-05-25
[QUOTE=groggyboy]**A quick howto on using the GIMP to create a usplash:**

1. Create a new document that is 640x480.
2. Right click the image in the GIMP.  Choose "Image > Mode > Indexed..."
3. In the dialogue, select "Generate optimum palette" and set the "Maximum number of colors" to 16.  Click OK.
4. To edit individual palette entries, right click on the image and choose "Dialogues > Colourmap".
5. These are the indexed entries.  Edit the entries according to the guidelines on the first page of this thread (the howto).  This part can be tricky, as changes may affect your image.
6. Save as a .png, exit, and follow the instructions in the howto.

Good luck!
groggyboy[/QUOTE]

OK, thanks a lot, will try that at home :D

---

### Post by soulglo83 on 2006-05-25
finally, what everyone can agree will be the best ubuntu bootsplash possible.  i was inspired by the man that has made only excellant movies and endorsed only the finest of products, wilford brimley; to create a custom ubuntu wilford brimley bootsplash!

should (with wilford's blessing) become the default ubuntu bootsplash! something this great i couldn't keep to myself!

PS. this was modified from the ubuntu-olive.png on the front of this thread, i literally ripped it off, and i havent paid wilford anything.


EDIT: I too have made this work by adding the vga=791 to my kernel cheat codes in /boot/grub/menu.lst on dapper

---

### Post by openback on 2006-05-29
lol, wtf, now that's just madness.
(where's my Chuck Norris usplash now? lol)

---

### Post by BobSongs on 2006-05-30
Just thought I'd add my "thanks" here too.

I've got a "Blubuntu" happening. So I've got the blue splash screen. Thanks.

One of the first things I found a little weird about Ubuntu was it's brown interface. I just find blue to be more soothing.

Thanks again!

---

### Post by Nordoelum on 2006-06-04
How to change to the Xubuntu splash screen? The weird thing is that I have the Ubuntu splash and the Xubuntu turn off splash :(

How to fix?

---

### Post by Nordoelum on 2006-06-04
You should add to the HOWTO that it isn't clever to remove the usplash :P I have justed messed up my boot, so I am thinking about do a clean Xubuntu installation.

---

### Post by dude2425 on 2006-06-05
I've recently fallen in love with pink. It's my new favorite color, and have changed everything green on my desktop to pink. If anybody is interested, I made a usplash in pink. I figured out gimp has a Colormap dialog. Just select the color index, and change the html notation. What I did, I took a screenshot of the colormap dialog, put it in a new image, put a new layer on it painted in a pretty pink color, and set the layers mode to "Color", merged that down, and used the eyedrop tool to get the hex of all 16 colors, and pasted it into the Colormap dialog. Hackish, yes, but at least it worked.

I also made a version without the shadow and glow by changing the four darkest colors to bright white again using the Colormap dialog, penciled over all the white in the image, and changed the colors back so that I didn't screw with the progress bar. It seemed to work pretty well.
Here is my result. If anybody has a problem with it, just say so and I'll try to fix it.

---

### Post by jakev383 on 2006-06-07
I can confirm that in Dapper, I had to add "vga=791" for the splash screen to show. If I didn't have this in there, the screen would stay black until login time.

---

### Post by Bernie01 on 2006-06-10
[QUOTE=mindwarp]I got it to work in dapper by adding vga=791 in my menu.lst file in the part after ro splash vga=791[/QUOTE]


Can somebody please tell me where I will find this file?

---

### Post by Vinze on 2006-06-11
[QUOTE=Bernie01]Can somebody please tell me where I will find this file?[/QUOTE]
/boot/grub/menu.lst

---

### Post by byen on 2006-06-11
[QUOTE=jakev383]I can confirm that in Dapper, I had to add "vga=791" for the splash screen to show. If I didn't have this in there, the screen would stay black until login time[/QUOTE].
I second this. I have tried this in Dapper and this how-to works on Dapper as well. I also had to add vga=791 to the /boot/grub/menu.lst for the splash screen to show up. If you do not know how to add this vga option or where to add it. Here is what you do:
Open the Terminal and type:
```
sudo gedit /boot/grub/menu.lst
```

Search for the part that says 
> defoptions=quiet splash
And add vga=791 to it. So that it looks like 
> # defoptions=quiet splash vga=791
Update grub by typing the following code at the terminal
```
sudo update-grub
```
Restart and Enjoy!
Thanks for this How-to! Good luck Guys!
~byen

---

### Post by byen on 2006-06-11
[QUOTE=Nordoelum]How to change to the Xubuntu splash screen? The weird thing is that I have the Ubuntu splash and the Xubuntu turn off splash :(

How to fix?[/QUOTE]
If you are looking for the default xubuntu splash screen to show up at boot...you might want to see [this]("http://www.ubuntuforums.org/showthread.php?t=113250") 

Hope that helps.Goodluck!
~byen

---

### Post by JasonL on 2006-06-12
After many attempts at trying to get this to work someone from irc pointed me to: [https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)

This guide is totally incorrect, if you follow the wiki page then it will work. The images need to be 640x400. NOT 480!!!

Follow the wiki guide, more likely to work.

---

### Post by Steve S. on 2006-06-13
[QUOTE=SilentCacophony]**EDIT** - dude2425's post above may explain it, so I'd explore that first.

That's odd. I don't see anything in your commands that would be a problem, except possibly the fact that you ran the second gcc step twice for two different ouptut files, but I don't really think that's the problem.

The first two lines following the dpkg-reconfigure look as if dpkg-reconfigure may be acting oddly, but I wouldn't know why it would do that.

If it were me, I might try adding the *--force* option before the linux-image, but the manpage advises that it *could be risky* to use that option, so beware.

In any case, if all else fails, I would think that purge-removing (*sudo apt-get --purge remove usplash*) and re-installing usplash should restore it.

Sorry if I'm not much help, but I've no knowledge of problems with this.[/QUOTE]


Oops!  I did something wrong!  No error messages, no scrolling words, just a black screen when it goes through that point in the boot up process.  Any idea how I can figure out what I did?

---

### Post by groggyboy on 2006-06-14
> After many attempts at trying to get this to work someone from irc pointed me to: [https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)

This guide is totally incorrect, if you follow the wiki page then it will work. The images need to be 640x400. NOT 480!!!

Follow the wiki guide, more likely to work.
I agree.  I couldn't get this HowTo to work, so I ended up using the Wiki HowTo instead.

---

### Post by Steve S. on 2006-06-14
[QUOTE=groggyboy]I agree.  I couldn't get this HowTo to work, so I ended up using the Wiki HowTo instead.[/QUOTE]

Rockin', I'll give it a shot.  I reinstalled usplash and got it back, tried it again, then it wouldn't go, then reinstalled it.  I'll try the wiki.

---

### Post by hakker.de on 2006-06-14
[QUOTE=Vinze]Again, has anyone any idea or a link to a guide on how to set an indexed palette in the GIMP?[/QUOTE]

Changing the color palette in Gimp also changes the colors of the image. Even reducing an RGB image to a 16 color palette image with a custom made palette doesn't retain the order of the indices in the color map (this is at least what I experienced with gimp 2.2.11 in dapper. As a result, you get unexpected colors for text and progress bar.

This is how you can change the order of the colors in the palette:
1. Reduce your image to 16 color palette in Gimp (mode RGB -> indexed, and don't dither the colors).
2. Save it as .xpm.
3. Open the .xpm in a text editor. This is C code and at the top you can see the 16 colors of the palette:
```
/* XPM */
static char * usplash-artwork_xpm[] = {
"640 400 16 1",
"       c #000100",
".      c #2E302D",
"+      c #4E4F4D",
"@      c #CD3134",
"#      c #656663",
"$      c #816631",
"%      c #80817E",
"&      c #C79960",
"*      c #A5A69F",
"=      c #CECB96",
"-      c #C8D973",
";      c #C9CBC8",
">      c #FECD95",
",      c #E3E5E1",
"'      c #F2F4F1",
")      c #FFFECD",
"

```
Each line is a color of the palette, indexed from 0 to 15. Now you can swap lines to your liking, the colors of the image won't change.
4. Convert the edited .xpm to png. Don't do this in Gimp, it will be converted back to RGB mode. This can be done with convert from the imagemagick package (convert -depth 4 usplash-artwork.xpm usplash-artwork.png), but there's a bug in convert and the output is somehow garbled. A work-around is to convert it to .gif first, and then with gif2png into a png, and that's it:
```
convert usplash-artwork.xpm usplash-artwork.gif
gif2png usplash-artwork.gif

```

---

### Post by Steve S. on 2006-06-15
Ok, seriously need help figuring out why I only have a black screen after I follow either this howto or the wiki.

Please tell me if these clues are leading in the right direction and if you know what the heck is going on.  But, I think these clues may help:

The only things that make me question what I am entering (except, of course, the outcome) are these two items.  After I do this:
```
gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
``` I get this:
```
usplash-artwork.c:1330: warning: large integer implicitly truncated to unsigned type
``` repeated over and over again.  Something tells me this isn't good (like that shrewd Linux mind, huh?;) ).

And, at the end, when I run this:
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```
I get this:
```
Not touching initrd symlinks since we are being reinstalled (2.6.15-23.39)
Not updating image symbolic links since we are being updated (2.6.15-23.39)
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-23-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

So, those that know more than I, what does this mean and does that tell you enough to tell me why I can't get this to work?

---

### Post by JasonL on 2006-06-16
What size is your image? It has to be 640x400 NOT 640x480

---

### Post by Steve S. on 2006-06-16
[QUOTE=JasonL]What size is your image? It has to be 640x400 NOT 640x480[/QUOTE]

It is 640x400.

I had some questions, though.  In the wiki, there are times when it referrs to "yoursplash-image" or something like that, so I would put down the picture, but always with the ".png" extention, even though in the wiki sometimes the extension is, say, ".so".  Was that right?  What else have I done wrong?

---

### Post by JasonL on 2006-06-16
No that isnt right, leave the references as yoursplash-image.so and it should work.

---

### Post by sopo_dan on 2006-06-17
i followed the how-to exactly (copy/pasted all the commands) and no error messages were returned at any time but all i get is... a blank screen instead of the splash

---

### Post by JasonL on 2006-06-17
check the image size, it has to be 640x400, NOT 640x480. to check this, right-click the image > properties > image.

---

### Post by Steve S. on 2006-06-18
Ok, it wasn't the image size, but i finally got mine to work.

I was sure it was 640x400, but I opened it up in gimp to check the color and, although I thought it was 16, it turns out it was 256.  Changed that.  

Then following the wiki, I did it all exact cut and paste except for this line.
Where it says "cp yourimage.png usplash-artwork.png" I instead put my artwork in there, a la "cp /home/<my username>/pictures/ublue2.png usplash-artwork.png".  Other than that it was exact cut and paste.

Looks good now!

---

### Post by ayoli on 2006-06-20
woooh, changing my splash and changing to a better screen resol was done in few minute so easy, thx to author of this how-to ;)

---

### Post by HeeZy on 2006-06-28
i got this to work, but my boot screen is small and centered. i use the vga=791 options to get it to show. when i remove it, all i get it a black screen, but it still loads up.

is there a way to stretch the 640x400 boot screen.?

thanx

---

### Post by orgy on 2006-07-02
Here's a counter strike splash i made, pretty simple but i think it looks fine.

---

### Post by pepolez on 2006-07-03
Thread method didn't work, wiki didn't work. Black screen every time. After several tries  - wasting 1 and a half hours, i give up ](*,) 

Lets just hope I can restore it :/

---

### Post by Steve S. on 2006-07-04
[QUOTE=pepolez]Thread method didn't work, wiki didn't work. Black screen every time. After several tries  - wasting 1 and a half hours, i give up ](*,) 

Lets just hope I can restore it :/[/QUOTE]

Hey, pepolez, check my last post...I encountered the same thing until I followed the steps I mentioned.

Not only that, but I've followed it exactly as I mentioned since then on other installs and it worked fine.

Hope it helps.

---

### Post by anubix on 2006-07-06
ok, i tried to put the blu one u provided on after ubuntu upgraded itself to 6.06 (i did it before and it worked fine, upgrade put it back)
now when i re-install it (following ur guide), all i get is a black screen 'till i hit the logon screen.
will this no longer work with 6.06?

---

### Post by rniella on 2006-07-07
Hi, I use dapper too and had to add vga=791 to make it work...during boot time,  HOWEVER, when I shutdown the computer, I`m not getting the splash screen at all, only a blank screen.  Anybody experienced the same ??  best regards and thanks to all !

Reinaldo


> **jakev383 said:**
> I can confirm that in Dapper, I had to add "vga=791" for the splash screen to show. If I didn't have this in there, the screen would stay black until login time.

---

### Post by Steve S. on 2006-07-07
Hey rniella and anubix,

Whether you get the picture from the guide or not, open it in gimp and check to make certain that it is a 16 color photo.  The blue one that was in one of the original howto's was not a 16 color.  I had the black screen too, until I rechecked it.

See a couple of my last posts and see if they help.

It's pretty consistent now that I figured it out (as are most things, I suppose ;-)).  Hope that helps...

---

### Post by heathen on 2006-07-10
ok, even being a total newb to linux, I managed to do this.  However, when loading my image is no longer streatched to match the screen.  This isnt a big deal to me. I have lost my shutdown splash though... any thoughts why? 

I'm using dapper..

---

### Post by rniella on 2006-07-10
Yeap, I did that, reduced the image to 640 x 400 and made sure that it was 16 colors, repeated everything and still dont get the shutdown image... ayways, I think I can live without it, no big deal.. thanks !

RN

> **Steve S. said:**
> Hey rniella and anubix,

Whether you get the picture from the guide or not, open it in gimp and check to make certain that it is a 16 color photo.  The blue one that was in one of the original howto's was not a 16 color.  I had the black screen too, until I rechecked it.

See a couple of my last posts and see if they help.

It's pretty consistent now that I figured it out (as are most things, I suppose ;-)).  Hope that helps...

---

### Post by palintheus on 2006-07-11
I have both the shutdown and startup screens back, they changed to the Kubuntu splash after I installed KDE. Although the starup is now much smaller than before, the shutdown is back to normal.

EDIT : Fixed....I just deleted the vga=791 line.

---

### Post by Narpas on 2006-07-13
Could someone post the .c file for [this]("http://ubuntuforums.org/showpost.php?p=752153&postcount=57")
thread's image? I can't get the png -> c app to work for any files, oddly. Always, the output file is, "Image has too many colors (256)."

Thanks!

---

### Post by Footissimo on 2006-07-18
Just if anyone is confused with the length of this topic..but this is what I did to get the blue usplash to work..

Opened up the original blue usplash image in GIMP - went into the indexed colours dialogue (next to RGB and greyscale and all that) and changed the number of colours to 16.  Cropped off 40 pixel-lines from the top and bottom (to make the image 640x400).  See attached for result.

Did the HOWTO as per normal (just using the new image instead, obviously)

Did a: ```
sudo gedit /boot/grub/menu.lst
```

...and changed ```
# defoptions=quiet splash
``` ..to.. ```
# defoptions=quiet splash vga=791
```

..and it worked lovely. Thank you for the HOWTO and all the people who have worked out the details :)

---

### Post by Steve S. on 2006-07-20
I must say that this thread and the links stemming from it have helped me multiple times.

For example, just did a clean upgrade to Dapper on my parents computer and, instead of the usual Bootsplash, added a picture of their kids...they were very appreciative.;) 

Thanks again...

---

### Post by Polygon on 2006-08-05
> **Jimmy_r said:**
> I made a few from scratch with gimp today...
They work fine in Dapper with boot option vga=0x31b
If i omit the vga line, only the background shows.

(They are not blurry as the previews appear to be) ;)

are you sure that vga line is correct? i tried it and put that vga line in boot.lst and i only get the backround, no ubuntu picture and no text.

---

### Post by ricesteam on 2006-08-06
Failed to get this howto to work.

I copied and pasted the commands and followed the guide exactly.  When I rebooted, there was no splash screen, and although I can hear my system booting up normally, nothing appears on my screen. I couldn't get into the terminal or anything.

In the end I had to reinstall Ubuntu....

I think it has to do with my ATI card/drivers and recompiling the linux-image that messed up my system.

---

### Post by mrmcctt on 2006-08-15
> **Footissimo said:**
> Just if anyone is confused with the length of this topic..but this is what I did to get the blue usplash to work..

Opened up the original blue usplash image in GIMP - went into the indexed colours dialogue (next to RGB and greyscale and all that) and changed the number of colours to 16.  Cropped off 40 pixel-lines from the top and bottom (to make the image 640x400).  See attached for result.

Did the HOWTO as per normal (just using the new image instead, obviously)

Did a: ```
sudo gedit /boot/grub/menu.lst
```

...and changed ```
# defoptions=quiet splash
``` ..to.. ```
# defoptions=quiet splash vga=791
```

..and it worked lovely. Thank you for the HOWTO and all the people who have worked out the details :)

I did have the black screen problems after following the instructions in the original post.  I downloaded the 640x400 image from the post quoted here but I did not have to change my menu.lst.

I now have the boot up and shutdown splash screens.

Could some of these problems be due to widescreen vs. normal screens?  Or was the problem just a matter of the initial images being 256 color instead of 16 color?  I never tried to adjust the original images in the original post to 16 colors and never tried to just resize them to see if they worked.   Just curious.

---

### Post by Steve S. on 2006-08-16
> **mrmcctt said:**
> I did have the black screen problems after following the instructions in the original post.  I downloaded the 640x400 image from the post quoted here but I did not have to change my menu.lst.

I now have the boot up and shutdown splash screens.

Could some of these problems be due to widescreen vs. normal screens?  Or was the problem just a matter of the initial images being 256 color instead of 16 color?  I never tried to adjust the original images in the original post to 16 colors and never tried to just resize them to see if they worked.   Just curious.

In my opinion, most of the problems posted (including mine) were due to the image being 256 and too wide.  As soon as I checked that then made the corrections (gimp is great for both of those)that I did in my last post (which was basically follow the wiki as is except for changing the first line to be where my picture was) it worked, and has worked everytime since on the other systems I configured.  Not only that, but have since used images I've made (with the afformentioned 640x400 and 16 color stipulations) my own and it worked.

---

### Post by kg4dni on 2006-08-17
I'm new to Ubuntu.

I am running Ubuntu Drake Dapper 6.06.

I tried your tutorial to change my boot screen. I don't get the screen to show up but I see all the white-on-black text for the bootup and then I get the Login GUI page.


Any way I can use a GUI program to change the boot screen or can someone help me out with the commands?

---

### Post by phenolholic on 2006-08-17
I followed the commands verbatim and I got nothing. Changed the #defoptions in menu.lst to read
#deftoptions ro quiet splash vga=791

without that, I get the text based bootup. with that, i get a blank screen. can anyone put a finger on what's going on? TIA

---

### Post by mrmcctt on 2006-08-17
To both of these posts

> **phenolholic said:**
> I followed the commands verbatim and I got nothing. Changed the #defoptions in menu.lst to read
#deftoptions ro quiet splash vga=791

without that, I get the text based bootup. with that, i get a blank screen. can anyone put a finger on what's going on? TIA

> **kg4dni said:**
> I'm new to Ubuntu.

I am running Ubuntu Drake Dapper 6.06.

I tried your tutorial to change my boot screen. I don't get the screen to show up but I see all the white-on-black text for the bootup and then I get the Login GUI page.


Any way I can use a GUI program to change the boot screen or can someone help me out with the commands?

The best I can say for both of you is that you need to make sure that the resolution of the image is 640x400 and 16 colors.  The instructions work fine in the original post but the image did not. The image in [I Am The FootIssimo]("http://ubuntuforums.org/showthread.php?t=82835&page=12")'s thread (#114) worked with the instructions in the original post.  I did not have to edit my /boot/grub/menu.lst at all.  Before using the new image I did get the Black and White text-only boot up.  From my experience, the size of the image fixed everything.

I hope this helps because this seems to be working great for me.

---

### Post by Midway on 2006-08-18
I just tried this out but now I just get a black screen at bootup and shutdown.  I got no error messages when I performed each step.

EDIT: N/M I am going to try the above suggestion, didn't see it before.

EDIT2: that did the trick :) sorry about this post, it has been a long day, lol.

---

### Post by phenolholic on 2006-08-18
Okay I saved the image indexed at 16 colors. I reduced its size to 640x400. I followed the instructions on this post. I added vga=791 #defoptions in menu.lst. Still no splash, only a blank screen.

---

### Post by John Jones on 2006-08-20
Hi there.

After following your instructions to the letter, I ended up with a blank screen right up to the login screen. I got the brownness back by following the instructions to reinstate the original colour, so that worked okay.

Presumably, as it's worked for other people, it's something I've done wrong, but I have no idea what that might be (still a relative noob).

I'm trying this on Ubuntu 6.06; could that have any bearing on the problem?

Please help an aging noob.

Cheers,

John :-?

---

### Post by John Jones on 2006-08-20
Message removed.

John

---

### Post by macstevejb on 2006-08-21
I tend to agree with the poster above....I followed all the steps but I just get a blank screen on both logging-out and rebooting.

I too am using Ubuntu LTS 6.06.1 (a brand new installation at that)...is it something to do with the newer kernel perhaps?

:???:

---

### Post by vamsidhar on 2006-08-24
will all these stuff work for 6.06 when i tried to do it.It showed up nothing just a black screen.what can i do....](*,)

---

### Post by Jaxilian on 2006-08-25
> **SilentCacophony said:**
> I wrote this HOWTO because I've noticed that myself and some other people have trouble reading the default usplash screen, and also because I wanted mine to be blue. ;) I've included a few files as attachments, one for the default brown usplash, one that's color-shifted to be blue, and one with a custom olive palette. All are optimized for brighter text and a more obvious progress bar background, and each will still use the default red failure color for failed steps.

This HOWTO was derived from the wiki page found at [https://wiki.ubuntu.com/USplashCustomizationHowto]("https://wiki.ubuntu.com/USplashCustomizationHowto") , but modified for a bit more user-friendliness (I hope,) and to accomodate ease of use with the files that I made. This was written with usplash (0.1-22) in mind, as future versions of usplash may be subject to change.

If you wish to try one of the usplash image replacements that I have attached below, the process takes only a few minutes, and is relatively painless. Note that step one, installing the *gcc* and *libbogl-dev* packages, may install a few development packages as dependencies, and may take awhile on dial-up connections.

Download either the [COLOR="Brown"]usplash-fix.png[/COLOR], [COLOR="Blue"]usplash-blue.png[/COLOR], or [COLOR="Green"]usplash-olive.png[/COLOR] (see attachments at the bottom of this post) file to your ~/ (home) directory, and open a terminal (it should start you in your ~/ directory, but enter **cd ~/** if you're not sure.) Then follow these steps:

**_1. Install the GCC and BOGL packages needed:_**

```
sudo apt-get install gcc libbogl-dev
```

**_2. Enter *only* the line below that matches whichever file that you downloaded:_**

```
[COLOR="Brown"]cp usplash-fix.png usplash-artwork.png[/COLOR]
[COLOR="Blue"]cp usplash-blue.png usplash-artwork.png[/COLOR]
[COLOR="Green"]cp usplash-olive.png usplash-artwork.png[/COLOR]
```

**_3. Now enter each of these steps to build your usplash:_**

```
pngtobogl usplash-artwork.png > usplash-artwork.c
gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
gcc -shared -Wl,-soname,usplash-artwork.so usplash-artwork.o -o usplash-fix.so
```

**_4. Copy your usplash to the usplash directory and create a new link to it:_**

```
sudo cp usplash-fix.so /usr/lib/usplash/usplash-fix.so
sudo ln -sf /usr/lib/usplash/usplash-fix.so /usr/lib/usplash/usplash-artwork.so
```

**_5. Regenerate the initramfs:_**

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

[COLOR="Red"]*** EDIT *** - Please note that the output of the last step may include the message *"splash image... none found, skipping..."*, which does not affect **usplash** in any way. It is a function of the /sbin/update-grub script which is executed while reconfiguring the linux-image package, and only displays if you've never previously set up the *optional* **grub** splash image, which would display *before* usplash would, and is an entirely separate splash image meant for the grub menu alone.[/COLOR]

**DONE!** The resulting usplash file will be **/usr/lib/usplash/usplash-fix.so**, and the next time you boot ubuntu, you should see the new usplash.


You'll be left with 4 extra files that you can delete in ~/ if you wish:

```
rm usplash-artwork.o usplash-artwork.c usplash-artwork.png usplash-fix.so
```


If you change your mind, then you can revert it back to the default usplash, by following these steps:

```
sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)
```


If you're interested in further modifying your usplash, and wish to know what I did, here's a summary:

* Downloaded the source, available from this page: [http://packages.ubuntu.com/breezy/misc/usplash]("http://packages.ubuntu.com/breezy/misc/usplash")
* Took the original usplash-artwork.png file and swapped the palette entries to increase the visibility of entries 2, 4, and 8 (described below.) Swapped 2 with 7, then 4 with 7, and 8 with 9. Saved the resulting file as usplash-fix.png.
* For the usplash-blue.png, I simply hue-shifted the entire palette of the usplash-fix.png so that thier RGB values swapped the R and B values.


Guidelines for the image format:

* The PNG must be: 640x480 16 colours.
* Some palette entries are used for particular purposes:

```
Palette Index | Used For
-----------------------------------------
0             | Background color
0             | Text background color
1             | Progress bar foreground color
2             | 'Ok' text foreground color
4             | Progress bar background color
8             | Description text foreground color
13            | 'Failed' text foreground color
```


The attachments (right-click > Save Link As...):

[COLOR="Brown"]Brown:[/COLOR]
[usplash-fix.png]("http://www.ubuntuforums.org/attachment.php?attachmentid=3197&stc=1&d=1130425734")
[ATTACH]3197[/ATTACH]

[COLOR="Blue"]Blue:[/COLOR]
[usplash-blue.png]("http://www.ubuntuforums.org/attachment.php?attachmentid=3198&stc=1&d=1130425734")
[ATTACH]3198[/ATTACH]

[COLOR="Green"]Olive:[/COLOR]
[usplash-olive.png]("http://www.ubuntuforums.org/attachment.php?attachmentid=3211&stc=1&d=1130475124")
[ATTACH]3211[/ATTACH]



omfg! all that to just change the usplash???? what happened to just edit a file and be done with? ](*,)

---

### Post by Steve S. on 2006-08-25
I tried this again, and it worked again.

I'll give my comments again, in hopes that it will help.

Use [the wiki]("https://help.ubuntu.com/community/USplashCustomizationHowto"), it works.

Except for one line, I cut and pasted without ANY modifications...just straight cut and paste.  The line I changed is the first line where it says to cp yourimage.png usplash-artwork.png.  The only part I changed on this line was the "yourimage.png" to where my image actually was (for example, /home/username/splashimage.png).  Oh, and one line in the wiki is very long, so make sure you paste the entire line after copying all of it (#4 in the wiki).

Before doing this, I opened my image (whatever I wanted) in Gimp.  In gimp, I changed the size to 640x400, and I selected under Mode>RGB then made it 16 colors rather than 256.  I have done this a few times with pretty much whatever image I wanted, as long as it had those stipulations.

I hope this helps.  At this point, I save the wiki in my bookmarks and change the boot splash whenever I want (although I like my current one the most and may keep it a while :cool: ).  It usually takes me maybe 15 minutes, if I make the picture myself or make heavy modifications.

I really hope that helps some as the wiki has been nothing but helpful for me.

---

### Post by krazed nun on 2006-08-31
check out my usplash image

---

### Post by phenolholic on 2006-09-01
> **flodis said:**
> omfg! all that to just change the usplash???? what happened to just edit a file and be done with? ](*,)

omfg! all this quoting just to write that? editing a file and being done with it ended with ms windows.

---

### Post by opticyclic on 2006-09-01
But for those people that want to just point and click you could just use my kommander script....
[http://ubuntuforums.org/showpost.php?p=969844&postcount=69](http://ubuntuforums.org/showpost.php?p=969844&postcount=69)

---

### Post by Steve S. on 2006-09-02
> **krazed nun said:**
> check out my usplash image

Very cool!

---

### Post by distroman on 2006-09-09
I ended up with a black screen, so I can say that revert work well. 

Thank you, that did it for me. 
> **Footissimo said:**
> Just if anyone is confused with the length of this topic..but this is what I did to get the blue usplash to work..

Opened up the original blue usplash image in GIMP - went into the indexed colours dialogue (next to RGB and greyscale and all that) and changed the number of colours to 16.  Cropped off 40 pixel-lines from the top and bottom (to make the image 640x400).  See attached for result.

Did the HOWTO as per normal (just using the new image instead, obviously)

Did a: ```
sudo gedit /boot/grub/menu.lst
```

...and changed ```
# defoptions=quiet splash
``` ..to.. ```
# defoptions=quiet splash vga=791
```

..and it worked lovely. Thank you for the HOWTO and all the people who have worked out the details :)
Maybe it would be worth to mention, that it changes your kernel name, you just change it back, no big deal, but why not tell?

ps
go to post #114 for the **usplash-blue.png**

---

### Post by statue on 2006-09-12
Thanks for writing this how to, it works great. Might want to add in the grub.lst menu edit though  as dapper drake needs it.

---

### Post by eklypse on 2006-09-20
When I run:

**sudo dpkg-reconfigure linux-image-$(uname -r)**

I get the following error:

[B]Package `linux-image-2.6.17.13' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-image-2.6.17.13 is not installed[/B]

What can I do to fix this?  Thanks in advance.

---

### Post by Invoker on 2006-09-20
> **Footissimo said:**
> Just if anyone is confused with the length of this topic..but this is what I did to get the blue usplash to work..

..and it worked lovely. Thank you for the HOWTO and all the people who have worked out the details :)

Thank you this works :) And everyone else.

---

### Post by petrhos on 2006-09-25
When i do this tuturial i get my boot screen just black :(

---

### Post by adipl on 2006-09-27
The images in the initial post are not correct. As mentioned above go to post #114 for the usplash-blue.png

---

### Post by BreakDecks on 2006-10-15
I made a script to help with installing custom boot screens.  I'm not all that great at Shell Scripting, but it works.

```

#!/bin/sh
if [ $1 = "-h" ]; then
	clear
	echo "convert.sh <FILENAME> [y/n]"
	echo "y: modify grub menu.lst"
	echo "n: do not modify grub menu.lst"
	exit 127
fi
CONTINUE="yes"
if [ $USER != "root" ]; then
	sudo -K
	CONTINUE="no"
	echo "enter your sudo password"
	sudo echo "logged in as root"&&CONTINUE="yes"
fi
if [ $CONTINUE = "yes" ]; then
	echo "Logged in as root"
	echo "Proceeding:"
	echo "Copying to placeholder"
	cp -v $1 usplash-artwork.png
	echo "Converting to C"
	pngtobogl usplash-artwork.png > usplash-artwork.c
	echo "Compliling:"
	echo "Step 1"
	gcc -v -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
	echo "Complete!"
	echo "Step 2"
	gcc -v -shared -Wl,-soname,usplash-artwork.so usplash-artwork.o -o yourimage-splash.so
	echo "Complete!"
	echo "Creating directory"
	sudo mkdir -p /usr/local/lib/usplash/
	echo "Copying Shared Library"
	sudo cp -v yourimage-splash.so /usr/local/lib/usplash/yourimage-splash.so
	echo "Installing splash screen"
	sudo update-alternatives --verbose --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/yourimage splash.so 55
	echo "Configuring usplash"
	sudo update-alternatives --verbose --config usplash-artwork.so
	echo "Reconfiguring Linux image"
	sudo dpkg-reconfigure linux-image-$(uname -r)
	if [ $2 = "y" ]; then
		echo "Launching gedit"
		echo "Find line # defoptions=quiet splash"
		echo "Add vga=#"
		echo "785 = 640x480"
		echo "788 = 800x600"
		echo "791 = 1024x768"
		echo "794 = 1280x1024"
		echo "Grub will be updated upon exiting gedit"
		sudo gedit /boot/grub/menu.lst
		echo "Updating Grub"
		sudo update-grub
	fi
	echo "Boot Splash Screen changed successfully"
fi
if [ $CONTINUE = "no" ]; then
	echo "failure"
fi
if [ $USER = "root" ]; then
	exit
fi
sudo -K
exit

```

---

### Post by SilentCacophony on 2006-10-16
Thanks to those who continued to help in this thread. Hopefully at some point it'll be easier and less problematic to do such a seemingly trivial operation. :)

I've been away so long because after buying a new computer a while back, I had been unable to get ubuntu to install on it, even after searching through the wealth of information here.

I find myself grudgingly but suprisingly satisfied with the Windows XP that resides on it now. I had used Windows 98, Ubuntu, and Debian before, and I do miss the linux that so reminds me of my Amiga OS days. I'm sure I'll get ubuntu back on here, perhaps next release, but in the meantime I've added a bit of a disclaimer to the original post, suggesting the wiki here:

[https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")

Good luck to all those who dare to make their computer in their own image. :)

---

### Post by fsanguinetti on 2006-10-21
Hi, 

I use Ubuntu Dapper 6.06 and had a problem with changes in the usplash color. I made all instructions step by step and nothing. I tried to change from default color to blue, but when I restarted my pc the usplash had disappeared and it didn't come back more. I also tried to do a revert process with explain here without sucess. It will be that I corrupted the usplash-artwork.so or something it type? :confused: :confused: 

Help me please :( :( :( :( :(  !!!!! thanks

Fabricio

---

### Post by digitalghost1 on 2006-10-28
> **testube_babies said:**
> As long as you change your boot parameters to include vga=791.  [Read on...]

Explain what you mean a little more. I'm running Dapper too, and I ran into the same issues as some of the others after applying the steps with the Blue Usplash, then it not displaying at all and then just seeing my login window. I'm a total newb to Linux in general but I have been pleasantly surprise at how well Ubuntu works and how much support there is for it. Thanks for your time.

---

### Post by jackschmidt on 2006-11-15
I have spent numerous hours reading the wiki, reading this thread, reading all the GIMP info... 640x400,1024x768, grub settings, 16-bit color... sometimes 15 bit color... on Dapper.  I've used that xpm imagemagick thing, Paintshop Pro... and of course, GIMP and I can say only one thing to all of this.

None of it works.  Nobody can seem to offer me something that works.  I can only use the default splash screen but making my own images never ever works.  I am very very frustrated and pissed at this usplash module which just refuses to do what I want.  Somebody tell me the accurate information of how to do it because my brain is about to explode.

---

### Post by Steve S. on 2006-12-13
I have used this thread multiple times in dapper and it has worked like a charm.

Haven't tried the script yet, but might give it a try.

The "might" comes from the fact that I just upgraded to Edgy and it seems the upgrade went well.

Some things to iron out (like no wireless suddenly) but I want to know (from this thread) if there is anything different that I need to do for Edgy to get my specialized boot screen back.

Any comments?

---

### Post by Steve S. on 2006-12-14
Anyone?  Anyone tried it in Edgy?  Works the same?

Edit:
Never mind...saw the edit/repost at the beginning.  Thanks.

---

### Post by linkrjr on 2007-02-05
HI SilentCacophony,

I have been trying to get this set up on my laptop but for a strange reason it just does not work.
I did all the steps you posted and when I restart, the default usplash is gone but the new one does not appear.
I just get a black screen.

Any idea of what can be happening?

thanks

---

### Post by Steve S. on 2007-02-06
> **linkrjr said:**
> HI SilentCacophony,

I have been trying to get this set up on my laptop but for a strange reason it just does not work.
I did all the steps you posted and when I restart, the default usplash is gone but the new one does not appear.
I just get a black screen.

Any idea of what can be happening?

thanks

What version of Ubuntu are you using?  If you are using Dapper, then I found the Wiki to work pretty consistently.

I found Edgy needed a little more tweaking/different approach.  Check my last few posts [on this thread ]("http://www.ubuntuforums.org/showthread.php?t=323520")and/or [this additional thread ]("http://www.ubuntuforums.org/showthread.php?t=334428")where I give an example of what I did for the Edgy usplash....

Post back if that helped at all...:)

---

### Post by robbie75 on 2007-02-10
Hi everybody,

I tried many times to change my usplash but with no luck...
Then I've found that, at least for my Dapper Drake, the splash
has to be 640x400 so I finally got it working.
Anyway you can test your setup without have to reboot,
simply type
```
$ sudo usplash -u 
```

and you'll see immediately if your splash is working;
or, if it's not, you can read the error messages and try
to fix them.
Then hit CTRL-ALT-F7 to switch back to your session.

Moreover, I think it's better to set up your usplash by update-alternatives
as in: [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)
instead of overwriting the pristine symlink. ;)

---

### Post by dorcssa on 2007-02-19
Ok, I tried everything, with 640*400 too, but it's all the same,there's a blank screen at startup, and when I write sudo usplash -u, it's say segment failure(I hope I translate it well). I write down the steps I made, in case I did something wrong. 

```

cp usplash-blue.png usplash-artwork.png
pngtobogl usplash-artwork.png > usplash-artwork.c
gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
gcc -shared -Wl,-soname,usplash-artwork.so usplash-artwork.o -o usplash-blue.so
sudo cp usplash-blue.so /usr/lib/usplash/usplash-blue.so
sudo ln -sf /usr/lib/usplash/usplash-blue.so /usr/lib/usplash/usplash-artwork.so
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/usplash-blue.so 55
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)

```

Then I made some changes to grub, at this line: # defoptions=quiet splash. I wrote vga=785, but in the 640*400 case I didn't know what to write here, so leave it.

---

### Post by robbie75 on 2007-02-19
For me vga=792 worked...
BTW if sudo usplash -u returns errors I think it'll be impossible
to get usplash working....
You should get usplash working with no errors from the
command line before.

Good luck :)

---

### Post by dorcssa on 2007-02-19
> **robbie75 said:**
> For me vga=792 worked...
You should get usplash working with no errors from the
command line before.


And how do I do that? I told the error message, but don't know what to do with it. :(

---

### Post by Steve S. on 2007-02-19
> **dorcssa said:**
> And how do I do that? I told the error message, but don't know what to do with it. :(

Well, you could always uninstall then reinstall usplash from Synaptic Package Manager in System>Administration...might be a good place to re-set then figure out what is going on.

---

### Post by samstar on 2007-05-16
Hi everyone,

I have a somewhat unique situation here.  First, allow me to bring you up to speed on it.

I am setting up an old sony vaio with the new Ubuntu feisty.  This is for a relative to help her learn Linux.  I wanted to change the usplash to the blue Ubuntu splash, to fit the rest of my customizations.

All three default usplash themes (Kubuntu, Ubuntu, and Xubuntu) can start up properly, and I can switch between them at any time.  Note: in order for these to work, I need to make my resolution 800x600 in the /etc/usplash.conf file.

However, when I use the instructions here to make my own usplash.so file, the bootup attempts to load it, then reverts to the verbose console, and prints an error that it can't find a usplash 800x600 theme.

I made sure the my usplash-blue.png file is 640x400, and at 16 colors.  I also tried it at 640x480 just in case.

A note on my video hardware: I CANNOT use any vga= boot parameters.  Regardless, as I said above, the default usplash themes work just fine.

I was comparing the size of the usplash.so files I was generating, and the default .so files, and there's a huge difference in size.  The defaults are over 2 mb, and the ones I generate are about 34 kb large.  Do the default usplash files contain program that will let them run without a specified framebuffer resolution?  Is there a way I can add that support to the usplash files I am generating with the instructions here?

Any help would be appreciated,
Sam

---

### Post by samstar on 2007-05-18
Well, nevermind.  I'm installing the Ubuntu Studio packages, and using their cool usplash theme.

---

### Post by boob11 on 2007-08-19
Thanks,

---

### Post by canonicalfreak on 2008-09-02
:popcorn::guitar::lolflag:biggrin::biggrin::biggrin::biggrin::wink::wink::lol:

---

### Post by mabb on 2008-09-03
Hi for all,

I have downloaded usplash-theme-ubuntu_0.18.tar.gz file and then changed just the pictures of it ( usplash_xxx_yyy.png (s)) to use same c and Makefile files, and then i did the following:

$ cd usplash-theme-ubuntu_0.18
$ make 
in this step gives me many messages like this:
usplash_640_480.png.c:11024: warning: large integer implicitly truncated to unsigned type

for all pictures, and after that when i put .so file by Startup Manager and restarted the laptop there is not any Usplash,

Can one help me ?

Thanks in advices,

---

### Post by Joe Kuan on 2009-06-02
First of all,

   Startup-Manager is for users to quickly configure the boot relationship between GRUB and usplash, ie you choose what boot resolution, what theme to use, password etc. You can still go through this route but IMHO it is time consuming.

   Ideally, what you want to do is to constantly 'experimenting' your new splash theme look without rebooting the box.

   So what you want is the command line 'usplash' and 'usplash_write', so u can start and stop the usplash and choose which theme (resolution) to load, progress bar, colour, positioning, etc

   Hope this will help. [http://joekuan.wordpress.com/2009/06/02/how-to-easily-experiment-your-new-usplash-theme-from-a-terminal/]("http://joekuan.wordpress.com/2009/06/02/how-to-easily-experiment-your-new-usplash-theme-from-a-terminal/")

PS: If you get blank screen, here are couple clues.

1) Your splash PNG image hasn't got 8 bits colormap. See [http://joekuan.wordpress.com/2009/05/26/how-to-create-8-bit-colormap-png-image-for-usplash/]("http://joekuan.wordpress.com/2009/05/26/how-to-create-8-bit-colormap-png-image-for-usplash/")

2) Make sure the index of the color in the theme.c is within the image colormap. Use GIMP to inspect.

Hope this helps

Joe

---

