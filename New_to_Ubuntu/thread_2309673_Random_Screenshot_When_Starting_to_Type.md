---
title: "Random Screenshot When Starting to Type"
date: 2016-01-12
forum: New to Ubuntu
---

### Post by Branden_Casto on 2016-01-12
Hey everyone, 

I am somewhat new to linux, I used to have mint on an old computer but never needed it much. Now I have started coding more and setting up servers so linux has become necessary and I would like to contribute to developing something open source at some point in the future also. Anyway, I have troubleshooted many problems I have had with this install already with no problem. One problem that I am continuing to have though is that sometimes when I go to start typing the OS will randomly take a screenshot. I have checked numerous times to make sure I am not accidentally hitting a known keyboard shortcut or anything like that. Its very strange and not sure where to start investigating. Thanks in advance for the help.

Set-Up:

Ubuntu 14.04 LTS 64 Bit

16GB RAM 
1TB HD
1TB HD 
120 GB HD (Ubuntu installed here)
2 Radeon HD 5670 Graphics Cards with Crossfire 
AMD Phenom(tm) II X6 1045T Processor × 6

---

### Post by DuckHook on 2016-01-13
Hi Branden_Casto and welcome to the forums.

You may have a failing keyboard. I had a similar problem some years ago: typing away would generate random keystrokes every once in a while. I spent hours trying to chase down the problem and could finally solve it only by swapping out the keyboard.

So try another keyboard. If you still get the same problem, have a look at your log files like dmesg and syslog, especially for lines containing "key" or "code", as follows:```
cat /var/log/syslog | egrep -i 'key|code'
```

---

