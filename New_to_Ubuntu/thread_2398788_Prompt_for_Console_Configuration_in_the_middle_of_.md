---
title: "Prompt for Console Configuration in the middle of an update"
date: 2018-08-17
forum: New to Ubuntu
---

### Post by xuomek on 2018-08-17
I was just installing some updates with updates with Software Updater and then the update just stopped. A prompt, which had the title 'Console Configuration', showed up and asked me to select what kind of Encoding I would like. I have no idea what caused this or what this is. I just picked UTF-8 and then the update resumed.

Any ideas what this is or what caused this? I could see on some Ubuntu Documentation that it had something to do with Locales and I sometimes get errors like Locale not found and such, Could that be it? I'm only curious about this because it just randomly showed up in the middle of an update.

---

### Post by TheFu on 2018-08-17
Welcome to the forums.

Yes. That is correct.

It wasn't random. Something got updated related to a locale configuration.  You could have kept the old settings, accepted the package maintainer's updates or used a merge to see both together.

If you want different languages or different keyboards or different displays based on the commonly used formatting in a specific province/country, the locale is part of that. Like which money symbol or showing dates with mm-dd-yyyy or dd-mm-yyyy or yyyy-mm-dd. Each is available as a locale setting.  Each userid and the system as a whole has control over their locale.

The console and the GUI  (X/Windows) have different controls for locale as well.

Flexibility.  That is a great thing and terrible thing for Unix-like OSes.

---

### Post by xuomek on 2018-08-21
Thank you for replying. You're explanation clears things up. I'm just trying to make sure nothing weird is going on with my Ubuntu OS.

---

### Post by TheFu on 2018-08-21
> **xuomek said:**
> Thank you for replying. You're explanation clears things up. I'm just trying to make sure nothing weird is going on with my Ubuntu OS.

Some packages contain all the updates for the entire world, so if any govt anywhere changes something, we all get an updated package.   The timezone and locale packages see updates all the time.  If a country changes their currency, at least 1 locale will get updates, for example and maybe all Unicode character sets are impacted too.  Hard to say.

If a screen pops up 5 hrs after you booted and ask you to approve something you didn't ask for, then there is an issue. If you are in the middle of doing system updates (and I think everyone should perform those manually), then being asked to confirm some settings isn't really unexpected.

---

### Post by xuomek on 2018-08-21
Ah, I see. I get it. I also think the fact that the terminal says 'No Locale Settings Found' while installing updates may have had something to do with it. However, that has been there since the beginning and I don't think it's an issue. I'm just trying to make sure that my OS is as secure as possible and the fact that I just switched to Ubuntu doesn't make that easy because I'm constantly questioning everything. It's probably me just being paranoid, like checking whether any of the update packages have been compromised and such( I know this is stupid). I think I've locked my system up pretty good now and everything seems to be fine. Thank you once again for clearing that up.

---

### Post by TheFu on 2018-08-21
My signature has lots of security links. Start with the "Basic Ubuntu Security" one, if you haven't already. Nothing is more important for security than a smart user, paying attention.

If you want to worry less, stay away from the GUI and learn to use the shell for most things. Shell/CLI-based programs are much easier to secure for programmers because automatic testing is much better than testing for a GUI and there are millions of lines of code less than used in even the simplest GUI. GUIs often hide important details too and are usually written by different people than who wrote the CLI version.  Often support a GUI will only 20% (or less) of the capabilities in an attempt to simplify.

To save time learning, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good step-by-step introduction that builds on the simple ideas of Unix.

---

