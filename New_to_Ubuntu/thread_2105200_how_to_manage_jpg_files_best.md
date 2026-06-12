---
title: "how to manage jpg files best"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by 12katia34 on 2013-01-15
dear all,
I am getting into organizing my pictures with the shotwell photomanager and enjoy the option of quickly fusing folders without terminal directories. Unfortunately whatever I do in shotwell doesn't affect the pictures saved in "my pictures" in the privat folder at all (not even if I send files to trash), whereas if I delete any jpg in the private folder it cannot be found in shotwell either.
Working strictly with photo files in my private folder under pictures is painful though because merging pictures from files named 2nd, 5th, 11th and 28th within one month can only be acchieved with an awful lot of copy paste.

> does anyone have any suggestions to limit the clicking? from what I understand about symlink that wouldn't be a time-saving option with all the terminal directory typing. Is there no way like windows has where you just marker all directories, right click and merge?

THANK YOU
Kat.

---

### Post by TheFu on 2013-01-15
> **12katia34 said:**
> dear all,
I am getting into organizing my pictures with the shotwell photomanager and enjoy the option of quickly fusing folders without terminal directories. Unfortunately whatever I do in shotwell doesn't affect the pictures saved in "my pictures" in the privat folder at all (not even if I send files to trash), whereas if I delete any jpg in the private folder it cannot be found in shotwell either.
Working strictly with photo files in my private folder under pictures is painful though because merging pictures from files named 2nd, 5th, 11th and 28th within one month can only be acchieved with an awful lot of copy paste.

> does anyone have any suggestions to limit the clicking? from what I understand about symlink that wouldn't be a time-saving option with all the terminal directory typing. Is there no way like windows has where you just marker all directories, right click and merge?

THANK YOU
Kat.


I don't use Shotwell and have been extremely frustrated using Windows for any photo management.  I trust my directories more than any software tool that claims to "manage photos" since next year, when I try some new tool, none of the metadata not embedded inside the EXIF part of the JPG will be honors.
This article outlines my methods: [http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival)  I'm using it for just under 20K photos.

The other tip is the use **recoll **as your search tool. recoll is amazing for local file indexing and searching beyond just the filename (htough it works for that too).

I would not use softlinks. I'd use hardlinks, if you needed to have the same photo in different places on the same disk.

---

### Post by eric-yorba on 2013-01-15
> **12katia34 said:**
> dear all,
I am getting into organizing my pictures with the shotwell photomanager and enjoy the option of quickly fusing folders without terminal directories. Unfortunately whatever I do in shotwell doesn't affect the pictures saved in "my pictures" in the privat folder at all (not even if I send files to trash), whereas if I delete any jpg in the private folder it cannot be found in shotwell either.

This is by design.  Shotwell is a non-destructive photo editor, meaning the goal is to make it difficult to accidentally destroy your original photos.

Shotwell has its own internal trash as a precautionary step against accidentally removing photos.  When you trash a photo in Shotwell it's just marked as trashed in the Shotwell database.  The file is only removed when you delete the file from Shotwell's trash.

Hope that helps!

---

### Post by t0p on 2013-01-15
I use shotwell.  The idea is to configure your files and folders through shotwell, not by using the file manager.  It may appear clumsy for the files to be sorted into year, month and day folders, but that doesn't really need to bother you if you always select files through shotwell's interface.  You can search for images by date, and if you use tagging, you can search by tags too.  It may seem odd at first but it grows on you (well, me at any rate).

If you do change files or folders through file manager, you'll need to import/re-import the changed folders into shotwell.  It will only import "new" files, it won't re-copy files that haven't changed.

I don't know if I've explained this well.  If not, maybe someone else could help?

---

