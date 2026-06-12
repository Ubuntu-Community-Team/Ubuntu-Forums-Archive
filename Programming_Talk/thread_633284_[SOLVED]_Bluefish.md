---
title: "[SOLVED] Bluefish"
date: 2007-12-06
forum: Programming Talk
---

### Post by gary0 on 2007-12-06
Hi all,
I am using bluefish to make webpages with php. It's new to me coming from MS Visual Interdev, I have made some good progress, connecting to a MySQL database and looping through records and displaying them in an html table. Good stuff indeed. My problem is, I can't get the external browser button to open firefox to display the page I am currently editing. I just manually open FF and navigate to the appropriate directory to view it, can anyone help please?

Many thanks,
Gary.

---

### Post by smartbei on 2007-12-06
Here is how I solved the problem (I don't use bluefish, I just downloaded it to see if I could find the problem):

this is assuming you want Firefox as the default browser.

Goto Edit => Preferences => External Programs. Add a new entry. Double click on the new entry and type 'Firefox' (just an identifier). Double click on the white space next to it (under where the other entries have commands) and paste:
```

firefox -new-window %s&

```
Remove all the other entries by clicking on each in turn and deleting it with Delete.

After this the button worked.

Hope this helped!

---

### Post by gary0 on 2007-12-07
Yep, that did it, thanks.

Gary.

---

### Post by gary0 on 2007-12-07
Ok, not quite solved - it works with flat html, but if I try to browse a .php page, firefox gives me the open with / save as dialogue. Any ideas?

Gary.

---

### Post by smartbei on 2007-12-07
The problem is that it is not running through apache/php - it is opening the file locally. What needs to be done is something like a sed script which will convert /var/www (or whatever your web root is) with [http://localhost](http://localhost).

Here is what banging on the keyboard for 15 minutes gives me :D:
```

firefox -new-window $(echo "%s" | sed "s/\/var\/www/http:\/\/localhost/")

```
That should go instead of the previous command I gave you for firefox. Note that if your server root is different from /var/www you will need to change command - /var/www = \/var\/www, /home/testing/apple/cute = \/home\/testing\/apple\/cute. etc. [Those are \ and / close together, not big Vs]

Thanks for providing a fun way to learn a bit of bash :).

---

### Post by gary0 on 2007-12-07
Fantastic! Thankyou muchly.

Gary.

---

### Post by Salosalo on 2008-01-14
Smartbei's solution only works for me if Firefox is already open. If not, it crashes as soon as I hit the "view in browser" button. Maybe some extra "sed"-stuff is needed?

Salosalo

---

### Post by misterdasher on 2008-12-19
> **smartbei said:**
> 
Here is what banging on the keyboard for 15 minutes gives me :D:
```

firefox -new-window $(echo "%s" | sed "s/\/var\/www/http:\/\/localhost/")

```
That should go instead of the previous command I gave you for firefox. Note that if your server root is different from /var/www you will need to change command - /var/www = \/var\/www, /home/testing/apple/cute = \/home\/testing\/apple\/cute. etc. [Those are \ and / close together, not big Vs]

Thanks for providing a fun way to learn a bit of bash :).

And thanks for banging away in bash for a quarter hour.  It's still paying dividends!

Your arguments (modified for my DocumentRoot) worked great.  I also tried replicating Salosalo's problem, but Firefox recognized the command whether it was already open or not.  Of course, it's almost a year later, so whatever package or configuration might have caused the problem may no longer be an issue...

---

