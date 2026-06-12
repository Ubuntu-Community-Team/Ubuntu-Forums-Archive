---
title: "Kernel requires a x86-64 CPU, but only detected an i686 CPU"
date: 2016-05-30
forum: New to Ubuntu
---

### Post by pablitome.com on 2016-05-30
Hello,

I am totally new to ubuntu but want to give it a whirl. I downloaded the latest version and have tried to install it on an old Toshiba laptop to see how it fares. Unfortunately I got this message..

[COLOR=#000000][FONT=Roboto][h=1]Kernel requires a x86-64 CPU, but only detected an i686 CPU[/h]



[/FONT][/COLOR]
I figure this means that it will not install as it is a 64 bit install and I only have a 32 bit system. I have seen old posts and there was a link to a 32 bit Ubuntu install but the link did not work as I guess the pages have moved since the post was made over a year ago.

I have no idea what the latest version 32 bit Unbuntu is or where I can find the ISO image. If anyone does know then please help me as most posts I have seen about this problem are about 5 years old.

Thanks,
Pablo

---

### Post by him610 on 2016-05-30
Hello pablitome.com, and welcome to Ubuntu forums. 

You did not specify, but it looks like you probably have the 64bit version of Ubuntu. Go to this page...
[http://www.ubuntu.com/download/alternative-downloads]("http://www.ubuntu.com/download/alternative-downloads")

You will find links to download both 64bit and 32bit versions of Ubuntu.

---

### Post by DuckHook on 2016-05-31
Another welcome pablitom.com

If your Toshiba cannot even install a 64-bit OS, then I doubt you will be happy with Ubuntu even in 32-bit architecture. For machines that old, you may be better installing the lighter flavours, Lubuntu, Xubuntu or Ubuntu-mate. Lubuntu is the lightest. Try them out as a LiveDVD session first. Install only if they run. I would have said LiveUSB, but some old machines will not boot from USB.

Downloads sites follow:

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)
[https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/)

Torrent if you can. They yield more reliable downloads.

---

### Post by kurt18947 on 2016-05-31
I've run into video problems with Lubuntu on an old machine, wouldn't boot reliably to a usable session. Xubuntu was more reliable but somewhat sluggish. What has proven most usable on this one machine was AntiX MX15. It's not a *buntu flavor but aside from the not-so-attractive XFCE desktop I've found it a good alternative for old marginal machines.

[http://antix.mepis.org/index.php?title=Main_Page#Downloads](http://antix.mepis.org/index.php?title=Main_Page#Downloads)

---

### Post by pablitome.com on 2016-05-31
Thank you [DuckHook]("http://ubuntuforums.org/member.php?u=1256508"), [kurt18947]("http://ubuntuforums.org/member.php?u=1447222") and [him610]("http://ubuntuforums.org/member.php?u=248298") for the really helpful replies. I might just give all three versions a try one by one just to see what works best for me and see the difference.

Thanks again,
Pablo

---

### Post by X-RED_Tech on 2016-06-01
Yes, that's the point. You can and should try as many distros/flavors as you want in live sessions and then install what works best for you and your hardware. 
That said. I partially disagree with DuckHook. The statement > [COLOR=#000000]If your Toshiba cannot even install a 64-bit OS, then I doubt you will be happy with Ubuntu even in 32-bit architecture[/COLOR] is generally true but has lots of exceptions. As an example, many decade old high-end 32-bit dual-core CPU notebooks with 1,5-2GB RAM still work fine with standard 32-bit Ubuntu (actually better then some current entry-level Atom and AMD cheap notebooks.

---

### Post by mastablasta on 2016-06-02
> **X-RED_Tech said:**
>  As an example, many decade old high-end 32-bit dual-core CPU notebooks with 1,5-2GB RAM still work fine with standard 32-bit Ubuntu (actually better then some current entry-level Atom and AMD cheap notebooks.depends on  the GPU and it's support. in general though it is still bette rot use a non 3D DE or to turn off the 3D acceleration on the de (e.g. on KDE4)

---

### Post by X-RED_Tech on 2016-06-02
> **mastablasta said:**
> depends on  the GPU and it's support.

Of course. Most have discrete Nvidia graphics, top notch at the time, but even the ones with integrated Intel still perform remarkably well considering the age.
The problem with 32-bit today is the limited software available. Recently Google Chrome added itself to the list of 64-bit only app.

The point being we shouldn't dismiss or jump to conclusion about the OP's hardware without knowing it and based solely on its age.
I prefer to lower newbies' expectations ONLY when and where we really need to.

---

### Post by mörgæs on 2016-06-03
> **X-RED_Tech said:**
> 
The problem with 32-bit today is the limited software available. Recently Google Chrome added itself to the list of 64-bit only app.

I am not aware of any list, in fact I have not heard of any other software than Chrome which has abandoned 32 bit.

Please don't spread these rumours as they might contribute to the notion that 32 bit is hopeless.

---

### Post by X-RED_Tech on 2016-06-03
By all means I was trying to defend 32-bit :D
Besides you took the "list" literally when it was just an expression. I'm not aware of the existence of such systematic list either. However, the fact remains that many software has 64-bit versions only (Viber, etc.) and such "list" will most likely grow in the near future... True, there are also 32-bit software only but those run in a 64-bit OS, not the other way around, so... Not hopeless - and certainly many 32-bit hardware is still perfectly capable today - but becoming less useful by the day.

---

### Post by mastablasta on 2016-06-03
many relatively new Atoms are 32bit only. i am not sure if any new PCU's are 64 bit but still 32 bit applicaitons are maintained as not everyone switches to a new PC every 5 years. i think all the things in software center will have both 32bit and 64 bit versions. still eventually 32bit will die out. slowly. just like 16 bit has. although there is still this old app database we have at work that runs in DOS. it's an old database. sometimes people want to repair their 15 or 20 year old appliance and that database helps identify the part. why people are so attached to old household appliances is difficult to tell.

edit: chromium on which chrome is based is still available in 32 bit (for now).

---

### Post by mörgæs on 2016-06-06
> **X-RED_Tech said:**
> the fact remains that many software has 64-bit versions only (Viber, etc.)

I wouldn't call it a fact and I wouldn't call it many. Now we have two examples.

---

### Post by mörgæs on 2016-06-06
> **mastablasta said:**
> 
chromium on which chrome is based is still available in 32 bit (for now).

And it probably will be for many years to come. As it is open source everybody can compile a 32 bit version.

---

