---
title: "FDE + bad HDD = instable system?"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by aef54 on 2012-09-03
I installed Ubuntu using the alternate installation disk and opted for the option of** full disk encryption**.

However the OS shows unstable behavior. After a few minutes of using it, it reacts very slow. The computer sometimes (temporarily) **freezes or even crashes** when an application (like Firefox) is opened.

I do use a pretty **old **(second hand) hard disk. However it worked fine when I installed **Ubuntu without encryption** on it.



My question: is it possible that Ubuntu with full disk encryption is more vulnerable for bad hardware than a regular unencrypted OS?




[COLOR=White].[/COLOR]

---

### Post by opensshd on 2012-09-03
Interesting link here: [https://help.ubuntu.com/12.04/ubuntu-help/disk.html](https://help.ubuntu.com/12.04/ubuntu-help/disk.html)

Have you checked the disk utility tools from the dash menu? There are some benchmarking type tools there that may give some insight to your disk health.

From what I understand, FDE (full disk encryption) does not significantly impact disk performance. There are some comparative benchmarks on google if you search a bit.

Edit: When did the problems start? Directly after install or after more software installations?

---

### Post by aef54 on 2012-09-03
Installation went smooth. Problems started shortly after installation. I didn't install much software, just a few lightweight programs (like TrueCrypt).

Further details:
- I did check the integrity of the installation disk
- I wiped the drive and reinstalled the OS several times (yes I have too much time)

I have not checked the health of the hard disk. That is a really good idea, since the problem is probably in that department. When I used DBAN on it (software to securely wipe a hard disk), it also crashed halfway, which (I think) indicates disk problems. I'm going to seriously look into that.

Say the disk is broken, is it likely that a broken HDD would that cause more trouble in an encrypted system than in a regular OS?

---

### Post by opensshd on 2012-09-04
Hmmm, when hardware fails it can lead to a swath of odd behaviors, especially hard drives in my experience.

Most times they do not cease functioning in one moment. Instead they kinda fade away... it'll work for a while, then fade out on heavy load - then they'll come back for a while.

I've done data recoveries where the best I could do was take a few MB's of data at a time before letting the disk "rest" for the next access :|

The good news: storage is cheap now! You should be able to put on a terrabyte for far < $100.

Whether or not the disk is encrypted, if it is having problems accessing data, it's not going to work out well.

Encryption is basically running data through an algorithm that scrambles it to a point that the entropy (the amount of uncertainty of randomized variables) requires more processing power/time to decipher than is reasonable. The strongest ciphers would actually take the fastest computers many of our lifetimes to decipher - hence, it's not realistically decipherable via brute force (guessing encryption keys), if implemented correctly.

Most of the work is done by your processor, it will read encrypted data and decrypt it 'over the wire' to use it. When you write data, it is scrambled by the processor and written as encrypted data. So, whether or not the data is encrypted or not, the work is the virtually the same for the disk.

---

