---
title: "dash does not show ANY applications"
date: 2013-02-02
forum: New to Ubuntu
---

### Post by Marcin Witold Piotrowicz on 2013-02-02
Dash shows downloads, recent files, folders, music and video. 
It does not however show any applications (neither filters for them).
Neither in home lens nor in application lens.

I am using ubuntu 12.04, which I istalled on lean disk about one month ago. I can not recall any change to system, that I would have done yesterday. Yesterday dash was working perfectly.

Any help, please?
Marcin

no problem anymore - for whatever reason - want to delete thread - do not know how to do it

---

### Post by Reno II on 2013-02-25
Yeah, I have the same problem now. I installed some new updates and no applications anymore. Any idea how to solve this? Any idea how to access the applications without the home search?

---

### Post by grahammechanical on 2013-02-25
@Reno II

Are you saying that the Dash does not appear when you click the Dash Home icon or when you tap the Super key?

Or you saying that the Dash fails to find applications when you type an application name in the Dash search panel?

Have you tried ALT+F2? That brings up a Run Command panel. Type the name of the application in there and press Enter and the application should run.

This may rectify itself. The Dash search engine may need to update its database after the update.

Regards.

---

### Post by bthomson100 on 2013-02-27
I just upgraded from Ubuntu 10 to 12.04.1. In Ubuntu 10 there was a nice menu with one click access to installed applications on the top of the screen. Now that's gone, and since I haven't a clue what their names on the hard drive might be, I can't just type their names and expect them to run. Surely there is some kind of menu application that will make it easier to find applications if the developers of 12.04.1 were too thoughtless to make it index installed applications and display them somewhere for newbies. They also gratuitously forced my Thunderbird to install an extension called EDS Contacts which loaded a corrupted address book into my existing address books and froze Thunderbird. It took me two days to be able to send emails because of this imperfect process of "upgrading".  :confused:

---

### Post by siddharth007 on 2013-02-28
Posted mistakenly.Unable to delete

---

### Post by napzilla on 2013-07-10
Here's a summary of the suggestions I found, followed by the one that worked for me. I was having the same problem on my computer, and Alt + F2 also did not work. I tried the following solutions, none of which worked:
[LIST]
[*]Restart
[*]rm -rf ~/.local/share/zeitgeist
[*]Reinstall unity-place-applications and unity-place-files
[*]rm ~/.local/share/zeitgeist/activity.sqlite
[/LIST]

However, running the following in a terminal did finally cause applications to appear (use Ctrl + Alt + t if you don't have a terminal pinned to your launchbar):
```
unity --replace &
```

I found this solution on Ask Ubuntu: [http://askubuntu.com/questions/125843/dash-search-gives-no-result](http://askubuntu.com/questions/125843/dash-search-gives-no-result)

---

