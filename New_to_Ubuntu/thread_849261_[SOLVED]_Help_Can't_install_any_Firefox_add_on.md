---
title: "[SOLVED] Help: Can't install any Firefox add on"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by imjscn on 2008-07-04
I didn't do anything strange but suddenly can't install any add on. I followed Firefox's support page...allow xpi install, enable cache, delete profile, delete everything, clean install, changed to Firefox2, changed back to firefox3...nothing works. Please help.

Edit: I disabled NoScript before the bad luck.

---

### Post by nowshining on 2008-07-04
if u disable noscript make sure to press f5 to reload the page. :)

---

### Post by dodle on 2008-07-04
Try this:  Close firefox and go to ~/.mozilla/firefox/dl1afknk.default.  Delete the files named "extensions.cache", "extensions.ini", and "extensions.rdf".  There might be another file named "extensions.somethingorother", go ahead and delete that too.  Restart firefox and see if you can install extensions.

P.S.  I'm not sure if the folder "dl1afknk.default" is named the same on everyone's computer, but you need to go into the folder that has the ".default" extension.

---

### Post by silkstone on 2008-07-04
You could also delete pluginreg.dat which is recreated when FF starts.

---

### Post by aysiu on 2008-07-04
Make sure you own your own settings folder by typing this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username*:*username* /home/*username*/.mozilla
``` where *username* is your actual username.

---

### Post by imjscn on 2008-07-04
thanks for helping!
I deleted those extension.xxx files, and the pluginreg.dat, restart firefox, it's still not working. the error message is 261, invalid file hash, posible file download corruption. 

.mozilla is in my home directory but this code:
 sudo chown -R me:me /home/me.mozilla
returns the result: can't access "/home/me.mozilla": no such a file or directory.

???

---

### Post by dodle on 2008-07-04
> **aysiu said:**
> Make sure you own your own settings folder by typing this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username*:*username* /home/*username*.mozilla
```
I think aysiu ment to put /home/username[COLOR="Red"]/[/COLOR].mozilla not /home/username.mozilla

---

### Post by nowshining on 2008-07-04
or better yet just put /home/username - change username to ur username.

oh and ur pw won't show up as you type.

---

### Post by imjscn on 2008-07-04
thanks, after type in the correct sudo...mozilla, it returns nothing, that means I'm the owner of this folder.
what to do next?
I'm feeling like a ant running on a hot hot pot, because I use PasswordMaker extention to manage all my passwords for a long time, I can't live without it.

---

### Post by cariboo on 2008-07-04
If you still start Firefox just export your bookmarks and then delete the complete .mozilla directory, the next time you start Firefox it will create a new directory.

Don't forget to import your bookmarks, and you will have to reisntall all the addons.

Jim

---

### Post by imjscn on 2008-07-04
I deleted .mozilla directory yesterday, it doesn't work.

I also completed removed Firefox, then delete .mozilla, then install , it doesn't work either.

The only thing I ddin't remove yesterday was the xulrunner-1.9 and Java plugin.

---

### Post by imjscn on 2008-07-04
Now I completely removed everything again, including Firefox and all the plugins and xulrunner and java. and manually deleted .mozolla
Reinstalled Firefox2, still not working.
Removed Firefox2, installed Firefox3, ubufox and xulrunner. still not working.
The error message is 261, invalid file hash, possible download corruption.

I belive it's not a download problem, coz all the add on get the same error message.

---

### Post by imjscn on 2008-07-04
I decide not to troubleshooting it. I manually installed all the add ons following this instruction:
[http://www.accessfirefox.org/Install_Addon_Manually.php](http://www.accessfirefox.org/Install_Addon_Manually.php)
Things are working perfectly. Thanks God I have a backup of all my add ons.

Thanks for all the helping!!!

---

### Post by nowshining on 2008-07-05
u could of just in the Terminal - 

```
firefox -profilemanager
```

and created a new profile there :) - u can also add that manually into ur start menu in the command box so u won't have to go thru the Terminal Next Time. :) - I mean not the run box - but as an menu item, etc..

---

### Post by imjscn on 2008-07-05
Thanks! I'm the happy FFubuntuee now :guitar:
Hope I won't have this problem again.

---

