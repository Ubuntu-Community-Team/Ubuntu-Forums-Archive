---
title: "removing home folder from menu panel"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by tropdoug on 2008-05-18
I have partitioned my drive into two, so that the OS can reside on one and all my data on the other. I have changed all ownerships and permissions so that I can read and write to the second partition, and re created the folders I want in there. 

I have renamed the menu entry [COLOR=Blue]'disk' to 'Home folder' [/COLOR]so that I go straight there without confusion when I want to access my docs, but I cannot remove the top entry in the[COLOR=Blue] 'Places' menu panel, 'Home Folder'[/COLOR] . Although I know what I have done, this puter will also be used by my wife, and I want to ensure we do not end up with a messed up filing system. 

How can I remove this entry? and is it possible to re position the renamed 'disk' entry to the top of the list. 

Thanks

---

### Post by HotShotDJ on 2008-05-18
> **tropdoug said:**
> I have renamed the menu entry [COLOR=Blue]'disk' to 'Home folder' [/COLOR]so that I go straight there without confusion when I want to access my docs, but I cannot remove the top entry in the[COLOR=Blue] 'Places' menu panel, 'Home Folder'[/COLOR] . Although I know what I have done, this puter will also be used by my wife, and I want to ensure we do not end up with a messed up filing system.1st... you can give your wife her own user account on the computer so that she can set up her own desktop the way she likes it without effecting yours.  But that really isn't what you asked about...

I would leave the original "Home Folder" as is.  It is supposed to point to /home/$USER and nothing else.  Also, remove the new Places entry that you created and named Home Folder.   For this next step, I'm assuming that the disk is mounted on /media/disk.  If not, make the appropriate changes.  Open a terminal and type:```
ln -s /media/disk /home/$USER/Storage
```Of course, replace $USER with your user name.  You may also change Storage to something else.  Perhaps if your Documents folder is empty, you can delete it and then replace Storage with Documents.  That is completely up to you. Now, you can access the drive by clicking on the folder you just created in /home/$USER or you can add that directory as a bookmark in places.

---

