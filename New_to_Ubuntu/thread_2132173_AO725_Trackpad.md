---
title: "AO725 Trackpad"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by zxcvbnmelvin on 2013-04-04
After I installed the ubuntu 12.04 LTS, it seems to be that the trackpad is not working even i press **Fn+F7** . Then i searched in this forum about my problem,and then i saw this code, I'm very happy that this works properly after restart. But then after several restart after the updates it seems not to work again :( i reopen the xorg.conf but codes is still there and copy and paste then save this same code again for it to work again. what must be the problem wit this. Thanks a lot.



sudo gedit /etc/X11/xorg.conf
Section "InputClass"	Identifier "ETPS/2 Elantech Touchpad"	MatchProduct "ETPS/2 Elantech Touchpad"	MatchDevicePath "/dev/input/event*"	Driver "synaptics"	Option "TapButton1" "1"	Option "TapButton2" "3"	Option "TapButton3" "2"	Option "VertTwoFingerScroll" "1"	Option "HorizTwoFingerScroll" "1"	Option "CoastingSpeed" "10"	Option "EdgeMotionMinZ" "30"	Option "EdgeMotionMaxZ" "40"	Option "EdgeMotionMinSpeed" "100"	Option "EdgeMotionMaxSpeed" "400"	Option "FingerLow" "9"	Option "FingerHigh" "12"	Option "EmulateMidButtonTime" "0"	Option "ClickPad" "True"	Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"EndSection

---

### Post by zxcvbnmelvin on 2013-04-04
here is the thread of this code.

[http://ubuntuforums.org/showthread.php?t=2020719&page=2](http://ubuntuforums.org/showthread.php?t=2020719&page=2)

---

