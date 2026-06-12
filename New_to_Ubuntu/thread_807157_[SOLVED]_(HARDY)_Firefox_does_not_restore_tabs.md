---
title: "[SOLVED] (HARDY) Firefox does not restore tabs"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by BassKozz on 2008-05-25
I just upgraded from feisty to Hardy and I used to use [TabsMixPlus]("https://addons.mozilla.org/en-US/firefox/addon/1122") for FF2 in order to save&restore tab sessions... but because TabsMixPlus isn't available for FF 3.0 (yet), I am stuck with using Firefox's built-in sessions manager (which is junk IMO), but the built-in sessions manager doesn't restore my sessions even thou I have "Preferences->Main->Startup->When Firefox Starts = Show my windows and tabs from last time" Set it doesn't restore the tabs :confused:

---

### Post by macness on 2008-05-25
I would start by creating a new profile in FF to see if it does the same thing.  You can do that by typing:

```
firefox -ProfileManager
```

in a terminal. This does not effect your current profile, but if it works (after setting the preference) then I'd just move your content from your old profile to the new one.  More info on how to do that [here]("http://support.mozilla.com/zh-CN/kb/Backing+up+your+information")

Hope this helps.

---

### Post by BassKozz on 2008-05-25
> **macness said:**
> I would start by creating a new profile in FF to see if it does the same thing.  You can do that by typing:

```
firefox -ProfileManager
```

in a terminal. This does not effect your current profile, but if it works (after setting the preference) then I'd just move your content from your old profile to the new one.  More info on how to do that [here]("http://support.mozilla.com/zh-CN/kb/Backing+up+your+information")

Hope this helps.
Nope, no go, that didn't fix the problem :(

---

### Post by Chr0mis on 2008-05-25
Go to about:config and type in "session"
Make sure the values are as followed: 
    *  browser.sessionstore.enabled (bool) - Activate the service. Default is true.
    * browser.sessionstore.resume_from_crash (bool) - Resume sessions post-crash. Default is true.
    * browser.sessionstore.resume_session_once (bool) - Resume session at the next application start, but not again. Default is false. This is used for restarting the browser after application updates and extension installation.
    * browser.startup.page (int) - What is displayed when Firefox starts: 0 = blank page; 1 = homepage; 3 = previous session. Default is 1. (Note: This preference is exposed in the Startup section of the Main pane of the Options/Preferences dialog.)

---

### Post by BassKozz on 2008-05-25
> **Chr0mis said:**
> Go to about:config and type in "session"
Make sure the values are as followed: 
    *  browser.sessionstore.enabled (bool) - Activate the service. Default is true.
    * browser.sessionstore.resume_session_once (bool) - Resume session at the next application start, but not again. Default is false. This is used for restarting the browser after application updates and extension installation.
That did the trick...
**browser.sessionstore.enabled** was set to false
and
**browser.sessionstore.resume_session_once** was also set to false so I switched it to true

Thanks Chr0mis !!! :D

---

### Post by c0mp13371331337 on 2008-05-31
I've tried both of these methods and unfortunately neither are working for me.  I, too, am having the same problem with the sessionsaver.  Although by creating a new profile, SessionStore will restore my previous session, but once I overwrite the contents of the new profile with the old profile, I lose SessionSaver again.  It's no doubt just a single or handful of files that are causing this, can anyone narrow this down so I don't have to copy, paste, and test one file at a time?

If it's any help, the Error Console shows the following on firefox start-up:

> SessionStore: The session file is invalid: TypeError: this._initialState.windows[0] is undefined

Thanks in advance!

---

### Post by c0mp13371331337 on 2008-06-10
Actually, I've discovered something interesting.  Using Quit from the menu, or Ctrl+Q, then opening firefox again, it will restore the tabs no problem.  However, using the Close Button (X) provided by the window manager, it will not restore the session next time I fire it up.

---

### Post by BassKozz on 2008-06-11
> **c0mp13371331337 said:**
> Actually, I've discovered something interesting.  Using Quit from the menu, or Ctrl+Q, then opening firefox again, it will restore the tabs no problem.  However, using the Close Button (X) provided by the window manager, it will not restore the session next time I fire it up.

Interesting, hopefully this will be fixed upon the final release.

---

### Post by kaibob on 2008-06-11
> **c0mp13371331337 said:**
> ...Although by creating a new profile, SessionStore will restore my previous session, but once I overwrite the contents of the new profile with the old profile, I lose SessionSaver again.  It's no doubt just a single or handful of files that are causing this, can anyone narrow this down so I don't have to copy, paste, and test one file at a time?...

Perhaps you have a corrupted or multiple sessionstore.js files in your profile directory. It's easy to backup then delete this file to see if that helps.

[http://support.mozilla.com/en-US/kb/Firefox+hangs](http://support.mozilla.com/en-US/kb/Firefox+hangs)

---

### Post by macness on 2008-06-11
> **c0mp13371331337 said:**
> Actually, I've discovered something interesting.  Using Quit from the menu, or Ctrl+Q, then opening firefox again, it will restore the tabs no problem.  However, using the Close Button (X) provided by the window manager, it will not restore the session next time I fire it up.

Holy $#@! This worked!  I been STRUGGLING with this for a bit... this is a GOOD *temporary* fix.

*clicks the thanks icon*

---

### Post by BassKozz on 2008-06-11
> **macness said:**
> *clicks the thanks icon*
I think someone forgot

---

### Post by macness on 2008-06-12
> **BassKozz said:**
> I think someone forgot

No I didn't :)

---

### Post by BassKozz on 2008-06-13
> **macness said:**
> No I didn't :)

Your right, sorry I was reading the post above, and you quoted the post before that.
I stand corrected #-o

---

### Post by eric1959 on 2009-01-25
Just found out that if you checked one of the two boxes at Edit > Preferences >Privacy > Private Data, you should look at "Settings".  At "History" uncheck the box "Visited Pages".

---

### Post by technologik on 2009-03-13
> **eric1959 said:**
> Just found out that if you checked one of the two boxes at Edit > Preferences >Privacy > Private Data, you should look at "Settings".  At "History" uncheck the box "Visited Pages".

This did it, I can't believe that I looked at every possible setting.  Yet I never tried the simple ones.  I feel like such a fool. :redface:

---

### Post by Ms_Angel_D on 2009-03-13
> **BassKozz said:**
> because TabsMixPlus isn't available for FF 3.0 (yet)

Actually there is a version available for 3.0 I have been using it for quite some time now it's available in the Tab Mix Plus Forums [http://tmp.garyr.net/forum/viewtopic.php?t=9864](http://tmp.garyr.net/forum/viewtopic.php?t=9864)

I know it's a developer build but I haven't had any problems with it what so ever it runs perfectly on Both computers.

---

