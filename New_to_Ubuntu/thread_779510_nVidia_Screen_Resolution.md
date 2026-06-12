---
title: "nVidia Screen Resolution"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by pianomany2k on 2008-05-02
Anyone had problems with the resolution with 8.04 LTS?

I have an Nvidia 6100 on-board, and the resolution went straight to 800x600, and I can't change it.

---

### Post by dublued on 2008-05-02
which drivers are you using?

i had the same problem with my asus with onboard video.  i installed nvidia-settings and ran it

it gave me options to increase and decrease resolutions that were not available otherwise thru the System>Preferences>Screen Resolution

```
sudo apt-get install nvidia-settings
```

after it installs it can be accessed either thru terminal by typing
```
sudo nvidia-settings
```

or you can go to System>Administration>Nvidia Settings (i forgot what it's called exactly)

---

### Post by mikewhatever on 2008-05-02
Have you installed the restricted nvidia driver yet? You might also want to clarify why you can't change it. What's the problem?

---

### Post by bilbo.san on 2008-05-02
I also had the same problem... the screen res. was from 1024 and below, not any higher.
But perhaps the solution with with Dublued explanation. I will give it a try myself.

---

### Post by GeekGirl1 on 2008-05-02
if that doesn't work, try installing the NVidia proprietary drivers using the EnvyNG script. The restricted drivers wouldn't work for me. GeForce 7900 GTX 512 MB.

Available here: [http://albertomilone.com/index.html](http://albertomilone.com/index.html)

If you have Hardy, it should be available in the package manager or here: [http://packages.ubuntu.com/hardy/envyng-core](http://packages.ubuntu.com/hardy/envyng-core)

(I installed it before it was available as an Ubuntu package)

---

### Post by bilbo.san on 2008-05-02
I downloaded the Linux drivers for Linux on the official website, did not installed it as it worked... but perhaps you could... go to [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Good luck!

---

### Post by pianomany2k on 2008-05-03
> **mikewhatever said:**
> Have you installed the restricted nvidia driver yet? You might also want to clarify why you can't change it. What's the problem?

It was a complete fresh-install. I haven't touched anything yet, other than trying to change the resolution. There are no other choices. 800x600 is all that is in the list. Could my Acer monitor be the issue? Do I need drivers maybe? The screen size "unknown"

And, on another note, I can't do anything with downloading packages until I get my stupid Belkin wireless to connect to my router.

---

### Post by mikewhatever on 2008-05-03
Try System->Admin->Screens and Graphics. Hopefully you'd be able to choose the type of screen and it's resolution there.

---

### Post by skyjacker on 2008-05-03
> **pianomany2k said:**
> It was a complete fresh-install. I haven't touched anything yet, other than trying to change the resolution. There are no other choices. 800x600 is all that is in the list. Could my Acer monitor be the issue? Do I need drivers maybe? The screen size "unknown"
Try this: 
1) Restart, and when the Grub Menu appears, boot into Recovery mode.
2) type this sudo dkpg-reconfigure xserver-xorg.
3) when you don't know the answer to a question, press Enter. eventually you will get to a place that lists screen resolutions. If one or more that you want has an X beside it you are good to go.
Continue until the end of the prog., save, and type "reboot" When you re-enter Ubuntu you should be able to choose the resolution you want from the drop down list...

---

