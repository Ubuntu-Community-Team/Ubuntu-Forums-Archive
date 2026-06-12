---
title: "How to make Ubuntu Tablet-Friendly (1: Modifier Keys)"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ErkDemon on 2011-08-24
One of the advantages of Ubuntu and Win8 against iOS/Android is the existence of a library of powerful, professional-grade cross-platform applications that let the user access the same familiar software tools on a desktop, netbook or tablet. 

If Ubuntu is going to embrace a tablet-style future, it can't expect these apps to be dumbed down and redesigned around a default iPad one-finger interface, with all the right-key and hover and modifier key options stripped out. "Pro" users on laptops and desktop machines don't expect their apps to be crippled -- they're not going to accept an Apple-style one-button mouse interface -- but if there are standard features on programs that tablet users can't access, the tablet users get frustrated.

So we need to devise a way for tablet users to be able to trigger features that are normally accessed through non-tablet interfaces.
 
Luckily, it seems fairly easy to do. All Ubuntu needs is a floating, dockable, "helper" strip with "sticky" modifier-key pads … "Ctrl", "Shift", & "Alt" for starters, colour-coded (I'd personally make the "Ctrl" button red, "Alt" yellow and "Shift" blue or green). If you poke the "Ctrl" pad, it changes to inverse colours, and from that point onwards, all your clicks, swipes and drags become Control-clicks, Control-swipes and Control-drags, until you prod the pad a second time and revert it to its normal state. Same with "Alt" and "Shift", either individually or together. 

Now it gets fun. 

Add a "right" pad. Poke it once, and your subsequent clicks and drags get reported as right-mouse-button clicks and drags. You can finally do right-mousebutton stuff. Yaaay!
The right mousebutton pad will probably be “sticky” too, but there are also times when you'll want to call up a context-sensitive menu with a brief right-click on an item, and for that, you can have a "Menu" pad that turns the next finger-poke into a momentary right-click, or into a “menu key” event. 

Then add a momentary "Help" pad, with a big friendly question mark. This turns the next poke into either an F1 event, or left-button-then-F1, depending on what works best.

Suddenly you have a high-profile integrated context-sensitive help system, that uses all the apps' existing help features, and requires almost no work to set up. And its high visibility immediately tells people that they already know how to use the new features. 

Instead of trying to copy the limitations of iOS, Ubuntu would be showing a friendly, professional interface that makes /iOS/ look as if it hasn't been properly thought-out (how do you access iOS help?). It'd be putting iOS into a position of having to either copy Ubuntu and acknowledge it as an interface market leader, or sticking with their existing system and looking perverse, like they did with the one-button mouse.

And we can do other things. Add a hover-pad. Poke the pad, click on an object, and the OS wrangles some way of sending the app something that it'll recognise as a hover action. 

Not everyone will want these features, so the panel strip needs to be hideable, and maybe also configurable. And now that we are supporting right-clicking, we can make the panel itself configurable with a right-click option menu, so people can chose which edge of the screen they want it attached to by selecting options from a dialog box without having to do fiddly dragging with stubby fingers. 

And that's it. Implement that one feature, and potential users can see right away from a screenshot that this is a powerful tablet OS designed to be used with fingers, that it has functions that are missing from iOS, and that there are methods in place to allow their existing software to be used on an Ubuntu tablet without modification.

---

