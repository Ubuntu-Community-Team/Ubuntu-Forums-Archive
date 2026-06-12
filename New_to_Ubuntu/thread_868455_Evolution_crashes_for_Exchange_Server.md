---
title: "Evolution crashes for Exchange Server"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by mailkarthi on 2008-07-23
Hi,

I use Evolution to connect to my office Exchange Server. I don't use outlook mainly because I have to be connected to VPN and I dont want to connect to VPN.

I configured Evolution to use Web Mail address (over Internet, like webmail.mycompany.com/exchange) and it works great to check mails. Mails I delete in Evolution gets deleted in Server as well. So far so good. But when-ever I click on reply or new mail or click on contacts, Evolution turns non-responsive and I have to "Force Quit" Evolution. I believe this happens when Evolution looks for Corporate Address Book. I am ok even if you suggest me on how to disable Evolution from looking for Server Address Book.

---

### Post by braddcadd on 2008-07-26
Start evolution from a terminal and see if any error messages appear in the terminal.  Also take a look at the manfile for evolution.  It looks like you can send debug information to a certain file.  If you get an error message that may be causing your problem, post it hear, google it, or look at the gnome forum (evolution is developed by gnome).

```

man evolution
evolution --debug=my_error_file.txt

```

---

### Post by stmiller on 2008-07-26
Do you know what version of Exchange server you have? I think support for the latest exchange 2007 is not 100% yet.

---

### Post by darkjester74 on 2008-07-27
Hello...

I am having the exact same problem.  I captured the errors as instructed above, and here are the contents of my log file:

```
error : unterminated entity reference       Migration
evolution-shell-Message: Killing old version of evolution-data-server...
BBDB spinning up...
```

I am connecting to an Exchange 2003 SP3 server.  The man page for evolution seems to give very little information.  I will go ahead and search the Gnome forums as well, and if I find anything I will post it here.

I am a total Linux newb, if you couldn't tell, btw.  :)

---

### Post by darkjester74 on 2008-07-27
Well, I guess I should have done that Google search first, because I think I just solved my problem.  :lolflag:

Googling the "BBDB spinning up" message lead me to [this]("https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/154464") Launchpad thread.  This crash appears to be caused by Evolution attempting to automatically save the Exchange addresses in the Contacts folder.  This will occur even if the options for this feature is unchecked.  

The workaround seems to be to go into Preferences, tic and clear the appropriate checkbox, then restart Evolution.  The issue has not resurfaced since.  Hope this helps!

---

