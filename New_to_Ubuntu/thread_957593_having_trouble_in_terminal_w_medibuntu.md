---
title: "having trouble in terminal w/ medibuntu"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by dizzy1kenobi on 2008-10-24
I paste the command from [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and then it asks for a password.  The problem is that it will not let me type anything at the prompt.  Does any one have a solution?

---

### Post by scragar on 2008-10-24
It still works, it just doesn't show what you are typing. Just type your password as if it was showing.

---

### Post by jpoRS on 2008-10-24
When you type in a password in a terminal, you don't see anything.  Just type in your password and press enter.  It should be fine.

jim

---

### Post by oldos2er on 2008-10-24
Go ahead and type in your password and press enter. It's normal not to see anything echoed to the terminal.

---

### Post by Duck2006 on 2008-10-24
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by marko_4454 on 2008-10-24
Probably you are talking about the "sudo" command. This is a "command" that will allow you to switch to your superroot account for just one line (command). 
It prompts you for the password like you mentioned. When you write any letters, they will not appear in the screen, however when you press enter you should see if you entered it correctly or not. 
SO summary, when it prompts you for your password write it without looking at the screen dont bother. When you finish putting it all, press enter and it should tell let you in if you wrote it correctly or return with an "Incorrect Password" if you didnt.
Hope this makes some sense.

---

### Post by trigsenior on 2008-10-24
yes , become super user before hand use this command.

sudo su 

then run command you need , warning if this can be avoided it not recommended. 

type 'exit' to exit.

---

### Post by dizzy1kenobi on 2008-10-24
Cool, thanks everyone.  I must have put it in wrong.  I also have another question.  Firefox has been acting a bit off so I downloaded a new version from mozilla.  How do I do I swap it for the old version?

---

### Post by marko_4454 on 2008-10-24
Did you install both versions using Synaptic? or using a deb file? or some other method?

---

### Post by Duck2006 on 2008-10-24
You can do it all in your Synaptic Package Manager

Mark the ones you want to uninstall and apply, then mark the ones you want and apply.

---

### Post by LowSky on 2008-10-24
no need to swap anything.
Best thing to do is back up your bookmarks
go to /home directory and delete the .firefox folder (you wont see it it's hidden, hit CTRL+h to see hidden folders)
restart up firefox and everything will be back to factory settings

---

### Post by marko_4454 on 2008-10-24
//nothing

---

### Post by marko_4454 on 2008-10-24
//double post

---

### Post by scragar on 2008-10-24
> **marko_4454 said:**
> Try running this command:



Maybe the version is different for liba52

no comma's.
```

sudo apt-get install w32codecs gstreamer0.8-plugins lame 

```

---

