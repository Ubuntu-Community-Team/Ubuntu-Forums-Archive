---
title: "[SOLVED] Firefox 3 starting in Offline Mode"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Tom--d on 2008-05-10
Why?

I have an manual configuration connection. (through /etc/rc.local). Its wireless. I do not use nm-applet. 

How will this be resolved?

Can I make nm-applet think that I have a internet connection?



**To solve this problem, I did this. **

```
sudo apt-get remove network-manager
```

And it worked fine :D

**Firefox now starts in online mode again!!**

Really tho, Firefox should not rely on Network manager for a connection. Nor any app really.

---

### Post by Biggy on 2008-05-10
Firefox 3 is a beta version..

From Add/Remove uninstall Firefox 3 and install Firefox 2

---

### Post by FuturePilot on 2008-05-10
> **Tom--d said:**
> Why?

I have an manual configuration connection. Its wireless. **I do not use nm-applet. **

How will this be resolved?

Can I make nm-applet think that I have a internet connection?

That is why. There's currently an issue where most applications will ask Network Manager if there is a connection. If there isn't one, or if you are not using Network Manager, it will start in Offline mode.

---

### Post by Tom--d on 2008-05-10
I see, Could I make nm-applet 'think' that I have a connection?

---

### Post by FuturePilot on 2008-05-10
I'm not sure how you have manually configured your connection (through /etc/network/interfaces or whatnot), but I think you could manually configure it through Network Manager. That way all applications will see your connection.

---

### Post by Tom--d on 2008-05-10
Through /etc/rc.local

---

### Post by ruiruas on 2008-05-12
Hi guys,
network manager still seems to have some problems regarding wireless devices and a few other things. Since many of us use other apps or small scripts to configure our network, I think we can simply remove network-manager.

```
sudo apt-get remove network-manager
```

* I tried using firefox-2, but in hardy (at least in my case) firefox-2 seems to run very slow and sometimes hangs gnome.

After doing that, firefox 3 started working correctly, starting online.

Cheers,
Rui Ruas

---

### Post by 0ni on 2008-05-12
I had this problem once, but it just went away on it's own.

---

### Post by Tom--d on 2008-05-13
Still got the problem. 
have removed Network manager Gnome.. do i remove the Network manager aswell?

---

### Post by blakegrover on 2008-05-16
I have found the problem, it isn't firefox's problem, it is a addon ubuntu has added.  If you go into Tools->Addons and then disable Ubuntu firefox modifications and restart firefox you will be able to bypass the default offline mode

Blake

---

### Post by Tom--d on 2008-05-16
> **blakegrover said:**
> I have found the problem, it isn't firefox's problem, it is a addon ubuntu has added.  If you go into Tools->Addons and then disable Ubuntu firefox modifications and restart firefox you will be able to bypass the default offline mode

Blake

Still didn't work :(

---

### Post by Grishka on 2008-05-16
sudo aptitude remove network-manager

---

### Post by Tom--d on 2008-05-16
No, that doesn't work.

I cannot remove network-manager. 

I can remove gnome-network-manager which I have and it does nothing. Firefox still starts in offline mode :@

I use a little script to run my wireless on boot in my /etc/rc.local file. This is the reason Firefox is in offline mode.

I NEED the commands in the /etc/rc.local to be run at boot.

Is there a file which runs at boot and Network Manager recognizes?? So it will say I have a connection?

---

### Post by Grishka on 2008-05-17
why can't you remove network-manager? it shouldn't really be needed on a typical install, unless you want the monitoring applet.

---

### Post by Tom--d on 2008-05-17
It said when Removing Network manager that it needed a lot of packages (ubuntu-desktop etc) so I said no.
That was with:
```
sudo aptitude remove network-manager
```

But in Synaptic manager, it was uninstalled fine :). No other packages need to be removed. 

[b]Removing network-manager and gnome-network-manager solved my problem!!

Firefox now starts in online mode :D

Yay[/b]

---

