---
title: "PART 1: Customizing the graphics in Grub, Usplash, Xsplash and GDM."
date: 2010-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by towheedm on 2010-04-03
[SIZE=3][B]UPDATE:

[/B]This tutorial has become too large to post on the forums.  I have instead created a 58 page PDF file comprising the entire tutorial.  The tutorial includes screenshots and sample files that can be used for testing.  All of the files, including the PDF file are archived in a .tar.gz file.  It can be downloaded from this link:

[/SIZE][http://www.mediafire.com/file/2yimyo3ow3t/ubuntu_customization.tar.gz](http://www.mediafire.com/file/2yimyo3ow3t/ubuntu_customization.tar.gz)
[SIZE=3]
This is my first tutorial, so any comments is appreciated.  I will leave Part 1 posted but any questions and or comments on any part of the tutorial can be posted in this thread.
[B]
DISCLAIMER:[/B][/SIZE]

The procedures outlined below have been tested ONLY on Karmic. There is no guarantee that they will work on other versions of Ubuntu. If you decide to test on other versions, YOU DO SO AT YOUR OWN RISK. A lot of the customization is carried out at the command line and involves directly modifying system files. Of course, we all know the dangers associated with such actions, so if your system gets screwed, refuses to boot, catches afire, runs away or goes to sleep and never wakes up again, DO NOT BLAME ME. You have been FORE-WARNED.

With all the prelimanaries out of the way, put on the coffee, send the kids to bed, put out the dog, kiss the wifey good-nite and let's get cracking.

[SIZE=3]**INTRODUCTION**[/SIZE]

In my quest to fully customize the graphics in Ubuntu 9.10 (Karmic Koala) starting fom the Grub menu and working my way up to the desktop I've found bits and pieces of informations scattered throughout the threads. Most of these were not geared towards people new to Karmic. Also, a lot of the customization were not thorough enough, I wanted to do a lot more than what was given. This is when I decided to test the waters of customizing Karmic. The learning curve was very steep because I am also a beginner to Karmic and Linux on the whole. I decided to put everything I've learnt into what I hope will be a very comprehensive guide on customizing the graphics screens of Karmic starting from the Grub menu.

This guide is written for beginners and so the more experienced users may fnd it a bit repetitive. Some may even say that there are programs available that allows you to do the customizations easily, but I've found that such programs just scratches the surface of what's possible.

Open a Terminal window by clicking on Applications => Accessories => Terminal. Most of the commands that's used start with the [COLOR=Red]sudo[/COLOR] command. [COLOR=Red]Sudo[/COLOR] allows us to run a command with root privileges. For more information on [COLOR=Red]sudo[/COLOR], open the Ubuntu Help Center and type '[COLOR=Blue]man sudo[/COLOR]' in the search box or have a look at the following links:

[http://ubuntuforums.org/showthread.php?t=261204](http://ubuntuforums.org/showthread.php?t=261204)
[http://ubuntuforums.org/showthread.php?t=723263](http://ubuntuforums.org/showthread.php?t=723263)
[http://ubuntuforums.org/showthread.php?t=292094](http://ubuntuforums.org/showthread.php?t=292094)
[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

Throughout this document, whenever I back-up fles, I append '[COLOR=Red]_orig[/COLOR]' to the original names. This applies to both files and directories. You may rename them whatever you like but, please try to be consistent.

Gedit is used as the text editor throughout this document but, if you are more comfortable using another editor then please do.

The different graphic screens during the boot-up sequence occur in this order:

grub => usplash => xsplash => gdm (login screen) => xsplash => desktop

I will go through the procedures for customizing each of these, starting with Grub.

BTW, the graphics are meant to educate not entertain, so please. :mrgreen:

Finally, this tutorial has become too long to put into one post, so it's split up into four parts:

Part 1:  Customizing the graphics in Grub (shown in this post)
Part 2:  Customizing Xsplash
Part 3:  Customizing the graphics in GDM
Part 4:  Customizing Usplash


**[SIZE=3][COLOR=Blue]PART 1:[/COLOR] Customizing the graphics in GRUB[/SIZE]**

The procedure listed below changes the Grub menu colors and adds a background image (Grub wallpaper). It was tested on Grub 1.97~beta4 [COLOR=Red]ONLY[/COLOR].

First, back-up the files that will be modified. The three files that will be modified are:

[LIST=1]
[*]/etc/grub.d/05_debian_theme
[*]/etc/grub.d/00_header, and
[*]/etc/default/grub
[/LIST]
 Enter the following commands in the Terminal window:
```
sudo cp /etc/grub.d/05_debian_theme /etc/grub.d/05_debian_theme_orig
sudo cp /etc/grub.d/00_header /etc/grub.d/00_header_orig
sudo cp /etc/default/grub /etc/default/grub_orig
```To restore the original files, enter the following commands:
```
sudo cp /etc/grub.d/05_debian_theme_orig /etc/grub.d/05_debian_theme
sudo cp /etc/grub.d/00_header_orig /etc/grub.d/00_header
sudo cp /etc/default/grub_orig /etc/default/grub
```**Menu Colors:**

The text colors for Grub's menu are specified in the 05_debian_theme file. Open this file for editing with gedit:
```
gksudo gedit /etc/grub.d/05_debian_theme
```Locate the following two lines at the beginning of the file:
```
set menu_color_normal=white/black
set menu_color_highlight=black/white
```The color format is: foregroundcolor/backgroundcolor. For a list of possible colors that can be used, have a look at:
[http://www.gnu.org/software/grub/manual/html_node/color.html#color](http://www.gnu.org/software/grub/manual/html_node/color.html#color)

Set the menu colors to green text on a black background and reverse it for the selected item in the menu:
```
set menu_color_normal=green/black
set menu_color_highlight=black/green
```Save the changes and exit gedit. Grub must be updated for the changes to take effect.

Enter this command in the Terminal window:
```
sudo update-grub
```This updates the /boot/grub.cfg file. Reboot to see the new menu colors. Here's a screenshot of what it looks like.

[attach]152220[/attach]

Notice the Grub title and help text are still white. To change these colors, do the following:

Open /etc/grub.d/05_debian_theme for editing:
```

gksudo gedit /etc/grub.d/05_debian_theme
```Add the following line (shown in red) beneath the set menu_color_highlight line:
```
set menu_color_normal=green/black
set menu_color_highlight=black/green
**[COLOR=Red]set color_normal=green/black[/COLOR]**
```The beginning of the /etc/grub.d/05_debian_theme file should now look something like this:
```
set_mono_theme()
{
  cat << EOF
set menu_color_normal=green/black
set menu_color_highlight=black/green
set color_normal=green/black
EOF
}
```Save the changes and exit gedit. Update Grub to reflect the changes.
```
sudo update-grub
```Reboot to see the changes.

Now that we can change the menu colors, let's add a backgound image.

**Background:**

Grub's default screen dimension is 640x480. Grub does not scale the background image to fit the screen's dimension so the image used should have the same size as the screen's dimension. At this point in the tutorial, copy the image file to /usr/share/images/desktop-base/moreblue-orbit-grub.png. Grub wll accept either a png or tga format image file.

Assuming your image file is in your Documents directory and named mygrubimage.png, enter (in the Terminal window):
```
sudo cp ~/Documents/mygrubimage.png /usr/share/images/desktop-base/moreblue-orbit-grub.png
```Grub can also use a different menu color when a background image is displayed. Open /etc/grub.d/05_debian_theme for editing and locate the following lines:
```
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
```Change the colors:
```
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=green/black
  set color_highlight=black/blue
else
```Save the changes, exit gedit and update Grub to reflect the changes:
```
sudo update-grub
```Can I use images from another directory? Yes, you can. This is how it's done:

Open /etc/grub.d/05_debian_theme for editing and locate the line:

```
for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga} ; do
```Add the directory with the image to this line like this (assuming that the name of the directory is /home/towheed/Documents/images):
```
for i in {/boot/grub,/usr/share/images/desktop-base[COLOR=Red],/home/towheed/Documents/images[/COLOR]}/moreblue-orbit-grub.{png,tga} ; do
```Next, assuming the name of the image is shaded.png, replace moreblue-orbit-grub with shaded. The line should now look similar to this:
```
for i in {/boot/grub,/usr/share/images/desktop-base,/home/towheed/Documents/images}/[COLOR=Red]shaded[/COLOR].{png,tga} ; do
```Remember, the dimensions of the image file must be 640x480.

Update Grub to reflect the changes.
```
sudo update-grub
```Reboot to see your new background.

Grub can use images of different dimensions for its background. Before this is done though, the video mode that Grub uses must be changed. Grub may not necessarily support all of the video modes of a particular graphics card. To determine which modes Grub support, follow this simple procedure:

[LIST=1]
[*]    Reboot
[*]    When the Grub menu shows, press 'c' to go the Grub command line. Your prompt should be '[COLOR=Red]sh.grub>[/COLOR]'.
[*]    At the prompt type 'vbeinfo'. A list of video modes will be displayed.
[*]    Take note of the mode you would like to use, i.e.: 1024x768, 1280x1024 etc.
[*]    Press <ESC> to return to the menu.
[*]    Boot your menu choice and continue from below.
[/LIST]
  Open /etc/default/grub for editing:
```
gksudo gedit /etc/default/grub
```Locate this line:
```
#GRUB_GFXMODE=640x480
```The hash (#) symbol indicates this line is a comment. Uncomment the line by deleting the hash and replace the 640x480 with the mode that you noted in Step 4 above. If 1024x768 was chosen the line should look like this:
```
GRUB_GFXMODE=1024x768
```Grub will now use this video mode and an image this size can now be used for the background.

When finish editing, save the file, close gedit and update Grub. Reboot to see the menu and background image in the new video mode.

If after rebooting, the menu is still shown at 640x480, the file /etc/grub.d/00_header must be edited.

Open the file for editing:
```
gksudo gedit /etc/grub.d/00_header
```Locate the following line:
```
  set gfxmode=640x480
```Change it to:
```
  set gfxmode=[COLOR=Red]${GRUB_GFXMODE}[/COLOR]
```Save the file, close gedit, update Grub and reboot.

NOTE: Whenever we modify these files (or any of Grub's configuration files) we must update Grub for the changes to take effect.

For those interested in customizng other aspects of Grub take a look here:
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=add+menu+entries+grub](http://ubuntuforums.org/showthread.php?t=1195275&highlight=add+menu+entries+grub)
[SIZE=3]
[/SIZE]

---

### Post by towheedm on 2010-05-07
I see the file has been downloaded 85 times.  Anyone care to post any comments or remarks?  I am thinking of expanding it to include Lucid and Plymouth.  I would like to know whether there's enough interest in it before I invest any time into it.

Thanks.

---

### Post by 9tails on 2010-05-08
Thanks towheedm! Your guide is very well written and easy to follow. I've been looking for months for info on how to customize the new evil GDM and almost gave up... until someone sent me a link to your guide =D>

Now i can avoid the useless gdm2setup...

---

### Post by towheedm on 2010-05-10
[QUOTE=9tails]Hi, I followed your guide and was able to fully customize my Lucid-based system to my liking, so THANKS for your work!

I was wondering if there is a way to change the system name appearing below the icon on the login screen (just above the optional banner message). I don't want to change my system's name, I just need a way to specify a different message. Do you know if it is possible?

Oh and if there is a way to hide the bottom bar (on the login screen) it would be awesome :)[/QUOTE]

To answer your first question, there is no easy way to change this message.  This message has two values: the computer's name and the OS version.  You can click on the message to toggle between these two values.  Unfortunately, both are hard coded into the simple-greeter source code.  I looked into this when I was writing the guide and the only way I could see of changing this would be to re-code GDM.  Not a simple task for the average user.

The bottom bar is the panel, similar to the panel on your desktop.  I'm not sure about this one, but again, it appears to be hard coded into GDM.  This is at the top of my TODO list because I would also like to get rid of the panel.  A work around though might be to make it completely transparent using Compiz.  I have not put much effort into it though as I've been testing Lucid.

Thanks again for your wonderful comments.

---

### Post by 9tails on 2010-05-11
Hi towheedm, thanks for your reply.

I saw there was an option in the gdm configuration to specify a different welcome message, at least according to [http://projects.gnome.org/gdm/docs/2.14/configuration.html](http://projects.gnome.org/gdm/docs/2.14/configuration.html)

So I added a [greeter] section to /etc/gdm/custom.conf and used DefaultWelcome = false and Welcome = SOMETHING, but I guess it's only for older GDMs as it didn't work :(

Even the "OS version" message is hardcoded instead of reading /etc/issue dynamically. Unbelievable.

I'm tempted to alter the source code of GDM 2 and recompile it, but then again perhaps it's not a good idea as this new GDM is probably going to receive lots of updates and bugfixes (or at least I hope so... the new gdm is ugly!)

---

### Post by towheedm on 2010-05-11
Yes, version 2.28 is completely different than previous versions when it comes to theming.  One way I tried to change the simple-greeter window was to build a completely new simple-greeter.  Unfortunately, most of the objects in the simple-greeter are controlled by the simple-greeter source code.  These cannot be left out because when GDM looks for them and cannot find them, it simple hangs.  Even naming the objects the same and hiding them is useless bacause GDM shows then when it needs to.

Let's say for instance, you've disabled the user list.  You may noticed that GDM prompts you first for your username and then for your password using the same input box.  That's bacause there's only one text entry box named '[COLOR=Red]auth-input-box[/COLOR]' in the simple-greeter that GDM uses to collect authentication information.  So you cannot create a greeter with seperate username and password entry boxes.

So again, to redo the simple-greeter would involve modifying the simple-greeter.c source code file.  My present knowledge (or lack of it) of GTK2.0 controls prevents me from taking this further.

---

### Post by 9tails on 2010-05-12
> **towheedm said:**
> So again, to redo the simple-greeter would involve modifying the simple-greeter.c source code file.  My present knowledge (or lack of it) of GTK2.0 controls prevents me from taking this further.

Anyway as I said before I don't think it would be worth the trouble. In its present state the new GDM looks more like an alpha release than a finished product. No wonder there are lots of discussions around on how to downgrade to the older version. I guess it's going to be improved and functionality (e.g. theming) is going to be added, but that means we'd have to patch its code again and again, so I think I'll just wait for now.

---

### Post by BOFH+ on 2010-05-17
> **towheedm said:**
> To answer your first question, there is no easy way to change this message.  This message has two values: the computer's name and the OS version.  You can click on the message to toggle between these two values.  Unfortunately, both are hard coded into the simple-greeter source code.  I looked into this when I was writing the guide and the only way I could see of changing this would be to re-code GDM.  Not a simple task for the average user.

compiling gdm needs all sorts of -dev libraries and i really don't want to install them on my pc... however i would REALLY appreciate an edited version of the gdm-binary... one that lets you choose a string to display instead of your hostname, or at least one that doesn't show the distro name when you accidentally click on it.

thanks from me too for the awesome guide!

---

### Post by earther on 2010-05-17
> **towheedm said:**
> I see the file has been downloaded 85 times.  Anyone care to post any comments or remarks?  I am thinking of expanding it to include Lucid and Plymouth.  I would like to know whether there's enough interest in it before I invest any time into it.
Just downloaded.  Am impressed with what you have compiled in the PDF.  I had all this worked out for previous distros - Grub, Usplash, GDM etc. - but now will have to start from scratch if I want to go with Lucid.  Very frustrating.  But at least with your guide, I should eventually be able to do the customizations I want.  In the meantime, I think I'll be sticking with Hardy until Lucid's kinks (and there are MANY) get worked out.

---

### Post by JohnnyC35 on 2010-05-18
hey, I was wondering how to disable the splash screens when Ubuntu loads.In the pdf I see it shows the files here '/usr/share/images/xsplash/' but I don't see any images there.
Not a huge issue, but just want to be rid of it so it looks like it goes from POST straight thru to the Ubuntu desktop.

oh btw, interesting PDF file, will go thru it more when I can get my reader to zoom in beyond 400%. I use my TV as a monitor and PDF's are a bit hard to see on here for some reason.

---

### Post by warfacegod on 2010-05-18
> **towheedm said:**
> I see the file has been downloaded 85 times.  Anyone care to post any comments or remarks?  I am thinking of expanding it to include Lucid and Plymouth.  I would like to know whether there's enough interest in it before I invest any time into it.

Thanks.

There most certainly is. It would be a welcome guide that I would sorely love to link to people asking these same questions about 10.04. So far, the best I've been able to do is get some folks using the gdm2setup utility. While that works well for 9.10, in spite of being incomplete, in 10.04 the only thing it will do is change the greeter and icons themes and disable the user list. Better than nothing.

It is unfortunate that customizing has been made so difficult in 9.10 and even more so in 10.04. Your efforts are highly appreciated.

Addendum: Apparently Ubuntu Tweak is more effective than gdm2setup for some of these customizations in 10.04

---

### Post by k33bz on 2010-05-19
> **towheedm said:**
> I see the file has been downloaded 85 times.  Anyone care to post any comments or remarks?  I am thinking of expanding it to include Lucid and Plymouth.  I would like to know whether there's enough interest in it before I invest any time into it.

Thanks.

I would like a tutorial on plymouth on 10.04

---

### Post by KlavKalashj on 2010-05-23
This is great! I wanted to add shadows to the login window, and it worked fine. However, I came across a strange bug. After editing the comiz settings for user gdm, logging out and logging in as me again, some settings from the user are applied to my user too. The font size for window titles were much bigger, but that was an easy fix. More difficult was to change the window control buttons back to the left :S I was unable to start ubuntu tweak as user gdm, and the setting is still on the left for user [me], but they are showing on the right, as for user gdm although I am logged in as myself :P so strange!

Edit: oh nevermind, I solved it by launching sudo -u gdm dbus-launch gconf-editor and editing the metacity keys. But anyway, the settings for user gdm still applies to me, so I guess the bug is still up :P

---

### Post by towheedm on 2010-05-25
> **KlavKalashj said:**
> This is great! I wanted to add shadows to the login window, and it worked fine. However, I came across a strange bug. After editing the comiz settings for user gdm, logging out and logging in as me again, some settings from the user are applied to my user too. The font size for window titles were much bigger, but that was an easy fix. More difficult was to change the window control buttons back to the left :S I was unable to start ubuntu tweak as user gdm, and the setting is still on the left for user [me], but they are showing on the right, as for user gdm although I am logged in as myself :P so strange!

Edit: oh nevermind, I solved it by launching sudo -u gdm dbus-launch gconf-editor and editing the metacity keys. But anyway, the settings for user gdm still applies to me, so I guess the bug is still up :P

I did not notice this at the time of writing the tutorial because my gdm effects and themes were the same as my desktop.  The problem may be in the compiz.desktop file.  One workaround may be to restart the compiz daemon after entering your login credentials.  Thanks for the info, I'll make some time to try and figure it out.  Please post back if you solve it before me.

> **k33bz said:**
> I would like a tutorial on plymouth on 10.04

That was my next project.  Unfortunately for me, I have an nViidia card which just refuses to work with the Nouveau drivers despite my best efforts.  Anyway I preferred my 3d desktop so I reverted to the proprietary driver.

So I guess I'll wait until it's fixed or I'll have to replace my nVidia card. So sad the devs decided on this driver.

---

### Post by towheedm on 2010-05-25
> **JohnnyC35 said:**
> hey, I was wondering how to disable the splash screens when Ubuntu loads.In the pdf I see it shows the files here '/usr/share/images/xsplash/' but I don't see any images there.
Not a huge issue, but just want to be rid of it so it looks like it goes from POST straight thru to the Ubuntu desktop.

oh btw, interesting PDF file, will go thru it more when I can get my reader to zoom in beyond 400%. I use my TV as a monitor and PDF's are a bit hard to see on here for some reason.

You can disable the xsplash by removing the following lines from the /etc/gdm/Init/Default and /etc/gdm/PreSession/Default files:

```
if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --daemon
fi

```This would prevent the daemon from loading.

As for usplash, it can be disabled using a run-level editor such as boot-up manager.   have not actually tried it, but it should work.

Trying to remove either packages would effectively remove the entire ubuntu-desktop package.

---

### Post by k33bz on 2010-05-27
> **towheedm said:**
> 


That was my next project.  Unfortunately for me, I have an nViidia card which just refuses to work with the Nouveau drivers despite my best efforts.  Anyway I preferred my 3d desktop so I reverted to the proprietary driver.

So I guess I'll wait until it's fixed or I'll have to replace my nVidia card. So sad the devs decided on this driver.

Ok, Sounds good, please keep me updated on that portion :)

---

### Post by towheedm on 2010-05-27
Will certainly do.

---

### Post by towheedm on 2010-06-01
> **KlavKalashj said:**
> This is great! I wanted to add shadows to the login window, and it worked fine. However, I came across a strange bug. After editing the comiz settings for user gdm, logging out and logging in as me again, some settings from the user are applied to my user too. The font size for window titles were much bigger, but that was an easy fix. More difficult was to change the window control buttons back to the left :S I was unable to start ubuntu tweak as user gdm, and the setting is still on the left for user [me], but they are showing on the right, as for user gdm although I am logged in as myself :P so strange

OK, so I checked and checked and came up with this workaround for the compiz bug. 

Rename the /etc/gdm/PostLogin/Default.sample file:
```
sudo mv /etc/gdm/PostLogin/Default.sample /etc/gdm/PostLogin/Default
```Add the following line to the [COLOR=Blue]/etc/gdm/PostLogin/Default[/COLOR] file:
```
gtk-window-decorator --replace &
```

I will add this workaround to the PDF file.

---

### Post by xmmp on 2010-06-02
First I just want to say thank you for this guide. It is exactly what I was looking for. I'm new to Linux and Ubuntu both and so one of the first things I've been wanting to do was customize it and make it look how I wanted it to look. Its nice to have all this info in one place, and nicely laid out and formatted. 

Now I have a question. 

I know your guide was for Karmic, but I'm running Lucid (10.04) since it was latest release when I decided to give Ubuntu a try. I got through the Grub part of your tutorial fine. All the files are still in the same location and named the same as they are in your tutorial. I'm ready to work on my xsplash screen now, but I can not find the directory @ /usr/share/images/xsplash. I searched around a bit, and even tried the search function to look for 'xsplash' but I couldn't find anything. Any idea where the xplash directory might be?

Thanks again for the work you put into this!

---

### Post by towheedm on 2010-06-02
> **xmmp said:**
> First I just want to say thank you for this guide. It is exactly what I was looking for. I'm new to Linux and Ubuntu both and so one of the first things I've been wanting to do was customize it and make it look how I wanted it to look. Its nice to have all this info in one place, and nicely laid out and formatted. 

Now I have a question. 

I know your guide was for Karmic, but I'm running Lucid (10.04) since it was latest release when I decided to give Ubuntu a try. I got through the Grub part of your tutorial fine. All the files are still in the same location and named the same as they are in your tutorial. I'm ready to work on my xsplash screen now, but I can not find the directory @ /usr/share/images/xsplash. I searched around a bit, and even tried the search function to look for 'xsplash' but I couldn't find anything. Any idea where the xplash directory might be?

Thanks again for the work you put into this!

Thanks for the nice comments.  XSplash has been completely removed in 10.04 and USplash was replaced with Plymouth.  The GDM customization should work fine though.  Read the post above yours if you're going to add Compiz to the GDM as it is not yet included in the PDF document.

---

### Post by Eddie Lee on 2010-06-07
Thank you VERY MUCH for this tutorial, I appreciate your effort very much, as others before me I too am running Lucid instead of Karmic, I know it could be a lot of work to do a complete update of your guide from Karmic to Lucid, but, could you please post a list of things we should be aware of as well of things we need to work specific to Lucid?

I am too kind of new to Linux/Ubuntu and never done this kind of "deep" customization so your work its very much appreciated, please keep up the good work :D.

---

### Post by towheedm on 2010-06-08
Thank you.  Keep in mind that XSplash was removed in Lucid and USplash was replaced with Plymouth.  The Grub and GDM customizations should work fine in Lucid.  Unfortunately, I cannot do a tutorial on Plymouth at this time because of my nVidia card.  I'm looking into changing my card or just wait until the Nouveau drivers works properly with the nVidia card.

---

### Post by jcoles on 2010-06-13
Be careful about copying command lines out of the PDF and pasting them into a terminal. 

I thought a command wasn't working. When I pasted it into a forum reply, I saw this:

sudo *u gdm gconftool*2 --**type bool **--set /apps/gdm/simple*-greeter/disable_user_list true 

I had copied the line from the PDF with evince, and pasted the command into the Gnome Terminal. The hyphens were missing, so I added them back, but I saw no asterisks.

When I typed the command instead, it worked. (or was accepted, at least. I haven't rebooted yet!)

Even copy/paste doesn't work properly in Ubuntu. That's pretty lame.

---

### Post by jcoles on 2010-06-13
Thanks, towheedm!

I thought that the GDM greeter was "hard-coded" because I couldn't find any config files for it. I have only used one command from your document and it did the job perfectly.

gconf is too much like the infamous Windows registry. The traditional Linux practice of plain text configuration files is much more open and accessible.

---

### Post by towheedm on 2010-06-14
You're welcome.  Glad it worked for you.

And yes, gconf is very similar to the Windows registry.  Unfortunately. a lot of stuff in GDM 2.28 and above has been hard-coded and cannot be changed short of modifying the appropriate file and re-compiling.  This is not an easy task for the normal everyday user who is not familiar with compiling.

Luckily, some stuff can be changed which allows us to do limited customization of the GDM.  This is moving more and more towards what Microsoft did with XP when they decided to lock down changes to the start-up screen and to the Windows themes.  Eventually someone will do a patch like was done for XP that allowed users to completely change the start-up screen and the Windows themes.

---

### Post by joabar on 2010-06-14
Hello towheedm,

First of all thanks a LOT for your incredible dedication on this. I feel very identified with all your work since I am a design enthusiast, and I'm constantly looking for making my ubuntu more and more eye-friendly.

I don't know if you have seen [this]("http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/") but anyways it worth to see. I hope it helps you and therefore, help us! haha

Good luck and thanks again.

---

### Post by towheedm on 2010-06-14
Thanks for the link joabar.  Will try this in a few minutes.

I have a triple boot setup using Karmic, XP and Lucid.  Karmic is my main OS so Grub is configured from here.  The grub settings in the link you provided has been my default settings for grub.  Booting into Lucid with these settings never worked for me.

I'll try the procedures in the link within the link you provided.  Thanks for the info.

---

### Post by Eddie Lee on 2010-06-25
> **towheedm said:**
> Thank you.  Keep in mind that XSplash was removed in Lucid and USplash was replaced with Plymouth.  The Grub and GDM customizations should work fine in Lucid.  Unfortunately, I cannot do a tutorial on Plymouth at this time because of my nVidia card.  I'm looking into changing my card or just wait until the Nouveau drivers works properly with the nVidia card.


Oh I see, well I also have a nVidia card so I guess Ill wait for that too, thanks \\:D/

---

### Post by jim0watkins on 2010-11-19
> **towheedm said:**
> I see the file has been downloaded 85 times.  Anyone care to post any comments or remarks?  I am thinking of expanding it to include Lucid and Plymouth.  I would like to know whether there's enough interest in it before I invest any time into it.

Thanks.

Awesome!  I love your posts towheedm, they are perfect for me.  Just wondering before I start, does it matter that I'm using Lucid as dual-boot with Vista.  I'll probably be getting rid of Vista sometime in the next few months (probably during xmas break), I'm just waiting on some help to figure out how to do that, and I'm not sure how all these changes can affect that.

I also saw that some people found these steps to work well with Lucid, but what's plymouth, I thought the latest release was maverick?

Thanks a lot for all your work!       J.

---

### Post by clockworktri on 2011-01-17
I would love it if you would explain Lucid and Plymouth! I've been trying to customize plymouth but I can't get it to do what I want...

---

### Post by adeee on 2011-01-25
Can any body tell me how to change or  Customizing the graphics in Grub, Usplash, Xsplash and GDM. in ubuntu 10.04.

is this tutorial for 10.04?
Can any body try it on 10.04?
it works?

---

### Post by JOHNNYG713 on 2011-01-25
Grub Customizer
[http://launchpad.net/grub-customizer/2.1/2.1.0/+download/grub-customizer_2.1.tar.gz](http://launchpad.net/grub-customizer/2.1/2.1.0/+download/grub-customizer_2.1.tar.gz)

Python GDM2 Note: You may have to install xsplash via synaptic if the back ground wont change !
[http://launchpad.net/gdm2setup/0.2/0.5.0/+download/python-gdm2setup.deb](http://launchpad.net/gdm2setup/0.2/0.5.0/+download/python-gdm2setup.deb)

Manage Plymouth Splash with Zorin plymouth splashscreen manager
[http://gnome-look.org/content/show.php/Splash+Screen+Manager?content=134231](http://gnome-look.org/content/show.php/Splash+Screen+Manager?content=134231)

**To customize you own Plymouth Splash from an existing one.**
**1 **open home folder, navigate filesys/lib/plymouth/themes
**2** copy and past the plymouth you want to customize, to where ever you want,desktop,etc.
**3** open the ( or any ) image from the Plymouth with Gimp and change to your liking !
**4** Change the name of you new Plymouth in the .plymouth file as well as the file itself and the name of the folder
Note: you can also change the animations, Placement,size,etc., in the YOURNEWSPLASH.scipts file if you feel you are experienced enough ! And if it has one ! like solar is a .so file and I have not found how to adjust it as yet !

**To change an existing Plymouth WITHOUT having to reinstall **!
in terminal
```
gksudo nautilus
```
and follow the above steps !
**To install a new Plymouth splash Manually**

**1** Open terminal in the place that holds the new Plymouth splash, Example
** $ cd downloads**
**2** enter these commands one at a time !
```
sudo cp -R YOURSPLASHNAME/ /lib/plymouth/themes/
``````
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/YOURSPLASHNAME/YOURSPLASHNAME.plymouth 100
``````
sudo update-alternatives --config default.plymouth
```  here, choose the number of the theme you want to use then hit enter

```
sudo update-initramfs -u
```Download , untar, make executable, place in your home folder, The Test (boot.sh) I have provided. If all went as planed you should see your new Plymouth with out having to reboot !

If anyone can add to this or find something i missed please feel free to add your findings !
This is what I do on all my custom ISO's via **Remastersys **!
[http://sourceforge.net/projects/remastersys/files/remastersys-ubuntu-karmic-lucid/remastersys_2.0.17-1_all.deb/download](http://sourceforge.net/projects/remastersys/files/remastersys-ubuntu-karmic-lucid/remastersys_2.0.17-1_all.deb/download)

I dont in any way mean to take away from this Great! Tut ! just adding to it ! :D

---

### Post by towheedm on 2011-01-25
> **adeee said:**
> Can any body tell me how to change or  Customizing the graphics in Grub, Usplash, Xsplash and GDM. in ubuntu 10.04.

is this tutorial for 10.04?
Can any body try it on 10.04?
it works?

You can customize Grub and GDM in 10.04 acccording to the tutorial.  Unfortunately, Xsplash and Usplash were replaced with Plymouth in 10.04 and above.

Someone sent me this link to customizing Plymouth.  I have not even looked at it because I still use 9.10.  Hope it helps you.

[http://brej.org/blog/?cat=16](http://brej.org/blog/?cat=16)

If you would really like to theme Grub extensively, that a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

---

### Post by bmurphytech on 2011-02-20
> **towheedm said:**
> I see the file has been downloaded 85 times.  Anyone care to post any comments or remarks?  I am thinking of expanding it to include Lucid and Plymouth.  I would like to know whether there's enough interest in it before I invest any time into it.

Thanks.

I will be sure to keep up with this as I have the subject now bookmarked, so please... do go on.

---

### Post by pweyandt on 2011-03-04
Hey Towheedm I know it has been said a few times already but I want to reiterate that this document is really outstanding work.  Thanks for all the time you have put into it.  I have tried a few times to change different parts and can only get one or two small items changed.  Most of the configuration widgets have not worked all that well for me.  I am going to try run through the whole thing on Meerkat over the weekend.  If I get to it I will post my comments on this thread.

---

### Post by towheedm on 2011-03-04
Could you say what did not work?  Things have changed considerably in Maverick and so some of the customizations may not work as expected.  When I wrote this, Maverick was not even code-named as yet.

For instance, running gconftool-2 as the user 'gdm' does not work as stated in the document anymore.  It has to be done differently.

I have only just switched from Karmic to Maverick and am now looking at these changes to include in a new release.

---

### Post by pweyandt on 2011-03-05
As I have been reading up on editing the boot screens it seems like what I need to edit in Meerkat is Plymouth.

---

### Post by towheedm on 2011-03-05
Check out post #33 above.

---

### Post by pweyandt on 2011-03-06
OK...grab some popcorn because this is longer than I would have thought it would be:
:popcorn:
...after working on this for more than I should have this weekend (wasting my time according to my wife) here are the results: 
1) grub...text changes did not work.  I was actually really looking forward to having the green text on black background for some reason.  Maybe showing my age :^0
2) Plymouth is working.  I have an Nvidia card this is somewhat problematic with Plymouth.  this is what did the trick:
* edit grub:
sudo gedit /etc/default/grub
edit this line with your default screen size: 
GRUB_GFXMODE=1280x1024
* edit your grub header 
sudo gedit /etc/grub.d/00_header
add set gfxpayload=keep just below the line containing fxmode=${GRUB_GFXMODE}  it is about 100 or so lines down. use the find command save yourself the trouble of counting lines.  :)
*update grub with these changes
sudo update-grub

I also downloaded plymouth manager and the solar theme although I did not need the manager.  I found how to change it in the terminal. However, now that I have manager I did not save the terminal commmand (stupid me :confused:)

Finally, I changed my graphic for the GDM log in.  I found this kind of interesting.  GDM is kind of like it's own user.  I used a command to set it up so it loads the theme manager automatically at the login screen then once I had it setup I logged in, turned the auto theme manager display off  One mistake I made was I found the boot screen I wanted and left it on my desktop.  Then I logged out and used theme manager to link the graphic  I logged in, ran the script to turn theme manager off at log in and then deleted the file thinking it was saved in the GDM user's hidden profile.  Not the case...I had go back and set it all up again.  
Here are the commands and process I used.
1) turn on theme manager:
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

2) log out.  
3) change your theme
4) log in and turn off theme manager
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

I looked at a lot of sites...the ones that I pulled these commands off of were:
Plymouth: 
[http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html](http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html)
GDM:
[http://www.techytalk.info/2011/02/ubuntu-debian-gdm-login-screen-theme-wallpaper/](http://www.techytalk.info/2011/02/ubuntu-debian-gdm-login-screen-theme-wallpaper/)
I hope this helps some others out there!  :)

---

### Post by towheedm on 2011-03-06
> looking forward to having the green text on black background for some reason.  Maybe showing my age Guess we are about the same age dude.:p  My terminal which sits on my desktop permanently is always set to green text on black background, sometime if I reminisce about vt240 I set it to blue text.:D

No need to edit 00_header for GFXPAYLOAD, if using Maverick, add this line to /etc/default/grub:

```
GRUB_GFXPAYLOAD_LINUX=keep.
```To change Plymouth theme from the command line:

```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

```I have no idea why people continue to make things seem so difficult to change in Linux, especially the background image in GDM.  It's on Pg 23 of the tutorial:

```
sudo -u gdm gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/dir/filename"
```where /dir/ must be an absolute path, not a relative one. For example:

```
/home/towheed/Documents/
```[COLOR=Red]**and not:**[/COLOR]
```
~/Documents/
```And /filename must include the filename's extension.  The file type can be either png, jpg or svg.

Again, it's all in the tutorial.

---

