---
title: "change uid to match username"
date: 2012-07-02
forum: Programming Talk
---

### Post by jahst on 2012-07-02
Ok, so UID drives me nuts sometimes.
I work on too many different PC's in different locations with different names, etc, to remember which name is which UID so if i use external hard drives to bring files to others PC's and the UIDs dont match, i have issues. 



Why can't I base the UID on the username just ensuring each username is unique? 



Why doesn't ubuntu just do this for me?



Something like this comes to mind.

* NOTE - i just wrote it.. didnt test it yet, but you can see what I'm getting at. It has some redundencies, probably some errors, and most definitely some better ways to do things...for example I plan on integrating it into the "adduser" command and also loop through existing users... and I get that I could end up with 2 different users that add up to the same values... plenty of ways around that in the future...I'll keep updating it. Just looking for some feedback before I invest more time.

I only have 10 or so users per PC so should be good enough for me.

How would it stand up in larger systems with more users?


The code should be safe to run... (should probably read it first)... just leave the config set to "no". 
Works on Ubuntu 12.04 64bit


```



#!/bin/bash


########################################################################
echo '
########################################################################
	Copyright (C) 2012 Christopher Bowhuis
	This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
########################################################################
'
########################################################################





MinUid='1100'
Admin_1000_Check='yes' 						# ( no / yes ) # checks if you have admin rights # recommended yes
Admin_User_Check='no' 						# ( no / yes ) # checks if you have admin rights # recommended yes
Do_Chown_Chmod='no'						# chown the /home/username folder # recommended yes
Do_Chown_Chmod_on_all_found_files='no'	# Find all files / mathing username and chown them.. this can take a long time.






echo ############################################
echo "MinUid is ACTIVE ($MinUid)"
echo ""
ls /home
echo ""
echo ############################################




echo "Enter username to fix userid / groupid, etc."
read username


if [ "$Admin_1000_Check" != "no" ] ; then
	UidCheck=$(getent passwd 1000 | sed -e 's/\:.*//')
	IAM=$(whoami)
	if [ "$UidCheck" = "$username" ]; then
		echo "You are trying to change yourself from admin/sudo group!"
		echo "You must do this manually do this to ensure you dont break your system"
		read
		exit 0
	fi
fi


# Admin check
if [ "$Admin_User_Check" != "no" ] ; then
	Administrator_Group=$(cat /etc/group | grep sudo | cut -d':' -f4)
	for Administator_Username in ${Administrator_Group[@]} ; do
		if [ "$Administator_Username" = "$username" ] ; then
			echo "ERROR: \"$Administator_Username\" is in the sudo group"
			echo "Trying to change an Admin Account.. this should be done manually!"
			read
			exit 0
		fi
	done
fi





# home dir check
if [ ! -d "/home/$username" ]; then
	echo 'ERROR: Invalid User name'
	echo "No /home/$username directory found!"
	read
	exit 0
fi


# passwd file check
CurrentUserCheck1=$(cat /etc/passwd | grep "$username" | wc -l)
if [ "$CurrentUserCheck1" != '0' ] ; then
	echo "Username Found!"
else
	echo "ERROR: $username not found!"
	read
	exit 0
fi









NewUid="$MinUid"
# max allowed is 16bit 60000
username=$(echo "$username" | tr '[:upper:]' '[:lower:]')	# just make everything lowercase
i=0
while [ $i -lt ${#username} ] ; do
	
	LetterInName=${username:$i:1}
	NameLetters[$i]=$LetterInName
	
	
	Alphabet=(a b c d e f g h i j k l m n o p q r s t u v w x y z)
	AlphabetNumber=1
	for AlphabetLetter in ${Alphabet[@]} ; do
		if [ "$LetterInName" = "$AlphabetLetter" ] ; then
			echo -en "$i) $AlphabetLetter:$AlphabetNumber "
			echo -en " ( $NewUid"	
			AlphabetNumber="$AlphabetNumber"
			if [ "$i" = '0' ] ; then
				AlphabetNumber=$(($AlphabetNumber * 1000))
			elif [ "$i" = '1' ] ; then
				AlphabetNumber=$(($AlphabetNumber * 100))
			elif [ "$i" = '2' ] ; then
				AlphabetNumber=$(($AlphabetNumber * 10))
			fi
				NewUid=$(($NewUid + $AlphabetNumber))

			echo -en " + $AlphabetNumber = $NewUid )"
			echo ""			

		fi
		let "AlphabetNumber += 1"			
	done
	i=$((i+1))
done



#echo ${NameLetters[@]}
echo ""
echo ""
echo "should have NewUid ($NewUid)"


if [ "$NewUid" -gt "$MinUid" ] ; then
	echo "$NewUid is greater than $MinUid"
	echo "Checking for existing users"
	
	
	CurrentUserCheck2=$(getent passwd "$NewUid" | sed -e 's/\:.*//' | wc -l)
	if [ "$CurrentUserCheck2" = '0' ] ; then
		echo "Username $username and Uid $NewUid Available!"
	else
		echo "ERROR: $NewUid taken"
                #exit 0
	fi
	
	
	
	
else
	echo "ERROR: $NewUid is less than $MinUid"
        # exit 0
fi


echo "usermod -u \"$NewUid\" \"$username\""
echo "groupmod -g \"$NewUid\" \"$username\""
echo "chown -R \"$username:$username\" \"/home/$username\""


if [ "$Do_Chown_Chmod" = "yes" ] ; then
	echo -en "$username old --> "
	id $username
	sudo usermod -u "$NewUid" "$username"
	sudo groupmod -g "$NewUid" "$username"
	sudo chown -R "$username:$username" "/home/$username"	
	echo -en "$username new --> "
	id $username
fi


if [ "$Do_Chown_Chmod_on_all_found_files" = "yes" ] ; then
	#find / -user "$username" -exec sudo chown "$NewUid:$NewUid" '{}' \;
        find / -user "$username" -exec sudo chown "$username:$username" '{}' \;
fi



echo 'End of Script'
read



```




Thoughts and opions welcome,
Thanks,
Jahst

---

### Post by oldfred on 2012-07-02
Instead of UUIDs why not use labels, then you can be consistent as the label can be anything you create.

ls /dev/disk/by-label -lah
UUID & labels
sudo blkid -o list

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

> Alternately syntax to refer to partitions : 

[LIST]
[*]Device : /dev/sdxy 
[*]Label : LABEL=label
[/LIST]


---

### Post by jahst on 2012-07-02
"why not use labels"

Because it has nothing to do with fstab... 
i'm talking about user id, group id, etc.


So i work on my friends and families PCs in various locations.

My account is always fine.

But lets say, i have my family side (say 5 PCs), my wifes side (lets say 6 pcs), and of course my own family.. lets say 3 PCs.

Nobody has the same name in all the families.

currently (and please correct me if I am wrong), if say "bill" needs access to 1 or 2 computers in each families house, he needs an account. If he is user ID 1002 on my pc, and 1006 on another, and 1008 on another..the user IDs doesnt match, then he gets locked out of his files, or worse can access other peoples.

i never seem to have a problem at home where the users are all the same order and same userids, but when I setup accounts elsewhere in a different order, I always seem to have this problem. 

I was under the impression file permissions are based on UID's (user ID's) not usernames?

---

### Post by oldfred on 2012-07-02
I think then you need groups & group IDs. But I do not know how to do that. And you would have to set that up on every system.

Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

---

