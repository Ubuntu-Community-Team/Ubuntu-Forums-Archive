---
title: "how to make files invisible dispite renaming them (.) one by one"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-07-04
how to make existing folders and files invisible dispite renaming them (.) one by one?

---

### Post by ibutho on 2008-07-04
AFAIK, you can't make them invisible. If you don't want people to access certain files and directories, then look at encrypting them.

---

### Post by the_hardy_kid on 2008-07-04
This can be done by creating a text file called 
```
.hidden
```
and then writing the names of the folders you wish to hide in the file.

eg, you have a file called hello.
you would make the .hidden file and inside it write

.hidden
hello

hope this helps

---

### Post by hyper_ch on 2008-07-04
or you can make a hidden directory and put all the files in there...

---

### Post by Archmage on 2008-07-04
> **ibutho said:**
> AFAIK, you can't make them invisible. If you don't want people to access certain files and directories, then look at encrypting them.


I think removing the permision of everybody else to read the file should work.

---

### Post by Frozsyn on 2008-07-04
It really depends on what you really want to do:
- You can prevent any other user to access to the content of a directory or file by changing their permissions.
- You can use the terminal to "script" a quick renaming of a set of directory
- You can encrypt your files

I'm not sure to understand your goal. Which of my propositions fits better your need ?
(EDIT: Ok, just the time to write my message and every propositions have been done)

---

### Post by Troll_the_Great on 2008-07-04
I would suggest what hyper_ch said... It's easy to create a hidden folder and then to move into it all that you want to hide.And to be absolutely sure you can limit the permission to that folder and you're done :)
Cheers!

---

### Post by t0p on 2008-07-04
> **the_hardy_kid said:**
> This can be done by creating a text file called 
```
.hidden
```
and then writing the names of the folders you wish to hide in the file.

eg, you have a file called hello.
you would make the .hidden file and inside it write

.hidden
hello

hope this helps

That's cool.

---

### Post by afeasfaerw23231233 on 2008-07-20
thanks all your suggestions!

---

### Post by Dedoimedo on 2008-07-20
Hi,

You can also make another cool trick.

Pluggable Authentication Modules (PAM)

The access.conf defines who can access which resources from where. Adding entries to this file allows access or denies access to resources.

This is a great way of policing the system.

For example:

Adding this to the access.conf file

- : dedoimedo : ls : ALL

will prevent user dedoimedo from using the ls command, preventing him from being able to get directory listings.

Of course, you can narrow this down further - or expand.

PAM are a great policing tool - just be careful not to lock yourself out of the system, always make backups!

But this is definitely a centralized way of doing things, and probably the least likely to get circumvented by culprits.

Dedoimedo

---

### Post by Sawubona on 2008-07-20
> **the_hardy_kid said:**
> This can be done by creating a text file called 
```
.hidden
```
and then writing the names of the folders you wish to hide in the file.

eg, you have a file called hello.
you would make the .hidden file and inside it write

.hidden
hello

hope this helps

This is a great tip. Just wondering:

Will this only hide files by the name hello(for example) in the directory that the .hidden file is in? or will it apply to all files named hello on the drive?

---

### Post by mcduck on 2008-07-20
You'll need to create a different .hidden file in every directory where you want to hide files/directories.

---

### Post by steveneddy on 2008-07-20
> **afeasfaerw23231233 said:**
> thanks all your suggestions!

That's it?

No reason why you need files hidden.

Permissions issue?

Encryption on a server?

You never answered the question of why you need files hidden.

Answering this question will give more insight into the correct answer we give you.

You have about 10 different people giving answers, but no reason why you need files to be hidden. Answering the question of why you need to hide files would give the answer that you are looking for, I believe.

---

