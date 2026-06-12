---
title: "Paths in in launcher are not correct for download"
date: 2015-08-29
forum: New to Ubuntu
---

### Post by robertzito on 2015-08-29
This is odd and just notice it today. When I right click under "Files" and take the shortcut downloads it is taking me to "/home/rzito/eclipse/Downloads" rather than /home/rzito/Downloads. How do I correct this?

---

### Post by monkeybrain20122 on 2015-08-29
Open the file manager at your home, press ctrl+h or choose show hidden files from menu, find the hidden directory .config (note the "."), open it and find the file usr-dirs.dirs You can edit it and reset the XDG_DOWNLOAD_DIR to default
> XDG_DOWNLOAD_DIR="$HOME/Downloads"

Then save it. Logout and log back in (or reboot) for that to take effect.

(Probably when you installed eclipse it messed up your download path by  writing to .bashrc or .profile. Check these two hidden files and see if there  is any suspicious line added to the end. If so comment them out)

---

