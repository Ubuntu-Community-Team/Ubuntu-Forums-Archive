---
title: "[SOLVED] .dmrc file"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by RH9R on 2008-07-13
I reinstalled this morn, and all seems fine. When i booted up this evening, I get a warning message upon login that my $HOME/.drmc file is being ignored, that it should be owned by me and no one else should be able to write to it. I found a .dmrc file in my home folder, changed permissions to 644 (which the msg said it should be. I look at the file permissions in the file browser, it says I own it. I'm very puzzled. It says with this error condition it can't save certain items to session.
 
Has anyone else seen this or know how to fix? 
I appreciate the help.

---

### Post by aktiwers on 2008-07-13
Look here
[http://ubuntuforums.org/showthread.php?p=479186#post479186](http://ubuntuforums.org/showthread.php?p=479186#post479186)

---

### Post by RH9R on 2008-07-13
Atkiwers, Thank You! I just stumbled onto a similar link & was going through it & rebooting. No luck so far, but will keep working it. 
 
Again, thank you for your kind help.

---

### Post by aktiwers on 2008-07-13
I think I had a error like that once.. I cant remember how I got rid of it.

Will this fix it?
```
sudo chown -R username:username /home/username/
```And
```
sudo chmod -R 644 /home/username/
```Where username is your ubuntu username in all cases.

Its just a guess try it out :)

---

### Post by aktiwers on 2008-07-13
If it does not work, I guess you can delete that file, and the system will recreate it.
```
sudo rm .drmc
```

---

### Post by RH9R on 2008-07-13
Atkiwers - The 644 did not work, but the 700 did! Thank You so much. 'Marking this one resolved.

---

