---
title: "Add users as a batch script then send them an email"
date: 2006-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by jakedh on 2006-07-28
If you have managed multiple users or intend to in the future you should find this of interest.
I needed a script which would improve my laziness :) so, I wrote one which parses a CSV file with user names, names, and groups and does the dirty work.

The script will add or update a long list of users, create a password for them, set it to expire, and send the users an email. It includes several options in order to prevent accidentally changing every-one's password...that never happened :^o 

So here it is:

```

#!/bin/bash
# create users from list file

cd /home/jake/

mailserver="127.0.0.1"
black='\E[30;48m'
red='\E[31;48m'
green='\E[32;48m'
yellow='\E[33;48m'
blue='\E[34;48m'
magenta='\E[35;48m'
cyan='\E[36;48m'
white='\E[37;48m'

x=0
usernum=0
line=

username=
fullname=
password=
crypword=
groups=
addusers=0
update=0
email=0
userfailed=0
quiet=0
changepassword=0
fake=0
defaultgroups="users,audio,cdrom,floppy,video,plugdev,scanner"
exitstat=
newusersfile="newusers.csv"
existingusersfile="existingusers.csv"
file=""
messagefile="userupdate.html"
domain="home.com"
adminuser="admin"
adminname="Jake"
admingroups="activemembers" # Not completely implemented
adminemail="$adminuser@$domain"
admin="Admin <$adminemail>"
subject="Your new user account"

function usage
{
	echo -e "-a --add\tAdd users from $newusersfile"
	echo -e "-d --dummy\tUse a dummy user"
	echo -e "-e --email\tSend an email to the users"
	echo -e "-h --help\tShow this list"
	echo -e "-f --fake\tList actions, do nothing"
	echo -e "-p --password\tChange passwords"
	echo -e "-q --quiet\tBe quiet!"
	echo -e "-u --update\tUpdate users from $existingusersfile"
}

function checks
{

	if [ $addusers == $update ]; then
		usage
		exit 1
	fi

	if [ $addusers == 1 ]; then
		file=$newusersfile
	fi

	if [ $update == 1 ]; then
		file=$existingusersfile
	fi

	if [ $update == 1 ] && [ $changepassword == 1 ]; then
	#	usage
	#	exit 1
		file="updateusers.csv"
	fi
}

function dostuff
{
	mkdir /home/$username/Desktop &> /dev/null
	mkdir /home/$username/Documents &> /dev/null
	mkdir /home/$username/.mozilla &> /dev/null
	ln -s ../Desktop /home/$username/.winprofile/ &> /dev/null
	ln -s ../../.mozilla /home/$username/.winprofile/Application\ Data/Mozilla &> /dev/null
	ln -s ../Documents /home/$username/.winprofile/My\ Documents &> /dev/null
	ln -s ../Desktop /home/$username/.winprofile/ &> /dev/null
	rm Examples &> /dev/null
#	cp -p /home/jake/.dmrc /home/$username/
#	chown -R $username:$username /home/$username &> /dev/null
#	chmod -R 755 /home/$username/* &> /dev/null
#	chmod -R 755 /home/$username/.* &> /dev/null
#	chmod 755 /home/$username &> /dev/null
#	setfacl -R -P -b /home/$username &> /dev/null
#	setfacl -R -P -m g:admin:rwx /home/$username &> /dev/null
#	setfacl -R -P -d -m g:admin:rwx /home/$username &> /dev/null
#	setfacl -b /home/$username/.dmrc &> /dev/null
	chmod 644 /home/$username/.dmrc &> /dev/null
}

function adduser
{
	sudo groupadd -f $username &> /dev/null
	sudo useradd --comment "$fullname" --create-home --gid $username --groups $defaultgroups$groups $crypword $username &> /dev/null
	stat=$?
	case $stat in
		9 )	echo -e $red"$username exists; bailing!"; tput sgr0
				userfailed=1;;
		6 )	echo -e $red"$username: unknown group in listing...bailing"; tput sgr0
				userfailed=1;;
		0 )	userfailed=0;;
		* )	echo -e $red"useradd exit status: $stat"; tput sgr0
				userfailed=1
	esac
	if [ $userfailed != 1 ]; then
		dostuff
	fi
}

function updateuser
{
	sudo groupadd $username &> /dev/null
	sudo usermod -c "$fullname" -g $username -G $defaultgroups$groups $username &> /dev/null
	stat=$?
	case $stat in
		9 )		echo -e $red"$username exists; Ignoring!"; tput sgr0
					userfailed=1;;
		8 )		echo -e $red"$username seems to be logged in. bailing on this one..."; tput sgr0
					userfailed=1;;
		6 )		echo -e $red"$username: does not exist or contains unknown group. please check...bailing"; tput sgr0
					userfailed=1;;
		1 )		echo -e $red"must be root!"; tput srg0
					userfailed=1;;
		0 )		userfailed=0;;
		* )		echo -e $red"unknown usermod exitstatus: $stat"; tput sgr0
					userfailed=1
	esac
	if [ $userfailed != 1 ]; then
		dostuff
	fi
}

function handleuser
{
	userfailed=0
	if [ $changepassword == 1 ]; then
		password=$(apg -x8 -n1)
		crypword="-p `echo $password| openssl passwd -1 -stdin`"
	else
		crypword=""
	fi

	line=$(head -n $x $file | tail -n 1)
	if [ -n "$line" ]; then
		username=`echo $line| cut -s -d, -f 1| sed "s/\"//g"`
		fullname=`echo $line| cut -s -d, -f 2| sed "s/\"//g"`
		groups=`echo $line| cut -s -d, -f 3| sed -e "s/\"//g" -e "s/+/,/g"`
	fi
	
	if [ -n "$groups" ]; then
		groups=`echo ,$groups`
	else
		groups=""
	fi
	
	if [ $update == 1 ]; then
		updateuser
	fi

	if [ $addusers == 1 ]; then
		adduser
	fi

	if [ $changepassword == 1 ] && [ $userfailed == 0 ]; then
		sudo passwd --expire --quiet $username
#		echo -n $password
		echo -e "$password\n$password" | smbpasswd -a -s $username &> /dev/null
	fi
	
	if [ $email == 1 ] && [ $userfailed == 0 ]; then
		groups=`echo "$groups"| sed -e "s/,/ /g"`
		cat $messagefile|
		sed --expression "s/usersfullname/$fullname/g" --expression "s/yourusername/$username/g" --expression "s/Username:/Username: $username/g" --expression "s/Password:/Password: $password/g" --expression "s/Groups: /Groups:$groups/g"|
		sendEmail -f "$admin" -t "$fullname <$username@$domain>" -bcc $adminemail -u "$subject" -s $mailserver -q
	fi

	if [ $quiet == 0 ] && [ $userfailed == 0 ]; then
		echo -e "$username\E[$usernum;12H$fullname\E[$usernum;33H"$green"done"; tput sgr0
	fi

	if [ $userfailed == 0 ] && [ $fake == 0 ] && [ $update != 1 ]; then
		echo -e "`sed -e '/^[\"]'$username'[\"]/d' $newusersfile`" &> $newusersfile
		echo $line >> $existingusersfile
	fi

}

function mainloop
{
	x=1
	usernum=0
	y=$(wc -l <$file)
	while [ $x -le $y ]; do
		let usernum=usernum+1
		handleuser
		let x=x+1
	done
}

while [ "$1" != "" ]; do
	case $1 in
		-a | --add	)	addusers=1;;
#		-d | --dummy	)	shift; dummy=1;; ## Not implemented
		-e | --email	)	email=1;;
		-h | --help	)	usage; exit;;
		-f | --fake	)	fake=1;;
		-p | --password	)	changepassword=1;;
#		-q | --quiet	)	quiet=1;;
		-u | --update	)	update=1;;
		*		)       usage; exit 1
	esac
	shift
done

####MAIN####

checks
clear

if [ $fake == 1 ]; then
	exit ## Not completely implemented...
	userdel $username
	username=$adminuser
	fullname=$adminname
	groups=$admingroups
	handleuser
else
	mainloop
fi

if [ $quiet == 0 ]; then
	echo -e "\n$green!!! all done !!!\n"; tput sgr0
fi

exit 0


```


users are added to the samba list but be-ware: users should change their password on windows
note: this feature assumes that you use samba and is configured to sync unix passwords

---

### Post by cursedTCO on 2006-11-22
Hi,

that script looks to do exactly what i need.
Whats the format of the csv file?

Thanks
~cursed~

---

### Post by jakedh on 2006-11-22
The format of the CSV file is:
"username","User's Full Name","groups+the+user+belongs+to"
Example:
"jake","Jake H","soccerteam+trackteam"

There are two CSV files; newusers.csv & existingusers.csv
The HTML file used for sending an email is: userupdate.html
You can include fields such as "usersfullname" which is replaced by "Users's Full Name".

The script makes several assumptions that you...
have installed "sendEmail"
are using Samba on the local system
are using file ACLs (access control lists)
keep your CSV and HTML files in /home/jake; you can change this at the first line of the script

If you have any modifications to make please post them. I would love to see this written so that it is as generic as possible for everyone.

I have posted my most recent copy of the script.

Enjoy.

---

