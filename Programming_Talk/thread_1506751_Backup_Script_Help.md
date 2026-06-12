---
title: "Backup Script Help"
date: 2010-06-10
forum: Programming Talk
---

### Post by ikeurb on 2010-06-10
Okay, needless to say I don't have much experience with Linux or shell scripting. 

For practice, I am writing a script that will prompt the user for a path to backup from then a path to backup to. Sounds easy enough, but I'd like to do some error checking and prevention too.

This first think I do is ask the user for folder to backup.

echo "Welcome $USER!, what would you like to backup? "
read BACK_UP_FROM

then I ask the user for the destination to backup to.

echo "Welcome $USER!, what is the destination path to backup to?"
read BACK_UP_FROM

I then check to see if the destination directory exists, if not I create it.

Next I create the filename...
FILENAME=backup-$CURRENT_TIME.tar

and start the backup process.
tar cf $BACK_UP_TO$FILENAME $BACK_UP_FROM

My questions are:
1.) How do I validate that source path to backup is valid or not?
2.) How can append the filename with a suffix if the backup file already exists. i.e. If backup-20100610 already exists, how can I append the filename to backup2-20100610?
3.) I also would like to avoid backing up the /. hidden files and folders. Advice?


Thanks for helping me learn the ways of shell scripting.

---

### Post by geirha on 2010-06-10
First off, don't use all uppercase vars, you risk overwriting special shell variables or environment variables. Secondly, I strongly recommend you read [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide), and [http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ) will likely answer many questions/problems you encounter.

For your specific questions, assuming you are writing a bash script;
1)
```
if [[ -e $back_up_from ]]; then echo "$backup_up_from exists"; fi
```
Use -d instead of -e if you want to check for an existing directory. «help test» in a bash shell will give you a complete list.

2)
You already have a date in the filename. If you intend to do full backups more than once a day, just add hour and minute to it.

3)
You don't want to backup settings? Anyway «man tar», GNU tar which ships with Ubuntu has alot of options, including options to exclude dirs that match a certain pattern.

---

### Post by ikeurb on 2010-06-11
Thanks for the quick reply. This should get me going in the right direction. Thanks for the tips about all caps variables. Very good point. With C++ programming I'm used to the standard of naming constants using all caps. I'll have to remember not to do that with shell scripts.


Thanks again!

---

