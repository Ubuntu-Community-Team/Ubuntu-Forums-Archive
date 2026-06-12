---
title: "How do i reinstall default audio driver"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by stx2 on 2014-07-22
I installed a different sound driver, the flash player started to crash and burn, how do i revert my settings ?

---

### Post by Bucky Ball on 2014-07-22
Welcome. What did you install and what release/flavour *buntu are you using?

---

### Post by stx2 on 2014-07-22
hello, the driver is [here]("https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=11636&lang=eng&ProdId=2229"). My computer curently runs Xubuntu 14.04 (32bit) codenamed Trusty Tahr. The sound works fine in all my applications but my flash player crushes every time on start, i did a reinstall of the current flash but that did not work, installed manually and again did not work so the problem i guess, it's the sound/audio different driver.

---

### Post by Bucky Ball on 2014-07-22
Start the computer and if you get to a desktop after the crash, open a terminal before doing anything else and paste this in:

```
dmesg
```

Hit return and post back the last part, say, 25 lines. There should be an error regarding flash or sound or something down near the bottom somewhere.

BTW, everything you need is already here or can be installed from the repositories. You are likely to muddy the waters by installing third-party audio drivers. There's no need. You may eventually need to un-install them to get things working.  ;)

My money's on a Flash issue, and resolving that may be confused by installing manually. You need flashplugin-installer from Software Centre. That's it. Once that's installed Flash, if Flash is still crashing then it's probably an issue with Flash. I'm not sure if installing it will flush out what you have installed. You may end up with three versions of Flash!

(PS: Installing xubuntu-restricted-extras also installs the correct version of flash. Adobe are no longer supporting Linux so I think flash version stops at 11.2, could be 11.7). You could install open-jre, an open-source alternative - and see if that is any help.)

---

