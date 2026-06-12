---
title: "64 bit nvidia driver display issue"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by bnosam on 2012-11-25
I installed Ubuntu 12.10 today on my Asus G73SW-A1. The graphics card in it is an Nvidia GeForce Gtx 460M, so I downloaded the linux drivers for it and installed them.

Before I installed them, the default video driver let me view the screen in 1920 x 1080 resolution, now after this I'm stuck with 1024 x 768 or 800 x 600. I also can't see side bar, or the top bar now.

When the package was installing it said something like disabling nouveau in order to continue and gave me errors about KDMS or something. 

I'm not sure what to do to fix this, it really has me annoyed because I can't believe it would break this easily on me considering I've been a windows user for years and I've never had anything like this happen that I couldn't fix easily.


Thanks

---

### Post by mansonfan78 on 2012-11-26
Did you check the "Additional Drivers" in the "settings" menu?  Or did you just install manually?

---

### Post by bnosam on 2012-11-26
I installed it manually.

---

### Post by audiomick on 2012-11-26
I would suggest de-installing what you put on manually, and using the "additional drivers" application to get the recommended nVidia proprietary driver. Is there any reason why you would not want to go this way?

---

### Post by bnosam on 2012-11-26
> **audiomick said:**
> I would suggest de-installing what you put on manually, and using the "additional drivers" application to get the recommended nVidia proprietary driver. Is there any reason why you would not want to go this way?

I uninstalled the package but it said it all couldn't be removed. So I removed all nvidia packages and it didn't fix the problem.

I didn't go that way because I didn't know I could because when I googled installing nvidia drivers on ubuntu it told me to download them from nvidia and run it manually to install the latest. If I had have known it would break my installation or there was a better way I wouldn't have done it.

---

### Post by audiomick on 2012-11-26
> **bnosam said:**
>  So I removed all nvidia packages and it didn't fix the problem.

It wont be fixed until there is a driver running properly. The next thing would be to try the Additional Drivers application and see if that will install a proprietary driver for you that works properly.

Have you found that application? On the Unity desktop, you can type "additional" into the search box in the dash. You need to have an active internet connection, because the application goes off and gets the drivers on the web.

---

### Post by linux4me on 2012-11-26
I had a similar issue with my Nvidia GT 440.

I prefer to fix this kind of thing from terminal. You can open one from the within Ubuntu by hitting Ctrl + Alt + T.

The first thing to do is get back to the nouveau driver. To do that, you'll need to clean out all the nvidia files you installed by running the following commands:
```
sudo nvidia-installer --uninstall
```
Don't worry if the command above reports that the file wasn't found. You're just making sure all the nvidia stuff is gone.
```
sudo apt-get remove nvidia-*
```
Now, restart your machine and the nouveau driver should be loaded automagically.

Once you're back at your desktop, you can either use the GUI mentioned in the previous post to install one of the proprietary nvidia drivers, or do so using Terminal.

With my GT 440, neither the nvidia-current nor the nvidia-current-updates drivers worked for me. The former displayed grub in 640 x 480 and caused problems with evolution-calendar-factory. With current-updates, the launcher wouldn't come out of auto-hide, but the nvidia-experimental-304 driver seems to work just fine. To install it from the command line, use the following commands. The first makes sure you're up-to-date, the second installs linux headers which are a dependency of the nvidia proprietary drivers, and the third installs the experimental 304 driver:
```
sudo apt-get update
```
```
sudo apt-get install linux-headers-generic
```
```
sudo apt-get install nvidia-experimental-304
```
After that, restart to use the new driver.

---

### Post by grahammechanical on 2012-11-26
For the record,

in Ubuntu 12.10 we go to System Settings>Software Sources>Additional Drivers tab. And there we get 4 options for those with Nvidia.

Nvidia-current (proprietary, tested)
Nouveau (open source)
Nvidia-current-updates (proprietary)
Nvidia-experimental-304 (proprietary)
Nvidia-experimental-310 (proprietary)

This is different from 12.04 where there is a separate Additional Drivers utility.

Six months ago I would have recommended the Nvidia drviers over the Nouveau drivers. But not any more. Too many broken desktops due the buggy Nvidia drivers.

Regards.

---

### Post by bnosam on 2012-11-26
I tried ```
sudo nvidia-installer --uninstall
sudo apt-get remove nvidia-*
```

and it said it uninstalled, I restarted and the drivers are still displayed in the additional drivers tab. I have the default nouveau driver selected. But it still hasn't changed. I'm still limited to my display modes, and I can't get back to 1920 x 1080 like it was when I installed it.

There is no launch bar on the left and no bar on the top.
Image below:
[http://oi48.tinypic.com/210br4n.jpg](http://oi48.tinypic.com/210br4n.jpg)


So, is it just 12.10 that is this whacky and 12.04 is good, or is it just linux is just this easily breakable?


I'd like to have nvidia drivers working too because the main reason for using linux for me is to use it for application development and may do some 3D related apps or something.

---

### Post by linux4me on 2012-11-26
> **grahammechanical said:**
> 
Six months ago I would have recommended the Nvidia drviers over the Nouveau drivers. But not any more. Too many broken desktops due the buggy Nvidia drivers.

I tried the nouveau driver for a while with my GT 440 but had too many problems with corrupted video. That's why I suggested he try the proprietary drivers. 

The nvidia drivers will still display in the additional drivers even though you no longer have them installed. You can verify that you're using nouveau by running the following in terminal if you don't believe the additional drivers page:
```
lspci -nnk | grep -iA2 vga
```

I am not sure why you still have issues with the desktop. Someone above my pay grade will have to answer that for you. However, I don't think you'll do any harm by preceding with the installation of linux-headers-generic and one of the nvidia proprietary drivers as described above. I would try the experimental-304 driver if I were you since that's what worked with my GT 440, but there's no reason you can't try each of them and see which works best for you.

---

### Post by bnosam on 2012-11-26
> **linux4me said:**
> I tried the nouveau driver for a while with my GT 440 but had too many problems with corrupted video. That's why I suggested he try the proprietary drivers. 

The nvidia drivers will still display in the additional drivers even though you no longer have them installed. You can verify that you're using nouveau by running the following in terminal if you don't believe the additional drivers page:
```
lspci -nnk | grep -iA2 vga
```

I am not sure why you still have issues with the desktop. Someone above my pay grade will have to answer that for you. However, I don't think you'll do any harm by preceding with the installation of linux-headers-generic and one of the nvidia proprietary drivers as described above. I would try the experimental-304 driver if I were you since that's what worked with my GT 440, but there's no reason you can't try each of them and see which works best for you.

Thanks for your help guys but I just deleted my linux partition. I'm done with Linux, it just doesn't work. I've tried like 4-5 different versions of it and they all have the same issues. I tried Linux a couple years ago and I just tried it again lately hoping it matured, but unfortunately it's still the same.

Oh well.

---

### Post by BicyclerBoy on 2012-11-26
The root of the problem is optimus..

Your h/w has hybrid graphics which is not supported directly by nVidia yet..

You would have had to use Bumblebee to dynamically load/switch between nVidia & intel iGFX.
You do not manually load the nVidia driver with Bumblebee..

---

### Post by Magalaan on 2013-02-21
> **bnosam said:**
> Thanks for your help guys but I just deleted my linux partition. I'm done with Linux, it just doesn't work. I've tried like 4-5 different versions of it and they all have the same issues. I tried Linux a couple years ago and I just tried it again lately hoping it matured, but unfortunately it's still the same.

Oh well.
It can be a challenge at times. Most modern PC work quite well with Linux, but especially with laptops it is a good idea to check whether there are issues before you buy, if you have the intention to use Linux. The simple fact is that most manufacturers make PC's Windows compliant and not for Linux. In you case you have Optimus for which Nvidia refuses to maken Linux-drivers and also refuses to give information to maken a open source driver. 

As for your problem 

> **bnosam said:**
> I installed Ubuntu 12.10 today on my Asus G73SW-A1. The graphics card in it is an Nvidia GeForce Gtx 460M, so I downloaded the linux drivers for it and installed them.

Before I installed them, the default video driver let me view the screen in 1920 x 1080 resolution, now after this I'm stuck with 1024 x 768 or 800 x 600. I also can't see side bar, or the top bar now.

I had exactly the same problem as you describe with an Nvidia GeForce Gtx 460. I installed all Nvidea's drivers and the result was the same. I found that strange since I had no problems in previous versions of Ubuntu. 

What did the trick for me was, what [COLOR=#000000]linux4me[/COLOR] advised [here]("http://ubuntuforums.org/showpost.php?p=12374007&postcount=7"). Especially this line:
> sudo apt-get install linux-headers-generic 

That did the trick, after that all the drivers installed fine.  Windows look fine, panel and launcher are back, and I have my 1920x1080 back. 

I did some research on what are header files and why should we install them. Normally header files are only needed at compile time, and the executable (binary) does not need them after that. But Nvidia happens to be an exception to this rule: I quote

> NVidia is different because what they do is provide a binary chunk of proprietary code (pre-compiled but not runnable without some additional system-specific code) wrapped in some open source code that you must compile for your machine in order to use the driver. This way, NVidia can use the same core code for their Windows and Linux drivers, and just wrap the core in platform-specific code that hooks the driver into the OS. That's why installing the NVidia proprietary driver needs the kernel headers to be installed in order to compile (but the driver core itself is still proprietary and is actually pre-compiled platform-
 independent data). [source]("https://answers.launchpad.net/ubuntu/+question/54157") 
  I am quite sure you can solve the problem the same way as I had exactly the same symtoms. But of course Optimus will not work, so batterylife won't be as good as in Windows.  
  Many thanks to [COLOR=#000000]linux4me[/COLOR]

---

