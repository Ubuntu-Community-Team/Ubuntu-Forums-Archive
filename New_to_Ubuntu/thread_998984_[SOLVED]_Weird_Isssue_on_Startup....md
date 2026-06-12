---
title: "[SOLVED] Weird Isssue on Startup..."
date: 2008-12-01
forum: New to Ubuntu
---

### Post by hexbomber on 2008-12-01
So, my computer is behaving extremely weird now.

I don't know what I did but it seems to be fubar.
When I boot up, it gets passed the ubuntu loading screen, where I see a black screen, with a white cursor.... and it just hangs here...

It will be sitting here for like 20 minutes, and nothing happens. I left my laptop on for an hour and a half one time, and it eventually booted.. but evidently this can't be acceptable.

If I ctrl-alt-f1 to go into a text-mode boot, it won't let me manually "startx" saying, that it's already in use.

When I "sudo killall startx" It says "no processes killed"... and I've tried removing the /tmp/.X0-lock

Any suggestions?

---

### Post by metallicamike on 2008-12-01
is it doing this repeatedly? my computer does that sometimes and i just restart it and it is fine. But then again my hardware sucks!

---

### Post by halitech on 2008-12-01
what version of Ubuntu? (Ubuntu, Kubuntu, Xubuntu, 8.04, 8.10)

What kind of hardware do  you have? IE. video card, memory, CPU.

---

### Post by hexbomber on 2008-12-01
Yes, it does this repeatedly. And I can't quite remember what I did right before it started.

It does it everytime I boot. And I am using Ubuntu 8.10 with gnome.

---

### Post by ajgreeny on 2008-12-01
> So, my computer is behaving extremely weird now.
Do we assume from this that your computer used to behave itself?  If so you may have done something recently which has caused the problem, eg updating from 8.04 to 8.10.

We really need more info on your hardware before being able to help much further, but it sounds like a graphic card problem.  If you don't know what your card is go to the console (Ctrl+Alt+F1) and login and then enter sudo lspci and you should see the card details.  Let us know and then it may be possible to help more.

---

### Post by hexbomber on 2008-12-01
I am not on the ubuntu box atm, because obviously it won't connect. But It is ubuntu 8.10 (gnome if that matters at all), and even after the upgrade it worked fine.

Not like I don't have the specs to run ubuntu, it's got 4gb RAM, intel dual core...  it's been running all the versions of windows flawlessly from 6.06 till now.

Update*** It's the: Intel Integrated Graphics Media Accelerator X3100

---

### Post by halitech on 2008-12-01
it could be a case of the video drivers are corrupted or not working properly. what video card do you have?

---

### Post by hexbomber on 2008-12-01
Intel Integrated Graphics Media Accelerator X3100

---

### Post by halitech on 2008-12-01
maybe try this
```
sudo apt-get install xserver-xorg-video-intel
```
maybe its just using the wrong driver

---

### Post by hexbomber on 2008-12-01
How do I connect to the internet via the console. my GUI has spoiled me.

---

### Post by ajgreeny on 2008-12-01
Just login and type that in the console and it should install without problem.  You can do that easily in linux;  try it in windows and ???

---

### Post by halitech on 2008-12-01
```
sudo dhclient
```should get you an ip address. then issue the other command.

---

### Post by hexbomber on 2008-12-01
So I know I do a:

sudo dhclient
sudo apt-get .....

But I have 2 wireless networks around here.. how do I tell it which one  to connect to? 

The first, you connect to, login to the gateway (1.1.1.1) and enter your user/pass.

The second, you need to have securew2 (windows only) to connect. And you can't connect without it.

---

### Post by halitech on 2008-12-01
any chance of using a wired connection for this?

---

### Post by hexbomber on 2008-12-01
At home, I have a wired connection.. but it uses static IP's, and I've never actually setup my laptop with a static Ip because I always use my desktop at home :(.

---

### Post by halitech on 2008-12-01
router is not set up to give IP addresses at all?

I know you need to edit /etc/network.interfaces but I'm not sure what you need to enter other then the IP address

---

### Post by hexbomber on 2008-12-01
No, I always assign the IP address from the computer. Is there anyway to use the xorg from a cd? or like a repair function somewhere to fix xorg?

---

### Post by halitech on 2008-12-01
maybe from the command line this will work```
sudo xfix
```

---

### Post by hexbomber on 2008-12-01
xfix did not work. Is it possible to mount the ext3 file system, and modify it from windows? because I have a dualboot with vista + ubuntu on this machine. So I could edit my xorg.conf file from windows if possible...

---

### Post by halitech on 2008-12-01
possible but why not edit it from Ubuntu?

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by hexbomber on 2008-12-01
And what do I want it to say?

---

### Post by halitech on 2008-12-01
not sure cause I'm not sure what it has in there now. From what I have read, 8.10 basically takes control out of manually setting anything and does it 'automagically' so probably not much in there to start with.

---

### Post by hexbomber on 2008-12-01
that's what it looks like. I still have my ubuntu disk, is there anyway to do a repair, and reconfigure the xorg file from there.. while keeping all my settings and everything.

---

### Post by halitech on 2008-12-01
other then the xfix I'm not sure. I don't think the old dpkg-reconfigure xserver-xorg still works and not sure if the is any other repair option

---

### Post by hexbomber on 2008-12-01
"sudo xfix" is not found. Different syntax perhaps?

---

### Post by halitech on 2008-12-01
looks like it can only be done from the recovery mode, reboot and go into the recovery mode and run xfix. another thing we can try is while there, run ```
apt-get remove xserver-xorg && install xserver-xorg
``` maybe that will help as well.

---

### Post by hexbomber on 2008-12-01
root@hex-laptop:~# xfix
bash: xfix: command not found

apt-get remove xserver-xorg && install xserver-xorg is working, and taking quite a while... we'll see if it turns up anything. Do I need an internet connection to redownload xserver-xorg?

***UPDATE**
* Restarting Hardware abstraction layer hald
invoke-rc.d: initscript hal, action "restart" failed.
Install: missing destination file operand after 'xserver-xorg'
Try 'install --help' for more information.

---

### Post by halitech on 2008-12-01
as long as the cd is listed in sources.list it should hopefully grab it from there. 

hmmmmm, that doesn't look good. try ```
sudo apt-get install -f xserver-xorg
```

---

### Post by hexbomber on 2008-12-01
ahh.. I dont know if the CD is in the sources.list

---

### Post by halitech on 2008-12-01
run```
cat /etc/apt/sources.list
``` and see if it is

---

### Post by hexbomber on 2008-12-01
okay, so I added the cdrom to the sources.list with:
sudo apt-cdrom add

and it says it added.. but when I try doing apt-get install xserver-xorg it still says "failed to fetch from *****"

So, it's still looking for an internet connection, if I could figure out how to configure my gateway, and dns from ifconfig I could get an internet connection. I've set the IP already.

---

### Post by halitech on 2008-12-01
```
sudo nano /etc/network/interfaces
```

that will allow you to edit the config file

---

### Post by hexbomber on 2008-12-01
So, I just did a "route add default gw XXX.XXX.XX.XXX" and that seems to get me an internet connection, now it's downloading. We'll see what happens.

---

### Post by halitech on 2008-12-01
time to cross fingers, toes, eyes and anything else we can cross

---

### Post by hexbomber on 2008-12-01
BATTERY DIED.... just as it was finishing, so now i gotta go find an outlet.

On reboot, running from root I can now "startx" and it boots up fine.. but it doesn't load on it's own when I start my computer regularly.

---

### Post by halitech on 2008-12-01
crap, hopefully it didn't mess things up

---

### Post by hexbomber on 2008-12-01
Yeah.. so if I go into recovery mode, and drop down to a root console, I can "startx" successfully.. but in a normal boot, it won't let me.

---

### Post by halitech on 2008-12-01
what happens in a normal boot?

---

### Post by hexbomber on 2008-12-01
same this as before. Hangs at the black screen with the cursor. When I go to text mode, it wont let me manually start xserver, saying it's already in use.. make sure to end it first."

So I'm doing a reinstall.... thanks for your help.

---

### Post by halitech on 2008-12-01
thats strange, sounds like a permissions issue to me but not sure why it would happen

---

