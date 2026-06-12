---
title: "[SOLVED] Firefox Bookmarks"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by wstay on 2008-11-15
I recently updated my Ununtu8.04 through the internet and after that all the sites that I bookmarked before disappeared from my bookmarks menu.
Is there a way to get the sites that a bookmarked before back from my computer.

---

### Post by lisati on 2008-11-15
This might not be of direct help in your current situation, but might be worth checking out for the future:
I use the "Foxmarks" add-on for Firefox. That way the bookmarks on my various machines are kept in sync, and if I ever need to do something that would clear the bookmarks on one machine, there's a relatively painless way of getting them back.

---

### Post by tvtech on 2008-11-15
google offers a similar sync for bookmarks and preferences within firefox over multiple work stations.

---

### Post by tvtech on 2008-11-15
as far as rescuing your old book marks, sorry to say that I think your SOL mate.  I've had the same problem a couple of times.  but most of my book marks have to do with fixing problems on an install so it's never mattered much.

---

### Post by asgard_command on 2008-11-15
I always keep a backup of my bookmarks folder in case I want to move them to another computer.
If you did a clean instal of the new version there is nothing you can do, if you just did an upgrade your bookmarks would normally have been carried over.
You could look in the .mozilla/firefox folder in your home directory and see if there is an older profile with a bookmarks file or any old backups that firefox has created which you could then import into your new profile.

---

### Post by cariboo on 2008-11-15
Check in ~/.mozilla to see if a new profile was created. If there are two, the bookmark files are called bookmarks.html, check them in Firefox to see which one is which. If one of them is your old bookmark file, use Bookmarks-->Organize Bookmarks-->Import and Backup-->Export HTML to restore your bookmarks.

Jim

---

### Post by wstay on 2008-11-15
> **cariboo907 said:**
> Check in ~/.mozilla to see if a new profile was created. If there are two, the bookmark files are called bookmarks.html, check them in Firefox to see which one is which. If one of them is your old bookmark file, use Bookmarks-->Organize Bookmarks-->Import and Backup-->Export HTML to restore your bookmarks.

Jim

> 

Thanks, I got it.

---

### Post by wstay on 2008-11-15
Where can I find this post or thread under Quick Links?
Why it does not appear under Subscribed Threads?

---

### Post by wstay on 2008-11-15
I found an answer to this myself.
Use Search and Find All Your Threads

---

