---
title: "Var lib not root owned"
date: 2019-04-02
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2019-04-02
Hello,

I recently installed an app from gnome software center as a standard user.

but i am unable to run it when i try to launch from software center,

Tried through terminal and it says /var/lib not root-owned id:id where id mentioned my group number and user number

Note: I tried in standard user and admin user.

---

### Post by shag00 on 2019-04-02
to change ownership
```
sudo chown root:root /var/lib
```

Execute this from /$ prompt. This only changes ownership of the lib directory, to change the sub directories as well
```
sudo chown -R root:root /var/lib
```

---

### Post by Impavidus on 2019-04-03
> **shag00 said:**
> This only changes ownership of the lib directory, to change the sub directories as well
```
sudo chown -R root:root /var/lib
```

**Don't do that.** Not all contents of /var/lib should be owned by root. A recursive chown can do a lot of damage.

---

### Post by weirdygeekpsych on 2019-04-03
@impavidus, can you tell me which is doable as of now ?

---

### Post by Impavidus on 2019-04-03
First, let's see what's wrong. It's not normal that ownership of /var/lib changes spontaneously. It would be nice to know why something went wrong, but we must at least know the extend of the damage. Maybe only one directory is wrong. In that case, there's an easy fix.

Run these diagnostic commands (they won't change a thing):```
ls -al /var
ls -al /var/lib
```
Most files and directories in /var/lib, including /var/lib itself, should be owned by root, but there are some exceptions and if you get them wrong, strange things could happen. The number of exceptions is actually low enough that fixing this should be feasible.

---

### Post by weirdygeekpsych on 2019-04-05
This just list the files with the permission and it has owned by owner

---

### Post by SeijiSensei on 2019-04-05
Some directories in /var/lib are owned by various pseudo-users. For instance, /var/lib/mysql is owned by the mysql user and group. So you cannot just make the whole tree owned by root until you are sure which directories have non-root owners by design.

Seeing the directory listing for /var/lib like Impadivus suggested would allow us to help identify these problematic directories.

---

### Post by weirdygeekpsych on 2019-04-09
@seijisensei, Yes I changed that permission, so if I change the var\lib folder to be owned by root,  the problem solves I guess? or what should I have to do?

---

### Post by Impavidus on 2019-04-10
The only thing we know is that your /var/lib is owned by your ordinary user instead of root. We don't know how this happened and whether that's the total extend of your problem. In particular we don't know if anything is wrong with the contents of /var/lib or its parent directory /var. If at some point in the past you used the command```
sudo chown $USER:$USER /var/lib
```then the command```
sudo chown root:root /var/lib
```will solve the problem. But I don't think that's what happened, because you would have known. Usually when some system directory has a permissions or ownership problem it's just a symptom of a bigger problem. Hence our requests for more information.

---

### Post by weirdygeekpsych on 2019-04-14
@Impavidus, I am using a standard user which I am not allowed to do sudo and even I do it through root , the ls -al commands shows me that /var/lib is owned by my secondary user(from a group of adminstrator) so I can access the files from administrator user.

Hope you understand what I have done in my file accessing between users.

---

### Post by Impavidus on 2019-04-15
As told before, IF the only problem is that your /var/lib is not owned by root, you can solve it with```
sudo chown root:root /var/lib
```However, it's very unlikely that's the only thing that's wrong. Without more details, we can't provide more help.

---

