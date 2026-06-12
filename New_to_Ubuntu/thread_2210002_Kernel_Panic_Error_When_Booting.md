---
title: "Kernel Panic Error When Booting"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by Joseph_Dye on 2014-03-08
Hello,

About two weeks ago I installed Ubuntu 13.10 from a bootable USB and at first everything was fine. Now however, something has gone wrong. When I turn my laptop on I get the password prompt - not the one to log into my account but the one that appear just after turning it on - and after entering my password the screen goes blank and some text appears.

> 
[ 245.307033] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000100
[ 245.307033]
[ 245.307071] CPU: 3 PID: 1 Comm: runit Not tainted 3.11.0-17-generic #31-Ubuntu
[ 245.307095] Hardware name: Hewlett-Packard HP ENVY Sleekbook 4 PC/1894, BIOS F.23 01/15/2013
[ 245.307123]  ffffffffff81c450a0 fff8802b39e1e70 fffffff816e7654 ffffffffff81a40d48
[ 245.307150]  ffff8802b39e1ee8 fffffffff816e1589 fffffff00000000 ffff8802b39e1ef8
[ 245.307176]  ffff8802b39e1e98 fff8802b3978630 000000000100 ffff8802b3978390
[ 245.307202] Call Trace:
[ 245.307217]   [<ffffffff816e7645>] dump_stack+0x45/0x56
[ 245.307235]   [<ffffffff816e1589>] panic+0xc8/0x1d7
[ 245.307254]   [<ffffffff81064906>] do_exit+0x926/0xa40
[ 245.307272]   [<ffffffff816ec400>] ? __scedule+x3b0/0x7e0
[ 245.307292]   [<ffffffff81064a57>] SyS-exit+0x17/0x20
[ 245.307311]   [<ffffffff816f74dd>] system_call_dastpath+0x1a/0x1f
[ 245.307358] drm_kms_helper: panic occurred, switching back to text console


After this message appeared I left my laptop on for an hour and nothing else happened. To try and fix this problem I made a Ubuntu 13.10 bootable USB and I was going to re-install Ubuntu but when I I tried to boot off of it it was not recognized. I tried to boot of a Ubuntu 13.10 USB with three different USB's but none of them were recognized.

When I entered the Boot Device Options nnone of my memory sticks were shown and instead three other things were shown.

> 
ubuntu (St500L T012-9WS142)  --> This is the first option that is shown.
Ubuntu (St500L T012-9WS142)  --> This is the second option that is shown. The difference is that the U is capitalized.
Boot From EFI File                    --> This is the third option.


When I select the first option it takes me to a GRUB menu where I can select to load Ubuntu which gives me the Error shown above, I can choose to go into Advanced options for Ubuntu and  can go into System setup. When I have tried these options Nothing has happened.

If anyone who reads this post can help me either fix the kernel panic error or tell me how to fix the Boot Device Options so that I can re-install Ubuntu I would be most appreciative.

Thanks in advanced for your help.

EDIT: When I put a USB with dban autonuke on it into my pc the screen starts flashing from a dark grey to black over and over again.

---

