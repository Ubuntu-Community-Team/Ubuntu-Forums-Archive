---
title: "Faster internet?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by tahitiwibble on 2008-11-13
My internet connection is pitifully slow. I have found these two tweaks on the net and would like to know 
a) if it's a good idea to do it?
b) why they are slightly different?
c) which would be the best?

Add to your /etc/sysctl.conf file either

net.core.rmem_default = 32768
net.core.rmem_max = 32768
net.core.wmem_default = 32768
net.core.wmem_max = 32768
net.ipv4.tcp_wmem = 4096 32768 32768
net.ipv4.tcp_rmem = 4096 32768 32768
net.ipv4.tcp_mem = 32768 32768 32768
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

or

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

Thanks for your thoughts.

---

### Post by alienexplorers on 2008-11-13
Would like to know if one of these works.  My internet is creapy slow.

---

### Post by tahitiwibble on 2008-11-13
The top one is apparently specific to Hardy 8.04 and the lower one for "general" use.

---

### Post by CLomax on 2008-11-13
Just pasted the top one into mine, I'll let you know if I see any improvement ;)

---

### Post by tahitiwibble on 2008-11-13
> **CLomax said:**
> Just pasted the top one into mine, I'll let you know if I see any improvement ;)

Brave man! :) Here's the link to the site [http://www.zyxware.com/articles/2008/08/01/slow-broadband-in-ubuntu-hardy-speed-up-your-internet-connection](http://www.zyxware.com/articles/2008/08/01/slow-broadband-in-ubuntu-hardy-speed-up-your-internet-connection) , the other one looks a bit dodgy, not as serious.

---

### Post by CLomax on 2008-11-13
> **tahitiwibble said:**
> Brave man! :) Here's the link to the site [http://www.zyxware.com/articles/2008/08/01/slow-broadband-in-ubuntu-hardy-speed-up-your-internet-connection](http://www.zyxware.com/articles/2008/08/01/slow-broadband-in-ubuntu-hardy-speed-up-your-internet-connection) , the other one looks a bit dodgy, not as serious.

Brave but foolish.

Using speedtest.net I found that it's actually slower or it might just be a coincidence. My upload is faster than my download :shock:. That just should not happen.

I have a feeling that my ISP, Pipex, are throttling my traffic because my brother uses a BitTorrent client for *legal* purposes.

If anyone has stumbleupon they can check the reviews, they usually tell you if it works and whatnot.

As long as my installation hasn't been ruined, I'm happy.

---

### Post by Sealbhach on 2008-11-13
You could try different MTU settings:

[http://www.brunolinux.com/06-Fine_Tuning_Your_System/Tweaking_MTU_Settings.html](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Tweaking_MTU_Settings.html)



.

---

### Post by CLomax on 2008-11-13
> **Sealbhach said:**
> You could try different MTU settings:

[http://www.brunolinux.com/06-Fine_Tuning_Your_System/Tweaking_MTU_Settings.html](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Tweaking_MTU_Settings.html)



.

Does this apply to wlan0 too?

---

### Post by the.phantom on 2008-11-13
i did this one
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Howto:_Tweak_and_maximize_your_bandwidth_in_Ubuntu.2FLinux_via_sysctl.21](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Howto:_Tweak_and_maximize_your_bandwidth_in_Ubuntu.2FLinux_via_sysctl.21)

and benchmarked for 2 days with internetfrog and dsl reports and got about 5% increase and no problems
i would install run both test, uninstall and run both test
and no problems in about a week now

but like all things.. use at your own risk !!!!

---

### Post by CLomax on 2008-11-13
> **the.phantom said:**
> i did this one
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Howto:_Tweak_and_maximize_your_bandwidth_in_Ubuntu.2FLinux_via_sysctl.21](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Howto:_Tweak_and_maximize_your_bandwidth_in_Ubuntu.2FLinux_via_sysctl.21)

and benchmarked for 2 days with internetfrog and dsl reports and got about 5% increase and no problems
i would install run both test, uninstall and run both test
and no problems in about a week now

but like all things.. use at your own risk !!!!

Did this for myself and got rid of what I added earlier, hopefully I'll get an increase no matter how slight.

---

### Post by oldsoundguy on 2008-11-13
no one has mentioned the type of internet connection being used.  No tweaking of the OS is going to allow you to go faster than the limits set by the ISP! Nor has it been mentioned whether on a network or direct to modem or WIRELESS. Tweaking of the OS there will also be futile if there is a log jam upstream.
[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)
if you are in the US
[http://www.speedtest.net](http://www.speedtest.net)
if elsewhere


My ISP has a 6mbps limit right now .. going up to 15 mid December.

My figures:
1st site:
6689/2507
second site:
5594/2799
That is cable.

Another thing is to take into consideration just how many active plug ins you have working in your browser (those that load automatically, not those you have to launch.)

---

### Post by presence1960 on 2008-11-13
I run Hardy and had already used the first one a few days ago with definite improvements. The improvements were in Firefox 3. It now opens with no delay and when I close Firefox it now closes immediately. Prior to this there was much noticeable lag in opening & closing the browser. Also pages load faster now, especially this beloved forum. prior to adding this I would need a shave by the time a new thread loaded into the browser. Now it is super quick. I have also noticed more speed loading pages from other web sites.

---

### Post by Sealbhach on 2008-11-13
I'm using Minefield (Firefox 3.1 Alpha).

For me it's noticeably faster than 3.0.

[http://www.linuxhaxor.net/2008/09/28/firefox-minefield-faster-than-chrome/](http://www.linuxhaxor.net/2008/09/28/firefox-minefield-faster-than-chrome/)


.

---

### Post by Sealbhach on 2008-11-13
> **the.phantom said:**
> i did this one
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Howto:_Tweak_and_maximize_your_bandwidth_in_Ubuntu.2FLinux_via_sysctl.21](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Howto:_Tweak_and_maximize_your_bandwidth_in_Ubuntu.2FLinux_via_sysctl.21)

and benchmarked for 2 days with internetfrog and dsl reports and got about 5% increase and no problems
i would install run both test, uninstall and run both test
and no problems in about a week now

but like all things.. use at your own risk !!!!

Did this in Intrepid just now. Got an increase of around 350kbps on speedtest.net.


.

---

### Post by oldsoundguy on 2008-11-13
3.0.4 came out today.  Should be in the repositories by tomorrow (for 8.04 and 8.10).  
For those using Gutsy or older, you can install it via the Ubuntuzilla site as it won't get put into the repositories for those builds.

---

