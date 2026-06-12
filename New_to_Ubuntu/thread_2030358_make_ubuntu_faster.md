---
title: "make ubuntu faster"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by sutibun on 2012-07-20
Hi.
There is any way to make ubuntu 12.04 need less resources from my cpu?
2 Problem. I installed preload and i cant run it..i cant find it on dash board and when i try to open it with  the terminal it says ```
** (process:8774): ERROR **: cannot open /var/log/preload.log: Permission denied
&#928;&#945;&#947;&#943;&#948;&#945; Trace/breakpoint (core dumped)

```
&#928;&#945;&#947;&#943;&#948;&#945;=Trap (i think is the correct term, i am greek sorry)

Regards

---

### Post by NikTh on 2012-07-20
Hello , 
preload its not a graphical tool , so you cannot find it from dash and no Launcher exists. 

Preload its an automatic tool , record programs that you use often and makes them start (open) faster. 
I think the error message is about permissions, try to open pleload.log with "sudo"
```
sudo cat /var/log/preload.log
```If you want to customize preload,  you must open the configuration file 
e.g 
```
gksudo gedit /etc/preload.conf
```What is the problem about Cpu recourses ? 

> **sutibun said:**
> Hi.
  i am greek 


Check out my signature about GR Ubuntu Forums. ;)

Thanks

---

### Post by Bucky Ball on 2012-07-20
You could try a lighter desktop, like Xfce, or a lighter OS, like Xubuntu or Lubuntu. Ubuntu is nowadays fairly bloated by nature and likes the resources. 

Preload takes awhile to pick up your computing habits before it knows what programs/apps you are likely to use and loads them into RAM at boot, so see if there is any difference after a week or so (and remember, you need to reboot).

PS: Preload won't cut resources use at all. It is designed so the apps you use most are loaded into RAM at boot so when you launch them there is no wait. It is about speeding things up so you have that bit right. Resources? No, in fact it uses part of your RAM straight away at boot so in a way you could consider it uses more resources (you may never actually use the app loaded into RAM in that session so waste of space). I never use it. Just have the fat trimmed off in the first place (minimal Xfce install). ;)

---

### Post by sutibun on 2012-07-20
> **NikTh said:**
> 
```
sudo cat /var/log/preload.log
```
```
gksudo gedit /etc/preload.conf
```


Hi again my friend. Both code's worked thank you.
> **NikTh said:**
> preload its not a graphical tool , so you cannot find it from dash and no Launcher exists.
Sorry i dint knew that i am noob in ubuntu. :)

> **NikTh said:**
> What is the problem about Cpu recourses ?

I have an old laptop but ubuntu 12.04 runs good. BUT i wanna make runs a bit better if you know what i am try to say :p 

> **NikTh said:**
> Check out my signature about GR Ubuntu Forums. ;)

They have active members?

Thanks

---

### Post by sutibun on 2012-07-20
> **Bucky Ball said:**
> You could try a lighter desktop, like Xfce, or a lighter OS, like Xubuntu or Lubuntu. Ubuntu is nowadays fairly bloated by nature and likes the resources. 



Hi.
I currently using ubuntu 12.04 and really loved it! You suggest to go to Lubuntu tho? What is the difference?

Thanks

---

### Post by dFlyer on 2012-07-20
Why not add more ram to your computer?

---

### Post by epikvision on 2012-07-20
Better yet, why not a stronger processor?

---

### Post by sutibun on 2012-07-20
> **dFlyer said:**
> Why not add more ram to your computer?

Not THAT much a ram problem. ANd my pc is a laptop and i don't wanna touch it you know...

---

### Post by madjr on 2012-07-20
some tips:

[http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/](http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/)

---

### Post by foxmulder881 on 2012-07-20
Ubuntu can seem bloated straight out of the box, yes. You can generally speed up the computer by removing anything you find you're not using or not going to use and also install and use a different desktop environment. Something a little more lighter on resources than the standard Unity and GNOME Shell.

---

### Post by sutibun on 2012-07-20
> **madjr said:**
> some tips:

[http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/](http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/)

You can recommend any Lighter Desktop Environment? Its recommended to do that?

---

### Post by foxmulder881 on 2012-07-20
Ubuntu as a whole is not the problem, just the desktop environment it chooses. Once a different environment is installed, it's great!

---

### Post by NikTh on 2012-07-20
> **sutibun said:**
> 
I have an old laptop but ubuntu 12.04 runs good. BUT i wanna make runs a bit better if you know what i am try to say :p 

Hi ,
You can try **Ubuntu-2d**. I think it will run much faster than Ubuntu(unity 3d). 
From the login-screen click the gear-like button and select "Ubuntu-2d" . 
You will lose some effects , but the speed and environment's response will increase.

> **sutibun said:**
> They have active members?
Of course we have active members.
Do not compare this Worldwide forum with a local forum.
The trump is that, when solving a problem at your native language its always easier. (IMO). 

Thanks

---

### Post by sutibun on 2012-07-20
> **foxmulder881 said:**
> Ubuntu as a whole is not the problem, just the desktop environment it chooses. Once a different environment is installed, it's great!

Thanks allot :) just did that!

> **NikTh said:**
> Hi ,
 You can try Ubuntu-2d. I think it will run much faster than Ubuntu(unity 3d). 
 From the login-screen click the gear-like button and select "Ubuntu-2d" . 
 You will lose some effects , but the speed and environment's response will increase.

Thank you :) ill try this tomorrow!

> **NikTh said:**
> Of course we have active members.
 Do not compare this Worldwide forum with a local forum.
 The trump is that, when solving a problem at your native language its always easier. (IMO).

Ill try it tomorrow as well :)

I will close this thread tomorrow if everything goes smooth

---

### Post by afixane on 2012-07-20
My tips :

1. Remove U1, and therefore, don't use it.
2. Use BleachBit, it's like CCleaner for Linux
3. Try Openbox, it's a bit "difficult", but very lightweight (My minimal Ubuntu Install + Openbox just consume 90 MB RAM!).

---

### Post by sutibun on 2012-07-20
hello!

> **afixane said:**
> My tips :

1. Remove U1, and therefore, don't use it.



i dint get that.

thanks

---

### Post by mardybear on 2012-07-21
> **afixane said:**
> My tips :

1. Remove U1, and therefore, don't use it.
2. Use BleachBit, it's like CCleaner for Linux
3. Try Openbox, it's a bit "difficult", but very lightweight (My minimal Ubuntu Install + Openbox just consume 90 MB RAM!).

Agreed. I'm running Ubuntu 10.04 (lucid) on a 700MHz/256MB ram system quite well. Continue to tweak/lean your system as you learn. Don't get in the habit of reinstalling every time something goes wrong - learn how to fix it. I would also avoid installing a new flavour of the month just to see if the distriution is a bit faster - just install Ubuntu and tweak.

Definitely a bleachbit fan and i prefer to reboot after cleaning the system. Openbox is the leanest window manager around - learn how to use it. It's geek and actually quite simple once you get used to modifying configuration files. Openbox will probably make the biggest single improvement in your system's performance.

Hope this helps,

mardybear

---

### Post by TenPlus1 on 2012-07-21
Install Lubuntu which uses the LXDE desktop (OpenBox and tools) instead of Gnome/Unity and is a LOT lighter and faster to use...

Turn off unneeded services in Startup Applications (be careful what you turn off)

Add this line "vm.swappiness = 10" at the end of /etc/sysctl.conf (without quotes)

---

### Post by NikTh on 2012-07-21
> **TenPlus1 said:**
> Install Lubuntu which uses the LXDE desktop (OpenBox and tools) instead of Gnome/Unity and is a LOT lighter and faster to use...

A "correction" here.. Lubuntu its not just faster... Its a **[SIZE=3][COLOR=Black]Rocket [/COLOR][/SIZE][SIZE=3]!![/SIZE]**

:D

---

### Post by Bucky Ball on 2012-07-21
> **NikTh said:**
> A "correction" here.. Lubuntu its not just faster... Its a **[SIZE=3][COLOR=Black]Rocket [/COLOR][/SIZE][SIZE=3]!![/SIZE]**

:D

Correct.

To try Xfce, the desktop environment used in Xubuntu, install 'xfce4', log out, choose 'Xfce Session' from 'Sessions' pop-up, log in. Do the same to get back to Unity or whatever other DE you want to use.

You can develop all sorts of hybrids (Xubuntu with Unity, Ubuntu with Openbox). I agree it is about the desktop environment speeding things up, but it's not just that. 

For instance, an Xubuntu install is smaller and contains more lightweight apps, Lubuntu install is smaller again. The Ubuntu *core* is the same throughout the Ubuntu family, but the packages that come with the flavour are not. Therefore, some are faster than others (lightweight and less stuff plopped on the core). Try Kubuntu. It has Ubuntu core but the most bloated and resource hungry of them all because of apps, not Ubuntu core. An old machine running Lubuntu happily will die with KDE; same kernel used by both. ;)

You can use more lightweight apps also. Pcmanfm (default file manager in Lubuntu) instead of Nautilus and Iron instead of Firefox are a couple of examples. Look for lightweight alternatives to what you are using in the stock 'Ubuntu' install and try 'em out. Another good suggestion: What do you really use? Kill the rest. Another reason to try a minimal install when you're game enough to try it. That way, you only install what you really need right from the start (including DE). Now, that is lightning fast!!! (Desktop in 12 seconds.)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It can take a bit of tweaking but it's a good learning curve and definitely worth it if it's speed you're after (as long as you don't then install 'ubuntu-desktop'!).  

To the OP: You can't close the thread but you can mark it as solved from 'Thread Tools.'

---

### Post by andrew.46 on 2012-07-21
> **sutibun said:**
> You can recommend any Lighter Desktop Environment?

Fluxbox is a window manager rather than a Desktop Environment but well worth a look. Needs a little time to set up though....

---

### Post by Wirephire on 2012-07-21
*@sutibun**,* could you post your machine specifications?

If its coming to lighter desktop environment, +1 for LXDE and [Lubuntu]("http://lubuntu.net/"). Its pretty good for slower computers.


*~wph*

---

### Post by sutibun on 2012-07-21
Hello!


> **mardybear said:**
> Agreed. I'm running Ubuntu 10.04 (lucid) on a 700MHz/256MB ram system quite well. Continue to tweak/lean your system as you learn. Don't get in the habit of reinstalling every time something goes wrong - learn how to fix it. I would also avoid installing a new flavour of the month just to see if the distriution is a bit faster - just install Ubuntu and tweak.

I agree on that thats why i asked this question.

> **TenPlus1 said:**
> Install Lubuntu which uses the LXDE desktop (OpenBox and tools) instead of Gnome/Unity and is a LOT lighter and faster to use...

 Turn off unneeded services in Startup Applications (be careful what you turn off)

 Add this line "vm.swappiness = 10" at the end of /etc/sysctl.conf (without quotes)

Did everything already :)

> **Bucky Ball said:**
> Try Kubuntu. It has Ubuntu core but the most bloated and resource hungry of them all because of apps, not Ubuntu core. An old machine running Lubuntu happily will die with KDE; same kernel used by both.;)


I already installed Lubuntu too. You suggest to add kubuntu too?

Thanks.

---

### Post by sutibun on 2012-07-21
> **wirephire said:**
> *@sutibun**,* could you post your machine specifications?

If its coming to lighter desktop environment, +1 for LXDE and [Lubuntu]("http://lubuntu.net/"). Its pretty good for slower computers.


*~wph*

Yes i saw big difference since i installed Lubuntu. Now i am online with ubuntu unity 2D (i dint know that you can change that when you log in -.- ) 
and its very good!

My computer specifications? well ill give you a hint its a Celeron computer with 1GB ram (old old old old old) :D when i had windows my pc was for the trash.....

---

### Post by waynefoutz on 2012-07-21
> **sutibun said:**
> Yes i saw big difference since i installed Lubuntu. Now i am online with ubuntu unity 2D (i dint know that you can change that when you log in -.- ) 
and its very good!

My computer specifications? well ill give you a hint its a Celeron computer with 1GB ram (old old old old old) :D when i had windows my pc was for the trash.....

I have a good suggestion as well. The Enlightenment E17 window manager. You can install it on your current system and log into it. It takes a little tweaking to customize it to your liking, but once it's there, it blows everything else out of the water, in my humble opinion. it's fast, and it's pretty, with plenty of eye candy that will make that old computer feel new agan. Search for E17 in the Software Centre.

If you don't mind doing a reinstall, consider Bohdi Linux. It's an Ubuntu based distro using Elightement where they have done all the tweaking for you. 

[http://www.bodhilinux.com/]("http://www.bodhilinux.com/")

If it was me, I'd do a fresh install of Bohdi. 


It will run on a 300 megahertz 386 with 128 megs of RAM so it should fly on your system.

---

### Post by Megaptera on 2012-07-21
> **sutibun said:**
> . You suggest to add kubuntu too? Thanks.

No I don't think that's what's meant - I think it's the opposite in fact!
:P

---

### Post by sutibun on 2012-07-21
> **Megaptera said:**
> No I don't think that's what's meant - I think it's the opposite in fact!
:P

really?so no kubuntu..ok :p

---

### Post by Wirephire on 2012-07-21
> **sutibun said:**
> Yes i saw big difference since i installed Lubuntu.
I'm happy you like it. :)
[quote=sutibun]You suggest to add kubuntu too? ... Its a Celeron computer with 1GB ram ...[/quote]
Better don't, althought I find KDE to be faster then Unity3D.
If you are looking for even better performance, try some window manager, like *@andrew.46* said (for example Fluxbox).


*~wph*

---

### Post by sutibun on 2012-07-21
> **wirephire said:**
> 

Better don't,


thank you my friend i won't.but why?? :p

---

### Post by Megaptera on 2012-07-21
> **sutibun said:**
> thank you my friend i won't.but why?? :p

Because it uses more resources than Lubuntu and you were looking to cut down and not increase.
 :D

---

### Post by sutibun on 2012-07-21
> **Megaptera said:**
> Because it uses more resources than Lubuntu and you were looking to cut down and not increase.
 :D

Thank for the tip my friend :)

ill close this later :)

---

### Post by sutibun on 2012-07-21
Installed Preload OpenBox Lubuntu. Start up apps are checked.I work with Ubuntu 2D now and my CPU is doing fine for the moment. 

Thank everyone for the help i am thankful! 
I consider this thread as solved :)

---

