---
title: "Xubuntu turned gray and empty after updates"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by Ulvdatter on 2012-09-27
Hi!

Today I have installed some upgrades (not too sure which ones). I also deleted Thunderbird and some other mail and chat stuff. Now all that meets after the log in screen, is a gray emptiness and and error message saying: "unable to launch startxfce4 x session" followed by something my boyfriend did not bother to write down, but we think it was something like: unable to return to default setup... 
After closing the error message it does not respond to anything mouse related. We are quite blank when it comes to keyboard commands, so we have not tried much in that direction.

Mayday):P

---

### Post by doktorOblivion on 2012-09-27
If you can get a console session (if not reboot and go into recovery mode).  Once there login for that user and try and deleting your cache,
```

rm -fr .cache

```
From your home directory.

---

### Post by critin on 2012-09-27
Try restarting and when you get to login, click on the cog in upper right corner (of login box) and choose another option.  xfce4 session is broken.  Don't choose xfce4.  xubuntu should be there.

Add: It may not be a round 'cog'.  But there may be an arrow or something below the user name that is clickable--explore.

---

### Post by OrangeCrate on 2012-09-27
<Nevermind - I had two instances of the forums open, and I accidently posted a response to another thread here.>

---

### Post by critin on 2012-09-27
>  I also deleted Thunderbird and some other mail and chat stuff. 

Be careful uninstalling stuff.  Libraries often serve more than one app.  If you want to just remove something from the panel, right click and 'remove' usually works.

---

### Post by Ulvdatter on 2012-09-27
Thanx for good suggestions, but I am sorry to say they did not solve my problem. The cog wheel method did not work as there was no such to be found. In the systems present state, and with my very microscopic skills I am not able to enter "system" or anything else. I am not quite sure what a console session is, but I tried typing:  rm -fr .cache in what ever it is that appears when you press ctrl+alt+F2, but nothing happened...

---

### Post by Ulvdatter on 2012-09-27
Oh, and by the way. Can anyone tell me how to connect to a wireless network by command line?

---

### Post by rai4shu2 on 2012-09-27
Fun stuff, but why not: [http://tldp.org/HOWTO/Wireless-HOWTO-5.html](http://tldp.org/HOWTO/Wireless-HOWTO-5.html)

---

### Post by Ulvdatter on 2012-09-27
Ha-ha! I kind of drowned in information from that link : )  Thanks anyway.

---

### Post by black veils on 2012-09-27
> Now all that meets after the log in screen, is a gray emptiness and and error message

so you do have a normal graphical login screen which you use to sign-in? i cant remember exactly, but i think at the bottom of the screen there will be the word *session* or *xubuntu*, click it to choose another session option to see if you can get a functional environment, then enter login details as usual.

---

### Post by Ulvdatter on 2012-09-27
I have tried that already, but to my disappointment there was no options under that button. (It just changed from "session" to "xubuntu".)

---

### Post by black veils on 2012-09-27
recovery mode is your friend, so is booting live media (ubuntu cd or usb stick), like someone said.

enter recovery mode by holding down the shift key as you boot the computer, you will see a black screen as it loads grub. when it is loaded you will see a list of items like kernel, memtest and recovery. choose recovery, then the networking option, then go back to menu and choose drop to root shell.

as for what commands to run for removing which directories, i do not know. but be careful not to make a mistake with a command or you could delete a lot more than intended.

i suggest that before using commands, you boot into a live cd/usb stick to backup all your personal files and application configurations, like email, web browser, messenger etc (get those by being in home directory and pressing Ctrl+H to show hidden items).

---

### Post by Ulvdatter on 2012-09-27
Alright! I'm in recovery mode! I chose the network option, and returned to the menu, wich caused the computer to reboot, so I'm typing while waiting...
I'm not sure I quite understand what is supposed to hapend next.  Removing directories? Sounds scary!!!

---

### Post by Ulvdatter on 2012-09-27
Well, I'm back in recovery mode, but not quite sure what to do next...

---

### Post by black veils on 2012-09-27
start again then, go into recovery mode, straight to root shell option, enter this command```
mount -o remount,rw /
```to gain privileges and network. make sure to type it correctly.

then try the previously mentioned command to remove a .cache directory. dont do this unless you have a backup of your files and application data, in case a mistake is made.

---

### Post by Ulvdatter on 2012-09-27
[FONT=monospace]By "previously mentioned command", do you mean: "rm -fr .cache" ?
[/FONT]

---

### Post by Ulvdatter on 2012-09-28
Hooray! I solved it:p
I used my mobile phone as modem, and got into some mind of terminal where I typed "startxfce4" and the terminal suggested some kind of installation command, which I of course agreed to. After a reboot everything looked just as gray and gloomy as it has been the last 12 hours, but to my joy and delight the gloom was now created by a gray desktop, and everything else seems to be back to normal. 

After being at verge of war, the future  now appears to bring peace and happiness to our humble house, as our Earthbound saves in the SNES-emulator is no longer lost:p

---

