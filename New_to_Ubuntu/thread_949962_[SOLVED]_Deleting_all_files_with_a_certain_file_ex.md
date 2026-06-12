---
title: "[SOLVED] Deleting all files with a certain file extension"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by saj0577 on 2008-10-16
1.) Deletes all files that are not .mp3 inside a folder(searches inside all sub-folders)
2.) Deletes any empty directories (not essential)



Short and sweet.Any solution to that would be great.
Thanks in advance
Saj

---

### Post by Sarmacid on 2008-10-16
Not sure about the mp3s, guess you'd have to play around with find. For more details run

```
man find
```

As for the empty folders

```
find <path> -empty -type d -exec rm -r '{}' \;
```

When I tried it, it was returning some errors, but worked anyways

---

### Post by Sub101 on 2008-10-16
EDIT: Sorry just re read what you said. Anything thats NOT an MP3. My post will remove all mp3's.

Not tested but something like:

```
cd {folder of choice}
rm *.mp3 
```
That should work. Just be very careful with the rm command. 
I just tried it with a made up extension of .abc on my desktop and it worked fine.

---

### Post by Sub101 on 2008-10-16
I assume there is not a great deal of file extensions in your folder could you not remove each extension one at a time? And to include sub-folders the -r option would work.

---

### Post by Idefix82 on 2008-10-16
For 1. I think this should work (just tested it):
```
rm -r *[^.mp3]
```

By popular demand:
edit: be warned that this command will do what the original poster wanted it to do - delete all files which don't end with ".mp3" from the active folder and all subfolders.

---

### Post by randy78 on 2008-10-16
> **Idefix82 said:**
> For 1. I think this should work (just tested it):
```
rm -r *[^.mp3]
```

Just BE SURE that you're in the directory where the files and folders are located that you want to remove...

Otherwise, this could be disastrous.

---

### Post by Idefix82 on 2008-10-16
Obviously.

---

### Post by randy78 on 2008-10-16
> **Idefix82 said:**
> Obviously.

Yeah, obviously... but what if this person is a brand new user?
How obvious would it be to them then?

Take Care
:popcorn:

---

### Post by fenian on 2008-10-16
Here is a another way to do it,2 more steps but gives you more of an idea of what you are actually deleting...

Open a terminal and cd into the directory with your mp3 files (I'll use $HOME/music as an example)

> cd $HOME/music

next run...

> find . \( \! -name "*\.mp3" -type f \) -print0

(should list all the files that are not .mp3)

next run...

> find . \( \! -name "*\.mp3" -type f \) -print0 | xargs -0 echo

If the files listed are what you want gone go ahead and run...

> find . \( \! -name "*\.mp3" -type f \) -print0 | xargs -0 /bin/rm -f

Files should be gone and you may have a little more assurance that nothing you wanted was deleted by mistake.

---

### Post by Idefix82 on 2008-10-17
> **randy78 said:**
> Yeah, obviously... but what if this person is a brand new user?
How obvious would it be to them then?

Take Care
:popcorn:

Relax. It was pretty clear to me that a person with twice as many posts as me and advertising himself as Beta-tester in the signature is not a brand new user.
I really don't understand why you are having a go at me for answering his question. I am sure that it was clear to him that deleting recursively all files which do not satisfy some criterion can be dangerous if you are careless. Nobody on these forums has lost any files he didn't want to lose because of me and I have helped a fair few people, among other things to get rid of things they didn't want.

Next time, just read the posts properly.

---

### Post by saj0577 on 2008-10-17
Thanks everyone, sometimes the simple stuff is the stuff you need help with.

Thank you for your inputs, I am going to give them a try in a minute.

@Sarmacid  Thanks for the method on the empty directories.

@Idefix82 Thanks for the method on deleting all none .mp3 files. Just in future I know I do not apppear to be a New user,(although I am a beginner on many areas still), but there may be new users that read these threads so just make it clear.

@randy78 Good point just keep it civil,I am not having a go at anyone just saying.

@fenian Spot on method thanks will certainly give it a try.

Thanks,
Saj

---

### Post by saj0577 on 2008-10-17
P.s I will mark as solved when i have tried and got it to work. :)

Saj

---

