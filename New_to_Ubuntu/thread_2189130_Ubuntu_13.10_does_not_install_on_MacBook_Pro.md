---
title: "Ubuntu 13.10 does not install on MacBook Pro"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by thealmightyev on 2013-11-20
Hi. I have a problem with trying to install Ubuntu on my MacBook Pro (15inch, late 2012). I made a bootable DVD for Ubuntu using the instructions on the website, and pressed ALT / OPTION when restarting. I clicked the "Windows" CD (it's a glitch or something on Mac, it means Ubuntu or Linux) but when it booted from it, I got a black screen with a little blinking underscore and it sat there for a few minutes. I was getting impatient so I just forced-shut-down my laptop (which I hate doing). I tried it again by pressing C to see if it'd make a difference but the same thing happened.

Does anyone know how I can fix this issue? I see people talking about changing the boot options when they get to a purple screen but I never get to that screen. Any help? I really want to use Ubuntu but this is starting to depress me already.

Thanks.

---

### Post by simbauad on 2013-11-21
Well could you check the md5sum of the image you downloaded. Read [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM). and compare your output with the appropriate image you downloaded: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes). By the way, which image did you download: [COLOR=#333333][FONT=Ubuntu]ubuntu-13.10-desktop-amd64+mac.iso or [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]ubuntu-13.10-desktop-amd64.iso?[/FONT][/COLOR]

---

### Post by thealmightyev on 2013-11-21
I clicked on the "Download Ubuntu Desktop 13.10" and it gave me the "amd64". There was no "-Mac". I read somewhere that it should be "-Mac" but I dunno how to get that one.

Could that be the problem?

Thanks mate!

---

### Post by howefield on 2013-11-21
> **thealmightyev said:**
> I clicked on the "Download Ubuntu Desktop 13.10" and it gave me the "amd64". There was no "-Mac". I read somewhere that it should be "-Mac" but I dunno how to get that one.

[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

Scroll down the page to the "Other images" section.

---

### Post by simbauad on 2013-11-21
Here is a direct link: [http://releases.ubuntu.com/saucy/ubuntu-13.10-desktop-amd64+mac.iso](http://releases.ubuntu.com/saucy/ubuntu-13.10-desktop-amd64+mac.iso) Please do tell us if you face any problems, even after trying this iso.[COLOR=#000000][/COLOR]

---

### Post by thealmightyev on 2013-11-21
Burned a disk with the "-mac" version of the iso. 

Didn't work. Same exact results; black screen with blinking underscore. God, I hate having to slam the power on my machine....

Any other ideas?

---

### Post by dkudriavtsev on 2013-11-21
wait a bit...

---

### Post by thealmightyev on 2013-11-21
> **dkudriavtsev said:**
> wait a bit...

Uh-oh, am I just being impatient? Is that normal for it to take a while?

I waited about... 2 minutes probably. I know it wasn't very long but I was getting quite anxious. Would you suggest to try it again?

Thanks.

---

### Post by simbauad on 2013-11-21
Ok! This might seem strange, but when I burned an iso from my previous windows installation, it used to give me a blinking underscore. Surprisingly, when I did it from Ubuntu it went on just fine. Do you have a spare usb at hand? Try what is mentioned on the installation page: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx). Tell us if it boots. And no, it is not normal to have to wait more than a few seconds.

---

### Post by thealmightyev on 2013-11-22
> **simbauad said:**
> Ok! This might seem strange, but when I burned an iso from my previous windows installation, it used to give me a blinking underscore. Surprisingly, when I did it from Ubuntu it went on just fine. Do you have a spare usb at hand? Try what is mentioned on the installation page: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx). Tell us if it boots. And no, it is not normal to have to wait more than a few seconds.

Should I put the "-mac" iso on the USB or just the original iso?

Thanks for the continued help.

---

### Post by thealmightyev on 2013-11-22
-stupid question, solved- Sorry!

---

### Post by thealmightyev on 2013-11-22
Alright. Sorry for triple posting but I have refined my overall question.

How can I install Ubuntu 13.10 on my external hard drive with my MBP? Do I start with a LiveCD? And if so, how can I fix this issue I am having with the black screen and blinking underscore? I basically want to run Ubuntu off of my external hard drive and eventually one day down the road install it on my machine.

---

