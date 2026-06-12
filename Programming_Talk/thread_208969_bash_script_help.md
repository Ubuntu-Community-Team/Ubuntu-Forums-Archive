---
title: "bash script help"
date: 2006-07-04
forum: Programming Talk
---

### Post by cjssmo on 2006-07-04
I recently migrated from windows to a completly linux lan, and while switching over I ended up with a lot of files that had spaces in them, so I searched the forums and found this script


for i in `find . | tr "[:blank:]" "+" | grep "+"`; do echo "Changing Directory: " `echo $i | sed -r 's/\+/\\ /g'` " to " `echo $i | tr "+" "_"`;  mv "`echo $i | sed -r 's/\+/\\ /g'`" `echo $i | tr "+" "_"`; done

it works great.  Renamed all my mp3 and movie files in minutes.  My question is can this script be modified to take the () out of a file name: for example I now have alot of files that look like this 

granny/grannypics_(38).jpg

and would like for them to look like this

granny/grannypics_38.jpg

I'm sure this can be done I am just not sure what to change.

Thank you for your assistance

---

### Post by tseliot on 2006-07-04
Moved to a more appropriate section

---

### Post by IYY on 2006-07-04
for i in `find . | tr "[:blank:]" "+" | grep "+"`; do echo "Changing Directory: " `echo $i | sed -r 's/\+/\\ /g'` " to " `echo $i | tr "+" "_"`; mv "`echo $i | sed -r 's/\+/\\ /g'`" `echo $i | tr "+" "_"` **| tr -d "()"**; done

---

### Post by cjssmo on 2006-07-07
Thanks for the help but it didn't work.  Going to look at all the howto's out there and maybe make some since of this thing, not a newbie but not a pro either. All I want to do is rename some files, in mass.  This is what they look like

/granny/grannypic_(1001).jpg

and this is what I want them to look like

/granny/grannypic.1001.jpg

use to use Winblows (thats where all the () came from) and switched over to ubuntu which by the way I think is a great OS.  

Let me thank you for any help in advance

---

### Post by yaaarrrgg on 2006-07-09
there's a command line tool called "rename" that lets you rename a batch of files.  not sure it is installed by default, might need to find in in the repository.  

then you'd do something like this (untested code)
```

rename 's/[()]//' *.jpg

```

uses perl regular expressions...

---

