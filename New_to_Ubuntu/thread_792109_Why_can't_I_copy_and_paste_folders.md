---
title: "Why can't I copy and paste folders?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by leotemp on 2008-05-12
For some reason i cannot copy and paste folders only files, if I need to copy a folder to another location I have to open the folder, copy the files and then recreate the folder in the desired location and then past the files in the new folder, this of course takes forever with large structures, help!

---

### Post by mpince on 2008-05-12
You could zip the folder. That way you would maintain the folder structure.

---

### Post by leotemp on 2008-05-12
I could but shouldn't i be able to just copy and paste folders?

---

### Post by mpince on 2008-05-12
Yep. You should be able to copy/paste a folder though.

---

### Post by DBrocks on 2008-05-12
```
sudo cp -a /path/to/folderWITHOUTASLASHATTHEEND! /where/you/want/folder/to/go
```

---

### Post by leotemp on 2008-05-12
right, i realize i could do it from the term but is this is a bug in gnome or something? It doesn't work from the gui..

---

### Post by DBrocks on 2008-05-12
I really don't know. I do not know. I pretty much live on the command line. the gui is too complicated for me :lolflag:

---

### Post by Mr A Mouse on 2008-05-12
Could it involve file permissions? I just tried on Heron and it worked like a charm.

---

### Post by leotemp on 2008-05-12
Doesn't look like it, i just set it to the maximum available option "Create and delete files" and still cannot copy and past in gnome. FYI I am also using Hardy

---

### Post by Mr A Mouse on 2008-05-12
Hmmm. Try to create a folder in your home directory, and c/p it to your desktop. That way we can see the basics of whether or not c/p works on your system.

---

### Post by BlueSkyNIS on 2008-05-12
Are there copy/paste options in right click menu?? Or they just don't work?

If those options are in gray color, then you probably have problem with some permissions. In order to see what permissions you do have then right click on it goto properties->permissions tab ;)

---

### Post by guildofghostwriters on 2008-05-12
I think it is about permissions. I've just tried and was able to cut and paste folders, including contents, in places like documents, media etc. The other stuff on the file system you just can't do that - try doing sudo nautilus in the terminal and see if you can copy paste the folders you want to then.

BTW - I'm a total noob and in checking the above out I made the mistake of trying to copy the folder 'documents' into itself which it tried to do into infinity until it produced an error. God knows how many copies of itself it had made before the error.

---

### Post by leotemp on 2008-05-12
Yes, that worked. I am attempting to copy a folder from Documents to var/www
perhaps there is something special about these folders?

---

### Post by Mr A Mouse on 2008-05-12
That may be it--check to see who owns /var/www

---

### Post by guildofghostwriters on 2008-05-12
As I say, total noob, but from what I've worked out so far, anything that's important and unwise to mess around with, you can't write to unless you're super user or root. It's like if you gedit xorg.conf you can't save changes, which is why you always sudo gedit when you're making changes to configuration files. It's just an extra level of security to prevent idiot noobs like me totally lousing up the system. Which, I guess, means we should be extra careful when we cut and paste after sudo nautilus.

---

### Post by Mr A Mouse on 2008-05-12
Total n00b or not, you hit the reason for why things are done this way on the head. :D

---

### Post by leotemp on 2008-05-12
AHA! its owned by root, which makes sense now that i think about it, i guess ill just start my static docs on the web server from now on. Thanks for all the help to those involved.

---

### Post by leotemp on 2008-05-12
> **guildofghostwriters said:**
> As I say, total noob, but from what I've worked out so far, anything that's important and unwise to mess around with, you can't write to unless you're super user or root. It's like if you gedit xorg.conf you can't save changes, which is why you always sudo gedit when you're making changes to configuration files. It's just an extra level of security to prevent idiot noobs like me totally lousing up the system. Which, I guess, means we should be extra careful when we cut and paste after sudo nautilus.


Well your not a noob, your an ***. :P

I meant that in fun in case you take things a little to serious.

Oh and did you mean to imply that i can sudo start Nautilus and then paste however i want *DESTROY!!*

---

### Post by guildofghostwriters on 2008-05-12
> **leotemp said:**
> Well your not a noob, your an ***. :P

I meant that in fun in case you take things a little to serious.

Oh and did you mean to imply that i can sudo start Nautilus and then paste however i want *DESTROY!!*

I can't work out any insulting swear words with only 3 ***s but then over here in blighty idiot noobs are arses rather than asses.

---

### Post by leotemp on 2008-05-12
> **guildofghostwriters said:**
> I can't work out any insulting swear words with only 3 ***s but then over here in blighty idiot noobs are arses rather than asses.

Can't I be both? Actually its weird it added an extra "s"

---

### Post by bmcase on 2008-05-12
I bet it is permissions. Type ls -l on the directory to see the permissions for all the files (or subdirectories) in that directory. You should see something like: drwxr-xr-x at the beginning of each file or directory listing, which is read, write and execute permissions for owner, group and all users respectively.

    For example, I am in the process of moving all my music from a Windows PC to my Linux laptop; and when I move them into my Linux "Music" folder they appear with a lock icon and I am unable to copy/paste that folder. Typing ls -l at the /home/me/Music prompt showed me the permissions on the new file to be dr-xr-x--x. This same problem keeps occurring for some reason; but the fix is simple. After I move the music files into that folder, I go to the command line, go to /home/me and type chmod -R 755 Music. After that, the permissions are: drwxr-xr-x, meaning the owner (me) has read, write and execute permissions on all the files in that folder.

   chmod is the command for modifying permissions. The -R specifies it to recursively change all the files or subdirectories in the specified directory to these permissions. The 755 is the octal value for the permissions. 7 is full rwx permissions while 0 is no rwx permissions. 5 is r-x permissions. 

   Be very careful not to change permissions on things you are unsure of. To first fix this, I ran chmod -R 755 on my /home/me directory thinking I should have full rwx permissions on all the files in my home directory. Not so! I advise everyone not to do this!

---

### Post by guildofghostwriters on 2008-05-13
> **leotemp said:**
> Can't I be both?

I think you're managing to be both without my permission... :P

---

