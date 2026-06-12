---
title: "UFW entrys in syslog, normal?"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by DGINSD on 2012-03-10
I noticed while going through my syslog to try and find out what I could about some issues I have (critical battery on AC plug in, & window reloading and freeze in gnome shell) there's a lot of entries in the UFW BLOCK entries in my syslog, is this normal or something I need to look into it further. Here's a chunk of the log.
```
Mar 10 07:30:01 david-HP-Pavilion-g6-Notebook-PC anacron[10919]: Will run job `cron.daily' in 5 min.
Mar 10 07:30:01 david-HP-Pavilion-g6-Notebook-PC anacron[10919]: Jobs will be executed sequentially
Mar 10 07:30:12 david-HP-Pavilion-g6-Notebook-PC kernel: [53284.214833] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63556 PROTO=2 
Mar 10 07:30:17 david-HP-Pavilion-g6-Notebook-PC kernel: [53289.130094] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=35853 PROTO=2 
Mar 10 07:30:43 david-HP-Pavilion-g6-Notebook-PC kernel: [53315.341592] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63557 PROTO=2 
Mar 10 07:30:48 david-HP-Pavilion-g6-Notebook-PC kernel: [53320.157624] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=35858 PROTO=2 
Mar 10 07:32:48 david-HP-Pavilion-g6-Notebook-PC kernel: [53440.145774] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63558 PROTO=2 
Mar 10 07:32:52 david-HP-Pavilion-g6-Notebook-PC kernel: [53444.792728] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=35877 PROTO=2 
Mar 10 07:33:02 david-HP-Pavilion-g6-Notebook-PC wpa_supplicant[1176]: WPA: Group rekeying completed with 00:26:5a:ce:6b:a5 [GTK=CCMP]
Mar 10 07:34:53 david-HP-Pavilion-g6-Notebook-PC kernel: [53565.146138] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63559 PROTO=2 
Mar 10 07:34:56 david-HP-Pavilion-g6-Notebook-PC kernel: [53567.980440] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=35894 PROTO=2 
Mar 10 07:35:01 david-HP-Pavilion-g6-Notebook-PC anacron[10919]: Job `cron.daily' started
Mar 10 07:35:01 david-HP-Pavilion-g6-Notebook-PC anacron[10988]: Updated timestamp for job `cron.daily' to 2012-03-10
Mar 10 07:36:58 david-HP-Pavilion-g6-Notebook-PC kernel: [53690.161471] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63560 PROTO=2 
Mar 10 07:36:59 david-HP-Pavilion-g6-Notebook-PC kernel: [53691.668769] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=35911 PROTO=2 
Mar 10 07:39:03 david-HP-Pavilion-g6-Notebook-PC kernel: [53815.147717] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63561 PROTO=2 
Mar 10 07:39:04 david-HP-Pavilion-g6-Notebook-PC kernel: [53815.857961] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=35928 PROTO=2 
Mar 10 07:41:08 david-HP-Pavilion-g6-Notebook-PC kernel: [53940.163239] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63562 PROTO=2 
Mar 10 07:41:10 david-HP-Pavilion-g6-Notebook-PC kernel: [53942.050272] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=35947 PROTO=2 
Mar 10 07:43:02 david-HP-Pavilion-g6-Notebook-PC wpa_supplicant[1176]: WPA: Group rekeying completed with 00:26:5a:ce:6b:a5 [GTK=CCMP]
Mar 10 07:43:13 david-HP-Pavilion-g6-Notebook-PC kernel: [54065.149495] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63563 PROTO=2 
Mar 10 07:43:15 david-HP-Pavilion-g6-Notebook-PC kernel: [54067.742105] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=35964 PROTO=2 
Mar 10 07:45:18 david-HP-Pavilion-g6-Notebook-PC kernel: [54190.149848] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63564 PROTO=2 
Mar 10 07:47:23 david-HP-Pavilion-g6-Notebook-PC kernel: [54315.151190] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63565 PROTO=2 
Mar 10 07:47:27 david-HP-Pavilion-g6-Notebook-PC kernel: [54319.124993] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=35999 PROTO=2 
Mar 10 07:49:28 david-HP-Pavilion-g6-Notebook-PC kernel: [54440.153661] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63566 PROTO=2 
Mar 10 07:49:31 david-HP-Pavilion-g6-Notebook-PC kernel: [54443.815006] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=36016 PROTO=2 
Mar 10 07:51:33 david-HP-Pavilion-g6-Notebook-PC kernel: [54565.154601] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63567 PROTO=2 
Mar 10 07:51:37 david-HP-Pavilion-g6-Notebook-PC kernel: [54569.005602] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=36035 PROTO=2 
Mar 10 07:53:02 david-HP-Pavilion-g6-Notebook-PC wpa_supplicant[1176]: WPA: Group rekeying completed with 00:26:5a:ce:6b:a5 [GTK=CCMP]
Mar 10 07:53:38 david-HP-Pavilion-g6-Notebook-PC kernel: [54690.301280] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63568 PROTO=2 
Mar 10 07:53:41 david-HP-Pavilion-g6-Notebook-PC kernel: [54693.195056] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=36052 PROTO=2 
Mar 10 07:55:43 david-HP-Pavilion-g6-Notebook-PC kernel: [54815.303597] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63569 PROTO=2 
Mar 10 07:55:44 david-HP-Pavilion-g6-Notebook-PC kernel: [54815.882022] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=36069 PROTO=2 
Mar 10 07:57:48 david-HP-Pavilion-g6-Notebook-PC kernel: [54940.154937] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63570 PROTO=2 
Mar 10 07:57:52 david-HP-Pavilion-g6-Notebook-PC kernel: [54944.077352] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=36088 PROTO=2 
Mar 10 07:59:53 david-HP-Pavilion-g6-Notebook-PC kernel: [55065.158201] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63571 PROTO=2 
Mar 10 07:59:54 david-HP-Pavilion-g6-Notebook-PC kernel: [55066.764317] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=36105 PROTO=2 
Mar 10 08:01:58 david-HP-Pavilion-g6-Notebook-PC kernel: [55190.163986] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=63572 PROTO=2 
Mar 10 08:02:00 david-HP-Pavilion-g6-Notebook-PC kernel: [55191.954405] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:fb:00:90:96:c7:5a:c7:08:00 SRC=192.168.0.102 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=36122 PROTO=2 
Mar 10 08:03:02 david-HP-Pavilion-g6-Notebook-PC wpa_supplicant[1176]: WPA: Group rekeying completed with 00:26:5a:ce:6b:a5 [GTK=CCMP]
``` 

Basically there's entries like this all up and down the log, do I have something set up wrong, or is this someone probing my system. If more info is needed let me know I'll get it, nay and all help is appreciated, as I don't know much about this stuff but I have a desire to understand more.

---

### Post by Dangertux on 2012-03-10
This is broadcast traffic and is normal, it's also blocked by UFW by default. You really shouldn't worry about it. You could even allow it if you want, though it won't hurt anything (normally) by being dropped.

---

