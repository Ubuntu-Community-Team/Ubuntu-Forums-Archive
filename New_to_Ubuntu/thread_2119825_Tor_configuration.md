---
title: "Tor configuration?"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by yakinikku on 2013-02-24
I have been trying to get this working right and it just won't.  I know I am missing something small.  I followed the steps outlined here

[http://bodhizazen.net/Tutorials/TOR](http://bodhizazen.net/Tutorials/TOR)

and tried to get it working.  It doesn't.  From a terminal if I run 

```
curl ifconfig.me/ip
```

my public IP has not changed.  Can you guys help give me some direction?  TIA!!:guitar::guitar:

---

### Post by leclerc65 on 2013-02-24
Running Tor from the Tor-Browser bundle is much less of a hassle.

---

### Post by yakinikku on 2013-02-24
> **leclerc65 said:**
> Running Tor from the Tor-Browser bundle is much less of a hassle.

except that only masks traffic from the browser.  I want to mask all traffic.  anyone have any ideas?

---

### Post by MyTinFoilHat on 2013-02-24
> **yakinikku said:**
> except that only masks traffic from the browser.  I want to mask all traffic.  anyone have any ideas?

I recommend you go directly to the source: [https://www.torproject.org/](https://www.torproject.org/)
There you'll find the various installation pkgs as well as installation instructions. Look for and use the Browser Bundle.

I believe Tor Projects even have their own ppa you can add to your software sources. You may want to double check that. They also provide you with instructions for proxying all apps through the Tor service. Be sure to check keys to prevent MITM.

While you're at it, check out EFF's SSD pages for helpful tips: [https://ssd.eff.org/](https://ssd.eff.org/)
EFF also has a specific section of their SSD pages about Tor. [https://ssd.eff.org/tech/tor](https://ssd.eff.org/tech/tor)

It isn't enough to simply use Tor, you have to change your own behaviour.

---

### Post by yakinikku on 2013-02-24
> **MyTinFoilHat said:**
> I recommend you go directly to the source: [https://www.torproject.org/](https://www.torproject.org/)
There you'll find the various installation pkgs as well as installation instructions. Look for and use the Browser Bundle.

I believe Tor Projects even have their own ppa you can add to your software sources. You may want to double check that. They also provide you with instructions for proxying all apps through the Tor service. Be sure to check keys to prevent MITM.

While you're at it, check out EFF's SSD pages for helpful tips: [https://ssd.eff.org/](https://ssd.eff.org/)
EFF also has a specific section of their SSD pages about Tor. [https://ssd.eff.org/tech/tor](https://ssd.eff.org/tech/tor)

It isn't enough to simply use Tor, you have to change your own behaviour.

I agree.  Thanks!  I will probably have to post this same thing over at the tor site as well.

---

### Post by DuckHook on 2013-02-25
Perhaps you don't understand the limitations and uses of Tor. Because it is a multi-rerouting anonymizer, often channeled through low-bandwidth private connections, it usually suffers from considerable lag and limited throughput. It isn't a cure-all, and was never designed to be. Even heavy browser use for innocuous but bandwidth-heavy purposes (like Youtube) is considered an abuse of the Tor network. This is why most users install something like Torbutton so that Tor can be turned off when not truly required. Torrenting over Tor is also considered an abuse of the network.

Please appreciate that the network is often used by people in highly restrictive countries to acquire news and exchange thoughts they could not otherwise access. If the network gets clobbered by menial and inconsequential data transfers, then it becomes incapable of fulfilling its higher purposes. By its nature, it relies on the good judgment and self discipline of its user-base and requires self policing.

With those thoughts in mind, here is what you are looking for:

[https://trac.torproject.org/projects/tor/wiki/doc/SupportPrograms](https://trac.torproject.org/projects/tor/wiki/doc/SupportPrograms)
[https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO](https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO)

If you use Tor to any significant degree, please consider running a relay so that you can grow the network and enhance its throughput. It's a lot like torrenting, where it is only considered responsible conduct to put at least as much back into it as you take out of it.

<edit>
...and yes, I use Tor, but very sparingly. My usage plan is not sufficient to allow me to act as a relay, else I would.
</edit>

---

### Post by yakinikku on 2013-02-25
> **DuckHook said:**
> Perhaps you don't understand the limitations and uses of Tor. Because it is a multi-rerouting anonymizer, often channeled through low-bandwidth private connections, it usually suffers from considerable lag and limited throughput. It isn't a cure-all, and was never designed to be. Even heavy browser use for innocuous but bandwidth-heavy purposes (like Youtube) is considered an abuse of the Tor network. This is why most users install something like Torbutton so that Tor can be turned off when not truly required. Torrenting over Tor is also considered an abuse of the network.

Please appreciate that the network is often used by people in highly restrictive countries to acquire news and exchange thoughts they could not otherwise access. If the network gets clobbered by menial and inconsequential data transfers, then it becomes incapable of fulfilling its higher purposes. By its nature, it relies on the good judgment and self discipline of its user-base and requires self policing.

With those thoughts in mind, here is what you are looking for:

[https://trac.torproject.org/projects/tor/wiki/doc/SupportPrograms](https://trac.torproject.org/projects/tor/wiki/doc/SupportPrograms)
[https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO](https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO)

If you use Tor to any significant degree, please consider running a relay so that you can grow the network and enhance its throughput. It's a lot like torrenting, where it is only considered responsible conduct to put at least as much back into it as you take out of it.

<edit>
...and yes, I use Tor, but very sparingly. My usage plan is not sufficient to allow me to act as a relay, else I would.
</edit>

Thanks, I have no intention of using TOR for youtube or torrenting.

---

