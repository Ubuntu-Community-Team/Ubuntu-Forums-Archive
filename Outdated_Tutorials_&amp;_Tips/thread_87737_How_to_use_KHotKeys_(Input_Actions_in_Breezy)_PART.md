---
title: "How to use KHotKeys (Input Actions in Breezy) PART 1"
date: 2005-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Takis on 2005-11-08
(found in Settings->Regional & Accessibility)

KHotKeys ranks very highly on my list of why KDE is great. It's a really powerful tool that brings together a lot of good features.

Notes
[LIST]
[*]This does not cover how to map keyboard sequences into something that X recognises (for example, how to map a multimedia *browser* button to XF86WWW). You need to use xmodmap to do this, have a look at [this]("http://ubuntuforums.org/showthread.php?t=27039") tutorial.
[*]For some reason, Input Actions crashes frequently without error messages in Breezy, whereas it was quite stable in Hoary. Ah well.
[*]The latest version of KHotKeys even allows you to speak commands to your computer (how cool is this program???). I haven't really messed with this so can't comment on it.
[/LIST]
[B]
Part 1: How to use keys to start programs[/B]
This example maps the XF86WWW key to start Firefox.

[LIST=1]
[*]Open KHotKeys. Click 'New Action'. An action called "New Action" appears. Select it, and rename it to "Start Firefox".
[*]Directly underneath is the Action Type dropdown box. I prefer Generic because it basically lets you do anything you want, and allows for easy customisation in the future, but it's a little bit more complex so for this example we'll use 'Keyboard Shortcut -> Command/URL'.
[*]Click the Keyboard Shortcut tab and hit the button labelled 'None'. A dialog box appears that lets you select your shortcut. Hit the key sequence you'd like to use to open Firefox (e.g. the browser button on your keyboard, or CTRL+ALT+F, assuming you don't have KDE using it for some other function).
[*]Click the Command/URL Settings tab and type either '/usr/bin/firefox' or just 'firefox'. Same difference. Hit OK or Apply and you're done!
[/LIST]

In part 2 I'll show you how to use mouse gestures and why the 'Generic' action type is so useful.

---

### Post by stimpack on 2005-11-08
Excellent guide thanks, just yesterday I worked out binding a multimedia key to XF86WWW with xmodmap, now with this guide, I bound XF86WWW to firefox :)

---

