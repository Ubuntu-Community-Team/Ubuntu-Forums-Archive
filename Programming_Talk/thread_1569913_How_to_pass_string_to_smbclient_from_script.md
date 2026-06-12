---
title: "How to pass string to smbclient from script?"
date: 2010-09-07
forum: Programming Talk
---

### Post by littelbro14 on 2010-09-07
So this seems slightly out of place in Programming talk, being just a simple bash script, but I didn't know where else to put it.

Anyway, I'm a bit of a linux noob, but I'm trying to write a simple script that will relay the same message to several computers on my local network via smbclient -M. However, I'm not sure how to pass a string to smbclient once it's been called, or how to commit it with ^d from the script. Any ideas?

---

### Post by raffaele181188 on 2010-09-07
I think this can help
From [official samba doc]("http://www.samba.org/samba/docs/man/manpages-3/smbclient.1.html")

> 
-M|--message NetBIOS name
This options allows you to send messages, using the "WinPopup" protocol, to another computer. Once a connection is established you then type your message, pressing ^D (control-D) to end.

If the receiving computer is running WinPopup the user will receive the message and probably a beep. If they are not running WinPopup the message will be lost, and no error message will occur.

The message is also automatically truncated if the message is over 1600 bytes, as this is the limit of the protocol.

**One useful trick is to pipe the message through smbclient. For example: smbclient -M FRED < mymessage.txt will send the message in the file mymessage.txt to the machine FRED.**

You may also find the -U and -I options useful, as they allow you to control the FROM and TO parts of the message.

See the message command parameter in the smb.conf(5) for a description of how to handle incoming WinPopup messages in Samba.

Note: Copy WinPopup into the startup group on your WfWg PCs if you want them to always be able to receive messages.


---

### Post by raffaele181188 on 2010-09-07
Also you can try this
```

$ smbclient -M myxp <<EOF
Meeting cancelled
See you at coffee house in 2 hrs.
EOF

```

---

