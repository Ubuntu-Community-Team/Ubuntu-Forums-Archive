---
title: "cp command weirdness and rsync question"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-04-28
Hi Guys,

I have a strange situation:

For a long time I've been using a script with the command:

```
cp -r ~/source/ ~/Insync/google_address/destination/
```

A few days ago I noticed that I was ending up with a source folder inside my destination folder, which is not what I wanted. So I modified the command to:

```
cp -r ~/source/* ~/Insync/google_address/destination/
```

Things seemed to be working nicely.

Then, I decided I wanted to add another folder to the backup script.  I also wanted to backup my ~/notes folder to the Insync folder.
So I added this:
```
cp -r ~/notes/* ~/Insync/google_address/destination/
```

Here is the weird part:
When the script ran, the contents of ~/notes were moved (or copied and then deleted from) ~/notes.

I really do not understand why.

So, I Googled and found how to do this with rsync.

```
rsync -r -t -v --progress -s /home/gg/notes /home/gg/Insync/google_address/
```

So far so good, in fact so good I thought why not replace all of my backup cp commands with rsync?
Well, I have gotten into the habit of unhiding hidden files and folders when I back them up. example: .bash_aliases is backed up as simply bash_aliases.  The reason being if I don't see the backed up file, I **will** forget that it is there.  In the same vein I have a couple of hidden folders that I backup without the .

That long winded intro leads to this question:  Can I back up a hidden file or folder using rsync and have the backed up folder not be hidden? That is .bash_aliases to bash_aliases, for example?

---

### Post by GrouchyGaijin on 2013-04-28
Update:  OK I'm a goof.  I see that rsync will copy single files and let you change the name just as I wanted.

---

