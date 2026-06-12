---
title: "Confused level 3 Sudo?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Silvanarix on 2008-04-26
Im obviously not grasping how all of this works! I upgraded to 8.04 it works  easier for us NOOBS!! But i still dont know how to turn off my X server and become level 3 under my root.. (*explain it like you were talking to a kid please! im VERY new*) I use GNOME not KDE.. better explanation is.. I have UBUNTU 8.04 hardy linux kernel 2.6.24-16 GNOME 2.22.1

I have an Nvidia Geforce FX 8800 GS, I downloaded the pkg1.run file from the Nvidia website for the 32 bit linux OS.. When i try to run it, it tells me i need to turn off my X server.. I tried a bunch of things to do this, such as booting directly to kernal from the ESC boot options, and CTRL-ALT-F1(*which did not close my X server like they said it would*).. 

When i boot to the command prompt from the ESC menu the X server is disabled, but the .run file asks me to be level 3???? When i try telinit 3 or su -c 'telinit 3' it just boots to GNOME and enables the X server.. 

Now ive ONLY been toying with linux for 2 days so if you decide to answer me, please PLEASE do it in "Linux for retards" language with very step by step directions.. All i want to know is how i get to a command prompt with a disabled X server as level 3.. It would also be nice to know what that means =) Thanks in advance for reading all of this!

Its extremely frustrating migrating from Windows XP to Linux!! But i know linux has more potential than the RAM windows uses to run ! :guitar:

---

### Post by Silvanarix on 2008-04-26
Just so everyone knows, ive browsed the forums for solutions, but i just dont know enough to decipher the information passed along. I merely am not understanding it, and when i type what is there.. I eithe get an error or nothing happens

---

### Post by dreadlord_chris on 2008-04-26
ok... step by step...
1) Boot your computer to your normal desktop
2) hit CTRL-ALT-F1 - this **switches** you to virtual terminal #1 (vt1). You haven't yet shut down your Xserver, it's still running.
3) log in to the terminal with you normal account - you are now technically logged in twice. This is rather common in the Linux world - don't worry about it.
4) shut down X: _sudo /etc/init.d/gdm stop_
5) **Now** you can run the NVIDIA driver package: _sudo sh NVIDIA..._
6) If the installer asks if you want to reboot at the end 'Just Say No'
7) Once you're dropped back to the command line, restart X: _sudo /etc/init.d/gdm start_

Hope that helps...

---

### Post by ghost_ryder35 on 2008-04-26
> **dreadlord_chris said:**
> ok... step by step...
1) Boot your computer to your normal desktop
2) hit CTRL-ALT-F1 - this **switches** you to virtual terminal #1 (vt1). You haven't yet shut down your Xserver, it's still running.
3) log in to the terminal with you normal account - you are now technically logged in twice. This is rather common in the Linux world - don't worry about it.
4) shut down X: _sudo /etc/init.d/gdm stop_
5) **Now** you can run the NVIDIA driver package: _sudo sh NVIDIA..._
6) If the installer asks if you want to reboot at the end 'Just Say No'
7) Once you're dropped back to the command line, restart X: _sudo /etc/init.d/gdm start_
 
Hope that helps...
nice I was going to say
```

sudo vi /etc/inittab
# It should look like this
# The default runlevel.
id:5:initdefault:
#Change it to this
# The default runlevel.
id:3:initdefault:

```
And the reverse to get it back to starting x

---

### Post by Silvanarix on 2008-04-27
> **ghost_ryder35 said:**
> nice I was going to say
```

sudo vi /etc/inittab
# It should look like this
# The default runlevel.
id:5:initdefault:
#Change it to this
# The default runlevel.
id:3:initdefault:

```
And the reverse to get it back to starting x
It actually says new file, with no info on the screen, so that was kinda wierd.. I got the Nvidia driver installed though, through synaptic.. Now my problem is with my GFX Freezing whenever a 3D program is used.. I tried that Alien arena, froze in about 10mins then tried Warcraft 3, froze in 10mins(*in wine of course*) I could have sworn my GFX card was an 8800GS, its showing as a GTS in my Hardware information window.. In my hardware drivers window its showing Nvidia accelerated graphics driver, not a specific card..

---

### Post by dreadlord_chris on 2008-04-28
> **Silvanarix said:**
> It actually says new file, with no info on the screen, so that was kinda wierd.. I got the Nvidia driver installed though, through synaptic.. Now my problem is with my GFX Freezing whenever a 3D program is used.. I tried that Alien arena, froze in about 10mins then tried Warcraft 3, froze in 10mins(*in wine of course*) I could have sworn my GFX card was an 8800GS, its showing as a GTS in my Hardware information window.. In my hardware drivers window its showing Nvidia accelerated graphics driver, not a specific card..

Yeah, we don't use inittab anymore - hence the empty file :)

Right now you have the "Official (free)" NVIDIA drivers installed - with your graphics card I would really recommend gong with the *Propietary* drivers (the package you initially downloaded). You will get significantly better performance from them.

You can either follow the instructions I already posted...

or, if you want a (mostly) point-n-click method - use EnvyNG:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by The Cog on 2008-04-28
dreadlord_chris's instructions should probably work, I think. If the install script still bitches that you are not in runlevel 3, you need to add an additional step and runn this command:
```
sudo telinit 3
```
which may well restart the X server if you have already stopped it, so you may have to stop it again.

To explain, Linux has 5 different "runlevels" that is can boot into. runlevel 1 is reserved for "single user mode" which has no GUI, very few running services and is reserved for recovery operations by the administrator.

runlevels 2-5 are used differently by different distros. In Red Had and its derivatives, runlevel 3 runs all the normal stuff except the X server, and runlevel 5 runs all the normal stuff (5 is the default of course). In Ubuntu, runlevels 2-5 are configured identically and 2 is the default. The Nvidia installer seems to be assuming that you are on a red-hat system, which is somewhat incompetent but not uncommon.

In the current version of Ubuntu, the runlevel to choose at boot is set in the file /etc/event.d/rc-default.

Again, if you are interested, switching to runlevel 0 powers the machine off, and runlevel 6 reboots it.

---

### Post by dreadlord_chris on 2008-04-29
if you use the installer from NVIDIA - you just have to make sure that X isn't running. Just (re)installed the beta drivers yesterday - no futzing with runlevels necessary.

If you use EnvyNG everything can be done from within X.

---

