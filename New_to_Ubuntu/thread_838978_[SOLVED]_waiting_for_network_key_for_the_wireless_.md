---
title: "[SOLVED] waiting for network key for the wireless network"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by whispermeaverage on 2008-06-24
Hi, I'm as beginner as you get, and already causing mayhem  :-k
My only source of Linux help is currently unavailable so I've been tinkering with my Hardy 8.04 myself and have run into some problems. 

My friend had set up the wireless on my Dell Inspiron 1525 by doing what he posted on:
[http://ph.ubuntuforums.com/showthread.php?t=815293]("http://ph.ubuntuforums.com/showthread.php?t=815293")

However, I kept getting prompted with "nm applet wants to get access to keyring but it is locked" when I signed on, so I followed the instructions on one of the forums (sorry I can no longer find it) and changed the unlock password in 'Encryptions and Keys' to a blank password. I stopped getting prompted but my wireless stopped connecting altogether and now it just hangs on "waiting for network key for the wireless network". 

I spent the whole night following different instructions,and doing god knows what to my computer. I even went through the whole tutorial that my friend had already gone through  [http://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc]("http://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc") only to get this as the end result: 

ru@toaster:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have no clue what I'm doing and I really don't want to cause any more damage, help?

I should mention that I'm also running Vista and the wireless is working fine there.

P.S. Feel free to dumb everything down for me :grin:

Thanks in advance!!

---

