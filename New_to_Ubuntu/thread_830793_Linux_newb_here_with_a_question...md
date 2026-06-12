---
title: "Linux newb here with a question.."
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Tony4025 on 2008-06-16
I plan on starting out with Ubuntu for my first Linux OS. I'm currently using Windows XP, and it runs pretty well. My question is, would Ubuntu run fine and smoothe with my system's specs below? I mean would it run faster than my XP is currently running or atleast as good?

My PC's specs:
Current OS: Windows XP
CPU: Celeron 2.53ghz
System Memory: 256mb
GFX card: Radeon 9250 128mb

Also, what's up with the system requirements information for Ubuntu? Some ppl on this forum say that you can use Ubuntu with only 64mb ram and 2Gb HD space.. but then I read somewhere else that said you need 256mb ram and 4Gb HD space.., what's up with that?

---

### Post by barbedsaber on 2008-06-16
It will run fine, (you might dig into swap memory occasionally, but not nearly as often as you would have while you were running windows) There might be a problem getting the live cd to boot, and you may have to use the alternate cd. Basically, what this means, is instead of booting up, and seeing your pretty ubuntu desktop, you get a text based installer instead.
You might want to wait for someone else to confirm this though.
I have never seen a situation were ubuntu ran slower than XP, ever.

EDIT, I am not sure if that graphics card will play nice, it may, but I have no experience with ati cards.

---

### Post by the_doc on 2008-06-16
The bare minimum spec for running Ubuntu (Hardy Heron) is:

300 MHz x86 processor 
64 MB of system memory (RAM) 
At least 4 GB of disk space (for full installation and swap space) 
VGA graphics card capable of 640x480 resolution 
CD-ROM drive or network card

And the recommended minimum spec is (Hardy Heron):

700 MHz x86 processor 
384 MB of system memory (RAM) 
8 GB of disk space 
Graphics card capable of 1024x768 resolution 
Sound card 
A network or Internet connection


It should run fine on your system, but the RAM will obviously be a bottleneck.

EDIT:

It should run faster than XP!

---

### Post by PriceChild on 2008-06-16
You haven't enough ram to use the full graphical installed in a live environment, but you can still use the graphical installer if you choose the second option when the computer boots from the desktop cd.

You could also use the alternate cd to install ubuntu which will run fine.

I 'believe' your graphics card shouldn't give you too any troubles with ubuntu.

---

### Post by barbedsaber on 2008-06-16
May I suggest that you upgrade your RAM to 512MB, its not that expensive (well, compared to just about any other PC upgrade) and it would definitely be worth it. It will still run with 256MB, but it will definitely be more fun with at least 512MB.

---

### Post by Tony4025 on 2008-06-16
> **the_doc said:**
> The bare minimum spec for running Ubuntu (Hardy Heron) is:

300 MHz x86 processor 
64 MB of system memory (RAM) 
At least 4 GB of disk space (for full installation and swap space) 
VGA graphics card capable of 640x480 resolution 
CD-ROM drive or network card

And the recommended minimum spec is (Hardy Heron):

700 MHz x86 processor 
384 MB of system memory (RAM) 
8 GB of disk space 
Graphics card capable of 1024x768 resolution 
Sound card 
A network or Internet connection


It should run fine on your system, but the RAM will obviously be a bottleneck.

EDIT:

It should run faster than XP!

You just posted the same info that I found on various websites.. Someone on this forum said that ubuntu only needs 2gb HD space.

Also, how is Ubuntu faster than XP if it requires 2-3x as much RAM?? please tell me how.. Windows XP's minimum requirements are 1.5gb HD space, 64mb RAM, 233mhz CPU. 

So please, tell me how is XP supposed to be slower than Ubuntu? Because based on these statistics, you ppl are all wrong.. You just sound like another linux-biased fanboy.

> May I suggest that you upgrade your RAM to 512MB, its not that expensive (well, compared to just about any other PC upgrade) and it would definitely be worth it. It will still run with 256MB, but it will definitely be more fun with at least 512MB.
I really hate it when I post a thread on a computer forum asking for help and someone tells me to upgrade my hardware.. as if I don't know about that information. It's no use to me, and everyone already knows that buying better hardware would be helpful..

---

### Post by the_doc on 2008-06-16
Yes, I posted the minumiun specs found on the site because they are the official specs quoted from the developers and I'm guessing they should know.

Yes, you may hear people running it on less, but it won't run well.

EDIT:

You may not need to upgrade your RAM if you use a lighter windows manager like Fluxbox etc.

And I bet the minimum specs posted for XP would result in a really unusable PC.

---

### Post by barbedsaber on 2008-06-16
The reason Ubuntu is faster than XP, is Ubuntu was coded by more people, and they were able to find more bugs and memory leaks, so that it would be more efficient on system resources. I did not tell you to upgrade your hardware, I suggested that ubuntu would be more fun if you did. (I know its a fine line, but still...)
> **the_doc said:**
> 

And I bet the minimum specs posted for XP would result in a really unusable PC.

that is too true, the min Ubuntu specs, will leave you with a slightly sluggish computer, but the min XP specs will leave you with a computer that takes 20 minuets to boot up.

---

### Post by issih on 2008-06-16
Theres a difference between minimum spec and recommended spec....

That said the only major difference between xp and ubuntu's absolute bare minimum specs are that ubuntu needs more hard disk space, this is utterly unsurprising as it comes with a great deal more software included once installed. xp certainly doesn't come with office software included in the install.

Part of the problem here is that the term 'Ubuntu' can be used to refer to a range of things. Windows xp, however, is what it is. Ubuntu, being highly modular, can swap out different parts of the system for lighter, more optimal ones, typically at the expense of bells and whistles or eye candy. Therefore the exact specs needed to run the system can vary quite a lot dependant on how much tweaking you are willing to do.

Ubuntu as it comes on the cd will probably run fine on your hardware, although you may have trouble running from the live cd as suggested before. You may, however, want to look at xubuntu which is an official version that uses lighter components, and is therefore suited to older hardware.

Hope that helps

---

### Post by hyper_ch on 2008-06-16
Use a descriptive thread title that refelcts the content of your inquiry and not a generic "noob here" or "need help"

---

### Post by barbedsaber on 2008-06-16
> **issih said:**
> Theres a difference between minimum spec and recommended spec....

That said the only major difference between xp and ubuntu's absolute bare minimum specs are that ubuntu needs more hard disk space, this is utterly unsurprising as it comes with a great deal more software included once installed. xp certainly doesn't come with office software included in the install.

Part of the problem here is that the term 'Ubuntu' can be used to refer to a range of things. Windows xp, however, is what it is. Ubuntu, being highly modular, can swap out different parts of the system for lighter, more optimal ones, typically at the expense of bells and whistles or eye candy. Therefore the exact specs needed to run the system can vary quite a lot dependant on how much tweaking you are willing to do.

Ubuntu as it comes on the cd will probably run fine on your hardware, although you may have trouble running from the live cd as suggested before. You may, however, want to look at xubuntu which is an official version that uses lighter components, and is therefore suited to older hardware.

Hope that helps

someone give this man a medal.

---

### Post by the_doc on 2008-06-16
> **issih said:**
> 
That said the only major difference between xp and ubuntu's absolute bare minimum specs are that ubuntu needs more hard disk space, this is utterly unsurprising as it comes with a great deal more software included once installed. xp certainly doesn't come with office software included in the install.


That's a good point!

---

### Post by Tony4025 on 2008-06-16
> Theres a difference between minimum spec and recommended spec....
LMAO what's with the "...." at the end of your sentence? You seriously think I don't know the difference?

The recommended requirements for XP is still LOWER than the recommended requirements for Ubuntu you moron.. I thought you would be smart enough to figure that out.. but I guess I do have to point that out.. so here goes..

Recommended for Ubuntu:
700mhz CPU
384mb RAM
8gb HD space

Recommended for XP:
300mhz CPU
128mb RAM
1.5mb HD space

So I'm gonna ask you again.. how is Ubuntu faster if it needs 2-3x more RAM and CPU? please tell me..

Linux is crap compared to Windows XP in speed, compatibility, and ease-of-use. The only reason I'm trying out Linux, is because I'm curious.

I've been running Windows XP fine with my system specs, I never get any hangs, or lagginess except when playing a high-end PC game. But you ppl are saying that I have to upgrade my RAM to run Ubuntu smoothly.. so that there there is like admitting that XP is faster...

---

### Post by barbedsaber on 2008-06-16
If you are going to be rude obnoxious, and ignore our attempts to help you, then I really can't be bothered.

---

### Post by ChameleonDave on 2008-06-16
> **Tony4025 said:**
> 

Also, how is Ubuntu faster than XP if it requires 2-3x as much RAM?? 

How is 64MB "2-3x" as much as 64MB?

---

### Post by the_doc on 2008-06-16
People are trying to help, don't be childish and rude.

No one said you had to upgrade to run Ubuntu, rather that upgrading would make it run faster.

Build a PC with the minimum specs for XP and post back about you terrific experience.

---

### Post by rraj.be on 2008-06-16
> **Tony4025 said:**
> 
Recommended for Ubuntu:
700mhz CPU
384mb RAM
8gb HD space

Recommended for XP:
300mhz CPU
128mb RAM
1.5mb HD space

.

Had you ever installed ubuntu in your PC


I bet you it wont take more than 5 GiB space for instalation.

[At the most]

```

    *

      300 MHz x86 processor
    *

      64 MB of system memory (RAM)
    *

      At least 4 GB of disk space (for full installation and swap space)
    *

      VGA graphics card capable of 640x480 resolution
    *

      CD-ROM drive or network card

```

you can get this at 

[[COLOR="Blue"]https://help.ubuntu.com/community/Installation/SystemRequirements[/COLOR]]("https://help.ubuntu.com/community/Installation/SystemRequirements")

You are tellin 1.5GiB is enough for xp.

But you cant install just sp2 in that memory.

After installing sp2 your memory will be 3.5GiB.

You cant install even audio driver in XP without sp.

but for ubuntu there is no need for audoi driver itself.

When you install allother drivers along with sp it will become a space of 4.5-5 GiB.

Dont be rude.

If you cant help just leave others who are helping.

If you love Xp  then for that just keep loving and dont disturb others who are helping the begineers.

---

### Post by Tony4025 on 2008-06-16
> How is 64MB "2-3x" as much as 64MB?
read this official info on ubuntu. The requirements are stated at the bottom. 256mb for the alternate CD installation, and 384mb for the Live CD installer
[http://www.ubuntu.com/products/whatisubuntu/desktopedition](http://www.ubuntu.com/products/whatisubuntu/desktopedition)

It's not 64mb minimum for ubuntu.. please don't reply to my thread anymore k?

> I bet you it wont take more than 5 GiB space for instalation.
lol.. wow dude.. 5gb is still 2-3x greater than 1.5gb(XP). And the RAM/CPU recommended requirements are still 2-3x greater, so explain that. You tried to justify the HD space, that's great.. but you completely ignored the RAM & CPU information. So please don't reply to my thread unless you can completely explain your side ok?

---

### Post by ChameleonDave on 2008-06-16
> **Tony4025 said:**
> 
Recommended for Ubuntu:
700mhz CPU
384mb RAM
8gb HD space

Recommended for XP:
300mhz CPU
128mb RAM
1.5mb HD space


Anyone can recommend anything.  I hereby recommend ten times that for XP.  There you go: XP's recommendations exceed those of Ubuntu.

The fact is that Ubuntu can run on very little RAM with a slow processor, particularly if you use a streamlined environment such as Xfce or Fluxbox.  Ubuntu can also actually run with *no* hard disk space, unlike XP.  It also comes with a large amount of full-featured software, unlike XP.  If you don't need all that software, then install something like Puppy Linux instead.  There is really no need to use XP for anything but compatibility with legacy apps, etc.

---

### Post by rraj.be on 2008-06-16
Haven't you see this in the microsoft page

```
Additional Items or Services Required to Use Certain Windows XP Features
&#8226;	

For Internet access:
&#8226;	

Some Internet functionality may require Internet access, a Microsoft .NET Passport account, and payment of a separate fee to a service provider; local and/or long-distance telephone toll charges may apply
&#8226;	

14.4 kilobits per second (Kbps) or higher-speed modem
&#8226;	

For networking:
&#8226;	

Network adapter appropriate for the type of local-area, wide-area, wireless, or home network you wish to connect to, and access to an appropriate network infrastructure; access to third-party networks may require additional charges
&#8226;	

For instant messaging, voice and videoconferencing, and application sharing, both parties need:
&#8226;	

Microsoft .NET Passport account and Internet access or Microsoft Exchange 2000 Server instant messaging account and network access (some configurations may require download of additional components)
&#8226;	

For voice and videoconferencing, both parties also need:
&#8226;	

33.6 Kbps or higher-speed modem, or a network connection
&#8226;	

Microphone and sound card with speakers or headset
&#8226;	

For videoconferencing, both parties also need:
&#8226;	

Video conferencing camera
&#8226;	

Windows XP
&#8226;	

For application sharing, both parties also need:
&#8226;	

33.6 Kbps or higher-speed modem, or a network connection
&#8226;	

Windows XP
&#8226;	

For remote assistance:
&#8226;	

Both parties must be running Windows XP and be connected by a network
&#8226;	

For remote desktop:
&#8226;	

A Windows 95 or later&#8211;based computer, and the two machines must be connected by a network
&#8226;	

For sound:
&#8226;	

Sound card and speakers or headphones
&#8226;	

For DVD video playback:
&#8226;	

DVD drive and DVD decoder card or DVD decoder software
&#8226;	

8 MB of video RAM
&#8226;	

For Windows Movie Maker:
&#8226;	

Video capture feature requires appropriate digital or analog video capture device
&#8226;	

400 MHz or higher processor for digital video camera capture

* Actual requirements will vary based on your system configuration and the applications and features you choose to install. Additional available hard disk space may be required if you are installing over a network.
```

At  here

[[COLOR="Blue"]http://www.microsoft.com/windowsxp/pro/evaluation/sysreqs.mspx[/COLOR]]("http://www.microsoft.com/windowsxp/pro/evaluation/sysreqs.mspx")



Can you program any language without installing anything in your Xp.

Can you just play a sound without installing driver.

---

### Post by ChameleonDave on 2008-06-16
> **Tony4025 said:**
> WTF?? are u an idiot? read this official info on ubuntu. The requirements are stated at the bottom. 256mb for the alternate CD installation, and 384mb for the Live CD installer
[http://www.ubuntu.com/products/whatisubuntu/desktopedition](http://www.ubuntu.com/products/whatisubuntu/desktopedition)

It's not 64mb minimum for ubuntu.. please don't reply to my thread anymore k?


I was going by the stats posted in this thread that mentioned 64MB as the minimum for running both systems.  If you have a better source, then that's fine, but there is nothing stupid about me using the stats I was given and noting that they were the same.

---

### Post by the_doc on 2008-06-16
[B]Low-spec computers (Xubuntu)

If you have an old or low-spec computer, using a lightweight desktop system such as Xubuntu is recommended, as it should make more efficient use of your system's resources. 

If your system has less than 192 MB of system memory, use the Alternate Installation CD. 

Note: If you have a low-specification computer, certain features may be automatically turned off to conserve system resources. For example, if you have a graphics card with only a small amount of video memory (VRAM), the boot-up screen may not be shown. 

Follow this link for detailed instructions: Installation/LowMemorySystems. 
Minimum requirements

166 MHz processor 

64 MB of system memory (RAM) 

At least 1.5 GB of disk space 

VGA graphics card[/B]


There you go stop complaining.

---

### Post by rraj.be on 2008-06-16
> **Tony4025 said:**
> 
lol.. wow dude.. 5gb is still 2-3x greater than 1.5gb(XP)

I said at the most

But windows need 4.5-5 GiB at LEAST.

Can you install xp with in 4.5 GiB with Service pack and all your essential drivers.

```
I should report if you use word's like IDIOT any more.
```

Respect People.

Ubuntu --> [COLOR="Blue"]Humanity[/COLOR] for other's.

---

### Post by Tony4025 on 2008-06-16
> Low-spec computers (Xubuntu)

If you have an old or low-spec computer, using a lightweight desktop system such as Xubuntu is recommended, as it should make more efficient use of your system's resources. 

If your system has less than 192 MB of system memory, use the Alternate Installation CD. 

Note: If you have a low-specification computer, certain features may be automatically turned off to conserve system resources. For example, if you have a graphics card with only a small amount of video memory (VRAM), the boot-up screen may not be shown. 

Follow this link for detailed instructions: Installation/LowMemorySystems. 
Minimum requirements

166 MHz processor 

64 MB of system memory (RAM) 

At least 1.5 GB of disk space 

VGA graphics card
lol? that information is for xubuntu.. not the normal ubuntu. My argument about XP being faster than NORMAL ubuntu is still right. I never said **** about xubuntu, so wtf do u mean "stop complaining"?.. maybe you should figure out what the thread is about before u come here posting stats about a different Linux OS you moron.

---

### Post by Troll_the_Great on 2008-06-16
Look man, if you are happy with your XP, then keep it.Don't install Linux.Nobody said you should do it.Don't bother us anymore, and don't use a rude language.People here are just trying to help and they are not paid to do it.SO KEEP YOUR XP AND LEAVE US ALONE!!!

PS:Xubuntu is not a different Linux OS, is just Ubuntu with another display manager MORON, so if you don't know something don't comment.

---

### Post by the_doc on 2008-06-16
I thought the thread was trying to make the most efficient use of the hardware you'd got.  Your spec will run Ubuntu, but it would be better with Xubuntu.

And Xubuntu is Ubuntu with a different window manager, not a different OS you moron.

---

### Post by LaRoza on 2008-06-16
Thread closed.

@OP You have received the information you requested. As for why XP is faster than Ubuntu (which it is, by default) it has to do with history. XP is about 7 years old. Also, XP comes with minimal software, whereas Ubuntu comes with a lot more.

---

