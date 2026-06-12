---
title: "few issues"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by rsratner on 2012-01-16
Right now I am using a Wubi installation inside of Vista. One thing I do in Vista on a daily basis is remote desktop - I control my Windows XP computer remotely. Can I control that computer with Ubuntu?

I also use Sibelius 6, a music notation and playback program. From what I have read on the web, it will not run under Wine. Is there any other way to do it?

---

### Post by cavh on 2012-01-16
I can help with the first question. The answer is yes - use Terminal Server Client.

In a terminal window, type this command (or just copy-paste it) and enter your logon password when prompted (the characters you type for your password will not be shown on screen for security reasons, nor will you see any asterisks appear as you type, but rest assured the keyboard input is being captured):

```
sudo apt-get install tsclient
```

---

### Post by Double.J on 2012-01-16
Hi there, I just checked on WineHQ for you and Sibelius 6 has a rating of Garbage as I'm sure you saw - meaning pretty much a no go! I'f you own previous versions, 5 had a gold rating.. so may be possible there, But unfortunately it looks as though 6 may just be a no go for now.

I had a look into open source alternatives and came across [musescore]("http://musescore.org/en/download") If you were interested?

---

### Post by skompier on 2012-01-16
> **rsratner said:**
> 
I also use Sibelius 6, a music notation and playback program. From what I have read on the web, it will not run under Wine. Is there any other way to do it?

You could try running it under Virtual Box. From a Google search, it seems that what most people do. There's also MuseScore, which may have what you need and there's a Linux version.

[http://musescore.org/](http://musescore.org/)

---

### Post by rsratner on 2012-01-16
> **gnu/mirow said:**
> Hi there, I just checked on WineHQ for you and Sibelius 6 has a rating of Garbage as I'm sure you saw - meaning pretty much a no go! I'f you own previous versions, 5 had a gold rating.. so may be possible there, But unfortunately it looks as though 6 may just be a no go for now.

I had a look into open source alternatives and came across [musescore]("http://musescore.org/en/download") If you were interested?

Thank you for your suggestion. Unfortunately, it is important that I continue working with Sibelius for a variety of reasons. I suppose I'll just have to retain my Windows until this issue is solved. I must say it's kind of funny to rate Sibelius "Garbage" just because it doesn't happen to work with Wine - kind of like rating a person "Garbage" because he doesn't happen to speak one's language.

---

### Post by mastablasta on 2012-01-16
> **rsratner said:**
> Thank you for your suggestion. Unfortunately, it is important that I continue working with Sibelius for a variety of reasons. I suppose I'll just have to retain my Windows until this issue is solved. I must say it's kind of funny to rate Sibelius "Garbage" just because it doesn't happen to work with Wine - kind of like rating a person "Garbage" because he doesn't happen to speak one's language.


rating garbage is not for the application. 

it's a rating for how well it runs under wine. there are plenty excellent programmes/games that have this rating.

> **Garbage **
  An application gets this rating if it cannot be used for the purpose it was designed for. There should be at least one bug report in Bugzilla if it gets this rating. Application cannot be installed, does not start, or starts but has so many errors that it is nearly impossible to use it. 
more here: [http://appdb.winehq.org/help/?sTopic=maintainer_ratings](http://appdb.winehq.org/help/?sTopic=maintainer_ratings)

---

### Post by Mark Phelps on 2012-01-16
> **rsratner said:**
> ...kind of like rating a person "Garbage" because he doesn't happen to speak one's language.

Actually ... if you hired that person to be your interpreter (for a foreign language) and then learned that they did not speak YOUR language -- you probably WOULD rate them garbage.  Because, they couldn't serve their intended purpose.

Which is the same situation with Wine ratings.  Regardless of how well the apps works in MS Windows, if it won't install, or you can't even get basic functionality out of it, using Wine, it gets a Garbage rating.  This prevents folks from wasting lots of their time and effort trying to get it to work.

---

