---
title: "[SOLVED] Sansa View File permissions"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by RH9R on 2008-07-05
Feisty has lived w/ Sansa View 16g for months in bliss. I now encounter locked files that I cannot delete. Its a permissions thing, and I've not been able to change with chmod command (I've never been good at it). Is there a way to tell the Sansa that I want all files unlocked? I tried deleting files on the view while unplugged. It appears to delete, but all deleted files continue to show up on file browser when reconnected. 'Would sure appreciate help - its my wife's sansa & this is her first computer w/ Linux

---

### Post by ZabiGG on 2008-07-05
OK. I know absolutely nothing about Sansa View, but I can try to help with permissions.

Let's say your Sansa View folder is /home/your_user_name/SansaView.

Let's say you and your wife are the only people with access to your computer.

You would enter the following in the terminal to change permissions to allow any user to delete the files.

```
sudo chmod 777 /home/your_user_name/SansaView
```

But this means ANY user can modify/delete those files, and it is not recommended.

If you are unsure, enter this instead

```
sudo chmod 775 /home/your_user_name/SansaView 
```

Then, again, in a terminal, enter

```
gksu nautilus
```Click home > your_user_name > SansaView

You will be able to delete all the files you want, but don't forget to empty the trash while you are still root. 

WARNING: Running Nautilus as root (with the gksu command) is very dangerous. You should only do so when ABSOLUTELY needed, as you have the power to delete your entire system with one click. You should exit it as soon as you are done.

Hope this helps,

Z.

---

### Post by linfidel on 2008-07-05
There's a better chance that it's the owner that's set wrong.  Check to see the normal owner for the account that needs access by issuing "ls -l" in a terminal; the third column is the owner.  Then issue "sudo chown -R newOwnerName pathToSansa", where newOwnerName is the owner you see from ls -l, and pathToSansa is the pathname for the Sansa.

Or, if you prefer, issue "gksu nautilus" from the terminal, then highlight the drive and right-click, select properties, Permissions, then owner (and group, while you're at it, usually the same).

---

### Post by RH9R on 2008-07-05
linfidel & Zabigg, I sure appreciate your kind help. 
 
I tried changing owners first, then permissions. When changing permissions, get the error msg: chmod: changing permissions of `/media/SANSA VIEW': Read-only file system
 It almost seems like a device setting. Any other thought would be appreciated. Thank you for your kindness.

---

### Post by ZabiGG on 2008-07-05
> **RH9R said:**
> linfidel & Zabigg, I sure appreciate your kind help. 
 
I tried changing owners first, then permissions. When changing permissions, get the error msg: chmod: changing permissions of `/media/SANSA VIEW': Read-only file system
 It almost seems like a device setting. Any other thought would be appreciated. Thank you for your kindness.

OK. Try this:

```
sudo chown -R newOwnerName:newOwnerName /media/SAN[tab] 
```your pathname is tricky because of the space. A keypress on tab will fill it properly

```
sudo chmod -R 777 /media/SAN[tab] 
```The folder should no longer be read-only after this... I had forgotten the -R for the command to be recursive (apply to all files in the folder)

---

### Post by RH9R on 2008-07-06
ZabiGG, thank you again. I tried the command (great idea about the tab completion!) For one attempt, the 'move to trash' menu option appears, but when given, it says it has an i/o error [Error stating file '/media/SANSA VIEW/AUDIBLE/Bach_Baroque': Input/output error]
 
The returns from the commands look odd:
 changing ownership of `/media/SANSA VIEW/AUDIBLE/Western_Lit/01Foundations/ì}fl&#8976;d3|.r*l/&#9557;}&#9553;.\035&#9568;á/&#9573;ƒ&#8992;[¢&#934;&#966;&#9612;.&#9566;6r/q&#9567;;eñy¿º.\034s2/A&#9561;&#9552;&#966;9\bæ&#8734;.PÇ\031/&#9579;²»m|c\002m. ^ÿ/\034&#9600;eOf_v(.&#9532;9\n/)î&#966;-\006p&#8359;&#963;.)un/&#9557;\035>`\021!)à.\v&#948;&#9492;': Read-only file system

from the chmod command, it went on a long tirade - seeming like a look. I let it go for a full 10 min or so before killing it. I'm starting to wonder if it could be just formatted & go from there. Losing data is not an issue - its all backed up.
 
Again, I sure appreciate your kindness.

---

### Post by RH9R on 2008-07-06
ZabiGG, 'Wanted to let you know I found an option on the view that let me format it - clean slate again. AND all the normal file add/delete commands are now active again.
 
I'm very grateful for your help. Something was obviously wrong w/ the Sandisk unit itself - some more browsing on the sansa view model showed there were numerous other unhappy campers. The posts say that the new 'Fuse' model plays nice w/ Linux - so maybe this will be a better option. 
 
Thank You so much ZabiGG. You're kind & helpful & I hope everyone you help appreciates your kindness.

---

### Post by ZabiGG on 2008-07-06
I'm really happy you found a solution. Great work! :)

The best way to thank me would be to mark your post solved. It helps us help other people whose problems are not solved yet.

Just click on SOLVED in my signature below for short and sweet instructions.

Enjoy your new discoveries,

Z.

---

