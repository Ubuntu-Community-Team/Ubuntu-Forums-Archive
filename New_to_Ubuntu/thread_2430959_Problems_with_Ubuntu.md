---
title: "Problems with Ubuntu"
date: 2019-11-09
forum: New to Ubuntu
---

### Post by mitmag on 2019-11-09
Hi all:

  I have a question. I am running Ubuntu 14.04  and Lubuntu 18.04.

After booting both versions something starts running in the background after about 5 minutes.

It will run for some time. I have to reboot the machine to stop it. After I do this it never runs again

until I start it after shutting it down. I have tried for weeks to find out what is going on.

Does anyone out there know what it is and how to stop it? If I disconnect from WIFI it will still

do the same thing. Thanks for your time and have a great day!

---

### Post by TheFu on 2019-11-09
Free support for Ubuntu 14.04 ended in July or June.  No patches to fix remote kernel access have been released since then or any other security patches without a paid support contract. If you aren't paying for support, time to move/delete that 14.04 install.

To see what might be running out of the 10,000+ options, should we start guessing?  Is it a mv?  y/N?   We can keep guessing for the next few years.

Or you could look in the process table for running processes.  That would probably be faster.  Use **top** or **htop** to see running processes. They are ordered by CPU use.  These tools are basic for any Unix user.  [https://www.tecmint.com/12-top-command-examples-in-linux/](https://www.tecmint.com/12-top-command-examples-in-linux/) and the *top manpage* is good too.

If you tried using these tools already, what else have you tried?  On my systems, I run monitoring tools which centrally report every minute what each system is doing.  Having this data BEFORE it is needed means not being surprised and already having the data to proactively troubleshoot issues.

---

### Post by mitmag on 2019-11-10
TheFU:

Thanks for your comments! Please don't tell me what I should be using. If you can

answer my question, that is fine! I will use what I feel is best for me! That is NOT for you

to decide! Version 14.04 is what I want to use! Thanks!

---

### Post by oldrocker99 on 2019-11-10
14.04 is **no longer supported.** Why are you determined to use it, when there's real reason to keep using it?

Ubuntu puts out 2 releases a year, and only the LTS versions, which come out every even-numbered year in April, have long-term support. 14.04 has reached its End Of Life, just like Windows 7.

This is what's best for you! This is NOT for me to decide.

You say you have 18.04. What is the reason that you need to keep using 14.04?

---

### Post by Impavidus on 2019-11-10
We don't support Ubuntu 14.04, so we can't help you with that. We do support Lubuntu 18.04. So, what does top tell you? If the process uses enough cpu time to trouble you, it must be easy to find.

---

### Post by The Cog on 2019-11-10
Using top to see what the top CPU using processes are would be my first step. Two things I can think it might be are the automated check for updates, and the periodic **updatedb** process for scanning the disk and filling out the location database used by the **locate** command for quick file searches. Both of those run occasionally, but neither runs for more than a few minutes.

---

### Post by uRock on 2019-11-10
> **mitmag said:**
> Version 14.04 is what I want to use! Thanks!
We do not offer support for EOL versions.

Feel free to start a new thread after upgrading or installing a supported release.

Thread Closed

---

