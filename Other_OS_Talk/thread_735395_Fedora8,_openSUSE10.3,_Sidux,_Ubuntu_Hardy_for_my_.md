---
title: "Fedora8, openSUSE10.3, Sidux, Ubuntu Hardy for my IBM T60"
date: 2008-03-25
forum: Other OS Talk
---

### Post by Antman on 2008-03-25
Machine: IBM Lenovo t60
Goal: looking for the perfect distro to fit **my** needs.

I am a big fan of Sidux, but my ATI drivers just didn't like to wake up from suspend or hibernate.

openSUSE 10.3 loved my laptop (even the ATI drivers) but using zypper was just a pain speed wise (looks like the revamped zypper update will fix that issue), and sometimes using wireless was a little flakey at different locations.

I am now using Fedora8 on my laptops and I must say that I am very impressed with it. Yum is pretty fast and almost comparable with apt-get, The ATI drivers work flawlessly; even suspend and hibernate, and wireless is great. 
I must say Fedora8 is the best distro I have found for my IBM T60 (and yes I also tried PCLinuxOS 2008 minime). 

Now, I will download the Ubuntu Hardy and Fedora9 Betas and let them compete head to head.... and the winner is........??

I'll post my results

---

### Post by cardinals_fan on 2008-03-25
I hated yum, but Fedora 8 really surprised me.  They paid a lot of attention to the little things, and it showed.  Very polished.

---

### Post by markharding557 on 2008-03-26
if fedora fits the bill then use that this is what makes linux so good is options,options you don't get elsewhere

---

### Post by MaindotC on 2008-04-25
Hey, Antman.  I have a T60 and I just did the distribution upgrade from Gutsy to Hardy via command line, and here's what I noticed so far:

The big thing for me is the sleep button because I hate constantly shutting it on and off.  Sleep now works for me in Hardy!

I have an Intel 3495 wireless card as you may or may have the atheros card.  The wireless card works great, but the wireless light does not illuminate.  No big deal to me.  I operate on a WPA2 network so you shouldn't have any problems with passwords.

I don't think this has to do with the hardware, but just so you know - there seems to be a problem connecting to network shares.  I am in a campus environment and before Hardy I could connect to Windows shares.  Now that I upgraded to Hardy I cannot and it's very frustrating.  There's a bug report and I believe some guy in Sweden is working with the bug report team to fix it.  Last update I saw was April 22nd.

All USB ports seem to work fine - I used a trackball.  I also connect my laptop to a 23'' Samsung 213T monitor to use a larger screen than the 15'' from time to time and it works perfectly.  You can actually switch back and forth between 1600x1200 and 1068x764 flawlessly.  Before you could only switch down in screen size and any increases in desktop size would require restart of X server.

The Fn + F2 locks the screen perfectly (and you can unlock it).  Fn + F3 gives you battery information but I don't see any options to perform maintenance. Fn + F4 works as I said before.  

Fn + F5 works the wireless card (except the wireless light) but when I shut it off it had difficulty rejoining the network - I don't really find this a big issue but there is a new wireless driver and perhaps I just need to install it.  

The backlight keys work fine, as well as the nightlight.

That's all I have for now.  I think if you put Hardy on your T60 you'll be pleasantly surprised.  Keep watching the Hardy-On-A-Thinkpad-T60 wiki.

---

### Post by SneakyBooBoo on 2008-04-25
YUM is the reason i dont log into my Fedora 8 anymore. i want to install programs but its just hangs sometimes when i switch tabs and its hard to find my apps i want. The Add/Remove programs feature and Synaptic are the best ive seen ever. and easy to use.

---

### Post by MaindotC on 2008-04-25
Did you install Fedora on a T60?  If so, may I ask if you ran into any problems and how you resolved them?  Thanks!

---

### Post by Antman on 2008-04-25
> **strAlan said:**
> Did you install Fedora on a T60?  If so, may I ask if you ran into any problems and how you resolved them?  Thanks!

Fedora8 and 9 work very well on my T60. The only issue I have with F8 and my T60 is after it comes out of suspend mode it forgets I have a wireless card sometimes. Other then that it works great.

---

### Post by Antman on 2008-04-25
> **SneakyBooBoo said:**
> YUM is the reason i dont log into my Fedora 8 anymore. i want to install programs but its just hangs sometimes when i switch tabs and its hard to find my apps i want. The Add/Remove programs feature and Synaptic are the best ive seen ever. and easy to use.

The way around the default package manager in F8 is to just install YumEx. It works WAY better.
```
su
yum install yumex
```
Fedora 9 is using PackageKit which is on par with synaptic.

---

### Post by dptxp on 2008-04-25
ATI drivers will work in Fedora, Redhat has ATI driver support.
Not debian, not atleast 64-bit. 64 bit drivers did not work for my X1100.

---

### Post by SneakyBooBoo on 2008-04-25
> **Antman said:**
> The way around the default package manager in F8 is to just install YumEx. It works WAY better.
```
su
yum install yumex
```
Fedora 9 is using PackageKit which is on par with synaptic.
i'll look into that when im bored enough to log into Fedora haha.  thanks tho.

---

### Post by Antman on 2008-04-25
> **strAlan said:**
> Hey, Antman.  I have a T60 and I just did the distribution upgrade from Gutsy to Hardy via command line, and here's what I noticed so far:

Hardy runs pretty well on my T60 too. But I have noticed that it is a little buggy and slow sometimes. Like the system delays or stutters when doing normal stuff like selecting another window or opening a USB flash stick. 

The Fedora9 Preview (with the current updates) actually seems more stable at this point than Hardy at the moment. Also, Fedora9 works on more of my machines than Hardy. I have a x41 sub-notebook and hardy will not automount any usb stick (I have to manually mount); F9 though works perfectly with it.

Actually, I like Mandriva 2008.1 better than hardy right now. It's very nice and slick.

Now I am testing the new Sidux 2008.1 Nyx and that is nice. I have to see how it plays with my t60 again and ATI drivers.

My top 4 in order
1. Fedora
2. Mandriva
3. Sidux (may move up)
4. Hardy

EDIT: I'll try and disable the Hardy Desktop Effects and see if that calms the system down.

---

### Post by MaindotC on 2008-04-26
Yeah I've noticed little ticks like that too.  Firefox 3 crashes from time to time.  The system takes longer to recognize my login credentials and start gnome than usual - that may have to do with my startup processes, though.  I tried F8 before and I had a problem - not sure what it was but I'll try and boot into the livecd and see what I can do.  The HUGE issue I'm dealing with right now is you can't connect to windows password-protected shares and I'm on a campus and keep all of my stuff on the network drives.  Frustrating.  I'll be in touch.

Also, VLC - if I have a couple videos on a playlist, now VLC freezes for 120 seconds in between videos or when a video is done playing.  Just one of those things that I think they'll work out soon.

---

### Post by CPImmanuel on 2008-04-26
Interesting! I went through the same exercise, but I was so happy with Fiesty Fawn on my Thinkpad R51. So, when I got my Thinkpad T60p I tried Gusty Gibbon, but I could not get it to install at all. I tried Suse and Fedora, and they looked OK, alhough I did not proceed very far. Version 8.4 of Ubuntu install went all the way through, but the wireless card does not work. I have even tried PCMCIA cards, but it simply does not recognize wireless.... I have the Artheos wireless built in to the thinkpad. I will try some more with Ubuntu. but if I cannot get wireless to work, I will re-investigate Suse or Fedora. I do not plan to go back Windows Vista. 

The only other problems that I have seen so far, is the mouse pointer...it is weird looking. Also, KDE4 is quite different than before, but I don't mind using GNOME. I have not yet tested VirtualBox or USB connected devices... I have all these working well in my Thinkpad R51 with Fiesty Fawn Ubuntu. 

Paul

---

### Post by MaindotC on 2008-04-26
If you have the atheros chip, I  believe you need to install the madwifi driver.  I'm not sure how to do this but other classmates of mine who have T61's said they needed the madwifi driver to get the wireless card working.

---

