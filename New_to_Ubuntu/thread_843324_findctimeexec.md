---
title: "find/ctime/exec"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by bakechad on 2008-06-28
I am trying to use the following script to regularly clean up some files.  I have been using this type of script for years on a SUSE box at work.  I cannot get it to work at all on Xubuntu:confused:, I have tried several variations.  Here is the original and one of the variations, including errors.  

Any help would be greatly appreciated!

> #last edited 6/16/2008
#
#clean out 848 files older than 10 days and cue files
cd $HOME/POD/wbez/848 ; find ./ -name '*.mp3' -ctime +10 -exec rm {} \;
cd $HOME/POD/wbez/848 ; find ./ -name '*.cue' -exec rm {} \;


chad@vectra:~/scripts$ ./do_clean_stale~
find: missing argument to `-exec'
find: missing argument to `-exec'
chad@vectra:~/scripts$ 

 
2nd attempt based on info on Internet (added -f and quotes around the {})



#last edited 6/16/2008
#
#clean out 848 files older than 10 days and cue files
cd $HOME/POD/wbez/848 ; find ./ -name '*.mp3' -ctime +10 -exec rm -f '{}' \;
cd $HOME/POD/wbez/848 ; find ./ -name '*.cue' -exec rm -f '{}' \;


chad@vectra:~/scripts$ ./do_clean_stale
find: missing argument to `-exec'
find: missing argument to `-exec'
chad@vectra:~/scripts$ 



I tried several other variations and got the same errors


Thanks

Chad

---

### Post by mcduck on 2008-06-28
This is just and idea, but if the script worked on other distribution it could be related to Ubuntu using Dash as the default shell (instead of Bash).. Have you tested if those commands work correctly when run outside of the script?

In that case it would probably help to add the bash shebang to the first line of the script (#!/bin/bash).

---

### Post by bakechad on 2008-06-28
> **mcduck said:**
> This is just and idea, but if the script worked on other distribution it could be related to Ubuntu using Dash as the default shell (instead of Bash).. Have you tested if those commands work correctly when run outside of the script?

In that case it would probably help to add the bash shebang to the first line of the script (#!/bin/bash).


Thanks for the reply!

I added it:

> #!/bin/bash
#
# do_CleanStale - remove old files from data areas
#
#actual script
#
#last edited 6/16/2008
#
#clean out 848 files older than 10 days and cue files
cd $HOME/POD/wbez/848 ; find ./ -name '*.mp3' -ctime +10 -exec rm -f '{}' \;
cd $HOME/POD/wbez/848 ; find ./ -name '*.cue' -exec rm -f '{}' \;



and got this error:

> bash: ./do_clean_stale_test: /bin/bash^M: bad interpreter: No such file or directory
chad@vectra:~/scripts$ 


Permissions look good and I was able to execute it:

> chad@vectra:/bin$ ls -l bash
-rwxr-xr-x 1 root root 701680 2007-10-05 09:37 bash
chad@vectra:/bin$ 


---

### Post by unutbu on 2008-06-28
> 
bash: ./do_clean_stale_test: /bin/bash**^M**: bad interpreter: No such file or directory
Check to see if there is a ^M in your script. They show up in emacs.

I tested your script. It works fine for me.

You could also change bash to sh. That also works for me.

---

### Post by mcduck on 2008-06-28
Now that's strange.. The shebang definitely should work, at least it shouldn't result in any errors..

Anyway, did you try the commands alone (outside the script)? That would at least tell us if the problems is with the shell or not..

edit: oh, now I noticed the "^m" in the error message.. That comes from the diffent way Windows/Unix/OSX handle line changing in text documents (Carriage return and Line feed, or just one of them).. If you are writing that script on the Linux machine and you copypasted that line remove it and type it again by hand.. That should solve the problem.

If you are writing the script on some other OS make sure you set the text editor to save the file in Unix format.

---

### Post by bakechad on 2008-06-28
All fixed!:)

I pulled the script up in VI and had ^M at the end of each line.  I was using JEDIT to edit the file and it defaulted to DOS line feed/carriage returns.

Removed all the ^M and it works like a champ.

Thanks for everyone's help.  I love this forum!

---

