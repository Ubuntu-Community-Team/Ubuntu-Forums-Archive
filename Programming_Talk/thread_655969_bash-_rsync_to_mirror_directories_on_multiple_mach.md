---
title: "bash- rsync to mirror directories on multiple machines"
date: 2008-01-02
forum: Programming Talk
---

### Post by a_posse_ad_esse on 2008-01-02
Hello, all.  This is my first script in a _very_ long time, but I think that it has some real-world applicability.  Basically, the script attempts to mount directories via sshfs (locally first, then remotely) pulls the appropriate data from the directory using rsync to the server, and the server machine then disperses the sum of the changes back to the clients.  

At the moment, I am simply working out bugs.  Any help or suggestions would be very much appreciated.  Thanks

Here is what I have so far...

```

#!/bin/bash
unmnt="fusermount -u"
mirror="rsync -uv --super --progress --delete --include=*/.kde --include=*/.mozilla --exclude=*/.*"
nomnt="is not mounted on"
mnt="is mounted on"
opts="-o nonempty -o workaround=rename -o allow_other -o BatchMode yes"
m1="machine1"
m2="machine2"
m3="machine3"
user1="tim"
user2="kristen"
dir1="home"
m1loc="192.168.2.4:"
m2loc="192.168.2.3:"
m3loc="192.168.2.5:"
m2rem="remote.bla.com:"
m3rem="remote2.bla.com:"

#check for mount
chk_mnt_m1dir1user1 () {
chk_m1dir1user1=$(mount | awk -v mnt=/sync/$m1/$dir1/$user1 '{ if ($3 == mnt) print $0 }')

if [ "$chk_m1dir1user1" == "" ]; 
then
	echo "$dir1 $user1 $nomnt $m1"
	m1dir1user1="false"
else
	echo "$dir1 $user1 $mnt $m1"
	m1dir1user1="true"
fi
}

chk_mnt_m1dir1user2 () {
chk_m1dir1user2=$(mount | awk -v mnt=/sync/$m1/$user2/$dir1 '{ if ($3 == mnt) print $0 }')

if [ "$chk_m1dir1user2" == "" ]; 
then
	echo "$dir1 $user2 $nomnt $m1"
	m1dir1user2="false"
else
	echo "$dir1 $user2 $mnt $m1"
	m1dir1user2="true"
fi
}

chk_mnt_m2dir1user1 () {
chk_m2dir1user1=$(mount | awk -v mnt=/sync/$m2/$user1/$dir1 '{ if ($3 == mnt) print $0 }')

if [ "$chk_m2dir1user1" == "" ]; 
then
	echo "$dir1 $user1 $nomnt $m2"
	m2dir1user1="false"
else
	echo "$dir1 $user1 $mnt $m2"
	m2dir1user1="true"
fi
}

chk_mnt_m3dir1user2 () {
chk_m1dir1user2=$(mount | awk -v mnt=/sync/$m3/$user2/$dir1 '{ if ($3 == mnt) print $0 }')

if [ "$chk_m3dir1user2" == "" ]; 
then
	echo "$dir1 $user2 $nomnt $m3"
	m3dir1user2="false"
else
	echo "$dir1 $user2 $mnt $m3"
	m3dir1user2="true"
fi
}

#check for mount, and, if mounted, unmount
unmnt_m1dir1user1 () {
if [ $m1dir1user1="true" ]; 
then 
	echo "$dir1 $user1 $mnt $m1"
	echo "Attempting to unmount $dir1 $user1 on $m1..."
	$unmnt /sync/$m1/$dir1/$user1
#check to see if successful
	echo "Checking unmount of $dir1 $user1 on $m1..."
	chk_mnt_m1dir1user1
if [ $m1dir1user1="false" ]; 
then 
	echo "Unmount of $dir1 $user1 on $m1 was successful.  Continuing..."
else 
	echo "Unmount of $dir1 $user1 on $m1 was unsuccessful.  Exiting..."
	exit
fi
fi
}

unmnt_m1dir1user2 () {
if [ $m1dir1user2="true" ]; 
then 
	echo "$dir1 $user2 $mnt $m1"
	echo "Attempting to unmount $dir1 $user2 on $m1..."
	$unmnt /sync/$m1/$dir1/$user2
#check to see if successful
	echo "Checking unmount of $dir1 $user2 on $m1..."
	chk_mnt_m1dir1user2
if [ $m1dir1user2="false" ]; 
then 
	echo "Unmount of $dir1 $user2 on $m1 was successful.  Continuing..."
else 
	echo "Unmount of $dir1 $user1 on $m1 was unsuccessful.  Exiting..."
	exit
fi
fi
}

unmnt_m2dir1user1 () {
if [ $m2dir1user1="true" ]; 
then 
	echo "$dir1 $user1 $mnt $m2"
	echo "Attempting to unmount $dir1 $user1 on $m2..."
	$unmnt /sync/$m2/$dir1/$user1
#check to see if successful
	echo "Checking unmount of $dir1 $user1 on $m1..."
	chk_mnt_m2dir1user1
if [ $m2dir1user1="false" ]; 
then 
	echo "Unmount of $dir1 $user2 on $m2 was successful.  Continuing..."
else 
	echo "Unmount of $dir1 $user1 on $m2 was unsuccessful.  Exiting..."
	exit
fi
fi
}

unmnt_m3dir1user2 () {
if [ $m3dir1user2="true" ]; 
then 
	echo "$dir1 $user2 $mnt $m3"
	echo "Attempting to unmount $dir1 $user2 on $m3..."
	$unmnt /sync/$m3/$dir1/$user2
#check to see if successful
	echo "Checking unmount of $dir1 $user2 on $m3..."
	chk_mnt_m3dir1user2
if [ $m3dir1user2="false" ];
then 
	echo "Unmount of $dir1 $user2 on $m3 was successful.  Continuing..."
else 
	echo "Unmount of $dir1 $user2 on $m3 was unsuccessful.  Exiting..."
exit
fi
fi
}

#Start by checking for previous connections
echo "Checking for existing connections..."
chk_mnt_m1dir1user1
chk_mnt_m1dir1user2
chk_mnt_m2dir1user1
chk_mnt_m3dir1user2

if [ $m1dir1user1="true" ];
then unmnt_m1dir1user1
fi

if [ $m1dir1user2="true" ];
then unmnt_m1dir1user2
fi

if [ $m2dir1user1="true" ];
then unmnt_m2dir1user1
fi

if [ $m3dir1user2="true" ];
then unmnt_m3dir1user2
fi

echo "Attempting to mount devices locally..."
sshfs $user1@$m1loc/$dir1 /sync/$m1/$dir1 $opts
sshfs $user2@$m1loc/$dir1 /sync/$m1/$dir1 $opts
sshfs $user1@$m2loc/$dir1/$user1 /sync/$m2/$dir1/$user1 $opts
sshfs $user2@$m3loc/$dir1/$user2 /sync/$m3/$dir1/$user2 $opts

echo "Checking for local connections..."
chk_mnt_m1dir1user1
chk_mnt_m1dir1user2
chk_mnt_m2dir1user1
chk_mnt_m3dir1user2

if [ $m2dir1user1="false" ];
then echo "$dir1 $user1 on $m2 failed to mount locally.  Attempting remote connection..."
sshfs $user1@$m2rem/$dir1/$user1 /sync/$m2/$user1/$dir1 $opts -p 23
chk_mnt_m2dir1user1
fi

if [ $m3dir1user2="false" ];
then echo "$dir1 $user2 on $m3 failed to mount locally.  Attempting remote connection..."
sshfs $user2@$m3rem/$dir1/$user2 /sync/$m2/$user1/$dir1 $opts -p 25
chk_mnt_m2dir1user1
fi

#Determine which machines mirror to server
if [ $m1dir1user1="true" ];
then $mirror /sync/$m1/$dir1/$user1 /$dir1
else echo "$dir1 $user1 $nomnt $m1.  Continuing..."
if [ $m1dir1user2="true" ];
then $mirror /sync/$m1/$dir1/$user2 /$dir1
else echo "$dir1 $user2 $nomnt $m1.  Continuing..."
if [ $m2dir1user1="true" ];
then $mirror /sync/$m2/$dir1/$user1 /$dir1
else echo "$dir1 $user1 $nomnt $m2.  Continuing..."
if [ $m3dir1user2="true" ];
then $mirror /sync/$m3/$dir1/$user2 /$dir1
else echo "$dir1 $user2 $nomnt $m3.  Continuing..."
fi
fi
fi
fi

#Determine which machines the server will mirror to
#Don't need 'opts' here... the appropriate files will already be on the server
if [ $m1dir1user1="true" ];
then $mirror /$dir1/$user1 /sync/$m1/$dir1
else echo "$dir1 $user1 $nomnt $m1.  Continuing..."
if [ $m1dir1user2="true" ];
then $mirror /$dir1/$user2 /sync/$m1/$dir1
else echo "$dir1 $user2 $nomnt $m1.  Continuing..."
if [ $m2dir1user1="true" ];
then $mirror /$dir1/$user1 /sync/$m2/$dir1
else echo "$dir1 $user1 $nomnt $m2.  Continuing..."
if [ $m3dir1user2="true" ];
then $mirror /$dir1/$user2 /sync/$m3/$dir1
else echo "$dir1 $user2 $nomnt $m3.  Continuing..."
fi
fi
fi
fi

echo "Mirroring completed.  Unmounting folders."
unmnt_m1dir1user1
unmnt_m1dir1user2
unmnt_m2dir1user1
unmnt_m3dir1user2

exit

```

Edit- added "-o Batchmode yes" to prevent password prompt.

---

### Post by a_posse_ad_esse on 2008-01-11
Thoughts?  Questions?  Comments?

Also, I forgot to give credit for the mount test.  I found it [here]("http://www.bioinspired.com/users/ajg112/software/bashTips.shtml").

---

