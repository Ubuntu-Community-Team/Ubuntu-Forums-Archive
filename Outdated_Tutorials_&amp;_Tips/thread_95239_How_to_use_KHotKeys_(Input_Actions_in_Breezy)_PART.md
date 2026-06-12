---
title: "How to use KHotKeys (Input Actions in Breezy) PART 2"
date: 2005-11-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Takis on 2005-11-26
The saga continues, moving to show how KDE really can shine. In this week's episode, I'll take you through the first steps of mouse-gesturing in KDE.

First I'll show how to set all KDE-based programs to use the same shortcut sequence to do the same thing (this is very relevant). Since the Gnome standard is CTRL+Q for quit, it's good for your KDE to mirror this so that when you do the gesture for CTRL+Q, it'll work the same way in both Gnome and KDE programs. Go to Settings->Regional & Accessibility->Keyboard Shortcuts. Under the Shortcut Schemes tab and Application Shortcuts subtab, scroll down to the Quit setting and set it to CTRL+Q. Hit OK.

Go to Settings->Regional & Accessibility->Input Actions (may be called KHotKeys). Hit the Global Settings button and go to the Gestures Settings tab. Uncheck the 'Disable mouse gestures globally button'. (On a subnote, this window also houses the global exclude list - programs that will not be affected by mouse gestures. I have listed Wine and Firefox (Firefox can do its own, more customised gestures) to be excluded). Hit 'Apply'.

Click the 'New Action' button. Set the name to 'Quit Program' or something else that will help you identify it in future. Set the Action Type to generic. Hit 'Apply' (you need to hit apply reasonably often because KHotKeys seems a little unstable in Breezy and tends to crash for no reason every now end then).
Open the Triggers tab and hit New->Gesture Trigger. You'll need to draw the same gesture three times - I usually use down-right, because that's what Firefox uses as well. When you've drawn the same thing three times (it'll let you know when you haven't) hit OK. You may like to put a comment like "Gesture: Down-Right".
Open the Actions tab. Click New->Keyboard Entry. Type CTRL+Q exactly and hit OK. Hit Apply.

That's it! Give it a whirl, and post questions/comments here. Next episode I'll show you how to use DCOP calls with gestures to do funky stuff with running programs.

---

### Post by xtacocorex on 2006-02-12
I have been trying to figure out how to get mouse gestures to work for the longest time. I had no clue they were turned off by default. I thought I was doing the motions all wrong.

Thanks for this part of your HowTo.

---

