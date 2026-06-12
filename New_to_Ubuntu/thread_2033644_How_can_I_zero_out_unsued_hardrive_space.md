---
title: "How can I zero out unsued hardrive space?"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by cosmoshell on 2012-07-26
I used to have a script that zeros out unused hardrive space by createing a large random file and was woundering how to do this? Im looking for how to do it by termnal. Does this method usely work with common laptop hardrives? Are there any likely problems from using it on a enrypted drive?

---

### Post by androssofer on 2012-07-26
> **cosmoshell said:**
> I used to have a script that zeros out unused hardrive space by createing a large random file and was woundering how to do this? Im looking for how to do it by termnal. Does this method usely work with common laptop hardrives? Are there any likely problems from using it on a enrypted drive?

the dd command can do this.. well it can make a large file of zeros. 

here is an article about it:[here]("http://www.cyberciti.biz/faq/howto-create-lage-files-with-dd-command/")

---

### Post by cosmoshell on 2012-07-26
> **androssofer said:**
> the dd command can do this.. well it can make a large file of zeros. 

here is an article about it:[here]("http://www.cyberciti.biz/faq/howto-create-lage-files-with-dd-command/")

how do i get it to on its own fill the entire thing withought specifing size parameters in? How do I get it to use 1s and 0s randomly?.

---

### Post by androssofer on 2012-07-26
> **cosmoshell said:**
> how do i get it to on its own fill the entire thing withought specifing size parameters in? How do I get it to use 1s and 0s randomly?.

you can use 

```
/dev/random
```

to generate random stuff in the file. instead of /dev/zero as mentioned in the article... 

not sure how you would get it to it automatically...

could perhaps get a script to access the amount of free space using

```
df -h
```

then get dd to create it that size...

---

### Post by Cheesemill on 2012-07-26
How about running:
```
dd if=/dev/zero of=zero.file; sync; rm zero.file
```while inside the partition you wish to erase.

Is there any particular reason you want to use random data instead of zeros?
Random data will take much longer for absolutely no benefit.

---

### Post by cosmoshell on 2012-07-26
> **Cheesemill said:**
> How about running:
```
cat /dev/zero > zero.file; rm zero.file
```
while inside the partition you wish to erase.

Is there any particular reason you want to use random data instead of zeros?
Random data will take much longer for absolutely no benefit.

I was unaware, i thought it would have a benefit randomizing, agenst forensic tools.

---

### Post by androssofer on 2012-07-26
> **Cheesemill said:**
> How about running:
```
cat /dev/zero > zero.file; rm zero.file
```
while inside the partition you wish to erase.

Is there any particular reason you want to use random data instead of zeros?
Random data will take much longer for absolutely no benefit.

oo, so simple! I like! 

could be something on the partition OP wants covered up? in which case random might do it better... i think?

---

### Post by Cheesemill on 2012-07-26
> **androssofer said:**
> could be something on the partition OP wants covered up? in which case random might do it better... i think?
Nope.

Just one pass of zeros will leave the data unrecoverable from the wiped section of the disk.
One thing to note is that it may not delete everything that you want it to, there can often be copies of deleted files hanging about in other locations (tmp files, cache files etc).

---

### Post by Cheesemill on 2012-07-26
Just edited my original post to use dd instead of cat and add a sync command.

dd fails more gracefully than cat when the drive becomes full and the sync command makes sure that all the data is actually written to disk before the file is deleted.

---

### Post by asmoore82 on 2012-07-26
> **Cheesemill said:**
> Nope.

Just one pass of zeros will leave the data unrecoverable from the wiped section of the disk.

[SIZE="3"]Big +1[/SIZE]

---

### Post by Bufeu on 2012-07-26
> **Cheesemill said:**
> Nope.

Just one pass of zeros will leave the data unrecoverable from the wiped section of the disk.
One thing to note is that it may not delete everything that you want it to, there can often be copies of deleted files hanging about in other locations (tmp files, cache files etc).
Yes, once overwritten, always overwritten. No one can't get data back which have been overwritten, that's impossible.

---

### Post by cosmoshell on 2012-07-26
> **Cheesemill said:**
> How about running:
```
dd if=/dev/zero of=zero.file; sync; rm zero.file
```while inside the partition you wish to erase.

Is there any particular reason you want to use random data instead of zeros?
Random data will take much longer for absolutely no benefit.

where does this save to? my computer is full and cant delete this.

---

### Post by cosmoshell on 2012-07-26
> **cosmoshell said:**
> where does this save to? my computer is full and cant delete this.

nevermind

---

### Post by Cheesemill on 2012-07-26
> **cosmoshell said:**
> where does this save to? my computer is full and cant delete this.
It creates a file called zero.file in whichever directory you were in when you ran the command.

---

### Post by androssofer on 2012-07-26
> **cosmoshell said:**
> where does this save to? my computer is full and cant delete this.

if you open a terminal and run this, it will proably save it to the folder you are currently in. Which is most likely /home/username

where username is the name of the user who ran the command. 

so the file will be:

```
/home/username/zero.file
```

so this would delete it:

```
rm /home/username/zero.file
```

you could do:

```
locate zero.file
```

and it will show the location of the file. 

if it gives you grief about not deleting it. use:

```
sudo rm -f zero.file
```

however USE EXTREME CAUTION WHEN RUNNING THAT COMMAND.

as it can mess things up if you type it wrong.. (toy story 2 was nearly lost forever due to a miss typing of that command. True story: [source]("http://www.youtube.com/watch?v=EL_g0tyaIeE&feature=player_embedded"))

---

### Post by cosmoshell on 2012-07-26
> as it can mess things up if you type it wrong.. (toy story 2 was nearly lost forever due to a miss typing of that command. True story: [source]("http://www.youtube.com/watch?v=EL_g0tyaIeE&feature=player_embedded"))

I remember that story.

---

