---
title: "Cannot load certain websites in 12.04"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by efinlaw on 2013-01-22
Ok first off, I am not very experienced with linux. I have only just installed it today so bare with me if I am unsure how to access certain things and mess with the terminal. I installed the Ubuntu 12.04 64-bit flavor using a bootable USB. I went through the installer and chose to boot alongside my Windows 7 OS. Everything installs fine, im able to access the internet but I cannot get on websites such as Facebook and some of my university sites. I have tried getting on these sites using Firefox, Chrome, and Chromium and all give me the same problem. I don't believe this is a network problem as I have no problem getting on any website while in Windows 7. I have tried searching for a solution to this problem for a while and it seems that many others have the same issues but it appears no real fix has been found.
 
I figured making a new post about this would not only put out the specifics of my problem but also get knowledge of this issue circulating a bit more for others having similar problems.
Does anyone have an idea what could possibly be the issue here? Thanks.

---

### Post by Lightning Dragon on 2013-01-22
Hello,

I can try my best to help you.

Can you take a picture of the access problem or describe what it does? Does it simply not let you visit the sites with a given report, or does the page never load?

To take pictures in Ubuntu (since you said you are new?), go to the left screen and click the Dash button (the computer searching "engine") that looks like [this]("http://s2.postimage.org/mgmfzt59x/Screenshot_from_2013_01_22_00_53_50.png")   (< clickable, also, mine is a different color because I changed themes so don't worry about it) and type in "screenshot". You should see this;

[http://s1.postimage.org/59lkv2wbj/Untitled.png](http://s1.postimage.org/59lkv2wbj/Untitled.png)

Click it and then take a picture of the problem  you encounter in Firefox, i.e if it gives a "connection" error or a "blocked site" error. Next upload the file to a place like [postimage]("http://postimage.org/index.php?") and then post the URL here for us to see. Or, you can write down the problem and post it here.

Also, go to the preferences in Mozila (or the browser of you choice) and go to Advanced > Network > settings and make sure no proxy is on. It think this is definitely a security issue, at least without seeing the actual problem.

---

### Post by audiomick on 2013-01-22
It might be a Flash problem, I think.

Did you install the Ubuntu-restricted-extras package?

Read about it here
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")


There is a link to an similar article specifically referring to flash a bit of the way down, under the heading "web".

---

### Post by Warren Hill on 2013-01-22
Most likely issue is flash and the installing the restricted extras package should fix it.  See previous post for link

If not can you provide a link to some of the sites that don't work.  It may give us a clue why.

---

### Post by Bucky Ball on 2013-01-22
> **Warren Hill said:**
> 
If not can you provide a link to some of the sites that don't work.  It may give us a clue why.

> **efinlaw said:**
> ... Facebook and some of my university sites.

There's a few. 

Are there others we can test like Facebook? Facebook does lag sometimes and I can't get on either. That is their end, not mine. 

Uni servers not down for maintenance?

---

### Post by efinlaw on 2013-01-22
I have installed the restricted extras package but unfortunately there was no change. Here is a screenshot of what happens when I try to access some of these sites. There is no error message, the page simply does not load. As you can see, the "Welcome to Facebook" greeting appears in the tab but just shows the loading wheel and does not actually connect. I have waited to see if maybe it is just slow but it never loads.

[http://postimage.org/image/mqojph21f/](http://postimage.org/image/mqojph21f/)

I also tried changing my firefox networks settings to no proxy and still nothing.
Here are a few other sites that do not work:
[http://ecampus.wvu.edu/](http://ecampus.wvu.edu/)
[http://masteringphysics.com/](http://masteringphysics.com/)
[https://twitter.com/](https://twitter.com/)

EDIT: Twitter now loads but only partially.  ie. images for reply, favorite, etc are showing up as boxes

---

### Post by audiomick on 2013-01-22
There is something wrong with those last three links. They all lead back to a page here where I am logged out.

---

### Post by efinlaw on 2013-01-22
Sorry, should be good now.

---

### Post by steeldriver on 2013-01-22
sometimes these connection issues on an otherwise working connection are due to packet fragmentation / blocked ICMP echo requests (aka a routing 'black hole') - can you try this in a terminal 

```
ping -s 1472 -c 4 -M do google.com
```and post back the results please?

---

### Post by efinlaw on 2013-01-22
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 25.892/31.420/41.053/5.767 ms

There was no packet loss for Facebook either

---

### Post by steeldriver on 2013-01-22
OK thanks looks like we can rule that one out then

---

### Post by efinlaw on 2013-01-22
Is it safe to say that this is not a network issue? It's just strange that only certain sites don't load and without an error message too. I'm going to try downloading another browser and see what happens.

EDIT: I tried it in rekonq and the same thing happens so it's not a browser issue.

---

### Post by Lightning Dragon on 2013-01-22
Hello,

It *might* be a security issue on firewalls, networking, your provider or your router. We'll need to rule it out, first. 

Go to your internet settings and make sure you are accepting cookies, java etc etc and see if you have the browser's default proxy on. If all seems well, test your security level by visiting this site;

[http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/)

I want to see if something else works for you, too. Next, go into your settings. Preferences -> Privacy -> Exceptions and try adding one or two of the sites you can't go to to the "exceptions" list. Confirm it, exit out and restart Firefox to see if you can visit one of the sites you added. 

Reference image; [http://s14.postimage.org/9xscmmfpt/settings.png](http://s14.postimage.org/9xscmmfpt/settings.png)

If that doesn't do anything, try access sites through a proxy like this one here; [http://www.hidemyass.com/proxy-list/](http://www.hidemyass.com/proxy-list/)

Sadly reinstalling seemed to fix the problem for [this user]("http://ubuntuforums.org/showthread.php?t=2107394"). But there has to be a way to fix it, so I would hold off on that for now.

---

### Post by efinlaw on 2013-01-22
Hi,

Sadly, your first link doesn't even load for me. Don't know if that says anything. I tried adding the sites to the exceptions list but that doesn't work for me either. However, when I close my settings and go back into them, they do not save and it reverts back to this setting: [http://postimage.org/image/zea39oxot/](http://postimage.org/image/zea39oxot/).

I am able to access the sites through the proxy you posted, but of course their appearance is not very pretty. 

I'm not sure if reinstalling would help or not. I tried installing ubuntu using wubi before and it gave me the same problems. This is why I wanted to try to boot from the actual .iso file on its own partition, which is what I'm running on now, but it has not made any difference.

---

### Post by Lightning Dragon on 2013-01-22
Hello,

That is odd. Firefox is supposed to remember your settings. See if accessing the "Use custom settings for history" has all the options you checked still there. To be sure, check something not checked (or uncheck), close it and reopen to see if it is still in works. If they aren't, then not only do you have a security/permissions denial with your connection, but some problem with Firefox. 

So using a proxy makes it so you can visit the sites you normally cannot? Yes, this is definitely a network form of problem. It is either how you have the network set up in Ubuntu/Distro to disallow you access, or your provider did so. But I'm going to assume it **isn't** the later.

Do you think you could get a screenshot of your network settings within your distro for us (_**But remember to block out any sensitive information like IP address etc etc!**_)? You could also, within Network settings, put on an *automatic proxy* and see if that will allow you through. Next, type in "Firewall" into your distro's search engine (Dash for Ubuntu) and set it off and see if you can access the sites without the need of the proxy.

---

### Post by efinlaw on 2013-01-23
Which network settings do you mean? Sorry, I'm still a little new to this. 
This? [http://postimage.org/image/3z6b57603/](http://postimage.org/image/3z6b57603/)
Also, nothing comes up when I type in Firewall. Do I need to download an app?

---

### Post by Lightning Dragon on 2013-01-23
Hello,

> **efinlaw said:**
> Which network settings do you mean? Sorry, I'm still a little new to this. This? [http://postimage.org/image/3z6b57603/](http://postimage.org/image/3z6b57603/)

Also, nothing comes up when I type in Firewall. Do I need to download an app?

No need to apologize. :)

Yes, I meant that. Is there other options/tabs available in the network settings? Or when you open network settings is that the _only_ thing that appears? To the left there should be a clickable tab called "Network Proxy". Tell me what it says inside to the right after clicking into it. If it says "none", then try clicking on the dropdown box and using "automatic proxy" and see if you can load the sites. If not, switch back to the default setting it had which should be "none".

I do not remember having to install anything to edit the Firewall. Hmmm. Go to the Software Center or Synaptic Manager and see if there are any packages to download to access the Firewall.

---

### Post by black veils on 2013-01-23
firewall tool is gufw in synaptic package manager, its probably called something like "easy firewall" in software center.

---

### Post by efinlaw on 2013-01-23
I changed the proxy settings to automatic and asked for a configuration URL, but it had a message saying it was not needed. I tried with those settings, nothing happened.

I installed something called Firewall Configuration and it gives me this:
[http://postimage.org/image/q4yhsokcl/](http://postimage.org/image/q4yhsokcl/)

It was already set to 'off' when I opened it.

---

### Post by Lightning Dragon on 2013-01-23
Hello,

It will need a configuration URL for it to work. Does it give you a place to get the URL, or?  As for the Firewall, try setting it to "on" and "allowing" all of it through.

And thanks for the name of the firewall download,  black veils. I couldn't remember what it was called.

---

### Post by efinlaw on 2013-01-23
Here is exactly what is on the screen in my proxy settings:
[http://postimage.org/image/nn9vugd29/](http://postimage.org/image/nn9vugd29/)

As for letting everything through the firewall, no results. 

BTW, another person I live with has Ubuntu installed and is running on the same network and had no problems from the beginning. I just don't understand why my default settings would be different from his.

---

### Post by Lightning Dragon on 2013-01-23
Hello,

Something is up with your install. Instead of Automatic, make it "manual" and add the following to the correct places--don't worry, I'll tell you where.

First, add this "184.73.185.224" to the "HTTP Proxy" bar, which should be the first one. Next, right next to it (to the right) change "port" to "8080" if it isn't already. It should look like this;

[http://s8.postimage.org/59ek5cw85/Screenshot_from_2013_01_23_15_45_39.png](http://s8.postimage.org/59ek5cw85/Screenshot_from_2013_01_23_15_45_39.png)

However, feel free to change the current address to "207.182.158.171" with a port of "80", it might be faster than the last port. If it works, you can check out a list of ports and IPs to use from this list;

[http://www.hidemyass.com/proxy-list/search-225511](http://www.hidemyass.com/proxy-list/search-225511)

See this post [http://ubuntuforums.org/showthread.php?t=1894484&page=3](http://ubuntuforums.org/showthread.php?t=1894484&page=3) and look at his solution. He went into his Network settings and added his DNS and info. If your friend shares the same network, you can check out his settings so you can use it on your own machine. (:

For a permanent fix to it if all else fails--since the Firewall and Networking settings is *obviously* perfectly fine both on your end and the provider's end--is to do a fresh install with an internet connect hooked up during it. Possibly a newly burned DVD iso, too.

---

### Post by efinlaw on 2013-01-23
VICTORY! :D

Using the second address you gave me, I am now able to access all of the sites that I mentioned. Although they do run a little slow, it is a tremendous improvement from what I was dealing with before.

Later I will try to use the other method and copy my friend's settings to see if I gain any further improvement. If I do, Ill post it here, but for now I'll mark this as 'solved' as there have been plenty of suggestions posted.

Thanks so much, Lightning, for your persistence in helping me with this problem and thanks to everyone else too. I appreciate it. Have a nice day.

---

### Post by Lightning Dragon on 2013-01-23
Hello,

You are welcome, glad I could be of assistance, even if it was just a smidgen. Be sure to consult the forum again if you need help with something. 

As for speed, the link I gave is constantly updated with newer IP addresses and ports. Each will have different speed connections and whatnot. You can always switch between them. The bad news with this is that you would have to manually update it through the Network Settings again. Perhaps running a IP changing software through WINE might also be a solution.

I figured that if you try the DNS suggestion, you might want some links about configuring the settings;

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)
[https://help.ubuntu.com/10.04/serverguide/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/network-configuration.html)

However, I would not mark this solved if I were you. The issue is not solved, just that a workaround to the problem was used. If you keep it unsolved, perhaps staff or another more knowledgeable person might see the thread and know why you are restricted the way you are and have a solution for you.

Have a nice day too, and I hope by some miracle a reboot fixes everything for you.

---

### Post by Bucky Ball on 2013-01-23
> **efinlaw said:**
> 

Later I will try to use the other method and copy my friend's settings to see if I gain any further improvement.

Good plan. Glad you're getting somewhere. ;)

---

### Post by efinlaw on 2013-01-24
So, I was searching some more for some possible solutions. Mostly in the thread Lightning posted about changing the DNS settings.

I opened up /etc/resolv.conf
The nameserver listed is 127.0.0.1

However, my Windows 7 DNS server is listed as 10.13.18.1

nameserver and DNS server are the same thing, correct? Could this possibly be the issue? If so, how would I go about changing the nameserver? I read that if you edit /etc/resolv.conf , your settings will be overwritten after a reboot. I have already tried manually putting in my settings from Win7 in the Network Manager under IPv4 but the network still has problems and the nameserver stays as listed above.

---

