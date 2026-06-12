---
title: "Problems with NewEgg and TinyPic"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by Derrick79 on 2012-06-06
Ubuntu 12.04

When I click a preview photo of an item to enlarge it at newegg it dosent load.  The window opens up says one moment please and nothing happens.  I can upload photos fine at tinypic but I cant read the txt of my photo location to share it, its blank. I have to right click the photo and copy image location.  Any ideas, I have this problem with FireFox and Chromium. Thanks

---

### Post by irv on 2012-06-06
Sounds like maybe a flash problem. This is off the Adobe website. it helped me.
> Prerequisites for protected content playback

For Ubuntu 10.04 or later, ensure that the Hardware Abstraction Layer module is first installed using apt-get.
(Watch carefully for “hal” install errors, as a damaged package install can continue to affect video playback.)

```
sudo apt-get install hal
```

After the "libhal" (HAL) library install completes, close the browser and clear the Adobe Access directories by executing the following shell commands:

```
cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2
```

Note:

If the Hardware Abstraction Layer module is missing, Flash Player still functions. However, it cannot play protected content that requires the Adobe Flash Access DRM (Digital Rights Management) module.

To the top
Support for targeted 64-bit versions of Linux

Adobe publishes platform support for 32-bit and 64-bit Linux in the system requirements section of the Flash Player 11 site. Currently supported distributions (32 bit and 64 bit) are Redhat Enterprise Linux 5.6 or later and Ubuntu 10.04 or later.

openSuse is also supported.
Install the correct 32-bit or 64-bit Flash Player plug-in

Navigate to [http://www.adobe.com/go/flashplayer](http://www.adobe.com/go/flashplayer) to install the latest Flash Player for your platform and architecture.

If unsure which Linux package to install, click Do you have a different Operating System Or Browser? for more OS choices.
I also install Flash 11.

---

### Post by philinux on 2012-06-06
hal not installed here and flash works ok.

Maybe try flashaid. [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by Derrick79 on 2012-06-06
FlashAid worked but now I cant view youtube videos. Says missing plug in. I installed adobe flash before and never got youtube to work. So I uninstalled it and I think gnash was playing my youtube videos.

FlashAid fixed my NewEgg and TinyPic problem  just no youtube now. ](*,)

---

### Post by philinux on 2012-06-06
> **Derrick79 said:**
> FlashAid worked but now I cant view youtube videos. Says missing plug in. I installed adobe flash before and never got youtube to work. So I uninstalled it and I think gnash was playing my youtube videos.

FlashAid fixed my NewEgg and TinyPic problem  just no youtube now. ](*,)

Ok get a flash vid up on something other than youtube. Right click it and try unticking hardware acceleration. Other option could be addon flashvideoreplacer. Someone else may have an idea re youtube.

---

### Post by Derrick79 on 2012-06-09
Update - I stopped using FireFox, switched to Google Chrome not Chromium and everything runs flawlessly.

---

