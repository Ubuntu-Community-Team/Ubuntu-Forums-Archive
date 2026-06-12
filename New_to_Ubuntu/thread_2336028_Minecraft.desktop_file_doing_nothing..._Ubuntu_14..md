---
title: "Minecraft.desktop file doing nothing... Ubuntu 14.04"
date: 2016-09-03
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2016-09-03
Created .desktop file with these contents and linked from /usr/local/bin/minecraft/ to /usr/share/applications/

```
[Desktop Entry]
Name=Minecraft
Comment=Sandbox
Type=Application
Exec=/usr/bin/java -jar /usr/local/bin/minecraft/minecraft.jar
Icon=/usr/local/bin/minecraft/minecraft.png
Categories=Game;

```

Directory with everything in it for global access

```
jason@homewrecker:/usr/local/bin/minecraft$ ls -l
total 468
-rw-r--r-- 1 root root 137234 Sep  3 12:46 mcpatcher.png
-rw-r--r-- 1 root root    188 Sep  3 13:19 minecraft.desktop
-rw-r--r-- 1 root root 280212 Sep  3 10:13 minecraft.jar
-rw-r--r-- 1 root root  47840 Sep  3 12:45 minecraft.png

```
If I copy/paste the exec command out of the .desktop file to the terminal it launches Minecraft and away I go. However from the Superbar or whatever it's called the icon just flickers 6 times and does nothing. I'm at a loss. The icon is there and everything is correct, it just doesn't launch Minecraft from the icon.

---

### Post by mook765 on 2016-09-03
>  linked from /usr/local/bin/minecraft/ to /usr/share/applications/
This should be 
> linked from /usr/local/bin/minecraft/minecraft.desktop to /usr/share/applications/
Use
```
ls -l /usr/share/applications
```
to see where your link points to.

---

### Post by Tadaen_Sylvermane on 2016-09-03
```
jason@homewrecker:/usr/share/applications$ ls -l  minecraft.desktop 
lrwxrwxrwx 1 root root 42 Sep  3 17:36 minecraft.desktop -> /usr/local/bin/minecraft/minecraft.desktop

```

---

### Post by mook765 on 2016-09-03
Like you I don't see any reason why the link shouldn't work.
Try something else...
Add the line 
```
Terminal=true
```
to your .desktop file and see if it works.

---

### Post by Tadaen_Sylvermane on 2016-09-04
No difference unfortunately. This is puzzling at best...

*EDIT* Solved, kind of.
xe
I found that changing the permissions on the .desktop file to 755 and dragging the desktop file directly from the file manager to the bar and it works. Won't work straight out of the launcher menus though. Calling it half fixed at the moment. I'll keep researching it, works for the moment though.

'

---

### Post by mook765 on 2016-09-04
I tried out a bit. I just took an existing .desktop-file in /usr/share/applications and copied it to my Document-folder and renamed the original file.
Then I created a symlink in /usr/share/applicationsto the copy in ~/Documents. That was not going to work due to permissions and ownership.
I changed permissions and set ownership to root, then it worked.
```
mook@MookPC:~/Documents$ ls -l org.kde.knotes.desktop             
-rwxr-xr-x 1 root root 4363 Sep  4 23:26 org.kde.knotes.desktop
```
It seems that .desktop-files a treated in a special way for security reasons.
The easier way would be to copy your .desktop-file in the applications directory. That should work out of the box...
I don't see an advantage in using a link for the purpose.
Another way around might be to use a hardlink instead of a symlink, then it wouldn't be necessary to play with permissions, but this I didn't try out for the moment...

---

