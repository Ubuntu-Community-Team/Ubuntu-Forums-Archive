---
title: "I cannot Copy files from downloads to my other volume"
date: 2019-12-31
forum: New to Ubuntu
---

### Post by mzaid000 on 2019-12-31
[ATTACH=CONFIG]284719[/ATTACH]

The above error is received when I try to copy a file to my other volume which is NTFS/exFAT

---

### Post by TheFu on 2019-12-31
I have 2 guesses at this point.
a) permissions issues on either the source, target or both.
b) snap confinement limitations for the tool doing the copy.  bash doesn't have this, yet, so using a shell environment will work.

Please show the exact command used and copy/paste TEXT, not images.
Permissions for both the source and target are needed too.  Show them using **ls -la /path/to/directory** for both the source and target directories.

Please wrap the command and output in "_code tags_" so it appears in these forums just like it does in a terminal. Alignment matters.  Too hard to read otherwise.  Why is text better?  I can correct errors quickly by select/paste. Can't do that when images are posted.

The easier you make it for people to help, the more likely you'll get helpful answers.

---

### Post by mzaid000 on 2019-12-31
Output of **ls -la /Downloads**  | Source Directory
ls: cannot access '/Downloads': No such file or directory
Output of  **ls -la /media/mzaid/40680CD1680CC79C **| Target Directory

total 3134276
drwxrwxrwx  1 mzaid mzaid      16384 Dec 24 14:08  .
drwxr-x---+ 3 root  root        4096 Dec 31 16:38  ..
drwxrwxrwx  1 mzaid mzaid       4096 Dec 13 14:16  6th
-rwxrwxrwx  2 mzaid mzaid 1092971088 Dec 18 19:24 '6 Underground 2019 on lookmovie.ag in FullHD for free.ts'
drwxrwxrwx  1 mzaid mzaid       8192 Dec 24 13:20  Documents
drwxrwxrwx  1 mzaid mzaid          0 Jul  4 13:27 'EaseUS Data Recovery Wizard 11.9.0 Full Crack & Keygen'
-rwxrwxrwx  2 mzaid mzaid   33524634 Mar 12  2019 'EaseUS Data Recovery Wizard 11.9.0 Full Crack & Keygen.rar'
drwxrwxrwx  1 mzaid mzaid       4096 Nov 25 11:11 'English Course'
drwxrwxrwx  1 mzaid mzaid       4096 Jan 26  2019  InnovCre8
drwxrwxrwx  1 mzaid mzaid       4096 Oct  9 14:11 'Lg G4'
drwxrwxrwx  1 mzaid mzaid       4096 Jun 25  2019  MATLAB
drwxrwxrwx  1 mzaid mzaid      16384 Dec 24 12:42  NLP
drwxrwxrwx  1 mzaid mzaid       4096 Dec 24 12:45  Private
drwxrwxrwx  1 mzaid mzaid          0 Dec 24 14:08  Programs
drwxrwxrwx  1 mzaid mzaid       4096 Nov 16 12:17 '$RECYCLE.BIN'
drwxrwxrwx  1 mzaid mzaid       4096 May 27  2019 'System Volume Information'
-rwxrwxrwx  2 mzaid mzaid 2082816000 Dec 24 13:38  ubuntu-18.04.3-desktop-amd64.iso
drwxrwxrwx  1 mzaid mzaid      49152 Oct 10 21:03  UET
drwxrwxrwx  1 mzaid mzaid          0 Jul 27 14:19  VS
drwxrwxrwx  1 mzaid mzaid      49152 Sep  7 10:11  Wallpapers
drwxrwxrwx  1 mzaid mzaid       8192 Aug  9 19:02  WEB

---

### Post by mzaid000 on 2019-12-31
output of **ls**:
Desktop                                 hs_err_pid2475.log     Public
Documents                               hs_err_pid2488.log     snap
Downloads                               hs_err_pid2520.log     Task

**mzaid@Titan:~/Downloads$** **ls**
Application.pdf  Compressed  Core.pdf  Documents  Music  Programs  Pro.pdf  Video  Webots


output of [B]sudo cp Downloads/Core.pdf /media/mzaid/40680CD1680CC79C/Core.pdf
[/B]cp: cannot create regular file '/media/mzaid/40680CD1680CC79C/Core.pdf': No such file or directory

---

### Post by The Cog on 2019-12-31
Looking at your last post, you are **already in** the Downloads directory (the prompt says so, and you did ls, not ls Downloads). 
So you don't need to say Downloads again - the file is not in Downloads/Downloads.

As The Fu says, Please show the exact command used and copy/paste TEXT. If you had copied the prompt and the copy command, we could be more sure what you are doing- as it is I am having to guess what your current directory was and what the exact command you typed was. 

Also as The Fu says, please use code tags when posting copied code (the # button in the editor's Go Advanced panel).

---

### Post by yancek on 2019-12-31
If you are in your user Downloads directory where the Core.pdf file you want to copy is, just do:

cp Core.pdf  [B] /media/mzaid/40680CD1680CC79C/

[/B]Don't put Core.pdf at the end of the destination directory, if that fails with a permissions issue then use sudo or sudo su.  That is the reason you get the error you posted in post 4.
The command you used in post 4 would work to copy Core.pdf to that destination if there was a Core.pdf directory there but there isn't.

---

### Post by TheFu on 2019-12-31
Try:
```
cp ~/Downloads/Core.pdf /media/mzaid/40680CD1680CC79C/
```

Overuse of sudo can cause issues.  Above and below, I've wrapped it in code tags.

When I run that command:
```
thefu@posc:/tmp$ cp ~/Downloads/Core.pdf /media/mzaid/40680CD1680CC79C/
cp: cannot stat '/home/jp/Downloads/Core.pdf': No such file or directory
```
See how I include the full prompt with the userid, hostname, current working directory when select/paste everything?  This provides all sorts of extra information to us, especially when permissions are the likely issue.

BTW, wouldn't hurt to brush up on the differences between a _relative path_ and an _absolute path_.
~/Documents  is the same as /home/thefu/Documents is the same as $HOME/Documents for a userid "thefu".
If thefu is in $HOME, then Documents/ is the same too, but if thefu userid is in any other directory, it won't work.

If a path starts with a /, then it is from the system root directory and by definition is an *absolute path*.
All other paths are relative to the CWD - current working directory.

---

### Post by mzaid000 on 2020-01-01
It says read only file system
mzaid@Titan:~$ cp Core.pdf  /media/mzaid/40680CD1680CC79C/
cp: cannot create regular file '/media/mzaid/40680CD1680CC79C/Core.pdf': Read-only file system

---

### Post by The Cog on 2020-01-01
As I understand it, the most common reason for NTFS being read-only in Linux is that it is marked unclean. See this post for an idea what to do in Linux, or better, check the disk with Windows.
[https://ubuntuforums.org/showthread.php?t=2379710](https://ubuntuforums.org/showthread.php?t=2379710)

---

### Post by Impavidus on 2020-01-01
> **mzaid000 said:**
> 
output of [B]sudo cp Downloads/Core.pdf /media/mzaid/40680CD1680CC79C/Core.pdf
[/B]cp: cannot create regular file '/media/mzaid/40680CD1680CC79C/Core.pdf': No such file or directory
This error indicates that the directory /media/mzaid/40680CD1680CC79C/ does not exist. Whether the file exists doesn't matter. If it doesn't, it's created; if it does, it's overwritten. But cp won't create the directory for you. If you want the copy to have the same filename as the original, you can omit the name in the destination, but giving it anyway won't harm.

The directory is created by the file manager when you use that to mount the Windows partition and is removed when you use the file manager to unmount the Windows partition. So this error tells us that the Windows partition wasn't mounted when you tried that command.

> **mzaid000 said:**
> It says read only file system
mzaid@Titan:~$ cp Core.pdf  /media/mzaid/40680CD1680CC79C/
cp: cannot create regular file '/media/mzaid/40680CD1680CC79C/Core.pdf': Read-only file system

This means that the Windows partition is mounted read-only. This means it was either mounted explicitly as read-only or was mounted so because it's dirty and Ubuntu doesn't want to write to a dirty Windows filesystem. It could confuse Windows and the changes would probably be lost.

> **TheFu said:**
> 
If a path starts with a /, then it is from the system root directory and by definition is an *absolute path*.
All other paths are relative to the CWD - current working directory.
Note that any path that starts with something that's shorthand for an absolute path is an absolute path too. The / at the start may not always be visible. $HOME and ~ are the absolute path to the user's home directory, ~username is the absolute path to the home directory of user username.

---

### Post by TheFu on 2020-01-01
> **Impavidus said:**
>  
Note that any path that starts with something that's shorthand for an absolute path is an absolute path too. The / at the start may not always be visible. $HOME and ~ are the absolute path to the user's home directory, ~username is the absolute path to the home directory of user username.
Thanks for the clearer additions. I worded it incorrectly trying to keep it simple. I failed. 

[LIST]
[*]~/  .... gets expanded from the passwd entry (getent passwd $LOGNAME) for the userid HOME directory setting.
[*]~thefu/  .... gets expanded from the passwd entry (getent passwd thefu) for the userid HOME directory setting. Any username on the system can be used.   ~root would expand to root's home, usually /root/.
[*]$HOME/  .... gets expanded from the environment variable $HOME (set at login).  Some commands can change this value or it can be manually modified.
[/LIST]

I've added trailing / characters above to clearly show directories.   **ls -F** will do this too.

---

