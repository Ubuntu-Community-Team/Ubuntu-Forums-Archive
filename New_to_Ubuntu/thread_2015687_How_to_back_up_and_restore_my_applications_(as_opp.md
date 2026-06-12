---
title: "How to back up and restore my applications (as opposed to user data)?"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by ub07 on 2012-07-03
I recently installed Ubuntu 12.04 on a laptop. Everything worked fine, but now I am facing reinstalling it because of errors and a change in boot behavior resulting from stupidity on my part.

I would like to know how to back up the applications that I downloaded. I have dial-up internet, and it would take a huge amount of time to download all that software again. Most of the backup programs that I come across focus mainly on backing up the home directory/partition, but I really haven't anything that wouldn't fit on a very small USB drive in my home folder. I need the ability to back up my applications and to restore them again after I reinstall Ubuntu.

Does anyone have any suggestions on how to do this?

---

### Post by cipherboy_loc on 2012-07-03
What exactly is screwed up with your boot? Maybe we can help you fix that instead of a reinstallation.


Cipherboy

---

### Post by JKyleOKC on 2012-07-03
If you obtained all those applications through the Software Center or other apt-related program, the package files should be in your apt cache directory. You could copy them to a flash drive or external drive from there, then restore them to the same directory after reinstalling your system and run a re-install action to put them back. This would eliminate the need to download all of them again, but might not include all updates that have come out since the original installation (I found 175 updates to my 12.04 test system today when I fired it up after leaving it unused for a month or more).

Unfortunately I don't know the exact location of that cache directory for your system, since I'm still using 10.04 for most of my work and on top of that have Xubuntu rather than the plain Ubuntu system. However I'm sure someone with more detailed knowledge will jump in to help; I just wanted to make you aware that the download time can be avoided by some judicious backup actions...

---

### Post by Paqman on 2012-07-03
All the packages you downloaded to install your apps are sitting in /var/cache/apt/archives, if you copy them onto a USB stick then copy them back into the new system you will be able to reinstall using them. You'll need to be offline, otherwise the package manager will try to use the newer packages from the repos instead.

That location and those files are owned by root, so you'll need to use the file manager as root:
```
gksudo nautilus
```
or open a terminal and use:
```
sudo mv /move/from/location /move/to/location
```

You can also [generate a list of all your installed packages]("http://ubuntuforums.org/showthread.php?t=261366") and reinstall with one command.

---

### Post by ub07 on 2012-07-03
Thanks, guys, you've been a big help. One question I have though is how do I let the Software Center know that those packages are in the cache directory and not to download them again? Is there an option to  tell it to look on my disk first?

About the boot problem,  it simply takes longer to boot and the splash screen is now shown for only a fraction of a second before going to the login screen. Ordinarily, I would think that this might have been caused by installing the Gnome Desktop, but at around the same time, I tried to log in as root from the login screen. (Yes, I changed the root passwd). The system just sat there spinning and I had to shut it off and restart it and that is when the boot problem began.

 Also, when I did log back in, I got a message stating that there is a system problem and it gave me the option to report it. I was still having problems getting the modem to work so I couldn't report it. When I did finally get the modem working and reported it, I stopped getting the error message. For some reason, I think the problem is still there and it just doesn't let me know because it has been reported. Anyway, I need a stable system, and for peace of mind, I want to do a re-install.

---

### Post by Paqman on 2012-07-03
> **ub07 said:**
> Thanks, guys, you've been a big help. One question I have though is how do I let the Software Center know that those packages are in the cache directory and not to download them again? Is there an option to  tell it to look on my disk first?


It will always try to use the newest packages it can find, which will be the ones in the repos if you're online. If you're offline or if the packages in the repos aren't newer it'll use what's in the cache. So just make sure you're offline when you re-install the packages and as long as the cache has a copy of everything you need it'll work fine.

---

### Post by mapes12 on 2012-07-04
These are worth considering:-

[http://www.remastersys.com/](http://www.remastersys.com/)

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

I've used Remastersys to create a custom CD to reinstall my system exactly how I like it, apps and all. It works perfectly for me, and an easy GUI to help you on your way.

I've not used AptonCD but I guess it does the same job as the other posts have suggested but via a GUI.

---

### Post by Quackers on 2012-07-04
Have a look here too :-)

[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by mastablasta on 2012-07-04
another option is to use Linuxmintbackup tool (available in Ubuntu via PPA i believe). it's a nice GUI with 4 buttons. 
 
[IMG]http://community.linuxmint.com/img/screenshots/mintbackup.png[/IMG]

---

