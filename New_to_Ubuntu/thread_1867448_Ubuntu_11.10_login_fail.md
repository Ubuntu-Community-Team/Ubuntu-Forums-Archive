---
title: "Ubuntu 11.10 login fail"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by lordnemo on 2011-10-22
I recently upgraded Lubuntu on my laptop from 11.04 to 11.10 and now i can't login. some people have recommended removing ~/.Xauthority from the home folder using the terminal but every time i log out of the terminal and log back in the file reappears and i still can't log in through the GUI. are there any solutions? and please give easy, step-by-step instructions i'm still pretty new to linux.

edit: The .Xauthority file reappears whenever i try to log in through lxdm. i attempted to install gdm and lightdm but could get neither of them to work.

---

### Post by lordnemo on 2011-10-23
bump.

does anyone have a solution? my only other option is to reinstall my OS and that will delete several items i don't want to lose.

---

### Post by AnythingBut on 2011-10-23
I had a similar problem.  But removing the .Xauthority file fixed it for me.  The file gets created by an X server instance, which is why it keeps coming back.

Once you're in the terminal, try running these commands.

```
sudo killall lightdm
```

followed by

```
startx &
```

The first will stop lightdm (if you want it back just restart your computer).  The second will start an X session without using lightdm.  When I did that, it was giving me .Xauthority errors.  Does yours?

---

### Post by dunbrokin on 2011-10-23
I have the same problem....I cannot log into one of my profiles since 11.10. Fortunately one of the other profiles has full administrator access and so I can get at the files via sudo nautilus....but how do I get the original profile to work again?

---

### Post by AnythingBut on 2011-10-23
Have you tried removing that users .Xauthority* files?

In a terminal,
```
cd ~<username>
sudo rm .Xauthority*
```

If permissions don't let you go to that user's home directory (the first command fails), you can first use
```
sudo su <username>
```
to switch to that user in the terminal.

---

### Post by dunbrokin on 2011-10-23
Thanks, that worked for me....

---

