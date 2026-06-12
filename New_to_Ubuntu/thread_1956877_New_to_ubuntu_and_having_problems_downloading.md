---
title: "New to ubuntu and having problems downloading"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by RvShaitan on 2012-04-11
I tried to download chromium in 11.10 ubuntu 64 through the software center. It takes forever to download and has yet to finish after almost 20 minutes. I tried to update my repository with the same results. I am brand new to using ubuntu and wonder if maybe I am doing something wrong. I am at the point where I want to try reinstalling to see if that fixes it. I loaded up youtube in firefox and it loaded fine. (took an eternity to get flash to download but videos stream fast) My internet speed seems ok there. I tried to change my source for the update manager with the same problem. It took all night to get through the updater and I am still unsure if my repository is right. 

I had windows installed before this in a dual boot and when I installed ubuntu on a seperate partition on an external drive the update repository zipped by fast. I decided I liked ubuntu and formated my partitions and installed ubuntu 11.10 alone. This is when the problems started.

As I said, I am really new here and have no idea what I am doing wrong. Any advice for a new but hopeful ubuntu user? Apt-get seems to just sit there anytime i use it or to run super slowly.

ps. I hope this isn't already answered. I looked around the forum alot but I couldn't find any answers that were effective.

---

### Post by JoshuaRL on 2012-04-11
What kind of computer do you have?

What version of Ubuntu are you running?

Are you trying to do a full version upgrade?

Not that it's necessary, but would it work to do a full reinstall?

---

### Post by RvShaitan on 2012-04-11
**What kind of computer do you have?**

I have a Intel® Core™2 Quad CPU Q6600 @ 2.40GHz × 4 with 6 gigs of ram. A 500 gig internal drive that I installed ubuntu to and a 1 tb drive with random media stuff. 

**What version of Ubuntu are you running?**

The version is a fresh install of Ubuntu 11.10 64 bit.
[B]
Are you trying to do a full version upgrade?[/B]

I am actually trying to format my drive completely and just run ubuntu. It worked fine on my previous dual boot. (I did notice that the previous ubuntu 11.10 install with updated repository is still showing on my external 1 Tb drive and startup.)

**Not that it's necessary, but would it work to do a full reinstall?**

I can do a full reinstall easily yes. Is that the best option? It seems to work fine for me. It just hates to download any repository information or packages.


If you need anymore info let me know!

---

### Post by JoshuaRL on 2012-04-11
> **RvShaitan said:**
> **What kind of computer do you have?**

I have a Intel® Core™2 Quad CPU Q6600 @ 2.40GHz × 4 with 6 gigs of ram. A 500 gig internal drive that I installed ubuntu to and a 1 tb drive with random media stuff. 

**What version of Ubuntu are you running?**

The version is a fresh install of Ubuntu 11.10 64 bit.
[B]
Are you trying to do a full version upgrade?[/B]

I am actually trying to format my drive completely and just run ubuntu. It worked fine on my previous dual boot. (I did notice that the previous ubuntu 11.10 install with updated repository is still showing on my external 1 Tb drive and startup.)

**Not that it's necessary, but would it work to do a full reinstall?**

I can do a full reinstall easily yes. Is that the best option? It seems to work fine for me. It just hates to download any repository information or packages.


If you need anymore info let me know!

My apologies, I somehow missed the "Chromium" part of the OP, and thought you were trying to do a version upgrade of the OS.  My bad.

Now, can you run the following in the terminal?  I'd like to see what happens:

```

sudo apt-get update
sudo apt-get install chromium-browser

```

---

### Post by RvShaitan on 2012-04-11
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

No problem! I hope this helps. I hope I can figure out the problem.

---

### Post by JoshuaRL on 2012-04-11
Okay, first make sure USC and/or Synaptics are shut down and try again.

What that error is saying is that only one program at a time is allowed to use the sudo (root) access.  So no go.

---

### Post by RvShaitan on 2012-04-11
Ok I figured that as well. I ended up having to reboot to get it to work but it appears to be going through the repositories fine but very slowly.

Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en [3,165 kB]     
53% [5 Translation-en 1,658 kB/3,165 kB 52%]               241 B/s 1h 44min 13s

I can leave this going if you think this time it'll work. I let this go throughout the night last night and seemed to still fail. Is there a way I can verify that the repository is in there ok? Btw, my posts are really requiring alot of reloads to stick on the forum. I dunno if that is a related issue.

---

### Post by alphacrucis2 on 2012-04-11
What sort of network connection do you have? Possibly getting transmission errors.


Edit. I should also ask. Is it just the Ubuntu repos that are going slow, or general internet browsing as well. If it is just the repos then try a different mirror.

---

### Post by JoshuaRL on 2012-04-11
> **RvShaitan said:**
> Ok I figured that as well. I ended up having to reboot to get it to work but it appears to be going through the repositories fine but very slowly.

Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en [3,165 kB]     
53% [5 Translation-en 1,658 kB/3,165 kB 52%]               241 B/s 1h 44min 13s

I can leave this going if you think this time it'll work. I let this go throughout the night last night and seemed to still fail. Is there a way I can verify that the repository is in there ok? Btw, my posts are really requiring alot of reloads to stick on the forum. I dunno if that is a related issue.

Nah, the repos are still there and are flying for me.  But my mirror is "http://us.archive ....." so they're different places.  If I remember correctly your internet browsing, even streaming was going fine (if not please correct me) so I doubt that your internet is the issue.  

Using the directions here, you will want to pick new mirrors for your updates to flow through:
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Here is where you will find a list of all approved Ubuntu Mirrors.  Pick one nearest to you:
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by RvShaitan on 2012-04-11
This is the type of connection I have and it's wireless. Is this an issue?  I have a 10 meg download speed btw, but it seems my flash didn't install properly and I can't get it again to test my speed to see if it's still working correctly.

00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8221]
    Kernel modules: forcedeth

@Joshua I am also trying to use different mirrors. I get these errors. Sometimes others.

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe Translation-en
Fetched 72 B in 47s (1 B/s)
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>



Anything I try to do through USC freezes at installing and just sits there progressing for eternity. I think it has gotten worse. (lol)

---

### Post by alphacrucis2 on 2012-04-11
> **RvShaitan said:**
> This is the type of connection I have and it's wireless. Is this an issue?  I have a 10 meg download speed btw, but it seems my flash didn't install properly and I can't get it again to test my speed to see if it's still working correctly.

00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8221]
    Kernel modules: forcedeth

@Joshua I am also trying to use different mirrors. I get these errors. Sometimes others.

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe Translation-en
Fetched 72 B in 47s (1 B/s)
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>



Anything I try to do through USC freezes at installing and just sits there progressing for eternity. I think it has gotten worse. (lol)

Type in ifconfig and check for any errors listed against the wlan0 (wireless) interface. The interface you listed above appears to be the wired ethernet conroller. You can use:

```
sudo lshw -C network
```

To display all network hardware. The wireless should be listed as well as the ethernet.

---

### Post by RvShaitan on 2012-04-11
Oh, I see! I got the wireless info here then. It appears to be ok though I really am unsure. I notice a bit of a delay on certain pages that feels like extended dns lookups. Does it look good to you?

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:e3:46:72  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:37cd:9450:21e:e5ff:fee3:4672/64 Scope:Global
          inet6 addr: fe80::21e:e5ff:fee3:4672/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:107977835 (107.9 MB)  TX bytes:7493823 (7.4 MB)


  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:1e:e5:e3:46:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.0.0-12-generic firmware=0.29 ip=192.168.1.69 link=yes multicast=yes wireless=IEEE 802.11abgn

---

### Post by alphacrucis2 on 2012-04-11
Do you have a facility for connecting via ethernet (wired) cable connection. If so then it would be worth a try. If wired works ok then it would pin the problem down to the wireless - possibly a driver issue. 


Hmm a quick search turns up some issues with the rt2800usb. It might pay to read through some of this threads about this device. Eg

[http://ubuntuforums.org/showthread.php?p=11431184](http://ubuntuforums.org/showthread.php?p=11431184)


I wouldn't try anything until digesting the whole thread as there seems to be several different things tried which may or may not work. Although one easy thing to try that is suggested is to try disabling ipv6. That can be easily turned on or off via network manager. I can't offer anything for sure myself as I don't have a device that uses this driver.

---

### Post by RvShaitan on 2012-04-11
I believe that forum link helped me. I tried the changes with little effect till I rebooted and now with a more local mirror everything seems faster. The repository update was very fast and now I don't feel a 'dnsy' type hesitation before a webpage loads. Chromium was pretty snappy and installed before I knew it. I appreciate the help from both of you and I will mark this as solved. Thanks again to both of you!

---

