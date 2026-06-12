---
title: "Dolphin query"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by niteblind on 2008-09-13
Hi All,

Is anyone really good with figuring out how the back end of things work? (If so can you teach me ;p)

I use Kubuntu but do not like using dolphin as my file manager as it keeps colour changing the background of text in the "detauls" view. 

I attached a snapshot of a normal background in snapshot1 and the details view in snapshot2. As you can see the details view suddenly has this silvery grey colour vehind the file name which make it a lot harder for me (a visually impaired user) to use.

I have checked my KDE colour scheme and this is not the source of this colouring so I can only assume it is something within dolphin. Does anyone know where there is a default config file for this application I can trawl through to try and chane this colour back to black?

Any assistance would be appreciated.

Cheers
niteblind

---

### Post by Pro-reason on 2008-09-13
Report this colour issue as a bug to the KDE team.

[https://bugs.kde.org/](https://bugs.kde.org/)

---

### Post by Denestria on 2008-09-13
If you open System Settings > Appearance > Colors does unchecking Shade sorted columns in lists help your problem?

---

### Post by Denestria on 2008-09-13
Now that I had some free time I looked into this a little more.

I set my color scheme to High Contrast White Text, then set the Alternate Background in Lists to black.  This made the Dolphin details view background grey like in your screenshot.
When I unchecked Shade Sorted Columns in Lists the details view background in Dolphin is then black.  I had to change views to icon then back to details to make it show the change, or close Dolphin.

---

