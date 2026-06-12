---
title: "[SOLVED] Bash replacing rm and rmdir"
date: 2008-05-14
forum: Programming Talk
---

### Post by yao_man on 2008-05-14
I do not know a vast amount of bash, but I know enough to supplement my current interactive shell script here and there. I was trying to create aliases that allowed me to replace rm and rmdir with a command that sends them to trash while simultaneously creating a delete function that after asking for approval, permanently removes a file or directory (like the rm basic function). Here is what I have. ```
alias del="delete"
alias rm="trash"
alias rmdir="trash"

delete () {
	if [ $1 ];then
		if [ -d "$1" ];then
			echo -e "\"$1\" and all of its contents will be erased\nAll contents will be permanently lost\nAction cannot be reversed"
			read -sn 1 -p "Continue? [y/n]" ANS
			echo
			if [[ "$ANS" == "y"  || "$ANS" == "Y" ]];then
				echo "Contents will be permanently lost"
				read -sn 1 -p "Are you sure? [y/n]" ANS
				echo
				if [[ "$ANS" == "y"  || "$ANS" == "Y" ]];then
					rm "$1"/*
					rmdir $1
					echo "Directory and contents deleted"
				else
					echo "Directory not cleared"
				fi
			else
				echo "Directory not cleared"
			fi
		elif [ -f "$1" ];then
			echo -e "\"$1\" will be erased\nAll contents will be permanently lost\nAction cannot be reversed"
			read -sn 1 -p "Continue? [y/n]" ANS
			echo
			if [[ "$ANS" == "y"  || "$ANS" == "Y" ]];then
				echo "Contents will be permanently lost"
				read -sn 1 -p "Are you sure? [y/n]" ANS
				echo
				if [[ "$ANS" == "y"  || "$ANS" == "Y" ]];then
					rm "$1"
					echo "File deleted"
				else
					echo "File not cleared"
				fi
			else
				echo "File not cleared"
			fi
		fi
	else
		echo "\"$1\" does not exist"
	fi
}

trash () { kfmclient move "$1" trash:/; }
```
Is there a way to access rm and rmdir in the delete function without using the aliased rm and rmdir or should I approach this in a different way. Any comments from answers to code improvements/optimizations would be greatly appreciated, thank you.

---

### Post by dwhitney67 on 2008-05-14
Piece of cake... for 'rm', use /bin/rm and for 'rmdir, you guessed it, use /bin/rmdir.

---

### Post by yao_man on 2008-05-14
Fantastic, Problem solved. Thank you very much once again dwhitney

---

