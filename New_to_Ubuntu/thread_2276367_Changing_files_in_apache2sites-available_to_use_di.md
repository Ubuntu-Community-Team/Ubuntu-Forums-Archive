---
title: "Changing files in apache2/sites-available to use different website directory"
date: 2015-05-02
forum: New to Ubuntu
---

### Post by lucy5 on 2015-05-02
Hi,
(Completely new to Linux)
I have a split partition (Ubuntu/Windows) on my laptop, with a storage partition which both can access. I want to set up lamp so that I can use websites in this storage partition. So, I've been trying to edit the '000-default.conf' file in 'sites-available' to change the default folder path, but have so far been very unsuccessful. The permissions were set to read only and I've finally changed them, but when I try to save the file it keeps saying 'Could not create a backup file while saving &#8220;/etc/apache2/sites-available/000-default.conf&#8221;'. If I click 'save anyway' it just displays the same message again. This is after installing gksu nautilus and using that to change the permissions. Can anyone help? 

I'm starting to think the files had something wrong with them in the first place... I couldn't change the permissions with the terminal (it didn't display any sort of error, just didn't change them) and there was something I tried entering into the terminal which allowed you to edit it through that (can't remember what it was, sorry) which just showed a blank page.

Edit - actually, think I've sorted it out. Had to stop gedit from trying to create backups.

---

