---
title: "Synchronization Time Server Problem"
date: 2023-03-19
forum: New to Ubuntu
---

### Post by bhubunt on 2023-03-19
Hi, 
During live sessions on Ubuntu 18.04, desktop version, the time consistently changes to UK time, even after I have updated the time in settings.

I get the following code: 

```
 Synchronized to time server 185.125.190.58: 123  
``` 

And thereupon the time jumps one hour back.

This is an Ubuntu 18.04 flash drive, which I am using on a desktop. I do not have a server. Is such a connection to a UK-based NTP part of the 18.04 installation package?

The jump in time consistently messes up the system logs.

---

### Post by TheFu on 2023-03-19
> **bhubunt said:**
> Hi, 
During live sessions on Ubuntu 18.04, desktop version, the time consistently changes to UK time, even after I have updated the time in settings.

I get the following code: 

```
 Synchronized to time server 185.125.190.58: 123  
``` 

And thereupon the time jumps one hour back.

This is an Ubuntu 18.04 flash drive, which I am using on a desktop. I do not have a server. Is such a connection to a UK-based NTP part of the 18.04 installation package?

The jump in time consistently messes up the system logs.

System logs are stored in UTC.  When you use a read-only session, it makes perfect sense for a UK-based company to default to UTC.  
```
sudo dpkg-reconfigure tzdata
```
is how to change the timezone displayed by the system.
In about a month, standard support for 18.04 ends.  At this point, everyone should be moving off it.  I'm moving to 20.04 on my few remaining 18.04 systems.

---

### Post by bhubunt on 2023-03-19
> **TheFu said:**
> 
In about a month, standard support for 18.04 ends.  At this point, everyone should be moving off it.  I'm moving to 20.04 on my few remaining 18.04 systems.

Thanks very much, TheFu. 

However, I'd like to mention that I tested whether the problem is related to Ubuntu 18.04 and it is not. 

The same thing happened just now with a live Ubuntu 20.04 session, even though the entire session started out with the correct time. Then all of a sudden again the same code line reporting the switch to the UK Time Server, at about 15 minutes into the session. Sometimes the time switch happens 20 minutes into the session.

Here's the Ubuntu 20.04 log, line 41  [https://pastebin.com/DjBD4C0F](https://pastebin.com/DjBD4C0F) 

I have now changed the time zone in the terminal. 

Let me also add that I have had similar mess ups of times in other logs on two laptops that have Ubuntu 20.04 as an OS, as reported in another thread. In one, the year even switched to 2032. 

The time switches mess up the logs, as obvious from this screenshot. The actual session started at 17:34, not 18:34.

---

### Post by TheFu on 2023-03-19
Do an install of the OS.  Run the dpkg-reconfigure. It works.

The 18.04 comment was purely due to support ending shortly. Anyone thinking of installing 18.04 today is crazy.

---

### Post by MAFoElffen on 2023-03-19
> **bhubunt said:**
> Hi, 
During [COLOR=#b22222]live sessions[/COLOR] on Ubuntu 18.04, desktop version, 
TheFu is correct. Except he doesn't know the background, that because you have a bad hard disk, that you cannot make those changes permanent, so you are running from Ubuntu LiveUSB installation media.

You have made any posts where you are complaining that your system logs and other changes disappear when you shut down your system from the live media. I have tried to explain to you, that the Live Image environment  only exists in memory, and that all changes are lost when you shut down your system. I explained that if you created a, per-se, Ubuntu "On-The-Go" persistent USB, that most of the challenges would go away, just as they would go away if you were able to install Ubuntu permanently...

RE: 
[https://www.howtogeek.com/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)
[https://kb.uconn.edu/space/IKB/10763764277/Creating+a+Ubuntu+%22To-Go%22+USB+(Persistent+USB)](https://kb.uconn.edu/space/IKB/10763764277/Creating+a+Ubuntu+%22To-Go%22+USB+(Persistent+USB))

My recommendations would be to create it with a currently supported version of Ubuntu. (22.04.2), where a lot of things have already been resolved, and are supported. Also understand that it will take longer for a persistent image to boot. Buying a good USB 3.2 Thumb drive would make that faster... But you could wait and use that extra money towards buiyn a replacement internal drive for your laptop.

Just some thoughts to help you.

---

### Post by bhubunt on 2023-03-19
Hi,

TheFu made a helpful remark in this thread about the terminal command. I have no qualms with what you say about the live sessions. But even if these are only live sessions that only exist in memory, it's important that the time zone not change like that. TheFu's terminal command fixed the problem and I will issue the command now at the beginning of such "emergency" live sessions.  
As I mentioned before, this particular computer will get a different hard drive soon with a new installation. 

Moreover, as I noted in this thread and in another thread, I have had similar synchronization issues on stable Ubuntu operating systems, in other words, *outside* the Live image environment. That is the very reason why I brought up the recurring synchronization issue.

I am not "complaining." I am trying to gauge technical issues by asking questions.

---

### Post by MAFoElffen on 2023-03-19
Just understand that, at the start of every Live Image session (without persistence), that you will have to issue that command... And that once you shut down the Live image Environment, that those changes will be lost.

On an installed system, or on a Live Image installed with persistence, those changes are saved and permanent.

---

### Post by bhubunt on 2023-03-19
> **MAFoElffen said:**
> Just understand that, at the start of every Live Image session (without persistence), that you will have to issue that command... And that once you shut down the Live image Environment, that those changes will be lost.



Hi,

I do understand the difference between the Live image session and the stable system.

And as mentioned in my previous post, I plan to issue this time zone command at the beginning of each live session.

Believe you me, I would rather not use live sessions, but as long as my computer is in repair, I am forced to use such live emergency sessions for daily work.

---

### Post by TheFu on 2023-03-20
> **bhubunt said:**
> Believe you me, I would rather not use live sessions, but as long as my computer is in repair, I am forced to use such live emergency sessions for daily work.

Actually, you aren't.   Both **mkusb** and **Ventoy** [https://www.howtogeek.com/802328/how-to-boot-multiple-linux-distributions-with-ventoy/](https://www.howtogeek.com/802328/how-to-boot-multiple-linux-distributions-with-ventoy/) support using a flash drive with "persistent" storage between boots. **mkusb** is from an UbuntuForums active member. These modes really shouldn't be used longer than a few months, since weekly patching is still required to be network-secure and they aren't THAT bad initially.

OTOH, I've run for 5 days booting from a flash drive without any persistence after a boot drive failed on a server system. It ran in a degraded state with just a few core services running until a replacement HDD arrived and was installed.

A few friends use only flash storage for their MXLinux systems. The laptops they use don't have any internal storage at all. They both use Ventoy to manage the boot from the ISO and retain persistence.

Anyway, you have choices for persistence on flash storage.

As for time synchronization ... it is one of my nags with that other OS which can't keep time.  The exact same hardware, running Linux, has no issue maintaining correct time to msec accuracy, whereas that other OS on the same hardware would lose 20-35 minutes every day.  Had a problem with a number of laptops running that other OS not keeping time too. Eventually, I setup my own time server to avoid my public IPs being banned for ntpd abuse.  When systemd-timed became standard with Ubuntu, I found it didn't work well enough for my needs.  These days, well enough means, within about 30 seconds.  So, one of the first things I do on every new system is to dump systemd-timed and switch to chrony.  On 22.02, I know just installing chrony removes systemd-timed automatically. That's a good thing.  In prior releases (I'm not sure which), it was possible to end up with both tools trying to keep system time, fighting over which was correct. It wasn't good.

Chronyd.conf has reasonable defaults for most users.  I change the settings to point at my central time server, so all systems have the same time ... and logs are msec (or better), consistent.
```
$ sudo chronyc tracking 
Reference ID    : AC161604 (romulus)
Stratum         : 5
Ref time (UTC)  : Mon Mar 20 15:21:26 2023
[B]System time     : 0.000000055 seconds slow of NTP time
[/B]Last offset     : +0.000000854 seconds
RMS offset      : 0.000025099 seconds
Frequency       : 17.970 ppm fast
Residual freq   : -0.000 ppm
Skew            : 0.094 ppm
Root delay      : 0.019662751 seconds
Root dispersion : 0.005829429 seconds
Update interval : 64.8 seconds
Leap status     : Normal

```
Yep. more than accurate enough for pretty much anyone.  Of course, romulus, my time server, points to 3+ internet time servers.
Note, it is all UTC.  Getting things to be displayed in the local time zone using locale settings is really just setting the TZ environment variable.  The dpkg-reconfigure command sets the default TZ to be used by the system, but internally, it should still be using UTC to avoid all sorts of issues.

---

### Post by bhubunt on 2023-03-27
Thanks for the code.

---

