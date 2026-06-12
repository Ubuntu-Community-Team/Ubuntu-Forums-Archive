---
title: "File Manager problem in Ubuntu 14.04 LTS"
date: 2015-01-31
forum: New to Ubuntu
---

### Post by nsmith01tx on 2015-01-31
I'm trying to install the Arduino IDE on an older Dell laptop i recently loaded with 14.04 LTS.
Everything's was going fine until I tried to set it up to execute the executable text file on the desktop - otherwise it just opens it in gedit.
Seems to be a standard problem & I know the answer is to go into Files Preferences & set the Behavior for Executable text files to "ask me".

Here's the problem:  I can't seem to get the the "Files Preferences" window.  Apparently, there should be a file cabinet icon on the left nav panel that's not there.   Meanwhile, I've searched high and low in the file manager and other areas and can't find the Files Preferences window anywhere.

So, what do I need to do?

I don't mind being called an ignorant newbie as long as I can figure this out.   

Thanks

---

### Post by kerry_s on 2015-01-31
it should be at the top of the screen.
it should also be in settings.

---

### Post by Paulgirardin on 2015-01-31
Open the Dash (The  top button in the launcher or the super [windows] key.
Type files
the cabinet icon should be in the results.
Open files ,the icon should appear in the launcher,right click on it and select 'lock to launcher'

---

### Post by nsmith01tx on 2015-01-31
Thanks Paul, that solved the intermediate problem - I now have the 'file cabinet' icon.   

Unfortunately, it points to the File Manager interface I'd already seen - which doesn't seem to include the "Files Preferences" screen that I'm looking for.  Any idea where to find it?

[IMG]http://planfully.com/wp-content/uploads/2014/06/File-Preferences.png[/IMG]

---

### Post by nsmith01tx on 2015-01-31
Ugh, more research indicates that this is a common problem encountered when Nautilus was updated. "File Preferences" and other items were removed.
As I apparently have no way to execute this file from the desktop (though I guess I could execute it in a terminal, I don't want to), I guess I'll try a new file manager - Nemo comes highly recommended.

---

### Post by nsmith01tx on 2015-01-31
Installed Nemo - nice, but it doesn't seem to solve the problem, just another view of the files.

---

### Post by nsmith01tx on 2015-01-31
Solved it - I think.  Found this post by [Basharat Sialvi]("http://askubuntu.com/users/37006/basharat-sialvi") back in 2013.  I followed this & it looks like it's working fine.


 Follow these steps:
  Install dconf-editor because it isn't installed by default.
  Hit Alt+F2, type dconf-editor and hit Enter.
  In dconfg-editor goto: org &#10148; gnome &#10148; nautilus &#10148; preferences
  [IMG]http://i.stack.imgur.com/ZZJXr.png[/IMG]
  Click on executable-text-activation and from drop down menu select:
  **launch**: to launch scripts as programs.
  OR
  **ask**: to ask what to do via a dialog.
  Close dconf-editor. Thats it!

---

### Post by JeQhdMD on 2015-01-31
Hmm, I'm running Trusty . . standard Unity, and when I click on the files icon in the launcher, I just point my cursor to the top panel (aka "menu bar") and then "edit>preferences>behavior tab . . . and I see the screen you posted with the options all as posted.   So I can just click the radial button to alter the output action to "ask each time" . . . am I missing your point?

---

### Post by nsmith01tx on 2015-02-01
As I said, it apparently depends on when, and maybe how, you installed 14.04 LTS.  There's been some change made to Nautilus fairly recently that has caused problems.  I wasn't able to see that screen at all. Had to install dconf-editor to regain that capability.  I don't know what they were thinking when they made that change.

---

