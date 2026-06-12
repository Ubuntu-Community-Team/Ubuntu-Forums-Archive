---
title: "add &quot;custom command&quot; option missing in &quot;open with menu&quot;"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by beew on 2011-09-25
The title says it all. I can't find the option "use a custom command" in the "open with" menu when I right click a file. It is a fresh install of Ubuntu 11.10 beta2

---

### Post by mc4man on 2011-09-25
> **beew said:**
> The title says it all. I can't find the option "use a custom command" in the "open with" menu when I right click a file. It is a fresh install of Ubuntu 11.10 beta2

You can't find it because it's not there, been removed in gnome/nautilus 3
Either search out how to create 'desktop' launchers thru the gui or - 
Make a .desktop where the Exec= uses your custom command or script,  or add a custom command/script to the Exec= in a quicklist entry

---

### Post by beew on 2011-09-25
> **mc4man said:**
> You can't find it because it's not there, been removed in gnome/nautilus 3
Either search out how to create 'desktop' launchers thru the gui or - 
Make a .desktop where the Exec= uses your custom command or script,  or add a custom command/script to the Exec= in a quicklist entry

I see. Thanks for the info.. but they took it out??? Why??!!

---

### Post by mc4man on 2011-09-25
> **beew said:**
> I see. Thanks for the info.. but they took it out??? Why??!!
Basically [see here]("http://ubuntuforums.org/showthread.php?p=11285335#post11285335")

---

### Post by beew on 2011-09-25
Hi,

Maybe I am not explaining myself very well, I am not asking about creating desktop launchers (though it is certainly useful info) I am talking about setting default applications by right clicking a file and choosing the application to open it with. In 11.04 and before I was able to choose applications that are not displayed in the (usually limited) list they show you and choose an app say from /usr/bin by adding a custom command.

---

### Post by crdlb on 2011-09-25
You can easily create a .desktop file for your custom command by using the alacarte menu editor. The command should be followed by '%f' (or '%F' if it accepts multiple filenames on one command line). ```
foobar %f
``` It will then show up under 'Other Applications'.

You could also set the 'MimeType=' key in the .desktop file so that it would appear under 'Recommended Applications', but you'd have to do that manually.

---

### Post by mc4man on 2011-09-25
> **beew said:**
> Hi,

Maybe I am not explaining myself very well, I am not asking about creating desktop launchers (though it is certainly useful info) I am talking about setting default applications by right clicking a file and choosing the application to open it with. In 11.04 and before I was able to choose applications that are not displayed in the (usually limited) list they show you and choose an app say from /usr/bin by adding a custom command.

Really the same diff. - when you use a custom command it creates a custom .desktop (formally userapp .desktop's
The reasoning behind the lack of is the same

---

### Post by beew on 2011-09-26
> **mc4man said:**
> Really the same diff. - when you use a custom command it creates a custom .desktop (formally userapp .desktop's
The reasoning behind the lack of is the same

I think you can run the custom command in terminal without creating a desktop file, no?

The reasoning seems pretty stupid and definitely a step backward. It is not a big deal for me but why make process like creating .desktop files more difficult for new users while the ostensible reason for UI change is to attract new users? If the gnome upstream persists in this stupidity at least Canonical should provide a patch.

---

### Post by mc4man on 2011-09-26
What you can do from a terminal or run dialog has nothing to do with what's available from the  nautilus context menu or the 'open media' choices.
If you (or anyone else) wanted to pursue you could open a bug against nautilus, if not already, though I can't see any particular reason why ubuntu would want to modify this

see here for 1 element (regarding desktop launchers
[https://bugs.launchpad.net/ayatana-design/+bug/723861](https://bugs.launchpad.net/ayatana-design/+bug/723861)

---

### Post by chlorox on 2011-09-26
From the looks of things, Nautilus has removed my ability to define a custom path and application to open a particular file type.

I use Sublime Text to do my text editing but if I right-click on any text based file, the only options I get are GNU Emacs or Gedit (Text Editor).

When I click on "other applications", I don't see Sublime as a choice.

Ubuntu 10.10 gave a user the ability to add a custom command. Does this still exist somewhere buried in Oneiric?

---

### Post by dino99 on 2011-09-26
[http://ubuntuforums.org/showthread.php?t=1849973](http://ubuntuforums.org/showthread.php?t=1849973)

---

### Post by chlorox on 2011-09-26
> **dino99 said:**
> [http://ubuntuforums.org/showthread.php?t=1849973](http://ubuntuforums.org/showthread.php?t=1849973)

That is pertaining to creating desktop launchers. I can do that just fine. I'm talking about the Nautilus context menu.

Use case:

Connect to remote server, point to remote Javascript file that I want to edit, right click, choose open with other program (because, honestly, I DON'T want to open it with GEdit), be presented with no choice.

It seemed all the other users on that thread misunderstood what the person was asking.

Was it killing Nautilus to let us make a choice?

---

### Post by crdlb on 2011-09-26
The developers of Sublime Text should have installed a .desktop file to make this work automatically. See this thread on their forum: [http://www.sublimetext.com/forum/viewtopic.php?f=2&t=1689](http://www.sublimetext.com/forum/viewtopic.php?f=2&t=1689)

A .desktop file provides important extra information beyond the command itself, particularly for an application-based desktop.

---

### Post by mc4man on 2011-09-26
> **chlorox said:**
> he other users on that thread misunderstood what the person was asking.

Was it killing Nautilus to let us make a choice?
It was the same thinking - Both create desktop launchers & "use a custom command" have been removed.

---

### Post by chlorox on 2011-09-26
Ultimately frustrating... having to manually create launchers and not being able to (simply) choose what program one wants to use?

I don't see why this is considered a leap forward. But I digress... it seems most are behind these hugely important design decisions.

---

### Post by mc4man on 2011-09-26
> **chlorox said:**
> Ultimately frustrating... having to manually create launchers and not being able to (simply) choose what program one wants to use?

I don't see why this is considered a leap forward. But I digress... it seems most are behind these hugely important design decisions.

Probably most users that care one way or the other aren't behind these changes. It only takes a couple of people who are in a position to make such changes to think they're a good idea to have them happen, much harder to get them reverted, if ever..

---

### Post by chlorox on 2011-09-26
> **mc4man said:**
> Probably most users that care one way or the other aren't behind these changes. It only takes a couple of people who are in a position to make such changes to think they're a good idea to have them happen, much harder to get them reverted, if ever..

Yeah, I'm not familiar with any of the developers whom are working on Gnome.

I do find it complete irony that when I started working with Linux in 1998, one had to manually configure one's x86config by hand using vim from the CLI. We've come so far past that stage that now one has to configure one's application.desktop manually.

;)

---

### Post by mc4man on 2011-09-26
I guess it's all from perspective, the custom command deal, while it wouldn't be bad to have, doesn't bother me too much
Many of them I tend to keep using so I use some 'category' type launcher icons where they're avaialble from quicklists. In those cases for the most part still using ones created during natty dev, just copy the .desktops from a flash to ~/.local/..
I also pre-populate the run history from a saved file so some are already there.

On the other hand, while a tiny issue that most will likely care less,(or even like),  I hate the new screenshot name save format. Again someone decided date/time was better. 
The time/date means nothing to me, window titles do (or did

---

### Post by chlorox on 2011-09-26
> **mc4man said:**
> I guess it's all from perspective, the custom command deal, while it wouldn't be bad to have, doesn't bother me too much


Well knowing that it's not a bug, that it is flat out MEANT to be missing, is all the closure that I need on the issue.

The other two big players in the operating system game DO let you define a custom app to use, no matter where it's located or if it included a special file with it. As long as you can navigate to it, you can use it. I didn't see that as a point of confusion that needed a remedy.

The .desktop files remind me of Windows PIF files back in the early 90's.

---

### Post by seeker5528 on 2011-09-26
> **mc4man said:**
> Really the same diff. - when you use a custom command it creates a custom .desktop (formally userapp .desktop's
The reasoning behind the lack of is the same

?????

Since the Gnome devs don't want to support desktop launchers anymore the independently handled ability to specify what application to use to view a file of a certain type should also be broken?

Later, Seeker

---

### Post by mc4man on 2011-09-26
> **seeker5528 said:**
> ?????

Since the Gnome devs don't want to support desktop launchers anymore the independently handled ability to specify what application to use to view a file of a certain type should also be broken?

Later, Seeker
The 'reasoning' behind the decision(s) to remove Both is likely the same, for a more definitive ask them.


> ability to specify what application to use
You are free to choose any 'app' that shows in the r.click list  - nothing is 'broken, just limited to existing .desktops.
If not there as desired then the user can add by creating an appropriate .desktop in an applications dir.

---

### Post by cariboo on 2011-09-26
Merged two threads on the same subject.

---

