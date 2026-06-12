---
title: "Booting to purple screen"
date: 2014-03-20
forum: New to Ubuntu
---

### Post by HarisShahzad on 2014-03-20
I installed Ubuntu like a week ago
Everything was working fine when it stopped booting. It would hang at the purple screen. I had to press the power button to turn it off and then turn it back on. The GRUB boot menu came up. When I tried to normally boot from there, it wouldn't work. However when I went to recovery and booted from there, it booted although the resolution, if thats the correct word for it was all messed up. The text was large etc. I restarted. Again same. I ran Boot Repair and now I can boot normally without going to recovery option but I now face two issues
a) It takes a long time to go past the purple screen, i.e booting is now slow
b) The GRUB menu opens every time. I would prefer direct booting

---

### Post by PotatoHead007 on 2014-03-20
Hi :) 
As to your first question, no idea about that :/
The second question should be solved by the following:

Navigate to /etc/default, and open the file called "grub" with a text editor. 
In this file you will see lines that look something like this: ```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10

```
This should be near the top of the document. 
Mine shows GRUB_DEFAULT=0 because my grub does not show up on boot, but yours should be GRUB_DEFAULT=1.
Change: ```
GRUB_DEFAULT=1
``` to ```
GRUB_DEFAULT=0
```
After you have saved and closed the file, run ```
update-grub
``` in terminal to update the grub config file.
That should do it :)

**EDIT: **You may have to open the file with ```
sudo gedit grub
``` The update-grub command needs sudo too.

---

### Post by silex89 on 2014-03-20
Hi there and welcome! :D

Are you using a WiFi connection with a proxy or something else to connect to internet? The long time could be because the Network Manager daemon takes too long to get an IP address.

Also, are you running Ubuntu alongside a Windows 8/8.1 installation?

---

### Post by 7sbaV8Kt5PTh on 2014-03-20
On the first question, there is a lot going on behind the purple screen.  I had a similar experience, It turned out to be trying to boot PXE and was hanging until it times out.  I've seen a driver mismatch do this too.  The best thing to do is look in /var/log/syslog and boot.log and see what was happening during that boot sequence.  In boot.log, you should see something like this, maybe with an error in it:

fsck from util-linux 2.20.1
/dev/sda1: clean, 97545/121544704 files, 8758001/486147328 blocks
 * Starting configure network device security                            [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting configure network device                                     [ OK ]
 * Starting Mount network filesystems                                    [ OK ]
 * Starting Upstart job to start rpcbind on boot only                    [ OK ]
 * Starting Failsafe Boot Delay                                          [ OK ]
 * Stopping Upstart job to start rpcbind on boot only                    [ OK ]
 * Starting load fallback graphics devices                               [ OK ]
 * Starting Userspace bootsplash                                         [ OK ]
 * Starting Send an event to indicate plymouth is up                     [ OK ]

---

### Post by grahammechanical on 2014-03-20
For your information when we use the Recovery menu Resume option Ubuntu will load without using the proprietary video driver. Instead we will be running on the Gallium llvmpipe video driver that Ubuntu uses as a fallback video driver. Gallium llvmpipe can be used to give an approximation of Unity 3D on graphic adapters that do not have hardware video acceleration capabilities. It is the use of the Gallium llvmpipe driver that produces the large icon effect and the slow window movement effect that you were seeing.

You may wish to experiment with a different video driver. If you are using Ubuntu 13.10, then go to System Settings>Software and Updates>Additional Drivers tab and wait for the OS to find a selection of drivers. You need to be connected to the Internet.

Regards.

---

### Post by HarisShahzad on 2014-03-20
Grub timeout was set to 10 ._.
Thanks brother!
As for the video driver
I have three driver options in additional driver packages
One is the one i have installed
One is experimental beta release
One says post release update
Thing is, i have tried the other two and my dota doesnt run with them :'(
So i have to stick to this one
Or would they run with 13.10 cause i have 12.04 currently
Should i upgrade?

---

