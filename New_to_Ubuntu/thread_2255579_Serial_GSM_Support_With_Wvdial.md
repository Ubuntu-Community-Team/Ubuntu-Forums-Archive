---
title: "Serial GSM Support With Wvdial"
date: 2014-12-06
forum: New to Ubuntu
---

### Post by Nikunj_Patel on 2014-12-06
I use SIM900 GSM MODEM with MY Board in which i am using Ubuntu 12.04.
I interface GSM using 4 Pin as below
1)Rx
2)Tx
3)RTS
4)CTS

I use ttyS3 for GSM interface.

When i run Wvdial Command

it is start but stop with Below Log

--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Nov 12 16:07:28 2014
--> Pid of pppd: 2225
--> Using interface ppp0


Please help me to solve above problm.

Thanks in Advance.

---

### Post by llamabr on 2014-12-06
I don't exactly know what your problem is -- I assume you're saying you're getting this output, but it's not dialing?  or it does dial but doesn't connect?  Have you added your user to the dip group, like this:



```
sudo adduser userID dip
```

[http://ubuntuforums.org/showthread.php?t=1349773&highlight=llamabr+wvdial](http://ubuntuforums.org/showthread.php?t=1349773&highlight=llamabr+wvdial)

---

### Post by Nikunj_Patel on 2014-12-11
Thanks for your reply.

I use Gsm modem with Serial connection. i use rx,tx,rts,cts pin.

all command run fine.



[COLOR=#000000]When i run [/COLOR][COLOR=#417394]Wvdial[/COLOR][COLOR=#000000] Command[/COLOR]

[COLOR=#000000]it is start fine

 but stop with Below Log[/COLOR]

[COLOR=#000000]--> Carrier detected. Starting PPP immediately.[/COLOR]
[COLOR=#000000]--> Starting pppd at Wed Nov 12 16:07:28 2014[/COLOR]
[COLOR=#000000]--> Pid of pppd: 2225[/COLOR][COLOR=#000000]


Please provide support me for same and also tell me  my hardware connection is ok 
means i use only rx,tx,cts,rts pin
there is no use of DTR & DCD pin.

So Wvdial is require DTR & DCD or not?



[/COLOR]

---

