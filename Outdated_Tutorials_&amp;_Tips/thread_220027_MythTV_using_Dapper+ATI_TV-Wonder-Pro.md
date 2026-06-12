---
title: "MythTV using Dapper+ATI TV-Wonder-Pro"
date: 2006-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by atrus123 on 2006-07-20
Edit: This guide is very outdated, but I'll keep it up here because there are a few still-useful points that are difficult to find elsewhere.  Aside from that, use this guide at your own risk.

[http://www.animewine.com/index.php?entry=entry060720-151531](http://www.animewine.com/index.php?entry=entry060720-151531)

This is a long guide aimed at people using the little-documented ATI TV-Wonder-Pro card.  I try and cover every step, and some information may be useful for people troubleshooting other cards and other distributions.

If you can think of anything to add, please visit the link above, and I will consider adding it to the guide.  I am likely to check those comments often.

Anyway, without further ado, here's the guide:

--------------------

I sincerely hope this guide will be useful to someone, considering that information regarding this combination is few and far between, which made my MythTV set up a true trial. I've come to believe that Ubuntu is not the best distro for MythTV, but I still insist on using it. Why?

1) I like Ubuntu
2) I didn't want to wait for Gentoo to compile everything
3) SuSE was too slow on this older hardware

I'm also a big fan of Gentoo and SuSE, but Ubuntu just seemed like a better choice. Some say Fedora is the best MythTV distro, but I had problems dealing with the Fedora repositories, and before long, I defaulted back to Ubuntu.

The main reason NOT to use Ubuntu is that you're currently stuck with MythTV 0.18 in the repositories. This sucks because 0.18 doesn't work well with MySQL 5, which is currently the latest version. In order to get it all working, I had to work around some stuff, which I intend to document here.

Here is the hardware I am using:

nVidia gForce 3
ATI TV-Wonder-Pro
Pentium III Copermine
256mb RAM

As you can see, it's a pretty modest setup, but the unit seems to run well, which speaks well of both MythTV and Ubuntu.

Anyway, let's get started. Note my sources at the bottom of the page, which you might want to check out if something I do doesn't work for you.

Step 1: Install your hardware.

This should be easy enough, if you follow the instructions. The only thing to keep in mind is that the little cable with the two mini-jacks is there for a reason; specifically, you need to run it from the open port on the TV card to the Line-In on your sound card. If you forget to do this, you won't get any sound.

Step 2: Install Ubuntu.

I'm using Kubuntu 6.06 LTS, because MythTV uses QT, and I used the text-based install disk rather than the desktop installer.

Ubuntu is an easy install. I used the following partition configuration:

root: /dev/hda1 8gb ext3
swap: /dev/hda2 512mb
home: /dev/hda3 6gb ext3
video: /dev/hda4 all-available xfs

It is a good idea to use XFS for your video partition because it is faster and can better handle large files. I note here that I also later altered my /etc/fstab file so that the video partition pointed to /home/mythtv/video. I forget why I did this, but I'm sure there was a reason at the time.

Also, when Ubuntu asks you for your user information, don't put MythTV, as it will cause problems later. Just enter your name, like Steve or Mark or Jean Luc.

Step 3: Prepare your enviornment

Ctrl+Alt+F1 and enter your logon information. At the prompt, type:

# sudo nano -w /etc/apt/sources.list

Add multiverse to the end of all repositories, and uncomment any commented repositories. Exit nano. Type:

# sudo apt-get update

to update your local program database.

From here, I installed the nVidia binary driver (nVidia users only):

# sudo apt-get install nvidia-glx

Once it's down, you need to set up your xorg.conf file. To do this, you can use the Ubuntu script, or you can edit it manually. I will edit it manually so that we can add a few extra things as well, for those of us running MythTV on a TV.

# sudo nano -w /etc/X11/xorg.conf

Then find the section beginning with Section "Device", and change "nv" to "nvidia".

In this same section, add the following lines:

Option "TVStandard" "NTSC-M" (or PAL, NTSC-J, etc.)
Option "TVOutFormat" "SVIDEO"
Option "TVOverScan" "0.5"
Option "RenderAccel" "1"

You may also want to comment out the DPMS line under Section "Monitor".

Save the file and close nano.

Install these final few packages:

# sudo apt-get install dvdauthor mplayer-586

Step 4: Fix your TV-tuner card

Ubuntu seems to recognize the TV-Wonder-Pro as something else, and as a result, it just doesn't work at first. To fix it, follow the following sequence:

# cd /etc/modprobe.d/
# sudo echo "options cx88xx card=4 tuner=44" > cx88xx
# modprobe -r cx8800
# modprobe cx8800

To test it, you can install tvtime and try and watch TV. If everything with the driver is kosher, you should see picture.

Even if you hear sound in TVTime, you may find that it doesn't work right in MythTV later. We should fix that before it starts causing heartaches.

# amixer set Master,0 100%,100% unmute
# amixer set PCM,0 100%,100% unmute
# amixer set Line,0 75%,75% mute captur
# amixer set Capture,0 100%,100% captur


We do this to send the Line audio to the Capture where it can be processed by MythTV. If you just use Line audio, your audio will be a good few seconds behind the video (if it records at all). I also had a problem with the TV audio playing even after I exited MythTV.

Step 5: Now for the fun

Ok, MythTV 0.19 likes using MySQL, but it doesn't like MySQL 5. Here you have to make a choice. Do you install Myth.19 or do you install MySQL 4.1. If you decide to install Myth.19, you need to compile it from source. This guide doesn't follow this route, and so if this is your choice, I recommend you use one of the guides posted below. I'm looking for the easiest way for anyone to install MythTV, and I found that just settling with 0.18 is a bit easier. Once everything in the repositories catches up to the latest version, this will no longer become an issue.

Install the following packages:

# sudo apt-get install mysql-server-4.1 apache2 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql ntp ntp-simple

# sudo /etc/init.d/apache2 restart

Ctrl+Alt+F7 to re-enter X. Open your favorite browser, and type 'localhost'

A phpmyadmin link show appear. Click it, enter 'root' as a username and hit 'go'. Do not enter a password.

Click on the 'Privleges' link. Find the 'root' user in the list, and click the edit privleges icon. Scroll down and enter a new password. Click 'Go'.

And for the love of all that is good and right, remember that password. MythTV will ask for it during install.

Step 6: MythTV

Ctrl+Alt+F1 to get back to your command prompt.

Install the following packages:

# sudo apt-get install mythtv mythbrowser mythdvd mythgallery mythmusic mythvideo mythweather mythweb myth-doc

Then:

# sudo passwd mythtv
and enter the new mythtv password.

# sudo nano -w /etc/group

Add 'mythtv' to the end of 'admin', 'cdrom', and 'plugdev'.

Reboot your computer. When KDM (or GDM) comes up, login as mythtv.

Open a terminal window, and type 'mythtv-setup'. Do this as the mythtv user and not as su.

A lot of the variables in General will depend on your own personal preferences. I think the only thing I changed was the location of my videos and my video cache.

In Capture Cards, I pretty must just used the default settings. The ATI TV-Wonder-Pro does not, to my knowledge, have a hardware MPEG-2 encoder, and so just use the standard capture card option. The video should be /dev/video0. Audio should be /dev/dsp. Save the information and escape to the main menu.

For Video Sources, just enter in your logon information from [http://labs.zap2it.com](http://labs.zap2it.com) and hit 'Retrieve Lineup' to make sure it's working.

Oh, and if you don't have that information already, you'd better go and get it. Your 'Certificate Code' is: ZIYN-DQZO-SBUT. (Note, this is for North American only).

Finally, for Inputs simply link your capture card to your video source using the drop-down menu.

Upon completion, escape out of the setup program.

Now you'll need to fill the MythTV database. To do this, type:

# mythfilldatabase

This process takes a while, so you might want to get a cup of tea.

If you get a few errors, you're probably alright, but if you get lots of SQL errors, then guess what: you're probably running MySQL 5.0. Either you forgot to append a version number when you installed it or you performed an Ubuntu dist-upgrade, which might upgrade that package.

Or, if you're sure you did everything right, re-enter phpmyadmin and drop the mythconverg database and go back to 'mythtv-setup'. Maybe it'll work right the second time.

Step 7: Finalization

So now you're basically done. The last thing to do is enter MythTV by typing (into the terminal):

# mythbackend & mythfrontend

If everything is happy, MythTV will come up, and you can start recording TV.

Keep in mind, that 'Watch TV' is probably going to be choppy unless you have a fast processor. MythTV is made more for recording TV rather than watching live TV.

To get MythTV to start at boot, I had to use the following commands:


# echo "mythfrontend" | sudo tee /home/mythtv/.xsession
# sudo chown mythtv.mythtv /home/mythtv/.xsession

and

# echo "su - mythtv -c \"mythbackend -d\"" | sudo tee /etc/init.d/mythtv-backend

Anyway, that worked for me. Again, if something doesn't work for you, I suggest you check some of my sources below.

Have a lot of fun....

Sources:
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) (primary source)
[http://www.mythtv.org/docs/mythtv-HOWTO-7.html](http://www.mythtv.org/docs/mythtv-HOWTO-7.html)
[http://www.cs.rit.edu/~css8044/?q=mythinstall](http://www.cs.rit.edu/~css8044/?q=mythinstall)
[http://www.ubuntuforums.org/showthread.php?t=186747](http://www.ubuntuforums.org/showthread.php?t=186747)
[http://www.mythtv.org/pipermail/mythtv-](http://www.mythtv.org/pipermail/mythtv-) ... 11489.html
[http://www.mythtv.org/wiki/index.php/ATI_TV-Wonder_VE](http://www.mythtv.org/wiki/index.php/ATI_TV-Wonder_VE)
[http://www.abarbaccia.com/content/view/17/32/](http://www.abarbaccia.com/content/view/17/32/)

---

### Post by atrus123 on 2006-08-02
Changelog:

August 2, 2006 - added MythTV at startup; adjusted the sound commands; added another source; added sources to Ubuntuforums.com (already present on blog)

Hope this helps.

---

