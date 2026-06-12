---
title: "rsync doubt"
date: 2019-11-21
forum: New to Ubuntu
---

### Post by giobaxx on 2019-11-21
Time to to time we use rsync to tranfert home folder of the user from a old to a new workstation like this
***rsync -avz /home/user   user@workstation:/home/user***

*If i need to update this backup with the only changed file/folder i need to run the same comand used to backup or i need to use the option -u*
******
[I][I][I]**rsync -avz[COLOR=#0000cd]u[/COLOR] /home/user user@workstation:/home/user**
[/I][/I][/I]
[I][I][I]

Tanks GIO[/I][/I][/I]

---

### Post by SeijiSensei on 2019-11-21
"rsync -av" always transfers just the files that are different between the directories. What exactly is the problem?

---

### Post by oldrocker99 on 2019-11-21
Personally, I use grsync, which, although the progress bar is useless, because it always uses the proper switches. Never had a problem at all.

---

### Post by giobaxx on 2019-11-21
I though that just running ***rsync -avz  source destination ***  was copying only the new/modified files from the *source dir* to the *destination dir*. So what do the *-u *switch?

---

### Post by TheFu on 2019-11-21
rsync doesn't remove any files that don't exist in the source tree, unless that is specifically requested.  There is a --delete option.  There are ways to delete-before and delete-after the rsync goes. Depends on what you need.

I use -avz for network transfers using client/server methods.  I don't use the 'z' - compression - for transfers that are local or appear to be local.  rsync behaves differently for client/server tasks than it does for local tasks - local includes tasks that use nfs.

---

### Post by SeijiSensei on 2019-11-21
I never use that option, but a quick scan of documentation online suggests that -u pays attention to time stamps on the receiver. It appears to only replace files whose timestamp on the sender is newer than on the receiver. From "man rsync"

> 
       -u, --update
              This forces rsync to skip any files which exist on the destination and have a  modified  time
              that is newer than the source file.  (If an existing destination file has a modification time
              equal to the source file&#8217;s, it will be updated if the sizes are different.)


My reading of this is that rsync will ignore files of different sizes if the receiver's version has a newer timestamp.

---

### Post by giobaxx on 2019-11-21
Normaly we use this command to trasfer the home folder of a user to a new workstation via network. Sometimes it happend that this replacement of the workstation is delayed by days sometimes weeks so before to swap the workstation we need to run an additional rsync to copy only the modified file/folder from the source to the destination. to do that i use the same commmand used for the first rsync. Then reading about the -u switch made me a bit on confusion

---

### Post by Skaperen on 2019-11-21
the -u option could be useful if the user has already begun using the workstation and has possibly created new files.  the 2 machines should be in close time sync for this to work correctly.  if there is no chance of newer files on the target workstation then you don't need -u.  i can't recall ever needing -u.

---

### Post by giobaxx on 2019-11-22
Tanks to Everyone! Now is clear

---

