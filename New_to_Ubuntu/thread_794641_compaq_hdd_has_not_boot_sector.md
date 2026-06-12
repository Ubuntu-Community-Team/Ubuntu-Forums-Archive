---
title: "compaq hdd has not boot sector???"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by asmugone on 2008-05-14
Hey gang, got a strange one here, im new to linux but have been a convert for awhile now and have done it with windows for years. I am rebuilding my moms compaq all new off the shelf parts and they all work fine with ubuntu.

But when I put her old compaq hard drive in and try to install linux everything goes fine used a guided install to use whole hard disk. but when I reboot there isnt anything, no grub, no boot, nothing, it acts like there isnt even a boot sector?? Anyone have any ideas? This only happens with this hard drive even when I install windows it wont work boot. Im at a loss here gang.

-Cliff

****SOLUTION******
low level format of the drive with a tool of major geeks is the fix for this problem! simple and elegant!***

---

### Post by will1911a1 on 2008-05-14
So it just hangs after post?

---

### Post by asmugone on 2008-05-14
no, it just skips the hard drive like it dosent even exist, in 15 years of tech support iv never seen anything like it, if i boot off another hard drive i can see all info on the drive like its fine.

---

### Post by will1911a1 on 2008-05-14
There's no error message or anything? What's the last thing that shows up on the screen?

---

### Post by asmugone on 2008-05-14
no nothing, it just goes to the next boot device if there is one, otherwise if it just boots to the hd and nothing else i get a blank cursor in the top left of the screen and nothing else. Strange huh!

---

### Post by will1911a1 on 2008-05-14
Yeah that is odd.

Are you using the same cable that the other drive works with?

How are the jumpers set on the drive?

---

### Post by asmugone on 2008-05-14
Yes same cable,works fine, jumper is set to slave 16 mb clip, its a deskstar. Strangest darn thing iv ever seen.

---

### Post by will1911a1 on 2008-05-14
Does the drive have a jumper position for "cable select"?

---

### Post by asmugone on 2008-05-14
tried that, no bueno

---

### Post by will1911a1 on 2008-05-14
> **asmugone said:**
> tried that, no bueno

That's weird.  If you boot to the other drive can you access the one that isn't booting?

If so, have you tried wiping it?

---

### Post by asmugone on 2008-05-14
yes I can access the drive and see the data, I have tried formating it that way and from the live boot ubuntu hardy heron cd. AND a windows xp cd, the files install fine and I can see them but there dosent seem to be a boot sector to start the drive.

---

### Post by will1911a1 on 2008-05-14
Wow, I'm really not sure what else to have you check.  It doesn't sound like the drive is fried, but I don't see how a fresh install would fail to create a bootsector.

If I think of anything else I'll let you know, but for the moment I'm stumped.

---

### Post by asmugone on 2008-05-14
I know its really strange, its like how a old compaq system wouldnt boot unless you had the special cd rom hooked up with the chip inside with boot instructions but I have never seen it taken to this level.

Kind of freaking me out here lol.

---

### Post by will1911a1 on 2008-05-14
One last thought:

Have you run a low level format on the drive yet?

I found this:
[http://answers.yahoo.com/question/index?qid=20080114215007AAVz515]("http://answers.yahoo.com/question/index?qid=20080114215007AAVz515")
Seems like the same problem you're having.

One of the posters link to a low level formatting utility that seemed to do the trick for them

---

### Post by dtrot55 on 2008-05-14
Or its possible that the boot sector of your hard drive has been corrupted ... as in when your computer first boots the information on the beginning of the drive isn't relaying the boot information.  But when you boot into windows it can still see the drive..hopefully im on the right track..but i have had instances in windows where my hard drive died but when i took it out of first boot and got into windows the drive work'd...so i dont know if its the same issue.

---

### Post by will1911a1 on 2008-05-14
> **dtrot55 said:**
> Or its possible that the boot sector of your hard drive has been corrupted ... as in when your computer first boots the information on the beginning of the drive isn't relaying the boot information.  But when you boot into windows it can still see the drive..hopefully im on the right track..but i have had instances in windows where my hard drive died but when i took it out of first boot and got into windows the drive work'd...so i dont know if its the same issue.

I'm thinking that might be what's going on here. If that's the case a low level format SHOULD fix the issue.

---

### Post by louieb on 2008-05-14
Just out of curiosity do a hex dump of the mbr.  The sda part of the command may have to change to whatever Linux is calling the old drive.
```
dd if=/dev/sda count=1 | hexdump -C
```

Most of the output will be meaningless. but you should  see the word **GRUB **in the output. At least you'll know if the installer put stage1 in the MBR.

---

### Post by asmugone on 2008-05-15
I know that the drive has a boot sector because I tried repairing it by bootstrapping the drive and then rewriting the entire boot sector, Next im going to try the low level format and im going to try the new suggestion from within another ubuntu install on a different hard drive. I will post results.

---

### Post by click4851 on 2008-05-15
+1 on the low level format....I have had good luck with Ultimate Boot CD

---

### Post by asmugone on 2008-05-15
can some one please post the terminal command to do a low level format? I dont know it lol.

---

### Post by asmugone on 2008-05-15
used the dd command. the drive has the mount point media/disk so i used that instead of dev. the dev just returned no file.

heres output.

dd: reading `/media/disk': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00810417 seconds, 0.0 kB/s

---

### Post by asmugone on 2008-05-15
alright I redid it it was under /dev/hdb the output is this.

1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0406914 seconds, 12.6 kB/s
00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  ee 0b b1 ca 00 00 00 01  |.....,Dc........|
000001c0  01 00 83 fe ff ff 3f 00  00 00 f4 b4 0e 09 00 fe  |......?.........|
000001d0  ff ff 05 fe ff ff 33 b5  0e 09 8e 2f 42 00 00 00  |......3..../B...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
that help at all gang???

---

### Post by asmugone on 2008-05-15
having trouble finding a low level format solution on the ultimate boot cd. the ibm diagnostic tool bombs out. Im running a tool now hd2 or something and doing a drive wipe it calls it. Then I will try and reinstall ubuntu and post results.

---

### Post by louieb on 2008-05-15
> **asmugone said:**
> alright I redid it it was under /dev/hdb the output is this...that help at all gang???-

For what its worth doesn't look like GRUB  code in the MBR.   Wonder if BIOS has the MBR write protected. Might see if the virus protection is turned on in BIOS. 

Was looking for something in the output like this:
```

...
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...[COLOR=Red]G[/COLOR]|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |[COLOR=Red]RUB .Geom.Hard D[/COLOR]|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |[COLOR=Red]isk.Read. Error.[/COLOR]|
0
...

```

---

### Post by asmugone on 2008-07-02
LOw level format did it, must have been some strange hold over from grub or something because i Had it happen again to a deskstar that I had a dual boot on after wiping it, just grabbed a low level format tool off major geeks, slammed the hard drive in as a slave in my backup windows system, low level format, AND FEEL THE LOVE!!

thanks gang!!

---

