---
title: "Desktop PC randomly freezes ..."
date: 2024-08-01
forum: New to Ubuntu
---

### Post by cwmoser on 2024-08-01
My desktop PC running 22.04 Ubuntu Mate will freeze and stop responding with mouse and keyboard.
This happens every few days to a week or more.
The screen still shows the desktop but no mouse cursor and the keyboard is not responsive.
The only way to recover is the Reset Button and it will boot up and everything works as it should.

Got any ideas?  Is it more of an intermittent hardware problem, or could it be a software issue?

---

### Post by TheFu on 2024-08-01
> **cwmoser said:**
>  Got any ideas?  Is it more of an intermittent hardware problem, or could it be a software issue?

It could be anything of 10,000 issues. The way to narrow down the possible issues are to look at the system logs.  If you note the time that the lockup happens, you can ask journalctl to provide logs from around that time.

Also, providing an overview of the system, software, configuration, and hardware would be helpful to people who recognize common issues with different setups.  **inxi -Fxxz** will help with that.

I have lots of ideas, but without any data, they are just guesses and would waste your time and mine.

---

### Post by euol on 2024-08-03
Check system logs to see if there are any clues:

sudo journalctl -b -1  # View logs from the last boot
sudo dmesg | less      # Kernel messages

---

### Post by cwmoser on 2024-08-15
My desktop PC froze again today Aug15.
I tried **sudo journalctl -b -1** but I get this:
*Specifying boot ID or boot offset has no effect, no persistent journal was found.*

I note that there is a **dmesg.0** log file ... but how to read it in "human form"??

---

### Post by TheFu on 2024-08-15
If the system isn't saving 200MB of logs, you need to change that setting.  That's in the journald.conf file.  There's a manpage that explains what each setting means, if you find the existing comments aren't sufficient.  I've always found the comments more than sufficient.

dmesg.0 is human readable, but it only covers the initial boot, so if the lockups are happening after that, it isn't so useful.

---

### Post by cwmoser on 2024-08-19
I made journalctl persistent and that is neat to recover logs from prior boots.
Then this morning I was at my desktop PC working with LibreOffice Calc and the Keyboard/Mouse hung again with the time on the desktop at **6:07 AM**.
i just let it sit like this until I made coffee, and then came back and RESET my PC.

This is the output of **journalctl -b-1** just before and after 6:07 AM:
```

Aug 19 06:06:09 klaatu-2 kernel: audit: type=1400 audit(1724061969.443:306): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/usr/share/zoneinfo-icu/44/le/timezoneTy>
Aug 19 06:06:10 klaatu-2 kernel: [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:b0:95:75:47:9c:c6:08:00 SRC=192.168.0.201 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Aug 19 06:06:10 klaatu-2 kernel: [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:fb:08:a6:bc:e5:06:41:08:00 SRC=192.168.0.169 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Aug 19 06:06:39 klaatu-2 kernel: [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:fb:aa:b3:68:b1:36:d4:08:00 SRC=192.168.0.165 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=38582 PROTO=2 
Aug 19 06:07:04 klaatu-2 kernel: nouveau 0000:01:00.0: fifo: SCHED_ERROR 0a [CTXSW_TIMEOUT]
Aug 19 06:07:04 klaatu-2 kernel: nouveau 0000:01:00.0: fifo: runlist 0: scheduled for recovery
Aug 19 06:07:04 klaatu-2 kernel: nouveau 0000:01:00.0: fifo: channel 2: killed
Aug 19 06:07:04 klaatu-2 kernel: nouveau 0000:01:00.0: fifo: engine 7: scheduled for recovery
Aug 19 06:07:04 klaatu-2 kernel: nouveau 0000:01:00.0: fifo: engine 0: scheduled for recovery
Aug 19 06:07:04 klaatu-2 kernel: nouveau 0000:01:00.0: fifo: fault 00 [READ] at 0000000080048000 engine 1b [CE2] client 01 [GPC0/T1_0] reason 0c [UNSUPPORTED_KIND] on channel -1 [0108040000>
Aug 19 06:07:04 klaatu-2 kernel: nouveau 0000:01:00.0: fifo: runlist 4: scheduled for recovery
Aug 19 06:07:04 klaatu-2 kernel: nouveau 0000:01:00.0: fifo: engine 4: scheduled for recovery
Aug 19 06:07:04 klaatu-2 kernel: nouveau 0000:01:00.0: fifo: fault 00 [READ] at 0000000080048000 engine 15 [CE0] client 01 [GPC0/T1_0] reason 0c [UNSUPPORTED_KIND] on channel -1 [0108040000>
Aug 19 06:07:04 klaatu-2 kernel: nouveau 0000:01:00.0: Xorg[5822]: channel 2 killed!
Aug 19 06:07:17 klaatu-2 kernel: [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:fb:aa:b3:68:b1:36:d4:08:00 SRC=192.168.0.165 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=22291 PROTO=2 
Aug 19 06:07:58 klaatu-2 kernel: [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:fb:4e:df:09:ae:28:73:08:00 SRC=192.168.0.129 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=13461 PROTO=2 
Aug 19 06:08:15 klaatu-2 kernel: [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:b0:95:75:47:9c:c6:08:00 SRC=192.168.0.201 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Aug 19 06:08:16 klaatu-2 kernel: [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:fb:e4:3b:c9:ff:b1:0d:08:00 SRC=192.168.0.119 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Aug 19 06:08:24 klaatu-2 kernel: [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:fb:d8:be:65:a6:43:18:08:00 SRC=192.168.0.107 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Aug 19 06:08:30 klaatu-2 kernel: [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:fb:4e:df:09:ae:28:73:08:00 SRC=192.168.0.129 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=22359 PROTO=2 
Aug 19 06:08:39 klaatu-2 kernel: [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:fb:aa:b3:68:b1:36:d4:08:00 SRC=192.168.0.165 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=721 PROTO=2 
Aug 19 06:09:12 klaatu-2 kernel: INFO: task kworker/u16:1:2538026 blocked for more than 120 seconds.
Aug 19 06:09:12 klaatu-2 kernel:       Tainted: G           OE     5.15.0-118-generic #128-Ubuntu
Aug 19 06:09:12 klaatu-2 kernel: "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

```

I can't  see anything that indicates what caused this.  The CPU cooling fins are clean and the fans are running.

---

### Post by tea for one on 2024-08-19
> **cwmoser said:**
> ```

nouveau 0000:01:00.0: fifo: SCHED_ERROR 0a [CTXSW_TIMEOUT]
```
Copy the line above and use your favourite search engine for info.
Quite a few links to read.

---

### Post by cwmoser on 2024-08-19
Thanks Tea for one.

I did a search and found posts suggesting it might be the nVidia graphics driver.

I switched drivers:
In Software and Updates -> Additional Drivers, I switched:
From:
Using X.Org X server - Nouveau display driver
To:
Using NVIDIA driver 570 (proprietary, tested)

Now I'm going to test to see if this fixes the issue.

Thanks much.

---

### Post by TheFu on 2024-08-19
Why are you looking only at boot messages?  Why not check for all errors, especially around the time of the lockup?

Looking at the boot messages, I'd guess your video driver is the issue.  If you don't have nvidia, then I'm wrong. If you have nvidia, look for better drivers.

Ah - tea for one already responded.  Your "Additional Drivers" should help, but nVidia drivers can be crap from time to time and eventually, they will drop support.  

If your GPU costs over $1000, that's the price of high-end GPUs - constantly moving the newer, faster, with more pipelines and DRAM.  NVidia is the only game in town for high-end GPUs and they charge whatever they like.

OTOH, if you have a mid-level or low-level GPU, then I would encourage you to consider AMD or Intel GPUs, which have their drivers included in the kernel.  I have an AMD APU from 2012 with drivers that still are supported by the current kernel.  Just something to consider when you open your wallet.

Yes, Intel makes discrete GPUs now.  I don't recall when they first hit the market, but it was over a year ago and back then, linux driver support sucked.  That has probably changed.  I switched to using AMD GPUs/iGPUs with my last system upgrades.  They are 3x better than low-end nvidia and probably 10x better than the Intel iGPUs included with i3/i5/7 CPUs.  I do video editing and HW-based transcoding using the iGPU on my Ryzen 5600G.

---

### Post by cwmoser on 2024-08-19
I don't purchase current state of the art Graphics Cards.
Instead, I go for former high end cards, used and value priced on Ebay.
I think I paid $30 or $40 for my nVidia card.

---

### Post by him610 on 2024-08-19
> Intel makes discrete GPUs now. I don't recall when they first hit the market
I have a Intel Pentium G4560 Kaby Lake that was released in 2017. Originally had a Nvidia GFX in the system, but I removed it a couple of years ago and have used the internal Intel HD Graphics 610  since then.

---

### Post by TheFu on 2024-08-20
> **cwmoser said:**
> I don't purchase current state of the art Graphics Cards.
Instead, I go for former high end cards, used and value priced on Ebay.
I think I paid $30 or $40 for my nVidia card.

[https://www.youtube.com/watch?v=UFytB3bb1P8](https://www.youtube.com/watch?v=UFytB3bb1P8) says getting a GPU used off eBay should be fine, but be certain to test it for issues BEFORE the return period is up.  

I have an old DDR5 Nvidia 1030 GT - it was the cheapest of the generation when nvidia dropped support for my existing nvidia on Linux.  It still worked, just at a sucky, lower, resolution. When everything in the system was exactly the same and with 1 OS, I was getting 1920x1200 resolutions, then upgraded to a new LTS release and found nvidia had dropped the proprietary driver completely, so I was getting something like 1280x720.  That's unacceptable.  Perhaps the Nouveau drivers are better now. At the time, they were not.

I felt it was time to get a new Ryzen APU (CPU+iGPU) and it was a 1-part swap (gotta love AMD motherboards that support so many CPUs/APUs for a long time.  Anyway, the new APU GPU performance is definitely faster than the 1030GT performance.  That's not really a fair comparison, since the Ryzen was much newer, but I had the fasted 1030GT with the fastest RAM.  During the peak of COVID, I could have sold that 1030GT for $130 (I paid $70).  I should have sold it.  Now it sits on a shelf here, somewhere as a spare GPU. I have other nVidia GPUs but all of them are definitely older and have lost nvidia driver support completely. None were high-end.  I think the most I've ever paid for a GPU was $130 and that was around 2000 for an S3 Virge 128.

I suspect my needs for a minimal GPU have nothing at all to do with your needs. ;)

Anyway, hope you got everything stable now.

---

### Post by cwmoser on 2024-09-24
It's been over a month after switching the video driver from Nouveau to an nVidia driver and my desktop PC has not locked up.
This fixes my problem.
Thanks to all who helped me.

---

