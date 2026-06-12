---
title: "Wireless to Ethernet"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by daniell59 on 2012-08-02
I am now in the process laying ethernet cable. Presently I am using a wireless network. Soon I will be ready to switch to the ethernet network. Must I first disable the wireless network?

Ubuntu 10.04

Thanks

---

### Post by Cheesehead on 2012-08-02
No.

Your LAN's router will happily assign two IP addresses to your system, one to the wireless interface and one to the wired interface. And your system is easily capable of handling that.

You can only access the internet, however, using a single network interface at a time; the second can be active but will be ignored by traffic.

After you hook up the ethernet connection, you can test it before disabling wireless. You really don't need to disable wireless at all, though it's generally considered good practice to disable interfaces you are not using.

---

### Post by audiomick on 2012-08-02
I am not absolutely sure, but I think that Ubuntu defaults to a cable connection when you plug a cable in, even if the wireless is running.

I would disable the wireless if it is not being used. I mean at the router, not at the computer, although I would also switch off the wireless on the computer if I were not using it.

First and foremost is the simplicity factor: the machine can't get confused if it only has one option.

Then there is the security related thing: no-one can be tempted to try and hack into a wireless connection that is switched off

The other thing is the environmental concern. Electro smog is a disputed issue, but my attitude is "why leave something running that I am not using and which may be detrimental to my health?". On top of that, having the wireless sender on uses energy. Not much, but it uses some, which puts a strain on the environment and costs money.

---

### Post by richpri on 2012-08-02
As a retired network engineer I can confidently say that the "security thing" is a much bigger issue then most people think.  Do indeed turn of your wireless at both ends if you are not using it.

---

### Post by OM55 on 2012-08-02
In my experience, [audiomick]("http://ubuntuforums.org/member.php?u=553389") is correct - Ubuntu defaults to the wired connection after a while, even without disconnecting the wireless.
Meaning, if you are on wireless connection, then connect the Ethernet cable _without_ disconnecting the wireless adapter, within a couple of minutes all network connections will be routed through the Ethernet wired connection and not through the wireless.

So both wireless and wired adapters will work, each with its own IP number, but network communication will be routed only though the wireless connection.

Since Ethernet connection is almost always faster, better and more secure than wireless connection, it is good that it happens.
If you do not intend to use your wireless connection, I definitely second richpri above - you probably should disconnect the wireless adapter and prevent it from switching on automatically on startup.

---

### Post by daniell59 on 2012-08-03
Thanks guys for you informative replies.
I am going to attach my internet cable to the wireless router.
I am ashamed to admit ignorance, but how do I disable the wireless mode of the router?

---

### Post by zandman on 2012-08-03
How to turn off wireless on your router: specifics depend on the exact router you have, but you should have an option somewhere to login to the router itself. 
It's typically started with typing 10.x.x.254 or 192.168.1.254 or so into the address bar of your browser.
Look in your router documentation (or that what was delivered by your provider) for the exact ip-address.
You'll encounter a screen asking for user-id and pwd, if you never changed it (very bad) you should use the defaults provided.
Look for something like "wireless"in the menu and there will be some sort of checkbox to turn wireless on and off

---

### Post by daniell59 on 2012-08-03
> **zandman said:**
> How to turn off wireless on your router: specifics depend on the exact router you have, but you should have an option somewhere to login to the router itself. 
It's typically started with typing 10.x.x.254 or 192.168.1.254 or so into the address bar of your browser.
Look in your router documentation (or that what was delivered by your provider) for the exact ip-address.
You'll encounter a screen asking for user-id and pwd, if you never changed it (very bad) you should use the defaults provided.
Look for something like "wireless"in the menu and there will be some sort of checkbox to turn wireless on and off

Sometime ago I changed the channel. I guess I can go back on their site and turn it off. I also have a unused ethernet router. Do you think that I would be better off using that one?

---

### Post by audiomick on 2012-08-03
> **daniell59 said:**
> Sometime ago I changed the channel. I guess I can go back on their site and turn it off.
Yep, you should be able to. Some machines, like mine, have a hardware switch on the outside to turn off the radio bit. I believe pretty much all of them have a function inside to turn it off via the software.

 > I also have a unused ethernet router. Do you think that I would be better off using that one?

You could use that if you want to, but I don't think that would make all that much difference unless you discover that the router with the wireless doesn't have any possibility to turn off the wireless, and you really want to have it turned off when not in use. I believe there is some difference in the performance of wireless gadgets, but for normal mortals on a cable network, I think a router is a router is a router.

---

