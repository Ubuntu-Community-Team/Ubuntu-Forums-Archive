---
title: "Symbolic link to SMB share"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by JeffNBNB on 2013-03-29
In Ubuntu 12.10, I am trying to create a symbolic link to an SMB share. This command is issued: 

```
ln -s "/run/user/me/gvfs" "/home/me/Mac-Share"
```

It works great in Terminal, but when I try to access link in Nautilus, it appears to lock up. I have been more specific in the link command, but to no avail:

```
ln -s "/run/user/me/gvfs/smb-share:server=mac.local,share=shared" "/home/me/Mac-Share"
```

Browsing through the bookedmarked share in Nautilis always works fine.

There has got to be a way to 'save-as' from an application to a network share. 

Jeff

---

### Post by Morbius1 on 2013-03-29
I'm not sure why the first command is locking up as I just did this myself and it seems to work fine.

If all you need is an easy way to have it appear in a Save As dialogue then bookmark it. Run the following command:
```
nautilus /run/user/$USER/gvfs
```
When nautilus opens up to that location immenidately bookmark it: Bookmarks > Add Bookmark.

It should show up in the left side panel on both nautilus and Save As .

---

### Post by JeffNBNB on 2013-03-29
I have bookedmarked the share and it does show up in the Nautilus "places" section, but not in the Save-As when I try to save an e-mail attachment in Thunderbird.

---

### Post by Morbius1 on 2013-03-29
I can't reproduce that problem either. The bookmark shows up in every application I've used so far including Thunderbird. Something's not working here and I'm not sure what it could be.

---

