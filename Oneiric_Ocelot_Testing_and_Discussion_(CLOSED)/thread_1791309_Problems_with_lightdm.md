---
title: "Problems with lightdm"
date: 2011-06-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by JRV on 2011-06-26
I installed Oneiric from the Daily Live CD on 6/25/11.
After finisning the install I made a few changes.
I used "gksudo gnome-terminal" to add .config/nautilus directories to /root/.
Then I made minor changes to the /etc/lightdm/lightdm.conf file.
In the XDMCP section, I uncommented the "enabled=yes" and the port number.
Shortly after I tried to reboot and it hung.
I think I have found two bugs in lightdm. 

1 - A minor edit to the config file makes it unbootable.
2 - I can't log in remotely using XDMCP after the edit.

The solution to the first bug was easy, I rebooted into recovery mode and ran dpkg.

I have filed bug reports using Apport before, but how do I file one where I have to just write it? I've looked all over launchpad and I can't find anything like that.

---

### Post by kansasnoob on 2011-06-26
My eyesight kind of sucks and I'm used to using Alt+SysReq+K from the live desktop after inserting a modified "xorg.conf" but I still haven't found a decent way to restart X on the live DE.

IMHO lightdm is hardly usable ATM :(

---

### Post by kansasnoob on 2011-06-26
**I have filed bug reports using Apport before, but how do I file one where I have to just write it? I've looked all over launchpad and I can't find anything like that.**

Like it says here:

[https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net](https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net)

File using "http://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect", in this case:

```
http://bugs.launchpad.net/ubuntu/+source/lightdm/+filebug?no-redirect 

```

I hope I got that right, I'm getting rusty ;)

---

### Post by cariboo on 2011-06-26
The one thing I like about lightdm is that you can test changes without having to reboot using the following command:

```
lightdm --test-mode
```

See screenshot, lightdm is fully function in test mode.

---

### Post by Atermoon on 2011-06-28
> **cariboo907 said:**
> The one thing I like about lightdm is that you can test changes without having to reboot using the following command:

```
lightdm --test-mode
```

See screenshot, lightdm is fully function in test mode.

Yeah, just remember to close it via the X button or ctrl+c in terminal. I made the mistake of clicking "shutdown" in the lightdm test window once... /facepalm

---

### Post by jbicha on 2011-06-29
> **JRV said:**
> 
I used "gksudo gnome-terminal" to add .config/nautilus directories to /root/.


I can't think of a single good reason to run gksudo gnome-terminal. Just run the terminal normally and run **sudo** before commands that need to be run as root.

---

### Post by cariboo on 2011-06-29
Why not open a terminal and use sudo -i?

---

### Post by jerrylamos on 2011-06-29
> **cariboo907 said:**
> Why not open a terminal and use sudo -i?

Problems with lightdm?

Crash.  Crash.  Crash.  On all 3 test pc's.  And doesn't even leave an entry in /var/crash.

Simple things like opening a terminal window either with BFB or Ctrl-Alt-t and doing a:
df
may well kill lightdm.  Oh, well, sudo service lightdm stop & sudo service lightdm start.  There's a lot of water to go under the bridge by RC time...  

Jerry

---

### Post by dino99 on 2011-06-29
> **jerrylamos said:**
> Problems with lightdm?

Crash.  Crash.  Crash.  On all 3 test pc's.  And doesn't even leave an entry in /var/crash.

Simple things like opening a terminal window either with BFB or Ctrl-Alt-t and doing a:
df
may well kill lightdm.  Oh, well, sudo service lightdm stop & sudo service lightdm start.  There's a lot of water to go under the bridge by RC time...  

Jerry

profile borked ?

---

### Post by cariboo on 2011-06-29
Jerry, there has to be something wierd going on on your three systems, the only time I've had a problem with lightdm, is when I changed the background image to one that didn't exist, and forgot to change it back before I rebooted.

---

### Post by jerrylamos on 2011-06-29
> **cariboo907 said:**
> Jerry, there has to be something wierd going on on your three systems, the only time I've had a problem with lightdm, is when I changed the background image to one that didn't exist, and forgot to change it back before I rebooted.

Well, this is a relatively new Aspire One netbook runs Unity 3D fine, Windoze 7 fine, Meerkat fine, Narwhal fine.  For hours.  29 June Daily Build iso lightdm crashed, rebooted did update, rebooted and just crashed again launchpad bug #803559.  

My notebook is "new", runs Narwhal and Windoze 7 fine, just installed 28 June amd64 daily build which is a little shaky, running except for problems with downloading the proprietary drivers which Ubuntu suggested I do. Lightdm crashes...

The tower is a Compaq 3.3 mhz, nice and fast, does TV etc.  Runs Lucid fast (!) Meerkat, Narwhal, and gets lightdm crashes too.

I do zsync on each of them direct from Daily Build so I'm not copying a .iso between them.

Jerry

---

### Post by jerrylamos on 2011-06-29
> **cariboo907 said:**
> Jerry, there has to be something wierd going on on your three systems, the only time I've had a problem with lightdm, is when I changed the background image to one that didn't exist, and forgot to change it back before I rebooted.

Launchpad has some info on the bug: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/802271](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/802271).  To quote part of the comments:

...In duplicate bug 798509, some characters (on a US/English keyboard, the 2 key in the alphanumeric portion of the keyboard, and both enter keys) trigger the X server to terminate (so it is not just that characters are sent to tty1--the X server also quits, popping the user back to a virtual console on tty1).,,

Hmmm.

Jerry

---

### Post by seeker5528 on 2011-06-29
> **cariboo907 said:**
> Why not open a terminal and use sudo -i?

Hmmm. 

Is there some advantage to doing 'sudo -i' over 'sudo su'? 
And if all you really care about is setting $HOME ('sudo -H') wouldn't 'sudo -i' be overkill?

And last but not least, if you are doing this in Unity, wouldn't it be quicker to open the dash type 'root', then select 'Root Terminal'?

But going back to....

> **JRV said:**
> I used "gksudo gnome-terminal" to add .config/nautilus directories to /root/.

Why use 'gksudo gnome-terminal' to add '/root/.config/nautilus/' when doing 'gksudo nautilus' *should* cause nautilus to create it?

Later, Seeker

---

### Post by Starks on 2011-06-29
lightdm is causing some nasty problems with plymouth

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/798509](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/798509)
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/802271](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/802271)

---

### Post by cariboo on 2011-06-29
> **seeker5528 said:**
> Hmmm. 

Is there some advantage to doing 'sudo -i' over 'sudo su'? 
And if all you really care about is setting $HOME ('sudo -H') wouldn't 'sudo -i' be overkill?

And last but not least, if you are doing this in Unity, wouldn't it be quicker to open the dash type 'root', then select 'Root Terminal'?

But going back to....



Why use 'gksudo gnome-terminal' to add '/root/.config/nautilus/' when doing 'gksudo nautilus' *should* cause nautilus to create it?

Later, Seeker

sudo -i is probably overkill for most things, but for those very few times that you really need to be root it works.

---

### Post by sparker256 on 2011-06-30
I am trying to shutdown or restart and instead I get a lightdm login screen and if I click on the icon on the far right there is no drop down. To get out I go into terminal and type sudo reboot and it reboots. This does not happen all the time but enough to be very annoying.

Bill

---

### Post by jerrylamos on 2011-06-30
30 June Daily build live what I thought was lightdm crash is likely X windows crash see Launchpad bugs 803847 and 802271.  Lightdm goes away so I do sudo service lightdm stop & start but what may be happening is starting X windows again.

Jerry

---

### Post by sparker256 on 2011-06-30
> **jerrylamos said:**
> 30 June Daily build live what I thought was lightdm crash is likely X windows crash see Launchpad bugs 803847 and 802271.  Lightdm goes away so I do sudo service lightdm stop & start but what may be happening is starting X windows again.

Jerry
Have you tried the command "sudo restart lightdm"? It works for me just wondered if it would work for someone else.

Bill

---

### Post by dino99 on 2011-06-30
no issue here, you should purge gdm & lightdm then reinstall lightdm; to clean that mess

---

### Post by jerrylamos on 2011-06-30
> **Starks said:**
> lightdm is causing some nasty problems with plymouth

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/798509](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/798509)
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/802271](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/802271)

Right on, Starks.  The comments in the bug#802271

Steve Langasek wrote 10 hours ago: 	#6

Analysis with Robert:

- currently lightdm tries to start on the active VT. It shouldn't do this; if plymouth is running it should use the active VT (after proper hand-off), otherwise it should take the next available
- /etc/init/plymouth-stop.conf doesn't special-case lightdm currently, so plymouth is *never* running when lightdm starts - so we never get the hand off. As a result, we always have a race condition between the VT switch on plymouth exit, and the lightdm start-up.

Jerry

---

