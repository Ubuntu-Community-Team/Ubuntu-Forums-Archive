---
title: "Re-creating the panels"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by mcbagpipe89 on 2008-08-09
I hate to admit it, but in my configuring of AWN, I seem to have deleted both of my panels.  I did some searching around the forums, and thought I had the solution (I thought gnome-core wasn't installed) but it is in fact installed. Is there a way to recreate my panels short of creating a new user account?  (I have the terminal accessible, and a somewhat crippled main menu in AWN)  Thank you for your assistance!

---

### Post by ggaaron on 2008-08-09
You mean gnome-panels? If yes, then there is... Unfortunately it is a GNOME way -> advanced features should be hidden from user, so it is unpleasant, not time consuming though if you know how to do this. I've done this before, so if your problem is with gnome-panels then I'll try to remind myself how I did it.

---

### Post by mcbagpipe89 on 2008-08-09
That would be great.  Thank you.

---

### Post by ad_267 on 2008-08-09
Can you run gnome-panel from the command line to get it back?

---

### Post by mcbagpipe89 on 2008-08-09
I receive the message "a panel is already running"  (I cannot see it though, or use alt f2)

---

### Post by sisco311 on 2008-08-09
try to rename(delete) the config folder (~/.gconf/apps/panel)
and let the system to recreate the default panels.

---

### Post by mcbagpipe89 on 2008-08-09
I am unsure as to how to do that.

---

### Post by ggaaron on 2008-08-09
Hmm, if you just deleted the panels, then maybe setting toplevel_id_list=[top_panel] in /apps/panel/general in gconf-editor might do it.

---

### Post by sisco311 on 2008-08-09
> **mcbagpipe89 said:**
> I am unsure as to how to do that.
Press Ctrl+H in nautilus(the default file manager) in order to list hidden folders.
Navigate to the *.gconf/apps/* directory and rename the *panel* folder.
Press Ctrl+Alt+Backspace to restart the xserver.

---

### Post by ggaaron on 2008-08-09
To restore defaults try gconftool --dump /apps/panel/default_detup > panel.xml ; gconftool --load panel.xml /apps/panel or something like this.

---

### Post by nothingspecial on 2008-08-09
In plain english -

Click on Places

Click Home folder

Press ctrl  + H at the same time

Look for .gconf and click it

Click  apps

Look for panel and right click on it

Send it to the deleted items folder

Press ctrl + alt + backspace

Log back in.

---

### Post by ggaaron on 2008-08-09
Please don't be rude. I'm not even sure if gconf directory removal will help, I remember being frustrated several times when it changed nothing.

---

### Post by sisco311 on 2008-08-09
> **nothingspecial said:**
> In plain english -

Click on Places

Click Home folder

Press ctrl  + H at the same time

Look for .gconf and click it

Click  apps

Look for panel and right click on it

Send it to the deleted items folder

Press ctrl + alt + backspace

Log back in.

Thanks. It's 2:10am here and my English is weak.:oops:

---

### Post by nothingspecial on 2008-08-09
> **ggaaron said:**
> Please don't be rude. I'm not even sure if gconf directory removal will help, I remember being frustrated several times when it changed nothing.

Hey, not being rude.

When I started this crazy venture I`d have had no idea what -

"try to rename(delete) the config folder (~/.gconf/apps/panel)
and let the system to recreate the default panels."

meant, backed up by the subsequent post -

"I am unsure as to how to do that."


If only every answer on the absolute beginner forum was in plain english!

---

### Post by mcbagpipe89 on 2008-08-09
I deleted the folder you recommended, but upon restart, the panels were still absent.  Is there a step I am missing?

EDIT: restart-meaning, ctrl+alt+backspace

---

### Post by nothingspecial on 2008-08-09
I`m at a loss here. But if your system were my system I might try deleting the file "gnome-panel".
This is located in .gconf > apps > gnome-settings
Remember you have to press ctrl + H to see the hidden files.
Sorry if I`m being too simplistic.

---

### Post by ggaaron on 2008-08-10
OK, I probably overreacted as the previous message was clear enough for me, sorry.

Really - you should try with gconftool and --dump, --load. This works for sure and will load default settings, only I don't remember the load syntax and it is not in the manual, and I don't want to try and destroy my panels configuration=)

---

### Post by mcbagpipe89 on 2008-08-10
Thank you both for your help, I restarted the whole machine, and the panels were back (seems that ctrl-alt-backspace wasn't enough)

---

### Post by nothingspecial on 2008-08-10
Glad to hear it!:):guitar:

---

### Post by SlushieGute on 2008-08-11
Hey alrighty this is my first attempt at using Ubuntu or any Non-windows system for that matter. i installed from a Live CD and it worked very well for first two days then when i installed updates both my top and bottom panels were gone.  ive tried reading through posts that recommend ALT+F2, SHIFT+F9, and a few others. I when i do those nothing happens. only thing i can do is Press F1 for help really.

any help appreciated :)

---

### Post by ggaaron on 2008-08-11
Do you remember what updated did you install? It shouldn't happen. Have you altered panels configuration - added new applets, installed and added new applets after default installation? And what updates do you have on (testing, unsupported)?

If you haven't done anything that you want to keep then you can press alt+ctrl+F1 to get to text console, give it your login and password and then remove all user configuration by: rm -drf * .* this will REMOVE ALL FILES IN YOUR HOME FOLDER. If you want to keep your files and you don't have any hidden files in home that are important to you, you can do: rm -drf .* this will remove all hidden files including configuration that will be reset after restart. If you'd like to follow this steps, then at best don't login into GNOME while doing this, stay in the login screen and login afterwards.

---

### Post by SlushieGute on 2008-08-11
Hey thanks a lot ill give that a try i hadn't seen that Key combo yet. i don't have files stored on my home folder yet, but nothing will happen tot the windows files on my windows partition right?

and no im not sure what update i installed. after i installed Ubuntu from the CD it automatically searched for updates and there were like 254 of them i think.

---

### Post by ggaaron on 2008-08-12
When you login, you will be transported to your home folder and this commands will remove everything there, anything outside will be untouched, so if you don't have windows partitions mounted somewhere in home then nothing will happen. I forgot - to go back to graphical mode use alt+ctrl+F7

---

### Post by SlushieGute on 2008-08-12
ok i tryed punching in rm -drf*.* as well as rm -drf.* and it replys 

rm: invalid operation -- *
Try 'rm --help' for more options

what now? lol and thanks again for all the help

---

### Post by ggaaron on 2008-08-13
Mind the spaces=)
rm -drf[space]*[space].*

---

### Post by SlushieGute on 2008-08-13
haha ok i tried that and it says it cannon delete directories '.' or '..'

any other ides? :)

---

### Post by ggaaron on 2008-08-13
It should be done, it couldn't delete . and .. (they stand for current directory and upper directory), ignored them and did the job=) If you'd like to see what is left from your home directory the command is 'ls -al'.

---

### Post by SlushieGute on 2008-08-13
ah im sorry i forgot to post that last time. i restarted everything and nothings seems to have changed. all i can really do is right click and use F1 lol

sorry this is such a pain and thanks again for all your help.

is there any way to remove ubuntu and reinstall it? will that maybe work?

---

### Post by ggaaron on 2008-08-13
It should have worked, if it didn't then probably you've used some testing/unsupported updates and it is a bug that can't be dealt with without reinstalling older versions of software.

To reinstall ubuntu just install it one more time over the old installation.

---

### Post by SlushieGute on 2008-08-13
alrighty ill give that a try. thanks for all the help im not sure what i did wrong but ill be more careful haha

---

### Post by starcannon on 2008-08-13
I wrote a little how to
[[COLOR="DarkOrange"][SIZE="4"]Restore gnome-panels Guide[/SIZE][/COLOR]]("http://ubuntuforums.org/showpost.php?p=5578191&postcount=10")

Enjoy

---

