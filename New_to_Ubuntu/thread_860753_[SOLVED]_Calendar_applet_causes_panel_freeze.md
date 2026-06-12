---
title: "[SOLVED] Calendar applet causes panel freeze"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by flyingsolo on 2008-07-15
If I click on the date/time/weather/calendar applet in top right panel, it will not open the calendar and weather information and also causes all buttons on the top & bottom panels to 'freeze' or become inactive.  Even the red shutdown button doesn't work.  CTRL/alt/del also will not shut down system and I have to resort to a hard shutdown.
I found nothing in searching forums about this so hopefully someone can direct me.
Thanks.

---

### Post by flyingsolo on 2008-07-15
I found [this thread]("http://ubuntuforums.org/showthread.php?t=356398") which seems to be similar to my problem but they didn't really find a fix as far as I can tell.

---

### Post by flyingsolo on 2008-07-16
Bump--still looking for someone with similar problems.

---

### Post by iaculallad on 2008-07-16
Try:

```
sudo apt-get install --reinstall gnome-applets
```

---

### Post by MatthewPlanchard on 2008-07-16
I had this problem as well. It had to do with evolution linking up with Google calendars. I had to go to evolution and uncheck any calendars under the 'Google' heading, and that fixed it for me.

Let us know if it works.

---

### Post by flyingsolo on 2008-07-18
Sorry I missed the latest 2 posts above but much thanks to MatthewPlanchard--that seems to have done it for me too!  But how in the world did you figure that out?!  There's just no way I was ever going to sort that out myself.  (I guess that's why this is the 'Absolute Beginner Talk' part of the forums!)
Many thanks but some explanation would be appreciated too.

---

### Post by MatthewPlanchard on 2008-07-19
Hm, glad to hear it worked.
As I recall it took me at least a few days of searching on the forums and elsewhere to figure out what was wrong.  In the future, here's a couple of sites that are usually pretty helpful.
[Ubuntu Search Engines]("http://crunchbang.org/ubuntu-search-engine/")
[Linux oriented Google search]("http://www.google.com/linux")

Thanks for the thanks.
Blessings!

---

### Post by yetiARC on 2008-07-28
> **MatthewPlanchard said:**
> I had this problem as well. It had to do with evolution linking up with Google calendars. I had to go to evolution and uncheck any calendars under the 'Google' heading, and that fixed it for me.


I think I'm having a similar problem. I tried to link up evolution with a Google calendar and during the same session subscribed to an ics calendar on the web.
Now evolution freezes on start up (see attached screenshot). It doesen't even get to the point where it asks the password for the keyring for checking email.

[IMG]http://wundergraben.de/Priv/Bildschirmfoto-4.png[/IMG]

Unfortunately, this makes it impossible to just uncheck any calendars, as suggested.
I have tried to find a config file that could be manually edited, but no success, so far.

Any ideas?

---

### Post by MatthewPlanchard on 2008-07-28
Hello, Yeti,

Go ahead and try out the solution posted [here]("http://markmail.org/message/kftykmfdcsrftvlq#query:evolution%20calendar%20config+page:1+mid:kftykmfdcsrftvlq+state:results").

To summarize, you can fix the problem by going into gconf-editor and going to apps->evolution->calendar and taking out the entry that caused the crash.

Let us know if that fixes things for you.

Blessings.

---

### Post by yetiARC on 2008-07-28
> **MatthewPlanchard said:**
> Hello, Yeti,

Go ahead and try out the solution posted [here]("http://markmail.org/message/kftykmfdcsrftvlq#query:evolution%20calendar%20config+page:1+mid:kftykmfdcsrftvlq+state:results").

To summarize, you can fix the problem by going into gconf-editor and going to apps->evolution->calendar and taking out the entry that caused the crash.


Thanks for the quick reply. I opened the gconf editor and found the evolution/calendar section. Unfortunately, I could not find any entries that contained web sources for the calendar (see attached screenshot)??!??

Can anyone tell me how these entries should show up here?

[IMG]http://www.wundergraben.de/Priv/Bildschirmfoto-5.png[/IMG]

---

### Post by MatthewPlanchard on 2008-07-28
Have you tried uninstalling and reinstalling evolution?

If you don't mind losing all your settings, you can purge all previous config files before the install with the code found [here]("http://ubuntuforums.org/showpost.php?p=4561057&postcount=9").

```
rm -r ~/.evolution/
rm -r ~/.gconf/apps/evolution/
evolution --force-shutdown
killall gconfd-2
```

---

### Post by yetiARC on 2008-07-28
Matthew,
a complete uninstall did not seem very desirable. After having searched dozens of posts in different forums, I finally did what I should have done right away: open a terminal and check the evolution manpages.
After playing around a little bit, I found the following solution to my problem:

evolution --force-shutdown

evolution --offline

This allowed me to start evolution offline and uncheck the google calendar, which solved my problems.

Thanks for your efforts!

---

### Post by MatthewPlanchard on 2008-07-28
Excellent!

---

### Post by martvi on 2008-08-27
This has to do with the following circumstances imo (I do have the following experience)
1. click on de Gnome calendar applet
2. And Evolution is not running
3. And I have not yet a connection to the Google calendar through Evolution.

Is seems that the calendar applet does call a Evolution function somehow (bonobo?), and Evolution waits for the username/password connection with Google calendar for ever, thereby freezing the panel.

I can open the gnome calendar applet if Evolution was started before with a connection to Google calendar. If Evolution is NOT started before, the panel freezes. Evolution does not have to be running at that time.

---

### Post by johnboiles on 2008-10-02
I'm having the same issue as martvi. The applet works fine if I have already opened my calendar in evolution, but if I try to view the calendar applet without having already opened my calendar in evolution, it crashes. If I open evolution calendar, and then close it, the applet works fine from then on out.

I am using gCal. I find it very convenient to have my appointments in this applet.

Another thing I find is strange: after my panels freeze, I do a CTRL-ALT-BACKSPACE to restart x. I re-login, and my panels don't come back. I thought restarting X would surely fix things. I have to do a full reboot.

Any ideas on a real fix to this?

---

### Post by picaciam on 2010-01-30
I had the same issue and solved using the following instructions to include google calendar in evolution
[http://jkeating.livejournal.com/75230.html](http://jkeating.livejournal.com/75230.html)

Shortly, don't rely on the evolution option to directly include a google calendar,
but include the calendar via CalDAV

Hope this helps,
Massimo

---

