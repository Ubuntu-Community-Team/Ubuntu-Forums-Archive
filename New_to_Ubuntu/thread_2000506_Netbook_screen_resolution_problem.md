---
title: "Netbook screen resolution problem"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by janiemiec on 2012-06-09
Hello, I wanted to install ubuntu 12.04 on my Asus EeePC 1015CX. I have created a bootable USB from which I have chosen the 'Try' option to see how it would feel on my netbook. Unfortunately as I have found out the screen resolution seems to be blocked only at 800x600 where as my netbook normally operates on 1024x600. Can instruct me on how to change the resolution? (Please note that there is no other option in the settings).

Thank you in advance.

---

### Post by wilee-nilee on 2012-06-09
> **janiemiec said:**
> Hello, I wanted to install ubuntu 12.04 on my Asus EeePC 1015CX. I have created a bootable USB from which I have chosen the 'Try' option to see how it would feel on my netbook. Unfortunately as I have found out the screen resolution seems to be blocked only at 800x600 where as my netbook normally operates on 1024x600. Can instruct me on how to change the resolution? (Please note that there is no other option in the settings).

Thank you in advance.

The live cd may not be finding the graphic driver, a install most likely will. The eeepc in general is a commonly use set up.

---

### Post by janiemiec on 2012-06-09
So do you think that if I install the system it would work correctly?

---

### Post by janiemiec on 2012-06-09
Do you think that if I installed it then perhaps it would be able to get all the drivers from the internet?

---

### Post by wilee-nilee on 2012-06-09
> **janiemiec said:**
> So do you think that if I install the system it would work correctly?

It is quite possible, click the download updates button in the install.

The eeepc has been around a long time and is a commonly used so the graphic cards are not unknown, I would guess that  the resolution you want is quite possible.

It may take a update and checking the additional drivers app after the install to get you all linked up is all.

If you are worried google the model and ubuntu, and  if there is no resolution above 800x600 it will be all over the first hits.

---

### Post by snowpine on 2012-06-09
You can find a list of Ubuntu-compatible netbooks here:

[http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)

---

### Post by janiemiec on 2012-06-09
Hi, I just installed it and there is still no option, there also appear to be no additional drivers that need to be installed. I have read something about editing a file called xrandr or something like so.

---

### Post by wilee-nilee on 2012-06-09
> **janiemiec said:**
> Hi, I just installed it and there is still no option, there also appear to be no additional drivers that need to be installed. I have read something about editing a file called xrandr or something like so.

Try in the terminal running this command to see if the resolution you mentioned is available already.

```
xrandr -s 1024x600
```

Graphic stuff in general is not an area I really know really well.

---

### Post by janiemiec on 2012-06-09
It says that this size is not found in  available modes. :confused:

---

### Post by wilee-nilee on 2012-06-09
> **janiemiec said:**
> It says that this size is not found in  available modes. :confused:

Run this command and post the card.
  	 	 	 	 	 	   ```
lspci | grep VGA 
```

---

### Post by janiemiec on 2012-06-09
Here:
000:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)

---

### Post by wilee-nilee on 2012-06-09
> **janiemiec said:**
> Here:
000:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)

Take a look here. 
[https://answers.launchpad.net/ubuntu/+faq/1901](https://answers.launchpad.net/ubuntu/+faq/1901)

---

### Post by janiemiec on 2012-06-09
How would I find the "HorizSync and VertRefresh" values?

---

### Post by wilee-nilee on 2012-06-09
> **janiemiec said:**
> How would I find the "HorizSync and VertRefresh" values?

Not sure this is beyond my area all I can do is use google myself.

I found that link though using your card as a search, hopefully others will chime in, sometimes it takes a little while to get a response, weekends seem to be a bit slower.

---

### Post by janiemiec on 2012-06-09
Is there a command that would be able to show me these variables?

---

### Post by janiemiec on 2012-06-10
Hi again, I was I am still unable to find the resolution for my monitor I have looked some methods on the internet but they all fail. I was wondering if it might have something to do with a driver? Might there be a driver that I need to install or perhaps needs to be activated?

---

### Post by arpankrishna on 2012-07-09
Hello all..

I believe the problem is still unsolved and if I may add that the graphics card in itself is not properly installed and after going through the drivers for Ubuntu (Linux in general) from the Asus website I still could not find the linux driver for the graphics card.

The video in VLC and Totem are also not running properly, slower than what it is running on windows and also fullscreen mode in VLC is a mess.

Has anybody found a solution.

Any help would really be appreciated as I do not want to use windows.

Thanks.

---

### Post by diebels on 2012-07-09
> **arpankrishna said:**
> Hello all..

I believe the problem is still unsolved and if I may add that the graphics card in itself is not properly installed and after going through the drivers for Ubuntu (Linux in general) from the Asus website I still could not find the linux driver for the graphics card.

The video in VLC and Totem are also not running properly, slower than what it is running on windows and also fullscreen mode in VLC is a mess.

Has anybody found a solution.

Any help would really be appreciated as I do not want to use windows.

Thanks.

Hi arpankrishna,
I believe the driver you are looking for are here:
[https://launchpad.net/~sarvatt/+archive/cedarview]("https://launchpad.net/~sarvatt/+archive/cedarview")

See [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs") for howto adding a ppa.

This is a driver released by Intel June 7th this year:
[http://downloadmirror.intel.com/21519/eng/cdv-gfx-drivers-1.0.1_releasenotes.pdf]("http://downloadmirror.intel.com/21519/eng/cdv-gfx-drivers-1.0.1_releasenotes.pdf")

The 2d performance currently sucks, and it doesn't have proper OpenGL support, but you get proper resolution and the video playback performance is pretty good in supported players like vlc.  720p is flawless and 1080p is mostly OK with occasional tearing artifacts.

To get a slight improvement in 2d performance, you can try editing /usr/share/X11/xorg.conf.d/61-cdv-pvr.conf
and add the following to the Device section:
Option  "Soft2CompositeLimit"   "0"

To get accelerated flash, you need to download an old version of Chromium at:
[https://registrationcenter.cps.intel.com/regcenter/register.aspx](https://registrationcenter.cps.intel.com/regcenter/register.aspx)

Only a rpm package is available, so you'll have to convert it to deb with alien.

This graphics card is made by PowerVR (sgx545) and not up to the same standards as the regular intel GMA and HD graphics chips.  Not having open-source drivers makes it awkward to get up and running in Linux and the 2d and OpenGL performance and compatibility actually sucks in Windows7 as well.  Its main selling point is good video decoding performance at very low power draw.  You won't get to bothered with the 2d performance when running 1024x600 resolution, but stick it in a 1920x1080 TV and you'll get pretty annoyed unless you're a very calm and patient person.

---

