---
title: "Can't create shared folder"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by sophie2cu2 on 2012-07-24
Hi everyone,

As part of a longer / bigger project, I've been trying to set up a shared folder (the one with the two little arrows over the top). So, I went through all the steps, including:
[INDENT]"allow others to create and delete files in this folder" .
[/INDENT]I also click on "add permissions automatically" when I get:
[INDENT]Nautilus needs to add some permissions to your folder "Public" in order to share it
The folder "Public" needs the following extra permissions for sharing to work:
  - write permission by others
Do you want Nautilus to add these permissions to the folder automatically?
[/INDENT]But when I click on "create share" I get this:
[INDENT]'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. No such user.
[/INDENT]Double-dutch to me.

Anybody know what this is and what I should do about it?

Please help,
Sophie :confused:

---

### Post by Bufeu on 2012-07-24
Try run Nautilus as root (via *sudo*).

---

### Post by audiomick on 2012-07-24
> **Bufeu said:**
> Try run Nautilus as root (via *sudo*).

No, not via sudo. Nautilus is a graphical application. If you want to run it with root privileges, you should use

```
gksudo nautilus
```

You should also shut down this instance of nautilus immediately after doing whatever it is you started it for.

---

### Post by Bufeu on 2012-07-24
> **audiomick said:**
> No, not via sudo. Nautilus is a graphical application. If you want to run it with root privileges, you should use

```
gksudo nautilus
```You should also shut down this instance of nautilus immediately after doing whatever it is you started it for.
*sudo* or *gksudo*, what the matter?

---

### Post by oldfred on 2012-07-24
Some reasons why for graphical apps to use gksu or gksudo.

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

---

### Post by sophie2cu2 on 2012-07-24
Hi guys,
I'm completely new to Ubuntu (and everything else for that matter). It would be helpful if you could really talk me thru this.
"Try run Nautilus as root (via *sudo*)" doesn't mean anything to me. And "gksudo nautilus" - nope. It doesn't give me any clues.
Sorry for being so slow.
S

---

### Post by critin on 2012-07-24
> **sophie2cu2 said:**
> Hi everyone,

As part of a longer / bigger project, I've been trying to set up a shared folder (the one with the two little arrows over the top). So, I went through all the steps, including:[INDENT]"allow others to create and delete files in this folder" .
[/INDENT]I also click on "add permissions automatically" when I get:[INDENT]Nautilus needs to add some permissions to your folder "Public" in order to share it
The folder "Public" needs the following extra permissions for sharing to work:
  - write permission by others
Do you want Nautilus to add these permissions to the folder automatically?
[/INDENT]But when I click on "create share" I get this:[INDENT]'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. No such user.
[/INDENT]Double-dutch to me.

Anybody know what this is and what I should do about it?

Please help,
Sophie :confused:

[http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/](http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/)

You'll need to open Samba from Dash and configure the preferences if you haven't already.  
When I got the error 255, I went to Samba and changed what I had to 'Share'
Mine doesn't need password protection so I set it up as in the screen shot.

---

### Post by Bufeu on 2012-07-24
> **sophie2cu2 said:**
> Hi guys,
I'm completely new to Ubuntu (and everything else for that matter). It would be helpful if you could really talk me thru this.
"Try run Nautilus as root (via *sudo*)" doesn't mean anything to me. And "gksudo nautilus" - nope. It doesn't give me any clues.
Sorry for being so slow.
S
Open a new Terminal window (Ctrl + Alt + T). Then, type:```
gksudo nautilus
```Press "Enter" and Nautilus starts with root privileges (as superuser).

---

### Post by oldfred on 2012-07-24
Back to original issue.

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/ubuntu-no-longer-allows-windows-computer-to-connect-wireless-909508/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/ubuntu-no-longer-allows-windows-computer-to-connect-wireless-909508/)

> I found the problem and it's working now.  I right clicked on the shared  folder went to permissions and changed the Group from sambashare to the  username on the ubuntu computer.  I don't know how it got changed.   Anyway shares on the ubuntu machine can be accessed from the windows xp  machine.  Thanks to everyone who responded on this thread.



If using an older version there was a bug filed, but  changed to invalid as it looks like something that should be installed was not.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/513427](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/513427)
[http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by Morbius1 on 2012-07-24
@oldfred, That's a different bug. THere's a whole family of bugs that start off with: 'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID.

But end differently like "invalid parameter" , "Unexpected information received", etc. I have never seen a "no such user" before. Perhaps doing it as root is the answer - I don't know.

But I do know that the correct permissions on the usershares folder has to be sambashare:
> ls -dl /var/lib/samba/usershares
drwxrwx--T 2 root sambashare 4096 Jul 10 14:52 /var/lib/samba/usersharesThere&#8217;s a possibility that the OP is not a member of the sambashare group but that would be a totally different error message. In any event I have tried to reproduce this error but have not been successful so far.

[COLOR=Blue]**EDIT**[/COLOR]: @oldfred, forgive me. Apparently I can't read. The issue was the shared folder had the group change to sambashare.

---

### Post by oldfred on 2012-07-24
@Morbius1
I still read the link I found as wrong. 

@sophie2cu2
Follow Morbius1's suggestions, he understands Samba. 

I gave up on Samba and converted my XP laptop to Ubuntu just so I did not have to use Samba to copy data from Laptop to Destop.

---

### Post by Morbius1 on 2012-07-25
> 'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. No such user.I was finally able to reproduce this exact error message on my own system. I did it by adding the following line to the global section of smb.conf:
```
force user = bobby
```I have no local user named bobby. Samba knows that and throws an error when I try to create a share. So the first thing I would do is to do a search of smb.conf and see if there is a "force user" line somwhere in the file and either change the user name or remove the line.

If you need help with that post your entire smb.conf file and we can help you. To do that run the following command in the terminal:
```
cat /etc/samba/smb.conf
```Then copy and paste the output from the terminal to the forum.

---

### Post by sophie2cu2 on 2012-08-06
Hi Critin,
Or anybody, please help.

When I go to Samba, all I've got is:

           /var/lib/samba/printers | print$ | Read Only | Visible | Printer Drivers

I don't see anything that shows me the directory I want to share (Public, as it happens).

Sorry, I'm lost. What to do?

S

---

### Post by Morbius1 on 2012-08-06
Post the output of the following command:
```
cat /etc/samba/smb.conf
```

---

### Post by gordintoronto on 2012-08-06
What version of Ubuntu, please?

---

### Post by sophie2cu2 on 2012-09-19
Hi everybody,

Final update on this problem: none of the proposed solutions work for me.

But thanks for your input anyway.

S

---

