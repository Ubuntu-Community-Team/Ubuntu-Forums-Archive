---
title: "Google Chrome Black dialog boxes"
date: 2017-11-25
forum: New to Ubuntu
---

### Post by otter84 on 2017-11-25
Hello all, i have recently installed lubuntu and attempted to run chromium or even google chrome however both of these web browsers create black screens where dialog boxes would appear. Examples of this include the address bard when it pops down to show recently visited sites is all black, the settings tab when clicked to open is all black, and even the welcome page displays black boxes where google logo should be. This happens with both Chromium and Chrome, then after about 3 minutes of that they both unexpectedly close. Any help here would be appreciated as Google Chrome is my preferred browser but if i cant use it i will stick to firefox i suppose.

---

### Post by DuckHook on 2017-11-25
Welcome to the forums, otter84

More info please.

[LIST=1]
[*]What version are you using? <aside> I'm not too knowledgeable about anything beyond Xenial.
[*]What are your HW specs? Provide details.
[*]What video setup do you have? Provide details.
[*]What video drivers are you using? The default that come with the OS or a proprietary one that you added post OS-install? If so, provide details.
[*]Which version of chrome and chromium are you running?
[*]Does the same thing happen in a LiveUSB of Xenial (16.04)?
[/LIST]
As you can see from above, help is not possible without proper info.

---

### Post by otter84 on 2017-11-25
Understand the need for further info i will see what i can come up with. i am using Lubuntu Artful AARDVARK 17.10
HW is well older Intel Celeron D 2.8Ghz processor, 1 gig DDR Ram, storage 128 GB SSD, video NVIDIA nv36 GeForce FX 5700LE. all included drivers i have installed no new drivers other than what came with Lubuntu. 
Chromium version 62.0.3202.94-0ubuntu0.17.10.1388
Chrome Version 62.0.3202.94-1
could not tell you if this happens on the live version or not. i Installed this directly to my SSD and deleted it formt he USB afterwords.

---

### Post by Habitual on 2017-11-25
See [https://productforums.google.com/forum/#!msg/chrome/QgzVPJqhbTQ/3-yFfUyyPCIJ](https://productforums.google.com/forum/#!msg/chrome/QgzVPJqhbTQ/3-yFfUyyPCIJ)

Says disable hardware acceleration setting for the browser.

---

### Post by otter84 on 2017-11-25
> **Habitual said:**
> See [https://productforums.google.com/forum/#!msg/chrome/QgzVPJqhbTQ/3-yFfUyyPCIJ](https://productforums.google.com/forum/#!msg/chrome/QgzVPJqhbTQ/3-yFfUyyPCIJ)

Says disable hardware acceleration setting for the browser.


Problem with this idea is i cannot see the menu when i click the settings lines in the right corner, that screen is just a solid black box.

---

### Post by DuckHook on 2017-11-27
Start Chrome from the command line and disable hardware acceleration using a switch. A list of Chrome's switches is here: [https://peter.sh/experiments/chromium-command-line-switches/](https://peter.sh/experiments/chromium-command-line-switches/)

The switch you may be looking for is:```
--disable-gpu
```…note the double hyphens needed to designate the switch.

---

