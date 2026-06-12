---
title: "HOW-TO: Creating a Trashcan for CLI"
date: 2005-12-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Unrivaled on 2005-12-12
Hey guys!
I just deleted something that I needed, so I decided to make a trash can type deal for the command "rm".

To do this, rename your [COLOR="Blue"]/bin/rm[/COLOR] file to something else, like [COLOR="Blue"]/bin/rm.bak[/COLOR].
**$ sudo mv /bin/rm /bin/rm.bak**

Download the attached file [COLOR="Blue"]rm.txt[/COLOR] and stick it in your [COLOR="Blue"]/bin[/COLOR] directory. (Rename it from [COLOR="Blue"]rm.txt[/COLOR] to just [COLOR="Blue"]rm[/COLOR] . I'm sorry, it wouldn't let me upload just [COLOR="Blue"]rm[/COLOR].
**$ sudo mv *path_to_downloaded_rm*/rm.txt /bin/rm**
(Note: be sure to change the *path_to_downloaded_rm* to the path that you downloaded rm to)

Change the mode to be executable and readable and that garbage.
**$ sudo chmod 755 /bin/rm**

Create a trash directory:
**$ sudo mkdir /trash**

Now, you can do a couple things here; make the trash can so only root can view the files contained within (useful for when there are multiple users and you don't want another user being able to see what you deleted) or you can just allow everyone access to the trash can.

Only root can view trash:
**$ sudo chmod 733 /trash**

Anyone can view trash:
**$ sudo chmod 777 /trash**

*Note: the first number is owner, second is owner's group, third is others. 4 is for read access, 2 is for write access and 1 is for execute permission. You add together the numbers to give the permission. For example, 7 is 4+2+1, 4 being read, 2 being write, and 1 being execute.*

The way this command works now is that instead of simply deleting the file, it will move it to the trash directory. If there is already a file called that, it renames the file that is already there to file.1, and so on up to file.7

The only draw-back is that you can't [COLOR="Blue"]rm[/COLOR] anything that's in the trash, you have to rm.bak it.

Please post any corrections as it's been a long day at work. I'm also not responible for any damages this file or... for anything really. Use at your own risk.

---

