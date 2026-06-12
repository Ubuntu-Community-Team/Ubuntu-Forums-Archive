---
title: "[SOLVED] useragent, change"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by freeediver on 2008-10-31
I am having trouble with hotmail like lots of others, it seems to be a useragent problem
I am using FF 3.03
I need to change the useragent from Ubuntu to Firefix permanently.
I can change it but when I end the session the Ubuntu value returns
and hotmail quits.
Does anyone have a permanent fix for this issue?

---

### Post by kerry_s on 2008-10-31
it should stick unless you got permission problems in your profile.
ever run firefox with sudo? there is never a need to.

gedit ~/.mozilla/firefox/*.default/user.js

put:
user_pref("general.useragent.vendor", "Firefox/3.0.3");

restart ff

---

### Post by freeediver on 2008-11-01
I guess this is run in the terminal window?
Can you give a step by step?
If I enter the first command sudo(?) line then do I erase it when the new string appears and replace it as you suggest or do I  just add your new command then hit enter?

Second and maybe more important:
Who owns this problem, it's to wide spread.
Is the an Hotmail issue or:
Ubuntu
Mozilla, FF
Msn?
I would think if either Ubuntu or FF owned the ability
to rewrite the fix that it should have been done by now.
If it's only one line to fix replace how tough can it be
to fix it with an update once they know the problem exists?

---

### Post by kerry_s on 2008-11-01
> **freeediver said:**
> I guess this is run in the terminal window?
Can you give a step by step?
If I enter the first command sudo(?) line then do I erase it when the new string appears and replace it as you suggest or do I  just add your new command then hit enter?

Second and maybe more important:
Who owns this problem, it's to wide spread.
Is the an Hotmail issue or:
Ubuntu
Mozilla, FF
Msn?
I would think if either Ubuntu or FF owned the ability
to rewrite the fix that it should have been done by now.
If it's only one line to fix replace how tough can it be
to fix it with an update once they know the problem exists?

no, no, never use sudo in your home directory is what i was saying. if you use a program such as firefox using sudo it screws up the permissions. you then won't be able to make changes because you no longer have permission. i simply asked if you have already done that, that could cause your settings to not be changeable. 

here's the steps:

press alt+f2 
type> gedit ~/.mozilla/firefox/*.default/user.js

copy and paste> user_pref("general.useragent.vendor", "Firefox/3.0.3");

hit enter(in text files, always leave a blank line as the last line)
then close
restart firefox

---

### Post by freeediver on 2008-11-02
Thanks I will give that a try.
I change very little but I might have tried using sudo commands in the past but 'm not really sure. If I did is there any way to restore permissions, IE undo the damage? IIRC installing google earth needed a sudo command in the terminal window.

Will I need to print out these inst. to install the commands you suggest or will I still have access to this window after I click Alt+f2

Will this command restore all my permissions?  [http://ubuntuforums.org/showthread.php?t=907882&highlight=restore+permissions](http://ubuntuforums.org/showthread.php?t=907882&highlight=restore+permissions) I'm using Hardy
sudo chown edzell:edzell -R /home/edzell 
Of course using my logon.
Thanks

---

### Post by kerry_s on 2008-11-02
> **freeediver said:**
> Thanks I will give that a try.
I change very little but I might have tried using sudo commands in the past but 'm not really sure. If I did is there any way to restore permissions, IE undo the damage? IIRC installing google earth needed a sudo command in the terminal window.

Will I need to print out these inst. to install the commands you suggest or will I still have access to this window after I click Alt+f2

Will this command restore all my permissions?  [http://ubuntuforums.org/showthread.php?t=907882&highlight=restore+permissions](http://ubuntuforums.org/showthread.php?t=907882&highlight=restore+permissions) I'm using Hardy
sudo chown edzell:edzell -R /home/edzell 
Of course using my logon.
Thanks

alt+f2 only brings up a run dialog 
don't worry about permission problems, if you come across that will just delete the .mozilla folder and let it create a new one.

---

### Post by freeediver on 2008-11-02
Ok
What happens if Rather than modify the useragent value I select 
New string will that line simply be overwritten? Would that new value hold, ie the string replaced ? Can I just select new string and enter this line ?
general.useragent.vendor;Firefox
I don't like to press buttons until I have some idea what to expect or a way to undo the damage?
I'm slow to make changes.
I tried the useragent switcher plugin and it did not work for me.
I downloaded it and installed per the inst(?) It never worked and I tried all three selections. I uninstalled it with the package manager but the selection still remains in my tools menu, whats up with that?[COLOR="Red"]OK I figured out the uninstall[/COLOR]

Thanks

---

### Post by kerry_s on 2008-11-03
> **freeediver said:**
> Ok
What happens if Rather than modify the useragent value I select 
New string will that line simply be overwritten? Would that new value hold, ie the string replaced ? Can I just select new string and enter this line ?
general.useragent.vendor;Firefox
I don't like to press buttons until I have some idea what to expect or a way to undo the damage?
I'm slow to make changes.
I tried the useragent switcher plugin and it did not work for me.
I downloaded it and installed per the inst(?) It never worked and I tried all three selections. I uninstalled it with the package manager but the selection still remains in my tools menu, whats up with that?[COLOR="Red"]OK I figured out the uninstall[/COLOR]

Thanks

the user.js that we did above overrides all, you'll need to delete that file then restart firefox, then you can manually change it again.
[http://kb.mozillazine.org/User.js_file](http://kb.mozillazine.org/User.js_file)

---

### Post by freeediver on 2008-11-04
I have no idea what happened or even if I did anything to cause it but Hotmail is now working.
On to my next challenge, Evolution Mail.
Thanks for the help and advice, I have this thread saved.

---

