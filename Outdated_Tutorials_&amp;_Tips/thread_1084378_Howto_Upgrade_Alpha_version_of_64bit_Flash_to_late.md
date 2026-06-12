---
title: "Howto: Upgrade Alpha version of 64bit Flash to latest version (d22)"
date: 2009-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Vadi on 2009-02-26
Adobe has upgraded the prerelease/alpha version of the Native 64bit Flash for Linux, and I've updated the previous script used to install it for the new version. This upgrade is also required for the new [AIR Marketplace]("http://www.adobe.com/cfusion/marketplace/index.cfm?event=marketplace.home&amp;marketplaceid=1") to work!

[SIZE="5"]Graphical instructions[/SIZE]

[SIZE="4"]Step 1: Download the script[/SIZE]

Download and save the attached *native-64bit-flash-installer.sh* file onto your Desktop.

[SIZE="4"]Step 2: Allow the script to run[/SIZE]

Right-click on *native-64bit-flash-installer.sh*, select *Properties*, *Permissions*, and enable "**Allow executing as file**" (or something similar about execution).

[SIZE="4"]Step 3: Run it[/SIZE]

Open the terminal, drag the script file into it, and press enter to start the installation :) After you're done, see the Confirm Installation section.

[SIZE="5"]Terminal instructions[/SIZE]

Alternatively to the graphical instructions, running the following commands in the terminal would do:

```
wget http://dl.getdropbox.com/u/84880/native-64bit-flash-installer.sh
sh ./native-64bit-flash-installer.sh
```

[SIZE="5"]Confirm installation[/SIZE]

Go to *Tools* &#9656; *Addons* &#9656; *Plugins* in firefox. It should say that the Shockwave Flash version is *10.0 r22*. And that's it, enjoy!

PS. The flash binaries are [available here]("http://labs.adobe.com/downloads/flashplayer10.html"), if you're not comfortable with running the script.


Originally posted @ [http://vadi-blog.com/2009/02/26/howto-upgrade-alpha-version-of-64bit-flash-to-latest-version/](http://vadi-blog.com/2009/02/26/howto-upgrade-alpha-version-of-64bit-flash-to-latest-version/)

---

