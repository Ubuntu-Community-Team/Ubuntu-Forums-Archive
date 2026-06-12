---
title: "Customizing Grub2 boot menu"
date: 2009-10-20
forum: Outdated Tutorials &amp; Tips
---

### Post by johns996 on 2009-10-20
The grub boot menu Ubuntu uses has bothered me since I first saw the SUSE implementation of grub.  So, after installing the latest 9.10 beta, I decided it was time to figure out how to get rid of that awful black grub menu.  Two days later, here is what I have figured out.

[SIZE="3"]**Find an image**[/SIZE]

I used the cool heron image from a previous release of ubuntu.  [Find it here]("http://circodigital.org.br/site/wp-content/uploads/ubuntuhhok5.png").  My desktop resolution is 1280X1024 so that's what I trimmed down this image to match.

You'll have to save this image in PNG/TGA format.  You'll see why later so just make sure this is the format you use.

[SIZE="3"]**Set the default grub resolution**[/SIZE]

Grub2 uses a collection of files to set the various settings it uses.  You can specify your desired resolution in the /etc/default/grub file.  Edit it with this command:  

```
gksudo gedit /etc/default/grub
```

Look for the line #GRUB_GFXMODE=640X480.  Remove the # and set your desired resolution.  Here's what I did:

```
GRUB_GFXMODE=1280x1024
```

For whatever reason, one that I don't totally understand, this is not all you have to do to change the resolution grub uses.  As I discovered in [this blog]("http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html"), there is one more change you need to make.

Edit this file: /etc/grub.d/00_header with the command:

```
gksudo gedit /etc/grub.d/00_header
```

You are looking for the line that consists of:

```
set gfxmode=${GRUB_GFXMODE}
```

After that line, add:

```
set gfxpayload=keep
```

your block of code will look like:

```
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
  **set gfxpayload=keep**
  insmod gfxterm
```

With this new line, your resolution will now be displayed by grub.  If you ran the sudo update-grub command you could reboot and witness the glorious resolution.  Since I want to add a background, I won't run this command yet.
[SIZE="3"]
**Set a background image and change the highlighting colors**[/SIZE]

To set a background in grub you have to edit the debian theme file stored at /etc/grub.d/05_debian_theme.  Edit this file with the command:

```
gksudo gedit /etc/grub.d/05_debian_theme
```

First, look for the line:

```
use bg=false
```

change it to:

> use bg=true

Next you are looking for the "for" statement just below the use bg piece of code we just changed.  This for statement will show you the directories that grub will look for your background image in.  I added another directory, emphasized in bold, to this list so my entry looks like this:

```
for i in {/boot/grub,/usr/share/images/desktop-base**,/usr/share/images/grub**}/xxxxxxxxxx.{png,tga} ;
```

Make sure your image is in either png or tga format and then copy it into one of the directories listed above.  I just used /usr/share/images/grub.  I named my image ubuntu for ease of use, so I replaced the previous image name (the x's in the example above) with my image name.  

```
for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/ubuntu.{png,tga} ;
```

Finally, depending on your preferences, you might want to adjust the colors grub uses for text and highlighting.  With background images enabled, grub defaults to black text with magenta highlighting.  To change this scroll down to the bottom of the file and look for the code:

```
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
```

You'll want to keep the color after the slash, for both instances, set to black.  It seems this makes the foreground transparent allowing your to see your handsome new background.  You can see a list of available colors in the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html#color").  This is what I used for my brown-heavy image.

```
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=white/black
  set color_highlight=brown/black
else
```

[SIZE="3"]**One last thing**[/SIZE]
In order for all of this stuff to work, you'll have to recompile the grub configuration file.  Do this by running:

```
sudo update-grub
```

All that's left is to restart and behold the wonder.  Enjoy.

---

### Post by bodhi.zazen on 2009-11-05
A fair amount has changed with grub2

Please see : [Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2")

---

### Post by KroniKlepto on 2009-11-06
Well, everything went well until updating grub... 

```

Generating grub.cfg ...
No path or device is specified.
Try ``grub-probe --help'' for more information.
No path or device is specified.
Try ``grub-probe --help'' for more information.

```

I'm running 9.10 64.

Any ideas?  Is any more information required?  Thanks.

---

### Post by daemian57 on 2009-11-06
im getting the exact same error on 32 bit

i noticed that if i change the line

> use bg=true

back to:
> 
use bg=false

update-grub works, but the image is not shown in grub

---

### Post by zreed20 on 2009-11-06
That means that you have an invalid file path in your configuration file.  I'm going to guess that when you edited this line...

```
for i in {/boot/grub,/usr/share/images/desktop-base**[COLOR="Red"],[/COLOR]**/usr/share/images/grub}/ubuntu.{png,tga} ;
```

You forgot to put a comma after /usr/share/images/desktop-base. So, instead, you have an invalid file path.  If you do have the comma, the other thing I can think of is that you forgot to create the /usr/share/images/grub directory.

Hope that helps.

---

### Post by daemian57 on 2009-11-06
ahhh dangnabbit I had

> for i in {/boot/grub,/usr/share/images/grub}/ubun**u**tu.{png,tga} ; do

this is why spelling is important in school...

thanks for helping me find the problem

---

### Post by Cryptog on 2009-11-06
It is not necessary nor recommended to change use bg=true in the script. This is used as a flag for the loop logic. 

One thing I haven't tested and people should be aware of if they have problems: 

Suppose you put your image under the /usr directory tree. Does this need to be available at boot time? Some people create a large single partition that holds everything, including /boot. In that case there is no issue. But what if you put boot in its own partition like many people do? Will grub still find the image if it is in /usr and not mounted? Does the image get copied during "update-grub" or is it read at boot time? The **safe** thing would be to put the image in /boot/grub where grub can get to it no matter what.

---

### Post by KroniKlepto on 2009-11-06
Still a no-go.  Here's the offending line:

```

use_bg=true
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base,/boot/grub}/tux.{png,tga} ; do

```

---

### Post by robo_rat on 2009-11-06
Is there any way to increase the font size after setting a high resolution?

---

### Post by gonzorg on 2009-11-06
I tried the directions listed to change the resolution.  When I restart the screen re-sizes as it should, but I no longer can see the login prompt.

If I leave the gfxpayload=keep out, the machine boots ok, but back at the old resolution.

I am running Ubuntu Server 9.10 in Virtual Box 3.0.10.

Any help would be appreciated.  Thank you

---

### Post by CONCORAN on 2009-11-07
I followed steps as in post 1, but grub2 post install script started to fail wit a message saying grub-pc wasn't configured. So I undid the changes, went into synaptic package manager, remove just about everything grub, reinstalled grub2 (+grub-pc, grub-common) and was able to install Grub2. After that I installed startupmanager (GUI Tool) to set up start up options. It works fine now, except that I am not able to get spash screen behind grub menu.

---

### Post by Vichfret on 2009-11-07
it worked great now my grub looks absolutely nice

---

### Post by Don1500 on 2009-11-08
Did everything as shown, worked great. I now have the grub splash I want and I can change it every day if I please (in fact, I bet there could be a script that does that for you if you set it up right). Screen resolution is funky, but I found the right one for my 1680X1050 monitor (it's 1080X675, whatever, it works.) 

I do have one question;
Is there anyway to get rid of the box that surrounds the menu choices in Grub?

---

### Post by soul_nc on 2009-11-09
Hi,newbie here:p
I found out that I need to edit this line to get the desired resolution..

> if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=640x480 ; fito
> if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=1024x768 ; fi

---

### Post by leandromartinez98 on 2009-11-09
Edit: check the next post to see how to build this menu automatically.

My tweak of the Grub2 menu is the following, and makes the menu look like this:

```

Ubuntu Karmic
Windows Vista
=============== Other non-standard options ===============
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)

```

What I have done is:

1 - Copy the /etc/grub.d/40_custom to /etc/grub.d/06_custom
(by being 06 it will be loaded before 10_linux and your custom
options will appear at the top).

2 - Edit the 06_custom file created adding the menu entries
you want, copying exactly the content of the 
/boot/grub/grub.cfg file. You can copy exactly the entry from the grub.cfg file and change the title of the menuentry alone. My 06_custom file looks like this, then:

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu Karmic" {
      recordfail=1
      if [ -n ${have_grubenv} ]; then save_env recordfail; fi
      set quiet=1
      insmod ext2
      set root=(hd0,3)
      search --no-floppy --fs-uuid --set aecf5a37-4292-4545-9f7c-0dad8d118263
      linux /boot/vmlinuz-2.6.31-14-generic root=UUID=aecf5a37-4292-4545-9f7c-0dad8d118263 ro   quiet splash
      initrd      /boot/initrd.img-2.6.31-14-generic
}
menuentry "Windows Vista" {
      insmod ntfs
      set root=(hd0,2)
      search --no-floppy --fs-uuid --set 3056cb7d56cb4278
      chainloader +1
}
menuentry "=========== Other non-standard options ==============" {
      recordfail=1
      if [ -n ${have_grubenv} ]; then save_env recordfail; fi
      set quiet=1
      insmod ext2
      set root=(hd0,3)
      search --no-floppy --fs-uuid --set aecf5a37-4292-4545-9f7c-0dad8d118263
      linux /boot/vmlinuz-2.6.31-14-generic root=UUID=aecf5a37-4292-4545-9f7c-0dad8d118263 ro   quiet splash
      initrd      /boot/initrd.img-2.6.31-14-generic
}

```

Note that the third entry is exactly identical to first, and I use it only as a separator. I don't know how to put an empty entry for that.

Ideally the first "Ubuntu Karmic" entry should be something more intelligent that updates automatically when a new kernel is found. I don't know how to do that yet.

Edit: after changing the files you need to run update-grub, of course.

---

### Post by leandromartinez98 on 2009-11-09
The present script will build the menu I presented in the previous
post, but choosing the latest kernel automatically for the Ubuntu
option at the top. It is a slightly adapted 10_Linux script, which
shall be named 06_custom and put at the "/etc/grub.d" folder.

Just needed checking if the Windows partition is defined correctly
at the end, its menu entry should match your /boot/grub/grub.cfg
menu entry for Windows.

It cannot do much harm, to take back you only need to remove
the 06_custom file from the /etc/grub.d directory. But since this
is messing up with booting, I don't take responsibility for problems
that may arise, I'm not an ultra expert on this.

To use it:

1 - Copy the 06_custom.txt file attached to

/etc/grub.d/06_custom

2 - Make it executable:

sudo chmod +x /etc/grub.d/06_custom

3 - Your present /boot/grub/grub.cfg file
contains a menuentry for windows. Replace the content of
the windows vista menuentry with the content of the menuentry
of that file. Be careful with the following character: " and $.
If they are present in the content of the menuentry, add
a \ before it (\" and \$). 

4 - Update grub: 

sudo update-grub

5 - Check the content of the /etc/grub/menu.cfg created.
The first menuentry should be the newest Ubuntu kernel. The
second is the windows partition. And this one must exactly
match the windows partitions defined at the end, which
is generated automatically. 

6 - Reboot.

7 - If you don't like the result, just remove the 

/etc/grub.d/06_custom

file and re-update grub with:

sudo update-grub



----
If this works well, you shouldn't have to worry anymore with the grub menu when the
kernel is updated. The new kernel will be at the top and older ones will appear below
as an non-standard boot option.

---

### Post by GO%)$@*1 on 2009-11-11
I'd just like to say I love the tutorial and plan to use it as soon as I can.


Did you know this thread made Lifehacker?

[http://lifehacker.com/5398635/customize-ubuntu-910s-grub-boot-screen](http://lifehacker.com/5398635/customize-ubuntu-910s-grub-boot-screen)

---

### Post by The2DQuartet on 2009-11-12
I think the following may have something to do with the issue you are having:

```
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)		reader=png ;;
        *.tga)		reader=tga ;;
        *.jpg|*.jpeg)	reader=jpeg ;;
```

This would suggest grub is unable to read the directory you placed your background in, or that it's not in a format it will accept (png, tga or jpeg). I don't profess to be an expert in these matters so I'd be grateful to anyone who can corroborate this!

---

### Post by Don1500 on 2009-11-14
> **The2DQuartet said:**
> I think the following may have something to do with the issue you are having:

```
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)		reader=png ;;
        *.tga)		reader=tga ;;
        *.jpg|*.jpeg)	reader=jpeg ;;
```

This would suggest grub is unable to read the directory you placed your background in, or that it's not in a format it will accept (png, tga or jpeg). I don't profess to be an expert in these matters so I'd be grateful to anyone who can corroborate this!

If you want to get your Grub Splash screen from a directory that you do not need to "sudo" all the time just edit this:

```


for i in {/boot/grub,/usr/share/images/desktop-base,[SIZE="5"]**/usr/share/images/grub**[/SIZE]}/xxxxxxxxxx.{png,tga} ;
```

to whatever directory you wish.

---

### Post by nanouk on 2009-11-14
Worked mostly as indicated, but there were a few differences in the files; I just figured it out by reading the code and knowing what you meant as opposed to following blindly. Thanks for a great little tweak. Works fine.
N.

---

### Post by leandromartinez98 on 2009-11-16
> **nanouk said:**
> Worked mostly as indicated, but there were a few differences in the files; I just figured it out by reading the code and knowing what you meant as opposed to following blindly. Thanks for a great little tweak. Works fine.
N.

I'm not sure if you are referring to what I posted. But if this is the case, I want to highlight that the Windows menu entry MUST be edited according to the current entry in the grub.cfg file. Furthermore, it is important to check the new grub.cfg file created to see if any strange character was missinterpreted by the script. I have edited the post above to mention that.

---

### Post by brotherlen on 2009-11-16
Very cool, thank you for your tutorial.

---

### Post by zarf on 2009-11-22
there is probably a very simple solution to this but i cannot copy my pic into the folder

I get 

"*There was an error moving the file into /usr/share/images/desktop-base.  Error moving file: permission denied"*

WTF?  went into users and groups and I'm the admin and have all the permissions checked???

searching the help files but if anyone has an idea...
thanks

---

### Post by bodhi.zazen on 2009-11-22
You need to move your picture into place with sudo.

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by venkatad on 2009-11-23
> **zarf said:**
> there is probably a very simple solution to this but i cannot copy my pic into the folder

I get 

"*There was an error moving the file into /usr/share/images/desktop-base.  Error moving file: permission denied"*

WTF?  went into users and groups and I'm the admin and have all the permissions checked???

searching the help files but if anyone has an idea...
thanks

Before You move the pic to /usr/share/images/desktop-base, Open a terminal and type su root enter root password. (** If the password has not been set up....type command- sudo password OR su password and asks fo new UNIX password twice. Now your password is set). Then try to move the file that should work

--Cheers

---

### Post by bodhi.zazen on 2009-11-23
> **venkatad said:**
> Before You move the pic to /usr/share/images/desktop-base, Open a terminal and type su root enter root password. (** If the password has not been set up....type command- sudo password OR su password and asks fo new UNIX password twice. Now your password is set). Then try to move the file that should work

--Cheers

Wow, no need to set a root password to move a file =)

Use sudo.

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by ghostier on 2009-11-24
Updated successfully but the image doesn't show up in the grub menu, I don't think the colors changed either. And yes I did make sure I set the value to true instead of false. The resolution change worked fine. So I'm guessing it has something to do with the debian theme file.

---

### Post by dvl300 on 2009-11-24
I get a full screen :) but no image and after booting ubuntu from the bootloader I get this

vga=792 depreciated

then normal ubuntu loading splash screen

I had this problem before with grub 1 so I ended up redoing the grub files :(

Any suggestions?
thanks :)

---

### Post by zarf on 2009-11-24
thanks for the help. I cannot get past permission denied.

tried setting pswd for root but nothing happens. I cannot even delete files from My cptr. permission denied.

even the "send to trash is greyed out.

I will post a question and not tie up this thread anymore. getting off topic with my problems

thanks.

---

### Post by chrisinspace on 2009-11-27
Everything is working great for me except after I select my OS from the Grub menu, I get a one or two second flash of colors and characters (letters, numbers symbols).  It's almost like some graphics hardware diagnostics tests I've seen.  I didn't have this issue before I customized Grub2 to load an image.

It's not a huge deal, but I thought maybe someone else had seen it.  I have a Dell laptop with integrated NVidia graphics (see details in my sig).

---

### Post by chrisinspace on 2009-11-28
I've been playing around with this off and on all night, but still no luck.  I have tried 1280x800 and 800x600 resolution.  I've tried .png, .tga, and .jpg files.  Still no luck getting rid of brief flash of random colors and characters.

---

### Post by LequidMetal on 2009-11-28
Worked to perfection the only thing is .... the image is a little too short for the menu ... have to try increasing the picture rez
Thanks for the tutorial

---

### Post by LequidMetal on 2009-11-28
Do i have to update the grub everytime i change the picture ?

---

### Post by Foolishgrunt on 2009-11-29
Great tutorial. Thanks for doing it, johns. But I've got another question to ask you, or anyone else who can answer it.

Is there any way to set the resolution of the background image separately from that of the menu text? For example, a 1280x800 background with a 800x600 menu? I know I'm picky, but the text is so small when the resolution is set that high...

---

### Post by chrisinspace on 2009-11-29
> **Foolishgrunt said:**
> Great tutorial. Thanks for doing it, johns. But I've got another question to ask you, or anyone else who can answer it.

Is there any way to set the resolution of the background image separately from that of the menu text? For example, a 1280x800 background with a 800x600 menu? I know I'm picky, but the text is so small when the resolution is set that high...

I changed my image resolution and forgot to change my screen resolution and they were displaying differently.  They seem to be independent.

---

### Post by mantis8 on 2009-11-29
I have an issue I don't know how to fix - I upgraded from 8.10 to 9.04 and I cant update anything because the password is incorrect.  After looking in google for a while, I found out I could reset the password by going into grub during boot up.  I reset the pw extremely carefully multiple times, but it never goes into effect, even though the screen says that the password has been successfully reset.  

I don't want to upgrade to 9.10 because even after reformatting my hdd and doing a clean install on another computer, the internet connection is really bogged down.

Any ideas?

---

### Post by chrisinspace on 2009-11-30
> **mantis8 said:**
> I have an issue I don't know how to fix - I upgraded from 8.10 to 9.04 and I cant update anything because the password is incorrect.  After looking in google for a while, I found out I could reset the password by going into grub during boot up.  I reset the pw extremely carefully multiple times, but it never goes into effect, even though the screen says that the password has been successfully reset.  

I don't want to upgrade to 9.10 because even after reformatting my hdd and doing a clean install on another computer, the internet connection is really bogged down.

Any ideas?

This thread is discussing issues regarding Grub2 themes and customization.  Your post is asking about config issues in 9.04, which by default still uses the original Grub.  I think you're a bit off-topic. 

Try the instructions found here: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

If that doesn't work for you, I'd recommend looking for a thread that is focused on Grub 1.x (not Grub2...they are very different) or using Recovery Mode.  If you search extensively, but can't find what you need, then you could start a new one for your password problem.

---

### Post by mantis8 on 2009-11-30
thx for the info.  I"ve tried this before, but will see what I can do.

---

### Post by rawfull on 2009-12-11
I have windows 7. I also installed the windows XP special compatability partition that windows 7 uses sometimes. it is non bootable.
I right now have a working dual booting system through grub. the only thing im trying to change is the order of the OS's in the list. ill explain, this is my grub.d folder:

00 header
05 debian theme
10 linux  (my karmic)
11 windows (non bootable specialized XP partition managed by windows 7)
20 memtest
30 os prober
40 custom

pretty standard, i havent messed around with it too much. that is the list of boot options that shows up when i start my computer, but there is actually one more option listed on the very bottom that is called windows 7 (loader) on /hd/sda2

so im trying to move the location of the windows 7 menu item up higher, but as you can see there is no file for it in the grub.d folder.  anyone know what i can do about this

---

### Post by RevolutionMaster on 2009-12-30
After following this guide, my bootloader only shows the @ character.

It works fine, except that anything that is text shows up as @.

Ubuntu = @@@@@@

What should I do?:confused:

Actually, upon closer inspection, they're not @ symbols. They're question marks inside small boxes. [?] with rounded corners.

---

### Post by james.mccann1b on 2010-01-22
Thnx v. much for this post. Easy, great tip a newbie like me to understand the workings of linux :)

---

### Post by erictherev on 2010-01-27
I followed these directions and it worked perfectly. Thanks for the how-to!
:popcorn:
A couple of things I am wondering about:

It has been mentioned that if you set the background size and the text size (it might be called something else) to differing resolutions, you could wind up having larger text. How do I go about changing the text size without changing the background resolution?

Is it possible to remove the box around the text (or at least change it to a completely different color)?

Thanks for any help or advice.

---

### Post by PCHome on 2010-02-10
After upgrading to 9.10 and Grub2, my Windows XP drive no longer shows up in Grub. How can I restore it?

How can I remove all the extraneous Grub boot entries? There are so many that it has two pages through which to scroll.

Thanks.

Don

---

### Post by jh5637 on 2010-02-25
Just wondering if I can still get some help with this? I've managed to build the directory using sudo and made everything look like the tutorial but I get this when I do a sudo update-grub

Generating grub.cfg ...
No path or device is specified.
Try ``grub-probe --help'' for more information.
No path or device is specified.
Try ``grub-probe --help'' for more information.

This is my code:
use_bg=true
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/ubuntuhhok6.{png,tga} ; do
    if is_path_readable_by_grub $i ; then

Any help would be appreciated.  I'm a noob but love me some Linux.

Using Ubuntu 9.10 AMD64 version installed through Wubi on top of Win 7 64 bit

I get the boot screen but no image.  This seems like a really nice tweak and would really like to get my hands wet in the Linux pool by figuring out how to do this.

---

### Post by Arkitekt on 2010-02-25
I have having the exact same issue as jh5637, i made a post here [http://ubuntuforums.org/showthread.php?p=8877707#post8877707](http://ubuntuforums.org/showthread.php?p=8877707#post8877707)

I am surprised that so many people are experiencing this issue but no one has a definitive answer on how to fix it

---

### Post by jh5637 on 2010-02-28
I guess everyone's quit on this one?

---

### Post by Arkitekt on 2010-02-28
I really hope not, this is a pretty big problem, there has to be others out there experiencing it. 

I feel like either downgrading to 1.96 which I know works, or waiting for a stable release of 1.98

---

### Post by andrewthomas on 2010-03-07
> **jh5637 said:**
> Just wondering if I can still get some help with this? I've managed to build the directory using sudo and made everything look like the tutorial but I get this when I do a sudo update-grub

Generating grub.cfg ...
No path or device is specified.
Try ``grub-probe --help'' for more information.
No path or device is specified.
Try ``grub-probe --help'' for more information.

This is my code:
use_bg=true
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/ubuntuhhok6.{png,tga} ; do
    if is_path_readable_by_grub $i ; then

Any help would be appreciated.  I'm a noob but love me some Linux.

Using Ubuntu 9.10 AMD64 version installed through Wubi on top of Win 7 64 bit

I get the boot screen but no image.  This seems like a really nice tweak and would really like to get my hands wet in the Linux pool by figuring out how to do this.
I don't think that you want to change the line use_bg=false to use_bg=true.  I am using v1.98.
```
andrew@790x:~$ grub-install -v
grub-install (GNU GRUB 1.98~20100128-1ubuntu4)
```The only lines that you have to change in your /etc/grub.d/05_debian_theme file are the wallpaper line to point to your image and possibly the color  lines.  
```
else
  WALLPAPER="/usr/share/images/grub/Plasma-lamp.tga"
  COLOR_NORMAL="white/black"
  COLOR_HIGHLIGHT="magenta/black"
fi
```as referenced in [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
> The following guidance for setting the background  image is for the current default Grub 2 installation on Karmic Koala,  Ubuntu 9.10. In later versions of Grub 2 (1.97 and later), found in  testing versions of Lucid Lynx 10.04, the line: ">for i  in {/boot/grub,/usr/share/images/desktop-base}..."   has  been replaced with a simplified line: 
WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"I didn't change any of the info in the following section
```
# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found background image: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

```
Also, see [http://ubuntuforums.org/showpost.php?p=8928637&postcount=10](http://ubuntuforums.org/showpost.php?p=8928637&postcount=10)

---

### Post by Sonybuntu on 2010-03-13
I put my optimal resolution, 1650x1080, but it goes down to 1152x864.

---

### Post by andrewthomas on 2010-03-16
> **Sonybuntu said:**
> I put my optimal resolution, 1650x1080, but it goes down to 1152x864.
1152x864 is probably the highest resolution available during grub.  
```
grub>vbeinfo
```This will display all the resolutions that are possible with your system.

---

### Post by Cavsfan on 2010-03-23
I installed Lucid today and was able to get my custom grub screen looking good!
Thanks for the tutorial! I had it set to 640x480 with Karmic, but lost it when I did the fresh install.
That looked like the size it was meant to be, but this time I made it 1920x1200 and it looks great.

Edit: The screen actually looks great and looks as one would expect it to look.
It is a huge picture, but the box is in the right place and the font size is good.
I wouldn't want a size 21 font or something like that on there anyway.

So, no complaints! I am good! And the bootup screen is awesome in my opinion!

Thanks! :popcorn:

---

### Post by dejaime on 2011-03-26
> **bodhi.zazen said:**
> A fair amount has changed with grub2

Please see : [Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2")Thanks!

This link has everything I need!

---

### Post by towheedm on 2011-03-27
Oh customize it using the gfxmenu.  See this thread for my tutorial:
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

2nd edition to be released within the next 2 months.

---

### Post by Cavsfan on 2011-03-27
I guess I posted the above post before I created my tutorial for creating a super nice maintenance free grub2 menu, with **ranch hand's** knowledge.
It has the new font too, so that the text is no longer so small.

There are several examples of what my screen looks like with just these 3 entries: 
[LIST]
[*]Lucid Lynx
[*]Lucid Lynx (Recovery Mode)
[*]Windows 7
[/LIST]

Although I have 3 kernels installed, the top selection always boots into the most recently installed kernel.
It also never has to be modified. Unless of course you want to change the background picture. My screen size is 1920x1200.
Man, this is an old thread. :D

---

### Post by Enigmapond on 2011-03-27
For the GUI people...LOL there is now a great programme that does all this quite simply...

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

Cheers!

---

