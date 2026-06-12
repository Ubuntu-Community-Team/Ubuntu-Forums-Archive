---
title: "deleted .filename from home!"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2012-02-07
for example i performed following in ubuntu 10.04:-
=>downloaded jdownloader via synaptic package manager!
=>i did not find it good and and performed complete removal via synaptic!
=>opened home via nautilus!
=>hit Ctrl+H for hidden files and still see .jdownloader folder!
=>i wished it's complete removal already, still it's there, what the heck!
=>selected the folder and hit delete!

so, is this causing any problem if i wish to download jdownlaoader in future? not a big deal you may guess but i'm rather interested in learning how ubuntu works. your help would be appreciated!

---

### Post by wojox on 2012-02-07
Right Linux does not touch anything in your /home directory.

Will it effect a future download if you don't delete them? 
It should get overwritten.

---

### Post by yetiman64 on 2012-02-07
> **tojonukokhadush said:**
> for example i performed following in ubuntu 10.04:-
=>downloaded jdownloader via synaptic package manager!
=>i did not find it good and and performed complete removal via synaptic!
=>opened home via nautilus!
=>hit Ctrl+H for hidden files and still see .jdownloader folder!
=>i wished it's complete removal already, still it's there, what the heck!
=>selected the folder and hit delete!

so, is this causing any problem if i wish to download jdownlaoader in future? not a big deal you may guess but i'm rather interested in learning how ubuntu works. your help would be appreciated!
A complete removal removes the program AND its configuration files (in the root filesystem) from the install. What it doesn't remove are the user specific configurations (stored in the home folder) as you have noticed, this is so next time (if there is one) that you install the program it will be already set up for you as you like.

If you need a complete uninstall, possibly for repairs to a misbehaving program, the home folder hidden settings for the program must be removed as well (as you have done).

Doing what you have done is perfectly normal, in fact when I do a complete removal, if I have no intention of ever reinstalling the program, I do what you describe above. Just note not all programs use an individual hidden folder of their own, quite a few use the .config and .cache (more for log files / xml settings files etc) folders for their settings/configuration. **Edit**: never delete either of these 2 (config and cache) as many other programs can use them, dig further into the filesystem specifically for your programs folder.

Hope this helps you (and makes sense :)),
yetiman64

---

### Post by tojonukokhadush on 2012-02-07
thanks yetiman(hey, not that yeti was supposed to be in my country and not in australia? ;-) )

yeah, i now got why even after the complete removal of any software and reinstalling it later used to bring back the same undesired setting! interesting!
so what i need to get is that if i need to refresh my previous setting as well along with the complete removal of any application, i need to do what i mentioned at first hand, right?

what i need to still understand to quench my curiosity is, am i supposed to delete .bash and alike files without the system to end up breaking?

thankyou again!

---

### Post by yetiman64 on 2012-02-07
> **tojonukokhadush said:**
> ...
so what i need to get is that if i need to refresh my previous setting as well along with the complete removal of any application, i need to do what i mentioned at first hand, right?....If you need to refresh the previous settings, yes.

If you were happy with your previous setup, you can leave all alone and on the next installation those settings will be used.

> **tojonukokhadush said:**
> ...what i need to still understand to quench my curiosity is, am i supposed to delete .bash and alike files without the system to end up breaking?

thankyou again!
**No**, please don't touch (read that as delete) the hidden files for bash, profile or any other hidden file directly in the home folder. You will most likely break your user profile and may not be able to get back to a desktop after logging out/rebooting (depending on what you remove or alter).

Only alter these files "under advice", for the purpose of fixing a specific problem at the time. Those files are very important.

---

### Post by tojonukokhadush on 2012-02-08
thankyou yetiman! 
i haven't touched them and not will either now!

---

