---
title: "Firefox consuming much CPU ..."
date: 2016-02-05
forum: New to Ubuntu
---

### Post by cwmoser on 2016-02-05
I typically keep one session of Firefox running but with approximately 10 tabs.
Today I noted Firefox a little sluggish and checked System Monitor.
System Monitor showed FireFox consuming a lot of CPU.

I went and closed all Firefox Windows, but noted that Firefox was still consuming
a lot of CPU.  Did a **ps ax** command and there was a /usr/lib/firefox/firefox process running.
So I kill that process and start Firefox back up.
Now Firefox is running but consuming much less CPU, and seems much more responsive.

My questions are:
1- what caused this "zombie" Firefox process even after I closed all the Firefox windows?
2- Any tips on how to keep this from happening again?

Thanks

Carl

---

### Post by monkeybrain20122 on 2016-02-05
Clean  your cache. [https://support.mozilla.org/en-US/kb/how-clear-firefox-cache](https://support.mozilla.org/en-US/kb/how-clear-firefox-cache) or more thoroughly run bleachbit  as normal user (instead of root) with the appropriate boxes checked, bleachbit is in the repo. Firefox gets slow if your cache grows too big.

---

