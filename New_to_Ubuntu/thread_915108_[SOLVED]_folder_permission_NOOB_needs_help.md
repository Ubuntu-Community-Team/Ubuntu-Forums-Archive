---
title: "[SOLVED] folder permission NOOB needs help"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by jedat1 on 2008-09-09
Hi all, I've only been using Linux for a week so still trying to find my way around.

I've got a couple of folders on my desktop that i want to delete, however when i try to delete normally it tells me i don't have the right permissions to do so.

I'm running Hardy Heron loaded through windows with wubi. I followed all the prompts on install regarding users and passwords. Now whenever i try to delete these folders get told that they belong to root and i don't have the right access.

Reading round the net it says HH has the root user disabled as standard and using my ordinary user password will sufice. not having any luck with that.  Anyone any ideas how to get these files back under my control so i can get rid.

Thanks
JOhn

---

### Post by knix on 2008-09-09
you have to launchanything you want to run as root froom the command line or alt+F2, using sudo for command line programs, and gksu for graphical.

Edit: E.g., Alt+F2 >> gksu nautilus >> navigate to folder >> delete folder
or Terminal>> sudo rm -r /path/to/folder
or Alt+F2 >> gksu rm -r /path/to/folder

(rm -r for folders, rm for files.)

---

### Post by elmoosecapitan on 2008-09-09
There was someone who was having a similar problem today. Here you go:

[http://ubuntuforums.org/showthread.php?t=914884](http://ubuntuforums.org/showthread.php?t=914884)

---

### Post by starcannon on 2008-09-09
There are 2 ways that come to mind.

1) Alt-F2, then type: gksu nautilus, press enter.
[INDENT]now your running the file manager as root, browse to the offending folders or files and delete them, be careful, you can delete anythin you like while running as root, so don't delete the wrong things[/INDENT]

2) Open a Terminal: Applications>Accessories>Terminal
[INDENT]```
cd Desktop
sudo rm -r name_of_folder
```when you want to remove a folder and all of its contents you must use the -r (recursive) flag, use this command with caution, again being sure you are not accidentally deleting something you wish to keep[/INDENT]

GL have fun

---

### Post by xeth_delta on 2008-09-09
> **jedat1 said:**
> Hi all, I've only been using Linux for a week so still trying to find my way around.

I've got a couple of folders on my desktop that i want to delete, however when i try to delete normally it tells me i don't have the right permissions to do so.

I'm running Hardy Heron loaded through windows with wubi. I followed all the prompts on install regarding users and passwords. Now whenever i try to delete these folders get told that they belong to root and i don't have the right access.

Reading round the net it says HH has the root user disabled as standard and using my ordinary user password will sufice. not having any luck with that.  Anyone any ideas how to get these files back under my control so i can get rid.

Thanks
JOhn

What seems unusual to me is to have items on your desktop that do not belong to your user account and which hence require administrative rights to remove.

May I ask how you placed them? Did you do it yourself or was it some program?

For more information about sudo have a look at: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) and [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by dannyboy79 on 2008-09-09
> **jedat1 said:**
> 
Reading round the net it says HH has the root user disabled as standard and using my ordinary user password will sufice. not having any luck with that.  Anyone any ideas how to get these files back under my control so i can get rid.

Thanks
JOhn
just wanted to point this out, it's not that the root account is disabled, it's that the root user password isn't set and therefore you can't login under root. Someone correct me if I am wrong. There's of course a root account because you have folders that belong to root so that would mean that there is a root account, right?

What everyone is suggesting is true, follow what they say and you'll be golden. When using sudo, you just use you're own users password. logging in as root and or changing users to root and working that way is very dangerous because if you delete something it's gone, hence why Ubuntu uses sudo and has system critical folders/files owned by root. You can read that link about sudo to give you a better understanding.

I also am curious how folders were created on your desktop that are owned by root? Unless you did something like sudo mkdir ~/Desktop/folder from the command line, that would create a folder using root privelages which would automagically make it owned by root I think?

---

### Post by jedat1 on 2008-09-09
cheers for the answers guys, Starcannon it worked like a charm.

The folders were the remnants of bittorrent downloads, i'd downloaded them onto the desktop and extracted the file from them, i'd deleted most of the rar's in the folder but for some reason the folder got locked.

Thanks again

John

---

### Post by knix on 2008-09-09
Re: root user account disabled:
You cannot log in as root at GDM
You cannot use su to become root in the terminal.
You CAN use sudo bash to become root in the terminal
You CAN get into X as root if you install LXDE, then run startx as root when X and GDM aren't running. (you shouldn't)

---

### Post by billgoldberg on 2008-09-09
You could open nautilus as root or remove it using sudo from the command line, but if you can't delete folders from the desktop, then something as wrong.

You do not need root access to delete anything in your /home .

---

### Post by u-slayer on 2008-09-10
I got annoyed with this so I wrote a script to takeover folders that didn't belong to me. Now whenever I have errant folders or files I just type
```
sudo takeover folder
```

Here's my script. It should automatically detect what user is logged on and give that user ownership of the folder.

```
#Change ownership of files to the $user

print_usage() 
{ extractor -c -f $0 -t @manual@ ;}

#Get Options
while getopts 'u:' OPTION
do
  case $OPTION in
  u)	user=$OPTARG;;
  g)	group=$OPTARG;;
  ?)	print_usage; exit 2;;
  esac
done
shift $(($OPTIND - 1))


if [ ! $user ]; then user=`logname`; fi
if [ ! $group ]; then group=`groups $user | sed 's/ .*//'`; fi

if [ $1 ]; then
	for file in "$@"; do
		let "index+=1"
		eval chown $user:$group -R "'$file'"
		eval ls -lh "'$file'"
	done
else
	chown $user:$group -R .
	ls -lh .
fi

exit 0

@manual@
Usage: takeover [OPTIONS] file1, file2...

Optional:
	-u username
	-g group
@manual@

```

---

### Post by grashdur on 2008-11-10
Thank you starcannon for the useful post with gksu nautilus -- much better than logging in as root, which is what I used to do in these situations.

Billgoldberg, I think you're very right. I'm having the same problem, but I'm not satisfied with just changing files as root. I have more and more files that only root can access, in my home folder, and this doesn't seem right. Also, root cannot reassign permissions for these folders back to my main user account -- either the permissions revert back to root within a few minutes, or they simply do not reassign.

I'm trying to set up a fresh install of HH after a couple failed attempts at getting Itchy Ibex to run on my Gateway computer. I'm just going to ditch and reinstall this one more time. 

U-slayer, that takeover command looks like a great idea. I assume I'd create a file to put those commands in. What exactly would I name the file, and where would I put it?

---

