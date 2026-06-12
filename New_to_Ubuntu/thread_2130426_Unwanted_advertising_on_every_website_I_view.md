---
title: "Unwanted advertising on every website I view"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by msgreig on 2013-03-29
Hello,

Recently I think I have been invaded by advertising hacks. I use the current Ubuntu OP and enjoy the no frills aproach. But every web site I open takes longer to open and it puts a massive amount of crap all over my screen. Even web sites you would expect to have zero advertising such as the BBC are literered with it.

I have know doubt I brought this on myself, but surly there is a way to get rid of it and prevent it from happening again.

So any help would be most appriciated.

Thank you Martin

---

### Post by cmcanulty on 2013-03-29
if you use firefox try adblockplus add on

---

### Post by msgreig on 2013-03-29
Thank you! That seems to have worked a treat. Still a bit slow but it will do. Thank you again.

---

### Post by fantab on 2013-03-29
First of all clear all your Browser History and cookies. Restart your Browser.

If you are using either Chromium or Firefox, install some privacy/security addons like, adblockplus, adblockplus popup blocker(FF), Ghostery, BetterPrivacy(FF). NoScript is an excellent addon to have if you can handle it.
Last, but not least, install "[https everwhere]("https://www.eff.org/https-everywhere")".

If using Firefox: [Read]("http://www.insanitybit.com/2012/06/02/the-definitive-guide-for-securing-firefox/").
If using Chromium/Chrome: [Read]("http://www.insanitybit.com/2012/06/02/the-definitive-guide-for-securing-chrome/").

---

### Post by The Cog on 2013-03-29
You could always try deleting all your firefox settings and starting from scratch, if you can bear to lose your bookmarks. This command (while firefox is not running) will rename the settings folder so that you can put it back again if you want:
```
mv ~/.mozilla/firefox ~/.mozilla/firefox-old
```
and this will rename it back again if you want:
```
rm -rf ~/.mozilla/firefox
mv ~/.mozilla/firefox-old ~/.mozilla/firefox
```

---

