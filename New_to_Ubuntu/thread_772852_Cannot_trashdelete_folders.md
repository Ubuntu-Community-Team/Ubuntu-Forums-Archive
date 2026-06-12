---
title: "Cannot trash/delete folders"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by fullmetalgerbil on 2008-04-28
I have Hardy installed, but when I go to delete folders I get a permission denied message. I've tried unlocking things via sytem>administration>users and groups with absolutely no luck. In fact, now everything I try to do via users and groups brings an authentication error.
I'm at wits end. I posted about this the other day and got no help, then I tried some insturment approaches-installing kubuntu-desktop thinking it was maybe just a Nautilus bug, but still the same thing happened, then I tried installing from the Kubuntu 8.04 live cd, which seemed to work though other problems made it unusable. Then I downgraded back to a fresh Gutsy install and finally did a Hardy upgrade from the update manager-but the same thing happened, I couldn't delete or trash any files that were in folders.
:frown:

---

### Post by TeoBigusGeekus on 2008-04-28
Navigate to folder

/home/yourusername/.local/share/Trash/files

with the terminal and delete them manually with the sudo rm command.

---

### Post by fullmetalgerbil on 2008-04-28
They wont even go into the trash.

---

### Post by keylime on 2008-04-28
You also may need to run the chmod command if this persists - that will change the ownership permissions in most cases.

---

### Post by TeoBigusGeekus on 2008-04-28
What about

```
sudo rm nameoffile.ext
```

---

### Post by martyssweb07 on 2008-04-28
can you run a sudo command?  

you also should go into system=> administration => users and groups and see what permissions your local user has.

you might also want to check your passwd file and make sure things look as they should ie
sudo grep your_username /etc/passwd

You may if sudo does work, can you create a new user and login as that user, and have things works normally?

Also you say you can't add or delete, in what directories? 
try this test and let us know the result
cd ~/
mkdir test
rmdir -rf test
ls -lah /home/

let us know the results of all this.

---

### Post by fullmetalgerbil on 2008-04-28
This is what I tried, and no luck. Should I try it with the chmod command?david@david-desktop:~$ sudo rm 2007-12-28--16.32.53
[sudo] password for david: 
rm: cannot remove `2007-12-28--16.32.53': No such file or directory
david@david-desktop:~$

---

### Post by TeoBigusGeekus on 2008-04-28
This is not a permission error.

What is this

2007-12-28--16.32.53

a file or a folder?

---

### Post by fullmetalgerbil on 2008-04-28
And this is as far as I was able to get with the other commands:
david@david-desktop:~$ cd ~/
david@david-desktop:~$ mkdir test
david@david-desktop:~$ rmdir -rf test
rmdir: invalid option -- r
Try `rmdir --help' for more information.
david@david-desktop:~$

---

### Post by fullmetalgerbil on 2008-04-28
"This is not a permission error.

What is this

2007-12-28--16.32.53

a file or a folder?" 
Its a folder with files in it. The permision error comes when I try to send them to the trash using the GUI.

---

### Post by martyssweb07 on 2008-04-28
sorry my heads not screwed on right today
not rmdir -rf
rm -rf test

---

### Post by TeoBigusGeekus on 2008-04-28
I don't know if there is a rmdir command...

To delete a folder the command is

```
rm -rf test
```

---

### Post by martyssweb07 on 2008-04-28
also you said in your post that nothings working right, and your getting popups whenever you try to do anything, is that the case, or is it just that you can't delete this one folder? the first is probably a permissions problem.

---

### Post by TeoBigusGeekus on 2008-04-28
What happens if you type

```
sudo rm -r 2007-12-28--16.32.53
```

---

### Post by fullmetalgerbil on 2008-04-28
No, things are basically working as far as I can tell (I haven't had Hardy installed long enough for actual stress testing or anything :)) its just this one thing, and yes it appears to be a permissions problem.

---

### Post by martyssweb07 on 2008-04-28
try this 
sudo rm -rf 2007-12-28--16.32.53

---

### Post by martyssweb07 on 2008-04-28
errr... I should mention that will delete the folder and all it's contents.

---

### Post by fullmetalgerbil on 2008-04-28
When I type sudo rm -r 2007-12-28--16.32.53
I get:rm: cannot remove `2007-12-28--16.32.53': No such file or directory
david@david-desktop:~$ 
But this has happened previously, for some reason it seems bash wont recognise some directories or files/folders. I had the same problem when trying to unpack and install a tar.gz file the first time I installed Hardy.

---

### Post by TeoBigusGeekus on 2008-04-28
If you right click the folder and rename it to something not so exotic, say 'folder', does this still happen?

---

### Post by martyssweb07 on 2008-04-28
hmmm what does
ls -lah 2007-12-28--16.32.53
return to you?

---

### Post by fullmetalgerbil on 2008-04-28
And nothing happened when I tried to sudo rm -rf it:
david@david-desktop:~$ sudo rm -rf 2007-12-28--16.32.53
david@david-desktop:~$ 
 Yet the folder is still there.

---

### Post by fullmetalgerbil on 2008-04-28
I renamed it to folder1, ran the rm -rf command and still no joy. Its still there.

---

### Post by fullmetalgerbil on 2008-04-28
And I tried this, using the new folder name:david@david-desktop:~$ ls -lah folder1
ls: cannot access folder1: No such file or directory
david@david-desktop:~$

---

### Post by TeoBigusGeekus on 2008-04-28
I assume the folder is on your Desktop.

Type 

```
ls
```

while on Desktop. Is the folder still listed?

Also, do a reboot...

---

### Post by fullmetalgerbil on 2008-04-28
It was actually in my Pictures directory. I tried to move it to the desktop but wasn't allowed.

---

### Post by TeoBigusGeekus on 2008-04-28
Well then, type ls while in pictures folder.
And do a reboot, will you please?

---

### Post by fullmetalgerbil on 2008-04-28
Rebooted, no luck. Used the ls command while in the Pictures folder and a bunch of stuff came up (all the contents of the folder). Now this is going to sound really stupid, but I forgot how to scroll up while in the terminal so I can check if the folder I want to delete is there.

---

### Post by TeoBigusGeekus on 2008-04-28
There should be a scrollbar on your right...

---

### Post by fullmetalgerbil on 2008-04-28
Oh sheesh, I feel like a moron. Yeah, the scrollbar, duh, how could I be so thick?
Anyways the folder is still there.

---

### Post by TeoBigusGeekus on 2008-04-28
Jesus Christ mate! What's in that folder anyway? Is it a compiled and installed program that the system uses or something?

---

### Post by fullmetalgerbil on 2008-04-28
No its just photos. But I just loaded it with all my pictures to see if I could delete a folder-since I havent been able to delete anything when using Hardy, I've tried deleting all kinds of folders (and I may be stupid but I'm not stupid enough to delete system essential folders) of stuff I loaded into my home directory to test and see if I was able to delete stuff.

---

### Post by TeoBigusGeekus on 2008-04-28
Can you delete the pictures one by one?

---

### Post by martyssweb07 on 2008-04-28
try entering an interactive root shell, i've seen some flakyness in the sudo command before.

try 
sudo -i
this will put you into an interactive root shell, and will drop you in the /root folder.
try
rm -rf /full path to folder/folder1

if that doesn;t work give me a ls -lah folder1 output

---

### Post by fullmetalgerbil on 2008-04-28
Isn't there some way I can just give my user account the right permissions to delete stuff-without having to pull up the terminal ever single time I want to delete or move files?

---

### Post by fullmetalgerbil on 2008-04-28
And this is what I got when I entered the interactive root commands:
david@david-desktop:~$ sudo -i
[sudo] password for david: 
root@david-desktop:~# rm -rf/Pictures/folder1
rm: invalid option -- /
Try `rm --help' for more information.
root@david-desktop:~#

---

### Post by fullmetalgerbil on 2008-04-28
Also:
root@david-desktop:~# ls -lah folder1
ls: cannot access folder1: No such file or directory

---

### Post by TeoBigusGeekus on 2008-04-28
> **fullmetalgerbil said:**
> 
root@david-desktop:~# rm -rf/Pictures/folder1


It should be

```
root@david-desktop:~# rm -rf /Pictures/folder1
```

Leave a blank after rf.

---

### Post by c4v3m4n on 2008-04-28
have you tried
```
sudo nautilus
```
then deleting the files from there?

---

### Post by fullmetalgerbil on 2008-04-28
Tried the correct command-nothing, its still there.

---

### Post by fullmetalgerbil on 2008-04-28
:idea:Well, I have just enough time to reinstall Gutsy before I go out tonight so...

---

