---
title: "Shell Script to Move a file from one location to another and create folder"
date: 2013-10-14
forum: Programming Talk
---

### Post by Michel_Laporte on 2013-10-14
Hi,

I'm new to this forum but been using Ubuntu for a while.

I'm in a bit of a mix up. I'm not totally new to Ubuntu but compared to you guys i'm sure i'm an ultimate "noob".
 
I'm not looking for help merely a point in the right direction.

**At work, i have been asked to create:**
[I]
A script that will take a PDFs from a folder, move it onto another folder on the same server. (Later in the development we will look at putting it in a folder on another server by mounting it from start)
It will create a folder (Named the same as the file name) and put the file in that folder. Then delete the file from the source. (As it's moved im sure there isn't a need for that).
[/I]
The script will be a CRON job which will run lets say every 5 minutes.

Could someone point me in the right direction or help me out in terms of what i need to do to start this?

So far i've tried mounting a folder from another ubuntu server without any luck by following these guides : [HERE]("http://askubuntu.com/questions/282812/how-to-mount-ubuntu-share-on-other-ubuntu-machine") And [HERE]("http://petio.org/tools/cifs.html")

However, i had decided to try and create the script with 2 local folder on the same server instead of mounting from a different server which i will address later.

My setup is:

Proxmox 2.3

Server 1 : 12.04 LTS - 10.0.0.4 
Server 2 : 12.04LTS - 10.0.0.5 (Script will run from here) to copy over to server 1.

Both have access to internet through 2nd ethernet interface.

I only just started experimenting with Ubuntu terminal about a month ago so i may not understand a whole lot of things.

Thanks for any help,
Mike

---

### Post by Lars Noodén on 2013-10-14
Welcome to the forums.

The utility "rename" can also move files to another directory.  It uses perl regular expressions to match.  The example below uses s/// to substitute the old name for the new name.  The hashes (#) are used as dividers instead of the usual slashes (/) to make it easier to work with and read the paths. 

```

rename 's#^(.*.pdf)$#./Y/$1#' *.pdf

```

Also note that **-n** does a dry run without actually changing anything.  That allows you to test your regular expression to make sure it works the way you want it to.

Another thing to consider might be to not use cron but instead use inotify.  There is a tool there, incron, which works a bit like cron in that it launches scripts.  The difference is that it does not lauch them at a particular time but rather when a watched file or directory changes.  So you could have it watch for new or changed PDFs and then use rename to move them.

---

### Post by Michel_Laporte on 2013-10-14
Thanks for the reply!

iNotify looks better than as we do want it to run whenever there are changes.

However, i am a bit confused on the code you wrote. (I apologize for my stupidity but i am still only just getting used to it).

Will that basically rename the pdf file into a 'nicer' way for Ubuntu to read?

For the script, i been reading the forums and come across something like:
[I]
#!/bin/bash


source_dir= #The source of the PDF

dest_dir= #Where i want to move it to


cp -r "$source_dir/* $dest_dir/"
[/I]
Does that look okay?

If so, how would i use iNotify on that? + Creating the folder based on the filename.

---

### Post by steeldriver on 2013-10-14
I think you need to take a step back and clarify your requirements - for example

[INDENT]1. will the source .pdf files all be in a single folder, or can they be inside subfolders?

2. will there be other filetypes in the source folder or only .pdfs?

3. what should the script do about name conflicts i.e. if the destination folder already contains a *myfile.pdf*, should the script overwrite it? or rename it? or rename the old file? or abort?

4. what should happen if the destination folder is not available (possibly not an issue with the local destination, but definitely something to think about if it is a mounted remote server)

5. you initially wanted to move files but now you are talking about using cp - maybe rsync would be a better option?
[/INDENT]

---

### Post by Lars Noodén on 2013-10-14
> **Michel_Laporte said:**
> ... Creating the folder based on the filename.

Can you give a few examples of filenames?

---

### Post by Michel_Laporte on 2013-10-14
Hi Steeldriver:



[COLOR=#000000]1. will the source .pdf files all be in a single folder, or can they be inside subfolders?
[/COLOR]**The source is from a single folder only.**

[COLOR=#000000]2. will there be other filetypes in the source folder or only .pdfs?
[/COLOR]**No, only PDF's as it's files being scanned that's going to the only folder**

[COLOR=#000000]3. what should the script do about name conflicts i.e. if the destination folder already contains a [/COLOR][I]myfile.pdf, should the script overwrite it? or rename it? or rename the old file? or abort?
[/I][B][I]The printer gives unique ID's to each filename (I think by assigning a random number at the end of each file) however, if the file is moved the number could be generated again which im sure i can't allow to happen. So if a conflict a rename would be the way to go
[/I][/B][I]
4. what should happen if the destination folder is not available (possibly not an issue with the local destination, but definitely something to think about if it is a mounted remote server)
[/I][I][B]If destination folder is unavailable im guessing we should just end the task. Does Ubuntu have a way of alerting a sysadmin of any faults? Such as an email or system message?


[/B][SIZE=2]@Lard Nodeen
[/SIZE][/I][COLOR=#000000][I]... Creating the folder based on the filename.
[/I][/COLOR][SIZE=3]*Example file name*[/SIZE]*** : ***SKMBT_C28013070218080



I hope this helps. :)

Mike

---

### Post by Vaphell on 2013-10-15
so which part of the filename is supposed to go to the dir name? If you want automation you need to provide exact rules governing it.

SKMBT_C28013070218080.pdf => SKMBT_C28013070218080/SKMBT_C28013070218080.pdf ?

---

### Post by Michel_Laporte on 2013-10-15
[COLOR=#000000]Vaphell[/COLOR]
[COLOR=#000000][INDENT]**Re: Shell Script to Move a file from one location to another and create folder**
so which part of the filename is supposed to go to the dir name? If you want automation you need to provide exact rules governing it.

SKMBT_C28013070218080.pdf => SKMBT_C28013070218080/SKMBT_C28013070218080.pdf ?

Hi Vaphell,

That's correct. I want the whole filename to be the file name and the PDF moved into it like you wrote up there ^^.

So

123.pdf > 123/123.pdf
456.pdf > 456/456.pdf

Etc Etc[/INDENT][/COLOR]

---

### Post by Lars Noodén on 2013-10-15
> **Michel_Laporte said:**
> [indent]
123.pdf > 123/123.pdf
456.pdf > 456/456.pdf

Etc Etc[/INDENT]

You don't need any custom scripts for that, "rename" is up to the task.

```

rename -n 's#^(.*).pdf$#./$1/$1.pdf#' *.pdf

```

It will handle any regex that will fit in a perl substitution operator : **s///**

PS. Check your spelling in post #6 ;)

---

### Post by Lars Noodén on 2013-10-15
Forget the "rename" suggestion, it won't create the missing directories for you.  My mistake.

---

### Post by Michel_Laporte on 2013-10-15
Im working on test folders at the moment.#

All the files in the folder has a name along the lines of : [COLOR=#000000]SKMBT_C28013070218080.pdf (With different numbers at the end)[/COLOR]

This is as far as i've gotten:

for file in *.pdf; do
  mkdir "/home/user/scannedpdf/${file%.*}"
  mv "/home/user/pdf/*" "/home/user/scannedpdf/${file}"
done


exit 0

Im sorry im not fully confident with Bash im still new to it.

This command works to an extent where it moved the files to the /scannedpdfs folder i created. 

And sorry Lars i don't understand what you mean. A lot of things still sound very new to me. I sincerely apologize for this.

Mike

---

### Post by Michel_Laporte on 2013-10-15
Okay,

I've managed to come up with one that works!!!

[B]#!/bin/bash

for i in *.pdf;do mkdir "/home/${i/./#}";mv $i "/home/${i/./#}";done[/B]


This basically runs the script from the source directory and copies it over to another directory.

Now, how would i extend it to lets say run from a different folder? Do i merely add:



[B]for i in /folder/where/i/hold/the/files*.pdf;do mkdir "/home/${i/./#}";mv $i "/home/${i/./#}";done
[/B]

Then how do would i write an if statement based on that to say if there isn't a .pdf file, to do nothing. (Im going to use a CRON job rather than inotify as i can't find much info on how to use it).

Thanks

---

### Post by SeijiSensei on 2013-10-15
If you want to move the file to a remote machine, you have a couple of alternatives.

1)  Export the target directory with [NFS]("https://help.ubuntu.com/lts/serverguide/network-file-system.html") and mount it on the machine where the PDFs reside.  Then copying to the remote directory would use the same syntax as before with a different path.  For instance, if you mounted the remote server's destination directory to /mnt/PDF, you would use that path rather than /home above.

2)  Run [rsync]("https://help.ubuntu.com/community/rsync") to transfer the files.  It will use SSH as the transport.  You would need to use the [public-key method]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") so no passwords are involved.

3)  Use [scp]("https://help.ubuntu.com/community/SSH/TransferFiles") to transfer the files.  Same restrictions as rsync.

---

### Post by Michel_Laporte on 2013-10-15
> **SeijiSensei said:**
> If you want to move the file to a remote machine, you have a couple of alternatives.

1)  Export the target directory with [NFS]("https://help.ubuntu.com/lts/serverguide/network-file-system.html") and mount it on the machine where the PDFs reside.  Then copying to the remote directory would use the same syntax as before with a different path.  For instance, if you mounted the remote server's destination directory to /mnt/PDF, you would use that path rather than /home above.

2)  Run [rsync]("https://help.ubuntu.com/community/rsync") to transfer the files.  It will use SSH as the transport.  You would need to use the [public-key method]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") so no passwords are involved.

3)  Use [scp]("https://help.ubuntu.com/community/SSH/TransferFiles") to transfer the files.  Same restrictions as rsync.

I think im going to go with a NFS mount. Seems simpler. Thanks :)

Just need help on implementing:

[LIST]
[*]iNotifty
[*]If no iNotify, how to edit the code as a "if exist" job for files in the folder.
[/LIST]

---

### Post by Lars Noodén on 2013-10-15
To use inotify install the package "incron" and then at least glance at the manual page for [incrontab](http://manpages.ubuntu.com/manpages/raring/en/man5/incrontab.5.html).  That's where all the details are covered.

You'll need to use "sudo" to add your account to /etc/incron.allow before editing your incrontab.  Then launch "incrontab -e" and add the directory to be watched, followed by the event to watch for (e.g. IN_ALL_EVENTS), and lastly the script to be launch in case of the preceding event.  See "man 5 incrontab" for all the events available for monitoring.

Note you probably won't be able to run a bare [mv](http://manpages.ubuntu.com/manpages/raring/en/man1/mv.1posix.html) from inside the incrontab.  You will instead have to wrap it in a script, even if it is the only action in that script, and then call that script from incrontab.

---

### Post by Michel_Laporte on 2013-10-17
Thanks man! 

Will have a look and revert back

---

