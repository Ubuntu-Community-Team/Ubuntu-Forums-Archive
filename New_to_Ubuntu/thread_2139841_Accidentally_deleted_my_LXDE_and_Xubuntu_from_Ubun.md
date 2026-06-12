---
title: "Accidentally deleted my LXDE and Xubuntu from Ubuntu Greeter"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by Leslie Dorner on 2013-04-28
I did this:

cd /usr/share/xsessions
sudo rm LXDE.desktop
sudo rm xubuntu.desktop
sudo rm xfce.desktop

I installed LXDE and xubuntu-desktop using the Ubuntu Software Center. I don't see the option to select either one in the Ubuntu Greeter. How do I get them back so I can log into LXDE or Xubuntu?

Can you post your default LXDE.desktop and xubuntu.desktop configuration files or attach them from your /usr/share/xsessions directory? Thank you.

---

### Post by kamranm1200 on 2013-04-28
Yikes! Just uninstall LXDE and Xubuntu and then reinstall them and they should reappear in the Unity Greeter. Hope this helps! :)

---

### Post by Leslie Dorner on 2013-04-28
I tried that. I still don't see LXDE.desktop or xubuntu.desktop in my /usr/share/xsessions directory. I need someone to upload their files as an attachment so that I can download them and put them back into my /usr/share/xsessions directory. Thanks.

---

### Post by agent-squirrel on 2013-04-28
You could try running.

```
sudo apt-get install --reinstall LXDE
```

---

### Post by Leslie Dorner on 2013-04-28
No, that did not work either. I need a copy of the original default LXDE.desktop and xubuntu.desktop files found in /usr/share/xsessions. If someone who has either one installed could upload their copies as attachments, then this will solve my problem permanently. Thank you.

---

### Post by Leslie Dorner on 2013-04-29
I typed this in the terminal:

sudo apt-get install lubuntu-desktop

I got Lubuntu Desktop installed which is the full fledged version of LXDE. It's super ultra fast and responsive especially with my System76 Lemur Ultra (lemu4) and Ubuntu 13.04 64 bit. Zinio Reader 4 doesn't work, but I can switch back to Ubuntu Unity or GNOME to make it work. I'm really impressed that I got this to work without breaking my system. Now, I got to work on Xubuntu Desktop.

---

### Post by steeldriver on 2013-04-29
You can use apt-file to find out exactly which package contains the missing desktop files:

```
$ apt-file search LXDE.desktop
lxde-common: /usr/share/xsessions/LXDE.desktop
$ 
$ apt-file search xubuntu.desktop
xubuntu-default-settings: /usr/share/xsessions/xubuntu.desktop
$ 
```

---

### Post by Leslie Dorner on 2013-04-29
I get the same results. Xubuntu.desktop is found in /usr/share/xsessions and I'm missing that file no matter how many times or ways I try to re-install xubuntu-desktop or xfce4. I need a copy of xubuntu.desktop from /usr/share/xsessions from someone else.

This should be a piece of cake to upload this file as an attachment. It's not a security risk.

---

### Post by Leslie Dorner on 2013-04-29
My mother gave me her  old ASUS 1015PE netbook. I installed Ubuntu 13.04 64 bit on it. I  installed lubuntu desktop and xubuntu desktop. I copied the  lubuntu.desktop and xfce.desktop and xubuntu.desktop files from the ASUS  PC to my System76. It worked. I am using Xubuntu desktop environment  now. Solved.

---

### Post by kamranm1200 on 2013-04-29
If any of these solutions aren't helping you, then why don't you just reinstall the OS?

---

### Post by Leslie Dorner on 2013-04-29
I solved this problem on my own without having to re-install the OS.

---

### Post by Leslie Dorner on 2013-04-29
I already solved this problem myself.

---

### Post by deadflowr on 2013-04-29
> **Leslie Dorner said:**
> I solved this problem on my own without having to re-install the OS.

That's great.

Do you have a workable solution you can post?

Maybe help others later on?

---

### Post by Leslie Dorner on 2013-04-29
Copy LXDE.desktop, xubuntu.desktop, and xfce.desktop from one PC with the same Ubuntu 32 or 64 bit installation as the target PC from the /usr/share/xsessions directory. That's it. Ubuntu Greeter will display it as an option to log into.

---

### Post by deadflowr on 2013-04-29
well, that looks like a workable solution.

Now, my advice yo you is, if you want to try doing what you attempted to do again, use the mv command instead of the rm command.

And then just move the file somewhere where you can re-access it and put in back in if you want.

```
sudo mv file where-the-file-is-going
```

---

### Post by Leslie Dorner on 2013-04-29
Yes, I agree with your mv command rather than the rm command. It would have saved me some unnecessary pain. I made a full copy and backup of my /usr/share/xsessions onto other media just in case I run into this similar problem in the future.

---

