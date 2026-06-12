---
title: "[SOLVED] Cannot mount Lexar compact flash card"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by brad0022 on 2008-10-05
Sorry if this has been answered before. I am using Ubuntu EEE on an Acer Aspire One. When I try to access my Lexar compact flash I get this message:
[IMG]http://i95.photobucket.com/albums/l145/brad0022/Screenshot-17.png[/IMG]

I get this error whether I use a card reader or connect my Sony Alpha 100 directly to my Aspire One. I want to be able to temporarily dump some images to my netbook to free up my CF cared so I can shoot more pics when it fills up. 

What does superuser mean? How do I fix this? I am a newbie so I need a little bit of help in layman's terms.

---

### Post by mrtomservo on 2008-10-05
A super user or "root", is a user account that has access to your whole computer.  Most likely if you are the primary user of the computer, it's you.  You can use 'sudo' to temporarily become the super user to complete commands you couldn't normally run from your account.  This is for security and safety.

I believe there is a bug that sounds similar to the problem you're describing.  I'm not familiar at all with the EEE, so maybe someone else can give some pointers if i'm not being clear enough.

Anyway, you'll want to open up a terminal.  (command line) I would guess it could be found under Applications, Accessories, and Terminal.  You will be asked for a password (your password) when running sudo. Once at a prompt you need to type:

```
sudo cp /etc/fstab /etc/fstab.old
```

Command above is to make a copy of the original file in case there's a problem after we change it

```
sudo gedit /etc/fstab
```

This will open up the text editor and you can put a pound sign (#) in front of the lines in the file that contain "cdrom" in them.  Placing a # in front basically tells the OS to ignore that line.  

Save the file, then close it.  Reboot and see if it works.  I got this information from this link:

[https://lists.launchpad.net/ubuntu-eee-coders/msg00382.html]("https://lists.launchpad.net/ubuntu-eee-coders/msg00382.html")

---

### Post by nowshining on 2008-10-05
try this link:

[http://www.cs.sfu.ca/~ggbaker/personal/cf-linux](http://www.cs.sfu.ca/~ggbaker/personal/cf-linux)

---

### Post by brad0022 on 2008-10-05
Thank you much mrtomservo. It worked perfectly. Thanks again for the fast response. F-Spot opened and imported the pictures. :)

---

### Post by Haventfoundme on 2008-10-29
Thanks for the posting and the replies. I am so happy now, can't you hear it in my voice....



[COLOR="Blue"][FONT="Comic Sans MS"]"Living La Vida Ubuntu!"[/FONT][/COLOR]

---

