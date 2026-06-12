---
title: "250GB HDD, only 232GB usable, why?"
date: 2010-07-11
forum: Recurring Discussions
---

### Post by GreenDance on 2010-07-11
If a HDD is marketed as a 250GB HDD then surely it should be 250GB, if only 232GB is usable then surely it should be marketed as 232GB not 250GB, wouldn't that come under false advertising?

---

### Post by gnomeuser on 2010-07-11
[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)
[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using  tune2fs -m).

---

### Post by cascade9 on 2010-07-11
That is from the kilobyte 'problem'. 

1024b = 1 kB 

For HDD manufacturers- 

1000b = 1kB. 

Before anybody says 'but 1000kB = kilobyte and 1024 = a kibibyte' yes, yes I know, I just dont agree with theb logic behind that.

---

### Post by sandyd on 2010-07-11
> **GreenDance said:**
> If a HDD is marketed as a 250GB HDD then surely it should be 250GB, if only 232GB is usable then surely it should be marketed as 232GB not 250GB, wouldn't that come under false advertising?

the 18GB is usable by your system. its used as the hard drive's filesystem tables & such

---

### Post by chriswyatt on 2010-07-11
> **cascade9 said:**
> That is from the kilobyte 'problem'. 

1024b = 1 kB 

For HDD manufacturers- 

1000b = 1kB. 

Before anybody says 'but 1000kB = kilobyte and 1024 = a kibibyte' yes, yes I know, I just dont agree with theb logic behind that.

Don't forget also that lowercase b means bit.

b = bit
B = byte

I don't agree with the kibibyte thing either, they should just keep with the multiple of 2 standard.  Having 2 very similar standards is very confusing to consumers, and myself.  :S

---

### Post by cascade9 on 2010-07-11
> **carlee said:**
> the 18GB is usable by your system. its used as the hard drive's filesystem tables & such

Its nothing to do with filesystem tabels, etc. Its purely a function of 1000/1024.  

[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=615&p_created=1034613413&p_sid=vUEZhE4k&p_accessibility=0&p_redirect=&p_srch=1&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NDYsNDYmcF9wcm9kcz0yODgsOTUmcF9jYXRzPSZwX3B2PTIuOTUmcF9jdj0mcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1DYXBhY2l0eQ!!&p_li=&p_topview=1]("http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=615&p_created=1034613413&p_sid=vUEZhE4k&p_accessibility=0&p_redirect=&p_srch=1&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NDYsNDYmcF9wcm9kcz0yODgsOTUmcF9jYXRzPSZwX3B2PTIuOTUmcF9jdj0mcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1DYXBhY2l0eQ%21%21&p_li=&p_topview=1")

[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=194563&NewLang=en](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=194563&NewLang=en)

---

### Post by Jose Catre-Vandis on 2010-07-11
So why isn't it 244GB useable space?

250/1024*1000 = 244

Where did the other 12GB go?

Linux does reserve some system space when you format with ext3/ext4.

---

### Post by KdotJ on 2010-07-11
That is confusing stuff about the gibigyte and gigabyte. This has annoyed me in the past about losing that extra few gigabytes if space...

---

### Post by cascade9 on 2010-07-11
> **Jose Catre-Vandis said:**
> So why isn't it 244GB useable space?

250/1024*1000 = 244

Where did the other 12GB go?

Linux does reserve some system space when you format with ext3/ext4.

Because they miscount (IMO) several times, not just once. 

1kB = 1024b
1MB = 1024kB
1GB = 1024MB 

According to the HDD manufacturers

1kB = 1000b
1MB = 1000kB
1GB = 1000MB

So when a HDD says '1GB' its actually 1,000,000,000b. 1,073,741,824b is the 'real' figure.

---

### Post by KdotJ on 2010-07-11
Remember that the lowercase b means bit, as stated by chriswyatt
 
1kB != 1024b
...
But rather
...
1kB == 1024B

since we are getting technical on terminology lol

---

### Post by WinterRain on 2010-07-11
If I buy an 80gb hard drive, I realize I am really getting 74, and not getting ripped off. That's just the way it is.

---

### Post by cariboo on 2010-07-11
Asked and answered many times, moved to recurring.

---

### Post by McRat on 2010-07-11
I'm still in awe of anyone who can use the term ONLY with 232 billion.

Let's say you DO get them to pay you back.  A 1TB drive is now under $100, so that's 10GB per dollar.  They owe you a cheeseburger.

Seriously, on the Retail packages for most drives, and even a lot of ads now, tell you that they are sold per billion (10^9) bytes, not (2^30) bytes= 1073741824.  You're not being ripped off.  In the past they understated the drive size.

But if it's any consolation you are still ripping of the RAM mfr's as a 4 billion for them is actually 4294967296.

---

### Post by Queue29 on 2010-07-11
[http://www.wolframalpha.com/input/?i=250+Gigabyts+in+Gibibytes](http://www.wolframalpha.com/input/?i=250+Gigabyts+in+Gibibytes)

---

### Post by kamaboko on 2010-07-11
Good thing you didn't by a 1 or 2TB drive.  You would have been in for a big surprise.

---

### Post by ov3rcl0ck on 2010-07-11
They,the manufacture, used the gigabyte, which is 1000MB to make a gigabyte. Which isn't proper.

What ever you're seeing is displaying in a base of 1074MB to the gigabyte, which is the proper way to measure it, because 1074 is divisible by 8. 8 is the magic numbers, because it takes 8 bits to make a byte.

---

### Post by jerenept on 2010-07-11
> **ov3rcl0ck said:**
> They,the manufacture, used the gigabyte, which is 1000MB to make a gigabyte. Which isn't proper.

What ever you're seeing is displaying in a base of 1074MB to the gigabyte, which is the proper way to measure it, because 1074 is divisible by 8. 8 is the magic numbers, because it takes 8 bits to make a byte.

1024 Bytes = 1Kilobyte

the magic number is 2

1024=2^10

---

### Post by McRat on 2010-07-11
It is nice that we can argue about the def of Billion.  I remember the same question asked about MB vs million bytes of HDD space.

---

