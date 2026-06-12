---
title: "Wireless help"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by munchkin360 on 2008-10-29
I have an elonex webbook (free with mobile phone) and the wireless was working fine till me being silly me accidently turned the wireless adaptor off but hitting Fn + F1.

I had a fiddle about and it would not work then I noticed that the wireless was still off (silly silly me).

I hit Fn + F1 to turn it back on but its not turning it on. Have tried shutting down and restarting but I cannot get Fn + F1 to work. all the other Fn + F? keys work fine, have even set Caps Lock to a second Fn key and thats not working.

So my question is, is there any other way I can turn the wireless on to see if that solves my problem.

Many thanks.

---

### Post by munchkin360 on 2008-10-29
Anyone? I am on my windows machine but could really do with getting the webbook online again

---

### Post by twisted_steel on 2008-10-29
Did the connection completely stop working, or is the light no longer coming on?  I read a post about there being a problem with some of the earlier releases (maybe also yours if you did the complete reinstall) where the light wouldn't show up all of the time.

[http://webbookblog.com/?p=41](http://webbookblog.com/?p=41)

This thread on the forums has similar instructions: [http://ubuntuforums.org/showthread.php?t=871195](http://ubuntuforums.org/showthread.php?t=871195).

Does the Network Manager icon in the tray show any wireless access points?  If you on wireless, it will either show a few bars or I believe it will have a little 'x' if it is not connected.

You can try bringing up a Terminal (Applications -> Accessories -> Terminal) and seeing if you can ping Google.  Type
```
ping google.com
```in the window and see if you get any responses.  After a few, or if nothing happens, just press CTRL+C (Control key and C at the same time).  If nothing happens, in that same terminal, see if you have any wireless network interfaces listed with the following command:
```
iwconfig
```Does anything show up?

---

