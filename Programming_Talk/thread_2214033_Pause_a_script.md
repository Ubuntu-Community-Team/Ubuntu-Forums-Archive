---
title: "Pause a script?"
date: 2014-03-30
forum: Programming Talk
---

### Post by merriman222 on 2014-03-30
I'm trying to write a simple script to easily scan a XP partition with clamscan, but there are 2 extra things I'd like to add. One is a pause at the end to see the results, and the other is id like it to mount and unmount the drive automatically. I'm used to working with batch files in windows but just getting my feet wet elsewhere.
  
So far I have.
```
#!/bin/bash
echo mypassword | sudo -S freshclam
mkdir /tmp/virus
sudo clamscan -r --move=/tmp/virus /media/32E0XXXXXXXXXX43
```

What I'd like to add is.
```
#!/bin/bash
echo mypassword | sudo -S freshclam
mkdir /tmp/virus
**mount the windows partition**
sudo clamscan -r --move=/tmp/virus /media/32E0XXXXXXXXXX43
**unmount the windows partition**
**the equivalent of "pause" or even a prompt
```

By prompt I mean how a batch would behave with "[COLOR=#070F14][FONT=Verdana]Set /P x= Press Enter To Close." as the last line in a batch.

Also I know it's not advisable to put my password in a script, but the laptop in question is used as a learning tool/sandbox and nothing more so I'm not really worried.

===================
Of course, I finally locate the answer 5 mins after posting.......

So now I'm at:
[/FONT][/COLOR]```
#!/bin/bash
echo mypassword | sudo -S freshclam
mkdir /tmp/virus
**mount the windows partition**
sudo clamscan -r --move=/tmp/virus /media/32E0XXXXXXXXXX43
**unmount the windows partition**
[COLOR=#000000][FONT=Consolas]read [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]-[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]p [/FONT][/COLOR][COLOR=#800000][FONT=Consolas]"Press Enter To Close."[/FONT][/COLOR]
```

---

### Post by TheFu on 2014-03-30
Modify the sudoers file to allow the exact, specific command, including options, to be run by the specific userid.

Always completely, fully, specify all commands used inside a script.  /bin/mount, /usr/bin/sudo, /bin/mkdir - NEVER trust the PATH. This is a good habit to learn. I've been burned before and it is a very common problem when PATHs are not 100% consistent across userids.

You could just write the output to a file. Then you can run this script from cron and email the results to yourself easily. Just an option.

---

### Post by EddyDreizehn on 2014-03-30
Maybe, you mean something like that: 

```

read -n1 char

```

Wait for press any key. The pressed key is in variable char saved.

 :guitar:

---

