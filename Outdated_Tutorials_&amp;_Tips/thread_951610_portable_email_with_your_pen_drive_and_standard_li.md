---
title: "portable email with your pen drive and standard linux thunderbird"
date: 2008-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by blesbok on 2008-10-18
The aim: Portable email where a box with internet connection is available for sending and receiving at a separate location.

Start by opening a shell.  If your reaction's not something like "A what?" or "But how?" skip this paragraph and the following screenshot.  For good measure, we'll put konsole on the panel too. Steps 1) Right-click anywhere on the panel (bottom white in screenshot.) 2) Select (or hover on) Add Application to panel. 3) Select System. 4) Select Konsole.  Konsole is now on your panel.  Click it and the command line will be ready to do your bidding.

[http://ubuntuforums.org/attachment.php?attachmentid=88740&stc=1&d=1224340873](http://ubuntuforums.org/attachment.php?attachmentid=88740&stc=1&d=1224340873)

First locate your inbox for thunderbird in your home directory:  cd (puts you in your home directory) Now look for the relevant inbox:

find ~ -name Inbox

You should get just a few results.  Look for those in a directory .mozilla-thunderbird; you use the one which contains a subdirectory, Local Folders.  Your path to it will be something like: /home/blesbok/.mozilla-thunderbird/ohdgx5ou.default/Mail/Local Folders/Inbox

This Inbox is a file written in C which can have more contents like its own appended to it; that's the secret.  Now let's write some scripts to do just that!

Let's assume you have email access at a friend; I'll refer to the locations (boxes) FRIEND and HOME.

Set up a thunderbird account at FRIEND resembling your HOME account.  There, you'll download your email and copy it with an instruction like cp /home/goodfriend/.mozilla-thunderbird/ohdgx5ou.default/Mail/Local\ Folders/Inbox /media/disk/email

This copies your email into a folder (preexisting) on your pen drive called email.
That's a quick and easy way, since you're probably in a hurry to catch up on your email.

But once back, you can do the following at leisure at HOME.  Write a shell script to write the emails into your inbox.  I suggest using vi for this.  If you don't know vi, give the shell command vimtutor and take the course. (Note: if you struggle to do things like navigate using arrow keys in insert mode, your shell environment's buggy and you should substitue 'vi' with 'vim'.) Do the following in your shell (mkdir programs <ENTER> cd programs <ENTER> mkdir shell <ENTER> cd shell <ENTER> vi thmail <ENTER>)

[http://ubuntuforums.org/attachment.php?attachmentid=88741&stc=1&d=1224340873](http://ubuntuforums.org/attachment.php?attachmentid=88741&stc=1&d=1224340873)

After the vi command and ENTER, you'll see this:

[http://ubuntuforums.org/attachment.php?attachmentid=88742&stc=1&d=1224340873](http://ubuntuforums.org/attachment.php?attachmentid=88742&stc=1&d=1224340873)

Now we're ready to write a shell script called thmail.  Hit i for insert mode and write this script:

#!/bin/bash
# this script moves the newly downloaded email from your pen drive to your email client
# the contents of the file in the first path are appended to the second file
cat /media/disk/email/Inbox >> /home/blesbok/.mozilla-thunderbird/ohdgx5ou.default/Mail/Local\ Folders/Inbox
echo "New mail is in Inbox. You may close this shell while Thunderbird opens."
# open the mail client as session independent of the shell opening it
setsid thunderbird

A line can be added to delete the Inbox on the pen drive too.  Remember to mount the pen drive before running the script.
Oh, there's one more thing we need to run the script.  Give the script execute permissions:

In your script's directory: (cd /home/blesbok/programs/shell)
chmod 755 thmail
./thmail

The latter command is to run your script. Look good? Let's make a shortcut to change to the shell script directory with the command cdsh:

cd (puts you in your home directory)
vi .bashrc

under the line: 
#alias l='ls -CF'
add:
alias cdsh='cd /home/blesbok/programs/shell'
alias custom='vi /home/blesbok.bashrc'

The second line will make it easier to create future custom commands.  ;)

That's about it for HOME.  At computer FRIEND, write a shell script to do this: cp /home/goodfriend/.mozilla-thunderbird/ohdgx5ou.default/Mail/Local\ Folders/Inbox /media/disk/email

Edit FRIEND'S .bashrc on the applicable user to run your script with ease.  Set Thunderbird to open without first going online. Go to Edit >> Account Settings >> Server Settings: uncheck the two "Check for new messages" boxes. First always delete the emails already in the Inbox (the ones you have) before downloading new emails.

[http://ubuntuforums.org/attachment.php?attachmentid=88743&stc=1&d=1224340873](http://ubuntuforums.org/attachment.php?attachmentid=88743&stc=1&d=1224340873)

Hopefully this tutorial contains enough info to get you going.  Just as we've facilitated the moving of Inbox files from FRIEND to HOME, similar things can be done regarding Sentmail and Outbox.

---

