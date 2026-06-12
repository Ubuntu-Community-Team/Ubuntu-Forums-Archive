---
title: "Automating web tasks"
date: 2011-07-30
forum: Programming Talk
---

### Post by r.darwish on 2011-07-30
I wish to find a library for controlling a web browser (preferably Firefox) in Ubuntu. There is a very good library for Windows, which is written in C# and allows controlling Firefox or IE. It is called WatiN: [http://watin.org/](http://watin.org/)
I am looking for a similar library, preferably in Mono (but I can work with python too) that offers the same features for Firefox in Ubuntu.

---

### Post by soltanis on 2011-07-30
I don't know of a similar library, but consider what exactly you are trying to do. You can automate HTTP requests to certain URLs, for example, by using the library [curl]("http://curl.haxx.se/") for C, [wget]("http://www.gnu.org/s/wget/") on the command line (curl is also a program for that), [httplib]("http://docs.python.org/library/httplib.html") in Python, [LWP::UserAgent]("http://search.cpan.org/~gaas/libwww-perl-6.02/lib/LWP/UserAgent.pm") for Perl, and many others.

Since all web functionality exists through the HTTP dialogues between your browser and the web server, you should generally be able to emulate that functionality by examining the HTML of the web page to see what it's telling your browser to do. Provided that it isn't obscured by an obnoxious layer of Javascript, you can probably accomplish the same end goal as you can with controlling the mouse clicks and key presses of your browser.

---

### Post by r.darwish on 2011-07-31
Well, you're right, but as you guessed I'm talking about sites "obscured by an obnoxious layer of Javascript". Unless there's some sort of Javascript engine library for Python/C# I think the more simple (and slower) approach is to actually control the web browser.

---

### Post by LemursDontExist on 2011-07-31
If you need support for javascript, you might look at [Selenium]("http://seleniumhq.org/").

---

### Post by soltanis on 2011-07-31
Understandable. This goes back to what you are trying to do again. Since only web browsers have the whole DOM and friends if there is Javascript fogging then depending on what you're doing, you're out of luck.

So what is it you are trying to do? Since you mention Javascript, are you trying to automate the submission of some data, or are you trying to pull resources from a site, or do you need to go through some kind of login process and then pull some resources (like I dunno, get your Google Calendar or something)?

Depending on the site they might have a compatibility mode for older browsers, and that would be the most helpful path.

---

### Post by r.darwish on 2011-07-31
> **LemursDontExist said:**
> If you need support for javascript, you might look at [Selenium]("http://seleniumhq.org/").
Seems like the thing I was looking for. Thank you! :)

---

