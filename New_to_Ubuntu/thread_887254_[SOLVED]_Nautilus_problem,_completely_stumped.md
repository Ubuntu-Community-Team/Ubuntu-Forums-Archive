---
title: "[SOLVED] Nautilus problem, completely stumped"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by 3gotist on 2008-08-11
I cannot open the contents of my file system using Nautilus.

I tried running it from a terminal, just to see if I could learn anything relevant via error messages. This is what I get back:

```
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:7667): CRITICAL **: nautilus_directory_file_monitor_add: assertion `NAUTILUS_IS_DIRECTORY (directory)' failed

(nautilus:7667): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:7667): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:7667): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:7667): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (nautilus:7667): CRITICAL **: nautilus_directory_get_uri: assertion `NAUTILUS_IS_DIRECTORY (directory)' failed
Segmentation fault

```

It occurred to me then that perhaps I could run it as root from the terminal. Turns out, yes I can. Why can I use my file manager as root but not any other way? Help.

---

### Post by tinker312 on 2008-08-12
Usually if you can access a file, application, or anything else on your system with root but not with a user it means your user account doesn't have the correct permissions.  Now that said, getting the correct permissions can be a pain, especially if your new.  

To look at the permissions of nautilus first open up your terminal and issue: 

sudo -s
cd /usr/bin
ls -l nautilus 

Now the fun part . . . you'll see 3 groups of 3 letters and these three letters are values. The three values total a number and that number signifies the permission of that group.  The first group of numbers represent the owner of the file or application, the second group represent the group, the third group represents others.  

Remember I said the three values of each group total a number?  Well lets go over that. 
There are 4 numbers that stand represent your systems permissions.  4 = read permissions 2 = write permissions 1 = execute permissions 0 = no permissions.  

Lets say that you want to give the group, the owners, and others complete access to nautilus.  The command to use is chmod . . . but what is the number to use?  If we want read, write and execute permissions we need to use a 4 + 2 + 1  . . . so the command would be 

chmod 777 nautilus 

Once you learn how the permission numbers work they are easy.  If you become a sys admin then you can give crazy, custom permission on any file/app/group without using some java based permission calculator. It's critically important when tons of users accessing a server with different levels of access rights. 

You still may need to change the owner of nautilus.  The command would be: 

chown yourusername:yourgroup nautilus 

Most of this is taken from *The Complete Idiot's Guide to Linux* I picked it up at the library the other day. It's a ridiculously dumb title . . . but useful information for beginners. 

Good luck and I hope this helps a little in clearing up your question. 
Tinker

---

### Post by Thingymebob on 2008-08-12
nautilus should be owned by root and in group root with permisions 755 (rwxr-xr-x)

---

### Post by 3gotist on 2008-08-12
Would a permissions issue really cause those error messages? I followed your suggestions, problem still persists.

Also, this is a completely fresh install of 8.04.1. The install CD I used passed the md5 checksum, and the verification tool said everything was fine. I can't figure out why a totally critical component of a desktop environment wouldn't work right out of the box. Very weird.

---

### Post by Thingymebob on 2008-08-12
I seem to remember a similar bug being reported back in 2006 i think it was something to do with mime types.
try ```
nautilus -c
``` to run some self tests on nautilus and post the output
then try ```
nautilus /
``` to see if nautilus will open in a different location (there may be something in the folder screwing it)

---

### Post by ramnarayan on 2008-08-12
> **3gotist said:**
> 
Also, this is a completely fresh install of 8.04.1. The install CD I used passed the md5 checksum, and the verification tool said everything was fine. I can't figure out why a totally critical component of a desktop environment wouldn't work right out of the box. Very weird.

Not a direct solution but install konqueror so that your work does not stop,

Then check to see if nautilus has any updates - if so update it and then check if its back to normal.

By default nautilus should be enabled for the primary user.

ram

---

### Post by 3gotist on 2008-08-12
> **Thingymebob said:**
> I seem to remember a similar bug being reported back in 2006 i think it was something to do with mime types.
try ```
nautilus -c
``` to run some self tests on nautilus and post the output

Okie doke, here's that
```
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container

```
> then try ```
nautilus /
``` to see if nautilus will open in a different location (there may be something in the folder screwing it)

Still doesn't work. :(

```

seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:7020): CRITICAL **: nautilus_directory_file_monitor_add: assertion `NAUTILUS_IS_DIRECTORY (directory)' failed

(nautilus:7020): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:7020): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:7020): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:7020): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (nautilus:7020): CRITICAL **: nautilus_directory_get_uri: assertion `NAUTILUS_IS_DIRECTORY (directory)' failed
Segmentation fault

```

Konqueror it is, until I can figure out what the heck is going on. I was using xubuntu for a little while, but I decided to switch cuz there are certain things about it I didn't like. Maybe I ought to go back. Hah.

Edit: So I created another user on the machine, and I can definitely use nautilus as desired with the new account without changing any permissions or anything like that. I am totally lost, here.

---

### Post by 3gotist on 2008-08-12
I figured out a workaround. I dumped everything from my /home directory into a temporary folder on the same partition, and reinstalled using a different username in the installer than my previous one. Everything works fine, now.

Thanks for your help.

---

### Post by dwatling on 2010-02-23
I've been having this same issue for awhile and just fixed it. It turns out, for me at least, in my ~/.gnome2 folder there is a nautilus-scripts directory. Mine was a symlink for a directory that did not exist (/usr/share/nautilus-scripts). Once I created that folder nautilus started working.

Hope my solution works for someone else!

-Dan

---

### Post by jcDelta on 2011-05-16
> **dwatling said:**
> I've been having this same issue for awhile and just fixed it. It turns out, for me at least, in my ~/.gnome2 folder there is a nautilus-scripts directory. Mine was a symlink for a directory that did not exist (/usr/share/nautilus-scripts). Once I created that folder nautilus started working.

Hope my solution works for someone else!

-Dan

I had exactly this problem under 11.04 as I was reorganizing some things.  Took a little be to trace down the problem, but with your post I solved it in seconds.  Thanks!

The critical log line turned out to be in my .xsession-errors:

** (nautilus:17226): CRITICAL **: nautilus_directory_file_monitor_add: assertion `NAUTILUS_IS_DIRECTORY (directory)' failed

---

### Post by sharat87 on 2011-12-04
> **dwatling said:**
> I've been having this same issue for awhile and just fixed it. It turns out, for me at least, in my ~/.gnome2 folder there is a nautilus-scripts directory. Mine was a symlink for a directory that did not exist (/usr/share/nautilus-scripts). Once I created that folder nautilus started working.

Hope my solution works for someone else!

-Dan

Awesome! That's just what was going wrong. I was reorganising stuff and forgot about this symlink :)

I wish nautilus be a bit more tolerable.

Thank you so much Dan.

---

