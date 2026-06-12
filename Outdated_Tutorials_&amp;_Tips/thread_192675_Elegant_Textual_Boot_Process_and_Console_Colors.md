---
title: "Elegant Textual Boot Process and Console Colors"
date: 2006-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Mais on 2006-06-09
**Introduction:**
Hi, first of all, hope you all are enjoying Dapper! As far as I know this HOWTO will work on Dapper as well as Edgy. Any other version I am unsure of how they handle logging and whatnot.

If you have any questions or comments, feel free to respond on the forums or email me.

[B]Warning:
[/B][COLOR=DarkRed]This HOWTO is going to instruct you to change files that help your computer start and run in a functional manner. Modifying these files is dangerous to say the least and will require use of "sudo." With that being said, if you are careful to follow the instructions you should end up with no problems and may want to even change some things on your own to further personalize things!

[COLOR=Black][B]Step 1: Modifying GRUB
[/B][I][COLOR=Blue]This step will remove use of USPLASH without uninstalling it, as well as up your TTY1-6 console resolutions.[/COLOR]
[/I]```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
sudo gedit /boot/grub/menu.lst
``` Study the structure of the file reading some of the comments if you are not already familiar with it. What we want to change is the end of our stable primary kernel line. It should look something like this:
[/COLOR][/COLOR]```
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
``` Remove *splash* from the line:
```
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet
``` Next, find a sutiable VGA mode from the following link: [http://www.8ung.at/spblinux/grub.htm](http://www.8ung.at/spblinux/grub.htm) 
I will use 795 since I can support 24 bit color at 1280x1024 resolution. Add vga=XXX on to the end of the same line;
```
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet vga=795
``` Now when you reboot, your computer will boot without the USPLASH logo and will instead be a high resolution console showing you basically the same information we have seen from before.

[B]Step 2: Adding Color to the Boot Process
[/B][I][COLOR=Blue]This will change the look of the output from step 1. It will colorize the messages to make it a little easier on the human eyes.[/COLOR]
[/I]```
sudo cp /etc/lsb-base-logging.sh /etc/lsb-base-logging.sh_bak
``` Download the attachment [lsb-base-logging.sh.tar.bz2]("http://www.ubuntuforums.org/attachment.php?attachmentid=10932&stc=1&d=1149829830") to your home folder.
```
sudo tar xvfj lsb-base-logging.sh.tar.bz2
sudo chown root:root lsb-base-logging.sh.tar.bz2
sudo cp lsb-base-logging.sh /etc/lsb-base-logging.sh
``` I modified this script to make things turn blue and green and yellow and whatnot. You'll notice the colors during boot only if you followed step one. However, the changes are always visible after boot when you start and stop process from /etc/init.d.

If you want to take a stab at modifying it for yourself and changing the colors, go ahead, it's not overly difficult to study and learn the process. To test out your progress save your file and run
```
/etc/init.d/xxx stop
``` Where xxx is a process that you don't utilize. For example, I used pcimcia a lot because my computer doesn't have any pcmcia components.

[B]Step 3: Colorzing the Prompt
[/B][I][COLOR=Blue]This final amenity will colorize everything in front of what you type in the terminal, i.e. the [COLOR=Black]eft@edgy:~$[/COLOR] sorda deals.[/COLOR]
[/I]This step is very simple. And can be endlessly customized if you so feel.
```
cp ~/.bashrc ~/.bashrc_bak
gedit ~/.bashrc
``` Look for the following:```
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
``` and replace it with: ```
# set a fancy prompt (non-color, unless we know we "want" color)
#case "$TERM" in
#xterm-color)
#    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
#    ;;
#*)
#    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
#    ;;
#esac

# Comment in the above and uncomment this below for a color prompt
PS1='${debian_chroot:+($debian_chroot)}\[\033[32m\]\u@\h\[\033[00m\]:\[\033[34m\]\w\[\033[00m\]\$ '
```For details on how to customize this, check out this website: [http://www-128.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www-128.ibm.com/developerworks/linux/library/l-tip-prompt/)

[B]Step 4: Reboot and Enjoy!

Revert to Original Settings:
[/B]```
sudo cp /boot/grub/menu.lst_bak /boot/grub/menu.lst
sudo cp /etc/lsb-base-logging.sh_bak /etc/lsb-base-logging.sh
cp ~/.bashrc_bak ~/.bashrc
```

---

### Post by benplaut on 2006-06-09
this can be useful for the prompt:
[http://www.samisgreat.com/2004/05/bash-color-chooser.html](http://www.samisgreat.com/2004/05/bash-color-chooser.html)

i once found a little applet to make a prompt with, i'll try and find it again

---

### Post by Mais on 2006-06-09
[quote=benplaut]this can be useful for the prompt:
[http://www.samisgreat.com/2004/05/bash-color-chooser.html]("http://www.samisgreat.com/2004/05/bash-color-chooser.html")

i once found a little applet to make a prompt with, i'll try and find it again[/quote]


Ahh that is a handy tool! The choices are limited, but those are probably the most used ones. Thanks!

---

### Post by pejcao on 2006-10-19
I'm having issues @ 795 (It bitches with "unsupported mode") tho', @794 runs perfectly ;)  this is a gf3 (old, I know, but works).

do you know how to put the console at a refresh of 75Hz? (60Hz is annoying!)

on gentoo I used vesa-tng (which allowed me to set up FB 1280x1024x24@75)

colorfull console looks great! thx!

---

### Post by Mais on 2006-10-19
> **pejcao said:**
> I'm having issues @ 795 (It bitches with "unsupported mode") tho', @794 runs perfectly ;)  this is a gf3 (old, I know, but works).

do you know how to put the console at a refresh of 75Hz? (60Hz is annoying!)

on gentoo I used vesa-tng (which allowed me to set up FB 1280x1024x24@75)

colorfull console looks great! thx!

Glad to hear that it works! As far as changing your refresh rate, I just don't know enough about video drivers and frame buffers. I made this howto after examining my Gentoo install. I missed having all the colors. So it is basically a hack to mimic that, I truthfully don't understand the whole process that is going on in the background for low-level video communication.

---

### Post by bionnaki on 2006-10-19
thanks! works great. my bootup looks very sharp. now, do you know how to get gnome-terminal to have **full** colors, not just the prompt?



also, I like having a nice grub menu. here's what I do:

sudo nano /boot/grub/menu.lst

under *hidemenu*, comment "hidemenu" so the grub menu will always show up. and under *pretty colors*, change the colors to:

> color light-blue/black light-cyan/blue

I think it looks very clean.

---

### Post by Mais on 2006-10-19
> **bionnaki said:**
> thanks! works great. my bootup looks very sharp. now, do you know how to get gnome-terminal to have **full** colors, not just the prompt?



also, I like having a nice grub menu. here's what I do:

sudo nano /boot/grub/menu.lst

under *hidemenu*, comment "hidemenu" so the grub menu will always show up. and under *pretty colors*, change the colors to:



I think it looks very clean.

If I understand what you are asking correctly, I think it is up to whatever program you are running to display any colors.

For example, type ls somewhere in your system where you have a mishmash of different types of files. ls outputs in color by type; folders, for example are blue and .deb is red. 

When I get back from class I will put the "pretty colors" into the main post. I forgot about that as I use gfxboot for grub and have I nice image based menu. Thanks!

---

### Post by bionnaki on 2006-10-27
I did a fresh install of edgy and tried to use this how-to. I havent had any luck. the color changes to the terminal are the only mods that work in edgy - as far as I can tell. hmmmm...

---

### Post by Mais on 2006-10-27
unfortunately this how-to isn't going to work for edgy as the bootup process has changed significantly. In the coming weeks I'll take a hard look at how this can be done for edgy.

---

### Post by bionnaki on 2006-10-27
thanks!

---

### Post by ralf57 on 2006-10-27
> **Mais said:**
> unfortunately this how-to isn't going to work for edgy as the bootup process has changed significantly. In the coming weeks I'll take a hard look at how this can be done for edgy.

Please update your first post where you stated that
> 
As far as I know this HOWTO will work on Dapper as well as Edgy


---

### Post by wiggleroom on 2006-12-14
Hi :)

This works mostly fine for me in Edgy.  Along with the instructions here, I've also followed [this tip so I get a clean log in prompt]("http://gentoo-wiki.com/SECURITY_Clear_screen_on_logout").

My remaining query is how to get a verbose boot-up that *ends* with a login prompt on tty1.  At the moment, the login prompt get quickly buried because the system boot-up notices are still being printed to screen.

So I need to know either:  (1) how to stop boot-up notifications appearing once the login prompt has appeared, or (2) how to delay the login prompt until all the boot-up notifications have finished.

Does anybody know which /etc/rc... file is responsible for launching the tty shells and login prompt?  And if so, how could I delay it until everything else has done?  Or is this a bad idea?

---

### Post by Mais on 2006-12-14
I believe you should be looking for the RC script named gdm

I never really messed with much of that in Ubuntu. In Gentoo, the easiest way to remove a startup script is:
rc-update remove xdm   <--where "xdm" is the script name

---

### Post by wiggleroom on 2006-12-14
> **Mais said:**
> I believe you should be looking for the RC script named gdm
Thanks, Mais.  However, I'm pretty sure gdm is the Gnome Display Manager.  I don't think that's going to help with a text mode startup.  I thought this howto was about working with gdm and all that GUI stuff disabled.  gdm is certainly disabled on my machine now.

It's the script that fires up the text only shells (Ctrl+Alt+[F1-F6]) that I'm trying to hunt.  If possible, I'd either like to delay that until all the other boot services have started, or else keep the other boot services backgrounded once the login prompts (TTYs) have started.

---

### Post by Mais on 2007-08-26
> **wiggleroom said:**
> Thanks, Mais.  However, I'm pretty sure gdm is the Gnome Display Manager.  I don't think that's going to help with a text mode startup.  I thought this howto was about working with gdm and all that GUI stuff disabled.  gdm is certainly disabled on my machine now.

It's the script that fires up the text only shells (Ctrl+Alt+[F1-F6]) that I'm trying to hunt.  If possible, I'd either like to delay that until all the other boot services have started, or else keep the other boot services backgrounded once the login prompts (TTYs) have started.

Ok, this reply is way past due and I apologize for that.

This may help you out:
sudo apt-get install sysv-rc-conf
#then run:
sudo sysv-rc-conf
This will help you modify your different runlevels. A runlevel basically is a step in your bootup process. In a user environment the computer will eventually enter runlevel 6 which is where most services you use will start. Levels before that are for more low-level functions. 

This is all how I imagine it...I could be totally wrong with my description, but it should work nonetheless.

---

### Post by mu3en on 2007-09-06
step 1 - removing usplash and changing tty1-6 resolution:

slightly different approach, but certainly worked -

```
~$sudo apt-get remove usplash
```

```
~$sudo vi /boot/grub/menu.lst
```

change appropriate line to remove 'splash' and add 'vga=xxx'

--

step 2 - colorizing the boot process:

did not fully copy the /etc/lsb-base-logging.sh provided above.

instead, copied the relevant sections into current /etc/lsb-base-logging.sh

specifically these were: log_success_msg, log_failure_msg, log_warning_msg and log_daemon_msg.

--

thanks for the pointers, enjoy.

---

