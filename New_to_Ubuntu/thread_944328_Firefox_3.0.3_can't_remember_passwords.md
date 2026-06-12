---
title: "Firefox 3.0.3 can't remember passwords"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by webbie180 on 2008-10-11
Just upgraded to firefox 3.0.3, seems unable to remember passwords, anyway to solve this?

---

### Post by ashmew2 on 2008-10-11
You checked under Edit > Preferences ?

---

### Post by webbie180 on 2008-10-11
Yes, all passwords are saved and I can see them...but each time I restart firefox, have to login again for all my sites.

---

### Post by silkstone on 2008-10-11
Check the Cookies settings under Edit > Preferences > Privacy. They should be kept until they expire. It's possible that the current setting is to keep them until you close Firefox, in which case you'll have to log in again each time you restart FF.

---

### Post by webbie180 on 2008-10-11
Checked the cookies...yes it is kept till expired...

---

### Post by epidemiks on 2008-10-11
is it set to clear private data when firefox is closed?

---

### Post by webbie180 on 2008-10-11
Not set to clearing of private data when firefox is closed...seems I'm the only having this problem....have it for a couple of days since upgraded firefox.

---

### Post by epidemiks on 2008-10-11
perhaps clear everything yourself - cookies/cache/private data etc, restart and test.

or backup your bookmarks, and remove/reinstall ff

---

### Post by silkstone on 2008-10-11
Mmmm... I wonder if there are two sets of config files - one from the old installation, and it's getting confused.

Look under ~/.mozilla and make sure there is only one folder for Firefox. If there's also a Firefox2 folder (or something similar), delete it.

If that's OK, open the Firefox folder and delete the profiles.ini file. (It will be recreated next time you start FF.)

If still no joy, try deleting the xxxx.default folder. That will also lose all your bookmarks and add-ons, but it should ensure that any legacy issues are removed. You may have to reinstall FF after this.

---

### Post by aysiu on 2008-10-11
Try this.

**Step 1**
Close Firefox completely.

**Step 2**
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R $USER:$USER ~/.mozilla
```

**Step 3**
Start Firefox again and see if that fixed your problem

---

### Post by webbie180 on 2008-10-12
Still unable after trying all of the above.
Guess it's not fixed for all cases with firefox 3.0.3, have to wait for the next version 3.0.4 to have this fixed.  Thanks to all.

---

### Post by webbie180 on 2008-10-13
Solved by deleting "cookies.sqlite" under firefox.

---

### Post by paulstone on 2008-10-13
Can't understand why you use FF 3.x - the 2.x versions are much better in my opinion, everything seems to go much faster and you don't have to manually delete files to make things work.

FF 2.x forever - or at least until 3.x become as fast as good old 2.x :)

---

