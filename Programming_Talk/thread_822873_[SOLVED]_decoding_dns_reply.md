---
title: "[SOLVED] decoding dns reply"
date: 2008-06-08
forum: Programming Talk
---

### Post by sheazar on 2008-06-08
I've now (after some testing) finally written a program thats sends a MX request to a dns server (This because I'm trying to learn network programming). But now I've encountered a new problem, I dont know how to convert the byte array I'm recieving as reply to a readable string.

Anyone got any ideas (I'm using java)

posting a the reply im getting if it can help, this is for hotmail.com (taken from wireshark)```

0000   01 01 81 80 00 01 00 04 00 05 00 11 07 68 6f 74  .............hot
0010   6d 61 69 6c 03 63 6f 6d 00 00 0f 00 01 c0 0c 00  mail.com........
0020   0f 00 01 00 00 08 29 00 08 00 05 03 6d 78 34 c0  ......).....mx4.
0030   0c c0 0c 00 0f 00 01 00 00 08 29 00 08 00 05 03  ..........).....
0040   6d 78 31 c0 0c c0 0c 00 0f 00 01 00 00 08 29 00  mx1...........).
0050   08 00 05 03 6d 78 32 c0 0c c0 0c 00 0f 00 01 00  ....mx2.........
0060   00 08 29 00 08 00 05 03 6d 78 33 c0 0c c0 0c 00  ..).....mx3.....
0070   02 00 01 00 00 67 7b 00 0e 03 6e 73 35 04 6d 73  .....g{...ns5.ms
0080   66 74 03 6e 65 74 00 c0 0c 00 02 00 01 00 00 67  ft.net.........g
0090   7b 00 06 03 6e 73 33 c0 7d c0 0c 00 02 00 01 00  {...ns3.}.......
00a0   00 67 7b 00 06 03 6e 73 32 c0 7d c0 0c 00 02 00  .g{...ns2.}.....
00b0   01 00 00 67 7b 00 06 03 6e 73 31 c0 7d c0 0c 00  ...g{...ns1.}...
00c0   02 00 01 00 00 67 7b 00 06 03 6e 73 34 c0 7d c0  .....g{...ns4.}.
00d0   3f 00 01 00 01 00 00 06 6e 00 04 41 36 f5 08 c0  ?.......n..A6...
00e0   3f 00 01 00 01 00 00 06 6e 00 04 41 36 f4 08 c0  ?.......n..A6...
00f0   3f 00 01 00 01 00 00 06 6e 00 04 41 36 f4 88 c0  ?.......n..A6...
0100   53 00 01 00 01 00 00 08 26 00 04 41 36 f4 28 c0  S.......&..A6.(.
0110   53 00 01 00 01 00 00 08 26 00 04 41 36 f4 a8 c0  S.......&..A6...
0120   53 00 01 00 01 00 00 08 26 00 04 41 36 f5 28 c0  S.......&..A6.(.
0130   67 00 01 00 01 00 00 08 29 00 04 41 36 f4 48 c0  g.......)..A6.H.
0140   67 00 01 00 01 00 00 08 29 00 04 41 36 f4 c8 c0  g.......)..A6...
0150   67 00 01 00 01 00 00 08 29 00 04 41 36 f5 48 c0  g.......)..A6.H.
0160   2b 00 01 00 01 00 00 07 9a 00 04 41 36 f4 e8 c0  +..........A6...
0170   2b 00 01 00 01 00 00 07 9a 00 04 41 36 f5 68 c0  +..........A6.h.
0180   2b 00 01 00 01 00 00 07 9a 00 04 41 36 f4 68 c0  +..........A6.h.
0190   c9 00 01 00 01 00 00 45 55 00 04 cf 2e 42 7e c0  .......EU....B~.
01a0   79 00 01 00 01 00 00 45 55 00 04 41 37 ee 7e c0  y......EU..A7.~.
01b0   b7 00 01 00 01 00 00 45 55 00 04 cf 44 a0 be c0  .......EU...D...
01c0   a5 00 01 00 01 00 00 45 55 00 04 41 36 f0 7e c0  .......EU..A6.~.
01d0   93 00 01 00 01 00 00 45 55 00 04 d5 c7 a1 4d     .......EU.....M
```

EDIT: If you want something to compare to run the command nslookup -type=MX hotmail.com

---

