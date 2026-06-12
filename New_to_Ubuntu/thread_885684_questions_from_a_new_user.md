---
title: "questions from a new user"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by xrc6 on 2008-08-10
1. i opened repository and i think i installed the nvidia driver, but i'm not sure. i rebooted but how do i know?

2. how do i change the resolution of my desktop?

3. visual effects dont work. it says "desktop effects cannot be enabled"...how informative. at least windows vista is more informative.

4. i have a razer barracuda ac-1 soundcard...but cant find a driver for it. am i screwed from being able to use it?

5. i thought i downloaded some wallpaper stuff in repository, but cant find it, where are those things downloaded to?

6. is there anyway to have a video play as the desktop background? like dreamscapes for Vista OS?

thanks in advance

---

### Post by Ryadt on 2008-08-10
Can you first post the ouput of ```
lshw -C Display
```

---

### Post by kk0sse54 on 2008-08-10
To change the resolution you have to edit your menu and add Screens and Graphics. Once you have done this go to Other > Screens and Graphics and it will enable you to change the resolution and check what video driver you have installed and allows you to change it. As for your wallpaper right click on the desktop and click Change Desktop background. From there you can set your wallpaper and import new ones.

---

### Post by suprfish on 2008-08-10
1. Do you see the nvidia logo when you booted up? Make sure that you installed the driver from **System > Administration > Hardware Drivers**.

2. Can you not change it from **System > Preferences > Screen Resolution**? If you cannot, open up a terminal (**Applications > Accessories > Terminal**) and copy and paste the outputs of these commands (separately): "**cat /etc/X11/xorg.conf**" and then "**cat /var/log/Xorg.0.log | grep NVIDIA**".

3. There are various reasons it might not work. Open up a terminal (**Applications > Accessories > Terminal**) and enter the command "**compiz --replace**". Copy and paste the output here.

4. Maybe, see other posts

5. What were the packages?

6. Probably, but as far as I know, no one has developed something like that.

---

### Post by WRDN on 2008-08-10
> **xrc6 said:**
> 1. i opened repository and i think i installed the nvidia driver, but i'm not sure. i rebooted but how do i know?

2. how do i change the resolution of my desktop?
**System > Preferences > Screen Resolution**


3. visual effects dont work. it says "desktop effects cannot be enabled"...how informative. at least windows vista is more informative.

[B]To enable them, you may need the nVidia driver, from [www.nvidia.com](www.nvidia.com). What graphics card are you using?

If and when you want to install the driver, boot the machine and at the login prompt, press Ctrl, Alt and F1. Now login.
Once you have logged in type:

```
sudo /etc/init.d/gdm stop
```

Now, change to the directory of the nVidia driver, and type:

```
sudo sh [driver].run
```

This will run the file. Once it has installed, type:

```
sudo /etc/init.d/gdm start
```
[/B]


4. i have a razer barracuda ac-1 soundcard...but cant find a driver for it. am i screwed from being able to use it?
**Is the driver available on the manufacturers website?**

5. i thought i downloaded some wallpaper stuff in repository, but cant find it, where are those things downloaded to?
**What package did you download/ install? All packages that have downloaded, do so to /var/cache**

6. is there anyway to have a video play as the desktop background? like dreamscapes for Vista OS?
**Not that I know of, sorry**

thanks in advance

Comments in **bold**

---

### Post by suprfish on 2008-08-10
Info on #4:

Your sound card should be supported by ALSA ([here]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Razer")). So it should work in Ubuntu oot box (have you tried it?). Copy and paste the output of "**modprobe --list | grep oxygen**" into a new post.

---

### Post by xrc6 on 2008-08-10
> **Ryadt said:**
> Can you first post the ouput of ```
lshw -C Display
```

huh?

> 1. Do you see the nvidia logo when you booted up? Make sure that you installed the driver from System > Administration > Hardware Drivers.
i checked, nothing there...so how do i download and install it?

> As for your wallpaper right click on the desktop and click Change Desktop background. From there you can set your wallpaper and import new ones.
yeah, i tried that but i didnt know where the wallpapers i thought i downloaded in repository put them..so basically i cant find any but i'll just manually download some from the net..thanks

> 4. i have a razer barracuda ac-1 soundcard...but cant find a driver for it. am i screwed from being able to use it?
Is the driver available on the manufacturers website?

no but thought i'd double check with you guys, hopeing someone wrote one for it or something

> Once you have logged in type:

Code:

sudo /etc/init.d/gdm stop


wow, linux is more difficult than i hoped :(
but my card is a Nvidia gtx 280

> have you tried it?). Copy and paste the output of "modprobe --list | grep oxygen" into a new post. 
sorry, i thought i was in the Noob section of the forum..thats way beyond me since i dont see a modprobe program in my apps list, i'm lucky enough to figured out how to install linux on this computer much less anything else.

> 6. is there anyway to have a video play as the desktop background? like dreamscapes for Vista OS?
Not that I know of, sorry
i once read there is a video player that can do it but cant remember its name, but thanks anyway.

i'll be happy enough to get nvidia driver installed at the very least ....thanks in advance

---

### Post by xrc6 on 2008-08-10
alright, i downloaded a driver from nvidia but it wont run..tried to open it in packag emanager and nothing..why is linux so freakn difficult.

[IMG]http://img527.imageshack.us/img527/2064/screenshothc9.png[/IMG]

---

### Post by huxterby on 2008-08-10
Hi xrc6.

Linux does take a bit of getting used to huh?

Ok, firstly, if somebody posts a command in a code box like this:
```
sudo lshw -C Display
```

It just means that you have to open the terminal, copy and paste the command and hit enter and some information will appear.

The terminal window is located at: Applications > Accessories > Terminal

This is what comes up when I issue the command: (Nvidia Geforce fx 5200)
```
huxterby@ubuhh:~$ sudo lshw -C Display
[sudo] password for huxterby: 
  *-display               
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
huxterby@ubuhh:~$ 


```


There are 4 ways to install Nvidia drivers on Ubuntu.

1. System > Administration > Hardware Drivers
Open the app, if your card is listed, check the box and reboot.

2. Use Envyng, an application for installing Nvidia and Ati graphics card drivers. It is in the repositories and can be installed via the commandline:
```
sudo apt-get install envyng-core envyng-gtk
```
Or via synaptic by searching for envyng.

3. By installing the binary driver which you downloaded from the Nvidia website.

4. Via the commandline (terminal) with module-assistant. (A little more advanced)

Try 1 or 2 first. I will help with number 3 and 4 if you need it.

Huxterby

---

### Post by SunnyRabbiera on 2008-08-10
> **xrc6 said:**
> alright, i downloaded a driver from nvidia but it wont run..tried to open it in packag emanager and nothing..why is linux so freakn difficult.

[IMG]http://img527.imageshack.us/img527/2064/screenshothc9.png[/IMG]

you are new, all OS's are difficult at first.
I had a hell of a time learning windows 95 I remember.
There are many ways to go about this sort of thing fortunately for you.

---

### Post by xrc6 on 2008-08-10
> **huxterby said:**
> Hi xrc6.

Linux does take a bit of getting used to huh?

Ok, firstly, if somebody posts a command in a code box like this:
```
sudo lshw -C Display
```

It just means that you have to open the terminal, copy and paste the command and hit enter and some information will appear.

The terminal window is located at: Applications > Accessories > Terminal

This is what comes up when I issue the command: (Nvidia Geforce fx 5200)
```
huxterby@ubuhh:~$ sudo lshw -C Display
[sudo] password for huxterby: 
  *-display               
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
huxterby@ubuhh:~$ 


```


There are 4 ways to install Nvidia drivers on Ubuntu.

1. System > Administration > Hardware Drivers
Open the app, if your card is listed, check the box and reboot.

2. Use Envyng, an application for installing Nvidia and Ati graphics card drivers. It is in the repositories and can be installed via the commandline:
```
sudo apt-get install envyng-core envyng-gtk
```
Or via synaptic by searching for envyng.

3. By installing the binary driver which you downloaded from the Nvidia website.

4. Via the commandline (terminal) with module-assistant. (A little more advanced)

Try 1 or 2 first. I will help with number 3 and 4 if you need it.

Huxterby

i did the envy thing, it seems to be doing something i think...thanks, that was very informative.

however, one thing, how on earth does one go about remembering all those codes? i mean its like going back into the 80's and its just not something i care to go about again, plus i wouldnt do it often enough to remember and have to hunt down posts lol. 
i have the nvidia .run file but it doesnt do squat..they hsould make it so it installs when you click it.

---

### Post by xrc6 on 2008-08-10
crap...envg says it cannot install cause its not compatable or something to that nature

sorry guys, i cant handle this...6 hours wasted and i cant get much of anything to run or do what i want.

i'm gonna have to go back to windows i think.

---

### Post by huxterby on 2008-08-10
I realise your frustration xrc6. Remember that the install and setup of any Linux distro takes a bit of getting used to, just as it does with Windows.

The setup is only a small part of the overall user experience and possibly the hardest. But it's well worth it for a stable, secure virus free life, and all free to boot.

Why not have a breather, take a break for a few days, then come back and try again. It's really not as difficult as it seems, just a learning curve.

What's more you have chosen a distro with possibly the best support resources available for any Linux distro.

Huxterby

---

