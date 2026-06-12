---
title: "Login to 3 Mobile Internet using curl/wget"
date: 2010-01-07
forum: Programming Talk
---

### Post by OhneHerren on 2010-01-07
Howdy.

I'm trying to write a script to login to my 3 Mobile Internet account, to put my remaining usage into Conky. I've found two blog posts detailing solutions ([here]("http://systemnotebook.blogspot.com/2009/07/log-broadband-use-threeie.html") and [here]("http://altentee.com/2008/mythree-bandwidth-usage-widget/")), but they have not been much help. The first is for a different service, so the login will not work, and the second is written in Ruby. I've found guides on how to login using curl, and have followed the instructions about searching through the source for the form to send and whatnot. Unfortunately this has not helped. I tried to adapt what I could gather from the Ruby code, but it didn't work. I've tried this:

```
curl --cookie cjar --cookie-jar cjar --data 'login=mymobilenumber' --data 'password=mypassword' --data 'form=login' --output ~/3 https://www.my.three.com.au/My3/jfn
```

I've also tried variations on that, and tried with wget. I might be interpreting the source of the login page incorrectly. It is at: [https://www.my.three.com.au/My3/jfn](https://www.my.three.com.au/My3/jfn)

By "not working", I mean that viewing the saved page (I have retrieved it again, using the new cookie settings, after running the above command), returns the standard login page, not the usage report. Although, even when logged in via standard browser, the source of the usage info page appears the same as the log in page; that is, the usage info (what I'm trying to get via curl) doesn't appear in the page source. It is displayed via some fancy javascripting. So maybe it has logged in, but I just can't see the usage info.

I have done something similar with a previous broadband account, but the login page was much simpler. I know this barely contitutes "programming", but I thought this was the most appropriate sub-forum for this. Sorry if this is the completely wrong place. Any help that you can offer me would be greatly appreciated. I'm sure others with a 3 account would benefit. Thanks!

---

### Post by OhneHerren on 2010-01-09
For anyone interested, I found a solution thanks to information posted [here]("http://forums.whirlpool.net.au/forum-replies.cfm?t=1358303").

---

### Post by bobdobbs5 on 2010-08-18
I followed the thread over at whirlpool but seems like the code on  pastebin is no longer there.  Any chance you could repost somewhere?   Thanks.

---

