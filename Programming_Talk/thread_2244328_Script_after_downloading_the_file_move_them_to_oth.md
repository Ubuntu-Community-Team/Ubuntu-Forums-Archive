---
title: "Script after downloading the file move them to other location"
date: 2014-09-15
forum: Programming Talk
---

### Post by boby4 on 2014-09-15
Halo.
 I need this kind of script when firefox finish downloading the file to default folder compare the file name with file included list of files, if find the name in the filelist move this file to the specifed location.

Please help

---

### Post by dave131 on 2014-09-15
Let me see if I understand this correctly:

- if you had 3 file name lists:

list 1:  filea, fileb, filec

list 2:  filed, filee, filef

list 3:  fileg, fileh, filei

And you wanted:

- any file name in list1 to go to myfolder1
- any file name in list2 to go to myfolder2
- any file name in list3 to go to myfolder3

Then you want this automated?  I assume you would still manually execute the script after a download?

Does the file name matching go by the "front part" of the name:   filex.zzz would match on filex

- or- 

Does the entire file need to match:  filex.zzz would only match on filex.zzz

Do you want existing files of the same name overwritten or do you want them archived in some way?

[COLOR=#0000cd]*EDIT:  I should have added:  it's possible to do all of this within a script quite easily, and can be as simple or complex as you want.   A simple 'if' statement with grep searching for the file name in each of the filename list files followed by the command(s) to (1) archive if you want to (2) move the file from Downloads to the specified folder.*[/COLOR]

---

### Post by dave131 on 2014-09-16
If you still want something like this, I could help you with 1 approach.  There are a lot of people here quite versed in the shell (I'm not, but could still do it) that would probably have a cleaner way.

---

### Post by ofnuts on 2014-09-16
Hmmm. Maybe what you need is a Firefox plugin that runs when downloads end. But if you are downloading so many files that you need a script to move them around afterwards, maybe you could skip the Firefox part and use wget or curl to download them directly?

---

### Post by boby4 on 2014-09-16
To dave131 
> Then you want this automated?  I assume you would still manually execute the script after a download?
Yes i want automated.
> Does the entire file need to match:  filex.zzz would only match on filex.zzz
Yes like that.
> 
Do you want existing files of the same name overwritten or do you want them archived in some way?
I want existing files of the same name.

Please write this script, I will be very grateful
Im green from linux at all and scripting is magic for me, if i see ready solutions then maybe i start understand something.

---

### Post by Vaphell on 2014-09-16
if you want to convince others to help you, especially out of the goodness of their hearts, you should bend over backwards to make sure they know what you need exactly. People have to pull the information out of you by force, why should anybody bother to help you if you can't even find 5 minutes of time to describe the problem and its corner cases in detail? They will spend much more writing it.

[I]
Yes like that.
I want existing files of the same name.[/I]
are not valid functionality descriptions because what these mean *exactly*?



Give solid black on white examples, eg:

[I]- I have a file1.txt, zomg.jpg, myporn.doc in my whitelist

- If something like file1.txt lands in the browser's DL dir, the file gets moved to dest dir X or Y or Z depending on the name

- X, Y, Z defined in the whitelist file next to each filename.

- If the filename is already in use in the dest dir, i need versioning (numbers or date appended to the filename). Assuming numbers, conflicting file1.txt landing in its dest dir should have v#N attached to its name, #N being integers in ascending order.[/I]
[I]file1.txt
file1_v2.txt
file1_v3.txt[/I]


also you haven't answered the question if automating downloads themselves would not be better than downloading manually via webbrowser.

---

### Post by anika200 on 2014-09-16
This has already been done for you ..... look at source forge for a project named "Maid".

Whoops, it moved to Github [https://github.com/benjaminoakes/maid](https://github.com/benjaminoakes/maid)

---

