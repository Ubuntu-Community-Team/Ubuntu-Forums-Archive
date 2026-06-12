---
title: "thrash wont remove the files"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by 007casper on 2008-09-18
I got a directory around 380MB... and thrash bin cant remove the files... I figured I can load it back to one of the users and it kept saying you arent the user for this... some of the files belong to root user... so I skipped those files...  then used the terminal rm -r oldfiles but the thrash is still full... 

and ubuntu is getting a bit slower... :(

thank you so much in advance

---

### Post by Bucky Ball on 2008-09-18
Have you clicked on the trash, gone to 'File' and 'Empty Trash'? What happens?

---

### Post by Ryadt on 2008-09-18
Try```
rm -rf ~/.local/share/Trash/*
```

---

### Post by toasty_ghosty on 2008-09-18
I think the problem here is you most likely don't have the correct permissions to delete the file. If you do what is said above it should tell you if that is the issue. If so something such as:
> Error removing file: Permission denied

should pop up.

If so I would do these commands:

Change to the trash directory:

> cd ~/.local/share/Trash/files/

and then delete all the files in the trash:

> sudo rm -fr ~/.Trash/*

This will delete everything in the trash. This will work if the issue is a permission issue.

---

### Post by 007casper on 2008-09-18
yeah!... awesome!... thank you thank you so much everyone... worked like a charm... 

it was a permission issue

---

### Post by Beth1957 on 2008-09-18
> **toasty_ghosty said:**
> I think the problem here is you most likely don't have the correct permissions to delete the file. If you do what is said above it should tell you if that is the issue. If so something such as:


should pop up.

If so I would do these commands:

Change to the trash directory:



and then delete all the files in the trash:



This will delete everything in the trash. This will work if the issue is a permission issue.

Ah, I've been getting the "permission denied" message when trying to get rid of a couple of items from my Desktop Trash. 
I just tried running the code above, both as me and as root, but still got the same message unfortunately.
I'm the only active user of this machine, and it was certainly me (I?) who put the items in Trash... any ideas, please?

---

### Post by Bucky Ball on 2008-09-19
Toasty Ghosty, how would you set the permissions so this procedure doesn't need to be repeated each time?

---

