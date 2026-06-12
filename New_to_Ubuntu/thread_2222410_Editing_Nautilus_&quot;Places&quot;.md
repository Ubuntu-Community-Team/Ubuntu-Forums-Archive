---
title: "Editing Nautilus &quot;Places&quot;"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by joe_cool2 on 2014-05-06
Nautilus by default has the following places:

[LIST]
[*]Home
[*]Desktop
[*]Documents
[*]Downloads
[*]Music
[*]Pictures
[*]Videos
[*]Trash
[/LIST]

Is there a way of editing it? I would like to add some more places. (I'm using Ubuntu 14.04)

---

### Post by slickymaster on 2014-05-06
See this: [How can I edit Nautilus Places sidebar and Unity QuickList]("http://askubuntu.com/questions/325518/how-can-i-edit-nautilus-places-sidebar-and-unity-quicklist")

---

### Post by joe_cool2 on 2014-05-06
> **slickymaster said:**
> See this: [How can I edit Nautilus Places sidebar and Unity QuickList]("http://askubuntu.com/questions/325518/how-can-i-edit-nautilus-places-sidebar-and-unity-quicklist")

I've already seen that thread, it's the first link on Google, but it doesn't help me and that's why I'm posting this thread. First because those instructions are for Ubuntu 13.04 and I'm using Ubuntu 14.04, and second because editing Nautilus source code and recompiling it is just too much trouble. There might be a better way.

---

### Post by mcduck on 2014-05-06
> **joe_cool2 said:**
> I've already seen that thread, it's the first link on Google, but it doesn't help me and that's why I'm posting this thread. First because those instructions are for Ubuntu 13.04 and I'm using Ubuntu 14.04, and second because editing Nautilus source code and recompiling it is just too much trouble. There might be a better way.

In that case simply bookmarking a folder is the way to go. Just browse to a location you want to add and hit Ctrl-D or select Bookmarks->Bookmark This Location from the menu.

---

### Post by Tohunga on 2014-05-07
> **slickymaster said:**
> See this: [How can I edit Nautilus Places sidebar and Unity QuickList]("http://askubuntu.com/questions/325518/how-can-i-edit-nautilus-places-sidebar-and-unity-quicklist")

I followed the insturctions (substituing for nautilus-3.10.1), but the " quilt edit src/nautilus-places-sidebar.c" returns an empty file. 

Any help would be greatly appreciated.

---

### Post by joe_cool2 on 2014-05-08
> **Tohunga said:**
> I followed the insturctions (substituing for nautilus-3.10.1), but the " quilt edit src/nautilus-places-sidebar.c" returns an empty file. 

Any help would be greatly appreciated.

Don't follow any instructions which aren't for Ubuntu 14.04.

---

### Post by Frogs Hair on 2014-05-08
After some research it appears editing places is not possible in newer versions of  nautilus. I tried changing the places order in the configuration file with no effect in the gui and any attempts to add folders show up as bookmarks rather than places.

---

### Post by Tohunga on 2014-05-08
While I have not been able to add anything to places, at least the genius of the internet has helped me remove them:

The trick is to avoid the reset of *user-dirs.dirs* is to: 
**echo "enabled=false" > ~/.config/user-dirs.conf**
(thanks to [ycheng]("http://askubuntu.com/questions/285313/how-to-customize-add-remove-folders-directories-the-places-menu-of-ubuntu-13"))

Again, adding entries to the *user-dirs.dirs *does not appear to have any effect, but commenting out entries does remove them from my places sidebar.

---

### Post by beetcom on 2014-05-13
In my case (14.04) it was because the file that contains the bookmarks only had to modify the root (I do not know why), now i can drag and drop bookmarks are saved and the solution is simple. 


From a terminal change the permissions of the folder that contains the bookmarks 


sudo chmod -R 777 ~/.config/gtk-3.0

---

### Post by Drowz0r on 2014-05-18
> **beetcom said:**
> In my case (14.04) it was because the file that contains the bookmarks only had to modify the root (I do not know why), now i can drag and drop bookmarks are saved and the solution is simple. 


From a terminal change the permissions of the folder that contains the bookmarks 


sudo chmod -R 777 ~/.config/gtk-3.0

Not sure what this is meant to achieve. We can already drag and drop bookmarks around. Is this meant to allow us to drop bookmarks into the places area?

I've run the command but there has been no change.

---

### Post by joe_cool3 on 2014-05-19
It doesn't help me at all.

---

### Post by mcduck on 2014-05-20
> **Drowz0r said:**
> Not sure what this is meant to achieve. We can already drag and drop bookmarks around. Is this meant to allow us to drop bookmarks into the places area?

I've run the command but there has been no change.

Sounds more like the ownership of the file had somehow changed on his system (for example running graphical applications with "sudo" instead of"gksudo" can result in config files becoming owned by root instead of the user). In which case the best solution would have been changing the ownership back to user instead of leaving it as root but with permissions that allow anyone to edit the file...

Either way, that won't allow you to edit the "Places" area, which can only be edited by compiling the file manager from source. Bookmarks section is what's intended to be user-editable. (and on recent Ubuntu versions bookmark entries will also appear in Unity quicklist by default so the only difference really is that user-set location appear slighly lower in the side panel...)

---

### Post by ben_lutgens on 2014-05-20
> **Frogs Hair said:**
> After some research it appears editing places is not possible in newer versions of  nautilus. I tried changing the places order in the configuration file with no effect in the gui and any attempts to add folders show up as bookmarks rather than places.

Wow, they LOVE ripping out perfectly good functionality don't they? How stupid!

---

### Post by mcduck on 2014-05-21
As far as I'm aware, such functionality has never even existed. Apart from bookmarks, the Places have always been hard-coded to only display the directories specified in the XDG desktop standard.

---

### Post by Drowz0r on 2014-05-23
I've managed to "fool" it, kinda... if you place a shortcut in your home folder called "Pictures" or one of the pre-existing Places, it will take you to where ever that shortcut goes. It was handy for me having my Pictures and Videos etc on separate HDDs from my main one. No idea what else you would do with that "cheat" though.

---

