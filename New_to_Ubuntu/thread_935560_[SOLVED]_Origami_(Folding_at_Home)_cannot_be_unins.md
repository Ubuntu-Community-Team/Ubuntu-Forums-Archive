---
title: "[SOLVED] Origami (Folding at Home) cannot be uninstalled"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-01
Origami, a Folding-at-Home project, is supposed to run in the "background" being careful not to use system resources when the 'puter needs them. But mine has gone haywire.

I used aptitude to uninstall (remove) origami. Then I rebooted. It was still there. So I went to Synaptic and told it to remove all parts of origami. I rebooted and it's still there.

I looked through my: /home/mark directories . files to see if there was something labeled origami, but there's nothing there. The offending file is called:

FahCore_a0.exe

how can I locate this file in the OS and is it safe to delete it?

---

### Post by virtuallinux on 2008-10-01
you could use the find command:

```

find / -name "FahCore_a0.exe" -print

```

This searches the root directory for the file and outputs the directory where it finds it.  You'll probably want to prefix this command with "sudo", since it's searching the root directory.

It seems odd to me that the file would have a .exe extension.

---

### Post by Mark_in_Hollywood on 2008-10-01
mark@Lexington-19:~$ sudo find / -name "FahCore_a0.exe" -print
find: /home/mark/.gvfs: Permission denied
/var/lib/origami/foldingathome/CPU1/FahCore_a0.exe

Hmmm? the file:

FahCore_a0.exe 

runs/starts at boot time and is robbing my CPU ... let me say it's using 70 to 90% CPU all the time.

I tried to uninstall it from Synaptic. Rebooted. It's still there. The directory files in **origami** and directories in **origami** are owned by origami. I can't delete them. Do you know how to do that?

---

### Post by virtuallinux on 2008-10-01
You need to be root to delete the files. There are a couple of methods you could use:

1) type "sudo nautilus". This brings up a file browser window. You can navigate to the directory where the files are and delete them.

OR

2) type "sudo rm /var/lib/origami/foldingathome/CPU1/FahCore_a0.exe"

---

### Post by Mark_in_Hollywood on 2008-10-06
I got a solution to this through another thread:

[http://ubuntuforums.org/search.php?searchid=49158370](http://ubuntuforums.org/search.php?searchid=49158370)

Thanks, community.

---

