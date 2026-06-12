---
title: "Using wireless in a hotel"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by swa2b41 on 2008-06-12
hey there all, I gave my kids a laptop with Ubuntu on it and they stay in a lot of hotels anyways when they try to use the wireless it says they need netscape or internet explorer why is that and is there anyway they can use firefox to get connected? I had it connected at my house no propblem I don't get why they can't and please don't say they need to download this or that because they can not get on the internet. I'm hoping that there is a simple answer. They are both very inexperienced with Ubuntu so any ideas need to be laid out very plain and simple please please please and thank you thank you thank you.... jen...

---

### Post by bthoward on 2008-06-12
Usually the only reason it doesn't work is because the website they are using requires one of those two browsers but doesn't really need that in order to work.  

Go to this link on the laptop:
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

Then install that plugin.  Then under tools you'll have a user agent switcher that will allow you to select that your firefox should report that it is Internet Explorer.  This way the system on the other end will think its talking to internet explorer and it will probably work just fine.  

If it doesn't post here and we'll walk you through installing IEs4Linux.  Either way there is definitely a way to get you what you want.

---

### Post by wootah on 2008-06-12
> **swa2b41 said:**
> hey there all, I gave my kids a laptop with Ubuntu on it and they stay in a lot of hotels anyways when they try to use the wireless it says they need netscape or internet explorer why is that and is there anyway they can use firefox to get connected? I had it connected at my house no propblem I don't get why they can't and please don't say they need to download this or that because they can not get on the internet. I'm hoping that there is a simple answer. They are both very inexperienced with Ubuntu so any ideas need to be laid out very plain and simple please please please and thank you thank you thank you.... jen...

Sounds like the people who manage the hotel wireless setup a web page based gateway that will not let you through unless the browser sends a user agent string (to identify the browser type) with IE as the browser type. 

I think I am understanding you correctly here... you CAN connect to the wireless network, you just can't browse web pages? If this is _exactly_ the case, here is what you do:

We make the world 'believe' that we are using IE:

_**How to change User Agent String of [Mozilla Firefox]("http://www.walkernews.net/2007/06/03/where-is-firefox-internet-files-cache-folder")?**_
 
[LIST=1]
[*]Type about:config in the [Mozilla Firefox]("http://www.walkernews.net/2007/05/30/retrieve-flash-video-from-firefox-cache-folder/") address bar and press ENTER,
[*]Type general.useragent.extra.firefox in the Filter bar,
[*]Double-click on the returned Firefox setting, where you can change or spoof a user agent string to overwrite the default “Firefox/2.0.0.4&#8243;!
[/LIST]
Change it to **Mozilla/4.0 (compataible; MSIE 6.0; Windows NT 5.1)** but don't forget to write down your old one to change it back later on.

Good luck! :)

---

### Post by billgoldberg on 2008-06-12
Or you could just install netscape, it's based on firefox anyway.

[http://linuxowns.wordpress.com/2007/12/12/netscape-navigator-9/](http://linuxowns.wordpress.com/2007/12/12/netscape-navigator-9/)

---

### Post by swa2b41 on 2008-06-13
Thanks I will be talking to them tonight and if what you have suggested doesn't work I will repost, thanks so very very much... Jen...

---

