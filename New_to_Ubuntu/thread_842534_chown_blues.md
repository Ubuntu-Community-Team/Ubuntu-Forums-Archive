---
title: "chown blues"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by larryfroot on 2008-06-27
Hello people,

Welcome to my chown blues.

I decided to do a full back up of my hardy box onto media. All well and good. I then install hardy on my laptop. All well and good. I copy the files from the removable media onto the laptop hard drive. All well and good. 

Obviously the permissions need to be sorted out, so for every folder that I copied over, once on my laptop I ran 

sudo chown -R larryfroot:larryfroot foldername. 

As all this was happening from my home directory there was no need for paths in the command. which I could trust to work recursively within each folder freeing them for yours truly to write to, move, edit as needed. The files within the folders were chowned to larryfroot as were the folders. HOWEVER The folders were set to access files and that was it. So they are pretty immobile, just sitting there in a Stalinistic manner. I have gone into their permissions tab on a right click and tried to set read and write but the folders are having none of it. They just sit their proudly showing me their little padlocks. Also the files inside them were only read-only. That can be changed through going through the lot of them, right clicking and going into the permissions tab to change read only to read and write. 

I can only delete folders with a (very careful) sudo rm -rv which isn't much fun. I like to play safe and stick 'em in the trash for a while before nuking them.

So which part of sudo chown -R larryfroot:larryfroot /path/to/folder do I have to ammend in order to chown the permissions on all folders in the folder referenced to jettison those padlocks and return full ownership to larryfroot, and how do I set up the command so the permissions for the files within those folders go to read and write, not just read only? 

BTW I have man chown'd in the terminal and tried to understand the information. But obviously its in the nature of a man entry to be as concise as possible, which left me a bit behind, to be honest. 

I would really appreciate help on this one as I need to restructure my folder hierarchy and would like to assume all my files have the same permissions set as per my desktop box. Also I am as curious as an interested cat as to how its done proper! Thanks!

---

### Post by svk on 2008-06-27
The owner of a file and the permissions of a file are two very distinct things.

The chown command you ran should take care of the ownership issues.  Unless there's something I'm overlooking, your command should make Linux agree with you that your files are indeed yours.

But now the permissions: the command you want is chmod.  It allows you to change the permissions for files and directories.

In the terminal, are you able to use "cd" to go inside any of the directories in your home folder?  Does it say "Permission denied"?  Are you able to use "cat" to print the contents of any text files?

In order to help you diagnose this, run the command "ls -l" in the terminal while you are in your home directory and show us what is says.

---

### Post by The Cog on 2008-06-27
svk is right. chmod is used to change the permissions of files and folders.

But you should be able to do that with the GUI pemissions dialog - I don't understand why that doesn't work. You could try this from your home directory:
```
find . -type d -exec chmod 750 {} \;
```
which should find every directory and set it to full access to the owner, read access to the group.

---

### Post by larryfroot on 2008-06-27
Thank you! The bright sun of chmod arises, casting its light upon the carnage wrought by frooty ignorance! A whole new epoch of overblown drama queen penguin love breaches the walls of the dark tower of etc etc.

But really. thanks!

---

### Post by svk on 2008-06-27
Haha, I love your writing.

---

### Post by crashcoredump on 2008-06-27
> Thank you! The bright sun of chmod arises, casting its light upon the carnage wrought by frooty ignorance! A whole new epoch of overblown drama queen penguin love breaches the walls of the dark tower of etc etc.


Gracefully expressed indeed:)

---

### Post by mcduck on 2008-06-28
By the way, the next time you make a backup you might want to make it by compressing all your stuff into a tar.gz package.

This way all your permissions will stay, even when you burn the backup to a disk or put it into a removable drive with filesystem that doesn't support Linux-style permissions and ownerships..

---

### Post by larryfroot on 2008-06-28
I have dabbled around the edges of learning linux admin and cli stuff for far too long. It would be such a sound investment in time and effort to put aside Mr Shnoogles and basically get up to speed. my diary is coming out and dates are going in. I have also started to save handy little commands, scripts and posts as text files...I will be including the invaluable info received in this thread as part of that. 

I have been using Ubuntu for a few months now, and the community has impressed me as much as the software. I know that often I try to help out whenever I can because Ubuntu is free and the efforts of others inspire efforts of oneself. Part of the reason why I am going to learn to tell my cli from my grep from my chmod from that funny little plastic object I left by the phone yesterday which has now disappeared....

---

### Post by svk on 2008-06-28
Ooh, saving little commands in text files is definitely useful.  I started my own collection in a folder called "snippets", but looks like I've been slacking... there are only two things in there, and they're not all that terribly useful.

#1. convert-stdin-to-ascii-codes.txt:

```
serg@bijou:/data/snippets$ HELLO | od -c -t u1 -
0000000   H   E   L   L   O  \n
         72  69  76  76  79  10
0000006

```#2. combine-multiple-pdf-files-into-one.txt:

```
serg@bijou:/data/snippets$ gs -dNOPAUSE -sDEVICE=pdfwrite -sOUTPUTFILE=combinedpdf.pdf -dBATCH 1.pdf 2.pdf 3.pdf
```And yes, the community is definitely a large part of what makes Ubuntu great.  Without it, I would, no doubt, still be on Windows.

Oh, and yes, put away Mr. Shnoogles.  In fact, here's a challenge: try living without a desktop manager for an entire week.  Do not allow yourself to leave the terminal.  Try browsing the web with lynx.  Try installing stuff using synaptic, listening to music with cdplay or mpg123 or xmms.  Try editing stuff with nano, emacs, or vim.  Try printing stuff with lpr.

Comfort in using the terminal is an essential skill, and in a masochistic sort of way, kinda fun, too.

---

