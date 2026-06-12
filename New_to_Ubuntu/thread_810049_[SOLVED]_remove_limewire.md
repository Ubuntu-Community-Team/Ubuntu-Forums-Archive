---
title: "[SOLVED] remove limewire"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-05-27
Last week I removed Limewire from my system using: [COLOR="Blue"]System>Administration>Synaptic Pkg. Mgr. Comp. Remove command[/COLOR].
It appears that this removed all files related with Limewire except:
[COLOR="Blue"]runLime.sh_limewire/usr/share/ubuntu-docs/ubuntu/sample[/COLOR]
When I accessed the file runLime.sh_limewire in the sample folder,
I went into the 'Permissions' tab. The file 'Owner' is marked as root.
Under this is stated '[COLOR="Red"]You are not the owner, so you can't change these permissions[/COLOR]', which is what I think I need to do to get rid of it. Is there another way to delete this protected file ?

---

### Post by ethoxyethaan on 2008-05-27
```
sudo su
```
```
rm /path/to/your/file.extension
```

this deletes the file without further warning.

also if you want to remove all the limewire things you will have to find them first:

```
locate limewire
```

rm all the none needed files.

also be carefull to type the corrrect path using rm or your will delete important stuff.

---

### Post by Sarah L on 2008-05-27
To get rid of a file owned by root, you'll need to use sudo.

Navigate to the directory that runLime.sh_limewire is in - from what you've posted it looks like ```
cd /usr/share/ubuntu-docs/ubuntu/sample
```

and then use ```
sudo rm -fv runLime.sh_limewire
```

EDIT:
I notice that ethoxyethaan has posted a solution - however, using the su command is potentially very dangerous, as it continuously gives root permissions when running commands.
Stick with sudo when doing running only a few commands to reduce the risk of damaging your system.

---

### Post by CoCoKnots on 2008-05-27
Thanks Sarah, I tried your thread first & It appears to have worked.

[COLOR="Blue"]cocoknots@cocoknots-laptop:~$ cd /usr/share/ubuntu-docs/ubuntu/sample
cocoknots@cocoknots-laptop:/usr/share/ubuntu-docs/ubuntu/sample$ sudo rm -fv runLime.sh_limewire
removed `runLime.sh_limewire'
cocoknots@cocoknots-laptop:/usr/share/ubuntu-docs/ubuntu/sample$ 
[/COLOR]

Do I need to remove the rest of the command as well now that the runLime.sh_limewire command is removed?

[COLOR="Blue"]/usr/share/ubuntu-docs/ubuntu/sample
[/COLOR] Thanks, Cal

---

