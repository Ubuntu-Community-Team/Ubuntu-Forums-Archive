---
title: "Black screen after messing with desktop effects"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Teleka on 2008-08-02
Well I just installed linux and I enabled the desktop effects, and went to the next tab and pretty much check marked everything except for screen recording and stuff. Anyway, the problem is, my screen is now black and when I click I get some grey boxes where my pointer is (I can still see it). I was wondering if there was a way to reset the effects to their normal state, or off? Thanks. Also the problem isn't my gfx card (8800 gts). Thanks for any and all help.

---

### Post by eightmillion on 2008-08-02
Try these commands and restart X:
> rm -rf ~/.kde/share/config/compiz*

> rm -rf ~/.compiz/

---

### Post by eightmillion on 2008-08-02
You may also have to remove '~/.config/compiz'
> rm -rf ~/.config/compiz/

---

### Post by Teleka on 2008-08-02
Alright sorry if this is something obvious I should know, but I tried typing those in (in the konsole I think it was) and nothing happened (that I'm aware of). I don't even know if I typed those commands in the right place. So if you don't mind, a guide from boot up to the last keystroke would help of what to do. Thanks.

---

### Post by eightmillion on 2008-08-02
Those commands should have any output if they finish without errors. All they do is delete a couple of config files. After you've done them, do this command:
> sudo pkill Xorg

---

### Post by Teleka on 2008-08-02
Ok I tried typing in every command that you wrote like 4 times and the only one I got a response out of was 'sudo pkill Xorg' (which gave me root privelages or soemthing). I'm not sure if I'm inputting these in the correct place.

---

### Post by eightmillion on 2008-08-02
What happens when you log in to kde?

---

### Post by Teleka on 2008-08-02
I get a black screen, and only my cursor shows up.

---

### Post by eightmillion on 2008-08-02
Where are you inputing these commands? There should be an option under 'sessions' on your log in menu that says something like 'recovery console'. You should use that.

---

### Post by Teleka on 2008-08-02
There isn't that specifically. I tried using failsafe, and the other choice that opens up a console below it. neither do anything when I type in the commands (except for 'sudo pkill Xorg' that always does something).

---

### Post by eightmillion on 2008-08-02
Use your failsafe option and type in this command:
> sudo apt-get remove compiz
After this finishes type **exit** and then select KDE from the sessions menu and log in normally.

---

### Post by Teleka on 2008-08-02
Well the command worked but nothing happened. I got this message:
```
Compiz is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

My friend said to delete a kde folder somewhere to get rid of the changes I made. Btw I downloaded a driver so I can see my files from vista, if you know how to get to what I need to delete by folder, if that made any sense.

---

### Post by eightmillion on 2008-08-02
Try failsafe again and run this command:
> rm -r ~/.kde/share/config/compiz* ~/.compiz/ ~/.config/compiz/

This should get rid of any settings that are causing you problems. Then type **exit** again and log in. These commands will not have any output if they finish with no errors. If you get and error like: **rm: cannot remove `~/.compiz/': No such file or directory** that's ok.

---

### Post by Teleka on 2008-08-02
Ok I typed in the command successfully and got those errors. But when I get back in, I'm still having the problem.

---

### Post by OldTimeTech on 2008-08-02
this may sound defeatist and I don't want it too....

But since this is such a new install, I wouldn't think you've had a chance to do a lot to it or have a lot on it....

I would use gparted and reformat the hard drive and then re-install Ubuntu....at that point you would have your screen back and know to try one click box at a time ;)

---

### Post by Teleka on 2008-08-02
Well i was thinking about erasing that partition but i wanted to know if there was anything I could do before I resorted to that, but I guess there isn't. Alright, I formatted that partition and reinstalled ubuntu and it was working fine till I started messing with the effects again. then as soon as I enabled the desktop effects, the screen went black again, and a window popped up that said do you want to keep these effects, I said no, and it went back, i tried checking the box again and hitting apply, and the screen didn't go black. So I was thinking that I just had to click no and try it again, so i spend like 30 mins customizing my stuff, and something happens so that I have to log out, and when I log back in the screen is all black and crap. I don't really want to use linux if it doesn't look good :/. Anyone have any ideas?

---

### Post by Syock on 2008-10-12
The problem here is not because of Compiz, I think it's caused by KWin's compositing manager. I'm having a problem here too, and I can't find a way to enable the desktop effects yet.

My problem was: desktop becomes black after logging in, pointer is visible. If yours is the same, please try out these steps:

1. As soon as you get the black screen, press ctrl-alt-F1 to go to tty1
2. Login with your username and password.
3. Do this:
```
nano ~/.kde/share/config/kwinrc
```
4. Under the [Compositing] section, edit the line with:
```
Enabled=true
```
change it to
```
Enabled=false
```
save by ctrl-O, enter
5. Exit by ctrl-x, go back to X (the black screen) by ctrl-alt-F7
6. Press ctrl-alt-backspace (to restart KDM).

You should have your desktop again, without the fancy effects.

If you ever find solution to enable the effects, please share it with us!

---

### Post by barzam on 2008-11-19
Thanks! 
I managed to reset the settings and have visibility again! Now I just need to find a way to enable it I guess.

---

### Post by tegnoto89 on 2008-12-09
I've figured it out for my computer at least.

I just went to hardware drivers, and installed the driver for my 3D accelerated graphics card.  Now they do work, though they slow my computer down significantly, so I left them alone

---

