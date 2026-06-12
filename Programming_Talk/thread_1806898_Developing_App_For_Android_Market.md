---
title: "Developing App For Android Market"
date: 2011-07-18
forum: Programming Talk
---

### Post by NoFriends on 2011-07-18
Hi,

I've been been some researching on developing an application for Android.

But I'm stuck on where and how to start, Does anyone know where i can start
using ubuntu 11.04.

I'm really looking to build a test to start with, for me to be able to see how it functions, progressing and polishing up on features, before making it live...and how would i make it live on the market.

All help would be highly appreciated. :KS

---

### Post by akand074 on 2011-07-18
Download eclipse from the repositories. Download and install the Android [SDK]("http://developer.android.com/sdk/index.html") using the Ubuntu instructions. Go to the android [market]("https://market.android.com/") and make a market account (25$ one time fee I believe, go to my market account at the bottom). Then code away.

---

### Post by NoFriends on 2011-07-20
I have to pay $25 for a free application ? I don't think I'll bother if that's the case.

Thanks for the information.

---

### Post by PaulM1985 on 2011-07-20
I think you have to pay to join the market so that you can put games on it.  You certainly don't have to pay just to develop yourself.

Paul

---

### Post by SevenMachines on 2011-07-20
Eclipse is especially well integrated for android development. Essentially,
* Get eclipse
* Get android sdk
* Get eclipse android plugin

This is well described in 
[http://developer.android.com/sdk/installing.html#Preparing](http://developer.android.com/sdk/installing.html#Preparing)

This gives you a full android development environment to get started prgramming android apps. 
When you want to test your app you can
* Use the full android emulator that comes with the sdk and is integrated into eclipse
* Or use the adb tool that comes with the sdk to upload it to your android phone, if it supports it
* Or use adb to upload it to android-x86 running inside something like virtualbox

Once you're happy with your app and want to upload it to the android market, thats the time you need to register as an android developer with google with a one-time $25 fee. From googles blurb...
> You must register to be able to distribute your products through Android  Market. There is a one time $25 registration fee. We charge this fee to  encourage higher quality products on the market (e.g. less spammy  products).I'll leave it to your own judgement as to if it has encouraged 'less spammy products' :)

Just to emphasise though, market registration isnt needed to develop, debug, test, and even use the app on your own phone if you want.

---

### Post by NoFriends on 2011-07-20
So i only have to pay $25 to place them on the Market, that's fine, I'll only be producing and experimenting on apps which i would like to test.

When doing this on eclipse, how would i go about testing it to see how the application would look ?

---

### Post by PaulM1985 on 2011-07-20
When you run your app a little emulator starts up so you can see your app and use it.

Paul

---

### Post by NoFriends on 2011-07-20
> **PaulM1985 said:**
> When you run your app a little emulator starts up so you can see your app and use it.

Paul

Thanks Paul

When i get some time i will install everything needed and will see how things work out.

Thanks for all your help.

---

### Post by SevenMachines on 2011-07-20
The android sdk comes with a full emulator for android devices, this is integrated into eclipse run/debug also with the adt plugin.
The emulator can run any number of devices you set up to cover for instance, different android version, screen sizes, sdcard sizes, and so on that you want to test. Other options i've mentioned are
* Android x-86 port running on something like virtualbox
[http://www.android-x86.org/](http://www.android-x86.org/)
* Using the android sdk's adb tool to push your app to your own phone

But since the emulator allows testing on such a large variety of devices and android versions so easily, its probably the one you'll want to use the most to check your apps look and behaviour on a range of devices

Attached you can see android in virtualbox and an android device running in the emulator directly from eclipse

---

### Post by NoFriends on 2011-07-20
That's fantastic.


Thanks all. :D

---

### Post by akand074 on 2011-07-20
You can also test it on your Android device directly if you have one.

---

### Post by NoFriends on 2011-07-21
> **akand074 said:**
> You can also test it on your Android device directly if you have one.


How can i go about doing this directly on my android ?

I have setup eclipse along with Android SDK and the plug-ins required, to give me the VMD aswell.

But, how can i go about directly testing on my device. ?

---

### Post by moma on 2011-07-21
Hello,
Step 10) of this guide may help you.
[http://www.futuredesktop.com/maverick/android/developing_android_apps_on_ubuntu.html](http://www.futuredesktop.com/maverick/android/developing_android_apps_on_ubuntu.html)

---

