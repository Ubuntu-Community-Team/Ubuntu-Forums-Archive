---
title: "Latest updates have killed my wireless!"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by UncleAsriel on 2013-05-26
I just tog the latest updates for ubuntu 12.04 (Precise Pangolin).

Last night, I restarted my computer after installation, and now my wireless device isn't working. Given how this is my sole means of internet access, I'm a little worried, to say the least.

I had a previous issue with this (chronicled [here]("http://ubuntuforums.org/showthread.php?t=2140063")), and had it fixed by blacklisting some drivers.

Since then, I re-attempted all of the instructions in the linked thread), but they were ineffective.

Oddly, when I boot vista, the wireless works fine. This makes me sure that it had to do with one of the 35 updates which I installed. It has to be one of [these ones]("http://www.ubuntuupdates.org/packages/latest_logs?utf8=%E2%9C%93&dist=precise&commit=Filter&noppa=0&levels%5Bbackports%5D=1&levels%5Bproposed%5D=1&levels%5Bsecurity%5D=1&levels%5Bbase%5D=1&levels%5Bupdates%5D=1") (assuming that this site does what I believe it to do and that my link is working).

Is there any way to narrow it down to pick out individual packets which are the problem? Or do I have ti disable/uninstall each of them individually?

How do I even go about doing that on the command line? 

Please find attached the list of commands from lsmod (regrettably, I forgot how to recreate netinfo.txt)

[ATTACH]243061[/ATTACH]

---

### Post by UncleAsriel on 2013-05-26
Here is a list of the updates I installed yesterday - the question becomes, which one is the problem?

[ATTACH]243096[/ATTACH]

---

### Post by Jock123 on 2013-05-26
I have had the same problem, with the same module. The module seems to *disappear* every now and then, but I've always been able to solve it by following the instructions in post #13 of the link you provided.

I am no expert(!) but did you get any errors when running
```
sudo ./install.sh
```

---

### Post by wildmanne39 on 2013-05-26
Hi, you more then likey need to install the driver again because the kernel was updated.
Thanks

---

### Post by UncleAsriel on 2013-05-26
Wild Man: I installed the driver again. I had the same file I downloaded when I initially had the problem on my desktop, and ran. I was told that there was an error installing it. 

Jock123: I will try that now.

[EDIT]Reinstalled Ubuntu. The problem has been repaired. Ugly fix but it worked.


Problem solved. Thread closed.  Thanks, everyone!

---

