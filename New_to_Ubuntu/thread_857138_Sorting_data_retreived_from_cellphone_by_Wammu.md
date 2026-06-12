---
title: "Sorting data retreived from cellphone by Wammu"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by jbb on 2008-07-12
How do I sort the contact data retrieved from my Nokia cellphone when using Wammu to retrieve the contact data?
I can retrieve my contacts list but would like to be abe to sort it into alphabetic order so as as to easily delete duplicate data and or compact multiple entries same name into one entry.
Can any body offer any help?

Thanks
John,
:confused:

---

### Post by boblemur on 2008-07-12
hey how is your output formated?

because if it is just a list of text... you can go into terminal

program_that_gives_contacts | sort

will show you a list of them sorted...

and you can use uniq to remove duplicates...

or uniq -d to display any that have duplicates

---

### Post by jbb on 2008-07-13
Hi there  data is saved by Wammu as name.backup
I can't see option to change/select other file format
can only open file in Wammu     tried your suggestion but get

john@johns-laptop:~$ /desktop/contacts.backup | sort
bash: /desktop/contacts.backup: No such file or directory
john@johns-laptop:~$ /john/contacts.backup | sort
bash: /john/contacts.backup: No such file or directory
john@johns-laptop:~$ home/john/contacts.backup | sort
bash: home/john/contacts.backup: No such file or directory
john@johns-laptop:~$ ls -l /home/john
total 332
-rw-r--r-- 1 john john 81644 2008-06-24 19:13 CELL CALENDAR.backup
-rw-r--r-- 1 john john 71432 2008-06-24 19:12 CELL CONTACTS.backup
-rw-r--r-- 1 john john 52508 2008-07-11 19:40 contacts.backup
drwxr-xr-x 2 john john  4096 2008-07-13 08:18 Desktop
drwxr-xr-x 2 john john  4096 2008-07-12 18:29 Documents
-rw-r--r-- 1 john john 33549 2008-06-27 21:49 messages.smsbackup
drwxr-xr-x 2 john john  4096 2008-06-08 00:04 Music
drwxr-xr-x 2 john john  4096 2008-07-08 20:01 Pictures
drwxr-xr-x 2 john john  4096 2008-06-08 00:04 Public
drwxr-xr-x 2 john john  4096 2008-06-08 00:04 Templates
-rw-r--r-- 1 john john 51634 2008-06-27 21:44 Work Contacts.backup
john@johns-laptop:~$ cd /home
john@johns-laptop:/home$ /john/contacts.backup | sort
bash: /john/contacts.backup: No such file or directory
john@johns-laptop:/home$ 


:confused:,   very:confused:

Please advise

---

