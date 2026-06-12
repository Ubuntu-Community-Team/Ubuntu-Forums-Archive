---
title: "Installing programs in Ubuntu Studio"
date: 2016-05-02
forum: New to Ubuntu
---

### Post by nikkor2 on 2016-05-02
This is my first dip into the Ubuntu Studio waters and I am having a little trouble accomplishing what should be very easy.
I am running Ubuntu Studio - Ubuntu 14.04.4 LTS. When I download programs from the Ubuntu Software Center where are the programs saved (file path directory)? Is there a default directory for these downloads? I checked my /home/.../Downloads/ folder and the program is not there.
Also, how to discern the executable file?.. (in windblows GUI its pretty easy to distinguish the executable files).
Thank you for your assistance.

---

### Post by oldrocker99 on 2016-05-02
Programs downloaded from the Ubuntu Software Center (or by apt-get or Synaptic) are downloaded to /var/cache/apt/archives, not in /home, and are installed in other folders; the executable is usually in /bin or /usr/bin or /usr/games. The data files and libraries are installed in various other folders. Whichever file manager you use will show the executable as an executable. 

If there is no icon for the program you've installed, type its name into a terminal. That should run it.

---

