---
title: "Is there a way to block ads on Firefox without installing an extensions?"
date: 2015-10-27
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-10-27
Hello guys  Just as the title suggests, is there an alternative way to disable and block ads while browsing? Thank you

---

### Post by buzzingrobot on 2015-10-27
Search for something like "using custom hosts file to block ads" and you'll find discussion of how to use that approach.  I.e, block traffic from a host serving ads.

---

### Post by remmas-sido on 2015-10-28
> **buzzingrobot said:**
> Search for something like "using custom hosts file to block ads" and you'll find discussion of how to use that approach.  I.e, block traffic from a host serving ads.
Here in this forum, or Google?

---

### Post by remmas-sido on 2015-10-28
> **buzzingrobot said:**
> Search for something like "using custom hosts file to block ads" and you'll find discussion of how to use that approach.  I.e, block traffic from a host serving ads.

Luckily, I have found [http://someonewhocares.org/hosts/](http://someonewhocares.org/hosts/) it gives  instructions to all Operating Systems when it comes to Linux it says:
For Linux, Unix, or OS X place this file at "/etc/hosts" or on some
#    systems at "/private/etc/hosts". You will require root access to do
#    this. Saving this file to "~/hosts" will allow you to run something
#    like "sudo cp ~/hosts /etc/hosts".
# Ubuntu users who experience trouble with apt-get should consult
#    [http://ubuntuforums.org/archive/index.php/t-613521.html](http://ubuntuforums.org/archive/index.php/t-613521.html)
So can you help understand how the process go, because I don't want to  do it in the wrong way if I will do it I want to do it in the right way.

---

### Post by buzzingrobot on 2015-10-28
> **remmas-sido said:**
> Here in this forum, or Google?

Google or another search engine.

The existence of a hosts files dates from before the internet, when a computer may have been on a local network with only a few other machines. Computer names were resolved to IP addresses by simply looking them up in a small text file on a machine, the hosts file.  

A hosts file can be used to link the names of ad servers to the IP address of your own machine. So, for example, a browser would resolve something like "BigAdServer.com" to 127.0.0.1, which is your computer, not to the actual IP address of that server. As a result, you get no ads served from BigAdServer.com.

Access to any server can be blocked this way, not just ad servers. In addition, access to the servers is blocked for any software, not just a browser.  Any content from those servers, ads or not, will be blocked.

Setting up this approach is conceptually simple:  Collect the names of the servers you want to block, create the hosts file in the correct format that maps each server name to your PC's IP address, move it into place in /etc, reboot and you're good to go. 

Whether or not this is a better approach than using an extension is your choice. Hosts files would need to be updated to include new ad servers that come into use. (When you see ads that very likely means that server is not in your list.  So you get to find the server name and add it. Or rely on lists provided elsewhere online.)

Ad blocking extensions, I believe, often reformat a page in memory to remove blank spaces -- where the ads would have been -- before the browser displays it.  That increases the memory used by the extension.

---

### Post by vasa1 on 2015-10-28
> **buzzingrobot said:**
> ... Ad blocking extensions, I believe, often reformat a page in memory to remove blank spaces -- where the ads would have been -- before the browser displays it.  That increases the memory used by the extension.
Not really a practical concern, is it?

---

### Post by SeijiSensei on 2015-10-28
> **vasa1 said:**
> Not really a practical concern, is it?

Hasn't affected my browsing in the least, and I've been using AdBlock for years.  Now I'm using [uBlock Origin]("https://addons.mozilla.org/en-us/firefox/addon/ublock-origin/").

Host files are an absurdly labor-intensive method for ad blocking.  Are you really going to maintain the database of sites to block more reliably than a third-party like EasyList?

---

### Post by vasa1 on 2015-10-28
> **SeijiSensei said:**
> ... Now I'm using [uBlock Origin]("https://addons.mozilla.org/en-us/firefox/addon/ublock-origin/").

Host files are an absurdly labor-intensive method for ad blocking.  Are you really going to maintain the database of sites to block more reliably than a third-party like EasyList?

I switched from AdBlock Plus to ublock origin a few months ago.
> EasyList, Peter Lowe's Adservers, EasyPrivacy and Malware domains are enabled by default when you install uBlock&#8320;. Many more lists are readily available to block trackers, analytics, and more. Hosts files are also supported.Source: [https://github.com/gorhill/uBlock](https://github.com/gorhill/uBlock)

---

### Post by buzzingrobot on 2015-10-28
> **vasa1 said:**
> Not really a practical concern, is it?


I thought, perhaps, the OP was motivated to avoid using extensions due to memory constraints. Firefox recently apparently enabled Adblock to use less memory, but I recall it adding 100mb or so per page here not that long ago.

---

### Post by kurt18947 on 2015-10-29
I seemed to having problems with adblock plus blocking more than it should resulting in desired content not being displayed. i uninstalled adblock and installed Bluhell Firewall. It doesn't appear to be a firewall in the usual sense.  So far so good.

---

### Post by mystics on 2015-10-29
> **buzzingrobot said:**
> Ad blocking extensions, I believe, often reformat a page in memory to remove blank spaces -- where the ads would have been -- before the browser displays it. That increases the memory used by the extension.

Not all ad-blockers remove the blank spaces. Even if they do, I'd imagine the usage is small enough that anyone running into memory issues as a result would be better served not using Firefox all together and just going with a more lightweight browser.

> **kurt18947 said:**
> I seemed to having problems with adblock plus blocking more than it should resulting in desired content not being displayed. i uninstalled adblock and installed Bluhell Firewall. It doesn't appear to be a firewall in the usual sense.  So far so good.

What do you mean it was blocking stuff it shouldn't have? Was it blocking non-ad content or was it just blocking ads on sites you want to support?

---

### Post by kurt18947 on 2015-10-29
> **mystics said:**
> 

What do you mean it was blocking stuff it shouldn't have? Was it blocking non-ad content or was it just blocking ads on sites you want to support?

I was having problems with sites' function being impaired. The site wasn't totally blocked but functions built into the site weren't functioning. It's also possible I've messed with one too many things in this install :oops:

:p

---

### Post by SeijiSensei on 2015-10-29
I don't have that problem with Adblock or its successors.  I do encounter it with Ghostery, especially on commercial sites with video.  The easy solution is turn off blocking temporarily, reload the site, and see if that fixes the problem.  If you visit any major news or television sites, Ghostery will report it is blocking as many as 20 or more little bugs designed to track you across the Internet.  The front page of nytimes.com has twelve at the moment; on msnbc.com, the number is 59!

---

### Post by vasa1 on 2015-10-30
> **buzzingrobot said:**
> I thought, perhaps, the OP was motivated to avoid using extensions due to memory constraints. Firefox recently apparently enabled Adblock to use less memory, but I recall it adding 100mb or so per page here not that long ago.I guess that depends on what one blocks or doesn't. I didn't notice memory bloat when using Adblock Plus for quite a few years.

---

### Post by buzzingrobot on 2015-10-30
> **vasa1 said:**
> I guess that depends on what one blocks or doesn't. I didn't notice memory bloat when using Adblock Plus for quite a few years.

My hardware has more than enough memory not to worry about "memory bloat".  I block as much as possible and, out of curiosity, noticed a roughly 100mb hit per page in Firefox, or Chrome. 

Questions from users with older hardware with only 1-2 gigs of RAM are common here. Contemporary software products, FOSS and commercial, are not designed to run well, if at all, on such outdated hardware. For example, here, at the moment, with only two tabs open, Firefox is at 470 megs. We owe it to users of outdated hardware to help them find so-called "lightweight" software they can actually use, when possible.  But we need to be clear it's not a magic bullet, usually comes at the cost of reduced convenience and capability and that Linux doesn't exist to be that "skinny" platform for tired machines.

---

### Post by vasa1 on 2015-10-30
> **buzzingrobot said:**
> My hardware has more than enough memory not to worry about "memory bloat".  I block as much as possible and, out of curiosity, noticed a roughly 100mb hit per page in Firefox, or Chrome.I have 4GB RAM, but I note RAM usage carefully all the same. I'm pretty sure I didn't suffer a 100MB hit "per page" with Firefox. 

> **buzzingrobot said:**
> Questions from users with older hardware with only 1-2 gigs of RAM are common here. Contemporary software products, FOSS and commercial, are not designed to run well, if at all, on such outdated hardware. For example, here, at the moment, with only two tabs open, Firefox is at 470 megs. We owe it to users of outdated hardware to help them find so-called "lightweight" software they can actually use, when possible.  But we need to be clear it's not a magic bullet, usually comes at the cost of reduced convenience and capability and that Linux doesn't exist to be that "skinny" platform for tired machines.I won't get into yet another futile FOSS/Linux argument but I'm all for lighter solutions as a matter of principle.

I don't quite know what you mean by Firefox is at 470 megs but with Firefox open (two tabs: this and Ask Ubuntu), and Dropbox, I see:
```
04:30 PM ~ $ free -m
             total       used       free     shared    buffers     cached
Mem:          3916       1499       2417         73         67        996
-/+ buffers/cache:        435       3480
Swap:         4056          0       4056
04:30 PM ~ $ 
```

---

