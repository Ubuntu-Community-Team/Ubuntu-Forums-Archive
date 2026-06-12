---
title: "Updating Eclipse to helios?"
date: 2011-02-18
forum: Programming Talk
---

### Post by sneakyimp on 2011-02-18
I installed Eclipse on this machine using the Ubuntu Software Center.  Unfortunately, it's Galileo and the latest Eclipse is Helios.  I'd like to upgrade to the very latest Eclipse but I want to be sure that the Applications menu link correctly launches whatever I upgrade to.

Can I just download the tgz file of helios and overwrite my existing Eclipse install?  If so, where is that exactly?

Or, alternatively, is there some way to get helios through the Ubuntu Software Center?

Can anyone recommend the best way to upgrade Eclipse to the very latest version? Any help appreciated muchly.

---

### Post by GregBrannon on 2011-02-19
You can download the desired Eclipse distribution from the eclipse.org site, unpack it, and stick the result in a directory that you own, usually a directory off of your home directory.  You can build a launcher (shortcut, whatever it's called) to the eclipse executable in the eclipse subdirectory.  If you like, you can have multiple Eclipse installs that use the same or separate workspaces.

Some will point out that doing your own install outside the software center requires you to keep the program updated, but Eclipse does its own updating if you have it turned on.

---

### Post by sneakyimp on 2011-02-19
Thanks Greg.

I installed my current version of Eclipse using the Ubuntu Software Center (USC).  Inside that Eclipse under Preferences -> Install/Update -> Automatic Updates, I have the checkbox selected which says "Automatically find new updates and notify me".  It has yet to update my Eclipse from Galileo to Helios. I've run the overall ubuntu software update a couple of times. My guess is that this might be considered an "upgrade" and not an "update".  I'm currently going through a lot of (unpaid!) trouble to migrate my PHP dev to this Ubuntu machine and want to make sure I have the very latest.  

Since Eclipse has a built-in tool to update itself, I'm not particularly concerned about Ubuntu keeping Eclipse up-to-date so I think a manual download/install sounds like a good idea.  I would very much like to *replace* the existing Eclipse installed by USC but don't know enough about these Launchers...are these shell scripts?  Where do they live? I've tried right-clicking these in the GUI but can't seem to find their location on disk. Any resources or advice would be much appreciated.

---

### Post by GregBrannon on 2011-02-20
Yes, the Eclipse updater stays within the named distribution, providing updates to Galileo but not to a new version like Galileo to Helios.  I think there's a new one out soon, but I forget what it's called and when it's due.

You mention that you'd like to replace Galileo with Helios.  Since you installed Galileo using the Software Center, you can uninstall it the same way.  A reason you may want to keep Galileo is that I find Helios' code completion sometimes pauses for several seconds.  I've seen reports that this was a reported bug and that it was fixed in a SP2 (which I have), but I still see it often.  For that reason, I occasionally use Galileo, especially on less capable computers I sometimes edit on.  I bounce back and forth between the different Eclipse versions sharing the same workspace to work on the same project without a problem.  Just a thought.

Don't let your uncertainty about creating a launcher or shortcut prevent you from exploring a bit.  I don't use Ubuntu routinely, but in my KDE desktop's Desktop Folder, if I right click and select "Create New," then "Link to Application . ." I can create a simple shortcut to a program in the resulting dialog by specifying the name, location, icon, etc.  It's very simple.  There must be something equivalent in your environment.  What I've described is certainly easier than most Java programs beyond the introductory "Hello, World" program.

Good luck, but don't hesitate to ask if you need help.

---

### Post by Taamalus on 2011-03-14
> **GregBrannon said:**
> You can download the desired Eclipse distribution from the eclipse.org site, unpack it, and stick the result in a directory that you own, usually a directory off of your home directory.  You can build a launcher (shortcut, whatever it's called) to the eclipse executable in the eclipse subdirectory.  If you like, you can have multiple Eclipse installs that use the same or separate workspaces.

Some will point out that doing your own install outside the software center requires you to keep the program updated, but Eclipse does its own updating if you have it turned on.
Sorry to interrupt! Where, in the Home folder, should this program be installed? Technically, this question should go in the beginner forum, but I did not want to open another topic.

My Eclipse needs to do PHP and be be able to interact with a my server, sandbox as well as real one and WordPress. ](*,)

---

### Post by myrtle1908 on 2011-03-15
> **Taamalus said:**
> Where, in the Home folder, should this program be installed?

You can put it wherever you like. The home folder was just a suggestion.  For example, you may like to have a IDE directory in your home folder and shove all your IDEs in there ...

```

/home/you/IDE/Eclipse/europa
/home/you/IDE/Eclipse/helios
/home/you/IDE/Eclipse/galileo

```

etc

---

