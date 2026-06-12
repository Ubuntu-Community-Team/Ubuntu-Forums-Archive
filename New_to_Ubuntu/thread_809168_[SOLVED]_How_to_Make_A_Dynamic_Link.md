---
title: "[SOLVED] How to Make A Dynamic Link?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by dunomous on 2008-05-27
I am utterly appalled at my inability to find this, both by this forum (although, not blaming it) and by Google.

My Problem: My dynamic link for plugins (for Swiftfox) is pointing to the wrong folder. I am not sure how to edit it, create a new one, or anything about dynamic links. 

I suppose, I could create a symbolic link. But what am I doing wrong to find simple information about a dynamic link? One would think "How to create a dynamic link in linux" and all its variations would yield some helpful results in Google and/or this forum. 

Anyway, any and all help is appreciated as usual. Thanks!

---

### Post by sdennie on 2008-05-27
I don't know what you mean by a dynamic link.  It sounds like you want a symlink but you then say that you don't want to do that.

---

### Post by koshari on 2008-05-27
do you mean shared objects (so) ?

---

### Post by koshari on 2008-05-27
ln source destination
Create a hard link called destination to the file called source. The link appears as a copy of the original files, but in reality only one copy of the file is kept, just two (or more) directory entries point to it. Any changes the file are automatically visible throughout. When one directory entry is removed, the other(s) stay(s) intact. The limitation of the hard links are: the files have to be on the same filesystem, hard links to directories or special files are impossible.

ln -s source destination
Create a symbolic (soft) link called "destination" to the file called "source". The symbolic link just specifies a path where to look for the file. In contradistinction to hard links, the source and destination don't not have to tbe on the same filesystem. In comparison to hard links, the drawback of symbolic links are: if the original file is removed, the link is "broken", symbolic links can also create circular references (like circular references in spreadsheets or databases, e.g., "a" points to "b" and "b" points back to "a").

---

### Post by sdennie on 2008-05-27
Thinking a bit more, it's possible that you already have a symlink and you just want to replace it.  If that's the case, links don't always act the same as a file and so you'll first want to remove the existing symlink and then the instructions from koshari seem correct.

---

### Post by dunomous on 2008-05-27
Thank you so much, gents!

Solution/Explanation: From an update of Swiftfox (firefox) 3 pre 4, the sym/soft link (symbolic link) was broken because "xulrunner-addons" folder was renamed to just "xulrunner". Such happenings caused flash and other plugins to of course not work. This, I knew. On the Swiftfox forums, a solution was posted that an individual made a dynamic link (I suppose, he meant Hard link?). Regardless, a hard link was not possible, and creating a symbolic link (using sudo) certainly fixed the issue right up. For others who may be having this issue, this was the command I used:

```
sudo ln -s /usr/lib/xulrunner/plugins /usr/lib/swiftfox
```

Others (especially from Debian, or other distros) report the swiftfox folder being in /opt/swiftfox. 

Anyway, an easy and common sense fix (especially when not frustrated ;)). Thanks once more!

---

