---
title: "Howto: Make Firefox handle aim links with gaim"
date: 2005-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by lynng on 2005-04-21
I wanted Firefox to automatically pop up a gaim message window when I click on AIM links in webpages.  I searched the forum & googled, and haven't found a step-by-step for newbs like me.  So here goes:

1) In gaim, click Tools->Preferences->Plugins & click the check box next to "Remote Control" (You may need to restart gaim)

2) In Firefox, type about:config in the location bar.  Then right click in the list, and select New->String.  In the box that pops up, type ```
network.protocol-handler.app.aim
``` & click OK

3) In the second box that pops up, type ```
gaim-remote uri %r
```

If anyone knows how to get the same functionality for Thunderbird,  please post.

edit: Having become more familiar with the forums since this post, I realize it should probably be moved to the "Customization Tips & Tricks" forum instead.  Sorry.

---

### Post by TravisNewman on 2005-04-21
Wow, you're my hero ;)

I didn't even think that this was possible.

---

### Post by poofyhairguy on 2005-05-13
bump for this awesome howto

---

### Post by brentroos on 2005-10-10
*

---

### Post by NaWer on 2005-10-10
For thunderbird, see the extension [aboutconfig](http://aboutconfig.mozdev.org/)
maybe it's the same trick

---

### Post by lynng on 2005-10-10
Well, I tried making an entry for
```
network.protocol-handler.app.ymsgr
```
with the same value, but I keep getting a "not a registered protocol" error.  I don't know the syntax for linking to an msn account, so I haven't tried that.

---

### Post by lynng on 2005-10-10
Thanks, NaWer.  Using this extension to make an entry for aim now has the links working in Thunderbird.

---

### Post by five_rings on 2006-06-25
[QUOTE=lynng]I wanted Firefox to automatically pop up a gaim message window when I click on AIM links in webpages.  I searched the forum & googled, and haven't found a step-by-step for newbs like me.  So here goes:

1) In gaim, click Tools->Preferences->Plugins & click the check box next to "Remote Control" (You may need to restart gaim)

2) In Firefox, type about:config in the location bar.  Then right click in the list, and select New->String.  In the box that pops up, type ```
network.protocol-handler.app.aim
``` & click OK

3) In the second box that pops up, type ```
gaim-remote uri %r
```

If anyone knows how to get the same functionality for Thunderbird,  please post.

edit: Having become more familiar with the forums since this post, I realize it should probably be moved to the "Customization Tips & Tricks" forum instead.  Sorry.[/QUOTE]

Thanks for all the work you did...

I went through all the above steps to configure my netscape and firefox... it didn't work, however. :-k  Both browsers still don't recognize my yahoo link... IE does. Did they make any changes to the protocol/configuration since the message was posted?

Thanks in advance... Five Rings

---

### Post by lynng on 2006-06-25
[quote=five_rings]Thanks for all the work you did...

I went through all the above steps to configure my netscape and firefox... it didn't work, however. :-k  Both browsers still don't recognize my yahoo link... IE does. Did they make any changes to the protocol/configuration since the message was posted?

Thanks in advance... Five Rings[/quote]

Well I only ever confirmed it to work with AIM, not Yahoo.  I haven't tried it with Firefox 1.5, but I'll try later & see if I can get it to work.

---

### Post by dkbg on 2007-02-04
Hmm, I've gotten it to work using Firefox 2 by adding another about:config option, namely a boolean option of "network.protocol-handler.external.aim" set to true. The problem is that it will only work with aim: links that include a screen name (i.e. aim:goim?**screenname=foo**&message=bar) which makes it pretty much useless. It isn't really a useful feature for me anyway, I was just messing around.

---

