---
title: "root terminal"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by unibroker on 2012-05-01
I am running Ubuntu 12.04 in dual boot with Win XP.  Other than the known issue with the infrequent mouse/keyboard freeze-up my experience with Precise has been good.

This morning when my computer finished booting up Precise I called up a terminal and was greeted with a red border and above it "root terminal".  I had not done anything out of the ordinary in logging on (didn't logon as root).  I entered "exit" but when I called it back up it was still root terminal.  Any idea as to what I inadvertently did?

I ultimately rebooted and got the regular terminal.

---

### Post by ubume2 on 2012-05-01
My guess: 12.04 is still buggy.  My minimize,maximize,close buttons disappeared for a while today.  Hopefully, all these problems won't happen again as Precise gets new updates.

---

### Post by unibroker on 2012-05-02
> **ubume2 said:**
> My guess: 12.04 is still buggy.  My minimize,maximize,close buttons disappeared for a while today.  Hopefully, all these problems won't happen again as Precise gets new updates.

I believe you are correct although this just started happening within the last week.  Now it's on every boot up (I shutdown every night) and I have to log out and then log back in to get the regular terminal.  

I'm relatively new to Ubuntu having come over from Windows to 11.10 at the end of last year.  It took me awhile to get used to sudo as I always logged in as Administrator in XP.  Pretty late in the testing process to have this major a "bug" if that's what it is.

---

### Post by Dngrsone on 2012-05-02
> **ubume2 said:**
> My guess: 12.04 is still buggy.  My minimize,maximize,close buttons disappeared for a while today.  Hopefully, all these problems won't happen again as Precise gets new updates.

Did you happen to be using wine at the time?  there seems to be an issue there...

---

### Post by unibroker on 2012-05-02
> **Dngrsone said:**
> Did you happen to be using wine at the time?  there seems to be an issue there...

FWIW, I uninstalled Wine months ago.

---

### Post by oboedad55 on 2012-05-02
> **unibroker said:**
> I am running Ubuntu 12.04 in dual boot with Win XP.  Other than the known issue with the infrequent mouse/keyboard freeze-up my experience with Precise has been good.

This morning when my computer finished booting up Precise I called up a terminal and was greeted with a red border and above it "root terminal".  I had not done anything out of the ordinary in logging on (didn't logon as root).  I entered "exit" but when I called it back up it was still root terminal.  Any idea as to what I inadvertently did?

I ultimately rebooted and got the regular terminal.

Do you have the root account enabled?

---

### Post by unibroker on 2012-05-02
> **oboedad55 said:**
> Do you have the root account enabled?

I believe by default it is not enabled.  I have not changed my settings (at least knowingly).  I figure it is a bug because when I log out and then log back in the same way I do not get the root terminal.

---

### Post by ubume2 on 2012-05-02
> **Dngrsone said:**
> Did you happen to be using wine at the time?  there seems to be an issue there...


That is very likely that I was using wine at the time. Though I haven't had the problem in a couple of days.

Sorry, unibroker, I didn't mean to hijack your thread.

---

### Post by unibroker on 2012-05-02
> **ubume2 said:**
> That is very likely that I was using wine at the time. Though I haven't had the problem in a couple of days.

Sorry, unibroker, I didn't mean to hijack your thread.

No worries.  It's not like I can't escape from this root terminal issue.  Besides I learn from every post I read.

---

### Post by unibroker on 2012-05-02
> **ubume2 said:**
> That is very likely that I was using wine at the time. Though I haven't had the problem in a couple of days.

Sorry, unibroker, I didn't mean to hijack your thread.

No worries.  It's not like I can't escape from this root terminal issue.  Besides I learn from every post I read.

---

### Post by Dngrsone on 2012-05-03
> **ubume2 said:**
> That is very likely that I was using wine at the time. Though I haven't had the problem in a couple of days.

Sorry, unibroker, I didn't mean to hijack your thread.

A more appropriate place to continue this conversation is either [here](http://ubuntuforums.org/showthread.php?t=1970697) or [here](http://ubuntuforums.org/showthread.php?t=1969298).

---

### Post by unibroker on 2012-05-04
> **ubume2 said:**
> That is very likely that I was using wine at the time. Though I haven't had the problem in a couple of days.

Sorry, unibroker, I didn't mean to hijack your thread.

Update:  Not being too observant in the past, I did notice upon calling up the terminal this morning that while the heading did say "Root Terminal" it had a "$" instead of "#" for the cursor.  I then inputted a command that required root privileges and the terminal gave me an error ("requires root").

---

### Post by unibroker on 2012-06-06
> **unibroker said:**
> I am running Ubuntu 12.04 in dual boot with Win XP.  Other than the known issue with the infrequent mouse/keyboard freeze-up my experience with Precise has been good.

This morning when my computer finished booting up Precise I called up a terminal and was greeted with a red border and above it "root terminal".  I had not done anything out of the ordinary in logging on (didn't logon as root).  I entered "exit" but when I called it back up it was still root terminal.  Any idea as to what I inadvertently did?

I ultimately rebooted and got the regular terminal.
I am resurrecting this thread because I am still experiencing this every time I start up.  As has been said even though the terminal says "Root Terminal" it is not according to the $ prompt.  The reason the terminal that initially comes up is a problem is that it doesn't contain my command history nor my preferences including  a transparent background so I can simultaneously be typing in the terminal and see the Ubuntuforums code recommendations through it.  TIA

---

### Post by forrestcupp on 2012-06-06
First of all, how are you opening your terminal?

Also, assuming you're using Gnome Terminal, have you checked your profiles to see if somehow a profile other than Default was created? When you're having the problem, go to Edit->Profiles... and see if there is anything other than Default. You can also set which profile is used when the terminal is launched. In there, you can edit your profile settings. In the Background tab, you can set it to have a transparent background.

Just a few things to check out.

---

### Post by unibroker on 2012-06-06
> **forrestcupp said:**
> First of all, how are you opening your terminal?

Also, assuming you're using Gnome Terminal, have you checked your profiles to see if somehow a profile other than Default was created? When you're having the problem, go to Edit->Profiles... and see if there is anything other than Default. You can also set which profile is used when the terminal is launched. In there, you can edit your profile settings. In the Background tab, you can set it to have a transparent background.

Just a few things to check out.
I always use Ctrl + Alt + T.  This a home computer so my login name and password is the same on initial boot up as well as logout and back in to get my preferred terminal.

Edit: I shutdown and re-booted to get the "root terminal".  Even on window maximized there is no Edit function.  There is only close, minmize, maximize so I couldn't see if there is another profile besides Default.  When I logout and then back in I get my preferred terminal with the Edit->Profiles....

---

