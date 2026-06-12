---
title: "Response from GPS tracker"
date: 2014-08-23
forum: Programming Talk
---

### Post by cherva on 2014-08-23
Hello All,
I'm trying to understand what a TK-102B clone is trying to talk to me over TCP :)
I made a small php program that listens to a port and on a new connection it does this:
```
$a = 1;
                        while (socket_recv($connection, $in, 2048, MSG_PEEK) !== 0) {
                                sleep (2);
                                if($a==1){                                                                                                            
                                socket_send($connection, "LOAD", 4, 0);
                                __logger(date("d-m-y h:i:sa") . " Sent: LOAD\n");
                                $a=2;
                                }
                                echo "CLIENT:\n";
                                var_dump($in);
                        }

```

I try to send it load after the first loop, but I get something that I don't understand: (tcpdumped info)
 

```
00000000  78 78 0d 01 03 54 18 80  30 02 70 45 00 16 dc 43 xx...T.. 0.pE...C
00000010  0d 0a                                            ..
    00000000  4c 4f 41 44                                      LOAD
00000012  78 78 0d 01 03 54 18 80  30 02 70 45 00 16 dc 43 xx...T.. 0.pE...C
00000022  0d 0a                                            ..
00000024  78 78 1f 12 0e 08 18 00  3a 38 c5 04 93 4f c4 02 xx...... :8...O..
00000034  81 29 f3 00 35 5a 01 1c  05 03 e8 00 2b 5e 00 16 .)..5Z.. ....+^..
00000044  54 05 0d 0a                                      T...

```
The tracker sends me some 18 bytes, I send him LOAD and then he sends me again the same 18 bytes...
Any ideas what is this ?
I have an older model of this tracker and he just spits normal TEXT at this moment.... but this one is different....
Maybe I don't wait enough to get something normal to var_dump() .....
Any ideas will be helpful.
I tried different servers (like [http://www.traccar.org/]("http://www.traccar.org/")) .... same result there ... HEX I couldn't translate into ASCII....

---

### Post by tgalati4 on 2014-08-24
Some clones are better than others.  Seems there is a problem with knock-offs:  [http://i81.servimg.com/u/f81/13/31/80/10/tk102c10.png](http://i81.servimg.com/u/f81/13/31/80/10/tk102c10.png)

Perhaps the response is in Chinese rather than english ascii.

---

### Post by cherva on 2014-08-25
Chinese ASCII ?!?!!?

---

