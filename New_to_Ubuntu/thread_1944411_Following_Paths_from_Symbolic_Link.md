---
title: "Following Paths from Symbolic Link"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by Andavane on 2012-03-21
After upgrading to Ubuntu 11.10, all my attempts to get the Moneydance running, failed. So I am trying another way round, by using the unix tar file.
I've untarred it following this:
> untar the downloaded file (using the command "tar xzf moneydance_other.tar.gz") which will create a directory named "moneydance". In that directory, create a symbolic link from "jre" to the directory where Java is installed on your system (for example "cd moneydance; ln -s /usr/java1.4 jre"). You can then run the "moneydance" script in the new directory to start Moneydance

It's untarred but my  difficulty is in writing the script, of which I have no experience. I'm happy to have a go but have very little idea of how exactly to write it, or which tutorial to use. Using the standard installation directions simply doesn't work for this program since 11.10.

Regards

John

---

### Post by mcduck on 2012-03-21
Based on those instructions, you shouldn't need to write any script, it's already in the package.

Just create the symbolic link as the instruction suggests.

---

### Post by Andavane on 2012-03-21
> **mcduck said:**
> Based on those instructions, you shouldn't need to write any script, it's already in the package.

Just create the symbolic link as the instruction suggests.

Yes that  is what I am trying to do. I don't really understand where the java is in 11.10

I can see that ""cd moneydance; ln -s /usr/java1.4 jre"" is not the path. I understand that ln in the command line = link
but don't know what the -s in the line is.

Regards, John

---

### Post by mcduck on 2012-03-21
You should be able to run "which java" in a terminal to get the correct path to the Java executable.

And what comes to the command, "ln" is the command used for creating links, and the "-s" option for ln tells it to create a symbolic link.

---

### Post by Andavane on 2012-03-21
> **mcduck said:**
> You should be able to run "which java" in a terminal to get the correct path to the Java executable.

And what comes to the command, "ln" is the command used for creating links, and the "-s" option for ln tells it to create a symbolic link.

aaah which java... very handy.
I get this "usr/bin/java"

Now within the moneydance folder is this (in uploaded attachment).
Now the instructions say "create a symbolic link from "jre" to the directory where Java is installed on your system" but there is no "jre" in the folder so which file do increate the link from?
Regards, john

---

### Post by Andavane on 2012-03-22
I'm nearly there I think.

On a spare laptop I got it working fine.
On this think I show the lines I typed and what is said:

> andavane@andavane-think:~$ cd moneydance
andavane@andavane-think:~/moneydance$ 
andavane@andavane-think:~/moneydance$ which java
/usr/bin/java
andavane@andavane-think:~/moneydance$ ln -s/usr/bin/java
ln: invalid option -- '/'
Try `ln --help' for more information.
andavane@andavane-think:~/moneydance$ ln -s /usr/bin/java
andavane@andavane-think:~/moneydance$ moneydance
moneydance: command not found
andavane@andavane-think:~/moneydance$ 


---

### Post by EzioAuditore on 2012-03-22
> **Andavane said:**
> I'm nearly there I think.

On a spare laptop I got it working fine.
On this think I show the lines I typed and what is said:

Run the script like this-  ./moneydance

---

### Post by Andavane on 2012-03-22
> **EzioAuditore said:**
> Run the script like this-  ./moneydance

&#10003; :)
Thanks!

---

### Post by EzioAuditore on 2012-03-22
> **Andavane said:**
> &#10003; :)
Thanks!

your welcome.

---

