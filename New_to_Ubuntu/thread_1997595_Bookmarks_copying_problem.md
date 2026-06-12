---
title: "Bookmarks copying problem"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by Drawstop on 2012-06-05
I am on Ubuntu 10.04.
I have a new laptop. How can I copy/save my list of bookmarks so that I can load it into my new laptop?
Many thanks for all help in past.
Richard.

---

### Post by VE6EFR on 2012-06-05
What browser are you using? If you are using Google Chrome, you can login with the browser to your google account. The bookmarks will automatically sync. Then when you open and login to google chrome on your laptop it will import the bookmarks for you.

---

### Post by krustenBrot on 2012-06-05
You can also export your Bookmarks in Chrome or FIrefox to take your bookmarks with you if you choose to change your browser.

In Firefox:  Open the *Bookmarks Manager* (Shift + Ctrl + O) - in the upper Panel click *Import and Backup *and than you can choose to *"Backup..."* and export as *.json

):P

---

### Post by Drawstop on 2012-06-05
VE6EFR
Many thanks for your help. All is now OK with my bookmarks on both computers.
Regards
Richard.

---

### Post by ajgreeny on 2012-06-05
In Firefox you use Bookmarks > Show All Bookmarks and there you can export the current bookmarks as either an html or json file which can then be imported in the same way to your new setup, or you can just copy across the whole hidden ~/.mozilla folder from old home folder to the new machine.

If you use chromium the folder you need is ~/.config/chromium.

However, why not backup all your /home with rsync or other backup application and then restore that to the new machine.  You will then not need to worry about such minor problems as everything will be there just as it was.

---

### Post by Megaptera on 2012-06-05
I find Xmarks to be an excellent way of syncing, saving & using my bookmarks across various browsers in both Ubuntu and Windows: 
Quote "Install Xmarks on each computer you use, and it seamlessly integrates with your web browser and keeps your bookmarks safely backed up and in sync. Xmarks will sync across browsers too. Today we support Firefox, Chrome, Internet Explorer, and Safari (Mac OS)." [http://www.xmarks.com/](http://www.xmarks.com/)

---

### Post by mapes12 on 2012-06-05
+1 for Xmarks

---

### Post by RH9R on 2012-06-23
KrustenBrot - your post helped me a bunch. 'Was wondering where the heck the 'manage 
bookmarks' menu item went.

---

