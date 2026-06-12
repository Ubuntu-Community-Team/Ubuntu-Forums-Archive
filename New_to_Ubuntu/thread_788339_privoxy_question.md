---
title: "privoxy question"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by chadwit on 2008-05-09
I followed the instructions as dictated here:
[https://help.ubuntu.com/community/TOR]("https://help.ubuntu.com/community/TOR")

When starting it with "sudo /etc/init.d/privoxy start", I get the following response: Starting filtering proxy server: privoxy.

However when I try "netstat -a | grep 9050", I get nothing. Should I have a privoxy process running? If I should, I don't.  

Any ideas? How can verify that the app started? Why do I net get a LISTENING response to the netstat?

thank guys...

---

### Post by computerjunkie on 2008-05-09
privoxy is a filtering/http proxy service that runs on 8118, the instructions you are following tell you to run the netstat command after you start the program "tor". Tor runs on 9050, not privoxy thats why there is no output, also you must install tor for the proxy services to run properly. if you want to check to see if privoxy is running type ps -e in terminal and look for privoxy. have you installed tor yet?

---

### Post by chadwit on 2008-05-09
Ahhhh... I didn't know privoxy was dependent on Tor. Yes I have it installed but I hadn't started it yet. Anyway, I started Tor and life is good. Thank you Mr. Junkie!!!!

---

### Post by computerjunkie on 2008-05-09
anytime. I believe tor and privoxy start on boot. tor uses a lot of bandwidth so you might want to consider setting it so tor wont start on boot. This, if I remember correctly, is modified in the "sessions" options under preferences in the tab "session options".

---

