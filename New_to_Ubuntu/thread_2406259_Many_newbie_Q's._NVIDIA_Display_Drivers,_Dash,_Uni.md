---
title: "Many newbie Q's. NVIDIA Display Drivers, Dash, Unity bugs, general use"
date: 2018-11-18
forum: New to Ubuntu
---

### Post by spazz2 on 2018-11-18
Hi All !
I'm a new Ubuntu user , and am liking it. 


I am running Ubuntu Studio 18.04
I have a few newbie Q's (or lots?).
Maybe I should put them in individual forum posts?


Thanks in advance for any and all replies.
======================================
-- Reading through the manual, I see that there is a function called "Dash". 
I cannot find a way to use this !!
 It seems like a similar interface and function to mac's "spotlight" , a function which I love. 


Dash seems to be absent from my OS. 
The unity desktop, which dash it is a part of, also seems to be absent. 
I seem to have the XFCE desktop and panel, which I like very much, and probably don't need unity,
although it might be nice to be able to install unity to see if I like it, if I can uninstall it?


That said, I really just want the Dash feature only. 
I probably don't need the launcher or anything else about unity , per se.
======================================

I have attempted the following in terminal in an attempt to get unity, and bugged up my system.
[https://itsfoss.com/how-to-fix-no-unity-no-launcher-no-dash-in-ubuntu-12-10-quick-tip/]("https://itsfoss.com/how-to-fix-no-unity-no-launcher-no-dash-in-ubuntu-12-10-quick-tip/")

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
sudo shutdown -r now


This seems to have had MANY bad effects, and has made my system buggy. 


I have attempted to both uninstall and purge :
sudo apt-get purge ubuntu-desktop



no luck ! 
I now get error messages  when I restart ubuntu, relating to my display. The following :


DisplayCAL Profile Loader 3.5
(my monitor model) (resolution x resolution) : Display profile couldn't be loaded.

Also failed unity processes seem to continue running, such as during login time, the screen is different to how it was before.


How can I undo what I have done?


This even seems to have affected my chromium extensions somehow. 
I don't see how, but suddenly after doing this, various of my chromium extensions are failing.
Maybe just coincidence.
The two things seemed to coincide exactly together.
======================================
How to install the proprietary NVIDIA drivers ? 
I've got the .run file from the Nvidia website : 


But when I run it , I get a terminal window with following message.
ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see    
         the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at      
         [www.nvidia.com]("http://www.nvidia.com/").


I attempted :
sudo service lightdm stop
but this just shut my entire system / monitor off, and I had to do a hard-restart of computer.


I have x11vnc installed. 
Could this be causing conflict?
======================================
-- The "application select button" (similar to the windows menu icon) does not have a shortcut. 
This application menu in ubuntu seems to be a program called "whisker". 
How can I set a keyboard shortcut for "whisker" to launch it ? 
======================================
Is there a folder for applications ?
Where I can sort and organise my applications by type etc.
======================================
-- Lastly, and least significantly :
I signed up to these forums as "Spazz", but it's made it "Spazz2".
How can I eliminate the number?
======================================
Thanks again !

---

### Post by oldos2er on 2018-11-18
>  Maybe I should put them in individual forum posts?

That would be the best way to do it, simpler for you and those answering you.

> I've got the .run file from the Nvidia website : Don't do that, see [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by mastablasta on 2018-11-19
also, 18.04 doesn't use Unity anymore. and you are messing up your desktop (as you noticed) by doing entering some "random" commands without knowing what they will do on version 18.04.

---

### Post by angisky on 2018-11-19
Unity is no longer being supported. The versions of Ubuntu that had it and are still supported will continue seeing updates as bug fixes and security updates but Unity is no longer on anything past 18.04. The closest thing to Unity is to get Gnome. Even the new versions of Ubuntu that ship with Gnome actually run a custom setup with a nice dock that is similar to that of Unity. Totally worth checking out. I have it installed on my main rig running 18.04 and it's really nice. Granted I've got half decent hardware. My little thinkpad x131e is also running it but this UI is a bit much even if it is still stable.

---

### Post by monkeybrain20122 on 2018-11-21
Ubuntu 18.04 doesn't use unity as default but it is easy enough to install (yes it is supported by the community)

```
sudo add-apt-repository ppa:unity7maintainers/unity7-desktop
sudo apt update
sudo apt install ubuntu-unity-desktop
sudo apt install xserver-xorg-input-synaptics

```
Choose lighdm instead of gdm as default.
reboot.

The ppa is not necessary as all packages are in the repo, but it fixes some bugs since 18.04 was released. I have a few 18.04 installations running unity, much faster and smoother than gnome shell IMO.

---

### Post by spazz2 on 2018-11-22
> **oldos2er said:**
> That would be the best way to do it, simpler for you and those answering you.

 Don't do that, see [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Thank you oldos2er !
Yes, I read back on my OP, and it is a horrible wall of text. I think I just wanted to get all my questions out while I think of them. 
Will make separate posts. 

Thank you for your advice on the driver. 
I will try and learn how to deal with binaries.

---

### Post by spazz2 on 2018-11-22
> **mastablasta said:**
> also, 18.04 doesn't use Unity anymore. and you are messing up your desktop (as you noticed) by doing entering some "random" commands without knowing what they will do on version 18.04.

Thank you mastablasta !
Yes, I think I have messed up desktop a bit. 
I didn't think it was random commands that I entered. It was the commands that I mentioned above, from the article I mentioned, which didn't seem unreasonable that it might work.
I thought Linux / Ubuntu was configurable and backwards / forwards configurable in that way : But clearly not?

Is there a way I can undo completely what I have done ? 
Like is there some kind of console history ? 
Or do I need to reinstall the whole O/S again ?

I note that in terminal, there is a history of many of the past commands I have entered, even after I have powered system on and off again.

I really only entered the commands I mentioned in my OP from the article I hyperlinked, so if there is a way for me to reverse these commands, would be easier than an entire system reinstall for what seems like a tiny thing.
Thanks anyway for your reply.

---

### Post by oldrocker99 on 2018-11-22
Ubuntu MATE has, besides a "Redmond" and "Cupertino" DEs, but "Mutiny" gives you a pretty close DE to Unity.

I do love the name.

---

### Post by spazz2 on 2018-11-24
Thank you Angisky ! 
I am glad to know that it is possible for me to install and test Unity !
(Although I think the installation procedure I have tried has given me problems).

I am mostly interested in the "dash" feature of unity, which seems to be absent from stock installation of Ubuntu Studio 18.04, as far as I can tell.
Dash looks very similar to the spotlight feature in Mac OSX, which I love.

Ideally if I could have that alongside the stock XFCE desktop which has the windows-style corner button, that would be excellent !

---

### Post by spazz2 on 2018-11-24
Thanks monkeybrain20122
This sounds like an excellent solution. I will give this a go. 

I would like to try to remove the bad-job I did trying to install unity previously, before installing over the top of it.

I think I stuffed up my system quite a bit trying to install unity -- using the method in the article I linked to. 
I then tried to remove / purge that installation to restore my system to how it was, but this did not work either. 

I now get error messages after logging into the system, and this has coincided exactly with Chromium browser behaving very strangely for some reason (Many of my extensions seem to be dead for some reason).
There were no other new variables I introduced between the time of installing unity and Chromium behaving badly (seems very strange, but that's the case).

Can anybody spot any poor decisions I made in my bash history ?
(I am a complete novice with Linux -- happy to research any answers given though) :

[FONT=georgia]sudo apt ubuntu-desktop
[/FONT][FONT=georgia]sudo apt-get update[/FONT]
[FONT=georgia]sudo apt-get install --reinstall ubuntu-desktop[/FONT]
[FONT=georgia]sudo apt-get install unity[/FONT]
[FONT=georgia]sudo shutdown -s now[/FONT]
[FONT=georgia]sudo shutdown -r now[/FONT]
[FONT=georgia]sudo apt-get remove <software-name>[/FONT]
[FONT=georgia]sudo apt-get remove unity[/FONT]
[FONT=georgia]sudo shutdown -r now[/FONT]
[FONT=georgia]sudo apt-get purge unity[/FONT]
[FONT=georgia]sudo shutdown -r now[/FONT]
[FONT=georgia]sudo apt-get install --reinstall ubuntu-desktop[/FONT]
[FONT=georgia]sudo apt-get purge ubuntu-desktop[/FONT]
[FONT=georgia]sudo apt-get install xubuntu-desktop[/FONT]
[FONT=georgia]sudo shutdown -r now

=======================
Any assistance greatly appreciated. 
Thanks ! (:[/FONT]

---

### Post by spazz2 on 2018-11-24
oldrocker ! Thank you for all those suggestions and stuff for me to consider and try out (:   Mutiny does have a nice ring to it (:

---

### Post by oldos2er on 2018-11-25
Please post the error messages you're seeing.

---

### Post by spazz2 on 2018-12-02
> **oldos2er said:**
> Please post the error messages you're seeing.

Hi oldos2er.

It has a variable boot problem.
Sometimes it boots and goes onto a large terminal screen , and it just hangs there and won't boot into ubuntu.
_**(I have taken a photo of this screen and attached this).**_

It then needs a hard reboot.
This happened 3 times in a row just when I was trying to find the error message for you.

When it boots in , I get a sort of generic error message which doesn't really provide any information.
I didn't note it down the other day, but the next time I get it, I will make note of it (though I suspect it will not be very informative).

Thank you for the help .

---

### Post by Geoffrey_Arndt on 2018-12-04
Hmm . . wow.   Methinks you're well on the road to a Linux BSOD (Black Screen of Despair) . . . from which there is "no return" (just kidding - kinda) . . 

So for what it's worth, I have a friend (longtime Windows user) in our local computer club that just installed Ubuntu Studio with default DE (xfce) - and this is what I would/will suggest to him:
 
>  For your first Linux NOOB install . . . don't make the mistake of trying to admin Ubuntu like you would a Windows or even Mac PC,
>  Setup a stable VANILLA install and don't experiment (test) with it by adding, removing excess software, themes etc. (for now),
>  Instead, set up some partitions on your drives (single drive or multiple drives or external drives (like external portable usbv3 SSD's)),
>  On those additional partitions or drives, install Ubuntu again and use those installs as your TEST environments

Then you can do all the kind of changes you've been experimenting with so far.   Remember to keep your default stable install as your PROD (production) OS.   After a few months, you'll know enough to do some safe changes to PROD using only approved repositories.   Later will come other software sources like PPA's, stand-alone deb files, etc.

IF you have any important data yet on this unstable install, best to copy off that data asap (can use the actual install media (usb-stick or dvd) for that).

Google or use youtube to research more on multiple boot systems - see known authors like Joe Collins or Average Linux User for decent and correct content.

PS . . almost forgot . . . best odds of fixing this mess is a full re-install.   That would be faster than trying many patches which have a low rate of success.

---

### Post by spazz2 on 2018-12-10
Gday Geoffrey !
The suggestion about the separate partition is awesome ! 
Why didn't I think of that ? 
The only "small" thing is : 
Does that require a full separate install of Ubuntu on the separate partition?
(I would imagine it would) 
.....or is there a way to make the test partition "speak" to the same OS partition, while only making the big changes within it's own partition?
(I suspect I'm just wishfully thinking there, and talking complete nonsense)
Obviously to install a separate OS on a separate partition just as an OS tester is a bit of a space-drain -- 
but would be worth it to save headaches like this.
(can't remember how big installed Ubuntu Studio is, but between 2 and 4 gb? )


Yes, I'm suspecting it's looking like a full clean install may be in order to be on the safe side.
*sigh* -- growing pains / learning curves.
That said, I learned about this awesome function in terminal which dumps a text list of all installed apps,
and then on a fresh install, you can just auto-reinstall applications through terminal through by using that dump-list,
which is just astoundingly cool to me.
Reinstalling programs was the main worry (and I spent a lot of time after installing ubuntu just installing tons of interesting looking things thru software portal).


I may make a separate posts in these forums on just this same issue, 
to see if anybody else has any input that is as interesting as what you've given me.
Thanks for the recommendations on Joe Collins and Avg Linux User !
I'm going to try and do some reading on Linux as I get time through the years.


Unless anybody has anything to add to this thread,
I think I will start separate threads on all  my questions at this point, as I think my initial post was a bit convoluted !!


Thank you all for your input and clues !

---

