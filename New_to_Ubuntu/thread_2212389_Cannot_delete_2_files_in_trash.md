---
title: "Cannot delete 2 files in trash"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by Clifford_Sarokoff on 2014-03-21
I modified two files in GIMP program. I made copies as backup before the mod. I no longer needed the two files that I copied so I sent them to trash. When I emptied the trash folder everything  EXCEPT the two files were deleted. How do I delete these two files that I obviously do not have ownership over? 
Ubuntu 13.10
CliffordS

---

### Post by varunendra on 2014-03-21
See if you can see those files under "**.local/share/Trash/files**" directory within your home. You'll have to enable "Show Hidden files" option in your file browser to be able to see ".local" directory. From terminal, you can list them easily -
```
ls -l .local/share/Trash/files
```
Does it list those files? Is their owner someone else?

If you can find them there, delete them by either opening the file browser as 'root' (e.g., "**gksu nautilus**". Note: can be risky, so just do what you intended to do and immediately close it), or by simple terminal way -
```
cd .local/share/Trash/files/
rm file1 file2
```

If they were created by another user, they might be located in same path related to Their Home (e.g., /home/*User2*/.local/share/Trash/files), and you may not be able to access or delete them as current user (unless you run the command as root (sudo)).

---

### Post by Clifford_Sarokoff on 2014-03-21
Thanks for the reply. when I use [COLOR=#000000][FONT=Ubuntu Mono]cd .local/share/Trash/files/[/FONT][/COLOR]rm *.* I get a message that 2.0 is a directory and menurc.2 is a directory. It won't delete them.
CliffordS

---

### Post by varunendra on 2014-03-21
So there may be deleted directories in there. To remove directories, use the "-r" switch -
```
rm -r *
```

However, apart from the entities that you got error about, the rest of stuff should have been deleted. If your problematic files were among that 'stuff', your problem should have been solved now.

---

### Post by Clifford_Sarokoff on 2014-03-21
Thanks again, I got one of the two directories removed. The directory 2.0 still had an ownership issue and didn't delete.
CliffordS

---

### Post by varunendra on 2014-03-21
It would, with "sudo" -
```
sudo rm -r ~/.local/share/Trash/files/*
```

Note that I have used the full path with "~/" notation *(which expands to the path of current user's Home)* just to be safe, otherwise running "rm" command with "sudo" and wildcards **_can be very dangerous_** if not used carefully!

---

### Post by Clifford_Sarokoff on 2014-03-21
Success! 
Your good, really good!
Thank you, CliffordS

---

### Post by varunendra on 2014-03-21
Glad I could help. :)

Please mark the thread as [SOLVED] using "Thread Tools" link above the first post.

---

