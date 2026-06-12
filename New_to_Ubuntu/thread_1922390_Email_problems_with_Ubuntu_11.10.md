---
title: "Email problems with Ubuntu 11.10"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by grovenor on 2012-02-08
I have been searching on here but not found anything that covers my problem.
I have recently upgraded from 10.4 through 10.10, 11.4 to 11.10 with a few days between each step.
The first 2 of these went perfectly, 11.4 told me that for some reason it could not install unity and I would have the classic screen, which was just fine.
The last upgrade to 11.10 did install unity, which looks like a learning curve I could have done without, but i can probably get used to it. However worse than that I have lost my email. (the mail is backed up, just it doesn't work anymore).
From other posts on here I have learn't that support has been moved from Evolution to Thunderbird but that i should be able to re-install Evolution.  Oddly Evolution does appear in the menus but does not open and the Software Centre says it is not installed, nenc I can't uninstall it. Trying to install it I get a message that there are unspecified conflicts and it can't be installed, the "details" button does not give any details.
So Ok I try Thunderbird which does at least open and after a bit of configuring reports that it has connected and apparently downloaded my email. However, there is no sign of any inbox and the "Read mail" button does not do anything. 
Consequently i am having to read my email via webmail which is irritatingly slow and I dislike it.
Any advice on how I can get Evolution working again would be much appreciated, or failing that how can i read my mail with Thunderbird?
At the moment I am feeling like reverting back to 10.4 which never gave me any trouble.
Thanks in anticipation
Keith

---

### Post by kc1di on 2012-02-08
hi grovenor, 

How did you try to install evolution?
I have it installed in 11.10 with no problems works fine.

Installed it via terminal with sudo apt-get install evolution.

---

### Post by Bartender on 2012-02-08
A lot of folks (well, me anyway) stay away from upgrading.  You'll get more reliable results by installing anew.  Strange, glitchy behavior like you're describing sure sounds like problems that might have derived from upgrading rather than installing new.

---

### Post by kc1di on 2012-02-09
> **Bartender said:**
> A lot of folks (well, me anyway) stay away from upgrading.  You'll get more reliable results by installing anew.  Strange, glitchy behavior like you're describing sure sounds like problems that might have derived from upgrading rather than installing new.

Agree +1

---

### Post by winh8r on 2012-02-09
i would suggest using the terminal to 

apt-get remove evolution --purge

apt-get remove thunderbird --purge 

and start again with one or the other, this should remove any conflicts, you are at no risk of losing any emails as it is all on your webmail server.


hope this helps you.

---

### Post by grovenor on 2012-02-09
> **kc1di said:**
> hi grovenor, 

How did you try to install evolution?
I have it installed in 11.10 with no problems works fine.

Installed it via terminal with sudo apt-get install evolution.
I tried from the software centre and also from synaptic, same problem with both.
Thanks
Keith

---

### Post by grovenor on 2012-02-09
> **winh8r said:**
> i would suggest using the terminal to 

apt-get remove evolution --purge
apt-get remove thunderbird --purge 
and start again with one or the other, .

That sounds like its worth a try at least. If that doesn't work I suppose I can fall back on a new install.
Thanks
Keith

---

### Post by grovenor on 2012-02-09
> **grovenor said:**
> That sounds like its worth a try at least.
Thanks
Keith

I am really not at all familiar with command lines, trying this the terminal is telling me it doesn't have permission and asking if I am root. All well and good and I know the password but how do I tell it?
Thanks
Keith

---

### Post by grovenor on 2012-02-09
Managed to sort out the terminal password thing from the help and using winh8r's advice I have evolution up and running and can get back to normal.
many thanks
Keith

---

### Post by winh8r on 2012-02-09
Glad it worked for you.

All this clicking stuff is ok, but you cannot beat the power of the terminal!!!

---

