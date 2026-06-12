---
title: "Export Import Tomboy Notes"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Andavane on 2008-06-10
I use grsync for moving my work data to an external hard drive, and grsynch again to import to my laptop, so I can work at my desktop, or work mobile.

Now I export my tomboy notes to my data (they go to an html file) but I seem unable to import them to my laptop. I see from searching the documentation that one can import from sticky notes (which I haven't yet tried) but was wondering if there was a simpler way to reproduce my tomboy notes from one machine to another.

So far my searches have been in vain.

Regards

John

Gutsy Gibbon

---

### Post by y-lee on 2008-06-10
Have you tried just copying the note from the tomboy folder itself? It is a hidden folder found:

```
/home/username/.tomboy
```


where **username** is your own username in ubuntu.

---

### Post by The Cosmic Hobo on 2008-06-10
According to a review of Tomboy in this month's Linux Format magazine, notes opened that way have random alphanumeric names, and it currently doesn't have an import function. However, it is only v0.10.0 (as far as I know) and will probably improve.
The article also points out that you can synchronise your notes to a remote server with WebDav. I don't know if this is any help, but it sounds like you may be able to set up some kind of synch system that way - sadly it's outside of my technical know-how so I can't really say any more.

---

### Post by y-lee on 2008-06-10
> **The Cosmic Hobo said:**
> According to a review of Tomboy in this month's Linux Format magazine, notes opened that way have random alphanumeric names, and it currently doesn't have an import function. However, it is only v0.10.0 (as far as I know) and will probably improve.
The article also points out that you can synchronise your notes to a remote server with WebDav. I don't know if this is any help, but it sounds like you may be able to set up some kind of synch system that way - sadly it's outside of my technical know-how so I can't really say any more.


Interesting never tried it and didn't know about it, so thanks for bringing it to my attention. For  those interested I found a short article on this that looks promising, [Synchronizing Tomboy Notes with WebDav on Ubuntu 7.10 Gutsy Gibbon]("http://blog.vaxius.net/?p=18")

---

### Post by Andavane on 2008-06-11
> **y-lee said:**
> Have you tried just copying the note from the tomboy folder itself? It is a hidden folder found:

```
/home/username/.tomboy
```


where **username** is your own username in ubuntu.

Thank you.
I located the .tomboy folder. Using ctrl-h, 

 I have copied the contents, dropped them into a file on the desktop, made a tarbal then emailed the file to myself, downloaded onto the laptop, unzipped, copied the contents to clipboard, then  deleted contents of .tomboy  in home folder, pasted in the new contents.
It was necessary to reboot, and my tomboy noptes have all appeared!
Thank you... It is a little cumbersome and of course I would like to know  a slicker way to do this. Any ideas?
I don't have a server, just a desktop and a laptop, and use grsynch between the two.

By the way, if I copy the .tomboy folder and paste onto the desktop, I cannot see it, even although I know it is there.

Regards

John

---

### Post by Vadi on 2008-10-27
The desktop doesn't display the hidden (prefixed with a dot) folders.

But thanks for this tip, I'll be upgrading myself and needed a way to copy over the notes.

---

### Post by rj_steinert on 2010-09-07
I'm on Ubuntu 10.04.  Moving my .tomboy folder to my user's home directory probably would have worked but it looks like I did it the hard way by creating folder to 'Sync' to in the Tomboy preferences, copying all my old *.note files to that directory, syncing in the Tomboy preferences, logging out, and then logging back in.  Should definitely set up the web sync.

---

### Post by 1231232231231231 on 2011-06-30
Okay, I'm so happy I get to help out!!:KS

But basically "exporting" your tomboy notes for backup and "importing" them into your new system is way easier than whats been discussed above. Its just an issue of copying and pasting files from the /user/.local/share/.tomboy file on one system into the other. Note: to access .* files go to "View" and click "show hidden files"...

Since were all newbies, Ill go through the steps:

So, when you do your backup, make sure to include /user/.local/* file, this file includes your tomboy notes which are encoded in alphanumeric jibberish.

Then on your new system, copy and paste the tomboy files from your backup (which would be located for example here: externaldrive/backup/user-dateofbackup/user/.local/share/.tomboy/ ) into the exact same file on your new system ( /user/.local/share/.tomboy/) then close tomboy and reopen it again and all your notes will be in the program, and not as jibberish.

Yay!:KS

---

### Post by howlingredog on 2011-06-30
How To Import Sticky Notes into Tomboy. Open new note in Tomboy, click on prefs & import....easy!

---

### Post by markMDW on 2012-02-08
I can't export my notes to HTML from either Ubuntu or Xubuntu [both 10.04].  My add-ins say that this feature is enabled.  BTW, my notes are synchronized on Ubuntu One, so I just edit them either from my laptop or desktop to keep the same.  

I can't find a .tomboy folder under my user name even though I made hidden files viewable.

I want to export my notes or back them up locally.  any advice? Thanks!

---

### Post by dreamingdarkness on 2012-03-17
Probably late but just in case search results bring others to this page looking for how to move Tomboy notes.

These are saved in the following directory:
> /home/<username>/.local/share/tomboy

For example, if your user name is markMDW, the Tomboy notes are in:
> /home/markMDW/.local/share/tomboy

You can also find them by searching for files with the ".note" extension.

---

### Post by Andavane on 2012-03-22
> **dreamingdarkness said:**
> Probably late but just in case search results bring others to this page looking for how to move Tomboy notes.

These are saved in the following directory:
For example, if your user name is markMDW, the Tomboy notes are in:
You can also find them by searching for files with the ".note" extension.
Ahhh.. and there was me, hunting away :)
If in doubt, read the final post is the moral there I guess.
This thread had its birth on 12th June 2008.
So as we're nudging into April 2012 it's nearly 4 years old;
Oh my! what a lot of changes the world, ubuntu and tomboy notes have harried through since those earlier days.
Plants the seeds of nostalgia and hope in me.

---

### Post by markMDW on 2012-03-25
I've got my tomboy notes backed up.  Will be moving them to something else, but it will be tough to find something as good! 

For some unknown reason the synchronization with ubuntuOne is broken on my desktop.  It synchronizes on my laptop though.  On the desktop I can set it for Tomboy-Web on the dropdown menu and it replies back: "server not responding, try again later".  Then my setup in configuration preferences disappear.  it just won't synchronize anymore and oddly Firefox is broken too.  

I can connect to websites through bookmarks, but typing a URL out and hitting enter doesn't do anything.  The "busy" connection icon doesn't even spin.  (no real problem - I'm trying out Chrome, Seamonkey and Opera).  [sudo apt-get remove firefox [[and]] sudo apt-get install firefox ] didn't help Firefox btw.      

Back to Tomboy Notes-- I might try re-installing it and see if that helps.  Have a nice day!

---

### Post by momist on 2012-05-15
> **markMDW said:**
> I've got my tomboy notes backed up.  Will be moving them to something else, but it will be tough to find something as good! 


I've just moved to Lubuntu (couldn't get on with that Unity rubbish) and find that something called Osmo is installed by default.  I've never used it, and now I'm looking for a way of getting my Tomboy notes into Osmo without having to install Tomboy on my clean(ish) system.  There doesn't seem to be any "import" option there.

Does anyone have any ideas please?

Ta,  Ian

---

