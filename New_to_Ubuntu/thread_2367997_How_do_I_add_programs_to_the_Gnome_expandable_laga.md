---
title: "How do I add programs to the Gnome expandable lagacy icon bar?? screen shot provided"
date: 2017-08-05
forum: New to Ubuntu
---

### Post by aconcept on 2017-08-05
Hi Community, 

 I just installed Ubuntu-Gnome 16.04 and absolutely love it. I am was able to get an application into the expandable legacy icon bar and then I was able to use the right click feature from the app icon but upon reboot the application isn't attached to that bar anymore. My question is how can I put apps into this tray??  I'm not even sure what it's called but this link talks about it and even has an image of the tray found in the bottom left of the desktop and can be extended or hidden. None the less I am unable to use a clipboard function if I cannot right click this app from the tray. I can't find anything covering this anywhere.

[https://superuser.com/questions/941940/move-disable-legacy-icon-bar-from-bottom-left-in-gnome-3-16](https://superuser.com/questions/941940/move-disable-legacy-icon-bar-from-bottom-left-in-gnome-3-16)

Can someone please advise how to accomplish this?

[IMG]https://i.stack.imgur.com/vGxQB.png[/IMG]


This is the system tray / app tray / expandable legacy icon bar or something that I am talking about.

---

### Post by again? on 2017-08-06
The indicator icon of an app only shows when an app is running.
May need to add your application to startup applications.

You can't easily add icons to the legacy tray yourself... the application has to use indicators.
In regards to a clipboard manager you can use [Clipboard Indicator]("https://extensions.gnome.org/extension/779/clipboard-indicator/") extension.
(The 3 panel icons on the left are extensions and are always positioned in the top panel)
[ATTACH=CONFIG]276272[/ATTACH]

You can also use any clipboard manager that supports indicators.
eg I prefer glipper, because when shown in the menu dropdown it removes the middle section of what was copied.
(The 4 coloured icons are shown by the legacy tray, moved to the top panel by the [Topicons Plus]("https://extensions.gnome.org/extension/1031/topicons/") extension.
[ATTACH=CONFIG]276273[/ATTACH]

[How to Install GNOME Shell Extensions with Firefox & Chrome]("http://www.omgubuntu.co.uk/2017/01/install-gnome-shell-extensions-firefox-chrome")

---

