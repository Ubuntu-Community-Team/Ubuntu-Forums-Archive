---
title: "How do you change the Administrator user name"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by theamber on 2008-11-02
Hi, how do you change the name of the computer administrator for another and the password.

---

### Post by Peter09 on 2008-11-02
Create a new user and give them Admin rights. 
Then remove admin rights from the old user.

Use the menu options below.

System->Admin->Users and Groups

Make sure that you have admin rights on the new user before removing the old user rights.

---

### Post by Paqman on 2008-11-02
Once you've set up the new user you might want to copy the contents of the old user's /home over, to import their settings/bookmarks/whatnot.

Open Nautilus as an administator, alt-F2 and type:
```

gksu nautilus

```

Navigate to the old users /home, press ctrl-h to view hidden folders, and copy any or all of them over to the new user's /home folder. Then right-click on the folder of the the new user's username and set the permissions so that the new user is the owner (and apply to all files/folders within). If everything went fine you can delete the old user's /home directory.

Make sure to close your admin session of Nautilus afterwards.

---

