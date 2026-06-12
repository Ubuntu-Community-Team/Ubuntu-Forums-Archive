---
title: "HOWTO: Customize and use Gnome Terminal profiles"
date: 2009-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Junkieman on 2009-12-06
[SIZE="4"][COLOR="Sienna"]INTRO[/COLOR][/SIZE]

You can customize gnome-terminal to use different profiles to provide great visual feedback. It's not a technical-heavy howto, but I find this a very handy way to distinguish terminals at a glance. Whether you're a novice or an advanced user, I hope you find this as useful as I do!

This howto focuses on terminals launched from Custom Launcher buttons on your Gnome Panel.
[[img]http://h.imagehost.org/0517/taskbar-mouse-hover.png[/img]](http://h.imagehost.org/view/0517/taskbar-mouse-hover)

[SIZE="4"][COLOR="Sienna"]AN EXAMPLE[/COLOR][/SIZE]

- My default profile is green-on-black
- My traffic monitor (vnstat) shows yellow-on-black
- Folding at Home crunches proteins inside a black-on-gray terminal

Here's what they look like, scaled down for your viewing pleasure:
[[img]http://h.imagehost.org/0700/all-three-terminals.jpg[/img]](http://h.imagehost.org/view/0700/all-three-terminals)

I love my shortcut to open a Terminal, and I hope you have one too ;) -- *System -> Preferences -> Keyboard Shortcuts*

For our example let's create a profile for 'top', since I know everyone has top on their systems. But ultimately you'll want to use this on many other commands, and bash scripts. Especially ones that you run often.

[SIZE="4"][COLOR="Sienna"]STEP 1: ADD A NEW PROFILE[/COLOR][/SIZE]

Open a terminal and select Edit -> Profiles. Add a new profile and name it 'top' (to match our command name, but any name will do), click Create; The profile will open up so you can edit it. 

There are plenty options to fiddle with, but to be brief let's just set the Title (Title and Command tab) to 'Top'. On the Colors tab set the background color to white, and text color to blue; Click Close.

*Hint: Setting the title helps when alt-tabbing through the window list, and it shows in the window list too.*

[SIZE="4"][COLOR="Sienna"]STEP 2: CREATE A LAUNCHER[/COLOR][/SIZE]

Right-click your Gnome Panel -> Add to Panel. Select a 'Custom Application Launcher' and click Add. Choose an icon by clicking the large button, and enter the (descriptive) name, 'Top'. Enter a comment if you like, it will show in the launcher tooltip text.

Here is the command we will enter, I will explain it's parts after:

```
gnome-terminal --profile=top -e "top"
```

**gnome-terminal**: runs Gnome Terminal
**--profile=top**: tells the terminal to use our 'top' profile
**-e "top"**: runs the top command

*Note: On Intrepid use the "--window-with-profile" option instead of "--profile".*

Click Close and we're done. Click your launcher, you should see a blue-on-white terminal with top running. Press Ctrl+C to close it :)

[[img]http://h.imagehost.org/0551/top-in-action.jpg[/img]](http://h.imagehost.org/view/0551/top-in-action)

*Hint: You can adjust the terminal geometry and show/hide the menu bar, among others. Run "gnome-terminal --help-all" to see them all!*

[SIZE="4"][COLOR="Sienna"]TROUBLESHOOTING[/COLOR][/SIZE]

If your launcher doesn't run, check the following:

- Does the command you are trying to run exist?
- Commands after the -e option must be enclosed in "quotes".
- The default action is to close the terminal window when a command exits. You can change this behavior in the profile's *Title and Command* tab.

[SIZE="4"][COLOR="Sienna"]THANKS[/COLOR][/SIZE]

Thanks for reading, if you have any questions please post them, and I'll answer as best I can. Have any related tips you want to share? I'd be happy to hear them :) 

Happy customizing!

---

### Post by Luffield on 2010-08-29
Thanks for this HowTo - it's brilliant!

I would like to add that the --geometry option could be handy for this purpose. If you need the terminal window to be large in some cases and small in other cases, you can use this option.

Example:

gnome-terminal --geometry=80x45 --profile=top -e "top"

will open a terminal window with 80 columns and 45 lines (compared to 80x24 of the default).

---

