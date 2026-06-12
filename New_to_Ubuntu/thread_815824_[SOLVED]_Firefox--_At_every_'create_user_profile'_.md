---
title: "[SOLVED] Firefox-- At every 'create user profile' is starting"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-02
When ever i start my firefox its starting create user profile window.

each time i create it allows me to start firefox.

next time again when i start firefox the window appears again and i shud create user profile to start firefox.

how could i stop this

---

### Post by HotShotDJ on 2008-06-02
> **rraj.be said:**
> how could i stop thisRename .mozilla to .mozilla~

If this works, you might want to copy your bookmarks from the old folder.

---

### Post by rraj.be on 2008-06-02
I cant get what you are telling.

Where to rename mozila.

Please can you specify the location to be renamed

---

### Post by HotShotDJ on 2008-06-02
> **rraj.be said:**
> I cant get what you are telling.

Where to rename mozila.

Please can you specify the location to be renamedThe file is called .mozilla and it is in your home directory.  It is a hidden file, so when you open Places --> Home Folder you will need to go to the "View" menu and click "Show Hidden Files" in order to see it.

---

### Post by kesman on 2008-06-02
Isn't it a directory, not a file?

---

### Post by HotShotDJ on 2008-06-02
> **kesman said:**
> Isn't it a directory, not a file?Yes.  But that is a distinction without a difference for the immediate purpose.

---

### Post by rraj.be on 2008-06-02
Yeah.thanks a lot.

It solved my problem.

i want to mark it solved.

but  one more doubt.

whats the reason for the thing i got.

and how renaming solved this.

---

### Post by HotShotDJ on 2008-06-02
> **rraj.be said:**
> whats the reason for the thing i got.

and how renaming solved this.Most likely, a corruption in a configuration file was the cause... but any number of things can cause the problem you experienced.  By renaming the the folder, you forced FireFox to create a new folder along with new configurations.

---

