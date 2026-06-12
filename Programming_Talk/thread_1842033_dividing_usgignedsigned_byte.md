---
title: "dividing usgigned/signed byte"
date: 2011-09-10
forum: Programming Talk
---

### Post by nataliafoster26 on 2011-09-10
bnum1		db	25 	bnum2		db	17 	bnum3		db	8 	bnum4		db	17 	bnum5		db	-6 	bnum6		db	-19
   wans12=289
unsigned
;       bans18 = wans12 / bnum3 ;	brem18 = modulus (wans12 / bnum3) i keep getting wrong answer FOR THESE
0x804926a <bans16>:    3
0x804926b <bans17>:    2
0x804926c <bans18>:    4
0x804926d <brem18>:    1
0x804926e <bans19>:    -2
0x804926f <bans20>:    3
0x8049270 <bans21>:    6
0x8049271 <brem21>:    0

; unsigned byte division
;    bans16 = bnum1 / bnum3
;    bans17 = bnum4 / bnum3
;    bans18 = wans12 / bnum3
;    brem18 = modulus (wans12 / bnum3)
   mov al,[bnum1]
   mov ah,0
   div byte [bnum3]
   mov [bans16],al
   mov al,[bnum4]
  mov ah,0
  div byte [bnum3]
   mov [bans17],al
  mov  al,[wans12]
 mov ah,0
  div byte [bnum3]
  mov [bans18],al
  mov [brem18],ah

THANKS FOR HELP

---

### Post by TeoBigusGeekus on 2011-09-10
Mixing signed and unsigned types is a can of worms.
You'd better ask at the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39").

---

### Post by sisco311 on 2011-09-11
Moved to Programming Talk.

---

### Post by PaulM1985 on 2011-09-11
Is this a copy of this post?  [http://ubuntuforums.org/showthread.php?t=1842070](http://ubuntuforums.org/showthread.php?t=1842070)

What is your question?

---

### Post by sisco311 on 2011-09-11
> **PaulM1985 said:**
> Is this a copy of this post?  [http://ubuntuforums.org/showthread.php?t=1842070](http://ubuntuforums.org/showthread.php?t=1842070)

What is your question?

Oh, indeed it is. Next time please use the [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG] button to report duplicate posts/threads. Thanks.

Thread closed.

---

