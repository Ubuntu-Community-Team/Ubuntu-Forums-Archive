---
title: "Ubuntu UI, app is running but inaccessible."
date: 2015-07-22
forum: New to Ubuntu
---

### Post by 1clue on 2015-07-22
Hi.

New to Ubuntu, but I've been using Ubuntu Server and Xubuntu (and a few other variants) for years.  What I'm new to is the current mainstream desktop.  I'm really trying to like it.

I've finally decided to give the new gui a go, and I've got a couple questions.  Background first:

[LIST=1]
[*]I have multiple desktops/workspaces going.
[*]I have dual monitors.
[*]I'm keyboard/hotkey oriented.
[/LIST]

Now, questions:
[LIST=1]
[*]I start an app (sublime-text-3 is problematic right now) and then fat-finger something or other for command/control keys, and then sublime disappears.
[LIST=1]
[*]It's still running, I can alt-tab to it and I can see it in 'ps axf | grep subl' but not in gnome-system-monitor unless I click 'my processes' instead of 'running processes.'
[*]When I alt-tab to it, there are no menus or windows.
[*]I can open a project on the  command line, use control keys, whatever, nothing shows up.
[*]I can kill it and even reboot, it still shows as running in ps but not in gnome-sytem-monitor whenever I run it.
[*]This has happened for other apps too.
[/LIST]

[*]The launcher, (Windows key) allows me to start typing to get a list of search matches.
[LIST=1]
[*]By default it makes me use arrow keys to select the app I want.
[*]Can I make it automatically select the most common match so I can just type <windows>app<enter>?
[/LIST]
[/LIST]

Thanks.

---

### Post by Bucky Ball on 2015-07-22
> (sublime-text-3 is problematic right now)

How exactly is it problematic? Just the fact you can't find it? How did you install it? Which release are you using? :)

---

### Post by grahammechanical on 2015-07-22
> Can I make it automatically select the most common match so I can just type <windows>app<enter>?

Have you tried doing that?

Of course, it all depends upon how specific the search term is. For example, typing software will bring up Software Updater, Software Centre; Software & Updates. It will also include recently used utilities to are connected in some way to software. So, if Synaptic Package Manager installed and has been loaded recently then it will appear in the selection. Pressing Enter will load the last used (first in the list) application found by the search term.

Being more specific in the search term limits what is found. The Dash search feature adjusts itself to our work habits. By going to System Settings>Security & Privacy>Search we can prevent the Dash searching online. Then we do not by mistake load a Wikipedia article or something like that.

Oh, by the way, Sublime text 3 is beta software. For an application to load after a reboot suggests that it has somehow become a Startup Application. Search the Dash for Startup Applications and check if it has been listed as a startup application.

Regards.

---

### Post by 1clue on 2015-07-22
@bucky ball: It's a webupd8 install, using sublime-text-installer.  It's been working for quite awhile, now the app starts but is inaccessible through any means I can find.  I can alt-tab to it and there are no windows, no menus.  The only way to kill it is to kill -TERM the process id, because the app is not responsive.  System updates, reboot, nothing makes it responsive.

This app is what I use to make my living.  It's problematic.

@grahammechanical, Yes I've tried that before and it seemed to not work, not sure why.  Works now, thanks.

---

### Post by PaulW2U on 2015-07-22
> **1clue said:**
> @bucky ball: It's a webupd8 install, using sublime-text-installer.  It's been working for quite awhile, now the app starts but is inaccessible through any means I can find.  I can alt-tab to it and there are no windows, no menus.  The only way to kill it is to kill -TERM the process id, because the app is not responsive.  System updates, reboot, nothing makes it responsive.

This app is what I use to make my living.  It's problematic.

1clue, have you tried downloading Sublime Text from the Sublime Text website? I've been using ST for some time and never had a problem with it while running Kubuntu, Xubuntu or Ubuntu. I'm currently running Ubuntu 15.10 and ST behaves exactly as it should.

Actually on one machine it appears as "Enter licence" rather than "Sublime Text" but that's a minor problem as I can still search for it as Sublime Text in the dash.

What's the advantage in getting ST from WebUpd8? Easier installation? Do they make any other changes?

---

### Post by 1clue on 2015-07-22
PaulW2U,

I have in the past used sublime from the website.  Since they have a PPA for it, this time I elected for the PPA.  It has been working fine for a month or better.  Now it's suddenly broken.

I've uninstalled sublime and re-installed it again.  Same problem.

The disappearing is not the app being lost on the disk.  It installs into /opt/sublime-text/ on the hard disk when you use the PPA.  It's still there.  The app is running.  I can see it in the process list.

[ATTACH=CONFIG]263327[/ATTACH][ATTACH=CONFIG]263328[/ATTACH][ATTACH=CONFIG]263329[/ATTACH]

The problem is that [B]when sublime is running, there is no menu and no windows and no response of any sort.
[/B]
Can someone who has installed sublime from the PPA tell me where the user settings go?  This is all I can think of at this point, something must be corrupt there.

---

### Post by 1clue on 2015-07-22
Solved.  Project file corrupted.

You have to start sublime from the command line with -n option in order to force it to not open the project that was opened before.  Then edit the project file manually, fix the errors and you're back in business.

---

