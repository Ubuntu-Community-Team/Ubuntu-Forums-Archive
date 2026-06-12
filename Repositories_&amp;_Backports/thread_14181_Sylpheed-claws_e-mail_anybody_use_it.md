---
title: "Sylpheed-claws e-mail anybody use it?"
date: 2005-02-05
forum: Repositories &amp; Backports
---

### Post by Yukonjack on 2005-02-05
Would like to replace evolution since it is not my cup of tea. 
I have read the features on the Sylpheed-claws website and really like the features in it. 
I was just wondering if anyone is using this e-mail program and if you do how do you like it? 
I am really curious about this one. All comments are welcome good or bad. 
Thanks!

---

### Post by RichardA on 2005-02-08
Yup.

I used Sylpheed on Mandrake for years, though I never saw the need to use the Sylpheed-claws development branch.

I'm currently using Sylpheed-gtk2 (I think that's the name - posting from work), as it fits the look of the desktop better.

Sylpheed is lightweight, very quick and deals easily with folders holding many thousands of email messages. I especially like the mail format it uses - a folder structure the same as the one in the program view, and each email in it's own file (the files are named '1', '2', etc.). When you have all your mail in one mbox format file, it seems to me that if it corrupts, you lose the lot (backups excepted).

I converted my old mail over with a simple script I found on the web, and it seems to me that this fits the Unix philosophy well - 'everything is a file', etc.

---

### Post by Yukonjack on 2005-02-08
Yes I was also looking at Sylpheed-gtk2 and I will give this one a go. Looks like the one for me. I do have a lot of mail to transfer/convert over from Evolution if it's possible could you post the script for converting my mail. I do agree that the mbox format is not the greatest. 
I remember trying evolution back in Gnome 2.4 but at the time it didn't support pop3 accounts, but now with Ubuntu and the new Gnome I tried it again and I am not impress, uses to many resources/processes for an e-mail program.

Thanks for your feedback Richard!

Update: Ok installed and works great I like it just what I was looking for, man it is ever fast  :mrgreen:

---

### Post by RichardA on 2005-02-08
I don't have the script -- it was five years ago I used it.

The Sylpheed format is called MH, and this might work:
[http://cvs.sourceforge.net/viewcvs.py/sylpheed-claws/sylpheed-claws/tools/convert_mbox.pl?rev=1.4](http://cvs.sourceforge.net/viewcvs.py/sylpheed-claws/sylpheed-claws/tools/convert_mbox.pl?rev=1.4)

This claims to convert from maildir to MH (maildir uses separate files per message, but is more complicated. I can't remember what uses it):
[http://cvs.sourceforge.net/viewcvs.py/sylpheed-claws/sylpheed-claws/tools/maildir2sylpheed.pl?rev=1.3&view=log](http://cvs.sourceforge.net/viewcvs.py/sylpheed-claws/sylpheed-claws/tools/maildir2sylpheed.pl?rev=1.3&view=log)

... and I've just noticed 'import from' and 'export to' mbox entries on the file menu of Sylpheed 0.9.9-gtk2-20040229, so there should be no need for a script any more!

Oh, and WORK ON A COPY OF YOUR MAIL!! :-)

---

### Post by Yukonjack on 2005-02-08
[QUOTE=RichardA]I don't have the script -- it was five years ago I used it.

The Sylpheed format is called MH, and this might work:
[http://cvs.sourceforge.net/viewcvs.py/sylpheed-claws/sylpheed-claws/tools/convert_mbox.pl?rev=1.4](http://cvs.sourceforge.net/viewcvs.py/sylpheed-claws/sylpheed-claws/tools/convert_mbox.pl?rev=1.4)

This claims to convert from maildir to MH (maildir uses separate files per message, but is more complicated. I can't remember what uses it):
[http://cvs.sourceforge.net/viewcvs.py/sylpheed-claws/sylpheed-claws/tools/maildir2sylpheed.pl?rev=1.3&view=log](http://cvs.sourceforge.net/viewcvs.py/sylpheed-claws/sylpheed-claws/tools/maildir2sylpheed.pl?rev=1.3&view=log)

... and I've just noticed 'import from' and 'export to' mbox entries on the file menu of Sylpheed 0.9.9-gtk2-20040229, so there should be no need for a script any more!

Oh, and WORK ON A COPY OF YOUR MAIL!! :-)[/QUOTE]

Thank you for you time
 I just noticed the feature, mail backup and will give this import a go. Got my gpg keys working also.

---

### Post by Yukonjack on 2005-02-08
I'm happy to say the import feature works great. Very nice e-mail program. ;-)

---

### Post by Jspired on 2005-02-08
I use it from time to time.  Nice app!

---

