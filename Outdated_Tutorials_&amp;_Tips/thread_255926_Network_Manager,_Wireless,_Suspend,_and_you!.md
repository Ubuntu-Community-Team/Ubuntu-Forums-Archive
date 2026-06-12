---
title: "Network Manager, Wireless, Suspend, and you!"
date: 2006-09-12
forum: Outdated Tutorials &amp; Tips
---

### Post by jsully1 on 2006-09-12
Hi everyone.  After having issues getting my wireless to work after I resume from a suspend for a few weeks, I decided to do something about it.  Here is my solution, that automatically refreshes your wireless after a suspend.  After a ton of searching I found one post that mentioned that starting dbus solves the problem - so I just made a script (if you can call one command a script :)) that triggers the specific bit of the dbus restart that fixes the issue and makes Network Manager happy again.

The issue I'm referring to is when you suspend and move to a different location, upon resume network manager doesn't see your wireless device, and the only thing that fixes it is a reboot.

First, let's create a file in your home directory - I called it fixnetwork.sh

Add the following to the file:
```
/etc/dbus-1/event.d/25NetworkManager restart
```
Now 
```
sudo chmod u+s /home/user/fixnetwork.sh
sudo chown root\: fixnetwork
```

Now if you want to have it run every time the computer resumes, run the following command:
```
sudo cp fixnetwork /etc/acpi/resume.d
```

Doublecheck the permissions and ownership to make sure they match the other scripts here.  An "ls -la" should look something like this:
```
you@yourlaptop:/etc/acpi/resume.d$ ls -la
total 92
drwxr-xr-x 2 root root 4096 2006-09-11 17:25 .
drwxr-xr-x 8 root root 4096 2006-08-05 19:24 ..
-rwxr-xr-x 1 root root   75 2006-06-19 06:52 10-thinkpad-standby-led.sh
-rwxr-xr-x 1 root root  205 2006-06-19 06:52 13-855-resolution-set.sh
-rwxr-xr-x 1 root root   86 2006-06-19 06:52 15-video-post.sh
-rwxr-xr-x 1 root root  436 2006-06-19 06:52 17-video-restore.sh
-rwxr-xr-x 1 root root  523 2006-06-19 06:52 35-modules-load.sh
-rwxr-xr-x 1 root root  198 2006-06-19 06:52 40-infra-red.sh
-rwxr-xr-x 1 root root  205 2006-06-19 06:52 49-855-resolution-set.sh
-rwxr-xr-x 1 root root  152 2006-06-19 06:52 50-framebuffer-enable.sh
-rwxr-xr-x 1 root root   47 2006-06-19 06:52 50-time.sh
-rwxr-xr-x 1 root root  304 2006-06-19 06:52 50-tosh-restore-brightness.sh
-rwxr-xr-x 1 root root  103 2006-06-19 06:52 55-screen.sh
-rwxr-xr-x 1 root root  142 2006-06-19 06:52 60-asus-wireless-led.sh
-rwxr-xr-x 1 root root  200 2006-06-19 06:52 62-ifup.sh
-rwxr-xr-x 1 root root  179 2006-06-19 06:52 65-console.sh
-rwxr-xr-x 1 root root  102 2006-06-19 06:52 67-sound.sh
-rwxr-xr-x 1 root root  142 2006-06-19 06:52 69-services.sh
-rwxr-xr-x 1 root root  662 2006-06-19 06:52 72-acpi-pain.sh
-rwxr-xr-x 1 root root   75 2006-06-19 06:52 90-thinkpad-unstandby-led.sh
-rwxr-xr-x 1 root root  342 2006-06-19 06:52 90-xscreensaver.sh
-rwxr-xr-x 1 root root   82 2006-06-19 06:52 98-acpi-unlock.sh
-rwxr-xr-x 1 root root   93 2006-09-11 17:26 fixnetwork.sh
```
I'm using this specifically on my IBM T60.

---

### Post by christophe123 on 2006-09-14
On my x40, netwrok-manager does not like suspend/resume either but displays a different behavior: After resume, the nm-applet says that there is no network  but with "iwconfig eth1" I see that a low-signal not-protected has been picked up instead of my strong-signal WEP-protected one.

Christophe 

PS: I don't think your +s does what you want:

> sudo chmod u+s /home/user/fixnetwork.sh
> sudo chown root\: fixnetwork

As far as I know, +s does not work with script.

---

### Post by giacomolg on 2007-01-05
have a look to:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

cheers

---

### Post by accord on 2007-06-07
I'm having this problem too. I think the above post is what I'm looking for. Thanks a lot!

Are there plans to fix this bug in the next release? Maybe we should submit one!

---

### Post by RealG187 on 2009-03-24
Forget doing it automatically, I cannot even get it to come back manually

[http://ubuntuforums.org/showthread.php?t=1105558](http://ubuntuforums.org/showthread.php?t=1105558)

I am so F***ing ******* annoyed

---

### Post by theNthDoctor on 2010-08-19
A simple solution that worked for me:

[http://ubuntuforums.org/showthread.php?p=9740825#post9740825](http://ubuntuforums.org/showthread.php?p=9740825#post9740825)

With credit to user swizman for pointing out where to make the modification.

---

