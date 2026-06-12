---
title: "webpage-redirecter (to avoid advertisements)"
date: 2012-08-04
forum: Programming Talk
---

### Post by newsboost on 2012-08-04
Hi,

Sorry I have a hard time figuring out where to ask this question. Anyway: I want to make a / have a webpage-redirecter (to avoid advertisements) and I know python + bash (beginner/intermediate lvl) + c/c++ etc + most basic linux-commands, I've been running ubuntu for 2 years + suse for maybe a few years before.

I want, that for a certain website (someSite.com) then this webaddress:

[http://someSite.com/redirect.aspx?http://anotherSite.com/thisLastPart](http://someSite.com/redirect.aspx?http://anotherSite.com/thisLastPart) is where I want to go DIRECTLY, so in other words:

I don't even want to see this webpage:

[http://someSite.com/redirect.aspx?http://anotherSite.com/thisLastPart](http://someSite.com/redirect.aspx?http://anotherSite.com/thisLastPart) 

I want the browser/os to ignore the first part: [http://someSite.com/redirect.aspx?](http://someSite.com/redirect.aspx?) and just immediately go to:
[http://anotherSite.com/thisLastPart](http://anotherSite.com/thisLastPart) 


How is this task accomplished ?

I thought about /etc/hosts, but I think that is only up until "someSite.com" but I should also remove the "redirect.aspx?"-part...

Update: How about something with DNS ? My problem now is that I have NO clue about where to start, and yet I'm convinced this task must be possible to solve, especially in linux...

Thank you very much!

---

### Post by juancarlospaco on 2012-08-04
You need to do a UserScript.JS
Its javascript, a universal plugin for browsers, google is your friend.

---

### Post by newsboost on 2012-08-05
> **juancarlospaco said:**
> You need to do a UserScript.JS
Its javascript, a universal plugin for browsers, google is your friend.
Uh, thanks a lot for leading me on the right track... I'm a bit busy right now, but now I think I know where to look. Maybe another time, I'll try to make my own (very first) extension (javascript and web development is not my strongest)... I just tried this one:

[https://chrome.google.com/webstore/detail/lacckjdlmkdhcacjdodpjokfobckjclh](https://chrome.google.com/webstore/detail/lacckjdlmkdhcacjdodpjokfobckjclh)

And it's an arbitrary redirector. Looked promising. But I can't make it work. I looked into the source of the webpage (stupidWebPage.com):

<a href="/redirect.aspx?http://someSite.com/something/123123/" rel="nofollow" target="_blank">http://someSite.com/something/123123/</a>

So when I click on stupidWebPage.com (even using the redirecter chrome plugin) I get to:

[http://www.stupidWebPage.com/redirect.aspx?http://someSite.com/something/123123/](http://www.stupidWebPage.com/redirect.aspx?http://someSite.com/something/123123/)

I want to go directly to:

[http://someSite.com/something/123123/](http://someSite.com/something/123123/)


What's the easiest way for me to accomplish this?

I thought that [https://chrome.google.com/webstore/detail/lacckjdlmkdhcacjdodpjokfobckjclh](https://chrome.google.com/webstore/detail/lacckjdlmkdhcacjdodpjokfobckjclh) would do the trick, maybe it doesn't work when the stupidwebpage only has a relative link to itself, still it's strange... I hope someone can push me the in the right direction, maybe give a final push in completing this task in the most simple/easy way, thank you!

BTW: I don't think I'll publish the stupidwebpage-name because if I find a solution and they know somebody is avoiding their advertisements, they'll probably encrypt the url and then this will never work again and I'm / we are're forced to see their stupid ads :-(
Let's keep it a technical question and not talk about the morality in avoiding ads, thanks.

---

