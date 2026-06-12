---
title: "AMD Catalyst Control Center"
date: 2013-08-11
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-08-11
Hello All,
First time I've used a Radeon Card instead of NVIDIA.
I have installed the Catalyist Control Center from the Software Center Store, and I do have a AMD Radeon Control Center.
Problems:
 1. I don't have much control inside the Control Center because I need to be able to log in as a Super User Admin. and I don't know how to do that.
2. it will not recognize the second monitor, probably because I can't log in as an admin. to work with it.
3. There is an annoying little square in the lower right which states: " AMD Unsupported Hardware"

System (this is a new build)
1. ASUS Motherboard F2 A85-M PRO (AMD A-85X)
2. AMD Richland A10-6800K 4.1Ghz (still stock)
3. Radeon HD 8670 Integrated Graphics
4. I've gone to the AMD site, and tried to download the beta version, but it is extremely slow in loading on the computer; so slow, it could be said it doesnt work.  This is why I went to the software center and found the Catalyst Control Center in the store.


My idea here is to see if I can get this working with the onboard graphics...if not, I'll go with a discrete NVIDIA card; I've had success with getting NVIDIA to work.
Lastly, please let me know if this is the wrong forum.  If so, how do we get it to the correct forrum?

Any Thoughts are appreciated...
Thanks for the help

---

### Post by mastablasta on 2013-08-12
forum is ok.

is there no (root)version of the center? how did you install the ATI drivers? I could be wrong but i think AMD A APU's should be well supported. what Ubutnu version are you using?

btw 
```
gksu [I]application
[/I]

```will run applicaiton with admin privileges.

---

### Post by Mark Phelps on 2013-08-12
Ubuntu installs Radeon drivers automatically with the first setup.  Unless you want to do serious GPU tweaking, or need to have GPU temperature control, there is no need to mess around with installing your own drivers.  I'm using the default Radeon drivers and have no problem running two monitors, both at full resolution, and have no slowdown in performance doing that.

---

### Post by 3rdalbum on 2013-08-12
That GPU might be too recent for 13.04 until AMD releases a driver for it.

I always recommend Nvidia, but hopefully within a few days or weeks there will be a driver on the AMD site that will work with it.

---

### Post by mastablasta on 2013-08-12
i know A8 APU's work as they should but i am not sure about A10.

---

### Post by opendevlite on 2013-08-12
try this

sudo amdcccle

this will let you run Catalyst Control Center as root

---

### Post by verymadpip on 2013-08-12
> **opendevlite said:**
> try this

sudo amdcccle

this will let you run Catalyst Control Center as root

I think that should be gksu or gksudo for launching a graphical application/interface.
I may well be wrong about that of course.

There's always been a root option in the dash for me.

---

### Post by QIII on 2013-08-12
Hello!

Please don't use sudo with graphical applications.  Use gksudo (or kdesudo for Kubuntu).

Using sudo with graphical applications can cause future permissions problems.

Thanks.

---

### Post by GUZZLR on 2013-08-12
```
s there no (root)version of the center? how did you install the ATI  drivers? I could be wrong but i think AMD A APU's should be well  supported. what Ubutnu version are you using?

```
[ATTACH=CONFIG]245325[/ATTACH]So this is what I am currently trying to install, which I got from AMD website, the install is extremely slow. It is so slow, that I consider it not working.
Also, because the Catalyst Control Center was not working correctly, I went back to the original X.org drivers in Additional Drivers section, after that, I now have any Additional Drivers showing in Software and Update Centers.  So, I no longer have any Catalyst Control Center...It's back to the dull screen as a first install, with out any graphics.

Running 13.04
Thanks for the help

---

### Post by Claus7 on 2013-08-12
Hello,

> **GUZZLR said:**
> ```
s there no (root)version of the center? how did you install the ATI  drivers? I could be wrong but i think AMD A APU's should be well  supported. what Ubutnu version are you using?

```
[ATTACH=CONFIG]245325[/ATTACH]So this is what I am currently trying to install, which I got from AMD website, the install is extremely slow. It is so slow, that I consider it not working.
Also, because the Catalyst Control Center was not working correctly, I went back to the original X.org drivers in Additional Drivers section, after that, I now have any Additional Drivers showing in Software and Update Centers.  So, I no longer have any Catalyst Control Center...It's back to the dull screen as a first install, with out any graphics.

Running 13.04
Thanks for the help

I think that with the attachment you provide you are not installing anything, yet I might be wrong.

Since you want to install the driver directly from amd's website this link:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
section 3.1

will guide you on how to install the driver step by step.

Hope it helps,
Regards!

EDIT: since you are a new user, you will have to use the terminal in order to write the commands provided. In the new versions of ubuntu if I'm not mistaken you will have to go to dash and type the word terminal, and the terminal will show up. Then, you will be ready to issue any command you want. Watch out issuing commands with the sudo string in front, because this might mess things up. So you will have to know what you are doing.

---

### Post by GUZZLR on 2013-08-12
```
lspci -vvnn | grep VGA
```

I ran the code which the article tells of to see if my graphics is supported by fglrx drivers (not x.org), and my grahics is listed HD 8670, and the newer Richland series, which I have as well.  However, what I'm having trouble with, is if it is supported (which it says it is) why do I have the "AMD Unsupported Hardware" little box in the lower right side of the screen?  

Thanks for everybody's help

---

### Post by DuckHook on 2013-08-13
> **GUZZLR said:**
> ...why do I have the "AMD Unsupported Hardware" little box in the lower right side of the screen?That box is generated by AMD's fglrx driver (not Ubuntu) when it detects an AMD video chip that *might* still function, but which particular card implementation is not actually listed in its internal listing of supported hardware. The driver will still try to run (successfully, in your case) but it appends that warning to its output to tell you that your particular combo of driver and card has not been tested and is therefore "unsupported". A newer driver will usually make the box go away, but not always. The problem is that proprietary Linux drivers often lag Windows drivers by months. Therefore, each new card is guaranteed to have functional Windows drivers either included or available to download, whereas the Linux driver will not have caught up yet. This lag is multiplied when you download drivers from the software centre because Ubuntu tends to stock only older versions of drivers that have been time-tested and proven to be more stable.

Unlike Windows drivers, you cannot just download a driver and install it in binary form. In my case, I had to download the newest driver from AMD's website, compile it, and install the whole *dkms* environment so that kernel upgrades would not hose my video driver with each successive update. This is not a procedure for newbies or the faint-of-heart. However, once properly done it works like a charm. I haven't had any video problems at all from the time I installed the driver almost a year ago.

@Claus7 has already given you the link to the installation HowTo. If you go this route, you should heed his warning about the dangers involved. Unfortunately, a balky video driver is one of the worst things to befall a new install because it won't even allow you to see what is wrong or what you are doing. Make sure to first back up all important data. Other than that, there is no getting around the fact that you may just have to take the risk and wing it.

---

