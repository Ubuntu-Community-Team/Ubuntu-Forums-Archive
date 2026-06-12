---
title: "HOWTO: gmailfs automount in edgy"
date: 2006-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by rune_kg on 2006-12-11
This howto will allow you to use a google gmail account as a network drive mounted in /mnt/g

**1 SETUP FOLDER TO MOUNT IN**
```

sudo -s -H
mkdir /mnt/g
chmod 777 /mnt/g
chown username:usergroup /mnt/g
#So if your system username is joe it would most likely be:
#chown joe:joe p /mnt/g

```
**2 SETUP gmailfs**
```

sudo -s -H
apt-get install gmailfs
nano /etc/fstab
#Add this line somewhere in fstab
/usr/share/pycentral/gmailfs/site-packages/gmailfs.py /mnt/g gmailfs username=xxx,password=yyy,fsname=zzz
#replace xxx with google username. yyy with pass and zzz with something hard to guess
mount -a

```

Lines starting with a '#' are comments, and should not be written into terminal.

I can not garantie any support on this howto. I can also not not garantie any support:)

Take care

Rune Kaagaard
[http://runelyd.dk](http://runelyd.dk)

---

### Post by reza81 on 2007-01-10
I Have followed the instructions above, but I can't mount this 'G' drive

ERROR MESSAGE:

Unable to mount the selected volume,

more details:
mount: according to mtab, /fev/fuse
is already mounted on /mnt/g
mount faild



So does anyone know how to fix this ???

---

### Post by maggotbrain on 2007-01-21
Thanks for the HOWTO. Worked flawlessly.

---

### Post by goonies on 2007-01-21
```
root@carlisle:/home/whonicca# mount -a
Ignored option :rw
python: fuse_opt.c:67: fuse_opt_insert_arg: Assertion `pos <= args->argc' failed.
```


```
root@carlisle:/home/whonicca# mount -a
Ignored option :rw
fusermount: failed to access mountpoint /mnt/g: Transport endpoint is not connected
python: fuse_opt.c:67: fuse_opt_insert_arg: Assertion `pos <= args->argc' failed.
```

---

### Post by harrisony on 2007-01-21
@goonies dapper or edgy
it says it worked and i put a file there but i dont know how long it will be until i can get it, it needs some gui for seeing how longer its got to upload

---

### Post by mirshafie on 2007-01-25
I've tried several HOWTOs including the official gmailfs instructions, on Dapper and Edgy, but I always get the same error.

[INDENT]root@mirshafie:/home/mirshafie# mount -a
Ignored option :rw
[/INDENT]

df shows no gmailfs line, and it does not work to copy files to /mnt/g

Anyone know anything about this problem?

---

### Post by lime4x4 on 2007-01-25
same problem as mirshafie

---

### Post by durand on 2007-01-26
> **lime4x4 said:**
> same problem as mirshafie

same here...is that a problem tho?
if u open that folder in root, it seems to open fine...what do u have to do?

EDIT: great howto, worked brilliantly!

to upload files, just open the dir as root:
```
sudo nautilus /mnt/g
```
then drag and drop
nautilus does seem to hang for a while, i guess depending on the file size but it recovers and u should get emails in ur gmail inbox with random code...dont delete them cos they are the files stored as text, i guess.

---

### Post by Wangsta on 2007-01-26
i got it to work in command line mode, but using thunar, it doesn't show anything.

i've add files and accessed them from the command line, and they've shown up in my inbox, but i can't access any of the files in thunar...

---

### Post by goonies on 2007-01-27
> **harrisony said:**
> @goonies dapper or edgy
it says it worked and i put a file there but i dont know how long it will be until i can get it, it needs some gui for seeing how longer its got to upload

edgy

---

### Post by jawbreaker on 2007-01-27
> **mirshafie said:**
> I've tried several HOWTOs including the official gmailfs instructions, on Dapper and Edgy, but I always get the same error.

[INDENT]root@mirshafie:/home/mirshafie# mount -a
Ignored option :rw
[/INDENT]

df shows no gmailfs line, and it does not work to copy files to /mnt/g

Anyone know anything about this problem?

i get the same thing.

i found this post on ubuntu-nl that worked for me...

[http://forum.ubuntu-nl.org/message/5888](http://forum.ubuntu-nl.org/message/5888) #3

---

### Post by durand on 2007-01-27
same thing happens for me though its not a problem. You can run ur file manager as root and /mnt/g works fine...

---

### Post by caffienda on 2007-02-25
When I mount this
 mount -a
Ignored option :rw
Does this matter?

I also have 3 emails with every file copied to the "g" drive.    This is what one of the email subjects looks like.  "v=3 r=1172446558 q=__g__gmail__h__   "
That is pretty bad, is there a way to get this a little more useable?

What is the point of the fsname?  Does it matter what it is named?

---

### Post by tlacuache on 2007-04-03
I followed your instructions and it mounted successfully, but I can only actually enter and use the gmail mount point directory as root.

When I do an "ls -l" as root, I see this in my /media directory:

```
drwxrwxrwx 2 tlacuache tlacuache    1 2007-04-03 08:11 gmail
```

So I can see that I've got the permissions set correctly according to the original post. But when I do it as my user I see this:

```
?--------- ? ?    ?        ?                ? gmail
```

When I do "cd /media/gmail" I get

```
bash: cd: gmail: Permission denied
```

Here's the appropriate line from mount:

```
/dev/fuse on /media/gmail type fuse (rw,nosuid,nodev)
```

Any ideas would be appreciated.

Thanks,

-SG

---

### Post by durand on 2007-04-03
Yup, same problem here...:(

---

### Post by tlacuache on 2007-04-03
I found a workaround that works for me. It's not using fstab, it's using a bash script, but you could add it to you session startup programs for the same result.

I created two .sh files:

Here's gmailmount.sh

```
mount.gmailfs /usr/local/bin/gmailfs.py ~/gmailfs/ -o username=*********,password=********,fsname=********
```

(I have a symbolic link to gmailfs.py in /usr/local/bin, so if you don't, you can change the path accordingly. Also, of course, replace the ******** with your personal information).

Here's gmailumount.sh

```
fusermount -u ~/gmailfs
```

Now I'm finally mounting my gmailfs in ~/gmailfs with permissions to use it. When I'm done, I run the gmailumount.sh script and it unmounts properly.

Hope this helps somebody out.

---

### Post by mssever on 2007-04-03
> **caffienda said:**
> When I mount this
 mount -a
Ignored option :rw
Does this matter?

I also have 3 emails with every file copied to the "g" drive.    This is what one of the email subjects looks like.  "v=3 r=1172446558 q=__g__gmail__h__   "
That is pretty bad, is there a way to get this a little more useable?

What is the point of the fsname?  Does it matter what it is named?

You can find the answers on the gmailfs website. You should protect your fsname like you would your password (and use something much more secure--like a random string). Someone who knows your Gmail address and fsname can send you an email that will corrupt your gmailfs.

To hide the emails, simply create a filter that archives all messages containing the fsname in the subject.

---

### Post by mssever on 2007-04-03
> **tlacuache said:**
> I found a workaround that works for me. It's not using fstab, it's using a bash script, but you could add it to you session startup programs for the same result.

Thanks. Your workaround solved some of my issues and got me started on an alternative solution.

First, my fstab entry: ```
/usr/share/pycentral/gmailfs/site-packages/gmailfs.py /media/gmailfs gmailfs rw,noatime,users,exec,dev,suid,noauto 0 0
```I put the rest of the config in /etc/gmailfs/gmailfs.conf since I don't really like the idea of my password being in fstab. I included the noauto option because for some reason there doesn't appear to be a way to make the fs readable to anyone other than the owner of the mount process, which is root if you mount it during boot time.

Now, it's possible to mount the partition via ```
mount /media/gmailfs
```However, the umount command doesn't work unless you run it as root. The reason is that /etc/mtab shows the fstype as fuse, while fstab gives it as gmailfs. So, I wrote a little script to fix that. Save the following as /usr/local/bin/umount and make it executable. If your mount point doesn't match the regular expression (man grep for the gory details) in the $pattern variable (gmail), set it to something appropriate that won't match any non-fuse mount points.
```
#!/bin/bash

pattern="gmail"

if [[ $1 =~  $pattern ]]; then
  fusermount -u "$@"
  exit $?
else
  /bin/umount "$@"
  exit $?
fi
```Finally, here's a script to power a mount/unmount button on your panel. Save it somewhere and make it executable. Then add an icon on your panel with the path /path/to/script "/path/to/mountpoint" ```
#!/bin/bash

function Xmount {
  mount "$mountPoint" >"$tmpFile" 2>&1
  local exit_status=$?
  local result="$(cat "$tmpFile")"

  if [ Xmounted -a $exit_status -eq 0 ]; then
    zenity --info --text="Successfully mounted $mountPoint"
    Xstatus=0
  else 
    zenity --error --text="Mounting $mountPoint failed with exit status $exit_status. Here's the error message:\n\n\n$result"
    Xstatus=1
  fi
}

function Xumount {
  umount "$mountPoint" >"$tmpFile" 2>&1
  local exit_status=$?
  local result="$(cat "$tmpFile")"

  if [ "X$exit_status" != "X0" ]; then
    zenity --error --text="Unmounting $mountPoint failed with exit status $exit_status. Here's the error message:\n\n\n$result"
    Xstatus=1
  else 
    zenity --info --text="Successfully unmounted $mountPoint"
    Xstatus=0
  fi
}

function Xmounted {
  mount | grep --quiet "$mountPoint"
  return $?
}

function Xmain {
  mountPoint="$1"
  tmpFile="$(tempfile)"

  if Xmounted; then Xumount
  else Xmount
  fi

  rm -f "$tmpFile"
  exit $Xstatus
}

Xmain "$@"
```[COLOR=Gray]
[SIZE=1]EDIT: My 1,000th post! Hooray![/SIZE][/COLOR]

---

### Post by tlacuache on 2007-04-04
> **mssever said:**
> ... got me started on an alternative solution.

And what a solution it was. Thanks, that's exactly what I wanted. Much more elegant than what I'd done.

Thanks and thanks again.

-SG

---

### Post by mssever on 2007-04-04
In my earlier post, I forgot to mention a pitfall that I encountered. If your normal user isn't a member of the fuse group (type groups to find out), then you won't be able to mount/unmount your gmailfs as a normal user.

To add yourself to the fuse group, edit /etc/group and add your username there. For example, my fuse group entry reads ```
fuse:x:124:scott
```Log out and back in to apply the changes.

I'm running Edgy as the result of an upgrade from Dapper, not a clean install. That's probably why I wasn't already a member of the fuse group. If you're running from a clean install, you probably don't need to worry about this.

---

### Post by lotacus on 2007-04-22
I'm wondering if you can be more clear on your script. I copied everything exactly and when I press the launcher to run the script I get an error message saying cannot unmount ""

update: ok, I fixed it... something I overlooked. Now when I press the button I get some error saying that it disagrees with fstab.

fstab entry:

/usr/share/pycentral/gmailfs/site-packages/gmailfs.py /mnt/g gmailfs username=xxx,password=xxx,fsname=xxx,noauto 0 0

---

### Post by lotacus on 2007-04-23
Come on guys. help. heh

Running Edgy 6.10,  used mssever's scripts.

One thing you forgot to mention when adding a launcher button, that in the command properties you have to put in sudo as part of the command, or gksudo. However, I still don't get permissions when trying to browse the directory via console, and when I open it up in the file manager, gmailfs isn't a folder but some other icon as seen in the attachement.

---

### Post by kalahari875 on 2007-04-28
Set this up in Feisty and it does in fact mount. However I cannot rename files in the mounted folder with Nautilus and can only delete files if I Shift+Delete them. Is this expected, or is something wrong with the mounting?

---

### Post by mssever on 2007-04-29
Sorry for the long delay. I've moved recently, and I've had a terrible time finding Internet access where I am now. I'm traveling currently and using the hotel's Internet connection. So, until I get my Internet situation sorted out, I can't promise a timely response. Sorry.

> **lotacus said:**
> update: ok, I fixed it... something I overlooked. Now when I press the button I get some error saying that it disagrees with fstab.

fstab entry:

/usr/share/pycentral/gmailfs/site-packages/gmailfs.py /mnt/g gmailfs username=xxx,password=xxx,fsname=xxx,noauto 0 0
The problem is probably that you're using a mount point that doesn't match the regular expression pattern in the script. Here's how the umount script works: First, it tries to match the supplied mount point against the regex. If it succeeds, then we're dealing with a gmailfs partition, so we have to use fusermount -u to unmount it. If the match fails, then we're dealing with a normal partition, and we call umount to handle it. Because of where this file is saved, it gets called whenever the umount command is given, instead of the normal umount.

The upshot is this: If you know regexes, or if you're willing to invest the time to learn them, then adjust the pattern in /usr/local/bin/umount to match your mountpoint, making sure that you don't accidentally cause collisions with any non-gmailfs partition mountpoints. If you don't want to mess with regular expressions, then make sure that your mount point contains the string "gmailfs" somewhere in it.
> **lotacus said:**
> One thing you forgot to mention when adding a launcher button, that in the command properties you have to put in sudo as part of the command, or gksudo. However, I still don't get permissions when trying to browse the directory via console, and when I open it up in the file manager, gmailfs isn't a folder but some other icon as seen in the attachement.
Actually, it won't work right if you use sudo or gksudo. You have to use your normal user. Your problem is because you're mounting it as root. There's *no way* to set reasonable permissions, as far as I know. That's why my script runs as my normal user, NOT root. AFAIK, it's the only way to make it work.
> **kalahari875 said:**
> Set this up in Feisty and it does in fact mount. However I cannot rename files in the mounted folder with Nautilus and can only delete files if I Shift+Delete them. Is this expected, or is something wrong with the mounting?
Please post the permissions of the some sample files and folders so we can see what's up. The easiest way would be to type ```
ls -ld /path/to/mount/point/*
``` and post the output.

---

### Post by kalahari875 on 2007-04-29
> **mssever said:**
> Please post the permissions of the some sample files and folders so we can see what's up. The easiest way would be to type ```
ls -ld /path/to/mount/point/*
``` and post the output.

Sure thing; It is:

```
-rw-r--r-- 1 myuser myuser     0 2007-04-29 08:08 /media/gmail/new file
-rw-r--r-- 1 root  root  27837 2007-04-03 11:05 /media/gmail/oo-maxwell.odt

```

The first file I created by right-clicking in the folder and doing Create Document. The second I copied from the default examples folder. Even though the permissions on the second file are set to root, the effect is the same: I can shift+delete but not simply press delete, and I cannot rename the files. 

Thanks for your help. :)

---

### Post by mssever on 2007-04-29
> **kalahari875 said:**
> Sure thing; It is:

```
-rw-r--r-- 1 myuser myuser     0 2007-04-29 08:08 /media/gmail/new file
-rw-r--r-- 1 root  root  27837 2007-04-03 11:05 /media/gmail/oo-maxwell.odt

```The first file I created by right-clicking in the folder and doing Create Document. The second I copied from the default examples folder. Even though the permissions on the second file are set to root, the effect is the same: I can shift+delete but not simply press delete, and I cannot rename the files. 

Thanks for your help. :)

You're saying that both files behave identically? Weird. When you press delete, what happens? Some types of partitions don't seem to support moving files to the trash. I'm not sure about gmailfs, and the I don't have gmailfs set up on the machine I'm using right now to test it.

Can you do filesystem operations from the command line (copy, delete, move)? I'm asking this to determine whether your problem is in Nautilus or the system itself.

I'm about to check out from my hotel room, so as I mentioned in my last post, I probably will be without Internet access for a while. Hopefully someone else can step up and help. Of course, I'll check back once I get back online, but that could be a week or more.

---

### Post by kalahari875 on 2007-04-29
> **mssever said:**
> You're saying that both files behave identically? Weird. When you press delete, what happens? Some types of partitions don't seem to support moving files to the trash. I'm not sure about gmailfs, and the I don't have gmailfs set up on the machine I'm using right now to test it.

Pressing delete produces a dialog box with the following:
```
Error "Invalid parameters" while deleting "/media/gmail/new file". Would you like to continue?
```

> **mssever said:**
> Can you do filesystem operations from the command line (copy, delete, move)? I'm asking this to determine whether your problem is in Nautilus or the system itself.

Renaming produces the following error:
```
mv new\ file My\ document.txt
mv: cannot move `new file' to a subdirectory of itself, `My document.txt'
```

Deleting via rm worked, so the problem there may be Nautilus failing to move the file to the trash. Is there a way to mount the filesystem so that it disables the trash feature?

Copying the file to a new name worked.

Thanks for your help!

---

### Post by mssever on 2007-05-11
> **kalahari875 said:**
> Renaming produces the following error:
```
mv new\ file My\ document.txt
mv: cannot move `new file' to a subdirectory of itself, `My document.txt'
```

That's a weird error. Can you raname from within Nautilus?
> Deleting via rm worked, so the problem there may be Nautilus failing to move the file to the trash. Is there a way to mount the filesystem so that it disables the trash feature?Not that I know of. But I don't use Nautilus a whole lot. I'm more of a command line person.

By the way, I'm back online finally, after being forced to settle for satellite Internet--which is really expensive (almost $50/mo for 512 kbps max upload).

---

### Post by kalahari875 on 2007-05-11
> **mssever said:**
> That's a weird error. Can you raname from within Nautilus?

No, that's what I tried first. I forget the exact error but it's more cryptic than the one mv produces.

> By the way, I'm back online finally, after being forced to settle for satellite Internet--which is really expensive (almost $50/mo for 512 kbps max upload).

Doh! My condolences.

---

### Post by mssever on 2007-05-11
> **kalahari875 said:**
> No, that's what I tried first. I forget the exact error but it's more cryptic than the one mv produces.

Hmmm... I really don't know what to tell you. I don't understand what's causing that error message. Try this and see if you get the same error:
```
cd /path/to/your/gmailfs/partition
touch foo
cp foo bar
mv foo baz
ls
```The point of this is to create brand new empty files and see if we can manipulate them.

---

### Post by kalahari875 on 2007-05-12
> **mssever said:**
> Try this and see if you get the same error:
```
cd /path/to/your/gmailfs/partition
touch foo
cp foo bar
mv foo baz
ls
```The point of this is to create brand new empty files and see if we can manipulate them.

It's strange--now after mounting the console commands work "too quickly" and are not reflected in the Nautilus display of the mounted filesystem. Nautilus takes MUCH longer to create a new file, indicating it's actually going out to Gmail to add the file. The test above did work but I think it wasn't actually using the mount somehow even though I made sure it was mounted first.

---

### Post by mssever on 2007-05-13
> **kalahari875 said:**
> It's strange--now after mounting the console commands work "too quickly" and are not reflected in the Nautilus display of the mounted filesystem. Nautilus takes MUCH longer to create a new file, indicating it's actually going out to Gmail to add the file. The test above did work but I think it wasn't actually using the mount somehow even though I made sure it was mounted first.

If you unmount, verify that the files aren't there, then remount, you can see if the commands work. Since my test was merely touching a file, it can be expected to be faster than normal. The touch command merely updates the last modified time (creating an empty file if no such file exists).

---

### Post by aspora.isernia on 2007-06-14
Hi to all and thanks for this HOWTO.
I've just finished the configuration and all seems to work, but... I have some doubts related to the speed of this filesystem... It seems that the performances of the whole system are affected by this new filesystem: the auto-complete function of the bash seems much slower than before. It's only my truble, or someone else is experiencing this performance slow-down?
Moreover, when I try to umount the filesystem, Device or resource busy error appears... Any idea?
Many thanks!!

---

### Post by durand on 2007-06-14
Well, for a start, everything is online on the google servers so thats why its slow. Think of it as a page in a website. It takes sometime to load depending on your internet's speed. I'm not sure about the other error though. However, I think you can just ignore it as you don't need to unmount this f/s. Just make sure that it's finished uploading everything.

---

### Post by Anphisbena on 2007-10-22
How do I create a fsname?
 I tried to put a any password and appeared the following error:



mchim:/home/agatha# mount -t gmailfs none /mnt/google -o username=******@gmai
l.com,password=*******,fsname=*******
Ignored option :rw
HTTP Error 400: Bad Request
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/gmailfs.py", line 193, in _sendMessage
    if ga.sendMessage(gmsg):
  File "/usr/lib/python2.4/site-packages/libgmail.py", line 531, in sendMessage
    params = {U_VIEW: [U_SENDMAIL_VIEW, U_SAVEDRAFT_VIEW][asDraft],
  File "/usr/lib/python2.4/site-packages/libgmail.py", line 511, in _getActionTo
ken
    at = self._cookieJar._cookies[ACTION_TOKEN_COOKIE]
KeyError: 'GMAIL_AT'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/gmailfs.py", line 193, in _sendMessage
    if ga.sendMessage(gmsg):
  File "/usr/lib/python2.4/site-packages/libgmail.py", line 531, in sendMessage
    params = {U_VIEW: [U_SENDMAIL_VIEW, U_SAVEDRAFT_VIEW][asDraft],
  File "/usr/lib/python2.4/site-packages/libgmail.py", line 511, in _getActionTo
ken
    at = self._cookieJar._cookies[ACTION_TOKEN_COOKIE]
KeyError: 'GMAIL_AT'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/gmailfs.py", line 193, in _sendMessage
    if ga.sendMessage(gmsg):
  File "/usr/lib/python2.4/site-packages/libgmail.py", line 531, in sendMessage
    params = {U_VIEW: [U_SENDMAIL_VIEW, U_SAVEDRAFT_VIEW][asDraft],
  File "/usr/lib/python2.4/site-packages/libgmail.py", line 511, in _getActionTo
ken
    at = self._cookieJar._cookies[ACTION_TOKEN_COOKIE]
KeyError: 'GMAIL_AT'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/gmailfs.py", line 193, in _sendMessage
    if ga.sendMessage(gmsg):
  File "/usr/lib/python2.4/site-packages/libgmail.py", line 531, in sendMessage
    params = {U_VIEW: [U_SENDMAIL_VIEW, U_SAVEDRAFT_VIEW][asDraft],
  File "/usr/lib/python2.4/site-packages/libgmail.py", line 511, in _getActionTo
ken
    at = self._cookieJar._cookies[ACTION_TOKEN_COOKIE]
KeyError: 'GMAIL_AT'
.
.

---

### Post by Pixman on 2007-11-11
Mh,  I get this: 
> 
 sudo mount dimethyltryptamin/
Ignored option :rw
Ignored option :noauto
HTTP Error 400: Bad Request

Is gmailfs ou tof date?

---

### Post by daller on 2007-11-14
I get this:

```

Ignored option :rw
HTTP Error 400: Bad Request


```

What can I do to fix it?

---

### Post by soichih on 2007-12-14
When I try to mount the filesystem, I get following error message

soichi@shayas1006:/mnt$ sudo mount /mnt/gdrive/
Ignored option :rw
HTTP Error 400: Bad Request

What does this mean?

---

