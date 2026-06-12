---
title: "something wicked happened?"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by wonderingwhy on 2012-05-20
Hi

So I'm trying to update with the following command > sudo apt-get updateand I get this error message multiple times

> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_NZ.bz2)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

something wicked happens while trying to fetch other things too because there is no associated address with hostname.

1. where did I go wrong

2. how do I fix it

Many thanks

---

### Post by alphacrucis2 on 2012-05-20
> **wonderingwhy said:**
> Hi

So I'm trying to update with the following command and I get this error message multiple times



something wicked happens while trying to fetch other things too because there is no associated address with hostname.

1. where did I go wrong

2. how do I fix it

Many thanks

DNS problem? Is internet access otherwise ok.

What does 

```
dig archive.ubuntu.com
```

say.

---

### Post by wonderingwhy on 2012-05-20
Yes, no probs with internet at all.  I have some probs viewing certain types of media and listening to other types of media - hence trying to update, but as for general internet usage no probs at all.

I found another post that indicated I should make some changes to systems>preference>networkconnections but the test check that was suggested didn't tell me anything as I could already view and bookmark and view from bookmark.  So I put the settings back to how they were before I made the changes.

My package manager is out of date, and I wonder if its connected to this problem - I can't get new versions of any package in particular for instance ALSA or Kaffeine or VLC.

I had to down load the kaffeine upgrade manually, and same for firefox upgrade, but the ALSA upgrade just said package couldn't be found.

---

### Post by HiImTye on 2012-05-20
I'd try using OpenDNS at least for now,

change your DNS to '208.67.222.222, 208.67.222.220, 208.67.220.222, 208.67.220.220'
so that it looks like this:
[ATTACH]218362[/ATTACH]
to do so you will need to click on 'configure' then go to the 'IPv4 Settings' tab, for 'method' choose 'Automatic (DHCP) addresses only' and after 'DNS Servers:' put:
208.67.222.222, 208.67.222.220, 208.67.220.222, 208.67.220.220
so that it looks like:
[ATTACH]218361[/ATTACH]
then give it a try

---

### Post by Bucky Ball on 2012-05-20
> **HiImTye said:**
> I'd try using OpenDNS at least for now,

change your DNS to '208.67.222.222, 208.67.222.220, 208.67.220.222, 208.67.220.220'
so that it looks like this:
[ATTACH]218362[/ATTACH]
to do so you will need to click on 'configure' then go to the 'IPv4 Settings' tab, for 'method' choose 'Automatic (DHCP) addresses only' and after 'DNS Servers:' put:
208.67.222.222, 208.67.222.220, 208.67.220.222, 208.67.220.220
so that it looks like:
[ATTACH]218361[/ATTACH]
then give it a try

OP has no problem with DNS, as confirmed.

It could just be that mirror is down. You can try another mirror from  here to and see if that resolves anything before trying the above. Click  the 'Ubuntu Software' tab and change the mirror. 

If you've added a repository yourself and that is causing the problem, open Software Sources (or whatever/wherever it is in 12.04), click on 'Other Software', find the entry that matches the repo mentioned in whatever error message you are getting and untick it. This will ask for an update check. Let it rip and see what error you get. If it shows another, disable the repository mentioned. At least for the moment. 

Try enabling them later. It may be a (temporary?) problem(s) at the mirror/server end rather than anything amiss at yours (especially if your DNS is fine and you can hit addresses other than these). :wink:

---

### Post by wonderingwhy on 2012-05-21
Thanks Bucky Ball and HilmTye

So in the end it appears I needed both. 

But then I went to upgrade ALSA I'm still on .21 and .25 is the current version, first I checked Synaptic but the latest version was not there and then I did it through the terminal and I got this output"

> sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-41-generic


So it appears that something is still amiss and I'm still not able to update - even if I use a command line

Although I'm no longer being told something wicked happened and before trying to update ALSA all looked present and correct

---

### Post by Bucky Ball on 2012-05-21
Try these two commands one after the other:

```
sudo apt-get update
sudo apt-get upgrade

```The latter should upgrade packages you have installed if there are upgrades available. Have a look and see if it is going to upgrade ALSA. 

Seems your original problem is resolved, though.

---

### Post by mlentink on 2012-05-21
Please also keep in mind that not always the bleeding edge packages are in the repos.

---

