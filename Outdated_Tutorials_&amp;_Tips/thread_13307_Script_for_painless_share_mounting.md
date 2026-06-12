---
title: "Script for painless share mounting"
date: 2005-01-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Arktis on 2005-01-30
I wrote a very simple shell script that will mount a list of shares, unmount them, or show the mounted list depending on what option you chose when it prompts you.  It's very quick and easy, just use m for mount, u for unmount, l for list, and q for quit when prompted.  Say for instance you have a laptop and you need to access shares both at home and at work.  Put them all into this script (the ones from home AND work) and run it when you need to get to them.  Of course, it will fail to load your home shares when you are work and vice-versa, but it will still try to load everything it can so that's okay, you still get easy access to your home shares at home and your work shares at work.

Just throw it into a blank text file, do your editing (it's commented to show you where and how to edit), save it as 'shares' (no extension) then drop it into /usr/bin/ and type 'sudo shares' (putting it in /usr/bin basicly lets you run it like a command) when you want to mount or unmount your network shares easily all at once.  !!Make sure the permissions are set to allow you to read and execute.  Just right click the file and go to the permissions tab.

Comments and suggestions are welcome.  I know it's very basic (it's my first) but it gets the job done.

```
#!/bin/sh
#
# You should turn of text wrapping when editing this.
# This is a very simple network share mounting script
# to make life easier for laptop users.
# Do whatever you want with it.
# arcticflare@arcticmail.com for comments

echo -n 'Options are [M]ount / [U]nmount / [L]ist / [Q]uit : ' 
read Menu
if [ " $Menu" = " m" -o " $Menu" = " M" ]
then
# Edit/add lines below for the stuff you want mounted.
# You can put as many lines as you like here and the
# script will attempt to mount them all.
# Example : mount -t smbfs -o username=Administrator,password=123456 //bob_guy/docs /mnt/docs
# (That mounts the network share 'docs' from the computer
# named 'bob_guy' to the docs folder in the /mnt directory
# using the 'bob_guy' computer's admin account to
# authenticate.)
 mount -t smbfs -o username=yourname,password=yourpass //netname/sharename /path/to/mount/directory
 mount -t smbfs -o username=yourname,password=yourpass //netname/sharename /path/to/mount/directory
 mount -t smbfs -o username=yourname,password=yourpass //netname/sharename /path/to/mount/directory
 mount -t smbfs -o username=yourname,password=yourpass //netname/sharename /path/to/mount/directory
 echo 'Done.'
 shares
else
 if [ " $Menu" = " u" -o " $Menu" = " U" ]
 then
# Here you want to put the location of the directories
# being mounted to so they can all be unmounted with 'u'.
# Example : umount /mnt/docs (unmounts the share from the first example)
  umount /path/to/mount/directory
  umount /path/to/mount/directory
  umount /path/to/mount/directory
  umount /path/to/mount/directory
  echo 'Done.'
  shares
 else
  if [ " $Menu" = " q" -o " $Menu" = " Q" ]
  then
   echo 'Goodbye.'
  else
   if [ " $Menu" = " l" -o " $Menu" = " L" ]
   then
    mount
    shares
   else 
    echo 'Let us try again, shall we?'
    shares
   fi
  fi
 fi
fi
```

It should be noted that you need to create folders for your shares to be mounted to by running the command 'sudo mkdir /path/to/mount' directoy, where the path contains the location and name of where you want the network share to be mounted.

---

### Post by angrylittleman on 2005-01-30
[QUOTE=Arktis]I wrote a very simple shell script that will mount a list of shares, unmount them, or show the mounted list depending on what option you chose when it prompts you.  It's very quick and easy, just use m for mount, u for unmount, l for list, and q for quit when prompted.  Say for instance you have a laptop and you need to access shares both at home and at work.  Put them all into this script (the ones from home AND work) and run it when you need to get to them.  Of course, it will fail to load your home shares when you are work and vice-versa, but it will still try to load everything it can so that's okay, you still get easy access to your home shares at home and your work shares at work.

Just throw it into a blank text file, do your editing (it's commented to show you where and how to edit), save it as 'shares' (no extension) then drop it into /usr/bin/ and type 'sudo shares' (putting it in /usr/bin basicly lets you run it like a command) when you want to mount or unmount your network shares easily all at once.  !!Make sure the permissions are set to allow you to read and execute.  Just right click the file and go to the permissions tab.

Comments and suggestions are welcome.  I know it's very basic (it's my first) but it gets the job done.

```
#!/bin/sh
#
# You should turn of text wrapping when editing this.
# This is a very simple network share mounting script
# to make life easier for laptop users.
# Do whatever you want with it.
# arcticflare@arcticmail.com for comments

echo -n 'Options are [M]ount / [U]nmount / [L]ist / [Q]uit : ' 
read Menu
if [ " $Menu" = " m" -o " $Menu" = " M" ]
then
# Edit/add lines below for the stuff you want mounted.
# You can put as many lines as you like here and the
# script will attempt to mount them all.
# Example : mount -t smbfs -o username=Administrator,password=123456 //bob_guy/docs /mnt/docs
# (That mounts the network share 'docs' from the computer
# named 'bob_guy' to the docs folder in the /mnt directory
# using the 'bob_guy' computer's admin account to
# authenticate.)
 mount -t smbfs -o username=yourname,password=yourpass //netname/sharename /path/to/mount/directory
 mount -t smbfs -o username=yourname,password=yourpass //netname/sharename /path/to/mount/directory
 mount -t smbfs -o username=yourname,password=yourpass //netname/sharename /path/to/mount/directory
 mount -t smbfs -o username=yourname,password=yourpass //netname/sharename /path/to/mount/directory
 echo 'Done.'
 shares
else
 if [ " $Menu" = " u" -o " $Menu" = " U" ]
 then
# Here you want to put the location of the directories
# being mounted to so they can all be unmounted with 'u'.
# Example : umount /mnt/docs (unmounts the share from the first example)
  umount /path/to/mount/directory
  umount /path/to/mount/directory
  umount /path/to/mount/directory
  umount /path/to/mount/directory
  echo 'Done.'
  shares
 else
  if [ " $Menu" = " q" -o " $Menu" = " Q" ]
  then
   echo 'Goodbye.'
  else
   if [ " $Menu" = " l" -o " $Menu" = " L" ]
   then
    mount
    shares
   else 
    echo 'Let us try again, shall we?'
    shares
   fi
  fi
 fi
fi
```

It should be noted that you need to create folders for your shares to be mounted to by running the command 'sudo mkdir /path/to/mount' directoy, where the path contains the location and name of where you want the network share to be mounted.[/QUOTE]
 This looks great, I cannot wait to give it a try!!!

---

### Post by genjix on 2005-06-27
I do think you should distinguish between upper and lower case for the options though (like most of the GNU tools and posix standard).

cya and keep it up!

---

