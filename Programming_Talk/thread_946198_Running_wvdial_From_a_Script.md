---
title: "Running wvdial From a Script"
date: 2008-10-13
forum: Programming Talk
---

### Post by igb on 2008-10-13
I want to be able to send an email from a computer automatically via Bluetooth Dialup. I have the BT dialup part working correctly via wvdial. So what I want to do is call wvdial ins a script and once it's connected send my email then disconnect.

The problem is that wvdial doesn't return when it's connected, so it's difficult to use in a script. My idea is to fork wvdial then sleep for a few seconds to give it a chance to connect. I can then send my email and killall -9 wvdial.

Can anyone think of a method of telling from within my script if wvdial has connected? Also is there a better way of doing the whole thing?

Ian.

---

