---
title: "Changing permissions for all files on my mp3 players"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by grey1beard on 2013-04-12
I've just bought several old mp3 players, and found that they all function correctly.
The problem I face is that having recorded some background noise a few times while experimenting, I find that I can only delete them via the laptop.
I've looked at the permissions of the files, and the top directory(Record) is drwx----, but the .wav files in it are -rw-r--r--.

It's a long time since I needed to change the permission on a file, so I looked at the File Permissions page in Ubuntu documentation. Not too clear if it's possible, or how, to set a global permission for me to write/delete these and any future file I record.

Need nanny to guide me through the process :(

John

---

### Post by leclerc65 on 2013-04-12
I'd change me as owner of the partition that I keep my data in, and be done with.
Too old to learn new stuff.
I tried Fedora once then quit because I could not cope with Selinux.
I used to work as Security Officer of an IBM mid system !

---

### Post by ado464 on 2013-04-12
chmod -R 777 *.mp3

gives rights to all users - read, write and edit.

cheers 

Adnan.T

---

### Post by Routhinator on 2013-04-12
You haven't mentioned what the directory is, so I'll use the example /mnt/example

```

chmod -R 666 /mnt/example

```

This will make all the files in that directory able to be read/written to by anyone on the system.

You could also chown the files to your user, since the owner of those files already has RW permissions:

```

chown -R youruser:youruser /mnt/example

```

The -R is for 'recursive' which means it will go into subdirectories.

---

### Post by grey1beard on 2013-04-12
Hi Adnan.T - Thank you Nanny ;)

Hi Routhy, perhaps I should have added that my wife will also be using the players, on her own system after we've worked out the navigation on these things, so they would need to have all users permission to write etc.

EDIT
If I could find it, I'd use the tool to mark this thread as solved.
But as the designers of the layout have moved it from *Thread Tools* to **somewhere more obvious**, I can't find it.

---

### Post by Routhinator on 2013-04-12
That's fine, however I do recommend setting them as 666 and NOT 777 - There is no reason for an MP3 to be set executable. 7 = Read/write and execute.

---

### Post by grey1beard on 2013-04-13
> **grey1beard said:**
> 

EDIT
If I could find it, I'd use the tool to mark this thread as solved.
But as the designers of the layout have moved it from *Thread Tools* to **somewhere more obvious**, I can't find it.

Had to google to find instructions :(

So instead of a single step in Thread Tools, we now go back to our first post, click Edit, click Advanced, click Prefix, click Solved, click Save Changes.

And this is of course much better for everyone.

Er, sorry ? How is this better ?

Grumplestiltskin, aka John

---

### Post by coffeecat on 2013-04-13
> **grey1beard said:**
> Had to google to find instructions :(

So instead of a single step in Thread Tools, we now go back to our first post, click Edit, click Advanced, click Prefix, click Solved, click Save Changes.

And this is of course much better for everyone.

Er, sorry ? How is this better ?

Instead of posting snippy comments, or googling for that matter, you could have gone to the obvious place, [a sticky in Forum Feedback & Help]("http://ubuntuforums.org/showthread.php?t=2121377"), where there is an explanation of why Mark as Solved is temporarily missing from Thread tools, together with the workaround you have found.

---

### Post by grey1beard on 2013-04-13
> **coffeecat said:**
>  .......you could have gone to the obvious place,...... ..

Hi coffeecat, and thank you for your reply.
Pity you didn't reply to my *obvious* lack of knowledge in my earlier post, but perhaps I was making my request for help too obscure.
But then at my age, what can you expect. I'd betty heat up my milk, say goodnight to Matron, and toddle off to bed.

Regards,
John

---

### Post by leveller on 2013-04-13
Thank for you the chmod tip. I happened to be learning some network commands including chmod, this week (complete beginner). This thread has reminded me of the trouble my Mac gave me when I tried emptying the trash and it said I didn't have permissions. I now wonder if it does this again in future, I can use chmod to release the file permissions.

I think the error occured because I copied and pasted some files from an old install to a spare disc, formatted the computer, then copied the files back into my new OS install. I could be wrong - but I assume I may have created a different username than my previous install.

Anyway, cheers guys!

---

