---
title: "Connect to Wireless Systems"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by JerryC on 2013-02-08
We are spending the winter in our RV and occasionally move from one RV park to another.  Normally when you register at the park, they give you the wireless password if there is one.  We have been in three different RV parks this week and two of them would not let Ubuntu sign on.  On these occasions my Windows 7 (dual boot with Ubuntu) and my phone were both able to get on the wireless system so I know I have the correct password.  I have played with different settings for security with no luck.  The setting for my phone is WEP (which is working).  Any ideas for what to check next?  I don't want to be stuck with Win 7 for the next month.

JC

---

### Post by DuckHook on 2013-02-08
> **JerryC said:**
> I don't want to be stuck with Win 7 for the next month.
...heh heh. That bad, huh?

Let's see... it's been so long since I've even looked at WEP that I'm not familiar with it anymore.

[Here]("http://colekcolek.com/2011/07/11/connect-to-wireless-network-wep-in-ubuntu-11-04-using-command-line/") is a link to setting up a WEP interface using the command line. I've no idea if it works (it was written for 11.04) because I've no WEP router to test it on.

Before going there, have you tried going through Network Manager? On Ubuntu 12.04, creating a new wireless connection gives you the option under "Wireless security" to define either 40 bit or 128 bit WEP. Is this how you've tried connecting? If not, provide full step-by-step description of prior attempts. You may need to ask the RV park administration which level of WEP they use.

Re: Security

Just FYI, WEP is worse than useless because it gives the illusion of security while actually providing none. A script kiddy with an obsolete laptop can break WEP in a few minutes. In fact, there are downloadable apps that will do it for you with three clicks of a mouse. Even this is unnecessary because everyone on a wireless network shares the same encryption key anyway, which makes your WIFI link basically a node on a party line. The only proper way to really secure your connection is to tunnel back to a secure network and do all of your work through the tunnel. You can do this with either a VPN or SSH. SSH is "easier" but VPN is more versatile. There are numerous VPN providers who operate as subscription services. You can also tunnel back to your home if you set up a VPN server. This last requires more technical savvy, but saves money over the long term.

I don't even know why public hotspots bother with encryption other than to prevent people off the street from getting free access. Don't see why this would be an issue in an RV park, as most of them are so remote that the only people using it would be their clientele.

If interested, one of the best security primers I've ever read is on this very forum and located [here]("http://ubuntuforums.org/showthread.php?t=510812").

---

### Post by mapes12 on 2013-02-08
The campsite wifi network has no idea if your connecting with Ubu, windoze, a Mac or whatever. Sounds to me as if there is a problem with your Ubu network settings. Does Network Manager connect to other wifi locations OK?

---

### Post by JerryC on 2013-02-11
DuckHook -

I tried doing the terminal thing suggested by the link.  The first step was:

$ iwconfig
You will see wireless adapter as wlan0 or ath0 which depends on what driver is installed
 I made the assumption ath0 was a typo and used eth0.  The next instructions were:

Execute the following command to apply ESSID, network key, channel, and mode:
$ sudo iwconfig wlan0 essid yantoknuk-singtel
$ sudo iwconfig wlan0 channel 6
$ sudo iwconfig wlan0 key ngumbahkucing
$ sudo iwconfig wlan0 mode managed

When I tried the first one I got the following results:

jc@jc-Studio-1749:~$ sudo iwconfig eth0 essid palms-rptr1
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; Operation not supported.

Any ideas?

JC

---

### Post by JerryC on 2013-02-11
Mapes12 -

Yes, I have connected to 2 out of 4 wireless networks since we started this trip.  Last summer's trip, I connected to all 10 or 12 networks.  My guess is an update has messed with me but I don't remember seeing any updates having to do with wireless.

JC

---

### Post by Rex Bouwense on 2013-02-11
We are also full time RVers and have connected to possibly 200 different RV wifi networks since 2009 using Ubuntu and then Lubuntu (some password protected and some open) without a problem.  Mapes 12 is 100% correct.  The RV Park wifi system doesn't care what OS you are using.

---

### Post by landersohn on 2013-02-11
What wireless card are you using? There are a bunch of threads out there related to broadcom cards with connection problems. The broadcom drivers seem to have a problem with WAP2, so your problem may depend on what security the wirelsss network has been set up with which is why it sometimes works and sometimes doesn't.

In my experience, broadcom drivers worked kinda ok in 10.04 and for me completely stopped working in 12.04. So if you upgraded your ubuntu you may have a driver that doesn't work right.

My workaround was to buy a 10$ buffalo nano USB wireless dongle:worked like a charm out of the box. Dlink dongle worked also but has a larger form factor. Other's I tried (e.g. trendnet) had the same symptom as my build-in wireless: saw the network but could not connect.

---

### Post by DuckHook on 2013-02-11
The example from the linked post was specific to the poster's own network. You have to change:

1. the "ESSID" to that of your RV site's,
2. the "channel" to the one your RV site is actually using,
3. the "key" to that of your RV site's.

Before embarking on the command line, which should always be only a last resort for new users, did you try using the graphical Network Manager? I don't believe that you ever answered my question as to why you weren't using the easier method.

At this point, need far more info about your system. What make, model and wireless chipset is it? How did you install the wireless driver? If easier, post back with results to the following commands:

```
sudo lshw -short
``````
lspci -vk | egrep -iA7 'eth|wlan'
``````
ifconfig
``````
iwconfig
``````
cat /etc/modules
``````
grep blacklist /etc/modprobe.d/blacklist.conf
```You will need to open a terminal, then copy and paste these commands into terminal. The output will be considerable, so for easier reading, highlight each result and wrap it in a "code" box just like I have by using the hash (#) character at the top of the posting box. Please give each output its own box.

---

### Post by JerryC on 2013-02-13
[QUOTE=DuckHook;12505323]The example from the linked post was specific to the poster's own network. You have to change:

1. the "ESSID" to that of your RV site's,
2. the "channel" to the one your RV site is actually using,
3. the "key" to that of your RV site's.

Before embarking on the command line, which should always be only a last resort for new users, did you try using the graphical Network Manager? I don't believe that you ever answered my question as to why you weren't using the easier method.

I understand that. The palm-rptr1 is the ESSID I'm trying to connect to.  I'm not afraid of the command  line.  I started working with PCs in 1982 with DOS.  I just don't know what commands to use with linux.  I don't know how to discover what channel they are using.  I have used the graphical Network Manager.  It doesn't seem to show a lot of information.  Assuming I have figured out how to use it.  I will work on the rest of the posting suggestions today but it may be slow.  I am pretty sure they are trying serve 158 RV sites through a DSL connection.

JC

---

### Post by DuckHook on 2013-02-13
> **JerryC said:**
> I'm not afraid of the command line. I started working with PCs in 1982 with DOS.

Familiarity with the CLI is good. Most of the people posting in the Absolute Beginners section are not at all familiar, so it becomes habit to assume no familiarity. That said, I go back before the PC days to Big Iron and have become quite familiar with Linux over the years, but even I try to stick with graphical tools if possible. They are simpler and, though lacking many options, they allow less to go wrong.

> I don't know how to discover what channel they are using.If connection works through Windows, you should be able to find both ESSID and channel there. I've never worked with W7, so can't direct you. You may need to ask RV admin, though there is a good chance they won't know.

>  I have used the graphical Network Manager. It doesn't seem to show a lot of information.When setting up a new connection, one of the options in Network Manager>Security tab is two types of WEP key. On mine they are 40-bit and 128-bit. Was this option available in yours and, if so, what did you enter?

> I will work on the rest of the posting suggestions today but it may be slow. I am pretty sure they are trying serve 158 RV sites through a DSL connection.I imagine you are correct. Usually the case in remote locations. If it helps, just provide requested info without attaching output (I suspect you are doing this through Windows). Of course, output is preferable, but I know it's not always possible. We are looking for type of wireless chipset and drivers (if any) that Ubuntu has loaded to try to make it work. It is difficult to get driver info without the commands, but type/version of wireless chipset should be available once again by looking at the proper Windows system info page. This may be enough of a start.

---

### Post by JerryC on 2013-02-13
I have good news.  I remembered I have an external wireless antenna for use in RV parks where I am some distance from an antenna.  I didn't think of it because I have a good signal without it. I thought it had it's own driver, so I tried it, and lo and behold, I now have linux online for the first time in over a week.  I will continue to work with your suggestions but it may be a while before I get back to you; I have quite a bit of catching up to do.

There is no excuse for DSL here.  We are in the middle of downtown Aransas Pass, TX, and have cable TV service to the park.

JC

---

### Post by DuckHook on 2013-02-13
If it now works, my recommendation is to leave well enough alone and no need for further tinkering.

Happy Ubuntuing!

---

