---
title: "Perl and a Recursive Chown"
date: 2005-08-11
forum: Programming Talk
---

### Post by jimjawn on 2005-08-11
I've been looking around all over the place for an easy fix to this, but I'm stuck.  

I need to write a perl script to recursively chown a directory.  Here's my script:

```
#!/usr/bin/perl

open(PASSWD, "best");

while(<PASSWD>)
{
    ($uname, $passwd, $uid, $gid, $realname, $home, $shell)=
        split(/:/);

    # Change the permissions on the home directory
    print "chowning $uid on $home...\n";
    chown ($uname,$gid,$home");

    # Change the permissions on the mailbox
    print "chowning $uid on mailbox...\n";
    chown ($uname, 12, "/var/spool/mail/$uname")
}

close PASSWD;
```

Now my question is how can I execute the first chown function recursively?  I've also tried exec('/bin/chown -R $uid:$gid $home') but I can't seem to get it to work.  Not sure where else to post this and I have an idea that this is a pretty simple fix.  Hoping some perl nut can throw a fool a bone.

Thanks,

Jimjawn

---

### Post by jimjawn on 2005-08-12
Alright, well I figured out how to fix it.  

This is sort of a special case and I should have elaborated a little bit more.  I'm running winbind on my box and use it to authenticate against an Active Directory backend.  For some reason, my winbind_idmap.tdb file (the file that maps the local users with the active directory users) was corrupted and I had to rebuild it.  When I rebuilt the idmap file, the user id numbers and the permissions in the home directory didn't match up properly.  That's what this script is.  Once you pull a getent passwd > best and pull out the users  you don't want, you can run the script below and it will recursively return the permissions on your users home directories to match the winbind_idmap database.

This is kind of a special case, but if you know a little bit about programming you can figure it out...

```
#!/usr/bin/perl

# Open the file "best"
open(PASSWD, "best");

# Until the PASSWD file is at its end...
while(<PASSWD>)
{
    # Open up the password file and split it, with each
    # column in it getting assigned a value
    ($uname, $passwd, $uid, $gid, $realname, $home, $shell)=
        split(/:/);

        # Change our home directory
        chown ($uname,$gid,$home);

        # Not Really Sure..
        @ARGV = $home;

        # Use the find library
        use File::Find;

        # Execute this subroutine which correctly chowns the right file..
        find sub {      chown ($uid, $gid, $File::Find::name);
                        print $File::Find::name, -d && '/', "\n" }, @ARGV;

}
close PASSWD;

```

---

### Post by LordHunter317 on 2005-08-12
Why aren't you using find on the command line and chown -R?  

Here's a quicky that ought to work:```
#!/bin/sh

OLDIFS="$IFS"
IFS=:
cat best | while read uname passwd uid gid gecos homedir shellnam ; do
    chown -R "$uname:$gid" "$homedir"
done
IFS="$OLDIFS"
```

---

