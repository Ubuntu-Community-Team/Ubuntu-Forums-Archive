---
title: "linux security"
date: 2009-07-03
forum: Recurring Discussions
---

### Post by asliyanage on 2009-07-03
someone says linux is free from virus and is much better security than windows.what is the reason for this ?is there a specefic answer for this?

---

### Post by DGortze380 on 2009-07-03
> **asliyanage said:**
> someone says linux is free from virus and is much better security than windows.what is the reason for this ?is there a specefic answer for this?

IMO, the largest reasons are restrictions on administrative tasks (root user model) and frequency of updates/patches in that order.

---

### Post by paul_be on 2009-07-03
> **DGortze380 said:**
> IMO, the largest reasons are restrictions on administrative tasks (root user model) and frequency of updates/patches in that order.

Agreed the access control in linux is much better (fundamentally) than m$ also addition of apparmor and selinux can lock down your system even further.

[http://en.wikipedia.org/wiki/AppArmor](http://en.wikipedia.org/wiki/AppArmor)
[http://en.wikipedia.org/wiki/Security-Enhanced_Linux](http://en.wikipedia.org/wiki/Security-Enhanced_Linux)

---

### Post by SunnyRabbiera on 2009-07-03
Yes the main reason why Linux ix invulnerable to Windows viruses is because Windows viruses are made for windows... not linux.
Also Linux is practically virus proof, with the administration account separated from the main user account the administrative tasks are limited unless you do something stupid such as log in as root.
But normally linux users are deterred from using root one way or another, on Ubutu Root is rendered almost completely absent thanks to Sudo, Sudo does the exact same thing as root but there is not really a root account.
There is a lot of security concerning linux.

---

### Post by juancarlospaco on 2009-07-03
Enable SELinux, and the system doesn't be affected by Vulnerability or security threts.
*You can give root password and can't attack your system if SELInux is configured correctly.*

---

### Post by bodhi.zazen on 2009-07-03
> **asliyanage said:**
> someone says linux is free from virus and is much better security than windows.what is the reason for this ?is there a specefic answer for this?

Linux is less vulnerable due to many many reasons. Linux is built from teh ground up to be multiuser and thus more secure. 

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by Tibuda on 2009-07-03
[http://catb.org/~esr/writings/unix-koans/nervous.html](http://catb.org/~esr/writings/unix-koans/nervous.html)

---

### Post by chessnerd on 2009-07-05
> **asliyanage said:**
> someone says linux is free from virus and is much better security than windows.what is the reason for this ?is there a specefic answer for this?

There is no specific answer. There are many reasons for this, a few key ones are:
1. Linux's kernel is updated regularly to make it more secure and to fix bugs, also, it is combed over by hundreds of people to check it's code for flaws. The NT (Windows) kernel is updated much less frequently and is only updated when Microsoft feels like it and only a select few get to look at it for flaws.
2. Linux's user system sets up better permission levels than Windows. An Administrator level Windows user who gets a virus can infect the entire system. An Administrator level Linux user who gets a virus can do much less damage. (The exception is the Linux user who runs as root. Such a person will give the virus total system access, which is why a Linux user should only use root when they need to, never for day to day tasks.)
3. Linux is a smaller target. Many Linux enthusiasts will play this off as a non-issue, but the point is valid. The computer market is 80% Windows and only 5-10% Linux. If you want to write a virus that hits as many users as possible, who will you write it for? If/when Linux gets 30-50% of the market, I will be interested in seeing if the number of viruses increases.

---

