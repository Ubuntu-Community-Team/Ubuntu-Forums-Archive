---
title: "Searching your system"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Jimmy9pints on 2008-10-31
I have been using Ubuntu (and Mint) for 9 months now, and I still do not know how to search my system. I am looking for a GUI that comprehensively searches my hard disks for any string I give it.

I am sure somebody can tell me how to do this, but in any case I think that if it's not totally obvious, then is it not a great problem for all new Ubuntu users. 

When I go to Tracker Search Tool and enter a search string, it immediately says "Your search returned no results". This happens so quickly that I doubt that it has searched at all. 

I have turned on indexing but this has made no difference. 

Please tell me what I am doing wrong here and give me instructions to rectify things. And if I am not totally stupid, and this indeed a difficulty for new users, then I will raise it as an idea on Ubuntu brainstorm.

Cheers,

James.

---

### Post by jpkotta on 2008-10-31
I don't know how to do it with a GUI.  I use two tools for searching.

slocate is very fast, but limited.  You can only search by filename.  It builds an index of all files on the computer.  By default this is done every night, and you won't find anything that isn't already in the index.
```
locate *file*
```
```
locate -r *regex*
```
If you don't know regular expressions, they are extremely useful.  They are a notation for specifying patterns of text.
```
sudo updatedb # this brings the index up to date
```

find is slower, but extremely powerful.  You can use it to find files by size, date, name, and more.  You can make it run a command on each file it finds.  
```
find -iname "**file*"*
```

---

### Post by cyfur01 on 2008-10-31
The find command can be really handy for finding things when used in tandom with the grep command.

I usually use:```

find . | grep -i pattern

```
That will recursively search from the current folder and will print out all files and folders that match the search pattern.

If you're looking for code in a bunch of files, you can also use find and grep:```

find . -type f -exec grep -inH pattern {} \;

```
That will recursively search the current directory and subfolders, searching through each file for "pattern". The "-nH" options print out the line number and file the matches were found in.

[More on find.]("https://help.ubuntu.com/community/find")

---

### Post by Jimmy9pints on 2008-10-31
Well thanks guys for your replies. And I think I can handle the command line stuff now. But given these methods, does that not mean there's a major problem for new users getting a very essential function to work?

---

### Post by Sorivenul on 2008-10-31
The commandline tools work fine for me.  However, I understand Catfish might have this sort of functionality and can use various search backends to help users locate files, etc.  I know it's in the repository, but do not know if it comes in the default installs yet.

---

