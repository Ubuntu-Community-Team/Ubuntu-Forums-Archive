---
title: "might be leaving Linux  [ But where to go ?? ]"
date: 2012-07-09
forum: Recurring Discussions
---

### Post by MikeMiracle on 2012-07-09
Hi Experts,

                   I have been exclusively using Linux/Ubuntu for last 4 years. But now reached a state where I need to say goodbye to it. I am fed up with my DELL inspiron n5010's overheating. I am worried about the health of laptop now.I have tried most of the tricks . i have jupitor installed also.  I am having another annoying problem of left mouse clicks not working regularly until I do CTRL + FN to a non-GUI tty.

                 I understand  that , without contributing anything significant ,  it is not fair for me to complain.so no complaints. Instead I am thankful to the community for providing me such a wonderful computing experience for the last 4-5 years.
Can anybody suggest me an alternative to go.Here are my ideas.

1. Go back to Windows ( Its hard to use windows after tasting Linux's freedom , but i badly need a working system)
2. Use an older  distro with older version of kernel ( which has no overheating bug & the other bug ) [Any suggestions ? ]
3. Use some other  with a GUI which neither uses Linux Kernel nor Windows ( I am not sure here .. can I use opensolaris , freebsd ,android, chrome os .. pls suggest) 

I just need an OS which will allow me to browse and use common programs.

---

### Post by dino99 on 2012-07-09
its important to choose hardware which is compatible with the OS

i suppose you still have searched and read those threads:

[http://www.google.fr/#hl=fr&sclient=psy-ab&q=ubuntu+dell+inspiron+n5010&oq=ubuntu+n5010&gs_l=hp.1.3.0i5i30i19j0i8i30l2j0i8i30i19.886.886.4.5418.1.1.0.0.0.0.46.46.1.1.0...0.0.cBihSBdp9M8&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=d036f38857a5b17a&biw=1680&bih=893](http://www.google.fr/#hl=fr&sclient=psy-ab&q=ubuntu+dell+inspiron+n5010&oq=ubuntu+n5010&gs_l=hp.1.3.0i5i30i19j0i8i30l2j0i8i30i19.886.886.4.5418.1.1.0.0.0.0.46.46.1.1.0...0.0.cBihSBdp9M8&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=d036f38857a5b17a&biw=1680&bih=893)

and/or this forum:

[http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

and/or : [http://linux.dell.com/](http://linux.dell.com/)

---

### Post by Onesimus on 2012-07-09
I have a Dell Inspiron 6400, and unless I install i8kutils it overheats. You could try the following:
```

sudo apt-get install i8kutils

## Force loading at boot
echo "i8k force=1" | sudo tee -a /etc/modules
```

You then have to edit the file: /etc/default/i8kmon 
and change ENABLED=0 to ENABLED=1

Reboot the machine, and all should be fine.

---

### Post by insane_alien on 2012-07-09
have you tried cleaning it out? 90% of overheating laptop problems i've seen are because there is an unholy dust bunny inhabiting the heatsink.

---

### Post by sffvba[e0rt on 2012-07-09
*Thread moved to **The Community Cafe**.*


404

---

### Post by madjr on 2012-07-09
can you give us the current the temp.

[http://www.webupd8.org/2012/07/monitor-hardware-temperature-in-ubuntu.html](http://www.webupd8.org/2012/07/monitor-hardware-temperature-in-ubuntu.html)

---

### Post by angryfirelord on 2012-07-09
First, what video chipset does the laptop have? The open-source radeon driver runs at its highest setting in its default state, which will generate a lot of heat. 
> Go back to Windows ( Its hard to use windows after tasting Linux's freedom , but i badly need a working system)
If you still want to experiment with Linux, create a dual-boot system. That way, if you're having issues, you can at least use your laptop until you figure it out. Even if you end up just using Windows, the large majority of open-source applications have Windows binaries available, so you'll still be able to use the same apps in Ubuntu.
> Use an older distro with older version of kernel ( which has no overheating bug & the other bug ) [Any suggestions ? ]
That would be 10.04, which uses a 2.6.32 kernel. That's pretty much the oldest you're going to be able to go back to while still getting security updates.
> Use some other with a GUI which neither uses Linux Kernel nor Windows ( I am not sure here .. can I use opensolaris , freebsd ,android, chrome os .. pls suggest)

Other operating systems will have less support than Linux, which includes support for power management.

---

### Post by Tombgeek on 2012-07-09
> **MikeMiracle said:**
> 1. Go back to Windows ( Its hard to use windows after tasting Linux's freedom , but i badly need a working system)

Well, I moved to Windows 7 from Ubuntu 10.04 and I still use it as my primary OS (Ubuntu as a secondary). I can understand your concern, though Windows is quite versatile if you know what to do; you don't have to deal with Microsoft's lock-ins. Most of the software I use is available on Linux as well. Check MakeUseOf's list of decent Windows software.

> **MikeMiracle said:**
> 2. Use an older  distro with older version of kernel ( which has no overheating bug & the other bug ) [Any suggestions ? ]


What version are you running now? If you want, you could perhaps move to an older LTS like 10.04.
Or have you tried a lighter desktop environment (like XFCE)?

> **MikeMiracle said:**
> 
3. Use some other  with a GUI which neither uses Linux Kernel nor  Windows ( I am not sure here .. can I use opensolaris , freebsd  ,android, chrome os .. pls suggest) 

I just need an OS which will allow me to browse and use common programs.

Chrome OS isn't really an option unless all your work is done in a web browser. I'm not sure about OpenSolaris or FreeBSD though.
Or you could buy a Mac :P

---

### Post by O2Blevel on 2012-07-09
Have you tried 12.04. My Dell laptop temperature dropped about 10 degrees F, going from 11.10 to 12.04.

---

### Post by Primefalcon on 2012-07-09
sorry to hear about you leaving (if you do).

if you do decide to go back to windows, don't forget you have putty, which is a linux command line for windows, it comes with easy installers for ssh and such... so you can still use a lot of the same tools that you use under Linux cli there...

link's here for easy convenience: [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

### Post by bryncoles on 2012-07-09
With the latest Kernel, my Dell Inspiron 1525 started overheating like a... thing.  Which overheats.  And then Shutsdown without warning.  Regularly.  Regression the Kernel didn't help.  

Then (as someone above mentioned), it turned out to be a hardware problem, which Dell themselves provided [guidance about](http://support.dell.com/support/edocs/systems/ins1525/en/SM/cpucool.htm).  Basically, take out the thermal cooling unit, remove dust, replace the thermal cooling unit!

I also reverted flash from the latest release to one prior.  No more overheating for me!  Perhaps it'll help you too?

---

### Post by buzzingrobot on 2012-07-09
All open source operating  systems will offer the same drivers, given enough time for them to be spread around. So if your laptop runs hot with Linux, it almost certainly will run hot with any of the other OS's you mentioned. However, the only way to know is to try them.

I'm assuming you've tried the proprietary drivers with no success.

If you like Gnome 2, Centos 6.3 was released  today. It's a recompilation of Red Hat Enterprise Linux, with the Red Hat branding and trademarks removed.  it runs a (thoroughly patched and updated by Red Hat) 2.6 kernel.  Centos is a very popular server distribution, but it works very well on the desktop.  (I've used it.) It runs Gnome 2.  A bit of Googling will show how to add media codecs and the major current applications. It's very tested and very reliable.

---

### Post by 3Miro on 2012-07-09
Is the overheating the only reason why you ware considering leaving? If the overheating is a hardware issue, then you will see it in any OS. If it is due to a single bug in the kernel, you can just use older version of Ubuntu (10.04) until they fix the bug, or you can go to Debian or CentOS or maybe even Mint.

If you are experiencing issues with hardware incompatibility, then I suggest you get a machine from a Ubuntu vendor (like System76). Then you will receive official support and quick bug fixes and so on.

---

### Post by thatguruguy on 2012-07-09
> **3Miro said:**
> Is the overheating the only reason why you ware considering leaving? If the overheating is a hardware issue, then you will see it in any OS. If it is due to a single bug in the kernel, you can just use older version of Ubuntu (10.04) until they fix the bug, or you can go to Debian or CentOS or maybe even Mint.

If you are experiencing issues with hardware incompatibility, then I suggest you get a machine from a Ubuntu vendor (like System76). Then you will receive official support and quick bug fixes and so on.

Just out of curiosity, if it is a problem with the kernel, how will moving to Mint help?

Although I suspect there's a good chance that the over-heating problem the OP has is due to a build up of dust inside the case of his laptop.

---

### Post by ronnysingh on 2012-07-09
I've been using Ubuntu since two and half years and have not faced any major problem so far. If will ever have to use Windows/Mac for anything then I'll get a separate machine for that purpose. Ubuntu has never given me any problem with viruses. I also want to say that I am from a small city of India and am one of two Linux users in whole city. People across the city worship Windows and give business to computer shop owners as their OS can't remain clean after a few weeks of each re-installation of whatever version of Windows. Only Mac users are living as peacefully as Linux users.

---

### Post by MikeMiracle on 2012-07-10
Hi Guys,
              Thanks a lot for your replies. Actually I never had any problems till I upgraded to 12.04. over heating problem started with 12.04. All other versions worked perfectly with my system.
So I guess I can try older versions of ubuntu or other distros. Also thanks a lot for centos suggestion.I use RHEL servers at my workplace. so centos makes perfect sense career wise. cheers. I will try that. Yesterday I tried to install Mint 13 , but installation is not getting completed due to overheating :-) so my specific problem has something to do with the latest Kernels. I need to look at the hardware as well. Good suggestions.. thanx ..
 
Cheers,
Mike

---

### Post by vasa1 on 2012-07-10
> **MikeMiracle said:**
> ...
1. Go back to Windows ( ... i badly need a working system) ...
I just need an OS which will allow me to browse and use common programs.
This ^^^

---

### Post by MikeMiracle on 2012-07-10
> **vasa1 said:**
> This ^^^

slum dog :-)

---

### Post by buzzingrobot on 2012-07-10
> **MikeMiracle said:**
> Hi Guys,
              Thanks a lot for your replies. Actually I never had any problems till I upgraded to 12.04. over heating problem started with 12.04. All other versions worked perfectly with my system.
So I guess I can try older versions of ubuntu or other distros. Also thanks a lot for centos suggestion.I use RHEL servers at my workplace. so centos makes perfect sense career wise. cheers. I will try that. Yesterday I tried to install Mint 13 , but installation is not getting completed due to overheating :-) so my specific problem has something to do with the latest Kernels. I need to look at the hardware as well. Good suggestions.. thanx ..
 
Cheers,
Mike

The CentOS mirrors ought to be populated with 6.3 by now.  There are 2 install DVD iso's. You really need only the first one. (You can adjust package selection during the install so presumably you will be prompted if the second DVD is needed.)

The first DVD, though, is 4 GB.  A net install iso, at a bit less than 200 mb, is also available.

I'm was running 12.04 with gnome-shell, then moved to Mint 13 Cinnamon.  Very nice, but so was CentOS 6.2 when I used that. It's tempting to move to 6.3 because everything I do on Linux can be done in CentOS. 

If you move to CentOS, take a look at what the CentOS wiki says about using the independent repos available for it.  If you are a stickler about font rendering like me, freetype that shipped with 6.2 didn't have hinting enabled.  Infinality works, and a user named lemonzest has a repo with libxft, cairo, and free type with hinting.  I used those files with good results. Search the Scientific Linux forum for that thread.

---

### Post by Onesimus on 2012-07-10
> **Onesimus said:**
> I have a Dell Inspiron 6400, and unless I install i8kutils it overheats. You could try the following:
```

sudo apt-get install i8kutils

## Force loading at boot
echo "i8k force=1" | sudo tee -a /etc/modules
```

You then have to edit the file: /etc/default/i8kmon 
and change ENABLED=0 to ENABLED=1

Reboot the machine, and all should be fine.

@MikeMiracle
Did you have any success with my suggestion ?

---

### Post by wilee-nilee on 2012-07-10
> **Onesimus said:**
> I have a Dell Inspiron 6400, and unless I install i8kutils it overheats. You could try the following:
```

sudo apt-get install i8kutils

## Force loading at boot
echo "i8k force=1" | sudo tee -a /etc/modules
```You then have to edit the file: /etc/default/i8kmon 
and change ENABLED=0 to ENABLED=1

Reboot the machine, and all should be fine.

+1 on the 18kutils, you can control the the fans speed and temps at running.

---

### Post by sunfromhere on 2012-07-10
> **insane_alien said:**
> have you tried cleaning it out? 90% of overheating laptop problems i've seen are because there is an unholy dust bunny inhabiting the heatsink.

This!
If the computer started out on normal temperatures when you bought it, and then after 6 /or if HP, less/ months of usage temperatures got higher, it's this.

Also, one tip. If you tend to eat, smoke and create dust particles around your laptop, turn it off at night and put it upside down. In the morning, take a dust cloth and lift the "bottom" (now the upper) part of your computer and wipe the screen. You'll be surprised to know how much junk comes out. (Doing this once a month keeps my laptop at normal temperatures)

---

### Post by MikeMiracle on 2012-07-11
> **Onesimus said:**
> @MikeMiracle
Did you have any success with my suggestion ?

@Onesimus Sorry for not updating before. I tried your suggestion. But it didnt work out in my Dell insipron n5010.

Right now , I am in Mint 13 (knew that Mint is based on Ubuntu , but just installed it , as I had a Mint CD) , which has same issues as Ubuntu.


[LIST=1]
[*]overheating
[*]strange x.org/touchpad/mouse bug which will make mouse left clicks not working
[/LIST]
 In combination , these issues make the user experience annoying.Normal work around for issue 2 in Ubuntu is changing to an non GUI tty by CLT + ALT+ FN . This no longer works in Mint 13 Maya.No other way than system reboot.

I am gonna try buzzingrobot's suggestion of installing CENTOS next.

I have never opened a laptop , thus bit reluctant at opening and checking it. As suggested by  sunfromhere, **insane_alien** & others  , this might be a dust/ thermal paste issue.If centos won't work , I am gonna open up the laptop.

Thanks you all for valuable suggestions.

---

### Post by MikeMiracle on 2012-07-12
UPDATE

[B]CENTOS
[/B]
Unfortunately I couldn't install CENTOS as it didn't recognize my wifi card. With wired connection also not working (altogether another issue , don't want to digress ), CENTOS doesn't look promising.

**LINUX MINT 13**

With Jupitor & kernal params for aspm & rc6 and proprietary fglrx as the video driver, Linux Mint 13 works OK. It hots up to 70s with live video. But OK as my system can tolerate up to 90 degree celsius. But mouse left click functionality  stops occasionally and need a X restart occasionally.

**STRATEGY**

Now I think my issues (overheating and X ) are better addressed in latest kernels. Also I plan to use latest proprietary driver from ATI website directly , if open source driver has any problems.

**IMMEDIATE PLAN **

I am planning to try Fubuntu next for the 2 reasons

1. It has better power management & optimised for laptops
2. It has 3.4 Kernel.

**SUGGESTIONS**?

Are you aware of any other distro fitting my needs ?

---

### Post by madjr on 2012-07-12
> **MikeMiracle said:**
> UPDATE

[B]CENTOS
[/B]
Unfortunately I couldn't install CENTOS as it didn't recognize my wifi card. With wired connection also not working (altogether another issue , don't want to digress ), CENTOS doesn't look promising.

**LINUX MINT 13**

With Jupitor & kernal params for aspm & rc6 and proprietary fglrx as the video driver, Linux Mint 13 works OK. It hots up to 70s with live video. But OK as my system can tolerate up to 90 degree celsius. But mouse left click functionality  stops occasionally and need a X restart occasionally.

**STRATEGY**

Now I think my issues (overheating and X ) are better addressed in latest kernels. Also I plan to use latest proprietary driver from ATI website directly , if open source driver has any problems.

**IMMEDIATE PLAN **

I am planning to try Fubuntu next for the 2 reasons

1. It has better power management & optimised for laptops
2. It has 3.4 Kernel.

**SUGGESTIONS**?

Are you aware of any other distro fitting my needs ?

12.10 dev might be worth trying too, maybe help also report any bugs early.

you may also check the 12.10 forums

---

### Post by KL_72_TR on 2012-07-15
> **MikeMiracle said:**
> 
I just need an OS which will allow me to browse and use common programs.
If you don't want to keep up with Linux or Windows, well, than consider this:
[http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html)
Free and GNU GPL. Read FAQ.
I hope you have fun :-)

---

### Post by Bigtime_Scrub on 2012-07-15
> **MikeMiracle said:**
> UPDATE

[B]CENTOS
[/B]
Unfortunately I couldn't install CENTOS as it didn't recognize my wifi card. With wired connection also not working (altogether another issue , don't want to digress ), CENTOS doesn't look promising.

**LINUX MINT 13**

With Jupitor & kernal params for aspm & rc6 and proprietary fglrx as the video driver, Linux Mint 13 works OK. It hots up to 70s with live video. But OK as my system can tolerate up to 90 degree celsius. But mouse left click functionality  stops occasionally and need a X restart occasionally.

**STRATEGY**

Now I think my issues (overheating and X ) are better addressed in latest kernels. Also I plan to use latest proprietary driver from ATI website directly , if open source driver has any problems.

**IMMEDIATE PLAN **

I am planning to try Fubuntu next for the 2 reasons

1. It has better power management & optimised for laptops
2. It has 3.4 Kernel.

**SUGGESTIONS**?

Are you aware of any other distro fitting my needs ?
 

 I would suggest Fedora. It is more desktop oriented than CentOS. You will need to do a lot of configuration with CentOS to get it into a solid desktop. Fedora is very innovative and it will eventually become Red Hat. You get to see what Red Hat will be before it is made. Fedora has also gotten very good at detecting all your hardware with only free software.

---

### Post by MikeMiracle on 2012-07-16
UPDATE

Finally, I am settled with Linux Mint 13 (Maya) . Most of the other ditrsos (fubuntu , centos etc)didn't recognize my wireless card. With proprietary fglrx drivers & jupiter application for power management Mint is rock solid. It may heat up to 70s with video. But still workable as my machine can tolerate up to 90.  Mint 13 looks good, I am loving it.Thanks everybody for the comments. Thank you to all those invisible developers working behind making these amazing distributions. Linux world rocks. Its impossible to go back to Windows after tasting 4 years of Linux Freedom. :-)

---

### Post by madjr on 2012-07-17
> **MikeMiracle said:**
> UPDATE

Finally, I am settled with Linux Mint 13 (Maya) . Most of the other ditrsos (fubuntu , centos etc)didn't recognize my wireless card. With proprietary fglrx drivers & jupiter application for power management Mint is rock solid. It may heat up to 70s with video. But still workable as my machine can tolerate up to 90.  Mint 13 looks good, I am loving it.Thanks everybody for the comments. Thank you to all those invisible developers working behind making these amazing distributions. Linux world rocks. Its impossible to go back to Windows after tasting 4 years of Linux Freedom. :-)

90 degrees is a pretty high, so getting extra cooling for those intensive tasks would be great till the new kernels fix the issues (hopefully next ubuntu, which you could start testing).

anyway glad to see the problem is better.

---

