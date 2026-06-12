---
title: "How To: Tweak Linux for broadband"
date: 2006-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by OldGaf on 2006-09-05
Add the following to /etc/sysctl.conf (substituting your window size in place of 524288, if necessary):

# Tweaks for faster broadband...
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

Then to have the settings take effect immediately, run:

sysctl -p

See the whole story [here.]("http://www.santa-li.com/linuxonbb.html")

Made a ***HUGE*** diff for me \\:D/

---

### Post by BLTicklemonster on 2006-09-06
Thanks! One of the first things I'd do on windows was to run cablenut to tweak my connection, and I keep wondering if there's something to use to get linux tweaked. Thanks for sharing this.

---

### Post by PriceChild on 2006-09-06
```
pricechild@linbeast:~$ sysctl -p
error: permission denied on key 'net.core.rmem_default'
error: permission denied on key 'net.core.rmem_max'
error: permission denied on key 'net.core.wmem_default'
error: permission denied on key 'net.core.wmem_max'
error: permission denied on key 'net.ipv4.tcp_wmem'
error: permission denied on key 'net.ipv4.tcp_rmem'
error: permission denied on key 'net.ipv4.tcp_mem'
error: permission denied on key 'net.ipv4.tcp_rfc1337'
error: permission denied on key 'net.ipv4.ip_no_pmtu_disc'
error: permission denied on key 'net.ipv4.tcp_sack'
error: permission denied on key 'net.ipv4.tcp_fack'
error: permission denied on key 'net.ipv4.tcp_window_scaling'
error: permission denied on key 'net.ipv4.tcp_timestamps'
error: permission denied on key 'net.ipv4.tcp_ecn'
error: permission denied on key 'net.ipv4.route.flush'

``` 
I think that all those .'s need to be /'s by looking at the rest of the file.

---

### Post by Mickeysofine1972 on 2006-09-06
> **PriceChild said:**
> ```
pricechild@linbeast:~$ sysctl -p
error: permission denied on key 'net.core.rmem_default'
error: permission denied on key 'net.core.rmem_max'
error: permission denied on key 'net.core.wmem_default'
error: permission denied on key 'net.core.wmem_max'
error: permission denied on key 'net.ipv4.tcp_wmem'
error: permission denied on key 'net.ipv4.tcp_rmem'
error: permission denied on key 'net.ipv4.tcp_mem'
error: permission denied on key 'net.ipv4.tcp_rfc1337'
error: permission denied on key 'net.ipv4.ip_no_pmtu_disc'
error: permission denied on key 'net.ipv4.tcp_sack'
error: permission denied on key 'net.ipv4.tcp_fack'
error: permission denied on key 'net.ipv4.tcp_window_scaling'
error: permission denied on key 'net.ipv4.tcp_timestamps'
error: permission denied on key 'net.ipv4.tcp_ecn'
error: permission denied on key 'net.ipv4.route.flush'

``` 
I think that all those .'s need to be /'s by looking at the rest of the file.


You need to put sudo before that command

Mike

---

### Post by PriceChild on 2006-09-06
EDIT

he he you've already corrected me :)

---

### Post by kerry_s on 2006-09-06
It works on dsl too. Also the GUI(powertweak) version has been in the repos along time.

---

### Post by ~LoKe on 2006-09-06
I didn't notice a difference, heh.

---

### Post by DrMilo on 2006-09-06
Two other things sped up my connection:

1) Fasterfox (if you're using Firefox). You can change the settings manually as well.

2) Disable ipv6. In Firefox:

[http://www.ubuntuforums.org/showthread.php?t=248113&highlight=disable+ipv6+firefox](http://www.ubuntuforums.org/showthread.php?t=248113&highlight=disable+ipv6+firefox)

And in Linux in general. Scroll down to the entry from mhael:

[http://www.ubuntuforums.org/showthread.php?t=87798&highlight=%2Fetc%2Fmodprobe.d](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=%2Fetc%2Fmodprobe.d)

Big difference!

---

### Post by DrMilo on 2006-09-06
> **~LoKe said:**
> I didn't notice a difference, heh.

You may after a reboot.

---

### Post by OldGaf on 2006-09-07
> **BLTicklemonster said:**
> Thanks! One of the first things I'd do on windows was to run cablenut to tweak my connection, and I keep wondering if there's something to use to get linux tweaked. Thanks for sharing this.

My pleasure! :) 

I find it really helps to apply this change on a fresh install before doing your initial dist-upgrade.

---

### Post by Posh on 2007-05-24
I don't believe this will work as intended on machines with Edgy and beyond. From what I understand if you have tcp_moderate_rcvbuf = 1 (which is default) then the receive window is adjusted automatically.  Now setting the max values could help but I'm not sure what setting the defalts do when you have tcp_moderate_rcvbuf enabled.  Also I believe you will probably want to use net.ipv4.tcp_no_metrics_save = 1 instead of using the route.flush=1.

Here is a website with some [[COLOR="Blue"]tuning tips[/COLOR]]("http://dsd.lbl.gov/TCP-tuning/linux.html")

---

### Post by derekguy on 2007-05-25
I did the tips that Posh suggested in his link and it has made a noticable difference for me. I am using 2.6.20-15 on i686. Afterwards I also started using OpenDNS' servers and now I am flying along :p most noticeably streaming radio & video seem to load a lot quicker.

I live in New Zealand and find that telecommunications are lacking compared to the rest of the world so this is good for me.

---

### Post by simontay78 on 2007-09-27
Regarding these two lines

> net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288

Understand from the searching of some of the help that this is set for a broadband 512 Kbps internet connection right?

If yes, what is the recommended setting for 10Mbps connection? 

Thanks! :)

---

### Post by marioXXL on 2007-10-23
Thank you guys. This topic solved my high response times for my router. Here is the config I use:

#net.core.rmem_default = 4194304
# default values seems to work fine with my system
net.core.rmem_max = 4194304
#net.core.wmem_default = 4194304
# default values seems to work fine with my system
net.core.wmem_max = 4194304
net.ipv4.tcp_wmem = 4096 87380 4194304
net.ipv4.tcp_rmem = 4096 87380 4194304
#net.ipv4.tcp_mem = 256960 256960 4194304
# this should be uncommented only if it's not working well
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

# don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
# recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
net.ipv4.tcp_congestion_control=cubic

This settings work very well on an 2 mbit connection

---

### Post by John_5 on 2007-11-07
Thanks this helped **ALOT**. My speed has tripled, maybe even quadrupled thanks to this.

---

### Post by hopelessone on 2007-12-02
hi, 

how do i find the value (substituting your window size in place of 524288, if necessary)?

thanks

---

### Post by johnnybirdman on 2008-03-08
> **hopelessone said:**
> hi, 

how do i find the value (substituting your window size in place of 524288, if necessary)?

thanks

Ditto Bump.


And, what are users doing to test the download speed to see/find improvement?

---

### Post by doondoon on 2008-03-08
I'm still kind of new at this so how do you get to /etc/sysctl.conf to add the lines you mention and is it correct to assume you do that in the terminal instead of hunting the file. Can I put it anywhere in that file or am I replacing existing lines?

---

### Post by Nythain on 2008-03-08
> **simontay78 said:**
> Regarding these two lines



Understand from the searching of some of the help that this is set for a broadband 512 Kbps internet connection right?

If yes, what is the recommended setting for 10Mbps connection? 

Thanks! :)

aye... while i see upping it to meet a 512k connection would be an increase, i still feel like im shorting myself my true potential sitting on a 10Mbps cable connection :)

---

### Post by peabody on 2008-03-08
I just did a cursory bandwidth test before and after these changes.  I used the following site ([http://www.bandwidthplace.com/](http://www.bandwidthplace.com/)) and ran 10 tests for an average (times are in Mbps).

Before:
>>> 3.04 + 3.64 + 3.61 + 3.42 + 3.17 + 3.64 + 3.15 + 3.23 + 3.37 + 2.99
33.259999999999998
>>> _ / 10
3.3259999999999996

After:
>>> 2.66 + 2.98 + 3.14 + 3.18 + 3.67 + 4.06 + 3.69 + 3.81 + 3.63 + 3.82
34.640000000000001
>>> _ / 10
3.464

I really question whether that's a dramatic enough difference to notice.  Admittedly it's not a very exhaustive test, but I'm very concerned about a placebo effect among users.  Can anyone actually provide numbers to show what their improvements have actually been using reproducable test data?

---

### Post by johnnybirdman on 2008-03-09
> **doondoon said:**
> I'm still kind of new at this so how do you get to /etc/sysctl.conf to add the lines you mention and is it correct to assume you do that in the terminal instead of hunting the file. Can I put it anywhere in that file or am I replacing existing lines?

I just added the number to the bottom of the existing file.  I usually use nano to edit in terminal, or you can use gedit.

```
sudo gedit /etc/sysctl.conf
```

the advantage with the stock settings seems to minimal, but I do see some increase, however, I still can't get over 200kbps on any download, etc. before the changes, i would never get over 185ish.

J.

---

### Post by Warprunner on 2008-03-09
> **Posh said:**
> I don't believe this will work as intended on machines with Edgy and beyond. From what I understand if you have tcp_moderate_rcvbuf = 1 (which is default) then the receive window is adjusted automatically.  Now setting the max values could help but I'm not sure what setting the defalts do when you have tcp_moderate_rcvbuf enabled.  Also I believe you will probably want to use net.ipv4.tcp_no_metrics_save = 1 instead of using the route.flush=1.

Here is a website with some [[COLOR="Blue"]tuning tips[/COLOR]]("http://dsd.lbl.gov/TCP-tuning/linux.html")

Posh....thank you!!! Probably added 1/4 more speed!!

---

### Post by stream303 on 2008-03-10
> **marioXXL said:**
> net.ipv4.tcp_wmem = 4096 87380 4194304
net.ipv4.tcp_rmem = 4096 87380 4194304

I've noticed that the tcp_wmem default value in the docs are a bit lower changing from 87380 to 65536

Gentoo also has a nice little guide:
[http://gentoo-wiki.com/HOWTO_TCP_Tuning](http://gentoo-wiki.com/HOWTO_TCP_Tuning)

---

### Post by NickFie on 2009-12-04
Several points to add to this thread, based on extensive testing at my employer.

[LIST=1]
[*]Bandwidth Delay Product is interesting but an insufficient minimum unless you intend to only run iPerf. Web browsing hits global servers - how do you know what latency to put in the formula?
 

Even worse, there's a **lot** of latency at each end inside the server & client. Testing Linux-Linux on a US - Japan link showed:[LIST=1]
[*]BDP was just under 500 KBytes based on ping time & throughput tests.
[*]Actual windowsize to achieve wire-speed throughput (13 seconds, including ramp-up) with 20 MByte file was 2.7 MBytes - 5x bigger than the textbook calculation.
[/LIST]
[*]Longer, fatter pipes need even bigger rmem & wmem. My network ecologist colleague has been testing our regional (northeast US) GigE network and reports our standard 4 MByte max is inadequate. We've got some 10GigE pipes in plan - look forward to getting full value from those mothers. We don't throw away money on network - with proper planning leasing (not owning) these facilities is far less expensive than seeking smaller-capacity links.
[*]Modern computers measure memory in Gigabytes, and x64 Linux can use it well. Auto-tuning means the TCP stack takes only the memory it needs. Even if you define Gi-normous (technical term for really, really big) rmem & wmem the TCP stack will only grab the full measure when it's needed, and release it as soon as it's done.
[*]Set default mem values to about 128 KBytes. This means the auto-tuning requires fewer round-trips during ramp-up to reach optimum value. 16 KByte minimum seems OK.
[*]Selective Acknowledgments (tcp_sack = 1) are mandatory to maintain real-world throughput with that much data in flight. I've seen some misguided sites recommend disabling this feature.
[*]The easiest way to improve throughput? Defrag your hard drive. The receive buffer can't clear until that data is stuffed onto your hard disk. The longer your hard drive thrashes, the longer the sender must wait to transmit the next packets. Several years ago my old & slow single-core laptop signifcantly outperformed my colleagues dual core, fast-disk, large-memory machine simply because his disk was badly fragmented. His machine did outrun mine in the network tests after defragmentation.
[/LIST]Conclusion - don't waste time with bandwidth-delay product calculations, simply specify 16 MByte max rmem & wmem.

---

### Post by Falkor on 2009-12-22
Hi NickFie,

I got a 100mbps for my server, and wondering which settings should I be using.

Just the following three?

[COLOR=RoyalBlue] net.ipv4.tcp_sack = 1
net.core.rmem_max =[/COLOR][COLOR=RoyalBlue] 16 MByte
net.core.wmem_max =[/COLOR] [COLOR=RoyalBlue]16 MByte[/COLOR]

(The value should be in bytes, correct?)

By the way, from a Google search, this trick has been floating around for a few years now. I am wondering if those have been implemented to the recent Ubuntu releases already, that we should better off using the default settings...

I have read those interesting articles:

[COLOR=RoyalBlue]Linux TCP Tuning - Linux 2.6[/COLOR] ([link]("http://fasterdata.es.net/TCP-tuning/linux.html"))
[COLOR=RoyalBlue]TCP Stacks Testbed[/COLOR] ([link]("http://www-iepm.slac.stanford.edu/bw/tcp-eval/"))

---

### Post by Autodave on 2009-12-31
> **kerry_s said:**
> It works on dsl too. Also the GUI(powertweak) version has been in the repos along time.

What is the name of that program?  I searched through the repositories and couldn't find anything resembling that......

---

