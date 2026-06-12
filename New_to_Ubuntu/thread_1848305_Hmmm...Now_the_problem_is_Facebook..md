---
title: "Hmmm...Now the problem is Facebook."
date: 2011-09-22
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-09-22
Ok, new problem.
Up until a few days ago, everything on Firefox was working beautifully. Now, out of nowhere, I can't send any messages on Facebook. If I open that same Facebook page on my other computer (on Windows 7), everything works. 

Can anybody tell me what's going on?

Thanks in advance. :)

---

### Post by oldfred on 2011-09-22
My wife noticed Facebook was not formated correctly about 5 or 6 days ago in Firefox (using 3.6.22). It worked fine in my daughters Mac.

I downloaded Chromium and that worked fine, but then yesterday Firefox was ok again. My wife also said she does not like new format but that is what Facebook has changed.  

But it seems to work otherwise.

---

### Post by Inodoro Pereyra on 2011-09-22
Thanks Oldfred for the reply. :)
I agree completely with your wife: the new format sucks.
But this has been going on since before the format change. Maybe it is because of the Firefox version?
I like Firefox 3.6, but, if it doesn't work anymore, I guess I will have to update. Can anybody tell me how to do that?
Either way, Chromium is not an option. I hate the thing.

---

### Post by Inodoro Pereyra on 2011-09-22
Ok, I upgraded to FF 6.0.2, using the instructions here:

[http://www.webupd8.org/2011/03/install-firefox-4-in-ubuntu-1004-1010.html](http://www.webupd8.org/2011/03/install-firefox-4-in-ubuntu-1004-1010.html)

But Facebook messaging still doesn't work. :(

---

### Post by LowSky on 2011-09-22
> **Inodoro Pereyra said:**
> 

But Facebook messaging still doesn't work. :(

use empathy or pidgin for facebook messaging. Much better than using a web browser any day

---

### Post by Inodoro Pereyra on 2011-09-22
Tried it. Doesn't work either. It's giving me a "Network Error". :(

---

### Post by jockyburns on 2011-09-22
Facebook has never worked correctly for every user on there. My sister couldn't use messaging on there for weeks (if not months) using Chrome on WinXP then using IE on Win7. Wasn't her account settings either as they suddenly cleared up one day and have worked correctly for the past few months

---

### Post by Inodoro Pereyra on 2011-09-22
Yeah, but, why does it work on my Windows machine?
I just sent the message I needed to send using that computer, without a hitch.:confused:

In both machines, I'm running Firefox 6, so, why the difference?

---

### Post by Krytarik on 2011-09-22
Did you already check if the issue also occurs with a fresh, new profile?

To do so, just move your profile directory from "~/.mozilla/firefox" to somewhere else. Upon the next start of Firefox, a new profile would be created. To restore your old profile, just remove the newly created one again, and move back your profile directory.

Another way to check if any of your activated add-ons might be the culprit, is to choose "Help -> Restart with Add-ons Disabled". If this works, try finding the conflicting add-on by disabling each of them individually.

Hope it helps!

---

### Post by oldfred on 2011-09-22
A month or two ago my wife did have some issues in Facebook and I compacted & re indexed the sql files. That helped then not sure now, but I plan to reindex after every backup.

Optimize sqlite
[http://web.utk.edu/~jplyon/sqlite/SQLite_optimization_FAQ.html](http://web.utk.edu/~jplyon/sqlite/SQLite_optimization_FAQ.html)

Some have posted bash scripts, use at your own risk. I created my own but copied some of these commands.
[http://pastebin.pl/19714](http://pastebin.pl/19714)

---

### Post by Inodoro Pereyra on 2011-09-22
> **Krytarik said:**
> 
Another way to check if any of your activated add-ons might be the culprit, is to choose "Help -> Restart with Add-ons Disabled". If this works, try finding the conflicting add-on by disabling each of them individually.

Hope it helps!

IT DID!!! :D

I disabled the add ons, and everything works! Thanks again everyone for all the help.

Now, how do I disable each add-on individually?:confused:

---

### Post by Krytarik on 2011-09-22
> **Inodoro Pereyra said:**
> Now, how do I disable each add-on individually?
"Tools -> Add-ons", then choose "Disable" at the respective add-ons. ;-)

And re-enabling is the same way, just "Enable" then.

---

### Post by Inodoro Pereyra on 2011-09-22
> **Krytarik said:**
> "Tools -> Add-ons", then choose "Disable" at the respective add-ons. ;-)

And re-enabling is the same way, just "Enable" then.


Thanks. Will do and report back. :D

---

### Post by Inodoro Pereyra on 2011-09-22
Ok, since Murphy's Law never fails, having several add-ons, it had to be the one I **REALLY** didn't want to disable: Ad Block Plus.
The good news is, I disabled it only on Facebook, and everything seems to be working great.

Thanks again everybody, for all the help. :D

---

### Post by Krytarik on 2011-09-22
> **Inodoro Pereyra said:**
> Ok, since Murphy's Law never fails, having several add-ons, it had to be the one I **REALLY** didn't want to disable: Ad Block Plus.
In fact, I'm using Adblock Plus, too; and don't need to disable it on Facebook. I'm subscribed to the EasyList Germany+EasyList ad filter list, as well as to the EasyList Tracking-Filter. To what filter lists are you subscribed?

See here for available filter lists:

[http://adblockplus.org/en/subscriptions](http://adblockplus.org/en/subscriptions)

EasyList Tracking-Filter URL (surprisingly, not included on their website anymore):

[https://easylist-downloads.adblockplus.org/easyprivacy.txt](https://easylist-downloads.adblockplus.org/easyprivacy.txt)

---

### Post by Inodoro Pereyra on 2011-09-22
> **Krytarik said:**
>  To what filter lists are you subscribed?


Just Easylist in English. It'd always worked perfect;y for me.
Either way, I don't mind having ABP disabled on Facebook. So far, I haven't had any problems with unwanted ads from it. I'm just glad I didn't have to disable it on my other tabs...:)

---

