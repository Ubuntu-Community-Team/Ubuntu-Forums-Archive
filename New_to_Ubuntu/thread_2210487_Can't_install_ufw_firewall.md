---
title: "Can't install ufw firewall"
date: 2014-03-11
forum: New to Ubuntu
---

### Post by gregg3 on 2014-03-11
I'm really new so I'll run you through what I did. (first of all running Xubuntu 13.10 in Dell Optiplex 170L)

I downloaded Gufw Firewall Configuration from Ubuntu Software Center

I went to Settings Manager-->Firewall Configuration

Then it asked for my password

I gave the password and got this error message (see screenshot 090)

I checked in the Synaptic Package Manager (see screenshot 091) and it shows it's installed.

But when I run the status check (sudo ufw status)  in the terminal it shows 'inactive.'  (meaning, I'm assuming, the file is there but it's not turned on)

Anybody know what might be going on?

---

### Post by OrangeCrate on 2014-03-11
> **gregg3 said:**
> I'm really new so I'll run you through what I did. (first of all running Xubuntu 13.10 in Dell Optiplex 170L)

I downloaded Gufw Firewall Configuration from Ubuntu Software Center

I went to Settings Manager-->Firewall Configuration

Then it asked for my password

I gave the password and got this error message (see screenshot 090)

I checked in the Synaptic Package Manager (see screenshot 091) and it shows it's installed.

But when I run the status check (sudo ufw status)  in the terminal it shows 'inactive.'  (meaning, I'm assuming, the file is there but it's not turned on)

Anybody know what might be going on?

Start over. Uninstall Gufw, reboot, and try enabling UFW from the command line (terminal).

At the command line type this:

```
sudo ufw enable
```

(If the firewall is already configured somehow from what you've already done, it will tell you that the "firewall is active and enabled on startup". If not, as you say it is, it will enable it.

To check the status, as you did previously, enter this at the command line:

```
sudo ufw status
```

If is say enabled, that's it, your done. Don't worry about it until you install a new OS, or reinstall the current one. It seems that I remember other threads bemoaning Gufw. IMO, in this case, the command line is easier than the GUI.


UFW documentation here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by buzzingrobot on 2014-03-11
The message means gufw is already open and running. Check in System Monitor to see if that's the case. If not, the message itself is in error and something else is going on.

The advice to delete and reinstall gufw is good. You'll start from a clean slate.

Occasionally, some folks attempt to launch Gufw as a startup application thinking it *is* the firewall.  It isn't and shouldn't be a startup app. It's just a GUI tool to make configuring ufw a bit easier.

---

### Post by oldos2er on 2014-03-11
Moved to Absolute Beginners.

---

### Post by gregg3 on 2014-03-12
> **OrangeCrate said:**
> Start over. Uninstall Gufw, reboot, and try enabling UFW from the command line (terminal).

At the command line type this:

```
sudo ufw enable
```

(If the firewall is already configured somehow from what you've already done, it will tell you that the "firewall is active and enabled on startup". If not, as you say it is, it will enable it.

To check the status, as you did previously, enter this at the command line:

```
sudo ufw status
```

If is say enabled, that's it, your done. Don't worry about it until you install a new OS, or reinstall the current one. It seems that I remember other threads bemoaning Gufw. IMO, in this case, the command line is easier than the GUI.


UFW documentation here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Hey Orange Crate, I uninstalled gufw, rebooted, put in sudo ufw enable, got the  "firewall is active and enabled on startup" message, checked it with sudo ufw status and it said "active." So I'm a happy camper. Thank you. However, I do have a question (or two). When I did this on my identical other computer, I was instructed to go to the "Settings Manager" and there find the Firewall (the blue shield) thingie there, which I did. When I clicked on the Firewall shield, I had to give my password, and then I had to slide the indicator from "off" to "on."

And I looked in the Settings Manager after I did the status check on this installation and there is no Firewall thingie. 

I've gotten a little turned around with what I've done or not done with the other computer. And I (see attachment) I see that blue shield (for the gufw firewall configuration). Is that what would give me the Firewall thingie in the settings manager? And does it matter if I have that or not?

---

### Post by gregg3 on 2014-03-12
> **buzzingrobot said:**
> 
Occasionally, some folks attempt to launch Gufw as a startup application thinking it *is* the firewall. .

Thanks. I think that's exactly what I did.

---

### Post by OrangeCrate on 2014-03-12
> **gregg3 said:**
> Hey Orange Crate, I uninstalled gufw, rebooted, put in sudo ufw enable, got the  "firewall is active and enabled on startup" message, checked it with sudo ufw status and it said "active." So I'm a happy camper. Thank you. However, I do have a question (or two). When I did this on my identical other computer, I was instructed to go to the "Settings Manager" and there find the Firewall (the blue shield) thingie there, which I did. When I clicked on the Firewall shield, I had to give my password, and then I had to slide the indicator from "off" to "on."

And I looked in the Settings Manager after I did the status check on this installation and there is no Firewall thingie. 

I've gotten a little turned around with what I've done or not done with the other computer. And I (see attachment) I see that **blue shield** (for the gufw firewall configuration). Is that what would give me the Firewall thingie in the settings manager? **And does it matter if I have that or not?**

Nope, it's not needed at all. You configured your firewall from the command line, it's working behind the scenes, and you're all done. Good job.

:)

Edit:

Forgot to comment on your other question. The other computer apparently has Gufw installed too? If so, do the same for that computer as you did for this one. Uninstall Gufw, etc. (per my previous instructions). If you configure the firewall from the command line, like you just did, you do not need Gufw.

---

### Post by gregg3 on 2014-03-12
> **OrangeCrate said:**
> Nope, it's not needed at all. You configured your firewall from the command line, it's working behind the scenes, and you're all done. Good job.

:)

Edit:

Forgot to comment on your other question. The other computer apparently has Gufw installed too? If so, do the same for that computer as you did for this one. Uninstall Gufw, etc. (per my previous instructions). If you configure the firewall from the command line, like you just did, you do not need Gufw.

Yeah, the Gufw was installed there too. Uninstalled it. Followed the same instructions for the previous computer with the same results. I now have firewalls on both computers. Which feels really good. Thanks OrangeCrate.

---

### Post by OrangeCrate on 2014-03-12
> **gregg3 said:**
> Yeah, the Gufw was installed there too. Uninstalled it. Followed the same instructions for the previous computer with the same results. I now have firewalls on both computers. Which feels really good. Thanks OrangeCrate.

You're welcome, I'm glad you got it all worked out.

:)

---

