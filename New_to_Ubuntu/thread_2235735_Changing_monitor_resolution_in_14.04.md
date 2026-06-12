---
title: "Changing monitor resolution in 14.04"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by wilburdee on 2014-07-22
Hi - I just installed lubuntu 14.04 on two older computers. One of these has a vga graphics card & the other one has an nvidea 7600 card.
I'm using a 19" standard monitor capable of either 1024x768 or 1280x1024.
When I used Win XP on either of these computers I used 1024x768.
After installing 14.04 on one computer I can go to 'monitor settings' & select my preferred 1024x768 & then it will change to that
setting. It will revert back to 1280x1024 after I reboot.
I can live with that.
Now on the other computer I can not change the monitor setting at all. the option for the lower setting is there, but when I click 'apply' nothing happens.
I really need to figure out how to get the 1024x768 setting working because it's just too hard to read anything at the other setting.
Please also note that I'm not very good with anything command line related.
Other than this one problem, I'm pretty happy with lubuntu.
thanks for any help you can give me.

---

### Post by TheFu on 2014-07-22
So **lxrandr** doesn't work?

alt-F2, then type in lxrandr<enter>

---

### Post by wilburdee on 2014-07-23
thanks for the reply TheFu.
I really don't even know what lxrandr is.
I did see it mentioned when I was googling this problem.
Guess I've got some studying to do.
Don't be fooled by my forum join date of 2005. Back then I think I put Ubuntu on one of these same machines 
using wubi, but I only used it as a backup OS very briefly & then just kept using Windows.

---

### Post by TheFu on 2014-07-23
It is a program that is part of LXDE that lets us set the screen choice and screen resolution.
Run it as a normal user. No study needed, but you can read the 'manpage' if you like.  **man lxrandr** is the command.

---

### Post by wilburdee on 2014-07-24
TheFu - wow, that's great news! Also, I just now noticed that you told me exactly how to
open & run it in your other post.
I'll try it out later today.
Thanks
Jim

---

### Post by wilburdee on 2014-07-24
I tried using lxrandr & that didn't work. I got this error message: warning: output I-O not found;ignoring.
But maybe this is part of the problem? I have the driver for my nVidia 7600 GT card installed(xserver?).
It is version 304.117. I have messed around with those settings & they don't work either.
So would I be better off removing the nVidia driver? If so,how would I go about removing it?

---

### Post by TheFu on 2014-07-24
Please share the output from:```

$ echo $DISPLAY

$ xrandr
```

Thanks.

For someone new to Linux, never install software outside the package repositories - DO NOT GRAB A .deb file and install it - unless there is a specific, required, reason.  It is generally a bad idea to download drivers directly from nvidia. Installing a .deb file will break dependencies, if not immediately, later.

---

### Post by wilburdee on 2014-07-25
hope I did this right.
here's the output: 0$ xrandr
Thanks again

---

### Post by kira-yamato-2008 on 2014-07-25
I had sort of the same issue you had on your first computer for a tick then I stumbled upon a solution. After you set your desired resolution you need to go back to "Monitor Settings" and hit the save button too. That should stop it from reverting back to the original resolution on reboot. Hope that helped a little.

---

### Post by wilburdee on 2014-07-26
Well, I reinstalled Lubuntu 14.04 w/o the nvidia driver & I still have the same problem.
Will reverting to an older version of lubuntu help?
I really can't even use this at all at this resolution(1280x1024) because it's just too hard to see things.
I know I could somehow set dpi for larger text,etc. but that will only partially help me.
thanks again.

---

### Post by kira-yamato-2008 on 2014-07-26
Well you might want to try a different flavor like Xubuntu or maybe even Linux Mint. However I think you messed up the commands. If you're using or want to use Nvidia binary drivers then this thread: [http://ubuntuforums.org/showthread.php?t=1769989](http://ubuntuforums.org/showthread.php?t=1769989) might help you out. They did leave one step out though. At the bottom of the Nvidia X Server setttings there is an option on the left that says "nvidia-settings Configuration" select it and press the "Save Current Configuration" option and save it so your resolution doesn't revert. Also instead of the copy and paste method when doing resolution just save the xorg.conf from the tool, it worked for me.

---

### Post by sudodus on 2014-07-26
There is only one supported version of Lubuntu, and it is 14.04 LTS.

Does it work temporarity (until reboot) to run this command in a terminal window?

```
xrandr -s 1024x768
```

In that case I can suggest a work-around, that might be good enough for you. Add a line into the file autostart, that will run that command in a temporary terminal window. Copy and paste the command from my reply to a terminal window and press Enter to run it.

```
echo 'xterm -e xrandr -s 1024x768' >> ~/.config/lxsession/Lubuntu/autostart
```

I tested that it works in a computer with Lubuntu 14.04 LTS.

-0-

If it does not work, you can remove the line

```
xterm -e xrandr -s 1024x768
```

 with an editor

```
leafpad ~/.config/lxsession/Lubuntu/autostart
```

---

### Post by TheFu on 2014-07-26
Changing distros isn't going to matter. This is an X/Windows thing - NOT a distro thing.

I'd still love to see the output requested from **xrandr**. Can that please be provided?

---

### Post by wilburdee on 2014-07-26
Big thanks to you all for the help & quick replies!
I finally got this working after looking at a wiki page for Ubuntu.
Basically, following their directions, I reinstalled the nvidia driver previously mentioned & changed resolution in nvidia settings & then saved that config. & rebooted & I'm now at 1024x768 & I can actually read this forum in FF - no more going into the other room to my main computer just to read & reply to this forum.
Now, I had previously done on my own what those wiki directions told me to EXCEPT; I didn't save the config. file & I didn't reboot after saving it.
I think I'm really going to love this distro, especially after seeing that it's only using 7 - 10% cpu w/ FF running. WOW!
XP used 70 to 90%!
Again; thank you all & I know I'll be back with more dumb noob questions.
Jim

---

### Post by sudodus on 2014-07-27
Congratulations and thanks for sharing your solution :KS


Please click on **Thread Tools** at the top of the page and mark this page as SOLVED

---

