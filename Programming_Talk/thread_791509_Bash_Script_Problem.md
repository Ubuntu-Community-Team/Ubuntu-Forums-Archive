---
title: "Bash Script Problem"
date: 2008-05-12
forum: Programming Talk
---

### Post by rj175 on 2008-05-12
I'm currently trying to write a bash script so compile a samba config file but ive hit a snag. This is the bit of code

```
case "$roamingprofile" in

y | Y)
                        echo "logon path = \\%L\profiles\%U" >> $save_path/smb.conf
                        echo logon drive = H: >> $save_path/smb.conf
                        echo "logon home = \\%L\%U\.9xprofiles" >> $save_path/smb.conf
                        echo    >> $save_path/smb.conf
                        echo [netlogon] >> $save_path/smb.conf
                        echo    comment = Network Logon Service >> $save_path/smb.conf
                        echo    "path = /var/lib/samba/netlogon" >> $save_path/smb.conf
                        echo    admin users = root >> $save_path/smb.conf
                        echo    guest ok = yes >> $save_path/smb.conf
                        echo    browseable = no  >> $save_path/smb.conf
                        echo    >> $save_path/smb.conf
                        echo [profiles] >> $save_path/smb.conf
                        echo    comment = Network Profiles Share >> $save_path/smb.conf
                        echo    path = /profiles >> $save_path/smb.conf
                        echo    read only = no >> $save_path/smb.conf
                        echo    store dos attributes = yes >> $save_path/smb.conf
                        echo    create mask = 0600 >> $save_path/smb.conf
                        echo    directory mask = 0700 >> $save_path/smb.conf
                        echo    browseable = no >> $save_path/smb.conf
                        echo    guest ok = no >> $save_path/smb.conf
                        echo    printable = no >> $save_path/smb.conf
                        echo    writeable = yes >> $save_path/smb.conf
                        echo >> $save_path/smb.conf
                        echo [homes] >> $save_path/smb.conf
                        echo    comment = Home Directories >> $save_path/smb.conf
                        echo    valid users = %S >> $save_path/smb.conf
                        echo    read only = no >> $save_path/smb.conf
                        echo    browseable = no >> $save_path/smb.conf
                        echo    writeable = yes >> $save_path/smb.conf
                        echo "Writing Complete! Files Stored At $save_path"
;;

n | N)
echo [homes] >> $save_path/smb.conf
echo    comment = Home Directories >> $save_path/smb.conf
echo    valid users = %S >> $save_path/smb.conf
echo    read only = no >> $save_path/smb.conf
echo    browseable = no >> $save_path/smb.conf
echo    writeable = yes >> $save_path/smb.conf
echo "Writing Complete! Files Stored At $save_path"
;;

*)
echo "This is not an option": $roamingprofile

esac

done
```

After asking the user if they want romaning profiles I want them only to be able to enter y or n nomatter what case. It works it recognises the y or n no matter what cause and also if the user enters something diffrent it just dosn't loop back if they enter something wrong.

Any ideas?

Thanks in advance

rich

---

### Post by dtmilano on 2008-05-12
It's no completely clear what you want, but I guess is something like this:
> 
#! /bin/bash

while :
do
	read -p "Enter option [y/n]: " -s -n 1 REPLY
	case "$REPLY" in
		y|Y)
			echo YES
			break
			;;

		n|N)
			echo NO
			break
			;;

		*)
			echo "invalid input: $REPLY" >&2
			;;
	esac
done


---

### Post by rj175 on 2008-05-12
Thanks for that :D

Works like a dream now 

just another thing is there anyway to check that a directory exists and if it dosnt to create it?

thanks

---

### Post by ghostdog74 on 2008-05-12
```

# test -d directory

```
or
```

if [ ! -d $directory ];then
...
fi

```
by the way, why do need to compile the config file?? If you want to change something inside this file, just use tools like sed/awk will do.....

---

### Post by rj175 on 2008-05-12
im currently installing samba on alot of servers and others who arn't up to scratch on linux are going to be doing the same job so im tryin to make it a tad easier :)

---

