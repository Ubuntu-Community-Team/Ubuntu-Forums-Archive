---
title: "Can't install some software through Ubuntu Software Centre"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by brodedra on 2012-08-08
Hi!

I'm relatively new to Linux. As such, I had previously installed Ubuntu 11.04 and it was working well until I decided to do a fresh install of the new release - 12.04 LTS. 

Earlier, I used to use "Startup-Manager" tool but to my surprise, I am not able to download this tool via Ubuntu Software Centre or Synaptic Package Manager. This is surprising because I remember exactly downloading it in Ubuntu 11.04 using Ubuntu Software Centre.

I couldn't find "Xnoise" and "ENOME Do" either :(. I remember using it frequently under 11.04. 

Do I need to revert back to Ubuntu 11.04?

---

### Post by Zvlwab on 2012-08-08
I don't know those other tools, but I think that by ENOME Do you ment GNOME Do, which I use myself and I can confirm it is available on 12.04.

---

### Post by NikTh on 2012-08-08
Hi , 
I don't know about "Xnoise" and "ENOME do" packages . Some packages - programs , stops the support for newer versions of Ubuntu and Ubuntu is not responsible for that. Developers are. 
e.g.
Startup-manager is "dead" [on 2011-05-06]("https://launchpad.net/startup-manager") 
An alternative good application for startup-manager is Grub-customizer. 
It is not in Software-Center yet , but you can install it following below commands in terminal (ctlr+alt+t)
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update 
sudo apt-get install grub-customizer
```Thanks

---

### Post by brodedra on 2012-08-08
Sorry it's GNOME Do - my bad. Found it. 

Thanks.

---

### Post by brodedra on 2012-08-08
So it simply means that by the time you get used-to with an application, it disappears? I guess Windows is better then! 

It's like coming from 11.04 to 12.04 and the world changes.

---

### Post by NikTh on 2012-08-08
> **brodedra said:**
> So it simply means that by the time you get used-to with an application, it disappears? I guess Windows is better then! 


Hi , 
most of developers on Free Software and Open software doing a  volunteering job. They are not get paid , you or me not pay them and so  we mustn't have demands on them. They are humans and every kind of  problem can occur to prevent them for better support on their  applications. 

On the other hand, I will try to convince you that Ubuntu is a better OS  (that windows are) but I will not try to force my opinion. You are free  to choose any Operating System you want (or working better for you)
Thanks

---

### Post by wyliecoyoteuk on 2012-08-08
> **brodedra said:**
> So it simply means that by the time you get used-to with an application, it disappears? I guess Windows is better then! 

It's like coming from 11.04 to 12.04 and the world changes.

It's a bit like moving to the latest version of Windows and having to update or replace unsupported software and hardware.

My company just had to fork out over a grand to update our CRM package because we updated to Windows 7 and our version only supports XP or Vista.
At home, my printer is no longer supported by Windows7, etc.

Things come and go, but in Linux, at least it doesn't cost money to replace it.
As for the world changing, have you seen windows 8 yet?:o

---

### Post by Zvlwab on 2012-08-08
There is a repository for Xnoise:
[https://launchpad.net/~shkn/+archive/xnoise](https://launchpad.net/~shkn/+archive/xnoise)

---

### Post by brodedra on 2012-08-08
> **NikTh said:**
> Hi , 
most of developers on Free Software and Open software doing a  volunteering job. They are not get paid , you or me not pay them and so  we mustn't have demands on them. They are humans and every kind of  problem can occur to prevent them for better support on their  applications. 

On the other hand, I will try to convince you that Ubuntu is a better OS  (that windows are) but I will not try to force my opinion. You are free  to choose any Operating System you want (or working better for you)
Thanks

I can understand what you mean. The point which strikes me is the fact that if the above philosophy is in existence, then not only Ubuntu but the entire Linux, Open source and Free software philosophy is in danger. It simply suggests to the users of Linux that "We the programmers work free. We are hobbyist. We work in free time. We don't get paid. So don't ask MORE."

I mean how would you feel that the tools you usually work with or something that is really unique and productive to you vanishes! Then, you look for the new ones and this cycle continues. I know it's difficult to update or support softwares in FREE terms. However, I wish there was a way where developers could keep their valuable work even though they don't find time/money to support any further developments. This way, all the good and remarkable work in Linux will not only stay intact but will also reflect someones great work for the years to come. Perhaps, that's the reason why we are here as a community - helping, learning and sharing with each other.

Linux and especially Ubuntu is undoubtedly one of the best things that has happened to computers. But the sluggishness in some aspect is actually killing the real fun part of it. The disappeareance of the tools that I needed badly (which I was fond of using on Ubuntu 11.04) is a concept hard to gulp in any terms!

All I wish - If I had a GHOST copy of 11.04 - that had all of my best tools.

---

### Post by brodedra on 2012-08-08
Great! Thanks heaps.

---

### Post by wyliecoyoteuk on 2012-08-08
> **brodedra said:**
> 
I mean how would you feel that the tools you usually work with or something that is really unique and productive to you vanishes! Then, you look for the new ones and this cycle continues. I know it's difficult to update or support softwares in FREE terms. However, I wish there was a way where developers could keep their valuable work even though they don't find time/money to support any further developments. 

It is the same in any field. The software you are referring to didn't suddenly disappear, it stopped being supported 6 years ago, and in all that time, nobody has been interested enough to revive it.
It regularly happens in proprietary software too.
companies fail, or get taken over and their software gets dumped.
People move on, get ill or die and their software may not survive.

Windows95, 98, XP, Vista, then Win7, and now Win8.
At each step along the way, software has been dumped, some has been retained but changed beyond recognition, look at Office 2010 compared to 2000.

Anybody remember Wordperfect?

The good news is that if a project is worthwhile, it will be taken on by someone new, or a replacement project will supersede it. In fact a project often withers on the vine through lack of interest, but is is as often because somebody has produced a better implementation.

Next time you find a tool that does exactly what you want, see if you can make a donation, however small. Even just sending an email saying thank you, which is more than most people do.

---

