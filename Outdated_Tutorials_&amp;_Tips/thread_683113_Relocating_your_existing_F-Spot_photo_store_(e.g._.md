---
title: "Relocating your existing F-Spot photo store (e.g. ~/Photos to ~/Pictures)"
date: 2008-01-30
forum: Outdated Tutorials &amp; Tips
---

### Post by SeanHodges on 2008-01-30
This allows you to move your entire photo store to a different location, and instruct F-Spot to use this new path without re-importing photos and risking data loss:

**QUIT F-SPOT FIRST!!!**

1. Move the photo store where you want it to be (if you haven’t done so already!)

2. Back-up your F-Spot database

```
cp ~/.gnome2/f-spot/photos.db ~/.gnome2/f-spot/photos-backup.db
```

3. Install and start sqlite

```
sudo apt-get install sqlite3
sqlite3 ~/.gnome2/f-spot/photos.db
```

5. Perform an update command against the “photos” table. Make sure you set the paths to match your own

> update photos set directory_path = '/NEW/PATH' || substr(directory_path,length('/OLD/PATH/'),length(directory_path)) where directory_path like '/OLD/PATH/%';

Example:

> update photos set directory_path = '/home/sean/Pictures/photos' || substr(directory_path,length('/home/sean/Photos/'),length(directory_path)) where directory_path like '/home/sean/Photos/%';

6. Quit sqlite

```
.quit
```

From here on, assuming these steps worked, you should be able to start F-Spot and all your photos are still found!

***
If something went wrong, you can revert to the old database by moving the photos back where they were, and running this command:

```
mv ~/.gnome2/f-spot/photos-backup.db ~/.gnome2/f-spot/photos.db
```
***

*NOTE: F-Spot appears to rebuild it’s thumbnail cache when you start it the first time after doing this, you will notice that all the photos have no images. Leave it for a few minutes and you should find all the photos will eventually flood back into existence.*

Thanks to [nozell.com]("http://nozell.com/blog/2006/07/02/moving-photos-around-behind-f-spots-back/") and [itjungle.com]("http://www.itjungle.com/fhg/fhg040506-story02.html") for pointers.

---

### Post by YoHell on 2009-03-28
A neater way of doing the same thing in sqlite3 is:

```
update photo_versions set uri = replace(uri,'file:///old/path/','file:///new/path/');

```

**Note also** that you will have to update the photo_versions table as well:

```
update photo_versions set uri = replace(uri,'file:///old/path/','file:///new/path/');

```

---

