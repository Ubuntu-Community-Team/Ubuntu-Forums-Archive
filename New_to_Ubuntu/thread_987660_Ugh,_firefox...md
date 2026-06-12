---
title: "Ugh, firefox.."
date: 2008-11-19
forum: New to Ubuntu
---

### Post by adobrakic on 2008-11-19
It seems as if with every release their memory leak grows. 
Right now the usage is pretty low (36mb), but sometimes it gets well over 70mb, up to 100mb.

I know a lot of people use Opera, but is it better on memory usage?

---

### Post by itsmepaul57 on 2008-11-19
I never have anytrouble with Firefox - have you tried google chrome???  Pretty fast!!!

P

---

### Post by adobrakic on 2008-11-19
Google Chrome on Linux?

---

### Post by snova on 2008-11-19
Opera seems to be using 18 MB of memory with two tabs open.

(Assuming I'm looking at the right numbers, that is...)

Edit: Chrome hasn't been released for Linux yet. Crossover might yield results, I haven't tried it yet.

---

### Post by Pezhead on 2008-11-19
Ever since hardy everytime I use opera it crashes.

---

### Post by ciscosurfer on 2008-11-19
Memory leaks *are *annoying.  I can only see it truly being a problem on low-memory machines, though. I very rarely ever notice any type of slowdown in Firefox, even with many tabs open at once.  With the amount of memory in computers these days, is it really that big of a deal?

---

### Post by adobrakic on 2008-11-19
Well as of right now, i only have 735mb of RAM & 1.7ghz processor. So for me, it kind of is a big deal.

But once I get my 4gb RAM, quad-core (can't wait), it's not gonna matter.
:)

I'll try Opera, though

---

### Post by kansasnoob on 2008-11-19
Most likely a flash or ad prob.  

Try adding:

```
sudo apt-get install flashblock
```

And:

```
sudo apt-get install adblock-plus
```

Then restart Firefox by going to File > Quit.

You'll have to adopt an adblock service.

---

### Post by adobrakic on 2008-11-19
Yeah, I've got adblock-plus with the gfilter thing, and i'll try flashblock.
thanks
:D

---

### Post by ciscosurfer on 2008-11-19
[Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865") + [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722") = fast (and safer) browsing experience and can significantly reduce the memory footprint while surfing.  Flash is also blocked using these addons (but easily whitelisted).

---

