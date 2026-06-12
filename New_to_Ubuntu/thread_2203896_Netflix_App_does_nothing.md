---
title: "Netflix App does nothing"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by dylan9 on 2014-02-05
So I am trying to get the netflix app working. Here are the commands I ran:

```
sudo apt-add-repository ppa:ehoover/compholio
sudo apt-get update
sudo apt-get install netflix-desktop
```

It seems to install fine. But when I open the dash and click it; nothing happens. The computer just sits there. Any ideas?

---

### Post by bc.haynes on 2014-02-05
Please see [[color=blue]this[/color]](http://ubuntuforums.org/showthread.php?t=2197031) Thread.

---

### Post by monkeybrain20122 on 2014-02-05
Never used the netflix app, but pipelight definitely works (by same developers) and I suppose it is easier on the system because instead of running a full blown Windows Firefox in wine you are just running the silverlight plugin, it also feels a lot more natural.[ http://fds-team.de/cms/pipelight-installation.html]("http://fds-team.de/cms/pipelight-installation.html") Close all your browsers when you install (and when you get an upgrade)

You need also install a user agent switcher in Firefox as Netflix would not work on Linux.[https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/) Set it to Firefox 24/Windows would work for netflix.

---

### Post by protoss96 on 2014-02-06
If your country is not supported yet, then make sure you have downloaded mediahint addon for firefox.

---

