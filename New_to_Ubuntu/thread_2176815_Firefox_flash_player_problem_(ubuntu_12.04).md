---
title: "Firefox flash player problem (ubuntu 12.04)"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by pkdev on 2013-09-26
hi there. I have a problem with flash player but only on firefox, in chrome is everything ok.
The problem is when i watch movie in YT. Flash player says 

"[COLOR=#000000][FONT=Helvetica]The [/FONT][/COLOR]*Adobe Flash plugin*[COLOR=#000000][FONT=Helvetica] has crashed. [/FONT][/COLOR]*Reload*[COLOR=#000000][FONT=Helvetica] the page to try again. No report available."

[SIZE=2]when i refresh page sometime movie starting, but not always[/SIZE]
[SIZE=2][FONT=arial]Whats interesting is when i run this Ubuntu(I have it on my external hard drive) on my laptop everything is ok.
I guess my hardware is the problem.

What do u think?[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by johnlittler on 2013-09-26
I am replying to your question in a general way regarding Firefox, Youtube and flash.

Basically, since Firefox 24 you no longer need flash in Linux to watch Youtube. However, not many people have realised that yet. There has been very little publicity about this major positive change.


This answer will be of interest to you if you like using the terminal. If you are not used to the terminal, it is probably something you may not be interested in.

If you are using Firefox 24 or above, you can make a few changes to your Linux system and Firefox to enable you to watch in html5 ( H-264, mp3-aac ) without any plugin all the videos on Youtube ( which have been uploaded within the last two years) without entering the html5 trial and other sites like dailymotion.com.
see:
[http://www.ghacks.net/2013/06/23/firefox-24-for-linux-gets-native-mp3-aac-and-h-264-support/](http://www.ghacks.net/2013/06/23/firefox-24-for-linux-gets-native-mp3-aac-and-h-264-support/)

If you are interested, these are the steps to follow:

1. Type about:config into the firefox browser's address bar and hit enter.
2. Confirm that you will be careful if this is your first time.
3. Search for media.gstreamer.enabled
4. Make sure it is set to to true (which means enabled).
5. You need to install gstreamer: `libgstreamer0.10-dev` and `libgstreamer-plugins-base0.10-dev`

In the Ubuntu terminal ( open with ctrl + alt + t ) type these lines separately. Press enter after each line of code.

 sudo apt-get install libgstreamer0.10-dev

 sudo apt-get install bgstreamer-plugins-base0.10-dev

sudo add-apt-repository ppa:gstreamer-developers/ppa
sudo apt-get update
sudo apt-get install gstreamer1.0*

6. Install the following Firefox extension (to view Youtube videos)

[https://addons.mozilla.org/ja/firefox/addon/youtube-all-html5/?src=api](https://addons.mozilla.org/ja/firefox/addon/youtube-all-html5/?src=api)

7. Deactivate the flash plugin. There is no need to remove it. Just deactivate it. ''Add-ons &#8594;Plugins&#8594;ShockwaveFlash&#8594;Never activate

8. Restart Firefox. It is unlikely that you will need to restart your computer, but if these steps do not work restart.

9. Now test it with the flash plugin deactivated.

From Firefox 24, you can view Youtube without flash without joining the HTML5 trial.

Test it on non-Youtube tube videos such as Dailymotion.com and this test video.

[http://mirrorblender.top-ix.org/movies/sintel-1024-surround.mp4](http://mirrorblender.top-ix.org/movies/sintel-1024-surround.mp4)

10. You may need to reactivate flash for other sites. To do that easily, install this Fiorefox extension:

[https://addons.mozilla.org/en-US/firefox/addon/flash-onoff/](https://addons.mozilla.org/en-US/firefox/addon/flash-onoff/)

An icon can be dragged from Menu Bar&#8594;View&#8594; Toobars&#8594;Customize to a toolbar and clicking it can turn flash on and off.

---

### Post by Impavidus on 2013-09-26
For some time already Firefox has been supporting html5/webm video format. Google decided to move everything on youtube to webm format, so this is nice for us. In contrast to h264 it's patent-free. Unfortunately many videos are still unavailable in webm.

As to your problem, it may be hardware indeed. What's the difference in hardware between the computers? CPU, grahics.

---

### Post by pkdev on 2013-09-26
@[**[COLOR=#000000]johnlittler[/COLOR]**]("http://ubuntuforums.org/member.php?u=1864438") thank u so much fo reply. I ll do this:)

@[**[COLOR=#000000]Impavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721"). 
PC -  AMD Phenom(tm) II X4 955 Processor × 4, 3,9 GB RAM, GeForce GT 640 2GB.
LAPTOP - *Core*&#8482;*2 Duo* Processor  2.4 ghz E6300, 3GB RAM, GeForce 220M 512MB.
i dont get it;/ why on Laptop everything is ok, but on PC not

---

### Post by BBQdave on 2013-09-26
> **pkdev said:**
> I have a problem with flash player but only on firefox[COLOR=#000000][FONT=Helvetica][SIZE=2][FONT=arial]...[/FONT][/SIZE][/FONT][/COLOR]

Sorry, not seeing this on Ubuntu Unity 12.04LTS with updated system, Adobe Flash plugin, and Firefox - Toshiba Satellite c655-s5503.

YouTube and Pandora Radio playing fine.

Firefox is the only browser I have installed. Maybe a conflict between the two browsers you are running, Chrome - pepper flash and Firefox - Adobe Flash plugin?

---

### Post by johnlittler on 2013-09-26
[h=1][COLOR=#000000]To pkdev[/COLOR].[/h]I am also using using 12.04LTS (with kernel 3.8).

The tweaks which I have suggested in Firefox 24 have enabled me to turn off Flash.

I can now see ALL Youtube videos less than two years old without flash. It also means that you do not see the Youtube onscreen ads.The only exception is the 'pay to view' Youtube vdeos which are quite rare.

Furthermore, by turning off flash until you really need it, your general browsing is quicker. You will not realise how the flash plugin slows down browsing until you turn it off.

If my suggested tweaks work for you, please tell others on this forum, who may be struggling with Firefox and flash.

Incidentally, if you need to updated your kernel to 3.8, please see this page.
[http://namhuy.net/1365/ubuntu-lts-enablement-stacks.html](http://namhuy.net/1365/ubuntu-lts-enablement-stacks.html)

 Using the Raring kernel in 12.04LTS really speeds up streaming videos.

---

### Post by johnd.jasper on 2013-11-20
I too encountered this problem on 12.04LTS (with kernel 3.8) on a Dell Dimension 2400.  I tried turning off Flash as mentioned above and it did work but too cludgy to be satisfactory.  I eventually followed advice on booting from kernel 3.5 which resolved the problem nicely. Flashplayer displays all ads, videos, etc correctly and YouTube works a treat.

Without going into great detail, I used Synaptic to install "linux-image-generic-lts-quantal 3.5.0.43.49" then tested it by calling up the boot menu by holding down the LH Shift key immediately after the BIOS splashscreen disappears, then selecting the Previous Versions option and then the ...3.5.0.43.49 entry.  Once I was happy that it worked, I created a custom menu entry in /etc/grub.d.  To do this, I made a copy of 40_custom and renamed it 06_custom to make it the first entry in the menu.  Into that file, I pasted the corresponding menu entry from /boot/grub/grub.cfg.  In my case it was:

> menuentry 'Ubuntu, with Linux 3.5.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ad4e29ff-3e02-422e-ae60-3f2fce61c90a
    linux    /boot/vmlinuz-3.5.0-43-generic root=UUID=ad4e29ff-3e02-422e-ae60-3f2fce61c90a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-43-generic
}


As the 40_custom/06_custom remarks says, I just added it at the bottom of the file and didn't mess with any of the existing entries.  I then ensured that the 06_custom file had the correct attributes by running command "sudo ls -la /etc/grub.d/06_custom".  Because I had messed with the default order in a previous experiment, I edited /etc/default/grub and set GRUB_DEFAULT=0 so that the new menuentry would be selected automatically.  To finish, I then ran sudo update-grub.  Of course, all of these actions had to be accomplished as sudo.  For finer detail on this process, please refer to this help entry:

[https://help.ubuntu.com/community/Grub2/CustomMenus#Custom_Menu_Naming](https://help.ubuntu.com/community/Grub2/CustomMenus#Custom_Menu_Naming)

---

