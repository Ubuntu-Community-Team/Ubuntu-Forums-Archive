---
title: "Browsing problem"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by pracrichard on 2012-10-06
Hi,
I have a strange browsing problem which is driving me nuts. One particular website which I access quith often [www.stags.co.uk](www.stags.co.uk) automatically diverts to m.stags.co.uk which is the version of their site designed for viewing on a mobile device.
This problem does not occur on a windows machine - wife's XP desktop or presumably others. 
The problem started about a month ago.
It occurs both on my desktop machine running Ubuntu 11.04 and my laptop which runs 12.04.
Both Google Chrome and Firefox are equally affected.
I have complained to Stags but they don't seem able to do anything their end.
Has anybody any ideas? Many thanks 

Richard

---

### Post by vasa1 on 2012-10-06
I see the same thing. Do you know how to change your user agent string? Try replacing the current one with a Windows one. It may so happen that the site is browser-sniffing and doesn't recognize the user agent string used by the Linux versions of Chrome and Firefox.

---

### Post by oldsoundguy on 2012-10-06
It also could be that the site wants to see IE only for computers (and agent switcher works fine for other sites but not this one.) When it detects something else, it ASSUMES you are a mobile device. .... which is really stupid as IE has less than 1/3 of the browser market now! (maybe you should point that out too the company?

---

### Post by pracrichard on 2012-10-06
Many thanks for your comments. No I don't know how to change my user agent string. can you please point me to the info?

I'don't think it's a browser specific problem as we have Chrome and Firefox on the Windows machine too - we never use IE - and they both work fine.

---

### Post by will1982 on 2012-10-06
Hello,

I don't know much about this subject, but you can try clearing cache, history, and cookies.

Also, is there a button on the bottom of the site that says "Desktop Version" :P

---

### Post by vasa1 on 2012-10-06
> **pracrichard said:**
> Many thanks for your comments. No I don't know how to change my user agent string. can you please point me to the info?

**I'don't think it's a browser specific problem** as we have Chrome and Firefox on the Windows machine too - we never use IE - and they both work fine.

I wrote this:
 It may so happen that the site is browser-sniffing and doesn't recognize the user agent string used by **the Linux versions** of Chrome and Firefox.

You can get a lot of information on the net about user agent strings and how to change them in case a site is easily fooled.
In the meantime, there's an extension that will help for Firefox:
[URL="https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/"]User Agent Switcher 0.7.3
[/URL]

---

### Post by pracrichard on 2012-10-07
Many many thanks Vasa1. 

Agent switcher works perfectly! Setting it to IE8 means that I now have full access to the site I need through Firefox.

---

### Post by vasa1 on 2012-10-07
You're welcome! Although I haven't looked, I'm sure there'll be a similar extension for Chrome as well.
Alternatively, you could have "two" Chromes: one with the regular string and one with the modified one and use the modified one just for pesky sites.

---

