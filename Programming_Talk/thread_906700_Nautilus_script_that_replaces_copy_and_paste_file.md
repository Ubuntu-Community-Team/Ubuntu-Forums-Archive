---
title: "Nautilus script that replaces copy and paste file?"
date: 2008-08-31
forum: Programming Talk
---

### Post by wgw on 2008-08-31
I would like to write a Nautilus script that will use a script with cp to copy files instead of the normal paste in Nautilus.  (Sounds redundant, doesn't it? I explain below.) I need to replace files without moving them to the trash. I am most comfortable with python, but can muddle through bash. 

My problems: 

1) Is there a variable with the list of files that have been selected with ctrl-c ?  NAUTILUS_SCRIPT_SELECTED_FILE_PATHS tells me what is presently selected, but if I move to another directory to do the paste, that value changes (AFAIK). I don't see how I can select the files, run the script that grabs NAUTILUS_SCRIPT_SELECTED_FILE_PATHS, then navigate to another directory (while the script is running?), then tell the script to paste the files in the new directory (especially if it is in a different Nautilus window).

2) How does python get access to the Nautilus variables? (Sorry, being lazy; haven't really experimented with that question). 

3) Is there a comprehensive tutorial for Nautilus scripting that would answer such questions (especially python oriented)? 

Thanks for any suggestions!

PS: I am trying to do a workaround for managing files on Blackboard's webdav. When Nautilus overwrites a file it moves the old version to .Trash-user. Under Blackboard that is causing problems, because it catalogs the files on the system and follows the moved file to the trash. If I use cp, which simply overwrites the old version of the file, all works as expected. So I am trying to write a shortcut to do a "no trash" file replace through Nautilus. (Nautilus does have a "no-trash" delete, but not a no-trash replace.)

---

### Post by slavik on 2008-08-31
one way would be to save the paths to /var/run/copy-script.list or some such and then on paste to check the file for the list ...

---

### Post by wgw on 2008-08-31
Yes; that's a start -- or maybe an environmental variable, which could be set to a file list or used to copy the filelist (and set to zero after copying so the code will know nothing needs to be copied).

---

### Post by slavik on 2008-08-31
basically, you can have 2 scripts ... one that saves the list of files (full paths) and another that actually pastes them ...

you wouldn't even need Python here, sh can handle this job, since you just need to use simple shell commands.

NOTE!!!! I have not tested the code below and it should be considered approximate pseudo code

for copying
```

#!/bin/sh
#no idea if you need to preprocess the file list ...
echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > /var/run/copyscript/filelist

```

for pasting
```

#!/bin/sh
for i in [cat /var/run/copyscript/filelist];
do
  cp $i $variable for current directory;
done
rm /var/run/copyscript/filelist

```

---

### Post by wgw on 2008-09-01
Thanks for the code -- I can read bash but not write it!

A couple of variations/ questions: 

1) Is /var/run/ writeable by the script? I am tempted to use something in my home directory, like ~/.gnome2/temp. 

2) Would be neat to have a button; though it is not tough to make a shortcut or simply go through the script menus. 

3) Seems like it might be useful to have a single script, which checks to see if filelist is there or not and does the appropriate action. 

So, something like (pardon my bash): 

```


#!/bin/sh

if [-f ~/.gnome2/temp/filelist] 

then

for i in [cat /var/run/copyscript/filelist];
do
  cp $i $variable for current directory;
done
rm /var/run/copyscript/filelist

else

#no idea if you need to preprocess the file list ...
echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > /var/run/copyscript/filelist 


```

I will have to do some experimenting I see. And learn a bit more bash...

Thanks for your help; I should be set.

---

