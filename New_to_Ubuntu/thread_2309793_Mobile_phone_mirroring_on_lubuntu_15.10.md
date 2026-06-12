---
title: "Mobile phone mirroring on lubuntu 15.10"
date: 2016-01-13
forum: New to Ubuntu
---

### Post by nginmu on 2016-01-13
On Windows 7 I used a software by the name of Mobizen to allow me to connect to my Android mobile phone over a USB cable, and have an image of it appear on the PC screen.

I could use the mouse pointer and buttons to operate the mirrored image of the phone just as if it were the actual phone itself. Any changes I made, immediately appeared on both the PC monitor image, and the phone itself.

I could initiate a call from the PC, read & send SMS messages etc.

The beauty of this was that the phone itself could stay on the windowsill, where the signal was good and it was getting constantly charged.. & I didn't have to keep leaping up out my chair to use the phone for it's normal functions.

I should say I was/am using the phone's wifi hotspot for internet access so it was nice to just leave it where it is, and make and receive calls and SMS when necessary using the mirror on the PC screen.

What's the best way of doing this sort of thing in lubuntu? If anybody can suggest anything that would be good.

---

### Post by DuckHook on 2016-01-13
Hi nginmu

I don't know of any one app that will do what you want. However, there is a combination of apps that, together, do what you are looking for. Please note that Linux has a different philosophy from Windows. The Linux philosophy is to build one app for one thing only, but to build it well. Therefore, you will have to use a suite of apps to achieve the same goals.

1. You will have to install Chromium (if you are a stickler for open source) or Chrome (if you don't care about the philosophy and just want it to work). Chromium is available in the repositories. Chrome will have to be installed from Google's website.

2. To make calls from your computer, you will need Viber. This is also only available from Viber and is not in the repositories. You may also wish to install Viber in your phone. They will share contact databases and call histories if you link them up in this way, but you are not actually calling through your phone. Instead, you are calling using Viber's VOIP network, which is independant of your phone or its network provider. However, Viber calls are free to other cell networks. There is an insignificant charge to land lines ($10 will probably last you all year).

3. For SMS, you will need to install Pushbullet in both your phone and in Chromium/Chrome. This allows your phone to communicate with your computer using the Chromium/Chrome system calls whenever an SMS pops up on your phone. You can also initiate text messages from your computer at any time. Pushbullet also has a few other bells and whistles, but I use it exclusively for SMS and have never explored its other powers. To my knowledge, Pushbullet is available only in Chrome's web store and uses Chrome's APIs to deliver content. It may also work with FireFox, but I haven't tried.

4. Ubuntu is getting better and better with each version at exchanging files, synchronizing music and photos, etc, right out of the box. I use the default program bundled with Ubuntu, Rhythmbox, for my music synching and it works fine. Photos are simply transferred using Nautilus. Since you are on Lubuntu, you can try its default apps, Audacious and PCManFM. I don't use Lubuntu as my main OS, so you will have to do your own explorations there.

5. I have a bluetooth linking home phone for any calls that come through my cell, or that I may wish to call out using my cell. This phone has 5 extension sets that allow me to receive incoming calls throughout the house. I could be in the basement or upstairs and still hear, receive and make calls.

Using this setup, I can leave my cell on the recharging shelf in the living room and never have to get out of my chair to use any of the features that are most important to me.

Hope this helps.

If anyone has better workarounds or solutions for this, please feel free to chime in. I am eager to hear them.

---

