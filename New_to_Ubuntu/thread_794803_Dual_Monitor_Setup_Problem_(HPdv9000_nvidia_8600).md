---
title: "Dual Monitor Setup Problem (HPdv9000 nvidia 8600)"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by E-babe on 2008-05-15
Hi everyone,

I have been trying to get my notebook to do dual monitor with my 17" lcd monitor. I have already tried playing with the configurations in the "Nvidia X Server settings", I have no clue as to why my 17" lcd has nothing shown after i apply the desired setting. 

I just want to do what windows XP does, show two different desktops (not the same contents on two monitors), and i have success in doing so in windows xp so it's not connection problem.

Any help is greatly appreciated. :) :confused:

---

### Post by starcannon on 2008-05-15
I did dual monitor on an HP DV2600 with Nvidia 8400m gs card, I used nvidia-settings (a nice nvidia gui) worked like a champ, try that see how it goes, try running it from command line, if it complains that it isn't installed grab it from synaptic package manager.

---

### Post by E-babe on 2008-05-15
I actually tried that already with the nice gui interface of nvidia-settings under Administration. no luck with that :( 
If anyone needs my hardware information i 'd be glad to provide.
I'm using 8.04 ubuntu by the way...

---

### Post by EXCiD3 on 2008-05-15
Sometimes changes require you to restart the xserver before the 2nd display is usable. You can do this by pressing Ctrl-Alt-Backspace after saving your changes. Try that if you havent already.

---

### Post by E-babe on 2008-05-15
when i try to save to xorg.conf file, it says it's unable to save to it...may be that's the reason? can anyone tell me why is that

---

### Post by herbster on 2008-05-15
You're not running nvidia-settings as root, so you don't have permission to write to the /etc/X11/xorg.conf. Run it as:

```
sudo nvidia-settings
```

---

### Post by E-babe on 2008-05-15
OH!!! sudo is always the reason to everything
Let me give that a try and let u know if it works

---

### Post by E-babe on 2008-05-15
Ok. i finally got my dual monitor to work, BUT there 's a slight problem. I know i am picky, but how do i use 1 wallpaper on each screen? i mean, it stretched my wallpaper onto both screen which looks very unpleasant. Thank you!

---

### Post by herbster on 2008-05-15
You can use nitrogen. I don't know if it's in the repos for Ubuntu, you may wish to try:

```
sudo apt-get install nitrogen
```

Or open the Synaptic Package Manager and search for it. You can run it as such:

```
nitrogen --sort=alpha /path/to/wallpapers/
```

And it will show you the wallpapers in the selected folder, you can select the one you wish and tell it which head to use.

---

### Post by E-babe on 2008-05-15
it's not in the repos :(
what can i do to add

---

### Post by aamukahvi on 2008-05-15
> **E-babe said:**
> it's not in the repos :(
what can i do to add
Maybe just paste two images side by side into a bigger image and use that?

---

### Post by E-babe on 2008-05-15
that actually sounds like a feasible solution, but i am not a graphic program user myself. Is there any GUI program that helps u stitch the two wallpapers i have? or is there an easy way? Thanks :)

---

### Post by herbster on 2008-05-15
[http://projects.l3ib.org/nitrogen/](http://projects.l3ib.org/nitrogen/)

Perhaps grab the deb near the bottom, a link to them.

---

### Post by E-babe on 2008-05-15
When i do nitrogen /my/directory/ , nothing is shown in the program. I also tried your way... nitrogen --sort=alpha /my/directory/
do u know why's that, herbster?
Thanks for all your help

---

### Post by herbster on 2008-05-15
You're probably not inputting the correct path. What's the exact path to your wallpapers? Also, run it from the terminal and paste any output that shows.

---

### Post by E-babe on 2008-05-15
This is the output that i got from nitrogen:

name@name-laptop:~$ nitrogen /home/name/Pictures
terminate called after throwing an instance of 'std::out_of_range'
  what():  basic_string::assign
Aborted
name@name-laptop:~$

---

### Post by EXCiD3 on 2008-05-15
If you are running Compiz and have the advanced configuration installed (sudo apt-get install compizconfig-settings-manager) and System > Preferences > Advanced Desktop Effects Settings > Desktop Cube > Appearance > Background Images. You can setup the images with this instead of using nitrogen. But you will need to be running compiz.

---

### Post by E-babe on 2008-05-16
Hey thanks a lot i finally got it to work with nitrogen.
I 'm not running compiz so i dunno if i should install that.
Anyway, this is probably why i have switched from windows to linux, i get so much more help here and there're always so much to learn.

---

### Post by EXCiD3 on 2008-05-16
> **E-babe said:**
> Hey thanks a lot i finally got it to work with nitrogen.
I 'm not running compiz so i dunno if i should install that.
Anyway, this is probably why i have switched from windows to linux, i get so much more help here and there're always so much to learn.

Yep, the users here are always so helpful. At first i thought you were saying you were switching to linux because you could change your wallpapers like this. :lolflag:

If you arent running compiz there is no reason to install what i mentioned. It was just a simple solution to your problem had you been using compiz. I find compiz is awesome to show of, just not very productive in the long run. I tend to customize and play with it way toooo much. ;)

---

### Post by pingmai@yahoo.com on 2008-08-18
> **E-babe said:**
> Ok. i finally got my dual monitor to work, BUT there 's a slight problem. I know i am picky, but how do i use 1 wallpaper on each screen? i mean, it stretched my wallpaper onto both screen which looks very unpleasant. Thank you!

Can you send me your xorg.conf

---

### Post by herbster on 2008-08-18
You can use nitrogen to set wallpapers per monitor.

---

### Post by cooldude on 2008-12-11
For me I cannot put different wallpapers on separate screens on nitrogen. It just lets me put one.

---

### Post by c4rson on 2008-12-18
i messed with this for over two hours, frustrated as hell. i thank you very much your awesome. i read this and it took 10 seconds. thanks --Carson

---

