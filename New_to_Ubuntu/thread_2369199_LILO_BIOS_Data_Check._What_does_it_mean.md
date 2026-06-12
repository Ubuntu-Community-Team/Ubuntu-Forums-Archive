---
title: "LILO: BIOS Data Check. What does it mean?"
date: 2017-08-19
forum: New to Ubuntu
---

### Post by lukeborg on 2017-08-19
I have noticed while using LILO Bootloader that when selecting Linux to boot, it waits a little bit then says "BIOS Data Check Successful". 

Can anyone explain in some detail what is happening in this BIOS data check?

And,

Why is it that when inputting "compact" in the lilo.conf it drastically decreases the amount of time the BIOS Data check takes to finish? i.e. Without "compact" it can take up to 4 minutes, with "compact" it takes only 6-10 seconds.

I would like this information for my thesis. Thanks a lot and I appreciate your input.

Example bottom line Please note that this is not my system, but rather a relevant picture to the message Lilo gives after finishing with BIOS Data Check:
[IMG]https://www.netadmintools.com/wp-content/uploads/s10-2.gif[/IMG]

---

### Post by vocx on 2017-08-21
> **lukeborg said:**
> ...
I would like this information **for my thesis**. Thanks a lot and I appreciate your input.

Example bottom line Please note that this is not my system, but rather a relevant picture to the message Lilo gives after finishing with BIOS Data Check:


> **lukeborg said:**
> I am **testing different boot loaders for my thesis** and would really appreciate any help.

I have 2 Hard drives:
sda contains Windows 10
sdb contains Linux Ubuntu 16.04


I have installed LILO bootloader on Linux and have configured it and when I restart the system it boots up as it should. The problem is when I type "Windows" it boots up Windows but when I type Linux  it says "Loading Linux." and keeps saying that "Loading Linux......................................................" like its stuck.

I saw your other post about LILO that you made. And to be honest, I don't think you will find much help here.

The reasons are two. First, as far as I know, LILO is not used much nowadays. I think that at some point in the 1990s it was one of the possible bootloaders along with Grub. But eventually, just like Beta and VHS, one technology came on top. So, this is my feeling, that nowadays everybody uses Grub, and nobody knows a thing about LILO. I may be mistaken, but I've never heard anybody using LILO in the past 15 years. I hadn't even thought about LILO in 7 years until this post of yours. My initial reaction was "wait, LILO? Yeah, that exists. Is it still available for installation today? Wow, interesting!"

Second. This forum section, "New to Ubuntu", is probably not the right one for you. You are probably a computer science student working on your university thesis, just like Linus was when he developed Linux. This forum, "New to Ubuntu", is meant for absolute newbies that don't know what Linux is, what a terminal is, how to install packages, how to install their printer, etc. It's really for people who are very new. The kind of questions we answer here are more in the domain of getting newbies to start using their systems, install the video driver, install their wireless card, etc. We don't really deal with computer scientists that try to understand advanced subjects.

Personally, I think you would have more luck contacting the developers or Debian maintainers, or at least posting in a mailing list related to LILO.

---

### Post by lukeborg on 2017-08-21
I understand! I apologise for posting in the wrong section but still thanks for the reply.

---

### Post by vocx on 2017-08-21
> **lukeborg said:**
> I understand! I apologise for posting in the wrong section but still thanks for the reply.
You don't need to apologize. There is no "wrong" section. It's just the reality that this forum is meant for really new users.

But you can still post advanced questions and if you stick around maybe you'd get a reply. There are people in this forum that have been using Linux and Unix for a longer time than your age, probably. I feel sometimes they answer questions in a higher level than the new users can comprehend even. Thus why I mention that the forum is probably not suitable for advanced questions, even if you are technically new to Ubuntu.

---

