---
title: "root owner of created file"
date: 2019-02-14
forum: New to Ubuntu
---

### Post by alrobnett on 2019-02-14
I am totally green as far as ubuntu is concerned and have just moved from Windows 10. I use an app called MuseScore to create scores for songs that I write. In my first attempt to create a song in the ubuntu partition of my computer using MuseScore, the system somehow saved the beginning of the score in documents in my home directory and now won't let me modify or delete it because it says the owner is 'root'. This is all mystifying and exasperating. Is there a way for me to log in as root on my own computer?

---

### Post by alphaniner2 on 2019-02-14
'root' is the Administrator account, though rather than Administrator it's generally referred to as superuser. Logging in as root is disabled in Ubuntu for security reasons. The program 'sudo' is used to allow you temporarily acquire root privleges. To solve the immediate problem, open a terminal and change directory to your Documents folder, then run

```
sudo chown $USER\: <file>
```

Replacing <file> with the name of the score file that is owned by root. You'll be prompted to enter your password.

The bigger concern is why MuseScore created the file that way in the first place. Did you launch it from the terminal using sudo? Were you prompted to enter a password when you launched it?

---

### Post by alrobnett on 2019-02-15
Yes, my recollection (vague) is that, out of desperation, I tried "sudo MuseScore".

---

### Post by 1clue on 2019-02-15
You should never need to use escalated privileges to run a program unless it's a system maintenance app. It can be a big security hole to do so.

Read the installation information for MuseScore on their website, see if there is some group you need to belong to. [https://musescore.org/en/handbook/3/install-linux](https://musescore.org/en/handbook/3/install-linux)

---

### Post by alrobnett on 2019-02-15
Yes, my recollection (vague) is that, out of desperation, I tried "sudo MuseScore".

---

### Post by alrobnett on 2019-02-15
I used sudo because I could not find the MuseScore app _anywhere_. It now appears on the left side "Launcher". The instructions for changing owner of the unwanted file (which MuseScore says it can't read) resulted in permissions now indicating that the owner is "me" instead of "root", but it still merely beeps if I attempt to delete the file. Accessing the MuseScore app is now easy, but when I attempt save the score that I have created there is a message that says:

Open Temp File
/home/allen/Documents/MuseScore2/Scores/
Ode_To_Spring2.mscz.temp
failed: Permission denied

I have never before been denied permission to save a file that I created. Changing the name does not help. "Save As" results in no action, not even a reason for no action. I hope the security measures are as effective against hackers as they are against me. I am wading through the MuseScore handbook on installing on Linux, but the app is installed and functions up to the point of attempting to save the created file.

---

### Post by Impavidus on 2019-02-15
Most likely the directory is owned by root. Use chown to change ownership to you. It's the same as using chown to change ownership of the file, just replace the name of the file with the name of the directory.

---

### Post by #&amp;thj^% on 2019-02-15
> **Impavidus said:**
> Most likely the directory is owned by root. Use chown to change ownership to you. It's the same as using chown to change ownership of the file, just replace the name of the file with the name of the directory.

+1
Can you show us the permissions with:
Example on mine:
```
ls -al /home/me/Documents/MuseScore3
total 36
drwxr-xr-x 9 me users 4096 Feb 15 12:23 .
drwxr-xr-x 8 me users 4096 Feb 15 12:23 ..
drwxr-xr-x 2 me users 4096 Feb 15 12:23 Extensions
drwxr-xr-x 2 me users 4096 Feb 15 12:23 Images
drwxr-xr-x 2 me users 4096 Feb 15 12:23 Plugins
drwxr-xr-x 2 me users 4096 Feb 15 12:23 Scores
drwxr-xr-x 2 me users 4096 Feb 15 12:23 SoundFonts
drwxr-xr-x 2 me users 4096 Feb 15 12:23 Styles
drwxr-xr-x 2 me users 4096 Feb 15 12:23 Templates

```
Yours is probably as follows:
```
ls -al /home/allen/Documents/MuseScore2
```

---

### Post by The Cog on 2019-02-15
Try this command to change the ownership of the entire MusaeScore2 folder and its contents back to you:
```
sudo chown -R allen:allen ~/Documents/MuseScore2
```

> I have never before been denied permission to save a file that I created.
You didn't - root created it, in your home directory. When you use sudo it's very much like "Run as administrator" in windows. After a while you get used to mentally changing roles and remembering who you are. 

And actually, if "sudo MuseScore" worked, almost certainly just "MuseScore" would have worked. Your problem is that just running "sudo MuseScore" gave you root's user-id but didn't reset your home directory to /root, which is why it dropped root-owned files in your home directory. This is a potential problem when running any app as root that saves files (data, config, ...) in its user's home directory. "sudo -i" also sets the home directory back to root's home, which is safer. But you should not be running user apps as root.

---

### Post by alrobnett on 2019-02-15
Thanks to all.
Ownership of both the MuseScore directory and the Scores directory proved to be the problem. In changing ownership, not knowing any better, I used $USER instead of allen:allen, and changed to the parent directory each time, not knowing the syntax suggested for specifying the target. It seems to have worked, and God is back in his heaven.
Again, thanks to all.
Allen

---

### Post by The Cog on 2019-02-15
FYI, the '~' is short for "my home directory", but it gets expanded by the command interpreter before the arguments gets forwarded to the command sudo itself, so chown sees /home/allen, not ~ even though chown is running as root. Hoping that makes sense.

---

