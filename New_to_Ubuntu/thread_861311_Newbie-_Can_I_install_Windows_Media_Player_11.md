---
title: "Newbie- Can I install Windows Media Player 11?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by cgault9 on 2008-07-16
Hey I just downloaded ubuntu today and was curious to see if I could install Windows Media Player 11. I need it so I can re-sync my Xbox 360 with my PC so I can continue to stream media from it to my basement. Any help would be appreciated, mind you I'm new to this so I may require detailed instructions if possible.-thanks

---

### Post by halitech on 2008-07-16
natively there is no way of installing WMP11 in any flavor of linux. I don't know if WINE will work or not (have my doubts) so you may have to use something like VMware or virtual box and install windows XP in it

---

### Post by jnorth on 2008-07-16
[LEFT]Not natively.  WMP10 is possible but sketchy at best from personal experience ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=3212](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3212)) and there are rumors of WMP11 ([http://ubuntuforums.org/showthread.php?t=459491](http://ubuntuforums.org/showthread.php?t=459491)), but  I see nothing definite.

Edit - I'm slow - as halitech said, vmware is a good idea if you must have it.
[/LEFT]

---

### Post by cgault9 on 2008-07-17
> **jnorth said:**
> [LEFT]Not natively.  WMP10 is possible but sketchy at best from personal experience ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=3212](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3212)) and there are rumors of WMP11 ([http://ubuntuforums.org/showthread.php?t=459491](http://ubuntuforums.org/showthread.php?t=459491)), but  I see nothing definite.

Edit - I'm slow - as halitech said, vmware is a good idea if you must have it.
[/LEFT]

no no, thanks alot, I will try the vmware idea out.. I simply want to be able to stream media to my xbox 360 through WMP11, if that is not possible please say so and save me the hassle-
thanks again all

---

### Post by mcduck on 2008-07-17
There are many other uPnP media servers available, WMP is probably the worst one available so perhaps you should try some Linux-native medis server instead?

TwonkyMedia is one of the most popular, I use MediaTomb myself.

---

### Post by nothingspecial on 2008-07-17
You don`t need wmp to stream media with Ubuntu.
Use mediatomb, search in synaptic.

ps it`s not the done thing to have 2 threads on 1 subject simultaneously. :wink:

---

### Post by cgault9 on 2008-07-17
> **nothingspecial said:**
> You don`t need wmp to stream media with Ubuntu.
Use mediatomb, search in synaptic.

ps it`s not the done thing to have 2 threads on 1 subject simultaneously. :wink:


the only problem I have with these alternatives is that I will not be able to use the SYNC feature which is necessary (Thanks to Xbox) to set up a connection between my PC and my 360. This virtualbox or VMware idea that I keep seeing in numerous places sounds interesting, simply, how would one go about doing that and run Microsoft XP in the VM? I currently have my HD partitioned and have both OS' installed so I can tinker around with ubuntu before making the full commitment, would this effect either OS negatively?

---

### Post by seagullplayer77 on 2008-07-17
Natively, there isn't any way of installing WMP on Linux. I don't think Microsoft looks too kindly upon anything other than Microsoft, so they're pretty stingy about making Linux versions of their software. People have gotten Windows Media Player to work to some extent using Wine, but I don't think you're ever going to get it to work perfectly. After all, Wine is just an emulator.

If it's the Sync feature you're looking for, then neither of these suggestions will help, but if you're looking for an interface similar to that of WMP, Songbird and aTunes (not iTunes--aTunes) are both relatively similar. Sorry I couldn't be more helpful!

---

### Post by carandraug on 2008-07-17
> **cgault9 said:**
> the only problem I have with these alternatives is that I will not be able to use the SYNC feature which is necessary (Thanks to Xbox) to set up a connection between my PC and my 360. This virtualbox or VMware idea that I keep seeing in numerous places sounds interesting, simply, how would one go about doing that and run Microsoft XP in the VM? I currently have my HD partitioned and have both OS' installed so I can tinker around with ubuntu before making the full commitment, would this effect either OS negatively?

Installing XP in VirtualBox shouldn't affect anything negatively. It's pretty much like running a very heavy program inside Linux, that program being another OS. I recommend Virtualbox as it's really intuitive and easy to use. If you need USB support in VirtualBox you won't be able to get it with the one that's in the repositories, you'll have to go to [their site]("http://www.virtualbox.org/wiki/Downloads") and download the proprietary version (not the OSE version).

I don't know much about how to stream media with your Xbox but I find it hard that no one has come up with a solution for that.
> **seagullplayer77 said:**
> After all, Wine is just an emulator.
Actually wine is a compatibility layer and stands for Wine Is Not Emulator (recursive acronyms, you gotta love them!).

---

### Post by cgault9 on 2008-07-18
this is what I downloaded...  VirtualBox-1.6.2-OSE.tar.bz2

I cannot seem to figure out how to successfully open and install the package I download, any help would be appreciated and being completely overwhelmed by this as I am, in a panic I read half of the User Manual provided to no avail, so I figured I would ask as you all are much more helpful anyways

---

### Post by SunnyRabbiera on 2008-07-18
well the tarball will not do anyhow, go here [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)
and under platform select ubuntu 8.04 for your architecture (to find out what you have check under system > administration > system monitor and under the system tab check what you have)
agree to the license and crap and then try to install the debian binary.

---

### Post by cgault9 on 2008-07-18
> **SunnyRabbiera said:**
> well the tarball will not do anyhow, go here [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)
and under platform select ubuntu 8.04 for your architecture (to find out what you have check under system > administration > system monitor and under the system tab check what you have)
agree to the license and crap and then try to install the debian binary.

thanks, i ended up going through the terminal and just entered > sudo aptitude install virtualbox-ose virtualbox-ose-modules-generic and then gave my user name permission and was able to find it in my systems tab afterall... 
however....

got it up and running but when I try and install XP my system freezes up or somehow aborts the install. I only have 1G of RAM and a flimsy 40gb dedicated to ubuntu right now and have my VirtualBox sucking up 750mb of RAM and 5 gb reserved for the XP install... am I simply not going to be able to support all of this until I alot more space for ubuntu?

---

### Post by cgault9 on 2008-07-18
> **cgault9 said:**
> thanks, i ended up going through the terminal and just entered  and then gave my user name permission and was able to find it in my systems tab afterall... 
however....

got it up and running but when I try and install XP my system freezes up or somehow aborts the install. I only have 1G of RAM and a flimsy 40gb dedicated to ubuntu right now and have my VirtualBox sucking up 750mb of RAM and 5 gb reserved for the XP install... am I simply not going to be able to support all of this until I alot more space for ubuntu?

{EDIT}
here maybe this will explain better...
[IMG]http://a.1asphost.com/cwick/cg9-wbhstpics/Virtualboxcurrentconfig.png[/IMG]

thanks again all

---

### Post by Canis familiaris on 2008-07-18
Why dont you reduce the guest memory for XP from 750 to 384 MB?

---

### Post by nothingspecial on 2008-07-18
You really don`t need windows to stream to your xbox. Have a look at these. It seems like you`re jumping through an awful lot of hoops to achieve something you can do in Ubuntu.

[http://vanvalkinburgh.org/blog/612](http://vanvalkinburgh.org/blog/612)

[http://ubuntuforums.org/showthread.php?t=794489](http://ubuntuforums.org/showthread.php?t=794489)

[http://blog.kejadlen.net/articles/2008/01/27/using-ushare-for-streaming-video-from-ubuntu-to-xbox-360](http://blog.kejadlen.net/articles/2008/01/27/using-ushare-for-streaming-video-from-ubuntu-to-xbox-360)

[http://ge.ubuntuforums.com/showthread.php?t=632428](http://ge.ubuntuforums.com/showthread.php?t=632428)

[http://badoh.com/2008/01/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/](http://badoh.com/2008/01/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/)

Try some of them if all you want to do is stream. If you really do want windows then good luck.

---

### Post by cgault9 on 2008-07-18
> **nothingspecial said:**
> You really don`t need windows to stream to your xbox. Have a look at these. It seems like you`re jumping through an awful lot of hoops to achieve something you can do in Ubuntu.

[http://vanvalkinburgh.org/blog/612](http://vanvalkinburgh.org/blog/612)

[http://ubuntuforums.org/showthread.php?t=794489](http://ubuntuforums.org/showthread.php?t=794489)

[http://blog.kejadlen.net/articles/2008/01/27/using-ushare-for-streaming-video-from-ubuntu-to-xbox-360](http://blog.kejadlen.net/articles/2008/01/27/using-ushare-for-streaming-video-from-ubuntu-to-xbox-360)

[http://ge.ubuntuforums.com/showthread.php?t=632428](http://ge.ubuntuforums.com/showthread.php?t=632428)

[http://badoh.com/2008/01/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/](http://badoh.com/2008/01/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/)

Try some of them if all you want to do is stream. If you really do want windows then good luck.

one question.. when checking out ushare i saw that it is for streaming videos, does it also stream music?

when I was installing it I came [upon this ]("http://www.geocities.com/tke_180/usharelaststep.png")

then the instructions from [here]("http://vanvalkinburgh.org/blog/612") got foggy and started talking about ffmpeg which confused me even more... 
does anyone know where I go from here?

---

### Post by cgault9 on 2008-07-18
> **Anurag_panda said:**
> Why dont you reduce the guest memory for XP from 750 to 384 MB?

I will try that... thanks

---

### Post by cgault9 on 2008-07-18
> **Anurag_panda said:**
> Why dont you reduce the guest memory for XP from 750 to 384 MB?

it worked great, but i jumped in the shower because I had a 33 min install time and when I got it the Vbox had froze and I believe the error said i did not have enough memory on the host... do I need more than 5gb for the Vbox windowsxp install?

---

### Post by SunnyRabbiera on 2008-07-18
the virtual drive will probably be more then 5GB, try a virtual size of 8GB or more if you have the space.

---

### Post by cgault9 on 2008-07-19
> **SunnyRabbiera said:**
> the virtual drive will probably be more then 5GB, try a virtual size of 8GB or more if you have the space.

so i was clearing space for my virtualdrive on my windows (as i had both ubuntu and windows bot installed on my HDD) somehow, i am not sure how, but when i was using the windows tools to clear space,  the first thing it removed (and most likely listed but i did not check for it) was ubuntu and now I am back to square one. Before I delete windows for commiting this crime, will i need a new CD key to install XP inside my virtualbox? i know it may seem like an obvious answer but i am affraid to commit to ubuntu without being able to run xp when i need too.

---

### Post by sdowney717 on 2008-07-19
If you have an XP setup CD, you must have a Product Key to install in virtualbox.

If your currently running XP, and dont know your key. Download a little utility called, Belarc Advisor
[http://www.belarc.com/free_download.html](http://www.belarc.com/free_download.html)

and it will tell you the product key.

It would be a good idea though, to make sure that your product KEY will work with your CD install for XP

---

### Post by cgault9 on 2008-07-19
> **sdowney717 said:**
> If you have an XP setup CD, you must have a Product Key to install in virtualbox.

If your currently running XP, and dont know your key. Download a little utility called, Belarc Advisor
[http://www.belarc.com/free_download.html](http://www.belarc.com/free_download.html)

and it will tell you the product key.

It would be a good idea though, to make sure that your product KEY will work with your CD install for XP

ok, thanks... i have both an XP and a reinstall cd provided by gateway with no key attached to that.. any suggestions on which to use?

---

### Post by sdowney717 on 2008-07-19
the reinstall CD will likely not work.
If you have a XP setup disc, then that will likely work. But you still need the key.

---

### Post by cgault9 on 2008-07-19
> **sdowney717 said:**
> the reinstall CD will likely not work.
If you have a XP setup disc, then that will likely work. But you still need the key.

thats no problem, i have my key and a setup disk as well.. it will just be a few days, i ordered a 250gb HDD (since my 40gb was pathetic to begin with) so this problem wont surface again. thanks for your help I will let you all know how it went in a few days i'm sure.

---

### Post by nothingspecial on 2008-07-19
> **cgault9 said:**
> so i was clearing space for my virtualdrive on my windows (as i had both ubuntu and windows bot installed on my HDD) somehow, i am not sure how, but when i was using the windows tools to clear space,  the first thing it removed (and most likely listed but i did not check for it) was ubuntu and now I am back to square one. Before I delete windows for commiting this crime, will i need a new CD key to install XP inside my virtualbox? i know it may seem like an obvious answer but i am affraid to commit to ubuntu without being able to run xp when i need too.


It seems you want to get this working with windows and it looks like you`re almost there. That`s fine. The most important thing is that you can use your stuff the way you want to use it.:)
 But once you`ve got it working (if you like) we can try and get your xbox working with nothing but Ubuntu.

BTW I`ve not got an xbox and I`ve never had windows but I love a problem.

---

### Post by cgault9 on 2008-07-19
> **cgault9 said:**
> thats no problem, i have my key and a setup disk as well.. it will just be a few days, i ordered a 250gb HDD (since my 40gb was pathetic to begin with) so this problem wont surface again. thanks for your help I will let you all know how it went in a few days i'm sure.

til then, i dunno if you all will hate me for this but, is there a way to lauch a virtualmachine inside of windows and could I run ubuntu out of it so I could still use it?

---

### Post by nothingspecial on 2008-07-19
Never done it myself but look at this.

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by cgault9 on 2008-07-20
> **nothingspecial said:**
> Never done it myself but look at this.

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)



......coming from you live from a new version of ubuntu inside of windows.
--thanks guys

---

### Post by cgault9 on 2008-07-24
so i got ubuntu up and running inside of XP, my only issue is I cannot figure out how to get my cube back.. i have all of the settings correct in the advanced desktop and ran multiple tests that were suggested to other users on the compiz forum but i still am stuck with two desktops ( i have 4 enabled), Could this be because I am running ubuntu inside a virtual box?

---

### Post by cgault9 on 2008-07-24
[here is a screenshot of my virtualbox settings ]("http://a.1asphost.com/cwick/cg9-wbhstpics/cg9vboxss.JPG")

---

### Post by RomeReactor on 2008-07-24
> **cgault9 said:**
> so i got ubuntu up and running inside of XP, my only issue is I cannot figure out how to get my cube back.. i have all of the settings correct in the advanced desktop and ran multiple tests that were suggested to other users on the compiz forum but i still am stuck with two desktops ( i have 4 enabled), Could this be because I am running ubuntu inside a virtual box?

I don't think VirtualBox provides direct access to the hardware, only emulation; so unless I'm mistaken, that means no Compiz.

---

### Post by Methuselah on 2008-07-24
> **cgault9 said:**
> so i got ubuntu up and running inside of XP, my only issue is I cannot figure out how to get my cube back.. i have all of the settings correct in the advanced desktop and ran multiple tests that were suggested to other users on the compiz forum but i still am stuck with two desktops ( i have 4 enabled), Could this be because I am running ubuntu inside a virtual box?

There will be no 3D desktop because the virtual hardware doesn't emulate a 3D card.

---

### Post by cgault9 on 2008-07-24
poop

---

### Post by flytripper on 2008-07-24
Just for the record. i dont understand what exactly you mean by (sync) but i am running music and video including hd to my 360 via twonky with no tweaking save setting the twonky server up. my 360 is on auto network settings and found the server immediately.I have no microsoft products running whatsoever.

---

### Post by nothingspecial on 2008-07-24
> **flytripper said:**
> Just for the record. i dont understand what exactly you mean by (sync) but i am running music and video including hd to my 360 via twonky with no tweaking save setting the twonky server up. my 360 is on auto network settings and found the server immediately.I have no microsoft products running whatsoever.

So, like I said before, why don`t you go for a dual boot now, and we can see if we can set it up inside ubuntu, letting you fall back on windows if you need to. Then you can have your cube.

ps I`m going away for a long weekend, so no help from me `till tuesday :)

---

### Post by ByteJuggler on 2008-07-24
Compiz/the 3D cube requires 3D acceleration.  A VM's virtual graphics card is not accelerated, so Compiz/the cube wont work.

---

### Post by inkrypted on 2008-07-24
I have an Xbox 360 and a PS3 and can stream and sync with Ubuntu just fine using this.

[http://fuppes.ulrich-voelkel.de/features/](http://fuppes.ulrich-voelkel.de/features/)

Initial set up is a little rough make sure you read the instructions and comprehend them well.

:)  Good Luck

---

