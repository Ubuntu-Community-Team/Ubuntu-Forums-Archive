---
title: "Problems on 11.10"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by pavanmatham on 2011-11-21
Hi,

I brought a new laptop - DELL make - inspiron 4110 - 500 GB hard disk & 4 GB RAM.
It comes with windows. Installed Ubuntu 11.10 (32-bit) on un-allocated Hard disk space of 300GB (Dual boot - Manual/using '_something else_' option). 
Ever since I installed Ubuntu 11.10, I have been facing following problems 

1. It is [COLOR=Red]**consuming battery**[/COLOR] at faster rate.

2.** [COLOR=Red]Mouse struck[/COLOR]** frequently--> I have to restart the system-->  
   Since this evening it strucks for EVERY 2 MINUTES#-o ** But**, **external mouse works perfectly**. 

3.   **[COLOR=Red]Hibernate and Logout are not working[/COLOR]**--> When I use these options [COLOR=Red]screen freezes and nothing happens[/COLOR]. I have to use power on/ off switch to restart the system to work.**[COLOR=Red] And[/COLOR]**, there is [COLOR=Red]**no restart option**[/COLOR] found in this version. 

I never faced such problems with earlier versions of Ubuntu in the last 2 years. 

Help requested to fix the above. 
Thanks in advance

Pavan

---

### Post by grahammechanical on 2011-11-21
In 11.10 when we click Shut Down we are asked to confirm. This is when we get the option to continue with the Shut Down or to Restart. Are you saying that this option is not available to you?

As regards hibernation do you have enough swap space so that the operating system can be moved out of RAM and on to the hard disk? 

Regards.

---

### Post by Lalaith on 2011-11-29
Hi, 

I am reading this thread since I also have some hibernate/suspend problems but I don't know which is the cause.

Could you explain how to check if there is enough swap space to do a proper hibernation?

Thank you :)

---

### Post by kr651129 on 2011-11-29
Did you install via Wubi?

And I can second the battery usage, but I'm just assuming this is because of Unity.  Have you tried going back to Gnome?

---

### Post by lolpenguin on 2011-11-30
> **kr651129 said:**
> Did you install via Wubi?

And I can second the battery usage, but I'm just assuming this is because of Unity.  Have you tried going back to Gnome?

Also, there have been reports that the Linux kernel 3 uses excessive amounts of battery.

---

### Post by BC59 on 2011-11-30
For the battery consumption problem, many people noticed improvement installing Jupiter.

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

And here is described a tweak you can make for the kernel consumption:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

---

### Post by BlinkinCat on 2011-11-30
> **Lalaith said:**
> Hi, 

I am reading this thread since I also have some hibernate/suspend problems but I don't know which is the cause.

Could you explain how to check if there is enough swap space to do a proper hibernation?

Thank you :)

I would suggest that you should start your own thread - :)

---

### Post by clegends on 2011-11-30
> **Lalaith said:**
> Hi, 

I am reading this thread since I also have some hibernate/suspend problems but I don't know which is the cause.

Could you explain how to check if there is enough swap space to do a proper hibernation?

Thank you :)

For hibernation, you need twice as much swap space as you have ram. So for instance, if your ram is 2Gb, then you need a 4Gb swap partition. Also, hibernate WILL NOT work if you have encrypted your /home files. (or partition, if you were smart...) Suspend will still work, but hibernate only works if you haven't encrypted anything. Cheers.

---

### Post by Scott Baker on 2011-11-30
I hate to throw this at you, but if you spend more time in these forums, you'll notice two things. There is an ENTIRE section devoted specifically to Dell machines. Next, 11.10 has been a problem for a lot of us. You'll want to check out the Dell section to see if your problems have been addressed previously. When the Dells are configured properly, they work just fine with Ubuntu, but you have to be ready to do some head scratching to get your box set up right. Hang in there, don't give up on your Dell, and don't bail on us "Ubuntoids" yet, it will all be ok.

Dr Sheldon Cooper for U.S. president, 2012  =D>

---

### Post by bluexrider on 2011-11-30
> **BC59 said:**
> For the battery consumption problem, many people noticed improvement installing Jupiter.

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

For the laymen.....what is jupiter and how can it fix the issue

---

### Post by sammiev on 2011-11-30
> **bluexrider said:**
> For the laymen.....what is jupiter and how can it fix the issue

[jupiter]("http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html") lets you select performance modes, device controls and much more. :)

---

### Post by Plumtreed on 2011-11-30
...suggest you Google Jupiter to see what it can do...it is an app created to improve the performance of netbooks & laptops especially in the area of power conservation. It works exceptionally well on my eeepc701.

For the best instalation on an Ubuntu OS google 'Webupd8 Jupiter'

---

### Post by farrinux on 2011-11-30
> **bluexrider said:**
> For the laymen.....what is jupiter and how can it fix the issue
I believe Jupiter is the power management package located at the webup8.org ppa's. the link is in an above post. For me I haven't tried as my netbook does not have an issue with 11.10, so I do not know if it works.

---

### Post by Lalaith on 2011-12-02
Is it safe to download it from the web (webup8.org)? Why can't Jupiter be found on the repository?

---

### Post by HavoK360 on 2011-12-02
I know I am a newbie to Ubuntu, but difinetly not to the whole computer universe.
I have a theory on the problem at hand, actually a few:
1) Your computer MAY be trying to boot both Operating Systems at the same time (Check the processes at hand on the computer)
2)After getting something awesome, the computers brain got exploded, ad is now a zombie (Hey its just a theory!)
3)You are just noticing the problem
4)Ubuntu, while being lower profile that Windows 7, may have some un-nessicary program fault in the installation process, such ad accidently installing a program file twice due to a bad burn. Try running windows and see if it happens there as well.
And I also recomend checking the Dell fourms section on here.
Good luck!

---

### Post by wbrucem on 2011-12-02
> **grahammechanical said:**
> In 11.10 when we click Shut Down we are asked to confirm. This is when we get the option to continue with the Shut Down or to Restart. Are you saying that this option is not available to you?


Ah, for years I've had my Ubuntu configured *NOT* to ask me for those superfluous confirmations, so now I have no option to restart, only shutdown. :(

---

### Post by BC59 on 2011-12-03
> **Lalaith said:**
> Is it safe to download it from the web (webup8.org)? Why can't Jupiter be found on the repository?

WebUp8 is official Ubuntu PPA:
[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)
If you don't use the webupd8 PPA you can download and install it from Sourceforge.

> **bluexrider** For the laymen.....what is jupiter and how can it fix the issue

"Jupiter, is an application created by Fewt for Aurora OS (ex Eeebuntu) (but also works in other Linux distributions) which can be used to switch between maximum and high performance and power saving mode, change the resolution and orientation, enable or disable the bluetooth, touchpad, WiFi and so on. But most importantly it allows your Eeepc netbook to take advantage of SHE (Super Hybrid Engine).
Jupiter is not just for EeePC, it also works on other netbooks or laptops. Read our [Jupiter]("http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html") review for more info."

---

### Post by Lalaith on 2011-12-07
> **BC59 said:**
> 
But most importantly it allows your Eeepc netbook to take advantage of SHE (Super Hybrid Engine).
Jupiter is not just for EeePC, it also works on other netbooks or laptops. Read our [Jupiter]("http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html") review for more info."

I have installed Jupiter **and** jupiter-support-eee (I own a SHE Computer). How can I check that Jupiter-support-eee is also running?

(Should I start a new conversation for this question? Maybe I'm going too far from the initial topic of this thread :confused:)

---

### Post by BlinkinCat on 2011-12-07
> **Lalaith said:**
> I have installed Jupiter **and** jupiter-support-eee (I own a SHE Computer). How can I check that Jupiter-support-eee is also running?

(Should I start a new conversation for this question? Maybe I'm going too far from the initial topic of this thread :confused:)

Lalaith, it probably would be best to start your own thread - :)

---

### Post by pavanmatham on 2011-12-09
> **grahammechanical said:**
> In 11.10 when we click Shut Down we are asked to confirm. This is when we get the option to continue with the Shut Down or to Restart. Are you saying that this option is not available to you?

As regards hibernation do you have enough swap space so that the operating system can be moved out of RAM and on to the hard disk? 

Regards.

Hi Graham,

Many thanks for your reply. 

1. Regarding ' Restart' option, I am very sorry to post my problem that I really could not see! (oversee!) the restart option. It it at left corner while the other two are at right side. 

2. Regarding Hibernation, the problem remains same ...... attached herewith a screen shot to show you the swap size.  If the size is not enough, is there any thing possible to sort out the problem?


Thanks and regards,

Pavan

---

### Post by fabio_floripa on 2012-03-17
I installed 11.10 on my dell inspiron 4110. It fu***ed my laptop. the fans are runing 100% all the time, battery lasts less than 2h and wireless signal is very poor compared to win 7. ubuntu 11.10 unity really pissed me of. Do you guy think it is a bad idea to go back to 10,04 ??  This is my working/Colege lap top, I have no time to dive into google to try to discover a possible fix.. 10.04 looks the best choice huh??
Tks for any response...

---

### Post by ixtok on 2012-03-17
Go with whatever works for you, even if that might be Windows 7.

---

