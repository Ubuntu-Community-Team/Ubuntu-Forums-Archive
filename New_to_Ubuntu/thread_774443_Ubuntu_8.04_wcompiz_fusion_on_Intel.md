---
title: "Ubuntu 8.04 w/compiz fusion on Intel"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by titanium87 on 2008-04-29
Hi I'm new to The Linux Ubuntu world and I'm getting accustom to it day by day, but my problem is that I'm trying to get compiz fusion 0.6.2 to work on my computer my video graphics in on board 

superman@Superman-PC:~$ lspci
00:00.0 Host bridge: [B][COLOR="Red"]Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)[/COLOR][/B]

also I need help installing compiz fusion, I'm having trouble installing it

so can anyone please help me, greatly appreciated!!:(:)

---

### Post by Golem XIV on 2008-04-29
If you're using Gutsy you're SOL because that chipset has been blacklisted for use in Compiz.  There are ways to get around it but they mean sacrificing other things like video playback.  I would suggest that you upgrade to Hardy, since it fixed all those problems and makes the 965 work perfectly with Compiz.

<edit>
Doh!  I just saw you are on Hardy.  Did you enable the effects from System -> Preferences -> Appearance?

Why are you installing Compiz when it's supposed to come pre-installed?
Why are you installing 0.6.2 when the repositories have 0.7.4?
 </edit>

---

### Post by titanium87 on 2008-04-29
ok ummm there was this program that I found called Ubuntu tweak and in it it says sorry only takes compiz 0.6.2 or something like that so I went looking for compiz, and I'm trying to install it but cant and if ur saying it comes "pre-installed" with Ubuntu 8.04 (Hardy), please tell me where it is cuz I cant find it and earlier you said it should be in the repository???how do I install it from there then??

---

### Post by aheckler on 2008-04-29
Compiz is already installed in Hardy, if that's what you're running. The settings manager can be installed with:

```
sudo apt-get install compizconfig-settings-manager
```

You can turn it on by going to System > Preferences > Appearance then the Visual Effects tab and setting it to Normal or Extra.

---

### Post by Tom--d on 2008-04-29
I have the intel 965 chip set and using hardy. 

It works! its just perfect! 
Yeah, in gusty I had to take it of the blacklist but video playback was enabled (but a special way ;) in vlc)

Compiz fusion is pre installed and will be running if you are using hardy (8.04)

In the repo's search for CCSM. Its a configuration tool which you can change every single effect in compiz. Trust me. you will be amazed :D I was.

---

### Post by Golem XIV on 2008-04-30
> **titanium87 said:**
> ok ummm there was this program that I found called Ubuntu tweak and in it it says sorry only takes compiz 0.6.2 or something like that so I went looking for compiz, and I'm trying to install it but cant and if ur saying it comes "pre-installed" with Ubuntu 8.04 (Hardy), please tell me where it is cuz I cant find it and earlier you said it should be in the repository???how do I install it from there then??

I was asking because it wasn't clear in your post what flavour of Ubuntu you were using.  Ubuntu server and Kubuntu, for example, don't come with Compiz pre-installed. 

From the System menu, select Preferences -> Appearance.  Go to the Visual Effects tab and enable the effects.  If you get an error, please post it.

Now fire up the Synaptic package manager and find "compizconfig-settings-manager".  Mark it for installation and Apply.  Once installed, it will appear under System -> Preferences as "Advanced Desktop Settings".  You can tweak Compiz from there.

Ubuntu Tweak has been upgraded to [version 0.3]("http://ubuntu-tweak.com/") specifically to fix some bugs with Hardy.  I suggest that you get this new version and install it.

Good luck!

---

### Post by kshtjsnghl on 2008-04-30
hey
 
 I have got intel 945 gm chipset in my laptop and kept the normal settings in the appearance settings.
  
i upgraded to hardy just today and but when i was in gutsy i got some problems with the beryl and compiz.
 
 So, just so you know, will compiz fusion work properly on my laptop this time??

---

### Post by titanium87 on 2008-05-01
ok Thanks so much your help with my previous issues with my intel controller

VGA compatible controller: Intel Corporation 82G965 Integrated Graphics 
Display controller: Intel Corporation 82G965 Integrated Graphics Control

I currently upgraded from Ubuntu to Ubuntu Studio doing a "Online update"
But now I have a new problem 2 problems actually,

1st. When I try to activate the visual Effects from normal to Extra I get an error message saying "Desktop Effects Cannot Start"

2nd when I'm trying to get something from add/remove or like when I try to update something or install something...sometimes I get an error it says a bunch of stuff but at the end part of it it saying the my CDROM has to be recognized by APT. and that I cant use apt-get update, I have to use apt-cdrom or something like that.

---

