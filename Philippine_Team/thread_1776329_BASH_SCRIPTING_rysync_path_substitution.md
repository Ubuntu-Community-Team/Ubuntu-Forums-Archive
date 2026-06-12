---
title: "BASH SCRIPTING: rysync path substitution"
date: 2011-06-06
forum: Philippine Team
---

### Post by username.1919 on 2011-06-06
hi, a little help with bash scripting? i can't figure out why this script is not working, something to do with variable substitution..
here's the script:
```
#!/bin/bash

#hosts list
{
cat << HOSTS
server@ABDA.local
workstation-0@ABDA-II.local
workstation-1@ABDA-III.local
workstation-2@ABDA-IV.local
workstation-3@ABDA-V.local
thanatos@tartarus.local
HOSTS
} > /tmp/_host
_hostname=`cat /tmp/_host`

#rsync arguments
_opts1="--delete -ahHkKL"
_opts2="-avzhP --stats --fake-super --super --rsync-path='rsync --fake-super --super'"
_opts3="-avzhP $4"

#main source/destinations for rsync transfers used by '--all'
_src_hme=`echo '~/{.profile,.bashrc,.bash_aliases,Bricsys,Templates,Scripts}'`
_src_ssh=`echo '~/.ssh/{config,authorized_keys,known_hosts}'`
_src_wal=`echo '~/Pictures/Wallpapers'`
_src_ter=`echo '~/.gconf/apps/gnome-terminal'`

_dst_hme=`echo '~/'`
_dst_ssh=`echo '~/.ssh'`
_dst_wal=`echo '~/Pictures'`
_dst_ter=`echo '~/.gconf/apps'`

#test if script is being run in a terminal
if [ -t 0 ];
then
msg="echo"		#use echo for messages
root="sudo"		#use sudo for root
else
msg="notify-send"	#use notifyOSD for messages
root="gksudo"		#use gksudo for root
fi

{
case $1 in
-u|--upload|upload)
job=upload
xfer=to
;;
	
-d|--download|download)
job=download
xfer=from
;;

-h|--help|help|--usage)
cat << HELP
DESCRIPTION:
Sync files to/from your local area network.

USAGE:
resync [job] [options] [workstation]

JOB TYPES:

-u, --upload		Upload	 files across workstations on your LAN
-d, --download		Download files across workstations on your LAN


OPTIONS:
-a, --all		Sync everything to all workstations
			files/folders included in the sync are:
			-- ~/Bricsys
			-- ~/Scripts
			-- ~/Templates
			-- ~/.profile
			-- ~/.bashrc
			-- ~/.bash_aliases
			-- ~/.ssh/authorized_keys
			-- ~/.ssh/config
			-- ~/.ssh/known_hosts
			-- ~/.gconf/apps/gnome-terminal
			-- ~/Pictures/Wallpapers

-s, --scripts		Sync ~/Scripts to workstations
-S, --ssh		Sync ~/.ssh to workstations
-t, --templates		Sync ~/Templates to workstations
-w, --wallpapers	Sync ~/Pictures/Wallpapers to workstations
-P, --Projects		Sync ~/Projects to workstations
-A, --apt		Sync /var/cache/apt/archives to workstations
-h, --help		Display this help
    --options

WORKSTATIONS:
-s, --server		Sync to server
-0, --pc0		Sync to workstation-0
-1, --pc1		Sync to workstation-1
-2, --pc2		Sync to workstation-2
-3, --pc3		Sync to workstation-3
-l, --laptop		Sync to laptop

Note:			If a workstation is not specified, resync will
			automatically sync to all workstations across the
			Local Area Network or LAN.

HELP
;;	

*)
cat << USAGE
Specify a job type:

VALID JOB TYPES:

-u, --upload		Upload	 files across workstations on your LAN
-d, --download		Download files across workstations on your LAN

Type resync --help for more info.
USAGE
exit 1
;;
esac
}
{
case $2 in
-a|--all|all)
option=all
opts=$_opts1
;;
-s|--scripts|scripts)
option=scripts
src=`echo '~/{.profile,.bashrc,.bash_aliases,Scripts}'`
dst=`echo '~/'`
opts=$_opts1
;;
-S|--ssh|ssh)
option=SSH
src=`echo '~/.ssh/{config,authorized_keys,known_hosts}'`
dst=`echo '~/.ssh'`
opts=$_opts1
;;
-t|--templates|templates)
option=templates
src=`echo '~/Templates'`
dst=`echo '~/'`
opts=$_opts1
;;
-w|--wallpapers|wallpapers)
option=wallpapers
src=`echo '~/Pictures/Wallpapers'`
dst=`echo '~/Pictures'`
opts=$_opts1
;;
-A|--apt|apt)
option=apt
src="/var/cache/apt/archives"
dst="/var/cache/apt"
opts=$_opts2
;;
-P|--projects|projects)
option=projects
src="~/Projects"
dst="~/"
opts=$_opts3
;;
*)
cat << OPTIONS
Unknown or no option specified.
Type resync --help for more info.
OPTIONS
exit 2
;;
esac
}

if test -z "$3"; then #if 3rd variable is not specified, default to '--all'
workstation=ALL
else
{
case $3 in
-a|--all|all)
workstation=ALL
;;
-s|--server|server)
workstation=s
_username=`echo "${_hostname}" | head -1 | cut -d @ -f1`
_userip=`echo "${_hostname}" | head -1 | cut -d @ -f2`
_user=`echo "${_hostname}" | head -1`
;;
-0|--pc0|pc0)
workstation=0
_username=`echo "${_hostname}" | head -2 | tail -1 | cut -d @ -f1`
_userip=`echo "${_hostname}" | head -2 | tail -1 | cut -d @ -f2`
_user=`echo "${_hostname}" | head -2 | tail -1`
;;
-1|--pc1|pc1)
workstation=1
_username=`echo "${_hostname}" | head -3 | tail -1 | cut -d @ -f1`
_userip=`echo "${_hostname}" | head -3 | tail -1 | cut -d @ -f2`
_user=`echo "${_hostname}" | head -3 | tail -1`
;;
-2|--pc2|pc2)
workstation=2
_username=`echo "${_hostname}" | head -4 | tail -1 | cut -d @ -f1`
_userip=`echo "${_hostname}" | head -4 | tail -1 | cut -d @ -f2`
_user=`echo "${_hostname}" | head -4 | tail -1`
;;
-3|--pc3|pc3)
workstation=3
_username=`echo "${_hostname}" | head -5 | tail -1 | cut -d @ -f1`
_userip=`echo "${_hostname}" | head -5 | tail -1 | cut -d @ -f2`
_user=`echo "${_hostname}" | head -5 | tail -1`
;;
-l|--laptop|laptop)
workstation=l
_username=`echo "${_hostname}" | head -6 | tail -1 | cut -d @ -f1`
_userip=`echo "${_hostname}" | head -6 | tail -1 | cut -d @ -f2`
_user=`echo "${_hostname}" | head -6 | tail -1`
;;
*)
cat << UNK
"Unknown workstation '${3}'
Type resync --help for more info."
UNK
;;

esac
}
fi

{
case $option in
all) {
	case $workstation in
		ALL) {
		for _user in $_hostname ;
		do
		_username=`echo ${_user} | cut -d @ -f1`
		_userip=`echo ${_user} | cut -d @ -f2`
		ping -c 1 $_userip > /dev/null #check for connectivity.
		if [ "$?" -eq 0 ] ;
		then
			#make sure pc we're syncing into is not our own.
			if [ "$_userip" != "$HOSTNAME.local" ];
			then {
				if [ $job = upload ];
				then
				rsync $opts $_src_hme $_user:$_dst_hme
				rsync $opts $_src_ssh $_user:$_dst_ssh
				rsync $opts $_src_wal $_user:$_dst_wal
				rsync $opts $_src_ter $_user:$_dst_ter
				else
				rsync $opts $_user:$_src_hme $_dst_hme
				rsync $opts $_user:$_src_ssh $_dst_ssh
				rsync $opts $_user:$_src_wal $_dst_wal
				rsync $opts $_user:$_src_ter $_dst_ter
				fi
			} && $msg "resync:" "Done syncing $xfer ${_username}"
			else
			$msg "resync:" "Skipping workstation '$_userip'"
			fi
		else
		$msg "resync:" "${_username} is offline"
		fi
		done
		}
		;;

		s|0|1|2|3|l) {
		ping -c 1 $_userip > /dev/null #check for connectivity.
		if [ "$?" -eq 0 ] ;
		then
			#make sure pc we're syncing into is not our own.
			if [ "$_userip" != "$HOSTNAME.local" ];
			then {
				if [ $job = upload ];
				then
				rsync ${opts} '$_src_hme' ${_user}:'$_dst_hme'
				rsync ${opts} '$_src_ssh' ${_user}:'$_dst_ssh'
				rsync ${opts} '$_src_wal' ${_user}:'$_dst_wal'
				rsync ${opts} '$_src_ter' ${_user}:'$_dst_ter'
				else
				rsync ${opts} ${_user}:${_src_hme} ${_dst_hme}
				rsync ${opts} ${_user}:${_src_ssh} ${_dst_ssh}
				rsync ${opts} ${_user}:${_src_wal} ${_dst_wal}
				rsync ${opts} ${_user}:${_src_ter} ${_dst_ter}
				fi
			} && $msg "resync:" "Done syncing $xfer ${_username}"
			else
			$msg "resync:" "Skipping workstation '$_userip'"
			fi
		else
		$msg "resync:" "${_username} is offline"
		fi
		}
		;;
	esac
	}
	;;

scripts|SSH|templates|wallpapers|projects|apt) {
	case $workstation in
		ALL) {
		for _user in $_hostname ;
		do
		_username=`echo ${_user} | cut -d @ -f1`
		_userip=`echo ${_user} | cut -d @ -f2`
		ping -c 1 $_userip > /dev/null #check for connectivity.
		if [ "$?" -eq 0 ] ;
		then
			#make sure pc we're syncing into is not our own.
			if [ "$_userip" != "$HOSTNAME.local" ];
			then {
				if [ $option = apt ];
				then
				[ "`whoami`" = root ] || exec $root "$0" "$@"
				fi
				if [ $job = upload ];
				then
				rsync ${opts} ${src} ${_user}:${dst}
				else
				rsync ${opts} ${_user}:${src} ${dst}
				fi
			} && $msg "resync:" "Done syncing $xfer ${_username}"
			else
			$msg "resync:" "Skipping workstation '$_userip'"
			fi
		else
		$msg "resync:" "${_username} is offline"
		fi
		done
		}
		;;

		s|0|1|2|3|l) {
		ping -c 1 $_userip > /dev/null #check for connectivity.
		if [ "$?" -eq 0 ] ;
		then
			#make sure pc we're syncing into is not our own.
			if [ "$_userip" != "$HOSTNAME.local" ];
			then {
				if [ $option = apt ];
				then
				[ "`whoami`" = root ] || exec $root "$0" "$@"
				fi
				if [ $job = upload ];
				then
				rsync ${opts} ${src} ${_user}:${dst}
				else
				rsync ${opts} ${_user}:${src} ${dst}
				fi
			} && $msg "resync:" "Done syncing $xfer ${_username}"
			else
			$msg "resync:" "Skipping workstation '$_userip'"
			fi
		else
		$msg "resync:" "${_username} is offline"
		fi
		}
		;;
	esac
	}
	;;
esac
}

#cleanup
[ -e /tmp/_host ] && rm -rf /tmp/_host
exit 0
```

any help will be appreciated.. thanks

---

### Post by DaithiF on 2011-06-06
Hi,
for a realistic chance of a useful response you'll need to be more specific.  You can't just post a 368 line script and say 'its not working, please help' and expect someone to invest the time required to understand what the script is supposed to do and then conjecture all the possible ways that it might 'not work'.

So, what specifically doesn't work?  What line(s) in the script cause the problem?

---

### Post by username.1919 on 2011-06-06
my apologies, basically the script is intended to sync files across workstations on my LAN using rsync. but the thing is, I'm not exactly sure as to which part of the script is giving me problems.

So.. Main logic is: I have a bunch of hosts to sync,
```
#hosts list
server@ABDA.local
workstation-0@ABDA-II.local
workstation-1@ABDA-III.local
workstation-2@ABDA-IV.local
workstation-3@ABDA-V.local
thanatos@tartarus.local

```

but i want the hostnames and paths to be interchangeable, so I won't have a very lengthy rsync $SRC $USER:$DEST script.

what I'm sure of is that the problem has to do with the paths as a variable.

```
#main source/destinations for rsync transfers used by '--all'
_src_hme=`echo '~/{.profile,.bashrc,.bash_aliases,Bricsys,Templates,Scripts}'`
_src_ssh=`echo '~/.ssh/{config,authorized_keys,known_hosts}'`
_src_wal=`echo '~/Pictures/Wallpapers'`
_src_ter=`echo '~/.gconf/apps/gnome-terminal'`

_dst_hme=`echo '~/'`
_dst_ssh=`echo '~/.ssh'`
_dst_wal=`echo '~/Pictures'`
_dst_ter=`echo '~/.gconf/apps'`
```

when the script runs, this is the error i get:
```
rsync: change_dir "/home/user/~" failed: No such file or directory (2)
``` and a bunch of other 'No such file blabla'

---

### Post by DaithiF on 2011-06-06
> **username.1919 said:**
> 

what I'm sure of is that the problem has to do with the paths as a variable.

```
#main source/destinations for rsync transfers used by '--all'
_src_hme=`echo '~/{.profile,.bashrc,.bash_aliases,Bricsys,Templates,Scripts}'`
_src_ssh=`echo '~/.ssh/{config,authorized_keys,known_hosts}'`
_src_wal=`echo '~/Pictures/Wallpapers'`
_src_ter=`echo '~/.gconf/apps/gnome-terminal'`

_dst_hme=`echo '~/'`
_dst_ssh=`echo '~/.ssh'`
_dst_wal=`echo '~/Pictures'`
_dst_ter=`echo '~/.gconf/apps'`
```

the purpose of this line:
```

_src_hme=`echo '~/{.profile,.bashrc,.bash_aliases,Bricsys,Templates,Scripts}'`

```
is to populate the _src_hme variable with the expanded paths to the various files/directories within the { } braces.  But the single quotes prevents this expansion actually happening, so that _src_hme will contain the literal value: ~/{.profile,.bashrc,.bash_aliases,Bricsys,Templates,Scripts}
rather than,
/home/you/.profile /home/you/.bashrc etc..

so:
_src_hme=`echo ~/{.profile,.bashrc,.bash_aliases...etc}`

and same for the other variables.

---

### Post by username.1919 on 2011-06-06
I think i just solved this. Thanks for your input, it was key to what i did.
anyways here's what i did.

removed the single quotes from
```
_src_hme=`echo ~/{.profile,.bashrc,.bash_aliases,Bricsys,Templates,Scripts}`
```

but kept the single quotes from the _dst_hme=`echo '~/'` as this is the destination variable, and would expand to /home/myusername/ instead of /home/remote's-username/ when passed to rsync.

thanks for the help! :)

---

