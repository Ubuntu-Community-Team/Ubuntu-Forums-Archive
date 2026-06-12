---
title: "Set default web browser"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by rjmoerland on 2008-04-26
OK, so I upgraded 7.10 to 8.04, and, though there were some minor issues, most is working properly now. I only ditched Firefox 3, since one of the extensions I use regularly is not supported (yet). Instead, I reinstalled Firefox 2. Firefox 2 is working just fine, but links in e-mails are not opened if I click on them in Thunderbird. 

Then I remembered the Preferred Applications panel, and set it to 
```

/usr/bin/firefox-2 "%s"

```
for the default web browser.

Now firefox does get opened if I click on the help icon in the Application menu (totally unrelated to my problem, but it then says 'file not found'. Weird). However, still no Firefox when clicking in links in Thunderbird. 

Any suggestion would be appreciated, not a big problem though.

Cheers!

---

### Post by gn2 on 2008-04-26
If you check on the link in my sig back to Firefox 2.....

Hopefully it should do the trick.

---

### Post by natirips on 2008-04-26
Have you tried opening firefox, than Edit -> Preferences, look around all the options and you should be able to find the "Check Now" button to check whether it is your default browser. If it is not, it will ask you if you want to set it so.

Another thing you can try are the options/settings in Thunderbird itself. I'm sorry but I can't really help you in details about Thnderbird as I haven't used it even once in my lifetime (I just love webmails).

---

### Post by rjmoerland on 2008-04-26
Thank you both for the suggestions. I indeed did remove the .mozilla/firefox folder, but did not lock FF3 in Synaptic. Should I? Firefox 2 is running happily :)

I also had checked the 'default browser' setting in firefox itself, and it did not complain about not being the default. So far, it seems that Firefox 2 indeed is the default browser, since

1) It is opened whenever I press the help button in the Applications menu
2) Firefox does not complain that it is not the default browser ;)

So, I'm guessing it's something with Thunderbird, though I can't find a setting related to links.

Thanks again!

---

### Post by gn2 on 2008-04-26
If you lock FF3 in Synaptic, then it won't be offered as an update by update manager.
Unless you check all the updates before installing them (as everyone should but doesn't always....) FF3 could find it's way back onto your PC unless you lock it.

---

### Post by rjmoerland on 2008-04-27
I've followed the instructions on this page: [http://justanothertechblog.blogspot.com/2006/07/thunderbird-configured-to-open-links.html]("http://justanothertechblog.blogspot.com/2006/07/thunderbird-configured-to-open-links.html")

This gave me back my clickable links in Thunderbird. In my opinion, it's  a bit of a hack, since I think Thunderbird should use whatever is the default web browser. It gets the job done though.

---

### Post by qpieus on 2008-04-27
> **rjmoerland said:**
> I've followed the instructions on this page: [http://justanothertechblog.blogspot.com/2006/07/thunderbird-configured-to-open-links.html]("http://justanothertechblog.blogspot.com/2006/07/thunderbird-configured-to-open-links.html")

This gave me back my clickable links in Thunderbird. In my opinion, it's  a bit of a hack, since I think Thunderbird should use whatever is the default web browser. It gets the job done though.
Thanks for that. I installed firefox 3 yesterday, removed it after about 2 minutes of use and reinstalled firefox2. Http links no longer worked from thunderbird. That's because the firefox2 application name is firefox-2 now instead of plain old firefox. Your link refreshed my memory on how to fix the http link problem.

---

### Post by rjmoerland on 2008-04-27
Hehe, you're welcome :D

---

### Post by rjmoerland on 2008-04-28
Here's a little follow-up: though Thunderbird now opened links inside e-mails, the rest of my Xubuntu desktop was still browser-ignorant. I tried setting the preferred browser to firefox-2, but Xubuntu simply ignored this. I finally created a symbolic link to firefox-2 and named it firefox. Suddenly all links became clickable again. Does anyone have a clue where Xubuntu stores the preferred browser setting?

---

