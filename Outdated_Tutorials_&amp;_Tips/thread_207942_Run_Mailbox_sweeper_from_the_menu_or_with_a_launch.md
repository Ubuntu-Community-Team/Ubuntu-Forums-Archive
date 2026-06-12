---
title: "Run Mailbox sweeper from the menu or with a launcher"
date: 2006-07-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Jasper Houtman on 2006-07-02
[Mailbox sweeper]("http://sourceforge.net/projects/mailbox-sweeper/") is a Java based graphical spam filtering program.
The program can't normally be started using a (menu) launcher because it needs to be started in the terminal in it's own directory (it can't find it's profile.dat file if it's started outside it's directory).

This can be fixed by creating a .sh file (script) to go to the mailbox sweeper directory before running it.

First open up your text editor (gedit, etc) and type:

```
cd /directory/directory/Mailboxsweeper
java -jar MailboxSweeper.jar
```

Substituting /directory/directory/mailboxsweeper for the directory you installed the mailbox sweeper program in.

Now save the file as mailboxsweeper.sh

now create a new launcher or menu item
Select browse and select the mailboxsweeper.sh file
and finally set it to run in the terminal
Save the item and now you can start the program from your menu, panel or launcher.

---

