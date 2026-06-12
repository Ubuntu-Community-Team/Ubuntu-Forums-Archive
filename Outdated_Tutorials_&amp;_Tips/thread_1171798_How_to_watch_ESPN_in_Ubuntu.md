---
title: "How to watch ESPN in Ubuntu"
date: 2009-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by gasull on 2009-05-27
Short HOWTO about how to watch [ESPN]("http://sports.espn.go.com/broadband/ivp/?ref=splash") on Ubuntu:

[LIST=1]
[*]Install [Wine]("http://www.winehq.org/download/deb").
[*]Install [ies4linux]("http://www.tatanka.com.br/ies4linux/page/Installation") (Internet Explorer for Linux).
[*]Go to [ESPN]("http://sports.espn.go.com/broadband/ivp/?ref=splash") and follow [the link to download the Flash plugin]("http://kb2.adobe.com/cps/406/kb406791.html") *for Windows*.
[*]Install the Flash plugin with Wine.
[*]Backup your .wine directory with: ```
cp -r ~/.wine ~/wine.bak
```
[*]Move ies4linux to the Wine directory, so it can use the Flash plugin: ```
cp -r .ies4linux/ie6/drive_c/* .wine/drive_c/
```
[*]Execute .wine/drive_c/Program\ Files/Internet\ Explorer/iexplore.exe (You probably want to create an entry in your applications menu)
[*]Go to ESPN page with IE6: [http://sports.espn.go.com/broadband/ivp/?ref=splash](http://sports.espn.go.com/broadband/ivp/?ref=splash)
[*]Ignore the popup asking you to install Windows Media Player.
[/LIST]

---

### Post by ikus060 on 2009-06-01
What about using Firefox and Flash Player ? Because I don't have any problem to watch the short clip on the click you provide with this setup.

I'm using Ubuntu Jaunty.

---

### Post by Astinsan on 2009-06-01
I was going to say the same thing... I have NO issues with flash sites. Silverlight maybe... (should be fixed with the mono version that should be around soon) I don't think silverlight will go anywhere all that fast anyhow.

---

