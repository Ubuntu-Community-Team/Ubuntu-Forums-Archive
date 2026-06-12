---
title: "Hardy Heron install problems"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by jacquelinec on 2008-06-12
I installed the new release and the darned thing shuts down during boot up. It refuses to cooperate and I'm resorting to wild pounding of F12 then random changes. 

I don't know how to replicate the problem or the "fix" but it even shuts OFF when I've tried to leave it on. 

Also - when I try to Bookmark a page I get this error:

ASSERT: Invalid menuitem in the folders-menulist
Stack Trace: 
0:EIO__getFolderIdFromMenuList()
1:EIO_toggleFolderTreeVisibility()
2:oncommand([object XULCommandEvent])



Thanks in advance.
Jacqueline

---

### Post by geezerone on 2008-06-24
I get this error when trying to add bookmark too. Any solution?

---

### Post by geezerone on 2008-07-02
I find that an elongated window appears when FF3 is opened and the first attempt to save a bookmark is carried out. If you try and select a folder from the drop-down menu the error: ```
ASSERT: Invalid menuitem in the folders-menulist
Stack Trace: 
0:EIO__getFolderIdFromMenuList()
1:EIO_toggleFolderTreeVisibility()
2:oncommand([object XULCommandEvent])
``` appears in background window. You have to OK that and close the first FF3 bookmark menu. When trying to bookmark again the smaller 'normal' window appears and it is ok then.

I have removed and re-installed FF3 and gnome support from synaptic to no avail but the profile isn't removed. 

How to completely remove all of FF3 and its components may do the trick but anyone have this problem or show how to remove all FF3 for fresh re-install?

TIA

---

### Post by geezerone on 2008-07-02
Solved:

Delicious plugin causing problem Switched from advanced to normal mode and back and now just the one option to save bookmarks. :)

---

### Post by fatality_uk on 2008-07-02
> **jacquelinec said:**
> I installed the new release and the darned thing shuts down during boot up. It refuses to cooperate and I'm resorting to wild pounding of F12 then random changes. 

I don't know how to replicate the problem or the "fix" but it even shuts OFF when I've tried to leave it on. 

Also - when I try to Bookmark a page I get this error:

ASSERT: Invalid menuitem in the folders-menulist
Stack Trace: 
0:EIO__getFolderIdFromMenuList()
1:EIO_toggleFolderTreeVisibility()
2:oncommand([object XULCommandEvent])



Thanks in advance.
Jacqueline

For the first issue. Have you tried booting into recovery mode?

---

