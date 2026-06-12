---
title: "Installing Nvidia Drivers"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Shadius on 2008-05-04
Question: How do I install Nvidia Display Drivers? I'm new to Linux so I need step by step instructions. I believe Linux has detected my graphics card, but I'd like to have some more control over the display with the Nvidia Control Panel (that was in Windows). when I download the software from Nvidia.com, it has a ".run" extension, how do I go about installing the software? Any help is appreciated.

---

### Post by alienexplorers on 2008-05-04
The easiest way is to use Envyng which can be found in the repo's.  Run it and let it do the work for you.

---

### Post by robalcorn on 2008-05-04
Go to System/administration/hardware drivers and enable nvidia drivers and reboot. After you do that again go to system administration/nvidia server settings to control what you need to do.

---

### Post by Shadius on 2008-05-05
There's no Nvidia Server Settings.

---

### Post by ad_267 on 2008-05-05
```
sudo apt-get install nvidia-settings
```
Then to run it
```
gksudo nvidia-settings
```

---

### Post by iswa on 2008-05-05
> **alienexplorers said:**
> The easiest way is to use Envyng which can be found in the repo's.  Run it and let it do the work for you.
  

I agree with alienexplorers on this one - in my experience envyng is definitely the easiest way to install and keep up-to-date with the latest Nvidia / ATI drivers. 


From the package description:  

*"EnvyNG is an application written in Python which will download the latest ATI or NVIDIA driver or the Legacy driver (for older cards) (according to the model of your card) from ATI or Nvidia's website and set it up for you handling dependencies (compilers, OpenGL,*
* etc.) which are required in order to build and use the driver."*

Either use your package manager as described, or: 
```
sudo apt-get install envyng-gtk
```

---

### Post by UnknownFear on 2008-05-05
> **iswa said:**
> I agree with alienexplorers on this one - in my experience envyng is definitely the easiest way to install and keep up-to-date with the latest Nvidia / ATI drivers.

What if you are using 7.10 'Gust Gibbon'? How can you install the latest Nvidia drivers?

---

### Post by aktiwers on 2008-05-05
> **UnknownFear said:**
> What if you are using 7.10 'Gust Gibbon'? How can you install the latest Nvidia drivers?

I have made a small guide here how to do it manually:
[http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735](http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735)

Just remember to change the driver version, as it's newer now :)

---

### Post by Sinkingships7 on 2008-05-05
After you install the restricted drivers (System -> Administration -> Hardware Drivers), just type this into the terminal:
```
sudo apt-get install nvidia-settings
```
followed by:
```
gksudo nvidia-settings
```

You should use graphical sudo for administrative tasks that use a graphical front-end.

---

### Post by abhiroopb on 2008-05-05
Why would people not simply use the restricted drivers manager? It installed fine for me and I've even set up dual monitors (albeit with some minor problems, such as games having to be played in a window otherwise it is split between the two screens). I've heard envy/automatix can cause problems. Not sure though as I've never really used.

---

### Post by UnknownFear on 2008-05-05
> **aktiwers said:**
> I have made a small guide here how to do it manually:
[http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735](http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735)

Just remember to change the driver version, as it's newer now :)

I tried following it, but it gave me an error saying file not found? I typed everything in:

```
cd Desktop
```
```
sudo /etc/init.d/gdm stop
```
```
sudo chmod +x NVIDIA-Linux-x86-169.07.pkg1.run
```
```
sudo ./NVIDIA-Linux-x86-169.07.pkg1.run
```
```
sudo /etc/init.d/gdm start
```

But it didn't work.

---

### Post by Calash on 2008-05-05
Restricted Driver Manager did not work for my card, 9600 GT.  EnvyNG also did not work, so I had to download the beta drivers (172.xx) to get my card running.

EnvyNG and RDM are not going to work 100% of the time, that is why people ask for alternatives.  They should be the first thing you try though, both work great for most situations.

---

### Post by Sinkingships7 on 2008-05-05
> **abhiroopb said:**
> Why would people not simply use the restricted drivers manager? It installed fine for me and I've even set up dual monitors (albeit with some minor problems, such as games having to be played in a window otherwise it is split between the two screens). I've heard envy/automatix can cause problems. Not sure though as I've never really used.

Because not all GPU's have restricted drivers waiting for them, or they don't work. Other than that, yeah, I see your point. Why would someone want to go through all the trouble of installing drivers from the site when they're five clicks away?

---

### Post by UnknownFear on 2008-05-05
Oh wait. When I boot up into Ubuntu, I see the nVIDIA loglo. Does this mean that it works, and can I risk upgrading to 8.04 and not have the problem of my monitor shutting off and not being able to boot into Ubuntu?

---

### Post by aktiwers on 2008-05-05
> **UnknownFear said:**
> Oh wait. When I boot up into Ubuntu, I see the nVIDIA loglo. Does this mean that it works, and can I risk upgrading to 8.04 and not have the problem of my monitor shutting off and not being able to boot into Ubuntu?

That should be a sign that they are installed. But you have a pretty new card, and when I looked at there site, it did not find any Linux drivers for your card. I guess it works now anyways?

How many fps does:
```
glxgears
```give you? It's no benchmark test, but the result would show if they are installed correct or not.

Edit: By the way, driver installs require reboot to take effect.

---

### Post by jtclicker on 2008-05-05
because some of us, with hardy, can't get the restricted driver to work no matter what we do! [http://ubuntuforums.org/showthread.php?p=4877339#post4877339]("http://ubuntuforums.org/showthread.php?p=4877339#post4877339")

> **abhiroopb said:**
> Why would people not simply use the restricted drivers manager? It installed fine for me and I've even set up dual monitors (albeit with some minor problems, such as games having to be played in a window otherwise it is split between the two screens). I've heard envy/automatix can cause problems. Not sure though as I've never really used.

---

### Post by UnknownFear on 2008-05-05
> **aktiwers said:**
> 
How many fps does:
```
glxgears
```give you? It's no benchmark test, but the result would show if they are installed correct or not.

```
dan@dan-desktop:~$ glxgears
4483 frames in 5.0 seconds = 896.540 FPS
3855 frames in 5.0 seconds = 770.912 FPS
1905 frames in 5.0 seconds = 380.972 FPS
3871 frames in 5.0 seconds = 774.172 FPS
4091 frames in 5.0 seconds = 818.192 FPS
3896 frames in 5.0 seconds = 779.166 FPS
4508 frames in 5.0 seconds = 901.449 FPS
4501 frames in 5.0 seconds = 900.125 FPS

```

Is that good?

---

### Post by aktiwers on 2008-05-05
> **UnknownFear said:**
> ```
dan@dan-desktop:~$ glxgears
4483 frames in 5.0 seconds = 896.540 FPS
3855 frames in 5.0 seconds = 770.912 FPS
1905 frames in 5.0 seconds = 380.972 FPS
3871 frames in 5.0 seconds = 774.172 FPS
4091 frames in 5.0 seconds = 818.192 FPS
3896 frames in 5.0 seconds = 779.166 FPS
4508 frames in 5.0 seconds = 901.449 FPS
4501 frames in 5.0 seconds = 900.125 FPS

```Is that good?

It should mean that the drivers are installed but that is a pretty low score for your card.
I have the same score on my Nvidia 6200LE and you should get a lot higher!

Maybe the drivers that support your card is not out yet? You do have a pretty new card and I know the 98000GX2 still don't even have a Windows driver. Lets hope someone with more knowledge than me can tell us this :)

---

### Post by forumache on 2008-05-05
> **UnknownFear said:**
> Oh wait. When I boot up into Ubuntu, I see the nVIDIA loglo. Does this mean that it works, and can I risk upgrading to 8.04 and not have the problem of my monitor shutting off and not being able to boot into Ubuntu?

If you see it just before the logon screen appears, yes, we might presume that it is displayed by the nvidia driver.

Furthermore, open /etc/X11/xorg.conf and check where is says Driver, for your Video Card. If it is nv, than it is the opensource one, not working with compiz. If you see "nvidia", then it is the proprietary one, restricted driver, works great with compiz.

Good luck,
Dan.

---

### Post by abhiroopb on 2008-05-05
Oh yes if its Hardy then restricted drivers is a MAJOR problem. Frankly I don't understand why. I mean it works for me in Gutsy so why should an upgrade cause a problem! If it ain't broke...

---

### Post by Shadius on 2008-05-05
I looked for EnvyNG using Synaptic, but I got 3 different results. 

envyng-core
envyng-gtk
envyng-qt

Which one do I download, the description all say the same thing, "install the ATI or NVIDIA driver". Which one do I need to download?

---

### Post by Shadius on 2008-05-05
I'm getting a lock when I try to install it. Please help!! I installed it using Synaptic and downloaded "envyng-gtk". I also tried it through the Terminal and got the same lock response.

---

### Post by aktiwers on 2008-05-05
Remember you can only have one package manager open at the same time.
Please post the error message here

---

### Post by Shadius on 2008-05-05
> **aktiwers said:**
> Remember you can only have one package manager open at the same time.
Please post the error message here
This is weird. I just tried it again in terminal and it worked! Maybe I mistyped something? Anyway, it installed and I can run it. Thanks. I just need a lil' help understanding what I'm looking at here when I run it, but I'll leave that for tomorrow since it's late and I'm tired. Thank you guys for all your helpful posts.

---

### Post by aktiwers on 2008-05-06
Just pick "install nvidia drivers" and go with it :)

---

### Post by Shadius on 2008-05-06
Okay, I installed it! So can you explain to me what I can do in the NVIDIA X Server Settings?

---

### Post by aktiwers on 2008-05-06
Could you be more specific? What do you wanna do? :)

---

### Post by oldrocker99 on 2008-05-06
So, after reading this thread, I installed envyng and ran it, rebooted, and I'm again restricted to 640x480 or 800x600, nothing higher. 

NVIDIA Server Settings returns this when I run it:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

On my 10th day of Linux. How do I restart the X server?:confused:

---

### Post by aktiwers on 2008-05-06
That means you need to type this command if you did not already do it:
```
sudo nvidia-xconfig
```

then restart the x-server presseng CTRL+ALT+BACKSPACE

OR

typing:

```
sudo /etc/init.d/gdm restart
```

---

### Post by Shadius on 2008-05-06
> **aktiwers said:**
> Could you be more specific? What do you wanna do? :)
Two things please: 

(1) What can the NVidia X Server Settings do? 

(2) I want to adjust my graphics like how you adjust it in Windows, like fine-tuning the colors, contrast, brightness...etc. You know, like how Windows has NVidia Control Panel when you install the NVidia driver.

---

### Post by aktiwers on 2008-05-07
1) Did you install it? Try it out it can do a lot of stuff.
```
sudo apt-get install nvidia-settings
```

You can find it in System=>Administrator=> NVidia X Server Settings

For an example pick one the first one in the small menu, then you get to a bigger menu where you can do what you want in your question number 2. Look under "X Server Color correction".

---

