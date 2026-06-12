---
title: "High CPU usage when playing youtube videos on Google Chrome"
date: 2018-11-23
forum: New to Ubuntu
---

### Post by yousefsaber on 2018-11-23
Very high CPU usage when playing youtube videos on Google Chrome 

these are the specs of my Ubuntu 18.10 machine

[ATTACH=CONFIG]281749[/ATTACH]

[ATTACH=CONFIG]281750[/ATTACH]


using kernal release 4.9

$ uname -r
4.9.0-040900-generic


and using intel integrated graphics instead of my NVIDIA driver what's happening

what causes this issue and what's the solution for it ?

---

### Post by SeijiSensei on 2018-11-23
Unless you use the NVIDIA card, your computer will need to decode the video with software which puts high demands on the CPU.

---

### Post by Autodave on 2018-11-23
Mostly it is from all the ads that are running at the same time.  And, if you run an ad blocker, it can even get worse.  Same thing in Firefox.

---

### Post by nyeba on 2018-11-24
You should try to install your NVIDIA GPU that will reduce the cpu usage.

---

### Post by yousefsaber on 2018-11-25
thanks for your help but the issue is still present even with NVIDA drivers

[ATTACH=CONFIG]281772[/ATTACH]

---

### Post by Autodave on 2018-11-26
I have an 8 core overclocked to 4.0 and I see that much usage or more across all eight cores.

---

### Post by logix2 on 2018-11-26
Google Chrome and Chromium browsers don't support hardware acceleration by default on Linux, that's why you're noticing very high CPU usage. There is a patch to enable VA-API in Chromium which would reduce CPU usage, but it's not available in Chromium directly. There is a PPA which enables this patch for the latest [Chromium beta]("https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta") (you'll also need the [h264ify]("https://chrome.google.com/webstore/detail/h264ify/aleakchihdccplidncghkekgioiakgal") extension).

Using this PPA requires some extra steps if you want to enable some features like Widevine support (so you can play Netflix videos and paid YouTube videos, etc.), or if you need features like Sync, but it's worth it considering the CPU usage after installing those Chromium builds. If you need step by step instructions, see [here]("https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html").

---

### Post by monkeybrain20122 on 2018-11-28
You can activate hardware acceleration in Chrome as follows. Type about:settings in the url bar, then scroll down to Advanced > System and turn on use hardware acceleration if available then restart Chrome, to check type in url bar about:gpu and see that hardware acceleration is activated.

---

### Post by logix2 on 2018-11-28
> **monkeybrain20122 said:**
> You can activate hardware acceleration in Chrome as follows. Type about:settings in the url bar, then scroll down to Advanced > System and turn on use hardware acceleration if available then restart Chrome, to check type in url bar about:gpu and see that hardware acceleration is activated.

That option actually does not enable hardware acceleration on Chrome. It's there for Chrome OS, not Linux. See this article for example: [https://www.omgubuntu.co.uk/2018/10/hardware-acceleration-chrome-linux](https://www.omgubuntu.co.uk/2018/10/hardware-acceleration-chrome-linux)

Here is why they disabled the ignore-gpu-blacklist: [https://codereview.chromium.org/176883018/#msg6](https://codereview.chromium.org/176883018/#msg6)


This is why Opera disabled it too (see the linked comment, not post): [https://blogs.opera.com/desktop/2017/02/opera-stable-43-0-2442-991-update/#comment-3168783831](https://blogs.opera.com/desktop/2017/02/opera-stable-43-0-2442-991-update/#comment-3168783831)


This is the VAAPI patch that is not included in Chrome/Chromium: [https://chromium-review.googlesource.com/c/chromium/src/+/532294](https://chromium-review.googlesource.com/c/chromium/src/+/532294)


And here is how to check if accelerated video decoding actually works: [https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html](https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html) (scroll to the 'How to check if Chromium is using GPU video decoding' part)

---

