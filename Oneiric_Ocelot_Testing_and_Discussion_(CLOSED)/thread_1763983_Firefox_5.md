---
title: "Firefox 5"
date: 2011-05-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-05-21
I must have been asleep when they announced this, but Firefox 5 took me by surprise. Then I found this in the [Wikipedia Firefox page]("http://en.wikipedia.org/wiki/Firefox"):

> 
**Future versions**

 A draft roadmap indicates that Mozilla hopes to release versions 5, 6  and 7 in 2011 following the release of Firefox 4 in early 2011. These  versions will be smaller incremental updates, primarily focusing on  improving speed, stability and security.Incremental updates will get major version numbers? What are Mozilla trying to do? Overtake Internet Explorer? :wink:

---

### Post by el_koraco on 2011-05-21
They've changed their development model to resemble Chrome's. You no longer have the stable and nightly builds for FF, but three channels - stable, beta (Arora) and Nightly. The idea is that faster development will leed to better results, which, if you run the nightly builds, is working out pretty well.

---

### Post by Quackers on 2011-05-21
Firefox 4 addons are no good now :-(
Or at least the ones I use.

---

### Post by coffeecat on 2011-05-21
> **Quackers said:**
> Firefox 4 addons are no good now :-(
Or at least the ones I use.

Well, at least adblock plus still seems to be functional, which keeps me happy. Which ones are not working?

---

### Post by Quackers on 2011-05-21
The one that opens new tabs at your homepage and, for the moment, Google toolbar.

---

### Post by Squonk07 on 2011-05-21
Of course Nightly Tester Tools makes all the add-ons work again, if you don't mind the risk of potential incompatibility. Supposedly Mozilla will be implementing a system that automatically checks the add-ons on its server and, if they work with the latest version of Fx, updates the version check info accordingly.

---

### Post by chrisccoulson on 2011-05-21
I've uploaded this already to Oneiric, but i386 users will have to wait until the start of next week before they can download it, as it's sat in the new queue because of the language pack changes (amd64 users can download it already though)

---

### Post by MacUntu on 2011-05-21
Finally we 64-bit guys get something first! :P

---

### Post by scradock on 2011-05-21
> **chrisccoulson said:**
> I've uploaded this already to Oneiric, but i386 users will have to wait until the start of next week before they can download it, as it's sat in the new queue because of the language pack changes (amd64 users can download it already though)
Working fine here in Oneiric amd64, except for the pesky add-ons. Firefox 5 tried to update them, but couldn't; the failure message assured me it would keep trying, so I'm expecting updates when they are available.

---

### Post by lovinglinux on 2011-05-21
Mozilla has implemented a system to automatically bump version compatibility on add-ons that do not have any incompatibilities with the new Firefox version. Version bumps [were applied yesterday]("http://blog.mozilla.com/addons/2011/05/21/firefox-5-compatibility-bump/"). However, you will have to search for add-on updates in the Add-ons Manager to get the patches.

You can also use [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/") to turn off compatibility check. However, this method might result in some problems, if the extension has incompatibilities.

So far, I have confirmed that Speed Dial extension is not compatible and breaks completely.

---

### Post by lovinglinux on 2011-05-21
> **chrisccoulson said:**
> I've uploaded this already to Oneiric, but i386 users will have to wait until the start of next week before they can download it, as it's sat in the new queue because of the language pack changes (amd64 users can download it already though)

Is it going to land on *firefox-next* ppa?

---

### Post by chrisccoulson on 2011-05-21
> **lovinglinux said:**
> Is it going to land on *firefox-next* ppa?

Yes, but unfortunately Mozilla released it just before I was planning to go to bed on Friday night, and it's now the weekend, so it might not be until Monday

---

### Post by lovinglinux on 2011-05-21
> **chrisccoulson said:**
> Yes, but unfortunately Mozilla released it just before I was planning to go to bed on Friday night, and it's now the weekend, so it might not be until Monday

No worries. I just wanted to know, in order to update the Firefox 4 Mega Thread.

---

### Post by coffeecat on 2011-05-21
> **scradock said:**
> Working fine here in Oneiric amd64, except for the pesky add-ons. Firefox 5 tried to update them, but couldn't; the failure message assured me it would keep trying, so I'm expecting updates when they are available.

I think there's a problem with whichever server mozilla uses for add-ons at the moment, and for these last few hours. I'm trying to get adblock plus into a fresh install of Natty and the addons thingy in Firefox just sits there for ever saying, "Downloading". It isn't.

---

### Post by lovinglinux on 2011-05-21
> **coffeecat said:**
> I think there's a problem with whichever server mozilla uses for add-ons at the moment, and for these last few hours. I'm trying to get adblock plus into a fresh install of Natty and the addons thingy in Firefox just sits there for ever saying, "Downloading". It isn't.

It seems you are right, because I just received a similar report about NoScript.

Right-click the button to install the add-on on Mozilla AMO site, select "Save link as" to download and save it to your hard drive, then drag the downloaded xpi file to a Firefox window to install it.

---

### Post by Tekmoor on 2011-05-21
I tried this beta and it doesn't use global menu, is that normal?

---

### Post by lovinglinux on 2011-05-21
> **Tekmoor said:**
> I tried this beta and it doesn't use global menu, is that normal?

If you installed manually, then it doesn't use the global menu.

---

### Post by Larkspur on 2011-05-21
> **lovinglinux said:**
> If you installed manually, then it doesn't use the global menu.

If that's the case, could he copy the extension from /usr/lib/firefox-addons/extensions into his local profile?

---

### Post by Tekmoor on 2011-05-21
Thanks for the replies. I just used the binary from [https://www.mozilla.com/en-US/firefox/channel/](https://www.mozilla.com/en-US/firefox/channel/)

I can wait for the *firefox-next* ppa, or what is the appropriate way to install beta releases?

Edit: @lovinglinux I just read your tutorial on installing other versions, that's helpful! I knew about ubuntu-mozilla-daily but did not want to use it so I'm grateful to hear of firefox-next ppa, which I hadn't head of until just now.

---

### Post by lovinglinux on 2011-05-21
> **Larkspur said:**
> If that's the case, could he copy the extension from /usr/lib/firefox-addons/extensions into his local profile?

Nope. I just tested and it doesn't work.

> **Tekmoor said:**
> Thanks for the replies. I just used the binary from [https://www.mozilla.com/en-US/firefox/channel/](https://www.mozilla.com/en-US/firefox/channel/)

I can wait for the *firefox-next* ppa, or what is the appropriate way to install beta releases?

Best way is to use *firefox-next* ppa. However you can use the non-official [SilverWave]("http://ubuntuforums.org/showthread.php?t=1352580") ppa.

---

### Post by slooksterpsv on 2011-05-21
I'm using 6.0 Alpha 1 from the Nightly-Trunk.

It's not bad, not too different from 4.

---

### Post by kansasnoob on 2011-05-21
I've used Opera for just a few specific things for quite some time, but FF4 has been so bad I find myself using Opera for more and more things.

I hope FF5 and onward are better :)

---

### Post by donniezazen on 2011-05-22
> **slooksterpsv said:**
> I'm using 6.0 Alpha 1 from the Nightly-Trunk.

It's not bad, not too different from 4.

I too am using firefox-trunk 6.0a1. I find it more tuned to Ubuntu, i have always found ff more stable than chrome, less resource intensive and as fast as chrome. The only thing i miss is omnibar.

---

### Post by lovinglinux on 2011-05-22
> **soham_1207 said:**
> The only thing i miss is omnibar.

[https://addons.mozilla.org/en-us/firefox/addon/prospector-awesomeBar-HD/](https://addons.mozilla.org/en-us/firefox/addon/prospector-awesomeBar-HD/)

[https://addons.mozilla.org/en-us/firefox/addon/omnibar/](https://addons.mozilla.org/en-us/firefox/addon/omnibar/)

---

### Post by donniezazen on 2011-05-22
> **lovinglinux said:**
> [https://addons.mozilla.org/en-us/firefox/addon/prospector-awesomeBar-HD/](https://addons.mozilla.org/en-us/firefox/addon/prospector-awesomeBar-HD/)

[https://addons.mozilla.org/en-us/firefox/addon/omnibar/](https://addons.mozilla.org/en-us/firefox/addon/omnibar/)

Omnibar might not work with 6.0a1. I will try it with nightly tester tool later this evening.

---

### Post by lovinglinux on 2011-05-22
> **soham_1207 said:**
> Omnibar might not work with 6.0a1. I will try it with nightly tester tool later this evening.

Have you tried the Awesomebar HD from Mozilla labs?

---

### Post by donniezazen on 2011-05-22
> **lovinglinux said:**
> Have you tried the Awesomebar HD from Mozilla labs?

I will do that when i reach home later today.

---

### Post by VinDSL on 2011-05-22
> **kansasnoob said:**
> I've used Opera for just a few specific things for quite some time, but FF4 has been so bad I find myself using Opera for more and more things.

I hope FF5 and onward are better :)
One thing that I really, really, really like about Opera is, you can place the tabs on the bottom.

I know this *sounds* like a silly trick, but it works out much better for me.

I wish the Fx and Chromium/Chrome would copy this idea!

---

### Post by lovinglinux on 2011-05-22
> **VinDSL said:**
> One thing that I really, really, really like about Opera is, you can place the tabs on the bottom.

I know this *sounds* like a silly trick, but it works out much better for me.

I wish the Fx and Chromium/Chrome would copy this idea!

Firefox can do that with [Tree Style Tab]("https://addons.mozilla.org/en-US/firefox/addon/5890/") add-on. However, Opera tabs are very elegant.

Personally, I prefer the tabs on the right.

---

### Post by VinDSL on 2011-05-23
> **lovinglinux said:**
> Firefox can do that with [Tree Style Tab]("https://addons.mozilla.org/en-US/firefox/addon/5890/") add-on. However, Opera tabs are very elegant.

Personally, I prefer the tabs on the right.
Thanks!  I'll try those...

I don't want to hijack this thread, but here's Opera with tabs on the bottom:


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-23-may-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-23-may-2011.png")[/INDENT]


All browsers are starting to look the same, because they copy each other.

I just can't figure out why Opera is the only one that allows you to change the location of the tabs (et cetera)...  ;)

---

### Post by slooksterpsv on 2011-05-23
> **VinDSL said:**
> Thanks!  I'll try those...

I don't want to hijack this thread, but here's Opera with tabs on the bottom:


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-23-may-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-23-may-2011.png")[/INDENT]


All browsers are starting to look the same, because they copy each other.

I just can't figure out why Opera is the only one that allows you to change the location of the tabs (et cetera)...  ;)

Cause a lot of features that Firefox and IE started to get were a direct result of what Opera was already doing. If you look at like some of the old versions and compare that to when like FF2 or FF3 was released, you'll see that Opera actually already had a bunch of those features. Specifics? I can't remember.

So a lot of browsers have ripped from Opera quite a bit. It's sad, but amazing at the same time =D.

---

### Post by cariboo on 2011-05-23
> **slooksterpsv said:**
> Cause a lot of features that Firefox and IE started to get were a direct result of what Opera was already doing. If you look at like some of the old versions and compare that to when like FF2 or FF3 was released, you'll see that Opera actually already had a bunch of those features. Specifics? I can't remember.

So a lot of browsers have ripped from Opera quite a bit. It's sad, but amazing at the same time =D.

There's a Heinlein quote from [Glory Road]("http://en.wikipedia.org/wiki/Glory_Road") that seems to fit open source software more often than not:

> "That's the way with writers; they'll steal anything, file off the serial numbers, and claim it for their own."

---

