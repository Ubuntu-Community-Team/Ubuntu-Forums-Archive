---
title: "Trying to get the Android Dev stuff installed"
date: 2012-07-12
forum: Programming Talk
---

### Post by Vanillalite on 2012-07-12
Running Ubuntu 12.04 and trying to install all of the android stuff.

I decided to get more up to date versions of things so I downloaded Eclipse 4.2 from the web verses grabbing it from the Software Center. I also installed OpenJava 7.

I got the link to add the repository from Google for Ecplise 4.2 from [Google Developer Docs]("https://developers.google.com/eclipse/docs/install-eclipse-4.2") and the link worked.

I installed a few things to get things going, but I got a couple errors. When I go back to see if things installed correctly though it acts like everything is installed.

So I moved onto Android SDK Manager and selected all I wanted from that too. Everything seemed to install fine there as well except for one Motorola deal where it wanted me to login so I just skipped it.

Problem comes in now when I try to load up the Android Virtual Device manager. I can click to add new device, create a name, select what version of Android I want out of what I downloaded from the SDK Manager, and set how much space to give the SDK Card. Then I'm ready to create, and I hit create AVD. Now Create AVD isn't greyed out or anything, but clicking on it does nothing. I'm sort of at a loss in this regard on how to get that working.

Also besides getting that working is there anything else I really need to do or am I go to go to start coding away for Android in Ubuntu?

---

### Post by satsujinka on 2012-07-13
I had similar problems while trying to install the SDK on a 64 bit install of Arch Linux. So just to check, what version of Ubuntu (32 or 64bit) are you using? And did you install the 32bit libraries? (I would hope that the SDK deb does this for you, but I don't know.)

Also could you run the AVD from the commandline and post the output?

---

### Post by Dr Belka on 2012-07-13
> **Vanillalite said:**
> 

Also besides getting that working is there anything else I really need to do or am I go to go to start coding away for Android in Ubuntu?


All you need to start coding for Android is Eclipse, the ADT Eclipse plugin, and the Android SDK zip file you download from the Android developers website.  That's basically all you need! Having things like GIMP and Audacity are nice too...

As for the error you are getting: that is so strange.  Every time I set any computer up for Android development, I always hit a few snags.  This is by no means the ideal solution, but what I would do is install the Eclipse version from the Software Center (because that one has worked for me so far) reinstall the ADT plugin and reinstall the Android SDK.  

Also, I'm guessing the Motorola login thing you are talking about is from one of the packages you downloaded via the Android SDK manager.  You don't have to download all of the packages, only the ones you need.

---

### Post by Dr Belka on 2012-07-13
> **satsujinka said:**
> I had similar problems while trying to install the SDK on a 64 bit install of Arch Linux. So just to check, what version of Ubuntu (32 or 64bit) are you using? And did you install the 32bit libraries? (I would hope that the SDK deb does this for you, but I don't know.)

Also could you run the AVD from the commandline and post the output?

When running on a 64 bit system, try installing the ia32-libs package.  That fixes alot of errors for me.

---

### Post by satsujinka on 2012-07-13
> **Dr Belka said:**
> All you need to start coding for Android is Eclipse, the ADT Eclipse plugin, and the Android SDK zip file you download from the Android developers website.  That's basically all you need! Having things like GIMP and Audacity are nice too...

As for the error you are getting: that is so strange.  Every time I set any computer up for Android development, I always hit a few snags.  This is by no means the ideal solution, but what I would do is install the Eclipse version from the Software Center (because that one has worked for me so far) reinstall the ADT plugin and reinstall the Android SDK.  

Also, I'm guessing the Motorola login thing you are talking about is from one of the packages you downloaded via the Android SDK manager.  You don't have to download all of the packages, only the ones you need.

Interestingly, I find the eclipse download on eclipse.org to work best. Of course, I like it because I can setup throw away environments (just delete the folder I unzip it to) which is helpful if you're doing something new.

@Vanillalite
As Dr Belka said, if you're running 64bit Ubuntu the ia32-libs  package is necessary.

---

### Post by Dr Belka on 2012-07-13
> **satsujinka said:**
> Interestingly, I find the eclipse download on eclipse.org to work best.

That was definitely the case for me until the Juno release.

---

