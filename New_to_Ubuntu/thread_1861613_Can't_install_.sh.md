---
title: "Can't install .sh"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Arcken on 2011-10-15
Hi i used ubuntu for a few months then had to move to windows, now i am back to linux, but some commands i forgot xD,  but i managed to install a sh file on linux before, but now i get this error message:

```
sh: Can't open ./11.0sp1_quartus_free_linux.sh
```

The file have permission to run as executable, and i tried severel commands, but no success, even this post [http://ubuntuforums.org/showthread.php?t=907998](http://ubuntuforums.org/showthread.php?t=907998), i followed but no success, any clue?

---

### Post by gsmanners on 2011-10-15
If you have root permission, you can avoid the mess with . and / by simply copying the scripts into the path:

```
sudo -i
cd /usr/local/bin
cp /path/to/scripts/* .
chmod +x *
```

Then, it's just a simple matter of invoking the script by name.

---

### Post by husam212 on 2011-10-26
I have the same problem with installing quartus :(

---

