---
title: "Howto: make your terminal a bit nicer"
date: 2005-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by oceanelement on 2005-08-10
Anyone who uses terminals and fell victim to long bash lines such as below know the pain of dealing with:

john@nyork:~/directory1/directory2/directory3/.../directory10022/ 

Thus as a newbie, I went on a mission to fix this and got help from bimberi on xchat for ubuntu. 

Step 1: You will need to edit a file called .bashrc and before you do that make a backup. For example the the file is located at /home/john/.bashrc. There are several locations of this file but just stick with this one. 

To backup file in the terminal
> cp .bashrc bashrc.original

Afterwards lets dive into the program. Open .bashrc with gedit or whatever editor you prefer to use. Edit the following that is is in red  > PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)[COLOR=Red]
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '[/COLOR]
    ;;
esac

to ...
> 
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    [COLOR=Red]PS1='${debian_chroot:+($debian_chroot)}\u@\h:\$'[/COLOR] 
    ;;
esac


And voila! the bash should be nice and short from now on   :D

Any comments or corrections is greatly appreciated.

Enjoy

Oceanelement

---

### Post by transactionlogfiller on 2005-08-11
Thanks, I fell foul of the long prompt just last night. This is going to be useful.

---

