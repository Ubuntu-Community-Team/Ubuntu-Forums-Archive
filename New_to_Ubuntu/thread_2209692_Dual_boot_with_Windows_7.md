---
title: "Dual boot with Windows 7"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by ngorkes on 2014-03-06
I have successfully installed xubuntu on my computer but I have a few questions/ problems. I am dual booting with Windows 7 and I want to make Windows my default OS when my computer boots up; can you?  Another thing I ran into is that the xubuntu installer deleted all of my files on my second hard drive and installed itself there. Can I still make a folder on the hard drive and put all my files in it without messing xubuntu up?  Do I need hardware drivers to better run xubuntu?

---

### Post by 23dornot23d on 2014-03-06
> 
 I am dual booting with Windows 7 and I want to make Windows my default OS when my computer boots up; can you?

Here is a link showing the program that I was thinking of - 
[http://ubuntuhandbook.org/index.php/2013/08/change-boot-order-in-ubuntu-13-10-13-04/](http://ubuntuhandbook.org/index.php/2013/08/change-boot-order-in-ubuntu-13-10-13-04/)
but it is downloaded from a ppa ...... there used to be a easier option than this - 
maybe someone else can point you to it .........

Yes as far as I know this is possible ........... there used to be a program for easily configuring the boot loader.

> 
Another thing I ran into is that the xubuntu installer deleted all of my  files on my second hard drive and installed itself there.


That is usually not the case - unless the user asks to use a full drive instead of installing alongside another operating system
( but it can be checked to see if a full D: drive was used or if its set up alongside the data - gparted should show us the layout )

> 
Can I still make a folder on the hard drive and put all my files in it without messing xubuntu up?

Yep that is easy enough to do ......
( do you want this folder to be access able to both linux and windows ? - using gparted is one way to do it ...... )

> 
 Do I need hardware drivers to better run xubuntu?                 

Not usually ........ but xubuntu is a basic look and minimal ...... but it can be improved.


Some questions first about the system you use ..........
Which OS have you chosen 12.04 12.10 13.04 13.10 or something else
[https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

What sort of computer are you using Laptop or Desktop 

Does the computer you use have a Graphics Card in it like a Nvidia or Amd 
[http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card](http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card)

and are you comfortable using the terminal if we should go along the route of finding out
how the hard drive is set up ? 

Hope some of that helps - others might have some easier solutions ........

---

### Post by ngorkes on 2014-03-07
I have a desktop with a gtx 760.

---

### Post by 23dornot23d on 2014-03-07
I looked at this thread and it seems to have the best settings for your graphics card setup .....
 
[http://ubuntuforums.org/showthread.php?t=2177159&page=3](http://ubuntuforums.org/showthread.php?t=2177159&page=3)

You need to check to see how you have it configured at the moment .......

Can you post back what you find by doing the following commands in a terminal please.

Open up any teminal 

Then type in
```


**glxinfo | grep OpenGL**


```

Then post the returned text back please.

Also just to confirm the settings and exact specifications of the graphics card also post back what you
get from the following.

```


**lspci | grep VGA**


```

We will try to ensure the graphics are set up as best they can be ....... is nvidia-settings installed ?

You can check this by either looking in your menus under Preferences in the menu ........ if it is there
click on it to see what is setup for it - if anything and post back the driver information ........ 
 or post a screenshot of the screen showing the settings.

Once we know that the graphics card is working as well as it can be then you should be able to set
Xubuntu up anyway you would like to use it ..........

What sort of things are you interested in using in it - graphics / music / video / games ....... or do
you want to keep it light weight for working in.

Whatever the choice is ...... the graphics card still needs to be set correctly to give the better user
experience for speed and for responsiveness ...........

---

### Post by Mark Phelps on 2014-03-07
For configuring the GRUB loader, install GRUB-Customizer: [http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

---

### Post by ngorkes on 2014-03-07
nick@nick-desktop:~$ glxinfo | grep OpenGL
The program 'glxinfo' is currently not installed. You can install it by typing:
sudo apt-get install mesa-utils
nick@nick-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 760] (rev a1)

---

### Post by 23dornot23d on 2014-03-07
Ok lets do that command - as it will then allow us to see how the graphics are set up ......

Type this in the terminal

```


**sudo apt-get install mesa-utils**

then try this again

[B]glxinfo | grep OpenGL

[/B]thento find out which version of Ubuntu you are running[B]

lsb_release -a
[/B]
```

also because we know for sure you have the nvidia graphics card and we may need to
check the settings out ..........

```

**sudo apt-get install nvidia-settings**

then to run it ....

**nvidia-settings**


```

By doing this we should be able to determine if you have anything at all set up
for nvidia ...... basically just doing recon at the moment and finding out what
we have ...... before changing anything .

if nvidia-settings works - let us know what driver is installed if any please - post that information
back too .......... it should be on the xserver information screen.

---

