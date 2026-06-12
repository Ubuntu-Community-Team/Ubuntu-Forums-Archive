---
title: "Should bug filing documentation be changed?"
date: 2011-08-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-08-06
Many of you know I haven't been using the standard Ubuntu UI much lately, but rather focusing on Lubuntu, but I still want to very much know how to use our beloved parent Ubuntu :D

The old way to file a bug is to press Alt + F2 and then use "ubuntu-bug" as shown here:

[https://help.ubuntu.com/community/ReportingBugs#4.%20Collect%20information%20about%20the%20bug](https://help.ubuntu.com/community/ReportingBugs#4.%20Collect%20information%20about%20the%20bug)

But Alt + F2 no longer launches that old terminal app. Is there another way to launch that app or is it just deprecated?

I know I can just use the terminal but I'm curious. If the procedure has changed then we need to address the documentation I guess :)

---

### Post by dniMretsaM on 2011-08-06
> **kansasnoob said:**
> Many of you know I haven't been using the standard Ubuntu UI much lately, but rather focusing on Lubuntu, but I still want to very much know how to use our beloved parent Ubuntu :D

The old way to file a bug is to press Alt + F2 and then use "ubuntu-bug" as shown here:

[https://help.ubuntu.com/community/ReportingBugs#4.%20Collect%20information%20about%20the%20bug](https://help.ubuntu.com/community/ReportingBugs#4.%20Collect%20information%20about%20the%20bug)

But Alt + F2 no longer launches that old terminal app. Is there another way to launch that app or is it just deprecated?

I know I can just use the terminal but I'm curious. If the procedure has changed then we need to address the documentation I guess :)

Indeed it should. When I was filing a bug for this first time, this confused me for a long time. Now I can do it pretty easily, but for new users (which is usually who documentation is for), it should definitely be changed.

---

### Post by castrojo on 2011-08-06
You can just replace the screenshots with the alt-f2 from Unity and that would work out. (Feel free to just add them)

---

### Post by kansasnoob on 2011-08-06
I wonder who to bug about getting that changed :confused:

Maybe one of the mods will have an idea.

---

### Post by kansasnoob on 2011-08-06
> **castrojo said:**
> You can just replace the screenshots with the alt-f2 from Unity and that would work out. (Feel free to just add them)

I'm not sure I have the proper skills :)

I've never edited any docs like that.

---

### Post by kansasnoob on 2011-08-06
BTW I'm also a bit confused now by terminal options:

Gnome-terminal, Xterm, and UXterm :confused:

---

### Post by castrojo on 2011-08-06
> **kansasnoob said:**
> I'm not sure I have the proper skills :)

I've never edited any docs like that.

If you post some screenshots here I'll put them up for you. The ubuntu wiki's are all MoinMoin, the syntax isn't much different than a forum: [http://moinmo.in/HelpOnMoinWikiSyntax](http://moinmo.in/HelpOnMoinWikiSyntax)

---

### Post by kansasnoob on 2011-08-06
> **castrojo said:**
> If you post some screenshots here I'll put them up for you. The ubuntu wiki's are all MoinMoin, the syntax isn't much different than a forum: [http://moinmo.in/HelpOnMoinWikiSyntax](http://moinmo.in/HelpOnMoinWikiSyntax)

But it also involves editing the instructions since Alt + F2 is no longer the proper method. I'm honestly not sure what the proper method should be since I seldom use unity.

I don't think Crtl + Alt + F1 would be correct because it's non-gui, and suggesting to launch gnome-terminal seems lengthy.

I'm honestly not trying to be difficult, I'm just not sure what the official procedure should be ;)

What I currently do is click on the app icon in the launcher and type "term", that shows three options and I choose "gnome-terminal" but I have no idea what either of the other two would do.

Then I type "ubuntu-bug + whatever's_buggy" and follow the rest of the instructions.

But that is very sloppy to include as instructions.

I don't know much but I do know when I'm I'm ill equipped for a job :D

---

### Post by mc4man on 2011-08-06
The alt+f2 > type in  ubuntu-bug <package name or pid> works like before, the only difference is the run dialog box is different, now a lenses.

---

### Post by kansasnoob on 2011-08-06
> **mc4man said:**
> The alt+f2 > type in  ubuntu-bug <package name or pid> works like before, the only difference is the run dialog box is different, now a lenses.

Nothing pops up when I try that :confused:

This is why I say I'm ill equipped to deal with this :)

I know when I don't know what I'm doing.

---

### Post by mc4man on 2011-08-06
> **kansasnoob said:**
> Nothing pops up when I try that :confused:

This is why I say I'm ill equipped to deal with this :)

I know when I don't know what I'm doing.
Not at all - you could ck. ccsm and see if the binding was unset (assuming unity -
unless you mean ubuntu-bug does nothing, but alt+f2 works?

Otherwise differing behavior on individual installs seems quite common at this point, I see it here on 2 installs on 2 machines..

---

### Post by kansasnoob on 2011-08-06
> **mc4man said:**
> Not at all - you could ck. ccsm and see if the binding was unset (assuming unity -
unless you mean ubuntu-bug does nothing, but alt+f2 works?

Otherwise differing behavior on individual installs seems quite common at this point, I see it here on 2 installs on 2 machines..

This is a fresh install of Alpha 3 that I used to test for this bug:

[https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/822043](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/822043)

No doubt it's quite an insignificant bug but my real reason for doing that was to see how bug-filing now worked with lubuntu and I can now see most lubuntu bugs will likely go to lubuntu-meta.

But .............. Alt + F2 fails to launch old faithful. So we need to create a bug filing method that works across the board. Something that just works, but it must also allow access to the DE which Ctrl + Alt + F1 does not do.

Another way of putting this is: I don't know what to do, but the old method doesn't work anymore .......... HELP!

---

### Post by kansasnoob on 2011-08-06
I wished I'd put it this way earlier:

**We need a consistent and coherent method of filing bug reports, but I don't know what that should be ;)**

---

### Post by mc4man on 2011-08-06
I think many people would just use a terminal, but going back to the docu, - it works just fine as described - fail to see what's 'incoherent' there

If it, (alt+f2 itself, or alt+f2 ubuntu-bug <whatever>, not exactly sure what is failing you), isn't working for you then I wouldn't find that surprising
For instance on my 5 day old install I cannot create and use custom keyboard shortcuts, on an older one I can.

If I boot to the 5 day ago iso I can use custom binding, so either I messed something up or something messed itself up.

Rather than get hung up on I'm going to grab the latest, test in a live session and if all is well than dump this install and  redo. I won't touch anything so to speak and if I lose the ability again then I'd figure there is a bug, if not then it was me or just one of those things that happens..

So if you boot to a live session does alt+f2 blah, blah work? (in unity or unity-2d

Edit: - so if I create a new user it can create/use custom binding so it's likely something I did,  -turns out a dconf setting was unset, now it works

---

### Post by kansasnoob on 2011-08-06
So, instead of the documentation saying:

> Press Alt+F2 to open the "Run Application" window, pictured above. Type ubuntu-bug <package name> and click Run.

It should say:

> Press Alt+F2 to open the "Run Application" window, pictured above. Type ubuntu-bug <package name> and click Run. **But if that doesn't work just forget about it.**

---

### Post by mc4man on 2011-08-06
> **kansasnoob said:**
> So, instead of the documentation saying:


Press Alt+F2 to open the "Run Application" window, pictured above. Type ubuntu-bug <package name> and click Run. 

I guess if you wanted to be technically correct, for unity* is should say something to the effect of
Press Alt+F2 to open  "Run a command" 
... then press enter or double click on the command icon
> **kansasnoob said:**
> 
It should say:
Press Alt+F2 to open the [COLOR="Blue"]"Run Application" window,[/COLOR] pictured above. Type ubuntu-bug <package name> and [COLOR="Blue"]click Run.[/COLOR] But if that doesn't work just forget about it.

Maybe talking apples and oranges because what you're describing is not what happens on unity, unity-2d or gnome-shell
If so sorry to have wasted your time w/ my posts

---

### Post by cariboo on 2011-08-07
The wiki page only needs to have an addendum to show the differences in running ubuntu-bug in Unity and gnome-shell. There are still quite a few users using older versions, or one of the alternatives. Once the next LTS is released, there may be a need to completely redo the wiki page.

---

### Post by kansasnoob on 2011-08-07
> **mc4man said:**
> I guess if you wanted to be technically correct, for unity* is should say something to the effect of
Press Alt+F2 to open  "Run a command" 
... then press enter or double click on the command icon

Maybe talking apples and oranges because what you're describing is not what happens on unity, unity-2d or gnome-shell
If so sorry to have wasted your time w/ my posts

You weren't wasting my time. I apologize for getting grumpy but I thought I'd done well at explaining that I didn't know enough to try and edit the instructions myself.

I asked a question and I got quite frustrated when it was suggested that I edit something I was not at all comfortable doing ............... then my carpet "shampooer/steamer" blew up and my irritation boiled over on you :(

So please accept my apology, I was a turd :oops:

You've helped me many times and I should know by now to say nothing if I'm in a bad mood. I swear sometimes this re-remodeling of the kitchen is going to be the death of me.

---

### Post by kansasnoob on 2011-08-07
> **cariboo907 said:**
> The wiki page only needs to have an addendum to show the differences in running ubuntu-bug in Unity and gnome-shell. There are still quite a few users using older versions, or one of the alternatives. Once the next LTS is released, there may be a need to completely redo the wiki page.

That makes sense. I formed this as a question because I honestly haven't spent as much time as normal between the chair and the desk so I'm largely clueless as to what's a temp bug and what's a design change :)

And after 5 rounds of Ubuntu iso-testing, 1 round of Lubuntu iso-testing, and trying to deal with my torn up house I just boiled over a bit :(

That's really inexcusable. I'm rather ashamed of myself.

---

