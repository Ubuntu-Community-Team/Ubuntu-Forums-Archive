---
title: "Gamepad No Longer Connects To Laptop After Testing Game"
date: 2017-04-20
forum: Programming Talk
---

### Post by ezacharyk on 2017-04-20
I am making a game with HaxeFlixel. I have added gamepad support and was testing it using my AfterGlow PS3 wireless controller. This controller uses a USB dongle to connect. I tested the game without a controller plugged in to make sure it worked and my next test was to disconnect the controller while the game was running. This caused my game to lock up. That isn't my problem right now though. Now my controller won't connect to my laptop at all. It still connects to the PS3 and to my other Ubuntu laptop that I didn't run the test on. 

JSTest doesn't see it either. I even tried my other Afterglow controller (same model different pad and different dongle) and it doesn't connect either. So it seems to me that something in my system has decided it doesn't like these controllers.

My Ouya controller, that is connected via Bluetooth, still connects. So do all the other brands of controllers I have.

I restarted my laptop since this happened and that hasn't helped. I have pulled the batteries from the controller. Nothing seems to work.

Any ideas on how to reconnect the controller?

---

### Post by ezacharyk on 2017-04-22
I managed to fix my controller issue by completely purging XBoxdrv from my system and reverting back to the default XPad drivers. Doing so also fixed the minor button configuration issues with my XBox 360 controller. 

Moral of the story is to not use XBoxdrv.

---

