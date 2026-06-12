---
title: "Shell scripts.. password question.."
date: 2007-08-27
forum: Programming Talk
---

### Post by Kedaeus_Sendre on 2007-08-27
I'm writing a shell script to mount my secondary and tertiary hard drives at my whim without having to type out all the required commands.

I'm having trouble getting around the password issue. 
How can I embed  the users password into the script without prompting for it?
The only user interaction I want is actually executing the script. 

My wife refuses to touch the terminal so.. I have to give her an easy way to access her work without leaving the files
openly access-able for a 4 year old to alter or delete.

Thanks, 
-Ked

---

### Post by aysiu on 2007-08-27
Edit the /etc/sudoers file with the command ```
sudo visudo
``` Add this line to the end of the file: ```
ked ALL=NOPASSWD: /usr/bin/mount
``` I'm actually not sure if it's /usr/bin/mount or /usr/sbin/mount. You can try both, see which one works.

---

### Post by po0f on 2007-08-27
Kedaeus_Sendre,

You could also add the "users" option to the partition's entry in fstab:

```

# if the partition was present at installation (add the bold part):
UUID=<crap> /mount/point <fs_type> defaults**,users** 0 2

# if not, just create an entry for it:
## if you want to use the partition's UUID, use `blkid /dev/blah` to find it
## you can also just use the actual device
/dev/<blar> /mount/point <fs_type> defaults,users 0 2
```

mount's "users" option allows all users to mount/umount a partition, regardless of who had previously mounted/umounted it.

Let me ask this: are you writing a script solely for the purpose of mounting some partitions, or are you writing a script that uses the partitions for a little while then umounts them?  If it's the former, just create fstab entries for the relevant partitions and they should be mounted at boot for you.

And if you have any more questions, just ask away.  :)


aysiu,

To find the full path to an executable:

```
$ which <command>
```

Just for future reference.  ;)

---

