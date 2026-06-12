---
title: "To use Skype 4.1.0.20 webcam in Ub 12.10"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by ReleaseRoderick on 2013-04-27
Compaq Presario 1429UK with Ub 12.10. 32 bit + Logitec Quick Cam Messenger.
Works fine in Cheese.  Cannot get cam to work in Skype.  In skype>options>video devices there is just a black box where l should see a picture. 
Device: -PX629AA-ABU-SR1429UK-GB520:~$ lsusb
Bus 001 Device 005: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 003 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

From my info searches l have tried:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype  [FONT=arial] also[/FONT]  locate v4l2convert.so   [FONT=arial]but negative result[/FONT].[FONT=arial]
Tried to open Skype in Terminal, Skype opens but neg result again.

Also have found same problem in recent update 12.10 to 13.04 on Com Paq SR1819UK machine. 

Help kindly appreciated.
ian[/FONT]
 
[FONT=arial][/FONT]

---

### Post by ReleaseRoderick on 2013-04-28
Is there a better voip that will run in Ubuntu?

---

