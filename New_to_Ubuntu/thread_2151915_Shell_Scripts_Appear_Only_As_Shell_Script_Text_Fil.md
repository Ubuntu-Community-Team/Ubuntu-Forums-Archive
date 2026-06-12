---
title: "Shell Scripts Appear Only As Shell Script Text Files, Not As App Icons"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by CJMacalister on 2013-06-06
Whenever I download any shell script application of any kind -- not necessarily of relevance, but in my particular case, examples would include but not limit themselves to Tor Browser Bundle and ZSNES -- the files clicking upon which should open the downloaded app in question appear only as shell script text files. For purposes pertinent partly to OCD and partly to convenience, I'd rather not open these files via the terminal all the time, and would like to ensure that future shell scripts appear as actual app icons by default.

How do I accomplish for what I'm aiming?

P.S.   I filed a bug report with Ubuntu on this issue, and that has confered neither a fix nor an email informing me what in particular the problem is.

---

### Post by Isamu715 on 2013-06-06
Executable shell scripts give you an option to execute upon double-clicking them in the file manager so you don't need to use the terminal to run them. A shell script is a not an app launcher, so it won't be displayed with an application icon. What you want to accomplish is having an application launcher attached to every script. That's only possible on the developers part. However, if you want, you can create your own launchers for frequently used scripts and put the in menu or in the scripts directory. These will show up as app icons and will be executable by double-clicking.

---

### Post by newb85 on 2013-06-06
For security reasons, when you download scripts, they do not have execute permissions enabled by default.  Once you have enabled execute permissions, double-clicking the file should give you the option to execute them.

You can enable execute permissions in the terminal
```
sudo chmod a+x pathto/filename.sh 
```

Or you can right-click the file, click Properties and go to the Permissions tab.

---

### Post by CJMacalister on 2013-06-07
> **Isamu715 said:**
> However, if you want, you can create your own launchers for frequently used scripts and put the in menu or in the scripts directory. These will show up as app icons and will be executable by double-clicking.

Okay, I'll do that. How do I go about doing that?

---

### Post by CJMacalister on 2013-06-07
newb85: I went ahead and tried both the terminal command and checked out the Permissions tab. The former didn't do anything, and upon checking the latter, the checkbox for enabling execute permission was already checked.

Is it possible that an error occurs on my computer in which shell scripts for some reason are not saved in .sh format? That may sound odd or dumb, but I thought I'd ask because I can't seem to verify one way or the other whether they are in that format...

---

### Post by newb85 on 2013-06-07
Well, chmod doesn't normally give any output.  When you opened Permissions, it was already checked because the chmod command changed it to executable.

Could you link or attach a sample file?  That might shed more light on the problem.

---

### Post by Isamu715 on 2013-06-07
[QUOTE=CJMacalister]Is it possible that an error occurs on my computer in which shell scripts for some reason are not saved in .sh format?[/QUOTE]
No, it's not possible, .sh is just a part of the filename, it doesn't change anything on Ubuntu because it uses mimetypes to identify files.

In your file manager go to Edit > Preferences > Behaviour. Under **Executable Text Files** check either "Ask each time" or "Run executable text files when they are opened".

[QUOTE=CJMacalister]Okay, I'll do that. How do I go about doing that[/QUOTE]
Create a text file where you want to have your icon or in *~/.local/share/applications/*(create the directory if it doesn't exist) if you want it to appear in the menu. Put the following in that file:
```
[Desktop Entry]
Name=The name that will be displayed with your icon
Exec=/path/to/an/executable/script
Terminal=false
Type=Application
Icon=/path/to/the/application/icon
StartupNotify=true
Path=/folder/from/which/you/would/normally/launch/the/script
```
If you're putting it in *~/.local/share/applications  *you can also add a categories line indicating in which menu categories will the launcher appear, for ex. if it's a game you'd add:
```
Categories=Game;
```
You can put it in more than one category(separated by semicolons). Valid categories include: Audio, Video, Development, Education, Game, Graphics, Network, Office, Science, Settings, System and Utility.

Add the .desktop extension to your file and mark it as executable if it's not in *~/.local/share/applications.*

---

