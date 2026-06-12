---
title: "HOWTO: Encrypted directory with EncFS"
date: 2006-03-22
forum: Outdated Tutorials &amp; Tips
---

### Post by remmelt on 2006-03-22
This guide describes how to create encrypted directories. These can come in handy for laptop users, password lists and the like.

**1. Install the software**
```
sudo apt-get install encfs fuse-utils
sudo modprobe fuse
```
And since we don't want to modprobe each time we reboot, add "fuse" to /etc/modules (without quotes, on a line of its own)

**2. Add yourself to the fuse group**
The installer creates a fuse group and to use fusermount you need to be in this group. You can do this with your favourite GUI admin tool or command line:
```
sudo adduser *<your username>* fuse
```

**3. Create a directory where your encrypted stuff will be stored**
I put mine in my home dir, but you can put it anywhere you like.
```
mkdir ~/encrypted
```

**4. Create a mountpoint**
This is the directory where you will mount the encrypted directory. Through this path you can access the encrypted files.
```
mkdir ~/temp_encr
```

**5. Create the encrypted system and mount it**
The first time you try to mount the directory, encfs will create the encrypted filesystem. It works like the regular mount: 
```
encfs <folder to mount> <mount point>
```
So for this example:
```
encfs /home/*<your username>*/encrypted /home/*<your username>*/temp_encr
```
Note that encfs wants absolute paths, i.e. starting with a /

**6. Do the work**
Put some files in your ~/temp_encr folder and look in the ~/encrypted one: they will show up there, encrypted.

**7. Unmount the encrypted filesystem**
Unmounting is as easy as
```
fusermount -u /home/*<your username>*/temp_encr
```

**8. Goto step 5**
Repeat! EncFS will only create the filesystem once, after that first time it will ask for a password and mount your directory.


Remember to keep the two directories apart: in this example the "encrypted" folder holds your encrypted data and should not be used directly. The gateway to access this data is "temp_encr" or whatever you want to call it.


**Sites used:**
[http://arg0.net/wiki/encfs](http://arg0.net/wiki/encfs) - the main EncFS site
[how-to-mount-a-remote-ssh-filesystem-using-sshfs]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/")

---

### Post by GTvulse on 2006-04-04
Several observations:

[LIST]
[*]You need load the kernel module permanently, if you don't want to use modprobe every time. That's easy to fix:
```
sudo <your_editor> /etc/modules
```
Add [FONT="monospace,courier"]fuse[/FONT] to the list and you're done.
[/LIST][LIST]
[*]The system won't recognize you as a memeber of the fuse group until you reboot.
[*] While encfs wants absolute paths, you can let the shell do the expansion for you:
```

encfs ~/.my_hidden_encrypted_dir ~/my_visible_unencrypted_dir
fusermount -u ~/my_visible_unencrypted_dir

```
[/LIST]

---

### Post by remmelt on 2006-04-08
Thanks, I forgot to add that about the modprobe.

---

### Post by kolesarm on 2006-05-11
Good howto, this is just what i've been looking for for some time. Works great!

---

### Post by jgrantham on 2006-06-11
I can not get this to work on on dapper. Has anyone gotten it to work on Dapper yet?

---

### Post by GTvulse on 2006-06-11
[QUOTE=jgrantham]I can not get this to work on on dapper. Has anyone gotten it to work on Dapper yet?[/QUOTE]

Since late January this year. Did you take note of my observations to the how-to?

---

### Post by Juippisi on 2006-06-12
Wow, amazing! Thank you very much, this is something that I've (too) looked for some time. Yea, I wanted to encrypt a directory and not the whole fs. This is just what I've needed.. thanks! :-)

---

### Post by jon_gunnar on 2006-06-12
[QUOTE=remmelt]This guide describes how to create encrypted directories. These can come in handy for laptop users, password lists and the like.

**1. Install the software**
```
sudo apt-get install encfs fuse-utils
sudo modprobe fuse
```
And since we don't want to modprobe each time we reboot, add "fuse" to /etc/modules (without quotes, on a line of its own)

**2. Add yourself to the fuse group**
The installer creates a fuse group and to use fusermount you need to be in this group. You can do this with your favourite GUI admin tool or command line:
```
sudo adduser *<your username>* fuse
```

Remember to keep the two directories apart: in this example the "encrypted" folder holds your encrypted data and should not be used directly. The gateway to access this data is "temp_encr" or whatever you want to call it.


**Sites used:**
[http://arg0.net/wiki/encfs](http://arg0.net/wiki/encfs) - the main EncFS site
[how-to-mount-a-remote-ssh-filesystem-using-sshfs]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/")[/QUOTE]

Thank's a lot for this.I built up amd64 packages of the newest versons and it works very fine.
This were on a Ubuntu 6.06 LTS - Dapper Drake system.
It seems like fuse don't create any new group now.Did not add myself to anything.
But thanks for the info,and if anyone want the newest amd64 debs just send me a mail.

---

### Post by hippyjim on 2006-06-18
Hey thanks for that.

Now for KDE users who dont want to keep going into a terminal to mount their encrypted folder, I found this page on the Gentoo wiki -

[http://gentoo-wiki.com/TIP_EncFS#Using_encFS_with_KDE_.26_Kdialog]("http://gentoo-wiki.com/TIP_EncFS#Using_encFS_with_KDE_.26_Kdialog")

To make it work in Kubuntu you need to change the references of "/usr/kde/3.4/bin/kdialog" to "/usr/bin/kdialog" - but then it works like a charm.

My menu entry looks like:

./mountsafe.sh /full/path/to/encrypted/.store /full/path/to/revealed/store - run as root, with a work path of ~

Hope it's helpful.

---

### Post by berserker on 2006-06-18
[QUOTE=hippyjim]Hey thanks for that.

Now for KDE users who dont want to keep going into a terminal to mount their encrypted folder, I found this page on the Gentoo wiki -

[http://gentoo-wiki.com/TIP_EncFS#Using_encFS_with_KDE_.26_Kdialog]("http://gentoo-wiki.com/TIP_EncFS#Using_encFS_with_KDE_.26_Kdialog")

To make it work in Kubuntu you need to change the references of "/usr/kde/3.4/bin/kdialog" to "/usr/bin/kdialog" - but then it works like a charm.

My menu entry looks like:

./mountsafe.sh /full/path/to/encrypted/.store /full/path/to/revealed/store - run as root, with a work path of ~

Hope it's helpful.[/QUOTE]

Works great.  Thanks!

---

### Post by rosslaird on 2006-07-15
This is a pretty cool little app. Thanks for the howto. But I'm a little hazy on the decryption part. I couldn't find an answer about this on the encfs site.

Let's say I put some files into the enc_tmp directory. They do show up, indeed, encrypted, in the /encrypyted directory. But what happens then -- because I now have two directories with these files in them. Do I delete/unmount the tmp directory, or what? If I delete files from the tmp directory, are they deleted in the encrypted directory? I guess what I'm looking for is a way to have the encrypted directory, then access it with the password, and not to have to worry that another directory (i.e. tmp) is showing the same files unencrypted. There does not seem to be a tutorial on the encfs site about all this, so please excuse my lack of knowledge. I'm just getting started with this whole encryption thing.


Ross

EDIT:

I found this nice little CLI Magic tutorial, which helps quite a bit:

[http://www.linux.com/article.pl?sid=06/06/22/1332244](http://www.linux.com/article.pl?sid=06/06/22/1332244)

---

### Post by Sam on 2006-08-18
Thanks remmelt that's exactly what I needed !

Here is a bunch of scripts to mount/unmount your encrypted directory with launchers in menu/panel. It uses zenity to provide a GUI password input and to display password failures.

[list][*]Install zenity if you don't have it
```
$ sudo apt-get install zenity
```

[*]Create a script for asking the password with zenity, I named it **zenity.askpass** and I put it in **~/bin**
```
#! /bin/sh

zenity --entry --text="Enter password:" --hide-text
```

[*]**Optionnal step**: If you want your ~/bin in the PATH environnement variable (in order to type commands stored in that directory without providing the path), add at the end of **/etc/bash.bashrc**
```
#Set personal bin directory in PATH
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
    export PATH
fi
```

[*]Create **~/bin/mount.encrypted**
Change **/home/<your username>/.encrypted/** and **/home/<your username>/encrypted/** according to your system.
Note that I use the switch **--idle=15** so my encrypted directory gets unmount if there is no activity after 15 minutes. Change the value or remove the switch for your needs.
```
#! /bin/sh

out=`encfs --idle=15 --extpass=/home/<your username>/bin/zenity.askpass /home/<your username>/.encrypted/ /home/<your username>/encrypted/`
if [ $? -gt 0 ] ; then
        zenity --error --text="$out"
fi

```

[*]Create **~/bin/umount.encrypted**
Change **/home/<your username>/encrypted/** according to your system.
```
#! /bin/sh

fusermount -u /home/<your username>/encrypted/
```

[*]Make all the scripts executable
```
$ chmod +x ~/bin/zenity.askpass ~/bin/mount.encrypted ~/bin/umount.encrypted
```[/list]
That's all !
Now create your menu items or launchers and use **mount.encrypted** to mount your encrypted directory and **umount.encrypted** to unmount it.

---

### Post by Frédéric Perrin on 2006-08-21
EncFS seems to be what I'm looking for, but I have one question (which seems to be in line with rosslaird's) :
What will happen if, say, the power goes down while I'm using my encrypted partition or if I forgot to unmount the clear partition before switching off the computer ?
Will my files stay in clear on my disc ? For greater security, should I add to the boot / halt sequence something about unmounting the partition ? (and how can I do this ?)
Will setting the mountpoint in /tmp help (I think /tmp is emptied on halt, correct me if I am wrong) ?

---

### Post by Razac on 2006-08-22
Hello,All

Please someone help me i was trying to do just this and i do
have my 2 folders but when i try using them.

this is what i get

You do not have the permissions necessary to view the 
contents of "folder name"

& why is it that when i do this i have to use sudo
i don't see anyone else doing so.

oh yes how do i delete the 2 folders i have now
when i try i just get the above error so i can't delete them.

Thank you

---

### Post by Sam on 2006-08-22
> **Frédéric Perrin said:**
> EncFS seems to be what I'm looking for, but I have one question (which seems to be in line with rosslaird's) :
What will happen if, say, the power goes down while I'm using my encrypted partition or if I forgot to unmount the clear partition before switching off the computer ?
Will my files stay in clear on my disc ? For greater security, should I add to the boot / halt sequence something about unmounting the partition ? (and how can I do this ?)
Will setting the mountpoint in /tmp help (I think /tmp is emptied on halt, correct me if I am wrong) ?

If you don't have a script at startup which mounts your encrypted folder, there is no need to worry. And about the halt sequence, there is no need to put an auto unmount script (in my opinion).

---

### Post by Sam on 2006-08-22
> **Razac said:**
> Hello,All

Please someone help me i was trying to do just this and i do
have my 2 folders but when i try using them.

this is what i get

You do not have the permissions necessary to view the 
contents of "folder name"

& why is it that when i do this i have to use sudo
i don't see anyone else doing so.

oh yes how do i delete the 2 folders i have now
when i try i just get the above error so i can't delete them.

Thank you

Did you add yourself to the fuse group ?
Don't you inverted the hidden encrypted directory and the visible one when mounting ?
To delete your two folders, use sudo
```
$ sudo rm -rf <directory>
```

---

### Post by Razac on 2006-08-23
Hi,Sam

Yes thank you it works now did as you said.
may i ask please i am now trying the scripts
you posted, but now having much luck.

i get this error here

Error decoding volume key,password incorrect

Internal error: failed to exec program: No such file or directory
22:44:53 (SSL_Cipher.cpp:375) newKey: BytesToKey returned 0, expecting 20 key bytes
sh-3.1$ if [ $? -gt 0 ] ; then
>         zenity --error --text="$out"
> fi
sh-3.1$


not sure what the script needs from me?? if you please
can you tell me what you see in this error.

Thank you

---

### Post by Sam on 2006-08-23
> **Razac said:**
> Hi,Sam

Yes thank you it works now did as you said.
may i ask please i am now trying the scripts
you posted, but now having much luck.

i get this error here

Error decoding volume key,password incorrect

Internal error: failed to exec program: No such file or directory
22:44:53 (SSL_Cipher.cpp:375) newKey: BytesToKey returned 0, expecting 20 key bytes
sh-3.1$ if [ $? -gt 0 ] ; then
>         zenity --error --text="$out"
> fi
sh-3.1$


not sure what the script needs from me?? if you please
can you tell me what you see in this error.

Thank you

I think you have made something wrong in the file **~/bin/mount.encrypted** in the line:
```
out=`encfs --idle=15 --extpass=/home/<your username>/bin/zenity.askpass /home/<your username>/.encrypted/ /home/<your username>/encrypted/`
```
Check that the path to zenity.askpass is ok and that the directories are the good ones and in the good order, and that you did not mispelled something.

---

### Post by compwiz18 on 2006-08-23
Couldn't you make a ramdisk and mount the unencrypted directory on that, that way if something happens and you lose power, the RAM is wiped and so is your unencrpyed data.  Or is that being redundant and stupid cause I missed something?

---

### Post by peabody on 2006-08-23
> **Frédéric Perrin said:**
> EncFS seems to be what I'm looking for, but I have one question (which seems to be in line with rosslaird's) :
What will happen if, say, the power goes down while I'm using my encrypted partition or if I forgot to unmount the clear partition before switching off the computer ?
Will my files stay in clear on my disc ? For greater security, should I add to the boot / halt sequence something about unmounting the partition ? (and how can I do this ?)
Will setting the mountpoint in /tmp help (I think /tmp is emptied on halt, correct me if I am wrong) ?

To my knowledge EncFS encrypts per-file, so the worst that can happen is data loss for stuff that wasn't written to disk yet.

---

### Post by Razac on 2006-08-23
Hey,All

@ Sam

Sorry for sounding like a big *** here but when you say
and I put it in ~/bin. just how do you go about doing this

and do you place all of the scripts in ~/bin ????

Thank you ](*,)

---

### Post by bluntu on 2006-08-23
Have anyone here tried TrueCrypt yet? How is it like?

---

### Post by Sam on 2006-08-23
> **Razac said:**
> Hey,All

@ Sam

Sorry for sounding like a big *** here but when you say
and I put it in ~/bin. just how do you go about doing this

and do you place all of the scripts in ~/bin ????

Thank you ](*,)

If you did no mistake you should have thses files:

/home/<your username>/bin/zenity.askpass
/home/<your username>/bin/mount.encrypted
/home/<your username>/bin/umount.encrypted

Hum... I just thought... I didn't mention to make the scripts executable...

Type in a console:```
$ chmod +x ~/bin/zenity.askpass ~/bin/mount.encrypted ~/bin/umount.encrypted
```

---

### Post by Razac on 2006-08-24
Hi,Sam

Again thanks for all the help but i can't seem to get the scripts 
to work for me.??? & i did as you said i put them all in /home/user name/bin

i don't get it works great when i use.

encfs /home/user name/.encrypted_dir /home/user name/unencrypted_dir

&

fusermount -u /home/user name/unencrypted_dir

that's from a Term but as soon as i try using the scripts
no fun :(

any ideas what maybe wrong

Thank you ](*,)

---

### Post by Sam on 2006-08-24
What happen if you type in a terminal:```
~/bin/mount.encrypted
```
Post the output please.

---

### Post by Razac on 2006-08-24
Hi,Sam

First sorry for making this so hard on you,but i am trying here
well here is what i got when i did as you asked.


its@ubuntutime:~$ ~/bin/mount.encrypted
/bin/sh: out=`encfs --idle=15 --extpass=/home/user name/bin/zenity.askpass /home/user name/.encrypted_dir/ /home/user name/unencrypted_dir/`: No such file or directory
its@ubuntutime:~$

Thank you :roll:

---

### Post by Ahriman on 2006-08-25
where you have "user name", you need to replace that with you actual user name.
eg. my user name is khamsin, so it would like like on mine:

encfs --idle=15 --extpass=/home/khamsin/bin/zenity.askpass /home/khamsin/.encrypted_dir/ /home/user name/unencrypted_dir/

also, make sure that you have the directories created, ~/.encrypted_dir and ~/unencrypted_dir
or you can replace the names with other folder names that you want to use.

See how you go.

---

### Post by Razac on 2006-08-25
Hello,Ahriman

Yes i was not sure if it was some rule, that you had to use
user name in place of my name on the forums or not.

but yes i used my name and i also did 
creat, ~/.encrypted_dir and ~/unencrypted_dir

i have no idea what is wrong ](*,)  going nut's here

Thank you all

---

### Post by Ahriman on 2006-08-25
Are you getting exactly the same error message as before? Also, what permissions are on the directories .encrypted_dir and unencrypted_dir ?

---

### Post by Razac on 2006-08-25
Hi,Ahriman

Thanks for gething back at me and to what you asked me yes.
i am stell having the problem, but only when using the scripts 
when i goto Term it all works great. ????

and both of them are drwxr-xr-x  not sure if this is what you
need from me or not.but it would be a plus to have the scripts work.

Thank you ;)

---

### Post by Sam on 2006-08-25
> **Razac said:**
> Hi,Ahriman

Thanks for gething back at me and to what you asked me yes.
i am stell having the problem, but only when using the scripts 
when i goto Term it all works great. ????

and both of them are drwxr-xr-x  not sure if this is what you
need from me or not.but it would be a plus to have the scripts work.

Thank you ;)

I'll post the whole stuff again. Ensure everything is ok. Let's say your username in Ubuntu is [color="Red"]razac[/color] (if not, change every razac found below to your username). Your hidden encrypted directory is /home/[color="Red"]razac[/color]/[color="Blue"].encrypted[/color] and your visible unencrypted directory is /home/[color="Red"]razac[/color]/[color="Magenta"]unencrypted[/color]. Change these if you have another directories. I colorize what you can change to ensure you have not inverted anything.

You should have these directory/files:
[list][*]**/home/[color="Red"]razac[/color]/bin/** (directory)
Put the the right access
```
chmod 755 /home/[color="Red"]razac[/color]/bin
```

[*]**/home/[color="Red"]razac[/color]/bin/zenity.askpass**
```
#! /bin/sh

zenity --entry --text="Enter password:" --hide-text
```
Put the the right access
```
chmod 755 /home/[color="Red"]razac[/color]/bin/zenity.askpass
```

[*]**/home/[color="Red"]razac[/color]/bin/mount.encrypted**
```
#! /bin/sh

out=`encfs --idle=15 --extpass=/home/[color="Red"]razac[/color]/bin/zenity.askpass /home/[color="Red"]razac[/color]/[color="Blue"].encrypted[/color]/ /home/[color="Red"]razac[/color]/[color="Magenta"]unencrypted[/color]/`
if [ $? -gt 0 ] ; then
        zenity --error --text="$out"
fi
```
Put the the right access
```
chmod 755 /home/[color="Red"]razac[/color]/bin/mount.encrypted
```

[*]**/home/[color="Red"]razac[/color]/bin/umount.encrypted**
```
#! /bin/sh

fusermount -u /home/[color="Red"]razac[/color]/[color="Magenta"]unencrypted[/color]/
```
Put the the right access
```
chmod 755 /home/[color="Red"]razac[/color]/bin/umount.encrypted
```

[/list]

If you checked everything, now run this in a console an post the output:
```
/home/[color="Red"]razac[/color]/bin/mount.encrypted
/home/[color="Red"]razac[/color]/bin/umount.encrypted
```

---

### Post by Razac on 2006-08-26
Hey,Sam

Yes we got it working well on my end this was the problem.

#! /bin/sh

out=`encfs --idle=15 --extpass=/home/razac/bin/zenity.askpass /home/razac/.encrypted/ /home/razac/unencrypted/`
if [ $? -gt 0 ] ; then
        zenity --error --text="$out"
fi

Now if you look here

/home/razac/bin/umount.encrypted<---This was my problem when i changed
it to this here---> /home/razac/bin/unmount.unencrypted<-- all worked 100%

wow just like to say a great big thank you
for not giving up on me with this.

\\:D/ \\:D/

---

### Post by Sam on 2006-08-26
No problem, mistakes happen to everyone. I really didn't understand why it didn't work. I hope next time you'll check twice what you do in case of an error ! (copy and paste is your friend) ;-)

---

### Post by Razac on 2006-08-26
Hi,Sam

Oh yes i will and again thank you for all your help.\\:D/ 

Razac

---

### Post by sidestrand on 2006-11-21
I've tried this (using Kubuntu Dapper) but everytime I try:

encfs /home/richard/encrypted /home/richard/temp_encr

I get the reply:

fuse: failed to exec fusermount: Permission denied
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message

I had done 'modprobe fuse' before this but it doesn't seem to take any notice:confused: 

All the correct packages are installed, I'm sure.  

Any ideas?

Thank you

---

### Post by zek725 on 2006-12-02
```
encfs ~/encrypted ~/xtmp
```

returns...

> fusermount: mountpoint is not empty
fusermount: if you are sure this is safe, use the 'nonempty' mount option
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message

directory (mountpoint) is empty :confused:

**problem solved!**
I reboot pc, deleted the two folders and repeated the steps in creating the two folders. :)

---

### Post by zek725 on 2006-12-03
> **sidestrand said:**
> I've tried this (using Kubuntu Dapper) but everytime I try:

encfs /home/richard/encrypted /home/richard/temp_encr

I get the reply:

fuse: failed to exec fusermount: Permission denied
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message

I had done 'modprobe fuse' before this but it doesn't seem to take any notice:confused: 

All the correct packages are installed, I'm sure.  

Any ideas?

Thank you

try ```
sudo encfs /home/richard/encrypted /home/richard/temp_encr
```

---

### Post by dizm on 2007-01-30
Thanks for this.

After "adduser" you can say "newgrp - fuse" to join the newly-made group in your current session (saves having to log out).

---

### Post by scarpent on 2007-02-21
Great instructions, thanks both to Remmelt and follow-up commenters.  No problem getting this to work in Edgy.  I posted about this with a few additional remarks (including getting it to run on Fedora also) at:

 [HOWTO: EncFS Encrypted Filesystem in Ubuntu and Fedora GNU/Linux]("http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/")

---

### Post by JoBangles on 2007-03-03
Hi remmelt,
All went well until I entered step 5. All went O.K. for most of the way, but a note displayed "cannot do you do not have permission". I missed what this referred to, I think it was creating a directory. I rebooted, installed a file in "temp_encr" and the file showed up encrypted in the other directory but displayed as the original  file in the "temp_encr" directory. Any help greatly appreciated.

---

### Post by JoBangles on 2007-03-04
All is now O.K. Ignore my earlier question please. The files are not visible now. Thanks

---

### Post by ingo on 2007-03-10
Hi,

for all those who are on Kubuntu: ```
sudo apt-get install kencfs
```The only thing I cannot work out - sorry about the dumb question - but what kind of data do you put in there? Or is this worth another thread?

---

### Post by scarpent on 2007-03-10
You mean, what kind of data do you want to keep encrypted?  Could be financial information.  A personal journal.  Seditious material.  You name it.

---

### Post by ingo on 2007-03-11
Thank you scarpent, so far so good. I have this file with say all my passwords (although [https://www.boxknox.com](https://www.boxknox.com) is a good alternative for those on a number of machines).

What is the normal working process now - do I simply mount the encrypted drive and tie in any files on there in my address book, my email programme or my bookmarks into firefox automatically? If so, then the programme is excellent!

Or is the above not the case? If not, could you briefly explain how you use it?

Thanks in advance!

---

### Post by scarpent on 2007-03-11
Sure -- you just use it however you'd like.  You can keep your Firefox files in there if you wanted to, and make .mozilla be a symbolic link in to the mounted clear text volume.  It might be mounted most of the time you use your computer and therefore accessible by anyone with root or your logon, but if you shut the machine down or if it was stolen, you'd be protected from financial info being stolen (for example).

(For passwords in Windows I've used Password Safe.  I'm planning on using Password Gorilla in Ubuntu, which is based on Password Safe.  It's a nice password manager that may provide more than a simple password file.  For example, it has it's own password and can be configured to lock after so many minutes of inactivity.)

---

### Post by ingo on 2007-03-12
Thanks once again, scarpent. I have installed it and put this [http://www.kde-apps.org/content/show.php?content=54078](http://www.kde-apps.org/content/show.php?content=54078) on top to have a nice little GUI to go with it. My post from a couple of days ago (aka apt-get install) obviously does not work, but the above link is for a debian package which works a treat with (K)ubuntu.

---

### Post by berserker on 2007-03-12
> **ingo said:**
> Thanks once again, scarpent. I have installed it and put this [http://www.kde-apps.org/content/show.php?content=54078](http://www.kde-apps.org/content/show.php?content=54078) on top to have a nice little GUI to go with it. My post from a couple of days ago (aka apt-get install) obviously does not work, but the above link is for a debian package which works a treat with (K)ubuntu.

Thank you!  Very nice tool.

---

### Post by Palmyra on 2007-09-02
> **Frédéric Perrin said:**
> EncFS seems to be what I'm looking for, but I have one question (which seems to be in line with rosslaird's) :
What will happen if, say, the power goes down while I'm using my encrypted partition or if I forgot to unmount the clear partition before switching off the computer ?

Of course, we're not talking about the same application, but this may be of relevance:

> Note that TrueCrypt never saves any decrypted data to a disk &#8211; it only stores them temporarily in RAM (memory). Even when the volume is mounted, data stored in the volume is still encrypted. When you restart Windows or turn off your computer, the volume will be dismounted and all files stored on it will be inaccessible (and encrypted). **Even when power supply is suddenly interrupted (without proper system shut down), all files stored on the volume will be inaccessible (and encrypted).** To make them accessible again, you have to mount the volume. To do so, repeat Steps 13-18.

That passage is about Truecrypt.

---

### Post by peabody on 2007-09-29
I'm working off of a feisty install and I noticed that /dev/fuse was group root not group fuse.  Is this a bug in feisty?  I set the group to fuse using chgrp...

---

### Post by phillywize on 2008-03-02
Thanks for this thread!  It's been mentioned elsewhere on ubuntuforums.org, but here's a GTK-compatible tray app for managing encfs:

[http://www.getdeb.net/app/Cryptkeeper](http://www.getdeb.net/app/Cryptkeeper)

---

### Post by phrawzty on 2008-03-09
EDIT: Problem solved, see this thread :
[http://ubuntuforums.org/showthread.php?t=719486](http://ubuntuforums.org/showthread.php?t=719486)



Hello,

While following this tutorial on a reasonably fresh 7.10 system, i received the following error during the initial creation of an encrypted directory :

```
fuse: device not found, try 'modprobe fuse' first
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message

```

I assume the device, in this instance, is /dev/fuse ; however...

```
$ ls -l /dev/fuse
ls: /dev/fuse: No such file or directory
```

Modprobe should create this device, unfortunately...

```
$ sudo modprobe fuse
FATAL: Module fuse not found.
FATAL: Error running install command for fuse
```

Both fuse-utils and libfuse2 are installed :

```
$ dpkg -l | grep fuse
ii  fuse-utils                     2.7.0-1ubuntu5                  Filesystem in USErspace (utilities)
ii  libfuse2                       2.7.0-1ubuntu5                  Filesystem in USErspace library

```

In case the kernel version is relevant :

```
$ cat /etc/issue && uname -a
Ubuntu 7.10 \n \l

Linux sd-11222 2.6.23.10dedibox-r7 #1 Fri Dec 28 00:38:02 CET 2007 i686 GNU/Linux
```

I'm more than happy to accept any and all ideas on what the problem might be.

---

### Post by Johnnny on 2008-04-16
I skimmed through some reviews and read the description of EncFS and somehow this feels the same as Truecrypt except that in Truecrypt you don't see the actual files encrypted in code. But sounds interesting enough I'll look more into it.

Thanks for the tutorial.

---

### Post by Ziggy72 on 2008-04-18
I haven't read through all of this thread, but when I installed encfs, all I did was: 
```

sudo aptitude install encfs
sudo echo “fuse” >> /etc/modules
sudo modprobe fuse
sudo addgroup <your username> fuse
```
Then, using synaptic I installed cryptkeeper. Cryptkeeper looks after making, locating and opening encrypted folders. I find cryptkeeper to be an excellent little program.

---

### Post by Zeroedout on 2008-04-19
> **phrawzty said:**
> EDIT: Problem solved, see this thread :
[http://ubuntuforums.org/showthread.php?t=719486](http://ubuntuforums.org/showthread.php?t=719486)



Hello,

While following this tutorial on a reasonably fresh 7.10 system, i received the following error during the initial creation of an encrypted directory :

```
fuse: device not found, try 'modprobe fuse' first
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message

```I assume the device, in this instance, is /dev/fuse ; however...

```
$ ls -l /dev/fuse
ls: /dev/fuse: No such file or directory
```Modprobe should create this device, unfortunately...

```
$ sudo modprobe fuse
FATAL: Module fuse not found.
FATAL: Error running install command for fuse
```Both fuse-utils and libfuse2 are installed :

```
$ dpkg -l | grep fuse
ii  fuse-utils                     2.7.0-1ubuntu5                  Filesystem in USErspace (utilities)
ii  libfuse2                       2.7.0-1ubuntu5                  Filesystem in USErspace library

```In case the kernel version is relevant :

```
$ cat /etc/issue && uname -a
Ubuntu 7.10 \n \l

Linux sd-11222 2.6.23.10dedibox-r7 #1 Fri Dec 28 00:38:02 CET 2007 i686 GNU/Linux
```I'm more than happy to accept any and all ideas on what the problem might be.
okay, I had your exact same problem just now. All I had to do was restart the system. I'm guessing it just needed to make use of the fact that I added my user to the fuse group.

---

### Post by clfh on 2008-08-12
Have I hit a limitation in extfs that I had not understood?

What I want to do is encrypt a directory containing sensitive database files which are accessed and modified by an applet in a web server (which is remote and which I manage by using ssh). This means the web service is running in a daemon thread, not in a currently-logged-in ssh session.

It appears that extfs creates a session-specific binding between encrypted and decrypted directories. Certainly, if I run extfs from within a first ssh session, then close ssh (without running fusermount -u ), then connect again using ssh I can no longer access my data: the plain text directory is visible to 'ls' but with rubbish time, size etc. Its contents are inaccessible, and I cannot delete it or otherwise access it. 

I shall need to access the plan-text data from the long-lived web server daemon and from transient ssh sessions (for backup purposes). Unless I've misunderstood something or have finger-trouble, I seems I cannot do this with extfs.

Have I misunderstood something, or missed some feature?

---

### Post by boast on 2008-08-17
every time it comes to umounting it after use, it tells me the device is busy.

how can fusermount force umount or how can I tell what program could still be accessing the folder?

nm. its fuser -m folder

---

### Post by gacb on 2010-08-18
> **bluntu said:**
> Have anyone here tried TrueCrypt yet? How is it like?
My eyes glazed over when I was reading the Truecrypt instructions for the 5th time before trying it.

I'm a musician by training and hence a graphic type. Cryptkeeper is more my speed.

One question - other than creating a new unencrypted folder and copying the files, how does one decrypt a folder?

---

### Post by Saeen on 2011-05-12
Hi,
When i run this script from shell
```

#!/bin/sh

cd `dirname $0`
HOME=`pwd` firefox

```
I get these errors:
```

6409): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.

(<unknown>:6455): Gdk-CRITICAL **: gdk_drawable_get_display: assertion `GDK_IS_DRAWABLE (drawable)' failed

```

Any Idea ?

---

### Post by lovinglinux on 2011-05-12
Oops, please ignore. I should have edited this, but instead created a new post.

---

### Post by lovinglinux on 2011-05-12
See my reply at [http://ubuntuforums.org/showthread.php?p=10805234#post10805234](http://ubuntuforums.org/showthread.php?p=10805234#post10805234)

---

