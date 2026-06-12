---
title: "How to transfer /home/user to a new computer"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2012-03-08
I want to transfer my user directory from my old computer to a new one. Both run 10.04, and I have taken great care to ensure that my login and password on the new computer are exactly as they are on the old. Both computers are connected via a lan, and I have a 32GB thumb drive.

We need to be mindful of hidden files and permissions. What is the simplest way to do this?

---

### Post by papibe on 2012-03-08
I've successfully used rsync over ssh to do similar work. I would recommend it.

Just a thought, and tell us if you need tips with the rsync command.
Regards.

---

### Post by Odyssey1942 on 2012-03-08
Papibe,

Somewhere I got the idea that there can be permission issues with rsync, so presumably it must be done with the correct arguments. 

What was your command line?

---

### Post by papibe on 2012-03-08
Not at all.

First, I would save some files and directories on the new machine:
```
cd
mkdir savefiles
cp -rp .bashrc .bash_logout .ssh/ savefiles/
```

Then, you need to install openssh-server in one of the machines. Let's say you do it on the new one.

Then **from the old one**:
```
rsync -av /home/youruser/  new_machine:/home/youruser
```
Then, on the new one, I would recover the files saved:
```
cd ~/savefiles/
cp -rp .bashrc .bash_logout .ssh/  ~/
```
I hope that helps, and tell us how it goes.
Regards.

---

### Post by Odyssey1942 on 2012-03-09
I have been studying yours, and, with apologies for being such a noob, but to make sure that I understand, do you make the copies to avoid having those particular files changed when you copy the other files from the old to the new computer? Any elaboration on this will help me understand exactly what you are doing.

My way of doing it in this case was:
1-ensure same login and pw on both computers
2-make tarball of my user directory
3-scp over to new computer
4-rename user directory on new computer
5-move tarball to /home
6-unpack
7-restart

Yours is much less complicated. Does yours accomplish exactly the same thing (permissions intact, etc.)? 

Are there any other steps you take to ensure success?

Thanks.

---

### Post by papibe on 2012-03-09
The reason I would save the .bash* files is just to be extra safe. 'Bash' is usually updated from version to version (let's say 10.04 to 11.04). Thus it would be safer to keep the appropriate files to its corresponding version (unless, of course, you customized them).

Although the changes are small (may be a line or two), it is just to be safe.

The directory .ssh/ is another story. IMHO it would be safer to recreate ssh keys and the known host list, instead of just assuming the old ones. But again, it is just an extra precaution.

About the permissions:

Although rsync's option -a could seem like a simple option, it is actually like a macro. It implies all this options: -rlptgoD
[LIST]
[*]r for recursive.
[*]l to preserve symlinks.
[*]p to preserve permissions.
[*]t to preserve times.
[*]g to preserve group.
[*]o to preserver owner.
[*]and D to handle special devices (not that important for user files).
[/LIST]
BTW, username and password are not modified by rsync, so if you already set those correctly, rsync won't mess with them.

Your method is absolutely valid and will offer the same results.
Kind Regards.

---

### Post by Odyssey1942 on 2012-03-09
Really helpful and interesting. I think I have learned a lot in these exercises. 

Thanks for working me through this.

---

### Post by greymann on 2012-06-03
Just wanted to say papibe for your post.  I had similar problem and instructions worked perfectly.

Regards

---

