---
title: "How To: Cover you tracks with truecrypt in gnome"
date: 2008-09-03
forum: Outdated Tutorials &amp; Tips
---

### Post by innominate227 on 2008-09-03
when browsing around in your true crypt mount your data might not be as secure as you think.  Gnome keeps track of a list of your recent files and creates thumbnails of your files.  They will be there even after you dismount.  To fix this issue I wrote the following script to prevent gnome from tracking you while you use truecrypt.

```

#!/bin/sh

#save old recently used stuff, and stop tracking recently used
mv ~/.recently-used ~/.recently-used.bak 
mv ~/.recently-used.xbel ~/.recently-used.xbel.bak 
mkdir ~/.recently-used.xbel

truecrypt

#restore old recently used stuff
rm -r ~/.recently-used.xbel
mv ~/.recently-used.bak ~/.recently-used
mv ~/.recently-used.xbel.bak ~/.recently-used.xbel

#shred the thumbnail folder
find ~/.thumbnails -type f -execdir shred -u '{}' \;

```

I think this should cover all your tracks but there may be other places if any one knows of any please post.

---

