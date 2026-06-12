---
title: "Ad Blocking Proxy for Lubuntu Machine and VPN..."
date: 2014-06-10
forum: New to Ubuntu
---

### Post by badtlc on 2014-06-10
I have a lubuntu machine that I will be hosting either a VPN or SSH server on so that I can encrypt all my android data regardless of location.  Does anyone have any good advice on how to do this?

Right now, I think i'm going to do basic IPSec for the VPN so I can use it on androids and iphones.  But I'm not sure how to setup an ad blocking proxy in lubuntu.  I want the proxy to also block/filter for the Lubuntu machine itself.  I thought maybe Bfilter, privoxy or Diladele/squid could accomplish this.  I know any of these will work as proxies but a typical proxy needs to be pointed to in the browser configuration.  I want a proxy that filters automatically w/out setting up the lubuntu browsers or my android browser.  I want the ad blocking proxy to filter everything coming to and from the lubuntu machine.

Can anyone point me in the right direction?  Thanks.

---

### Post by SeijiSensei on 2014-06-11
You can accomplish this with a "transparent" proxy.  An iptables rule is used to divert all outbound HTTP requests through the proxy.  A quick Google search for "transparent squid proxy" will bring up details.

That said, are you always going to access the proxy from behind the Lubuntu machine?  Or do you want to use it from other public locations over the Internet?  That opens up a dangerous security hole unless you add authentication or some other method to limit access to the proxy.  It's also hard to set up a transparent proxy in this manner.  If you do want to use the proxy from outside, you're probably best off configuring the proxy settings in the browser on your device rather than trying to make such a proxy transparent.

Personally I find it easier to run add-ons to Firefox like AdBlockPlus and Ghostery to block ads rather than doing it at the proxy.

---

### Post by Vladlenin5000 on 2014-06-11
> **SeijiSensei said:**
> Personally I find it easier to run add-ons to Firefox like AdBlockPlus and Ghostery to block ads rather than doing it at the proxy.

+1

---

### Post by badtlc on 2014-06-13
The problem is with android devices, you can set a proxy for the browser but it doesn't work for the apps which is 90% of what is used on the device.  Hence, having to use proxy settings for a browser isn't an option.

As for addons, they are way too bulky.  When you install ABP or the likes, it doubles or triples the memory used by the browser.  This is not acceptable to me.  The ad blocking proxies use much less memory.  For this reason I also want the ad filtering proxy for the lubuntu machine.  I figured since I'll have one for the Lubuntu machine, and it acts as the VPN for my mobile devices, why not share the ad blocking proxy with the VPN connections so that all my mobile devices can get filtered pages and save some bandwidth along the way.

---

