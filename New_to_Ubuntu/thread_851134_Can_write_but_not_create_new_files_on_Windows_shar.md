---
title: "Can write but not create new files on Windows share?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by The Rocker on 2008-07-06
So this is kind of strange. I just installed Ubuntu the other day on my laptop.  I have a shared Windows (XP Professional) drive on my desktop computer which I have mounted on Ubuntu (via cifs).  I can see it fine, but when I started editing some text files, I was able to save them to the drive just fine but my text editor failed to create a backup file.  I just had to overwrite every time... not a big deal really, but then I tried to commit some changes to our servers at work using Subversion, and the commit failed because it was apparently unable to move/back up the old entry files prior to the commit.

Any idea why I'd be able to read/write/save files but not create new ones?

---

### Post by The Rocker on 2008-07-06
Hmm... well this is strange indeed... I just tried it again and the problem seems to have mysteriously gone away after a restart.

---

### Post by bumanie on 2008-07-06
Have you installed ntfs-3g and ntfsconfig yet? If not > sudo apt-get install ntfs3-g this enables read/write to ntfs > sudo apt-get install ntfsconfig this allows you nominate ntfs partitions/drives to read/write to and they will automatically be added to /etc/fstab Have no idea what you mean with the server - outside my territory, but the above is the 'accepted' way to enable read/write and as far as I know 'save' to ntfs from within ubuntu.

PS: You should mark your other post 'solved'

---

### Post by The Rocker on 2008-07-06
Apparently ntfs3-g is already installed.  And I did add the drive to /etc/fstab and can see/read/write to it.  I could see everything right out of the box, although I had to manually edit fstab in order to get the shared drive to mount every time at startup.

Anyhow it seems to be working at the moment, will report back if it happens again. Thanks for your help.

---

### Post by bumanie on 2008-07-06
Forgot to mention ntfsconfig is under Applications --> System Tools --> Ntfsconfig.

---

