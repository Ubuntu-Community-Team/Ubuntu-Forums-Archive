---
title: "Installing Steam on Ubuntu 15.10 64-Bit"
date: 2016-02-29
forum: New to Ubuntu
---

### Post by HaoleBoy1975 on 2016-02-29
So I have tried many different ways to install Steam on Ubuntu 15.10 64-Bit with no luck. First I tried with the Ubuntu Software Centrer, then I tried terminal copy & paste codes from all over the net. I have reinstalled so many times its not even funny. I hate having bad commands used in my install because sometimes it can cause Ubuntu to run poorly so I reinstall in hopes that the next time I will succeed in getting it to work right.

What happens when I install steam regardless of which method is used.

Steam installs, it creates a short-cut on my desktop & my side menu, it asks if I agree to the terms, then asks me to start to finish the installation. I click start, and nothing happens. So I close it. Then I click the short-cuts on both my desktop & side bar with the same action, nothing.

The only version I have gotten Steam to work on is 12, but I want the latest version of Ubuntu.

Any help would be greatly appreciated.

Thanks for your time, help, and patients.
HaoleBoy1975

---

### Post by jim_deadlock on 2016-02-29
Try starting it from the terminal, there may be some error messages which could help you find the problem:

```
steam
```

It works for me on 15.10-64

---

### Post by HaoleBoy1975 on 2016-02-29
Alright Its working now. To anyone else with this problem who was not able to get Steam working from installing by Software Center, Terminal, or Downloading from SteamPowered.com All you need to do is install the following.

* WINE
* PlayOnLinux

Then once you have these two programs installed Run PlayOnLinus, and Search for Steam. Then install it from there.

Steam is working fine for me now.

Also thanks Jim for trying to help.

[IMG]http://i66.tinypic.com/2s97wj4.png[/IMG]
[IMG]http://i68.tinypic.com/2lw3880.png[/IMG]
[IMG]http://i63.tinypic.com/28qvtjs.png[/IMG]
[IMG]http://i67.tinypic.com/2eyz5m1.png[/IMG]
[IMG]http://i66.tinypic.com/309h3cg.png[/IMG]
If you get that error there ignore it, and just click next
[IMG]http://i68.tinypic.com/1621dmt.png[/IMG]
Sign in or make a new account...
[IMG]http://i63.tinypic.com/6srux3.png[/IMG]
As you can see its working...
[IMG]http://i63.tinypic.com/125mert.png[/IMG]
Proof of Ubuntu Version

---

### Post by jim_deadlock on 2016-02-29
Although that does work, you're actually running the Windows version. It's better to run the native Linux version if you can.

---

### Post by HaoleBoy1975 on 2016-02-29
Yeah I knows... But couldn&#8217;t get the normal client to run so this was my only option.

---

