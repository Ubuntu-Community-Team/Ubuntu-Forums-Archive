---
title: "BASH script to remove home dirs"
date: 2008-04-08
forum: Programming Talk
---

### Post by Greslore on 2008-04-08
Ok.  I have been working on writing a script to remove users home directories.  This is proving much more challenging than I originally thought it would be.  Basically, I have a machine with LDAP users logging in.  Machine creates a local home dir every time a new users logs in.

I need to delete these home dirs after their session ends.  I am thinking of just doing this every 24 hours via a script using cron.

So I using the "users" linux command to build an array with current logged in users.  Because I cannot remove users home dirs that are currently logged in.

Here is the script so far:
> #!/bin/bash
ALLUSERS=($(users))
i=0
while (($i < ${#ALLUSERS[@]} ))
do
        echo "user id $i is ${ALLUSERS[i++]}"
done



This builds an array with all current logged in users.  The next step is to delete all directories that do not contain any element in this array.  This is where I am a bit stuck at the moment..... any ideas?

---

### Post by ghostdog74 on 2008-04-08
```

#!/bin/bash
awk 'BEGIN{
    FS=":"
    cmd="users"
    cmd|getline u 
    close(cmd)
    n=split(u,usr," ")  
    #store in array users
    for ( i=1;i<=n;i++) { users[usr[i]]}
}
{
    if ( $1 in users ) {
        next
    }else {
        cmd = "rm -rf "$6
        print cmd
        #system(cmd) #uncomment to use
    }
}' /etc/passwd

```

---

