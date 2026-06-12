---
title: "Bash script help!"
date: 2009-01-24
forum: Programming Talk
---

### Post by gjoellee on 2009-01-24
I am currently working on a program which consists of HTML files and bash scripts. It is on rolling releases, but I encountered a problem when i tested this script (below). It will check for updates by downloading and extracting a tarball then launching the script inside it which will will replace an "index.html" file in the system which is the front page for the program I am making. On the index.html file that replaces the old file it will say if any updates is available.
```
#!/bin/sh

echo "Checking updates:"

echo "Selecting directory"

cd /home/$USER/.ksarchv/

echo "Downloading"

sudo wget http://www.kshoster.net/downloads/ksarchcheck.tar.gz

echo "Extracting"

sudo tar -xzf /home/$USER/.ksarchv/ksarchcheck.tar.gz -C /home/$USER/.ksarchv

echo "Launching script"

sh /home/$USER/.ksarchv/ksarchcheck/install.sh
```It downloaded the tarball and extracted it and then again started downloading the tarball, and just downloaded it again and again. What is wrong?

The script it moves to (install.sh) looks like this:
```
#!/bin/sh

echo "Writing information..."
sudo cp /usr/share/kshoster/ksarch/contents/html/index.html /home/$USER/.ksarchv/index.html
echo "Information is written"
echo
echo "Starting Ks Arch"
cd /home/$USER/
sh .ksarch.sh
```

---

### Post by slavik on 2009-01-24
what is in the following script?

.ksarch.sh

---

### Post by sisco311 on 2009-01-24
You don't need root permissions to download and extract the script.

---

### Post by skoorbevad on 2009-01-24
Well, a few things here:

1) What is in the ksarchv.sh script that the install.sh script is calling?  Is that the original script?  If it is, there's the problem with your loop.

2) Remember, whenever possible you may wish to use 'mv' instead of 'cp', as file copy on EXT2/EXT3 is not a fully atomic operation.  (Technically, 'mv' isn't either -- but it's better)

3) Seeing how you're moving files around, you may wish to consider utilizing 'set -e' at the beginning of your script, which will cause the script to exit immediately on any non-zero return value.

For instance, what happens if the wget fails?  Then the tar fails.  Then the next script is launched, and you end up with an index.html file in the directory and nothing else.

You can bypass the automatic exit of the script in a 'set -e' environment by doing something like:

```

tar -zxvf $FILE || { echo "$FILE not found!"; exit $?; }

```

This will also save you writing in tons of if..then loops checking exit status and the proper existence of necessary files.

---

### Post by slavik on 2009-01-24
what do you mean cp is not fully atomic?

---

### Post by gjoellee on 2009-01-25
Hey, I solved to problem. I was so smart that one of the scripts re launched .ksarch.sh (the first script). Not weird it just repeated itself all the time!

---

### Post by gjoellee on 2009-01-25
Thanks for the help here, I got it "stable" and it is time to add more features to this. Take a look at the first "Pre Alpha" of the script here:  [http://kshoster.net/content/ks-arch-v01-pre-alpha-1-released](http://kshoster.net/content/ks-arch-v01-pre-alpha-1-released)

NOTE: It is designed for Arch Linux, I am currently working on Ks Ubu which is the same as Ks Arch but for Ubuntu

I would like to have some tips etc...

---

### Post by skoorbevad on 2009-01-26
> **slavik said:**
> what do you mean cp is not fully atomic?

Well, 'mv' isn't really atomic either, especially if you're moving across filesystems, but I'm ignoring that bit and assuming that we're dealing with one filesystem for this example.  And of course it may be trivial if you're only dealing with a small bit of data that can easily be rolled back if any corruption on the write process occurs.

Since 'cp' is copying the data bit for bit to a new location with a new inode(s), other processes can interact with the incomplete data and the possibility of bad things can occur.  Again, take this with a grain of salt -- if we're copying a small amount of data on a fast drive, maybe this isn't a huge issue.

It may be better to copy the data into a temporary location away from any other meddling processes, and then simply use 'mv' to swap the inode once the copy operation completes.  The swap then becomes nearly instantaneous as you're only dealing with inodes and not the data as a whole.

Some other filesystems (zfs off the top of my head) use a "copy-before-write" scheme which can greatly mitigate this risk.

So it's best to gauge based on what you're doing -- it's just something I like to keep in mind when writing scripts, especially if they're in a production environment and the end goal is data accuracy and stability.

---

### Post by slavik on 2009-01-26
makes sense, then there is also ability to lock the file so that nobody else can open it ;)

---

### Post by skoorbevad on 2009-01-26
...also a possibility, but be mindful of the operation at hand.

If we're copying a huge chunk of data that may take several seconds, even minutes, to complete -- locking the files before the copy operation finishes may be detrimental to application availability.  It's probably a non-issue for the purposes of this thread and the scope of this specific script, of course, but it can come into play in production environments.

A copy -> move operation will incur much less application downtime, and the locking you mention can still be applied for better success and a lesser chance of data corruption.

Good call, though! :)

---

### Post by slavik on 2009-01-26
well, the answer to "What is the best procedure to copy/move a file?" is the same as the answer to any Comp Sci question ... "It depends." ;)

---

### Post by skoorbevad on 2009-01-26
Tmtowtdi ;)

---

