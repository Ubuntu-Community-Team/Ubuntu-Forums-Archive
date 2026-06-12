---
title: "Programming an Ubuntu feature"
date: 2010-07-31
forum: Programming Talk
---

### Post by smmalmansoori on 2010-07-31
[This issue]("https://bugs.launchpad.net/ubuntu/+bug/592330") is bugging me and I'd like to try programming the fix.

The problem is I don't know which part of the system responds to double-clicking an executable, that's the file I need to modify can anyone point me to it?

---

### Post by Bachstelze on 2010-07-31
Where does the "root access required" message appear?

---

### Post by Tony Flury on 2010-07-31
If you think about how the command line works, you have to explicitly state that you want to run the command as root (use sudo or gksudo), and then provide the password - i.e. a two step process.

It would be a retograde step if Clicking an icon suddenly became a single step process for running as root (i.e. just entering the password).

I would prefer to have a right click menu option available for executables that says something like "Open As" - that way you maintain the two step process, and as an added bonus you could allow the icon to be run as any user - just like "su" on the command line.

---

### Post by smmalmansoori on 2010-07-31
@Bachstelze: It appears in a dialog box when I double click on the installer

@Tony Flury: That's a great idea, I think I'll be going that way since it makes more sense.

Could you point me to where I could find resources documenting the right-click menu options and how they're modified?

---

### Post by Bachstelze on 2010-07-31
> **smmalmansoori said:**
> @Bachstelze: It appears in a dialog box when I double click on the installer

Can you make a screenshot?  The dialog is probably created by VMWare, not by Ubuntu.

To customize the right-click menu, look at nautilus-actions.

---

### Post by smmalmansoori on 2010-07-31
Thanks for the info about nautilus-actions, and you were right about vmware creating the error rather than ubuntu.

Will probably post here when I finish the right-click menu option.

Here is the screenshot of the vmware error

---

### Post by SevenMachines on 2010-08-01
nautilus-gksu adds a 'open with root privileges' right-click option with password prompt, i dont know if it allows running scripts or not but it might be worth looking into that and adapting that if needed

---

### Post by smmalmansoori on 2010-08-06
@[SevenMachines]("http://ubuntuforums.org/member.php?u=915690") it allows you to "open as administrator", the problem with that is you'd have to choose a program to open it with, I need an option like "run as administrator" something that does "gksudo ./filname.extension" in the background.

---

### Post by interval1066 on 2010-08-06
Ok, I have a lot of experience using VirtualBox and none with VMWare, so if for some reason you must have VMWare I apologize; BUT- I've downloaded and installed the virtbox.deb from the web site and never had a problem with it, you simply click on it, the debi package installer asks for the root pw, and its done. Like I said, maybe vb won't work for you, but I've simply never had any root auth problems with it.

---

### Post by smmalmansoori on 2010-08-08
@[interval1066]("http://ubuntuforums.org/member.php?u=298972") I already installed it and all but it brought to my attention the need to have an "Run as Administrator" option.

I installed nautilus-actions to use the Nautilus Actions Configuration Tool, in the Command tab I set the Path to **/usr/bin/gksudo** and I set Parameters to **./"%d/%f"** so this is equivalent to "gksudo ./filename". But when I use it nothing happens.

Any ideas?

---

### Post by smmalmansoori on 2010-08-08
All Done, will look through the packaging section to make this available in the repos if anyone wants it

---

### Post by smmalmansoori on 2010-08-21
I added it to nautilus-actions in launchpad with the attachments, have a look [over there]("https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/592330") if you want this feature all the steps are provided in the posts.

---

### Post by worksofcraft on 2010-08-21
An easy alternative is to make a gksudo launcher and instead of double clicking you just drag your icon on to it to run it with supervisor privileges...

Right click on your panel, from "add to panel" choose Launcher and enter the details as seen in attached picture.

---

