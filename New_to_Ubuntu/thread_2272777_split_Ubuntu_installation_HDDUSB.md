---
title: "split Ubuntu installation HDD/USB"
date: 2015-04-08
forum: New to Ubuntu
---

### Post by stepan3 on 2015-04-08
Hello. I am new in Linux. But I've problem already ). I want to install Ubuntu (Lubuntu 12) on my old net-book WYSE x90. The problem is- i have 512 MB HDD. I want to install a part (may be kernel) to relatively fast HDD and other part of Ubuntu to USB. Is it possible? I will be very thankful for links with description. Thank you in advance.

---

### Post by dino99 on 2015-04-08
yes it is :p
instead of the automatic installation, choose the 'something else' option when proposed by the iso installer: there you will prepare your partitions (/, swap & /home)
Set / (root where the OS will be installed) about 10 gb, swap about 4 gb and the rest for /home (where your settings & data will be)

note: when you says '512 mb hdd' i suppose there is a typo, because its so small that you cant install anything but DOS ;)

---

### Post by michi1983 on 2015-04-08
> **9d9 said:**
> note: when you says '512 mb hdd' i suppose there is a typo, because its so small that you cant install anything but DOS ;)

haha nope ;) it's a thin client
[http://www.pcworld.com/product/1327249/wyse-x90-thin-client-notebook.html](http://www.pcworld.com/product/1327249/wyse-x90-thin-client-notebook.html)

---

### Post by stepan3 on 2015-04-08
512 MB it is not TYPO :). That is why i want to split system and use external USB for the main part.

One more question how i may change graphical settings. I need VESA mode. In other case it did not work.

Thanks

PS Slax Linux works in this configuration. But i want try Ubuntu

---

### Post by sudodus on 2015-04-08
Welcome to the Ubuntu Forums :-)

I think the WYSE X90 is a thin client, not a netbook, and that the 512 MB is the RAM. I don't think it has a HDD at all. Probably Windows is/was installed in an internal flash memory of some kind, embedded Windows. I don't know if that memory is available and re-programmable.

Anyway, since you could run slax in your WYSE X90, you can also run Ubuntu or maybe a flavour of Ubuntu with a lighter desktop environment, Xubuntu or Ubuntu Mate, or with an ultra-light desktop environment, Lubuntu. If the 512 MB is really the RAM, you should select Lubuntu or even a lighter distro like Puppy Linux or Tiny Core. Xubuntu and Ubuntu Mate need 1 GB RAM to work well, standard Ubuntu and Kubuntu want at least 1,5 - 2 GB RAM to work well.

I think you should install the whole operating system into the USB drive. If the 512 MB is not RAM but a fast flash drive, you could install the swap partition there to make swapping faster. As said before, select ***Something else*** at the partitioning window.

Another option is to run your Ubuntu flavour as a live system from the USB drive, and not install it. You can also run it as a persistent live system. See this link and links from it [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by sudodus on 2015-04-08
> **stepan3 said:**
> 512 MB it is not TYPO :). That is why i want to split system and use external USB for the main part.

One more question how i may change graphical settings. I need VESA mode. In other case it did not work.

Thanks

PS Slax Linux works in this configuration. But i want try Ubuntu

Is 512 MB RAM or some other kind of memory?

***Wary Puppy*** can run the graphics in VESA mode. It is good for many old computers.

---

### Post by stepan3 on 2015-04-08
Thank you very much. I have 512 MB flash drive and 512 MB RAM. I want try ubuntu as it is 1) better packages than slax 2) slax 6 works wonderful but i could not install wifi. Moreover i could not understand which WLAN i have.
Now i try ububntu Mini. But i still have problem with Graphic... Is Puppy better than Slax. I need this PC for internet, and simple office. It is hard to use my tab when i need to type big text.

Thank you again

---

### Post by stepan3 on 2015-04-08
Finally i install Ubuntu mini to my HDD. The question is how to install packages on USB. Please help me.

---

### Post by sudodus on 2015-04-08
Different linux distros might work best in different computers (depending of how the hardware drivers match the hardware in each particular computer). So it is worth trying several distros. ***Wary Puppy*** is good for very old computers. ***TahrPup*** (another Puppy flavour) is good for old and also newer computers.

You might get the same problem with wifi also with other linux distros. If you can figure out what is your wifi chip, if will be easier to help you find a solution. Otherwise you can buy a USB wifi 'dongle': be sure to get one that works well with linux. See our [Networking & Wireless forum]("http://ubuntuforums.org/forumdisplay.php?f=336"), where you can also start a new thread to get help with wifi.

---

### Post by sudodus on 2015-04-08
I would start with Lubuntu. Are you running the basic text mode system that comes with Ubuntu mini.iso, or are you running a graphical desktop now?

In the text mode system you can run (when connected via wired network, ethernet)

```
sudo apt-get install lubuntu-desktop
```

and reboot to get into Lubuntu.

---

### Post by stepan3 on 2015-04-08
Thank you very much. Last question for today. Again i could not understand whether it is possible to install packages to other drive

---

### Post by sudodus on 2015-04-08
Maybe possible, but not recommended to install programs in non-standard places. I suggest that you put the swap partition there, to get faster swapping. With only 512 MB RAM, you will probably get a lot of swapping, which is very slow via USB 2.

---

### Post by Bucky Ball on 2015-04-08
Can't see that anyone's mentioned this after I had a quick scan, but you realise Lubuntu 12.04 is no longer supported? Their first LTS release is 14.04 LTS, supported for three years, and I advise you go for that if you are still heading down the Lubuntu path ... 

Just thought I'd throw it in. Good luck. ;)

---

### Post by sudodus on 2015-04-08
Good catch *Bucky* :-)

We certainly recommend running supported versions and Lubuntu 12.04 had no long time support, so it has passed end of life. So[COLOR=#000000] *stepan3*[/COLOR]*, *please tell us what version of Ubuntu mini.iso you did use! Like Bucky Ball, I recommend version 14.04 LTS, maybe the point version 14.04.1 LTS.

---

### Post by stepan3 on 2015-04-08
Thanks. I am new on Linux and did not think about support. So after this discussion i understand that i should install the whole system on USB and use flash drive for swap. Moreover, it seems i should use Puppy or something like this. Ubuntu 14 is too hard for this client (&#1102; 

Thank you everybody!

---

### Post by sudodus on 2015-04-08
Please come back and share your results, whatever they are :-)

If they are bad, we can try some other way to solve your problem.

If/when they are good, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. That helps other people to find your solution.

---

### Post by stepan3 on 2015-04-09
Hello everybody! 
So, finally I increase RAM to 2GB. Thus now i have funny configuration - 2GB RAM and 512MB HDD ).
I install Slax 6 on HDD and adjust to start from RAM. It works pretty fast. Now i think to buy for 20$ mSSD HDD instead of WLAN adapter. BUT i have a very big problem with my video system.

I try to install on HDD/or/USB/or/LiveUSB

Ubuntu,Xubantu,Lubuntu,DAMN,Mint,Slax7,Suse, Puppy,Alt,Mandriva and something else

Each attempt was stopped with graphic start. With command line everything ok, but i could not start graphic. I try different VGA and VESA modes, nothing helps (.

What special has this Slax 6, when even Slax7 has not i dont know. I ask this question on different forums. So waiting for an answer.


P.S.Sorry for my English

---

### Post by sudodus on 2015-04-09
If you tell us what is the graphics chip, maybe we can give relevant advice. Otherwise we can only guess.

Maybe you can find out by [installing and] running lshw or hardinfo in Slax 6.

---

### Post by stepan3 on 2015-04-09
VIA Chrome9 HC IGP  i have the same clien near with windows XP embedded. It is terrible)

---

### Post by sudodus on 2015-04-09
I have read that it is difficult to succeed with old VIA graphics, but I have no own experience of it. You might get some useful tips at the following link

[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

An alternative is to try a light-weight flavour of Ubuntu 12.04 LTS which is supported until April 2017,

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

by *kansasnoob*. Maybe you will stay with Slax 6 and be happy that you have found at least one distro and version that works well in the old WYSE machine.

---

### Post by stepan3 on 2015-04-09
Thank you very much. You are right. I will make last attempt with porteus and than i will be happy that Slax 6 works.
In any case their positive moments in this story. I install Ubuntu 14 on my descktop. And I think to change OS on my old NAS/media server.
Thank you again.

P.S. should i close the topic? (Problem is not solved, i just give up...)

---

### Post by sudodus on 2015-04-09
We only close a thread if it is violating the forum code of conduct, or it has not received any post during one year. We just stop writing :-)

---

### Post by mytien on 2015-04-09
Finally i install Ubuntu mini to my HDD. The question is how to install packages on USB. Please help me!

---

### Post by sudodus on 2015-04-09
@mytien

***Please create an own thread with a good descriptive title!*** Most likely, your problem is different from what is discussed in this thread. You will get better help, and the original poster's thread will not be cluttered with posts about other problems.

---

### Post by Geoffrey_Arndt on 2015-04-10
For Stepan , , , why beat your head against a brick wall???   That system is just not made to do what you're trying to do , , , so, there are better solutions for a nominal amount of money"   [http://symplepc.com/](http://symplepc.com/)

Also, if you really like to "tinker" (experiment etc.), get a Raspberry PI and you have a bunch of new Linux OS's that can be installed on a PC that costs around $35.     But, the simple PC link above is a better solution for a turn-key system (no real effort or work required).

---

