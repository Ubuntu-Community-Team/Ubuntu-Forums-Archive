---
title: "Bash and file permisions..."
date: 2010-03-12
forum: Programming Talk
---

### Post by Beezleray on 2010-03-12
Hi,
I could use some help. I'm writing a little bash script that allows students to submit their source code files directly to their professor on a linux server. The file system is set up something like this:

/home/classes/cs101/
/home/students/bob/

What I'm trying to do is allow bob to cp a file into the cs101 folder without the user actually having access to the folder. So that students can submit their files but not be able to see whats in the directory, cd into it or change any files within the directory. I am able read from a file within cs101 (the instruction file the professor writes to state what files he'll allow into the folder), but can't figure out what permissions to use to allow this.

Any help would be great.

---

### Post by prshah on 2010-03-12
> **Beezleray said:**
> The file system is set up something like this:
/home/classes/cs101/
/home/students/bob/

allow bob to cp a file into the cs101 folder without the user actually having access to the folder. students can submit their files but not be able to see whats in the directory, cd into it or change any files within the directory. I am able read from a file within cs101 but can't figure out what permissions to use to allow this.

I would suggest a setup as follows:

create a new group (eg, cs101g) and assign all students to it. Then, give the ownership of the /home/classes/cs101 to classes:cs101g (group cs101g). Then, give full permissions to classes, and change group permissions to only "w"rite, no "r"ead or e"x"ecute (which will allow directory listing, cd etc). However, note that the entire chain in /home/classes will have to give write permissions to "others" so it will be better to have a separate directory (such as "/classes").

Eg```

sudo addgroup cs101g
sudo adduser bob cs101g
sudo chown classes:cs101g /home/classes/cs101 
sudo chmod 722 /home/classes/cs101

```

---

