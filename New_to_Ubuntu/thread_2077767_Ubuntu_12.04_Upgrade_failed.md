---
title: "Ubuntu 12.04 Upgrade failed"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by rohkap4444 on 2012-10-29
I am very much new to Ubuntu. Now after 2 upgrades I have 12.04 LTS. At the time of installation something bad happened and the main screen disappeared. After few hours assuming that it would have been finished, I shut down my **Laptop, which is an old one now and does not have the option in BIOS to boot from CD/ USB.**
Now I am facing a big problem, I do not have Ubuntu icon or any other icon in my Ubuntu,nothing comes in search when I write something in Dash home. I figured out how to reboot from terminal but it is VERY FRUSTRATING for me.
Please help me to find all these icons. I will be very very grateful to you.


Regards

---

### Post by amjjawad on 2012-10-29
> **rohkap4444 said:**
> I am very much new to Ubuntu. Now after 2 upgrades I have 12.04 LTS. At the time of installation something bad happened and the main screen disappeared. After few hours assuming that it would have been finished, I shut down my **Laptop, which is an old one now and does not have the option in BIOS to boot from CD/ USB.**
Now I am facing a big problem, I do not have Ubuntu icon or any other icon in my Ubuntu,nothing comes in search when I write something in Dash home. I figured out how to reboot from terminal but it is VERY FRUSTRATING for me.
Please help me to find all these icons. I will be very very grateful to you.


Regards

Hello and Welcome to Ubuntu Forum :)

Thanks for starting a new thread over here as advised on the mailing list ;)

Well, I don't use Ubuntu anymore, I'm a member of Lubuntu Team and I use Lubuntu only but I will for sure help you as much as possible.

First thing first, would you please list the hardware specifications of your machine?
Second of all, what was the version of Ubuntu you had?

Now, you mentioned that you have a big problem but let's cool down and make it easier :D

Can you login to your desktop?

---

### Post by rohkap4444 on 2012-10-29
> **amjjawad said:**
> Hello and Welcome to Ubuntu Forum :)

Thanks for starting a new thread over here as advised on the mailing list ;)

Well, I don't use Ubuntu anymore, I'm a member of Lubuntu Team and I use Lubuntu only but I will for sure help you as much as possible.

First thing first, would you please list the hardware specifications of your machine?
Second of all, what was the version of Ubuntu you had?

Now, you mentioned that you have a big problem but let's cool down and make it easier :D

Can you login to your desktop?
Thanks a lot for your quickest  reply.
My Laptop specification:
Made Sony Vaio VGN_CR24G
HDD 120 GB
RAM 1 GB
Processor Intel Core 2 Duo Processor t7250
I had Ubuntu 11.04 in which nothing was working after days of searching I found a very simple option for upgrade. I upgraded to 11.10 and after few minutes I started upgrade for 12.04 LTS. After an hour my screen goes blank with pink color background. I thought not to worry as process was going smoothly. In the morning ( after 7 hours or so) I turned on my Laptop after switching off ( as the same screen was there). When it restarted nothing was there, I tried dash home to search, " Sorry, there nothing matches your search".
I am very new to Ubuntu and I am sticking to it as my younger brother wants to have a Linux on our laptop. But no FB video chat, installation requires extra efforts than MS. But do not worry I am here to stay with it, it is a challenge for me and I have accepted it. 
Tell me please why did you move away from Ubuntu, will you suggest same for me.

---

### Post by amjjawad on 2012-10-29
> **rohkap4444 said:**
> Thanks a lot for your quickest  reply.
My Laptop specification:
Made Sony Vaio VGN_CR24G
HDD 120 GB
RAM 1 GB
Processor Intel Core 2 Duo Processor t7250
I had Ubuntu 11.04 in which nothing was working after days of searching I found a very simple option for upgrade. I upgraded to 11.10 and after few minutes I started upgrade for 12.04 LTS. After an hour my screen goes blank with pink color background. I thought not to worry as process was going smoothly. In the morning ( after 7 hours or so) I turned on my Laptop after switching off ( as the same screen was there). When it restarted nothing was there, I tried dash home to search, " Sorry, there nothing matches your search".
I am very new to Ubuntu and I am sticking to it as my younger brother wants to have a Linux on our laptop. But no FB video chat, installation requires extra efforts than MS. But do not worry I am here to stay with it, it is a challenge for me and I have accepted it. 
Tell me please why did you move away from Ubuntu, will you suggest same for me.

Ok, I promised to keep this as simple as possible and I will keep my words :D

You simply upgraded a system that wasn't working 100% correctly. 
> I had Ubuntu 11.04 in which nothing was working
Having that said, please be advised that "upgrading" in such case may not fix your issue, it may actually make it harder to fix.
We usually advise to do a fresh new installation.

We can still try to do something but IMHO and from my long experience with such issues, it is better to do a clean fresh install but of course you need to backup your data.
You mentioned that machine has no CD Drive and can't boot from USB, right?
Does it have an USB Port?

As why I moved to Lubuntu? that because Lubuntu is much faster, much simpler and doesn't give me hard time when I use it.

On your machine, Lubuntu will breath new life and it would be so fast.
I have it on less than 512MB RAM machine and it works perfectly.
So, yes, I would advise to go for Lubuntu instead.

Ubuntu with Unity on 1GB RAM is not a prefect choice.

And you are welcome anytime ;)

---

### Post by rohkap4444 on 2012-10-29
Yes I have USB ports, USB Cd drive and USB hard drive. Please tell me that why people are going for Ubuntu and not for Lubuntu as you are saying it is very fast. Why when there is no FB video chatting and it is very hard to install anything on it. 
I want to install through fresh installation. I have tried with boot-able USB pen drive, have made a cd from .iso file. But as I have said my system is not booting from any one of the above I am unable to do installation.
Now please tell me what to do.

I am very impressed and thankful to you to give me support in a blink of eyes. Thanks a lot. I hope you can solve my problem.:)

---

### Post by pedro.nariyoshi on 2012-10-29
Try installing gnome-tweak tool
```
sudo apt-get install gnome-tweak-tool
```

Probably your icon settings are misconfigured.
Hope that helps.

---

### Post by rohkap4444 on 2012-10-29
This is what I got
E: Unable to locate package gnome-tweak-tool.
Even I do not know where this Ubuntu is installing as the above line has starting letter "E:". Why on E partition and why not on primary partition. 
Anyway thanks for you help.

Regards

---

### Post by pedro.nariyoshi on 2012-10-29
Seems like your instalation might be more seriously damaged.

Tell me what this yields:

```
cat /etc/apt/sources.list 
```

---

### Post by amjjawad on 2012-10-29
> **rohkap4444 said:**
> Yes I have USB ports, USB Cd drive and USB hard drive.
That is great to know. If your machine can actually boot from a CD Drive and/or USB Drive, then that would great too.

> Please tell me that why people are going for Ubuntu and not for Lubuntu as you are saying it is very fast. 
It is a matter of choice, that is all. With Linux, you are totally free to choose the system that works better for YOU. There is NO prefect OS, that is for sure. However, there is, in someone's opinion, a perfect system for his/her needs. So, it's a matter of choice.

> Why when there is no FB video chatting and it is very hard to install anything on it. 

See this: [https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu](https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu)

It's not that Lubuntu is better or worse than Ubuntu. We can't blame the system all the time.

> I want to install through fresh installation. 

Good :)

> I have tried with boot-able USB pen drive, have made a cd from .iso file. But as I have said my system is not booting from any one of the above I am unable to do installation.
Now please tell me what to do.

First thing first, you need to enter your BIOS and make sure your CD Drive (if you want to install from a LiveCD) is set to be the first device to boot from:

[IMG]http://i56.tinypic.com/11hteoh.jpg[/IMG]

Please note that your BIOS could be different than mine. However, same concept.

If you want to boot from a LiveUSB, then make sure to go to Hard Disk Boot Priority (or something similar to this as per your BIOS) and:

[IMG]http://i51.tinypic.com/ezn95j.jpg[/IMG]

Save the changes on your BIOS and check if you can now boot from that LiveCD or LiveUSB.

For creating a LiveCD:
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

For creating a LiveUSB:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If you are going to use the LiveCD, I recommend to check MD5SUM for your downloaded iso and burn it at 8x for example.

If you are going to use the LiveUSB, I recommend to use UNetbootin.

HOWTO check MD5SUM?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)


> I am very impressed and thankful to you to give me support in a blink of eyes. Thanks a lot. I hope you can solve my problem.:)
It is my pleasure to guide a new comer to Ubuntu or Linux in general and help him/her as much as I can because after all, it is a community and we are like one family. I did nothing yet. I do hope we can sort it out and fix that soon :)

Best of luck and I'm here to help!

---

### Post by amjjawad on 2012-10-29
> **pedro.nariyoshi said:**
> Try installing gnome-tweak tool
```
sudo apt-get install gnome-tweak-tool
```

Probably your icon settings are misconfigured.
Hope that helps.

Please do not advise to install more packages while the main system has already problems. This will make it worse :)

Thanks!

---

### Post by rohkap4444 on 2012-10-29
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

This is what I got.I hope it can help you. I am sorry I do not understand these things so I copy and paste it as it is. If you dislike this effort of mine, I apologize to you.

---

### Post by cybergalvez on 2012-10-29
> **rohkap4444 said:**
> Yes I have USB ports, USB Cd drive and USB hard drive. Please tell me that why people are going for Ubuntu and not for Lubuntu as you are saying it is very fast. Why when there is no FB video chatting and it is very hard to install anything on it. 
I want to install through fresh installation. I have tried with boot-able USB pen drive, have made a cd from .iso file. But as I have said my system is not booting from any one of the above I am unable to do installation.
Now please tell me what to do.

I am very impressed and thankful to you to give me support in a blink of eyes. Thanks a lot. I hope you can solve my problem.:)

There is no FB vid chat because FB created a windows only plugin based on Skyp rather than use something a little more standard. Blame FB not ubuntu

---

### Post by rohkap4444 on 2012-10-29
Friend, if I forgot to tell you that my BIOS does have three option for USB,
1. Hard drive
2. Flash Drive
3.( not sure) but it is for Floopy drive as Laptop generally do not have floppy drive.

I tried first two but nothing worked. MY system start as normal and bypass this configuration of starting from USB. It is very strange for me. I have seen so many machine even older than this but they all had some kind of USB option which worked.

Now I think you are gonna say to me to throw away this Laptop. :) I want to but new one but money is the biggest problem. So I am searching for the option and ways to do my job and I hope I will get the solution. 

I did get a way to install Plop Boot manager but as mention on the related thread of Plop boot Manager that somebody's system is showing , no such file when he select this Manager. The same happened to me :(

Now if you still thinks my problem can be solved than I will appreciate your efforts and if not, I pay lots of thanks as I think everything is getting stuck at BIOS and unfortunately my Laptop BIOS is of the age of old King. :).

Anyways I am waiting for your reply.

---

### Post by pedro.nariyoshi on 2012-10-29
> **amjjawad said:**
> Please do not advise to install more packages while the main system has already problems. This will make it worse :)

Thanks!

Since the problem he mentioned was just about the icons, I believed this could help. I didn't know that was not advisable. (Well, to my defense, gnome-tweak-tool is quite harmless compared to ccsm or dconf-editor and the likes)

I was about to suggest a "sudo apt-get -f install" for him, do you think it could help? Although a broken installation is really tricky. He is probably better off with a clean install.

---

### Post by amjjawad on 2012-10-29
> **rohkap4444 said:**
> Friend, if I forgot to tell you that my BIOS does have three option for USB,
1. Hard drive
2. Flash Drive
3.( not sure) but it is for Floopy drive as Laptop generally do not have floppy drive.

I tried first two but nothing worked. MY system start as normal and bypass this configuration of starting from USB. It is very strange for me. I have seen so many machine even older than this but they all had some kind of USB option which worked.

Now I think you are gonna say to me to throw away this Laptop. :) I want to but new one but money is the biggest problem. So I am searching for the option and ways to do my job and I hope I will get the solution. 

I did get a way to install Plop Boot manager but as mention on the related thread of Plop boot Manager that somebody's system is showing , no such file when he select this Manager. The same happened to me :(

Now if you still thinks my problem can be solved than I will appreciate your efforts and if not, I pay lots of thanks as I think everything is getting stuck at BIOS and unfortunately my Laptop BIOS is of the age of old King. :).

Anyways I am waiting for your reply.

Asking you to buy new machine is giving up and I have no such word in my dictionary ;)

If you go back and check the two screenshots I have posted before for BIOS, you will notice that BIOS does not clearly say USB or Flash Drive. On that Screenshot, USB Drives are treated as Hard Disk Drives. That is why, you need to check that in your BIOS.

Can you take a picture and post it here? I will guide you step by step and don't worry, I love to do this.

---

### Post by amjjawad on 2012-10-29
> **pedro.nariyoshi said:**
> Since the problem he mentioned was just about the icons, I believed this could help. I didn't know that was not advisable. (Well, to my defense, gnome-tweak-tool is quite harmless compared to ccsm or dconf-editor and the likes)

I was about to suggest a "sudo apt-get -f install" for him, do you think it could help? Although a broken installation is really tricky. He is probably better off with a clean install.

Never mind :)
In fact, he mentioned that he upgraded a system that was already broken. Usually, we don't recommend that. Also, we think Fresh New Installation is much better.

What I mean by "we" is myself and many other guys over here :)

You are trying to help and this is very much appreciated.

If you ever would like to try Lubuntu, ping me. I'm one of the members and I will do my best to answer any Q in your mind.

---

### Post by pedro.nariyoshi on 2012-10-29
> **rohkap4444 said:**
> 

This is what I got.I hope it can help you. I am sorry I do not understand these things so I copy and paste it as it is. If you dislike this effort of mine, I apologize to you.

Don't worry, you did everything I expected. (;

There doesn't seem to be any problem with this. You will probably be better off with a clean install of _ubuntu. Besides Lubuntu (which is great), I would recommend Ubuntu Gnome Remix for you (although 1GB might be too close to the minimum requirements). Test it out and see what you prefer.

> **rohkap4444 said:**
> Now I think you are gonna say to me to throw away this Laptop.

No, no, no (:
Keep your laptop. We are here to help. "Throw your laptop away and buy a new one" is not a valid support answer (unless you are using another OS, haha)

If neither of these options work for you. Try finding a friend who uses Ubuntu. They are likely to have a CD/DVD with Ubuntu for you. You could also try to put your laptop harddrive into another computer, install Ubuntu and then transfer back to your computer. It is a little troublesome though. ): (But less troublesome than getting money for a new laptop)

---

### Post by amjjawad on 2012-10-29
> **rohkap4444 said:**
> unfortunately my Laptop BIOS is of the age of old King. :).


If you really think you really think you got an old machine, then may I cheer you up and shock you at the same time? :P

[http://ubuntuforums.org/showpost.php?p=11832431&postcount=152](http://ubuntuforums.org/showpost.php?p=11832431&postcount=152)

---

### Post by pedro.nariyoshi on 2012-10-29
> **amjjawad said:**
> Never mind :)
In fact, he mentioned that he upgraded a system that was already broken. Usually, we don't recommend that. Also, we think Fresh New Installation is much better.

What I mean by "we" is myself and many other guys over here :)

You are trying to help and this is very much appreciated.

If you ever would like to try Lubuntu, ping me. I'm one of the members and I will do my best to answer any Q in your mind.

I am very grateful for the Lubuntu guys. You put a lot of effort to get Lubuntu to be an official Ubuntu flavor. I currently use it on a MK802 and it's great.

---

### Post by amjjawad on 2012-10-29
> **pedro.nariyoshi said:**
> I am very grateful for the Lubuntu guys. You put a lot of effort to get Lubuntu to be an official Ubuntu flavor. I currently use it on a MK802 and it's great.

I'm glad to know that :D
You are most welcome! thanks for choosing and using Lubuntu and please, if you have a facebook account, you can have some fun with us [here]("https://www.facebook.com/groups/lubuntu.official/").

In case you may face any issue with Lubuntu, feel free to PM here or Email me. I think all my information is on my signature.

Take care ;)

---

### Post by rohkap4444 on 2012-10-29
:D :D Amazing machine and amazingly picture are of this year. Thanks for encouraging me. Thanks for help you are doing. What impressed me most the quick response you are giving.
I have checked my BIOS many times but nothing helped. I read somewhere in Ubuntu forum that old BIOS does not recognize ISOLinux that is why my Laptop bios is not able to read.
I have tried each and every tool and method I came across to install a new installation but things are not happening. 

YES, he is right @pedro.nariyoshi my icons are missing but I feeling nothing bad in using 12.04LTS as everything is working fine but issues is no icons of any kind, is this problem getting worse by the day. My frustration in real sense is that I am not able to find a solution to my BIOS to boot from USB.
But as you are saying and he is saying throwing away this Laptop means throwing away chance of learning something new and great. I will tey my level best to rectify and now I have you people to help me. I hope we will conquer the fort. :D
Thanks for the help.

---

### Post by amjjawad on 2012-10-29
> **rohkap4444 said:**
> :D :D Amazing machine and amazingly picture are of this year. Thanks for encouraging me. Thanks for help you are doing. What impressed me most the quick response you are giving.
I have checked my BIOS many times but nothing helped. I read somewhere in Ubuntu forum that old BIOS does not recognize ISOLinux that is why my Laptop bios is not able to read.
I have tried each and every tool and method I came across to install a new installation but things are not happening. 

I've been around for quite sometime and I started as someone who seek help and when I found out this place is full of active and skilled people who jumps in to help you and fix your issue no matter what, I tried to be one of them and this is what I'm doing now :) I'm still learning and I need to learn much more. It is helping and learning at the same time and I do love both.

If you really want to thank me, let's fix this issue :D
I'm sure we can do something. At least, we can try ;)

Have you considered that your LiveCD or LiveUSB could be damaged? maybe it is not your BIOS.
How old is your machine exactly?

I would really appreciate if you take a picture and upload it here so that I can guide you through the steps. I won't give up now.

I know you can use Print Screen on your Keyboard while you are on BIOS so if you have a Digital Camera or a Mobile with Camera, that would be more than enough.

To upload a picture here, scroll down until you see "Attack Files" and then click "Manage Attachments". You can upload up to 5 pictures/images. 

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8046[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8047[/IMG]

Or, you can sing up here to upload your picture then post the link: [http://tinypic.com/index.php](http://tinypic.com/index.php)

Example: [http://i48.tinypic.com/xnxe1x.jpg](http://i48.tinypic.com/xnxe1x.jpg)

---

### Post by furtom on 2012-10-29
I think the situation is not as dire as you suspect. A couple of questions:

1. How did you accomplish the first install of Ubuntu?

I suspect your BIOS can indeed boot from a CD. Your system doesn't seem that old. [[COLOR="Blue"]This[/COLOR]]("http://www.sony-asia.com/product/vgn-cr24g") is it, isn't it? Try holding F8 at boot time.

2. Do you have data on this computer that you need to back up or not?

Either way, we have to get you ready for a fresh install.

3. Does the computer still have Windows on it and do you want to keep it?

These are a few of the things to consider.

---

### Post by rohkap4444 on 2012-10-29
Okay, I will take the pictures. But now I am in Pune, India. I was in Delhi, India till 27September. I came here to meet my brother and I got job here. SO my everything is in my native land's home. I will post the pics ASAP. 
And I am ready to take this challenge I have checked my .iso file, my USB on other desktop PC, they are working fine. The problem is ( I think) with my BIOS. 
I will try to find another solution to this BIOS, I will try to locate an engineer from Sony who can fix this BIOS problem or can suggest me any solution.
If you do not mind it is late nigh here and as my job is new I have to go to sleep. I will prepare my food for lunch, so have to wake up early please do not mind and we will chat later.
Good night from here and I am grateful to you for your replies and intention to help. It is great to know you. You are a great person. Please be as it is if you can. Take care. God bless you.

---

### Post by amjjawad on 2012-10-29
> **rohkap4444 said:**
> Okay, I will take the pictures. But now I am in Pune, India. I was in Delhi, India till 27September. I came here to meet my brother and I got job here. SO my everything is in my native land's home. I will post the pics ASAP. 
And I am ready to take this challenge I have checked my .iso file, my USB on other desktop PC, they are working fine. The problem is ( I think) with my BIOS. 
I will try to find another solution to this BIOS, I will try to locate an engineer from Sony who can fix this BIOS problem or can suggest me any solution.
If you do not mind it is late nigh here and as my job is new I have to go to sleep. I will prepare my food for lunch, so have to wake up early please do not mind and we will chat later.
Good night from here and I am grateful to you for your replies and intention to help. It is great to know you. You are a great person. Please be as it is if you can. Take care. God bless you.

Good night and sweet dreams. I'm subscribe to your thread so when you will come back and post, I will come back and carry on so no worries.

Take good care and hope we will manage to fix that for you ;)

---

### Post by rohkap4444 on 2012-10-29
yes I did not install the previous one, my brother did and he is out of the country and very very busy in his project.

Yes I have few of the data and fortunately it has partition so I can install where ever I can install. 

No windows as I think he install Ubuntu on different drive but he did not uninstall or format any partition so remanents of windows still there. 
But I will again search my BIOS and will upload the pictures. And let you know about the same.
Thanks for the post.

---

### Post by pedro.nariyoshi on 2012-10-29
Good night.

Hope to hear back from you soon. (;

---

### Post by rohkap4444 on 2012-10-29
@amjjawad: Thanks buddy. Take care of yourself too. Yes I do not know why apart from knowing all the bad things know after so many days I am feeling relieved and a kind of positive hope has arrived in my mind. And it says we will crack the shell and find the solution.

I am not alone in this fight now.

Thanks a lot for all your efforts

have a nice time

---

### Post by rohkap4444 on 2012-10-29
@pedro.nariyoshi

Good night dear. Thanks to you to. I will come back ASAP.
a ray of hope is in my sight and I do not want to let it go away. So I have to come back.

Take care

---

### Post by rohkap4444 on 2012-10-30
@amjjawad
My friend how are you? I hope and always wish from today that you always remain happy and good luck kiss your feet. 
I am fine, I have good news for you and others. 
My problem has been solved, I do not know this thing has been waiting for me to come in contact with you people. Today an upgrade happened and I was leaving for office. So I let my laptop on. When I came back and restart my laptop everything has come back. :guitar:
:) Amazingly everything is working. 
Thanks a lot, thanks a billion though for your help and to others also who supported me yesterday and encouraged me.
@pedro.nariyoshi thank you buddy.
I hope you all people will remain helpful to everyone comes in contact.
Take care.:P

---

### Post by amjjawad on 2012-10-30
> **rohkap4444 said:**
> @amjjawad
My friend how are you? I hope and always wish from today that you always remain happy and good luck kiss your feet. 
I am fine, I have good news for you and others. 
My problem has been solved, I do not know this thing has been waiting for me to come in contact with you people. Today an upgrade happened and I was leaving for office. So I let my laptop on. When I came back and restart my laptop everything has come back. :guitar:
:) Amazingly everything is working. 
Thanks a lot, thanks a billion though for your help and to others also who supported me yesterday and encouraged me.
@pedro.nariyoshi thank you buddy.
I hope you all people will remain helpful to everyone comes in contact.
Take care.:P

I'm fine, thanks a lot for asking :)
This is really good news, thanks for updating us and I'm really glad for you :D

I know it is working now but I still do recommend to do clean install. Anyway, don't close this thread for now, keep it as it is for few days and if everything is ok, you can mark it as SOLVED:

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]


I have done nothing special. What I really enjoy is when I throw some advises on the way of other users and help them and I enjoy even more when I feel the smile on their faces when their issues got fixed :)

I'm here if you need anything and don't forget, Lubuntu is waiting you to give it a go ;)

ALL the best!

---

### Post by pedro.nariyoshi on 2012-10-30
Nice (;

Congratulations. Hope you have a good time with your laptop (;

---

### Post by rohkap4444 on 2012-10-30
On my new Laptop I will have Lubuntu, promise. 
Okay I will remain this post open for few days and then I will mark it solved. 
I have a question, do you think matter in this thread will help somebody as there is not much we did to rectify.
Still you think to mark it as solved I have no problem.

Cheers
Rohit:)

---

### Post by Elfy on 2012-10-30
If you are happy then mark it solved.

---

### Post by amjjawad on 2012-10-30
> **Elfy said:**
> If you are happy then mark it solved.

+1

And by the way, you can always un-mark it as solved just in case you have to.

---

### Post by rohkap4444 on 2012-10-30
:) I have done the same, marked as solved

Cheers

---

### Post by amjjawad on 2012-10-30
> **rohkap4444 said:**
> :) I have done the same, marked as solved

Cheers

Thank you and have a great time :)

---

### Post by rohkap4444 on 2012-10-30
Can I ask you a question here itself?

---

### Post by amjjawad on 2012-10-30
> **rohkap4444 said:**
> Can I ask you a question here itself?

Sure if it is related to the same topic and if not, start a new thread and if it is a question for me, you can PM me but I guess you can't due to the post number :/

---

### Post by rohkap4444 on 2012-10-30
> **amjjawad said:**
> Sure if it is related to the same topic and if not, start a new thread and if it is a question for me, you can PM me but I guess you can't due to the post number :/

yes related to the same, you know on the left hand side there is a bar which has icon to show which thing is open and etc, previously it hide automatically but not now. How can I do that?

I have started a new thread please let me know the solution

---

