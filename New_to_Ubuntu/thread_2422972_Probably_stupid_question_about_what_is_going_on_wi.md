---
title: "Probably stupid question about what is going on with my computer"
date: 2019-07-15
forum: New to Ubuntu
---

### Post by dora5 on 2019-07-15
I am running Ubuntu 18.04 on an Intel board with a 2nd generation i5 processor.   

For the past several days I've come home from work or gotten up in the morning, to find that Ubuntu appeared to have rebooted.  It is set for the sort of running updates that doesn't cause it to reboot and shouldn't be doing that every day.   

Specifically I've got the login after booting up screen and not the raise the screensaver and log in because the screensaver went on (and eventually the screen went dark) after I've not used the computer for awhile.   I have a three monitor setup and those two logins aren't on the same monitor.   

When I get logged in I find that my browser, which was open, closed, which again is consistent with the computer rebooted.

The computer is set in settings to never enter suspend state.  Google tells me that is the same thing as hibernate and sleep?

But when I check my logs to find out what happened, I consistently find that the computer was running all along.  Stuff was getting entered in the log.  So it didn't reboot.   Or, if it did, it didn't wait for me to start doing stuff on the computer to begin entering stuff in the system log.   

What is going on?

Is there anything I should search a specific log for to see if it did in fact reboot, and since the system promptly began doing stuff and entering it into the log, scrolling through the log doesn't reveal a time during which the computer was not running?   

Also, specifically how do I search the log file?

Sorry if everyone knows the answer to that but me.   I used Ubuntu 14.04 several years ago and just installed and began using 18.04, so there might be something very obvious I don't know.

Thanks for explaining!

Yours,
Dora Smith

---

### Post by dora5 on 2019-07-15
I found how to learn if my system rebooted.   It even gives sort of clues why. 

But I have more trouble.  I can't make out what time it occurred!

Here is the top entries.  It says that today, July 15, my computer never rebooted, but yesterday, when it acted the same way, it DID reboot. 

```
dora@dora-desktop-ubuntu:~$last
dora     :0          :0               Mon Jul 15 19:11   still logged in
reboot   system boot 4.18.0-25-generi Mon Jul 15 19:10   still running
dora     :0          :0               Mon Jul 15 18:48 - 19:07  (00:19)
**reboot   systemboot  4.18.0-25-generi Mon Jul 15 12:31 - 19:07  (06:35)**
**dora     :0          :0               Sun Jul 14 07:37 - crash (1+04:53)**
reboot   system boot 4.18.0-25-generi Sun Jul 14 07:10 - 19:07 (1+11:57)
dora     :0          :0               Sat Jul 13 19:04 - crash  (12:05)
reboot   system boot 4.18.0-25-generi Sat Jul 13 19:04 - 19:07 (2+00:03)
dora     :0          :0               Sat Jul 13 17:12 - 18:55  (01:43)
reboot   system boot 4.18.0-25-generi Sat Jul 13 17:11 - 18:57  (01:46)
dora     :0          :0               Fri Jul 12 21:20 - down   (19:50)
reboot   system boot 4.18.0-25-generi Fri Jul 12 21:19 - 17:10  (19:51)
dora     :0          :0               Fri Jul 12 06:14 - 20:22  (14:07)
```


"crash" seems self explanatory, but what does "down" mean?    

What I'm most having trouble with is the time.   What time did this system reboot?

On Sunday, did my computer crash and reboot at 12:31 AM, 12:31PM, 7:07 PM, or 7:37 no clue if it would be AM or PM?    


I changed BIOS to leave the system shut down if the power fails, but I do not see the usual option to leave the system shut down if it crashes.   


Of course if I know what time an event happened I can find it in the system logs and get a clue what happened  - I hope.

Dora

---

### Post by sevendogs1337 on 2019-07-15
Are you running journalctl -b to get your logs?

---

### Post by dora5 on 2019-07-16
There is evidently a new version of this in ubuntu - logs.

It did it again last night and I couldn't remember the command I used last night, this time I was told to use -x shutdown, which gave me 3:23 AM.   

dora@dora-desktop-ubuntu:~$ who -b
         system boot  2019-07-16 03:23

Now when I run last I find the number that is the time it rebooted.

dora     :0           :0               Tue Jul 16 06:19   still logged in
reboot   system boot  4.18.0-25-generi Tue Jul 16 03:23   still running

Doesn't say it crashed though.    

-x shutdown tells me it wasn't shut down at 3:23.

Here's the output of journalctl-b 

It brings up something at 3:23 but I can't figure out what.

Except that it booted.

```
dora@dora-desktop-ubuntu:~$ journalctl -b
-- Logs begin at Sat 2019-07-06 18:46:21 CDT, end at Tue 2019-07-16 06:32:31 CDT
Jul 16 03:23:59 dora-desktop-ubuntu kernel: microcode: microcode updated early t
Jul 16 03:23:59 dora-desktop-ubuntu kernel: Linux version 4.18.0-25-generic (bui
Jul 16 03:23:59 dora-desktop-ubuntu kernel: Command line: BOOT_IMAGE=/boot/vmlin
Jul 16 03:23:59 dora-desktop-ubuntu kernel: KERNEL supported cpus:
Jul 16 03:23:59 dora-desktop-ubuntu kernel:   Intel GenuineIntel
Jul 16 03:23:59 dora-desktop-ubuntu kernel:   AMD AuthenticAMD
Jul 16 03:23:59 dora-desktop-ubuntu kernel:   Centaur CentaurHauls
Jul 16 03:23:59 dora-desktop-ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x
Jul 16 03:23:59 dora-desktop-ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x
Jul 16 03:23:59 dora-desktop-ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x
Jul 16 03:23:59 dora-desktop-ubuntu kernel: x86/fpu: xstate_offset[2]:  576, xst
Jul 16 03:23:59 dora-desktop-ubuntu kernel: x86/fpu: Enabled xstate features 0x7
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-provided physical RAM map:
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000000000000-0
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x000000000009d800-0
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000000e0000-0
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000000100000-0
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000020000000-0
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000020200000-0
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000040000000-0
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000040200000-0
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000ca85a000-0
lines 1-23...skipping...
-- Logs begin at Sat 2019-07-06 18:46:21 CDT, end at Tue 2019-07-16 06:32:31 CDT. --
Jul 16 03:23:59 dora-desktop-ubuntu kernel: microcode: microcode updated early to revision 0x2f, date = 2019-02-17
Jul 16 03:23:59 dora-desktop-ubuntu kernel: Linux version 4.18.0-25-generic (buildd@lgw01-amd64-033) (gcc version 7.4.0 (Ubuntu 7.4.0-1ubunt
Jul 16 03:23:59 dora-desktop-ubuntu kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-25-generic root=UUID=24029b02-231a-45b8-b4c5-7154e
Jul 16 03:23:59 dora-desktop-ubuntu kernel: KERNEL supported cpus:
Jul 16 03:23:59 dora-desktop-ubuntu kernel:   Intel GenuineIntel
Jul 16 03:23:59 dora-desktop-ubuntu kernel:   AMD AuthenticAMD
Jul 16 03:23:59 dora-desktop-ubuntu kernel:   Centaur CentaurHauls
Jul 16 03:23:59 dora-desktop-ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
Jul 16 03:23:59 dora-desktop-ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
Jul 16 03:23:59 dora-desktop-ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
Jul 16 03:23:59 dora-desktop-ubuntu kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Jul 16 03:23:59 dora-desktop-ubuntu kernel: x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-provided physical RAM map:
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000020200000-0x000000003fffffff] usable
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000040000000-0x00000000401fffff] reserved
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000040200000-0x00000000ca859fff] usable
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000ca85a000-0x00000000ca8a4fff] ACPI NVS
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000ca8a5000-0x00000000ca8acfff] ACPI data
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000ca8ad000-0x00000000cabc8fff] reserved
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000cabc9000-0x00000000cabc9fff] usable
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000cabca000-0x00000000cabd9fff] reserved
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000cabda000-0x00000000cabe7fff] ACPI NVS
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000cabe8000-0x00000000cac0ffff] reserved
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000cac10000-0x00000000cac52fff] ACPI NVS
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000cac53000-0x00000000cae8dfff] reserved
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000cae8e000-0x00000000caffffff] usable
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000cb800000-0x00000000cf9fffff] reserved
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Jul 16 03:23:59 dora-desktop-ubuntu kernel: BIOS-e820: [mem 0x0000000100000000-0x000000042fdfffff] usable
Jul 16 03:23:59 dora-desktop-ubuntu kernel: NX (Execute Disable) protection: active
Jul 16 03:23:59 dora-desktop-ubuntu kernel: SMBIOS 2.7 present.
Jul 16 03:23:59 dora-desktop-ubuntu kernel: DMI:  /DH67BL, BIOS BLH6710H.86A.0119.2011.0523.1030 05/23/2011
Jul 16 03:23:59 dora-desktop-ubuntu kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jul 16 03:23:59 dora-desktop-ubuntu kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
Jul 16 03:23:59 dora-desktop-ubuntu kernel: last_pfn = 0x42fe00 max_arch_pfn = 0x400000000
Jul 16 03:23:59 dora-desktop-ubuntu kernel: MTRR default type: uncachable
Jul 16 03:23:59 dora-desktop-ubuntu kernel: MTRR fixed ranges enabled:
Jul 16 03:23:59 dora-desktop-ubuntu kernel:   00000-9FFFF write-back
Jul 16 03:23:59 dora-desktop-ubuntu kernel:   A0000-BFFFF uncachable
Jul 16 03:23:59 dora-desktop-ubuntu kernel:   C0000-CFFFF write-protect
Jul 16 03:23:59 dora-desktop-ubuntu kernel:   D0000-E7FFF uncachable
lines 1-48
```

---

### Post by dora5 on 2019-07-16
Now I've got logs open to the time when it rebooted, but I"m having trouble getting to the event itself - is there a way to search for it?

---

### Post by dora5 on 2019-07-16
Actually logs starts at the point when it rebooted so it's not telling me about why it rebooted.

---

### Post by dino99 on 2019-07-16
My feeling is you might hit short power cut in your area (can be less that 1 second) and you cant do anything except adding an UPS to secure that power feed, or shutting down your computer when it does not work ;)

---

### Post by mastablasta on 2019-07-16
> **dino99 said:**
> My feeling is you might hit short power cut in your area (can be less that 1 second) and you cant do anything except adding an UPS to secure that power feed, or shutting down your computer when it does not work ;)


or bad PSU.

you need to check the old logs (.old) to see where they stopped logging. i would also add some temp sensors (like psensor) and log the temps. if you want, there are also special log recording applications.

uptime will show how long the PC was working.

---

### Post by Holger_Gehrke on 2019-07-16
The journal does hold records for (far) more than the current session, but by giving the option '-b' without a parameter you asked to see what happened since the last **b**oot. Giving a positive integer after the '-b' will show you the records of previous sessions starting with the oldest session in the journal, negative integers go backwards from the current session. So to see what messages were produced at the end of the last session you should enter 'journalctl -b -1' and look at the end of the output. If the power cut out you'd probably not see anything there relating to a controlled shutdown. If something crashed so badly a reboot was necessary to get things back under control then there should be some related messages in the journal.

Holger

---

### Post by CatKiller on 2019-07-16
It's also worth noting (I'm not going to trawl through your logs on my phone) that the symptoms you describe would cover an X crash just as much as a restart. It wouldn't show up that your uptime was interrupted, because it *hadn't* been interrupted: just the applications that have windows.

---

### Post by dora5 on 2019-07-17
Thx for hardware suggestions, they are good ones.  I do have bios set not to boot up from power failure.   Sup at work said check bios events which shows nothing.

  Logs goes back further than 1 boot but 1st thing this am I forgot that.  

I'll discuss usb power thing at work tomorrow and do the temp sensors.  Been struggling w clonezilla so no more work on logs today.

---

