---
title: "desktops etc."
date: 2014-02-23
forum: New to Ubuntu
---

### Post by jayemcee3 on 2014-02-23
Hi there somebody, I had the latest version of Ubuntu put onto my computer some weeks ago & it isn't working well at all. Things like putting 4 desktops on only to find now it has decided to put 7 desktops on & heaps of other annoying things too many to put here , Is there help?? Can I get rid of this version & go back to some sort of sanity.

---

### Post by Vladlenin5000 on 2014-02-23
Hi.

Unfortunately we neither have a crystal ball nor remote vision. Without info on exactly what are complaining about I won't even dare to guess.

---

### Post by jayemcee3 on 2014-02-23
First, can you tell me where to go to find the version of Ubuntu I have please?

---

### Post by Vladlenin5000 on 2014-02-23
[https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

---

### Post by Frogs Hair on 2014-02-23
> [COLOR=#000000]Things like putting 4 desktops on only to find now it has decided to put 7 desktops on [/COLOR] Can you give a better description of what this means. Additional desktops or window managers would have to be installed manually and if you didn't install anything then there must be another explanation. The work space switcher offers 4 different work-spaces  and looks like the picture below is this what you are seeing? Please indicate what Ubuntu version is installed because there are four.  Ubuntu , Kubuntu , Xubuntu and Lubuntu.

---

### Post by jayemcee3 on 2014-02-23
Ubuntu 13.04

---

### Post by monkeybrain20122 on 2014-02-23
Do you have an amd card? It seems that this may be graphic card related. I have an installation of Ubuntu 13.10 on an external drive which I can boot off different machines. I have set 4 desktops in ccsm. However when I booted it off a lenovo T500(?) briefly it showed 6 and only two worked even though the ccsm settings still showed 4. Tried it on other machines and this didn't happen. The Lenovo has an Amd graphic card but I can't remember which one (I use the open driver obviously as this is a portable installation)

---

### Post by jayemcee3 on 2014-02-23
I have been asked by you to be more spacific, I understand that & I am doing my best to help. but in turn can I explain that I know absoutely nothing about the workings of a computer, so MonkeybrainI am sorry but that is all gobbledegoop to me....

---

### Post by monkeybrain20122 on 2014-02-23
Open a terminal and type
```
lshw -C display
```
and post the outputs

P.S Ubuntu 13.04 has reached end of life in jan, it is no longer supported so you should backup your data make a clean install of 13.10.

---

### Post by jayemcee3 on 2014-02-23
Ok... a few of the things are
My desktop files have all vanished & I have to go to 'Home Folder' which is a button on the left of the screen to access these. When there I can't even put them on the desktop from this folder.
With this forum, in the past, your answers would come up by itself, now I have to reload the browser..

```
lshw -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff ioport:ee00(size=256) memory:fdff0000-fdffffff memory:fde00000-fdefffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

Any help??

This I posted to you but I don't see it anywhere, so forgive me if you got it twice...


```
lshw -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff ioport:ee00(size=256) memory:fdff0000-fdffffff memory:fde00000-fdefffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

---

### Post by monkeybrain20122 on 2014-02-23
My hunch is that it is a graphic card problem. Your card is old (by ADM's standard) so they have dropped support with their closed source driver. There are ways to upgrade your open source driver but since you are running an unsupported release of Ubuntu it won't work (when it does work it does carry some risks)

---

### Post by jayemcee3 on 2014-02-23
Thanks Monkeybrain..... What do you suggest then.... the fella who put Ubuntu on my computer many moons ago when it was so simple to me then, has gone because of ill health so I am left in limbo & do not want to leave Linux for windows

---

### Post by deadflowr on 2014-02-23
You wanted to know how to find out what version of Ubuntu you are running?
```
cat /etc/lsb-release
```
Post the output back here.

---

### Post by jayemcee3 on 2014-02-23
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"

---

### Post by monkeybrain20122 on 2014-02-23
You can try to install Ubuntu 13.10. Download the iso, make a live usb with the startup disk creator if your bios has an option to boot from usb (you usually need to select it from the bios' menu) or if not burn a live cd. Then boot to it and choose install into hard drive and supply the information (such as time zone, keyboard etc) and wait for it to finish the job and that's it (since you are not trying anything fancy the basic installation is simple)

But I would wait for a second opinion first. I think it is graphic driver but I can be wrong. It would be nice if you can also tell us what brand and model is your machine and chances are someone might have had the same problem and figured out a solution already.

**Edited**: just saw your last post. So it is 12.04 rather than 13.04 and it is still supported so you may not have to install 13.10.

---

### Post by jayemcee3 on 2014-02-23
What I see on the front is a circle with Tt inside & Thermaltake underneath.. is this what you are after?? Sorry my ignorance with computers... I am told I am very knowledgable on other things but computers.... :)

---

### Post by monkeybrain20122 on 2014-02-23
I mean brand and model name, like e.g Dell latitude E5510 or Lenovo thinkpad T420, something like that.

---

### Post by jayemcee3 on 2014-02-23
Super
multi LG

Does that make sense? I don't see any other writing on it!

It isn't a laptop

---

### Post by Vladlenin5000 on 2014-02-23
It's an unbranded desktop then (Thermaltake is the brand of the tower, enclosure, whatever you wanna call the box where you put the hardware inside). 
So... An useful info would be the motherboard's brand/model, add-on graphics card (if any)...

---

### Post by jayemcee3 on 2014-02-23
Dum de dum dum..... How do I find that out??? I have to turn it all off & go inside the box then?

---

### Post by deadflowr on 2014-02-23
I'm not understanding the relation between the gpu and the growing number of workspaces.

Have you installed or used any configuration programs, such as MyUnity, or compizconfig-settings-manager?

Let's also make clear that this is indeed default Ubuntu 12.04
```
echo $DESKTOP_SESSION
```

As always a screenshot is worth a lot of time.
(Hit the prntscrn button to capture an image.
It'll be saved in the Pictures folder)

---

### Post by monkeybrain20122 on 2014-02-23
Just wondering, you said a friend set this up for you many months ago, do you experience this problem only recently?

---

### Post by monkeybrain20122 on 2014-02-23
> **deadflowr said:**
> I'm not understanding the relation between the gpu and the growing number of workspaces.

Have you installed or used any configuration programs, such as MyUnity, or compizconfig-settings-manager?


I suppose he has 
> Things like putting 4 desktops on only to find now it has decided to put 7 desktops on 

My understanding is that he used ccsm or unity-tweak-tool to put 4 desktops but it shows up as 7. But then may be there are other ways to do it from system settings. if this is the case, then may not be a gpu issue.

---

### Post by jayemcee3 on 2014-02-23
Yes, I noticed that too.... I went to [https://help.ubuntu.com/community/Ch...rUbuntuVersion]("https://help.ubuntu.com/community/CheckingYourUbuntuVersion")

Where it told me I has version 13.04 but then the terminal said it was 12.04 confusing to say the least... & I am not bothering about the desktops problem if I need to get rid of this version as it has soooo many problems.... Like this one where I can't get rid of the underline from where I pasted in the URL   Grrrrrrrr

& when it is posted here it becomes part of the URL...

---

### Post by 23dornot23d on 2014-02-23
Type df into a teminal and post the results back please 

df

( this just shows the disk and partition sizes )

---

### Post by jayemcee3 on 2014-02-23
No it was bad from the start...  monkeybrain

---

### Post by monkeybrain20122 on 2014-02-23
Well that page didn't tell you you have 13.04, it is a screenshot of what you may see. You go there with Windows and it will show you the same thing :)
As for the text following the link becoming part of it if you edit your post, it is an oddity of the forum apparently and has nothing to do with your OS. Just unlink the url with the third button from the right (it will still show up as a link when you post your message)

---

### Post by jayemcee3 on 2014-02-23
df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda5      454887848 231903312 199877568  54% /
udev              892680         4    892676   1% /dev
tmpfs             360000       856    359144   1% /run
none                5120         0      5120   0% /run/lock
none              899992       544    899448   1% /run/shm

Is there a better version? & how do I go about getting rid of this one & downloading the better one? Surely that would the the KISS way eh!!

Shivers monkeybrain you are clever!

---

### Post by 23dornot23d on 2014-02-23
There is a simple way to add a new desktop .......

( Let us know if it reports errors or if it installs ok - it will also show us if the graphics card works in it )

sudo apt-get update

then .......

sudo apt-get install lxde

[COLOR=#ff0000]**Answer no if it wants to remove lots of things though**[/COLOR]

Then if it is still showing problems we can go from there.

---

### Post by monkeybrain20122 on 2014-02-23
> **23dornot23d said:**
> There is a simple way to add a new desktop .......

( Let us know if it reports errors or if it installs ok - it will also show us if the graphics card works in it )

sudo apt-get update

then .......

sudo apt-get install lxde

[COLOR=#ff0000]**Answer no if it wants to remove lots of things though**[/COLOR]

Then if it is still showing problems we can go from there.

Now I get confused. I think OP means 4 virtual desktops showing up as 7, not installing another desktop environment. :confused:

---

### Post by deadflowr on 2014-02-23
Personally, instead of bloating up what you have, maybe download and install a fresh version.
You can get one by clicking on the option up top that says "Ubuntu Community" and choosing one of the Get 'buntu's that are listed.

For you I would recommend Xubuntu or Lubuntu.
Lighter and easy, in their own ways.

---

### Post by monkeybrain20122 on 2014-02-23
> **deadflowr said:**
> Personally, instead of bloating up what you have, maybe download and install a fresh version.
You can get one by clicking on the option up top that says "Ubuntu Community" and choosing one of the Get 'buntu's that are listed.

For you I would recommend Xubuntu or Lubuntu.
Lighter and easy, in their own ways.

In 12.04 he can just log into Unity 2d if 3d doesn't work rather than installing xubuntu or lubuntu. But it seems that unity 3d does sort of work, only broken somehow.

---

### Post by monkeybrain20122 on 2014-02-23
Since it is 12.04, can you just open a terminal and type
```

unity --reset
```
and logout/reboot
and then reset the number of desktop in ccsm/unity tweak?

---

### Post by 23dornot23d on 2014-02-23
My thoughts were to find out by doing a clean install of a new desktop - we can determine
if it is a graphics card problem or something else.

The install will show a few things ......... and quick and efficiently .....

1 ..... That the system itself is ok ............. ( no errors reported back on install )

2 ..... If errors are reported back - we will get a better understanding of what may be wrong. 
        [COLOR=#ff0000]**( no need to install if it shows errors - we can start fixing them ........... )**[/COLOR]

3 ..... If it installs as planned ..... at least the OP will have some sanity back in posting easily again.



if unity --reset works .......... then that is simpler ............ would agree ,

---

### Post by jayemcee3 on 2014-02-23
My goodness, am I confused now....
I don't want to add a new desktop, I have more than enough now.............. I just want the original Ubuntu (my original one!) that was put on my computer about 10 years back... So easy, so great, no problems at all.... bliss... & no, I don't know what version I had then.

My husband has a Samsung tablet that has windows on it, I was having trouble with the browser, Internet Ezplorer, not having the tool bars on it... daughter googled it & lots were having trouble with this too...after trying all they said, I gave up & downloaded Firefox.... problem fixed...

So I dearly hope to do the same thing here... Keep it simple sweetheart.... Can you help me do this?

---

### Post by monkeybrain20122 on 2014-02-23
Reset unity as in my post #33, then reset the number of desktop to see if it works. If not then logout and from the login screen choose unity 2d, may be you would like it.

It seems to be the most painless way to go about it as you don't need to install anything new.

---

### Post by jayemcee3 on 2014-02-23
Ok..... I did what you said Monkeybrain just don't know how to do the last bit
**and then reset the number of desktop in ccsm/unity tweak? 				**

Confusion in the household so please reply & I will try it when I get back on....
I am not ignoring you either 23dornot23 will complete monkeybrains first eh...

Thanks heaps you are great.... Just got to go as family calls... Ta muchly so far

---

### Post by monkeybrain20122 on 2014-02-23
Ok, never mind. I don't remember 12.04, maybe its default was 4 desktops? In newer Ubuntus the default is one and originally you said you have 13.04 so I assume you have used ccsm to make 4.

---

### Post by monkeybrain20122 on 2014-02-23
here is how you log into Unity2d if reset still doesn't work
[http://askubuntu.com/questions/74300/how-to-login-into-unity-2d](http://askubuntu.com/questions/74300/how-to-login-into-unity-2d)

---

### Post by jayemcee3 on 2014-02-24
Ok monkeybrain I am back...... 

I have done everything except   **'reset the number of desktop in ccsm/unity tweak?' 				**

How do I do this please??....

---

### Post by Bucky Ball on 2014-02-24
I use xfce4 as my desktop environment, but you need to be looking for 'Workspaces'. For me, it is in 'Settings>Settings Manager' so you will find it in settings somewhere. 

Once there, select to have only one workspace (if that's what you're after).

---

### Post by monkeybrain20122 on 2014-02-24
> **jayemcee3 said:**
> Ok monkeybrain I am back...... 

I have done everything except   **'reset the number of desktop in ccsm/unity tweak?'                 **

How do I do this please??....

Hi, how many desktops do you have now? This step may not be necessary. As I said in my last post I was thinking that you are using Ubuntu 13.04, since 13.04 defaulted to one desktop I assumed that you had used ccsm/unity tweak to make 4. But since it is Ubuntu 12.04 it was the default to have 4 desktops.

---

### Post by jayemcee3 on 2014-02-25
Will do then, thanks monkeybrain

---

### Post by steeldriver on 2014-02-25
If we are talking about the **number of workspaces** in the **default 12.04 desktop** then it can be set using the gsettings terminal command e.g.

```
gsettings set org.gnome.desktop.wm.preferences num-workspaces 1
```

or, if you can edit it graphically using the dconf editor (not installed by default, but available via the dconf-tools package)

[ATTACH=CONFIG]250682[/ATTACH]

---

