---
title: "Nautilus Actions for Dummies..."
date: 2012-01-20
forum: New to Ubuntu
---

### Post by 2CV67 on 2012-01-20
Sorry if this is cross-posting, but I think I need assistance that a different title might help.
It has already been mentioned here:
[http://ubuntuforums.org/showthread.php?t=1691638](http://ubuntuforums.org/showthread.php?t=1691638)

I have a script for renaming selected folders, which has been successfully activated by Nautilus Actions in Ubuntu for about a year.

After upgrading to 11.10, Nautilus Actions no longer works & I have installed a newer version (3.1.5-1) via GetDeb.

The interface is different now & I don't have the original data, so I have tried to set up an action, without really understanding what I am doing.
The result is that I see the new action when right-clicking on a folder, but the script does not execute.

Can I find a simple guide anywhere, or can anybody suggest where I am going wrong?
I suspect I may be getting my %d's & %f's in a twist...

Thanks!

This is the script (kindly provided by cjhabs):
```
#!/bin/bash
folder=$1
file=$2
parent=`echo $folder/$file | awk -F '[|/]' '{parent=NF-1;print $parent}'`
grandparent=`echo $folder/$file | awk -F '[|/]' '{grandparent=NF-2;print $grandparent}'`
mv $folder/$file $folder/${grandparent}_${parent}_$file
```

& my attempted N-A:

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/PhotoRename.png[/IMG]

---

### Post by 2CV67 on 2012-01-23
I tested this version (3.1.5-1) of N-A with a simpler script, without parameters, and that works OK!

Then I went to my (backup & almost empty) LTS 10.04 Ubuntu & installed the available Nautilus Actions (2.30.2-0Ubuntu1-i386).
I made a "Scripts" file in /home & created a new text file there & copied in the script I am trying to get to work (see previous post) & called it "PhoRen.sh" & made it executable.
In the "Command" tab of N-A, for "Path", I Browsed to PhoRen.sh.
In the "Parameters" area I put "%d %f".
With that it works perfectly...

Recap:
1. In 11.10 with N-A 3.1.5-1, I see all the Nautilus Actions I create OK when right-clicking on my target folder in Nautilus.
2. This Nautilus Actions executes scripts without parameters OK.
3. In 10.04 with N-A 2.30.2... my intended script works OK.
4. In 11.10 my intended script produces no action & no error message.

What can I do or try to debug this?

Thanks for any suggestion!

---

### Post by 2CV67 on 2012-01-26
Can somebody please explain (or preferably point me to a simple clear tutorial...) what is meant by "Working Directory" under the "Command" tab in Nautilus-Actions Configuration Tool version 3.1.5 (see first post)?

For instance, I am playing with a N-A where I click on a Folder in Directory A, which points to a Script in Directory B, which writes to a file in Directory C.
What do they want to see in "Working Directory"?

What is the signification of the %d which seems to be there by default?
I suppose it imports the Directory of the clicked file (in my case A)?

So what?

I am finding that my test N-A with %d works when clicking on folders in my Home Directory, but not anywhere else.
I don't understand what is happening & can't find any simple explanations.

Thanks for any help!

---

### Post by 2CV67 on 2012-01-28
Well - I finally got Nautilus-Actions 3.1.5 to run my previously-OK script, but it was hard work & a lot of groping in the dark!

Boiling it down to the essentials:
1. In Nautilus-Actions Configuration Tool > Command > Working Directory, I had to replace the default %d by the path to my home directory. I have no idea why.
2. Previously, in Command > Parameters, I had "%d %f". Then, %d imported the full address of the clicked-on file/folder's parent directory & %f imported just the local name of the clicked-on file/folder. Now, %f imports the full address of the clicked-on file/folder. So I had to re-write my Script around that change. Again, I don't know why this changed.
3. In a seemingly-random way, the simple Test Scripts I used for debugging often failed when used with the usual "#!/bin/bash" shebang but would be OK with "#!/bin/sh".

I am posting this, not to complain, but:
1. In case it can help anybody else who is struggling.
2. In the hope of finding some simple guides/instructions/explanations for next time!

Thanks!

---

