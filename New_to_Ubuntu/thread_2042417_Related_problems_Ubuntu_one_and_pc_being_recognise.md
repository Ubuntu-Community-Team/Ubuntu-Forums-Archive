---
title: "Related problems? Ubuntu one and pc being recognised as different device on login"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by queendeagle on 2012-08-14
Whilst I've been a home user for some time, I'm definitely still very much a beginner.

I've just gone from 11.04 to 12.04. I used the alternate CD and set up an LVM with encrypted drives & swap for both 11.04 and 12.04.

Because I've used LVM, I bypass the login screen.

First issue - I haven't set up a static IP (I tried once on 11.04 and couldn't get it to work), but this was never an issue before. But for some reason every time I login, my router and ubuntu one thinks my device is different. I've set up port forwarding on my router for Deluge and have to re-assign it to my device every time.  Why is my device being recognised as different every login? Would setting up a a static IP solve this?

Second issue - I'm getting "auth failure" on ubuntu one. When I login in, it gets stuck "getting information, please wait". I have the option to click next, but when I do that, I get the auth failure. I've tried all the steps here [https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/](https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/)

With ubuntu one, when I open it for the first time after reboot I do get a message saying that my key wasn't unlocked on login and it asks for my password. Ubuntu one also recognises my device as being different despite being the same one.

This is the first time I've tried to use ubuntu one

```
user@home:~$ u1sdtool -s
State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING
```

---

