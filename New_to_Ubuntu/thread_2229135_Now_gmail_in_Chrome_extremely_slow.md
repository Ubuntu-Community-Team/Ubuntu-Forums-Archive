---
title: "Now gmail in Chrome extremely slow"
date: 2014-06-11
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-06-11
Recently I had a problem with Firefox running slowly and the matter was quickly resolved:

> [http://ubuntuforums.org/showthread.php?t=2219036&highlight=Firefox+extremely+slow](http://ubuntuforums.org/showthread.php?t=2219036&highlight=Firefox+extremely+slow)

This is a similar but sufficiently different problem that the earlier FF solution doesn't seem to apply.

To recap, I normally run Chrome, Chromium, and FireFox concurrently in 14.04 (Gnome 2 no effects) with 16 GB RAM. At the moment, neither Chromium nor FF is running, but Chrome is on go-slow. To further complicate things, it is only gmail in Chrome that is running slowly. Other tabs (i.e., not gmail) seem to work at normal speed. AND if I open an incognito browser, gmail operates normally (even while gmail in a normal Chrome browser is very slow)

Other considerations:

47% of RAM being utilized (this is about as low as it ever is. It would be higher if I had the other two browsers running. Over a period of days, will all three browsers running it will build up into the low 90's, everything slows down, and I just restart to clear the congestion.)

Chrome has Script Defender installed. One might suspect this, but gmail in Chrome usually runs at the same speed as in Chromium and FF, so this may or may not be an issue. Also, if SD were causing an issue, it would likely affect all the tabs, not just gmail.

Also Google Docs extension and XMarks Bookmarks Synch extension are installed. They have been installed for a long time and previously gmail ran normally in Chrome, so I do not suspect them.

Any ideas?

---

### Post by gifford on 2014-06-11
Do you have the latest update for Chrome? After today's update Chrome is running faster and the small
issues I have been having with the previous version have been resolved.

---

### Post by Odyssey1942 on 2014-06-11
I may have posted a couple of hours too early. Suddenly, gmail is running normally.

Version shows to be 35.0.1916.114. How can I determine whether my browser was updated today?

Edit: now it's slow again. I would blame gmail, but it runs normally in an incognito window.

---

### Post by Odyssey1942 on 2014-07-02
Fortunately have been out of town and haven't had to endure this, but now back and am suffering with performance that reminds me of the old 56k telephone modem days.

Both Chrome and Chromium are dreadfully slow. I have Script Defender enabled in the Chrome version, but not in Chromium. Thought SD might be the problem, but the Chromium is just as slow. 

16GB RAM, so should not be a problem, and since this is a recent development, fairly sure this is not the issue.

Can someone please make some suggestions that I can run down, or whether I should reinstall? If the latter, just the two browsers or 12.04 also?

---

### Post by Odyssey1942 on 2014-07-04
Bump

---

### Post by lotharmat on 2014-07-04
I'm seeing a very speedy chrome (14.04) gmail very quick too!

I'd can your profile first (for chrome) and see if that helps! May explain why incognito is quicker!

---

### Post by Odyssey1942 on 2014-07-04
lotharmat, Thanks for the suggestion. I am not entirely sure what a "profile" is and do not know what the implications are for deleting my own.

What personalization and individual configuration will I lose by deleting my "profile"?

Is there any way to "capture" my profile so as to enable reseting things the way I have them set now in case that doesn't resolve the issue?

---

### Post by startas on 2014-07-04
Chrome 35+ in linux has some serious problems with gmail in general, as i cant even log off, because the button just doesnt react to my mouse clicks, i have to reopen browser many times until i get lucky and it logs off. Chrome 35 for linux is broken version anyway as it has many bugs, so i guess waiting for 36 or even 37 final version would be fair enough before judging if google are complete noobs and switching to, well, another broken browser, because there isnt what to choose from.

---

### Post by Odyssey1942 on 2014-07-04
Hello Startas,

What have you found on the internet about the problems with Chrome 35? Are there any websites that are discussing this?

---

### Post by craig10x on 2014-07-04
I use the extension: Checker Plus for Gmail in conjunction with my web based gmail and it works beautifully with Chrome 35 version...i notifies me promptly when i get mail with a little preview window and i can go right into my mail using it in a few seconds...it even lets you compose an e-mail without actually going all the way into your e-mail account...as i said, works great, and i highly recommend it... :D

---

### Post by monkeybrain20122 on 2014-07-05
> **Odyssey1942 said:**
> lotharmat, Thanks for the suggestion. I am not entirely sure what a "profile" is and do not know what the implications are for deleting my own.

What personalization and individual configuration will I lose by deleting my "profile"?

Is there any way to "capture" my profile so as to enable reseting things the way I have them set now in case that doesn't resolve the issue?

Close Chrome, open the file manager to your home directory, press ctrl+h or choose 'show hidden files' from menu, find the hidden folder .config (note the "." in front), open it, find the folder google-chrome, this is where your profile and settings are stored. Rename it to something like google-chrome-bak and now open Chrome and you are using a new profile.

To switch back, close Chrome, open .config again, delete google-chrome (which was just generated) and then rename google-chrome-bak back to google-chrome.

---

### Post by Odyssey1942 on 2014-07-06
Craig10X, are you suggesting that this will cure the problem in my Gmail, or just sort of a partial workaround?

MB, thanks for the explanation. I have not done it yet because I may have found a solution.

I tried using FireFox instead of Chrome, but ran into some gmail problems there also. 

It occurred to me that the number of gmail accounts that I keep open might be part of this new problem (or the problem). So I opened FF first, with 3 gmail accounts open in three different windows, then Chrome also with 3 gmail accounts open in two different windows. Both seem to be operating normally now, and I am hoping that this will normalize things permanently.

Don't know why having 6 mail accounts opened simultaneously (3 in a normal Chrome windows, 3 in incognito windows) would suddenly start causing problems after many months (probably years) of doing so without slowdown issues, but early indications are that this is the case. Maybe it has to do with a revision of Chrome that doesn't like it?  I notice that users can now have more than 3 gmail instances open in normal windows (not previously the case and that is why I used a combo of normal and incognito, which was a workaround to that limitation.)

Doesn't explain FF, but also since I didn't use FF this way previously (i.e., used Chrome for gmail), it may be similar revision issue there also, or may have also always been a problem with FF and I just didn't know it.

Thanks for the various input. If it keeps operating at normal speed, I will mark this thread solved.

---

### Post by monkeybrain20122 on 2014-07-06
6 gmail account??!! Sounds a bit excessive. :) I have no idea, only open one at a time (I have only 2) but my guess is that now google has integrated its services (some say spying) so things are a lot busier behind the scene when you log into your gmail account. My roommate has a very old laptop running lubuntu, recently he complained that Firefox crashed when he simultaneously logged into both his gmail accounts.. May be related.

---

