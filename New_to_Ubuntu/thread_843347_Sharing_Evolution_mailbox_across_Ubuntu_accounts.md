---
title: "Sharing Evolution mailbox across Ubuntu accounts"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by waggers on 2008-06-28
Hi

With our previous (MS Windows + Outlook Express) setup, we had separate user accounts on the OS (one each for my wife and me) but I set OE up so that we could both see our shared email account.  (ie. whichever one of us connected to the internet and received the emails, both of us would be able to see the messages that had been downloaded).  Is it possible to set Evolution up in the same way?

---

### Post by 505 on 2008-06-28
I think it is possible, although I have not tested it. Linux supports symbolic links, which are links to files at any other place on your system.
So you could do the following:
- Make your evolution folder accessable to your wife. It's under ~/.evolution Rightclick, choose Properties, Permissions and set "others" to read and write for the folder and the files. Apply the permission to all files.
- In your wife's home folder make a symbolic link to your evolution folder (command "ln -s /home/your_name/.evolution").

---

### Post by waggers on 2008-07-03
Sorry it's taken a while to try this out - have just done so and it works perfectly.  Thanks very much

---

### Post by waggers on 2008-08-02
Ok, I'm afraid things aren't going as well as I thought.  My wife can send and receive emails as she should; I can also receive emails.  However, when I compose a message and hit "send", the message window disappears (as you would expect when sending an email) but then reappears again a second or so later, without sending the message.  Also, when I delete items from the inbox, they are present again the next time I open Evolution.:(

---

### Post by eightmillion on 2008-08-02
You're problably having trouble with permissions. Try this:
> sudo chown -R waggers:waggers ~/.evolution
I'm assuming waggers is your username on the computer too. Change that as needed.

---

### Post by eightmillion on 2008-08-02
As for fixing this problem for good, you should delete the symbolic link and just have your wife run evolution as you. For example, she could run:
> gksu -u waggers evolution
This will run evolution under your user on her login. You could even edit her menu entries to reflect this.

---

