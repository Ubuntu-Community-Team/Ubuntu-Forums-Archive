---
title: "dividing unsigned"
date: 2011-09-10
forum: Programming Talk
---

### Post by nataliafoster26 on 2011-09-10
bnum1		db	25, 	bnum2		db	17, 	bnum3		db	8, 	bnum4		db	17, 	bnum5		db	-6, 	bnum6		db	-19
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

### Post by PaulM1985 on 2011-09-10
Is this a question?

01110000010101101101111101101010010111,
1101011010010010001001010100111
01010001001010100010111110101011?

---

### Post by cgroza on 2011-09-10
Hmm, let me use my psychic powers to reveal the question to the forum...

---

### Post by karlson on 2011-09-11
> **nataliafoster26 said:**
> bnum1		db	25, 	bnum2		db	17, 	bnum3		db	8, 	bnum4		db	17, 	bnum5		db	-6, 	bnum6		db	-19
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

Any reason you are trying to do this assembly? and by working with bytes? and what is this for exactly? and what's the question ?

---

