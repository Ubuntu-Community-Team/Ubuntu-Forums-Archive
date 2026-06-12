---
title: "After editing with non-writing permission vim changes user owner"
date: 2014-08-09
forum: New to Ubuntu
---

### Post by totito on 2014-08-09
Hi guys!!!!
My name is totito or toto and im new at the community :D as well as in gnu-linux
I am learning some basics commands and encountered myself with a little problem when editing files with vim (dont worry took some screens)
It goes like this:
1_ Created TEST directory = owner ROOT - group ROOT
2_ chmod 777 TEST
3_ Created file TEST/trimester_sales.txt = owner PEDRO (just some random names I created to practice) - group PEDRO
4_ chmod 664 trimester_sales
5_ Added trimester_sales to oficina1 group
6_ Edited the file with VIM by another user member of oficina1 group = PABLO
7_ On the screen you guys can check I ID to alba and nerea (two other users not members of oficina1 group) to show they dont really belong to this group
8_ Tried to write the file with VIM using ALBA user
9_ VIM lets me force the writing using the " ! " character
10_ Once the trimester_sales file was edited using VIM the owner and group has changed to ALBA's

¿How can be this possible? User alba only had permissions to read the file not writing it or executing it!!!!

Hope you guys can help with this one... im started  to love linux already

Thank you so much in advanced!!!!! 


edit: wow didnt know i had a 5 limit screens to attacht... ok i'd attached the las 5 caps :D


[ATTACH=CONFIG]255336[/ATTACH][ATTACH=CONFIG]255335[/ATTACH][ATTACH=CONFIG]255337[/ATTACH][ATTACH=CONFIG]255338[/ATTACH][ATTACH=CONFIG]255339[/ATTACH]

---

### Post by totito on 2014-08-09
Ok guys... think I found it :D just removed writing permission from TEST directory and that was it, out of the oficina1 group noone else (exept for root) can modfy the file!!!!!!!!!!!
Tried with sticky bit first though but removing it got the same result so no need for using it :D

---

### Post by Impavidus on 2014-08-09
Without writing permission user alba couldn't write to the file, so ordinary writing doesn't work. But the directory /home/TEST has write permission for everyone, so user alba has permission to delete files from that directory. When you forced writing of the file by user alba, vim deleted the original file and created a new one with the same name, but now with owner alba and the new contents.

---

### Post by totito on 2014-08-09
Yeah Imapvidus that is what i realized... but now when I remove writing permission from TEST no one else would be able to write to that directory
I was able to get denial writing permission to the file using sticky bits on TEST but no other user is allowed to create new files in that DIR either... so How can I let any user to create files inside TEST but not be able to write on files haven't been created by them if TEST directory doesnt have writing permissions?

Thx in advanced guys :D

---

### Post by Impavidus on 2014-08-09
For that the TEST directory must have full permissions and the sticky bit. Those are the same permissions as those of /tmp. Then all users are allowed to create files in TEST, but can delete only the files they own. For modifying you can use the permissions for owner, group and others of the file just as usual, but users without write permission for the file can lo longer delete it and replace it with another file with the same name.```
sudo chmod 1777 /home/TEST
```

By the way, instead of posting screenshots of a terminal, it's easier to copy the contents of that terminal into your post. Best to do it in [noparse]```
code tags
```[/noparse].

---

