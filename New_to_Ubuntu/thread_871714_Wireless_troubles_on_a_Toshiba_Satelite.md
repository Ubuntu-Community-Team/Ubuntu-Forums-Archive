---
title: "Wireless troubles on a Toshiba Satelite"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by BlackAeronaut on 2008-07-27
Howdy folks.  I'm a Noob Linux user who has long weighed the pros and cons of switching to a Linux distro and finally gave up when I saw Ubuntu sitting in the computer section of my base's Exchange.  I'm pretty tired of seeing all these new computers with Vista and that seeming to be the only option with a new computer.

At this time, I'm just trying out Ubuntu to see how effectively it can be used in place of another OS such as XP or *shudders* Vista.  I know that they are supposed to work perfectly fine, but as the story book version of Jumanji said, "Fun for some, but not for all."

At this time my primary concern is internet connectivity (or rather lack of it).  I'm using a Toshiba Satellite A105-S4011, which uses an Intel PRO/Wireless 3945ABG for wireless Ethernet with a Mobile Intel 945GM Express Chipset.  The Ubuntu OS itself is Hardy Heron.

I am not sure where the problem lies, exactly.  The drivers seem to be working, but for whatever reason I am unable to detect any wireless signals in Ubuntu.  However, when I restart in XP (I'm dual-booting) it works just fine.

I'd be very happy if someone could help me.  The internet is my primary to for resolving technical issues in the first place, so this has been a very trying issue for me.

---

### Post by deltaprime on 2008-07-27
heyo answer these questions:

-running on live cd or installed?

-open a shell and type > iwconfig post the output on this forum = )

-is your wireless switch on?

-in the top right you see a computer with an orange triangle? connect to a network with that.

-you said ethernet so that confused me if you really ment wifi or ethernet?


DELTA

---

### Post by diablo75 on 2008-07-27
Check to see if your wireless adapter may have any options within the system BIOS that might cause it to be disabled during startup.

---

### Post by deltaprime on 2008-07-27
oh try this just thought about it.
when you do iwconfig in the shell it should have wlan0, eth0 or whatever it is that you can identify as your wireless card show up. remember that name.

mine is wlan0 so you will have to maybe replace that with your own 

type :> ifconfig wlan0 up

---

### Post by BlackAeronaut on 2008-08-02
Thanks for all the assistance, folks, but much to my pleasant surprise, the damn thing just decided it was going to work for me the next time I booted Ubuntu without any assistance on my part.

I truly hate it when computer hardware/software does this.  Everything looks like it -should- work, but it doesn't until sometime much later on it starts behaving. :p

---

### Post by cybrsaylr on 2008-08-03
LOL! 

You are lucky. I had to play around awhile to get my new Toshiba wireless to connect. There's a whole forum devoted to wireless problems that helped me out. Guess that's expected since there are about 100 linux distros out there.

---

### Post by pacmeister on 2008-09-11
I am a real noob and had to figure out what a shell was.  Anyway, I've got the same problem--recognizes the wireless network is there, but won't connect. Here is the output from iwconfig

steven@steven-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:16:E3:9B:97:2F   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

steven@steven-laptop:~$ 


Can anyone help me out here?
Thanks.

---

### Post by pacmeister on 2008-09-17
I guess not.  Thanks anyway.  Back to XP/

---

