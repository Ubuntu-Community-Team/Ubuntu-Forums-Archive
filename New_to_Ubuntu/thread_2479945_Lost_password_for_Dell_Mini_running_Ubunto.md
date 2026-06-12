---
title: "Lost password for Dell Mini running Ubunto"
date: 2022-10-13
forum: New to Ubuntu
---

### Post by johjohjus2 on 2022-10-13
I am not computer literate.  About 8 years ago i purchased a dell mini running ubunto.  I was unemployed.  I played around with it for awhile.  Then i got a job and stopped using the little laptop.  Im retired now and would like to restart the computer.  My problem is for the life of me i cannot remember the password.  Is there a password recovery method?  I am looking for the version im running.  The only name i can come up with is GNOME?  If that helps.

---

### Post by QIII on 2022-10-13
First, it's "Ubuntu", not "Ubunto".

While [this]("https://help.ubuntu.com/community/LostPassword") is a bit old, the instructions should still work for you.

---

### Post by patrick2957672 on 2022-10-13
boot a live linux

mount /dev/xxx /mnt

vim /mnt/etc/shadow

and set :: without * to put no pass to your root account.

---

### Post by Impavidus on 2022-10-14
If it hasn't been used in years, the software will be outdated. Whatever Ubuntu release you had on it 8 years ago has reached end of life now. It's probably best to start with a fresh install.

But if you first want to use it a bit, follow QIII's link.

---

### Post by ActionParsnip on 2022-10-14
[https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword)

---

### Post by TheFu on 2022-10-14
> **Impavidus said:**
> If it hasn't been used in years, the software will be outdated. Whatever Ubuntu release you had on it 8 years ago has reached end of life now. It's probably best to start with a fresh install.

But if you first want to use it a bit, follow QIII's link.

+1.

But the Dell mini may have used a 32-bit CPU. If it did, modern Ubuntu distros don't support 32-bit CPUs and you'll need to get one of the Debian Desktop versions.  Ubuntu went 64-bit only after 2018. 
[https://www.debian.org/distrib/](https://www.debian.org/distrib/) has a link for a 32-bit netinst. That's where I'd start.

But we don't know if the CPU is 32-bit or 64-bit.  Is there any documentation that says clearly which intel CPU model is used?  I fear something like an N1010 CPU.  

How do I say this nicely.  Computers aren't like cars.  Low end computers from 10 yrs ago will struggle doing things that cheap $99 computers easily handle today.  If you aren't technical, then I suspect you'd be best off getting a used chromebook for $75.  Any chromebook since 2012 is faster than a Dell Mini and more capable for typical things that humans do online with their computers.

I did a quick google and found "Dell Mini 1012" - has an Atom N450 CPU. That CPU has a passmark of 200 and just 1GB of RAM. That would be painful to use with nearly any current Linux desktop.  The good news is that the N450 is 64-bit. That's really good news.  My 2012 chromebook uses a Celeron C955U CPU, with a passmark of over 900.  No speed demon at all, but still nearly 4x faster.  Current chromebooks ($89 new), have an AMD A6-9220C CPU with a passmark of about 1300 and come with 4GB RAM and 64GB storage.  That's the cheapest Lenovo Chromebook 1 search found at a nationwide big-box appliance store.  I'd spend about $30 more to get a much better model, while staying cheap. Of course, high end chromebooks sell for $1000+, but I'd never spend more than $200 on a new chromebook these days.  For a tiny bit more than that, a quality used laptop that is extremely capable of running any Linux you want is available.  

My current laptop (bought 3+ yrs ago) was a used $305 Asus with a enough RAM, fast enough CPU, plenty of SSD storage and long battery life. Passmark on it is 6,000.  My home desktop has a passmark of just under 20,000 and was less than $450 for the core components (CPU, RAM, and motherboard).  Just trying to put performance and price into perspective. There are massive leaps in performance with a tiny more cost.

OTOH, if you like to tinker and want to get this working at some level, the Linux learning curve is very steep.  I'd strongly suggest that you join a local LUG - Linux Users Group - show up to their meetings a little early, bring the device, ask for help.  Almost every city in the world has at least 1 LUG, though some areas will merge all the smaller cities for an hour-driving radius into a single LUG.  

My metro area has at least 5 LUGs, each meeting on different days in different parts of the area.  2 of our are online, so we have people joining from all over the world. We are physically in the eastern USA, but have members joining the video conferencing from India, Denmark, Singapore, and all over the USA.  Everyone is welcome.

It is difficult to replace in-person help when it comes to installation and setup of a computer with Linux. Also, the helpers will have network connectivity and be able to get nearly any software even if your system doesn't boot yet.

---

