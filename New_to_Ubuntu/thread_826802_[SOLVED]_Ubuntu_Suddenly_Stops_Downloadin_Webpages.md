---
title: "[SOLVED] Ubuntu Suddenly Stops Downloadin Webpages and Email"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by GregDonhardt on 2008-06-12
Hi Guys,

Been running Ubuntu 8.04 fulltime for about a week. But today at aroudn 11am, Firefox 3 beta 5 stopped downloading webpages. Thunderbird also stopped downloading mail from Gmail. Firefox behaved as if it was going to download a page, but then nothing was returned. Similarly, thunderbird was able to authenticate to the servers, but would time out when trying to download the mail using Imap. I went to a terminal and tried pinging different sites, all sites successfully. I tried to add a different browser to my installation in case the problem was with firefox, but when i went to download new packages ubuntu was unable to. It just sat there without any downloading occurring. I was able to download a file using wget in a download window. Tried several different sites around the world with no luck. It seems odd that ping is working, but firefox and thunderbird are having issues. I have checked my intwernet connection with a Windows machine and it is working fine. Router also reports no issues. 

Anyone got any ideas why it would suddently stop working, what I can do to fix it or anything I can try to find the problem.

---

### Post by ukripper on 2008-06-12
> **GregDonhardt said:**
> Hi Guys,

Been running Ubuntu 8.04 fulltime for about a week. But today at aroudn 11am, Firefox 3 beta 5 stopped downloading webpages. Thunderbird also stopped downloading mail from Gmail. Firefox behaved as if it was going to download a page, but then nothing was returned. Similarly, thunderbird was able to authenticate to the servers, but would time out when trying to download the mail using Imap. I went to a terminal and tried pinging different sites, all sites successfully. I tried to add a different browser to my installation in case the problem was with firefox, but when i went to download new packages ubuntu was unable to. It just sat there without any downloading occurring. I was able to download a file using wget in a download window. Tried several different sites around the world with no luck. It seems odd that ping is working, but firefox and thunderbird are having issues. I have checked my intwernet connection with a Windows machine and it is working fine. Router also reports no issues. 

Anyone got any ideas why it would suddently stop working, what I can do to fix it or anything I can try to find the problem.

Have you changed/installed anything new lately?

---

### Post by producer on 2008-06-12
I had a sililar problem with Evolution authenticating  I wonder if it could be something wrong with a PAM update.  The common aspect of the problem seems to be authentication.  My Firefox is working OK, however and I can use webmail.  What has happened to me now is I've lost my panel and my taskbar, but that's on another thread.  Something has royally messed up my system and I'd watch out for further problems.  Put links to your programs on the desktop in case you have similar problems.

---

### Post by GregDonhardt on 2008-06-12
I installed some software updates, there were a couple of dozen and I cant recall what they are. 

Thing is though, after installing those updates, it was still ok for a couple of days. Its really bizarrre. The fact that the network is actually working ok, and I can ping is really weird. It's only when you come to browsing and downloading imap email from Gmail through thunderbird.

---

### Post by ukripper on 2008-06-13
> **GregDonhardt said:**
> I installed some software updates, there were a couple of dozen and I cant recall what they are. 

Thing is though, after installing those updates, it was still ok for a couple of days. Its really bizarrre. The fact that the network is actually working ok, and I can ping is really weird. It's only when you come to browsing and downloading imap email from Gmail through thunderbird.

can you go to terminal and run firefox from there:
```
firefox
```

and post any output you get on terminal here.

---

### Post by GregDonhardt on 2008-06-14
SOLVED!

There was a DNS issue with my network card. So I have now forced it to a different DNS server and it is working like a charm.

Greg

---

