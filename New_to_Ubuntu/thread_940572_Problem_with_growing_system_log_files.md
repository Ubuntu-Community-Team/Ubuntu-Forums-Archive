---
title: "Problem with growing system log files"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by pilotbabo on 2008-10-07
Hi,

I am  runing Ubuntu 8.0.4 but I see in the /var/log file debug which is growing (now is 16 Mb). I dont need any debug. Can I switch this off? The same is for kern.log and syslog in the same directory. I don't have hd (runing on diskless machine with CF) and want avoid this filling my RAM.

The all 3 files are filled with these messages :

Oct  7 12:26:11 xxxx-desktop kernel: [43310.872894] out of order segment: rcv_next C5A760F seq C5A77B7 - C5A79D3
Oct  7 12:26:11 xxxx-desktop kernel: [43310.919371] ofo requeuing : rcv_next E0D51525 seq E0D51525 - E0D51640
Oct  7 12:26:11 xxxx-desktop kernel: [43311.008532] out of order segment: rcv_next C5A760F seq C5A79D3 - C5A7A03
Oct  7 12:26:11 xxxx-desktop kernel: [43311.220189] ofo requeuing : rcv_next C5A7671 seq C5A7671 - C5A76AA
Oct  7 12:26:11 xxxx-desktop kernel: [43311.220218] ofo requeuing : rcv_next C5A76AA seq C5A76AA - C5A77B7
Oct  7 12:26:11 xxxx-desktop kernel: [43311.220235] ofo requeuing : rcv_next C5A77B7 seq C5A77B7 - C5A79D3
Oct  7 12:26:11 xxxx-desktop kernel: [43311.220252] ofo requeuing : rcv_next C5A79D3 seq C5A79D3 - C5A7A03
Oct  7 12:26:12 xxxx-desktop kernel: [43311.510396] out of order segment: rcv_next C5A7A03 seq C5A7A3B - C5A7A9B

Anybody knows what is this and how to avoid it?


Thanks in advance.

---

### Post by wizard10000 on 2008-10-07
You can edit /etc/syslog.conf to change the behavior of syslogd - another option that might work better for you is to use logrotate.

Look here - you'll find all kinds of options.

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

Good luck -

---

### Post by Phkillah on 2008-10-20
> **pilotbabo said:**
> Hi,

I am  runing Ubuntu 8.0.4 but I see in the /var/log file debug which is growing (now is 16 Mb). I dont need any debug. Can I switch this off? The same is for kern.log and syslog in the same directory. I don't have hd (runing on diskless machine with CF) and want avoid this filling my RAM.

The all 3 files are filled with these messages :

Oct  7 12:26:11 xxxx-desktop kernel: [43310.872894] out of order segment: rcv_next C5A760F seq C5A77B7 - C5A79D3
Oct  7 12:26:11 xxxx-desktop kernel: [43310.919371] ofo requeuing : rcv_next E0D51525 seq E0D51525 - E0D51640
Oct  7 12:26:11 xxxx-desktop kernel: [43311.008532] out of order segment: rcv_next C5A760F seq C5A79D3 - C5A7A03
Oct  7 12:26:11 xxxx-desktop kernel: [43311.220189] ofo requeuing : rcv_next C5A7671 seq C5A7671 - C5A76AA
Oct  7 12:26:11 xxxx-desktop kernel: [43311.220218] ofo requeuing : rcv_next C5A76AA seq C5A76AA - C5A77B7
Oct  7 12:26:11 xxxx-desktop kernel: [43311.220235] ofo requeuing : rcv_next C5A77B7 seq C5A77B7 - C5A79D3
Oct  7 12:26:11 xxxx-desktop kernel: [43311.220252] ofo requeuing : rcv_next C5A79D3 seq C5A79D3 - C5A7A03
Oct  7 12:26:12 xxxx-desktop kernel: [43311.510396] out of order segment: rcv_next C5A7A03 seq C5A7A3B - C5A7A9B

Anybody knows what is this and how to avoid it?


Thanks in advance.


This type of syslog outputs have started since yesterday, when i upgraded the whole system.

I have ubuntu x64, latest (no beta).

My syslog was clear and useful, now it's simply full of crap :(

Anyone else knows about this ?

Cheers

---

### Post by philinux on 2008-10-20
Logrotate in part of the default install and runs daily normally.

Is there anything in /var/log/messages and dmesg that might pinpoint the problem.

---

### Post by Phkillah on 2008-10-20
> **philinux said:**
> Logrotate in part of the default install and runs daily normally.

Is there anything in /var/log/messages and dmesg that might pinpoint the problem.

Nope, couldn't find anything.

But here's a tip: tcp.c file from IPv4 section of the Kernel source contains the "printfs" i'm getting.

This seems a misconfiguration of the ".conf" in the latest kernel 2.6.24-21-generic........

Should we wait for the next version... :S i don't know how to build my own ubuntu-kernel with my own configs :S

Cheers

---

### Post by philinux on 2008-10-20
I would boot the previous kernel and see if the errors stop. If so install startupmanager and use it to select the default boot. Then wait for next kernel update to come along. I believe a few have minor problems and some graphics issues with .21

---

### Post by Phkillah on 2008-10-20
That's a good, simple, excellent tip :)

"startupmanager" is it worth the install? 
Is it the end of "vi /boot/grub/menu.lst" ? :D

Thkx

---

