---
title: "Can't open links in Firefox from Thunderbird (Xubuntu with XFCE DE)"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by mlnease on 2014-06-12
"Thunderbird 24.5.0" "Firefox 30.0" aka "Mozilla Firefox for Ubuntu canonical - 1.0"

Hello,

Though both function fine otherwise, I'm unable to open links in Firefox from Thunderbird (i.e. hyperlinks in emails).

This may be exclusively a Mozilla problem, but I've searched and found it's been a problem for many Ubuntu users over the years.  The past solutions I've found don't appear pertinent now because of changes in Thunderbird and Firefox (corrections welcome).

As these are the newest versions of these applications, I'm curious as to whether other (x)ubuntu users are having the same problem.  

Thanks in advance for any advice.

I should add that I've completely uninstalled and reinstalled both applications several times, to no avail.

---

### Post by ajgreeny on 2014-06-12
Have you set both FF and TB as your default programs in Xubuntu's Settings-Manager ->Preferred Applications?

That ought to do it.

---

### Post by mlnease on 2014-06-12
> **ajgreeny said:**
> Have you set both FF and TB as your default programs in Xubuntu's Settings-Manager ->Preferred Applications?

That ought to do it.

Thanks, yes I have (I should've mentioned it)--no luck.

---

### Post by kc1di on 2014-06-12
[here's a page]("http://kb.mozillazine.org/Changing_the_web_browser_invoked_by_Thunderbird") that may be of help.
you'll have to modify the config file to make sure it points to FF. 
Good Luck

---

### Post by mlnease on 2014-06-12
Thanks for this, Dave--I've been querying Mozilla for solutions too, without much luck so far.  prefs.js looks promising but there's a lot of room for disatrous error there to my taste and TB is definitely already pointing to FF already anyway, so I think that's a dead end.  I've spent so much time on this at this point that I have a last minute backup in progress and think I'll just reinstall xubuntu and start from scratch, as this is a function I rely on for very frequent use and I'm pretty well habituated to TB/FF.

Thanks again for your reply.

mike

---

### Post by amanchesterman on 2014-06-13
"I'm curious as to whether other (x)ubuntu users are having the same problem."

I'm not. I have the same versions of FF and TBird as you, and when I click on links in emails the pages open in FF instantly. So there's probably something wrong with your settings, not the programs themselves.

If you do decide to re-install, remember to delete the hidden settings folders for these programs in your /home directory, otherwise the new installations will inherit the old settings and your problems may well persist.

Good luck
John

---

### Post by robin7 on 2014-06-13
I had it way back on Xubuntu 10.04 (was that Lucid?  I forget), and my solution was to use Seamonkey instead - another Mozilla product with fully integrated e-mail and browser, with an interface very much like the old Netscape suite. 

It hasn't been an issue with 12.04, which was my next (and current) version of Xubuntu.

---

### Post by pretty_whistle on 2014-06-13
I have ubuntu 14.04 with Xfce desktop and I have the same problem.  I cant imagine what the fix is but I just right click links and choose "copy link location" and then paste it in the browser.

So it's not just you.........

---

### Post by amanchesterman on 2014-06-13
To clarify: I have Xubuntu 14.04 with default settings, downloaded from the Xubuntu official website. I **don't** have 'ubuntu 14.04 with Xfce desktop' like pretty_whistle does. Might the difference be important? In other words, might the Xubuntu distro be set up so that FF and TBird work together, whereas installing Ubuntu and then the XFCE desktop on top of it misses some crucial configuration? Just a thought ...

---

### Post by slickymaster on 2014-06-13
> **amanchesterman said:**
> "I'm curious as to whether other (x)ubuntu users are having the same problem."

I'm not. I have the same versions of FF and TBird as you, and when I click on links in emails the pages open in FF instantly. So there's probably something wrong with your settings, not the programs themselves.

If you do decide to re-install, remember to delete the hidden settings folders for these programs in your /home directory, otherwise the new installations will inherit the old settings and your problems may well persist.

Good luck
John

+1

I have a couple of tests boxes, one with Xubuntu Trusty and another with Xubuntu Utopic and so far haven't faced that issue.

---

### Post by mlnease on 2014-06-13
> **amanchesterman said:**
> "I'm curious as to whether other (x)ubuntu users are having the same problem."

I'm not. I have the same versions of FF and TBird as you, and when I click on links in emails the pages open in FF instantly. So there's probably something wrong with your settings, not the programs themselves.

If you do decide to re-install, remember to delete the hidden settings folders for these programs in your /home directory, otherwise the new installations will inherit the old settings and your problems may well persist.

Good luck
John

Hi John,

Sound advice!  After reinstalling, I made the mistake of restoring 'Home'--and, of course, got the same bugs back.  Reinstalled *again*, restored a bit more judiciously and now all's well.  

For anyone else with this problem, I had some advice from another thread [here]("http://ubuntuforums.org/newreply.php?do=newreply&p=13048605") that might help.  Thanks, all, for your time and attention.

---

