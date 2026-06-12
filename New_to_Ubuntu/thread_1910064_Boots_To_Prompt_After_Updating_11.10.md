---
title: "Boots To Prompt After Updating 11.10"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by younglemon on 2012-01-16
I just updated software on my Ubuntu 11.10, 64 server edition.  I upgraded to 11.10 when it was released and have been running without issue.  I just updated software and now it boots to the text prompt.  I can log in and everything seems to be there it's just that the desktop (I think its called Unity) is gone.  
 
I've seen several issues with graphics cards posted and I just don't know how this could have happened.
 
I apologize for repeated redudant questions.  I'm sure that the answer is posted and I am missing it and I will continue to search the threads.  In the meantime I'm going to attempt a new post.

---

### Post by MG&amp;TL on 2012-01-16
Well....what are your system specs?

Does it ask for login and pass, or are you just stuck at something like:

busybox v.xx.xx
$
(bad)

or just a blinking prompt? (possible worse?)

If if it asks for login and pass, try logging in and typing:

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by younglemon on 2012-01-16
Yes it does ask for a login and pw.  I am trying your suggestion now, thank you so much for your quick response.  Even if it doesn't end up working, I am grateful for your prompt response.  I will let you know, soon I hope.

---

### Post by younglemon on 2012-01-16
Wow this is taking a long time, its still chuggin away.

---

### Post by younglemon on 2012-01-16
Seems like it finished and now at the prompt it reads: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
This almost seems like it the error I usually get after installing or updating software.  I'm going to reboot and hope for the best.

---

### Post by younglemon on 2012-01-16
No, it still boots to 
"Ubuntu 11.10 Server tty1
Server login:"
From here I can log in but no desktop interface

---

### Post by MG&amp;TL on 2012-01-16
Ah....okay, you have somehow managed to install the server edition. I suggest backing up your stuff (you can do this from a live CD, or I can provide instructions for a CLI), then installing ubuntu from a new disk.

The server edition has no desktop, to increase security and decrease server load.

---

### Post by younglemon on 2012-01-16
Well, I've always had the server edition.  That part hasn't changed...unless you're saying that Unity desktop is only for the desktop edition and somehow I've managed to install it over a server edition install

---

### Post by younglemon on 2012-01-16
Or, are you saying I should create a disk and install it that way?

---

### Post by MG&amp;TL on 2012-01-16
> **younglemon said:**
> Well, I've always had the server edition.  That part hasn't changed...unless you're saying that Unity desktop is only for the desktop edition and somehow I've managed to install it over a server edition install

errr...no, but, but why would you do that? It would be easier to install apache on a desktop release...

Anyway, can you quote a bit more about the dpkg error code?

Creating a disk is often safer, upgrading is often a bit dodgy.

---

### Post by sonicsackboyver.25.04 on 2012-01-16
shouldnt the server edition be just for developers or big networks?

---

### Post by younglemon on 2012-01-16
I'm not sure what you mean.  There isn't anything more on the error.  As far as apache....I don't believe I'm running apache.  Unless of course I am and don't realize it.  
 
I can log into the server from the text prompt.  Is there a way to start the desktop from here?

---

### Post by younglemon on 2012-01-16
It appears as if the files are there and I can browse to them, but the graphic user interface (I think its called Unity) is no longer available

---

### Post by younglemon on 2012-01-16
Is there a way to undo the software update that may have had  a hand in causing this issue?

---

### Post by younglemon on 2012-01-16
I just attempted the command you asked me to try previously, again.  It seems like maybe I should try '-server' instead.  What do you think?

---

### Post by younglemon on 2012-01-16
I was using virtual box prior to the software upgrade.  Now, I closed it and shut out of the program in the usual way so, I doubt that it was the application but... could it have been?  
 
I'm dead in the water but seemingly so close.  I can log in at the prompt and see the directories and files but, thats about it from here.  Is it time to start looking at starting over?

---

### Post by MG&amp;TL on 2012-01-16
Why are you running ubuntu server if you're not running a web server? (if you're running a different webserver than apcahe then I apologise for being overly presumptious.).

There should definitely be some errors before the dpkg error, but if not, the entire output from the command, please. You can redirect the output to a file like this:

```
sudo apt-get install --reinstall ubuntu-desktop &> apt.log
```

which will dump the content to apt.log, in the $pwd.

Also try:

```
sudo apt-get install -f
```

and

```
sudo service lightdm start
```

Output from these, too, please. :)

---

### Post by younglemon on 2012-01-16
I wish you could see this as I don't think I can get to the output that youre requesting
 
Its soo very strange.  This was all good well and fine before the software update.  Blah! 
 
I'm still trying to figure this out exactly....even if I do tho, not sure how I'm going to get it to you here
 
....unless I retype the file.  Is there something specific we're looking for?  This has so thrown me.  I really didn't need this today.  Im probably going to have to cancel some things this week if I don't get this working again.  
 
Thanks for your continued suppoprt, I'll try to get you this info somehow soon.

---

### Post by younglemon on 2012-01-16
Looking at the apt.log file now.  Errors associated with Samba 4.  Many unknown parameters.  Is there a way to replace the desktop for the server edition?

---

### Post by younglemon on 2012-01-16
doesn't seem like the other two commands did anything
 
not sure if they worked

---

### Post by younglemon on 2012-01-16
Oh boy.  How do I get out of viewing this file now?  I think I used 
vi apt.log
How do I close this file?

---

### Post by younglemon on 2012-01-16
I just rebooted.  Nothing seemed to work.

---

### Post by younglemon on 2012-01-16
Is there a start up procedure that I could somehow bypass the items that are automatically starting up?  It almost seems like vboxguest is fouling up the works.  Perhaps the vboxguest is somehow attempting to start with Ubuntu and it cant find the 'PCI device' (display I'm guessing) so it goes right to the text prompt.  Is that possible?

---

### Post by MG&amp;TL on 2012-01-16
> **younglemon said:**
> Is there a start up procedure that I could somehow bypass the items that are automatically starting up?  It almost seems like vboxguest is fouling up the works.  Perhaps the vboxguest is somehow attempting to start with Ubuntu and it cant find the 'PCI device' (display I'm guessing) so it goes right to the text prompt.  Is that possible?

That's a bit weird. I'm no way a hardware expert, but it wounds like it can't find your graphics card (not your display, you wouldn't be able to see anything at all). Obvious question-is it still in the socket?

I've no idea what the ubuntu startup files are, but check /etc/rc.local.

You could try temporarily disabling samba (i.e uninstall it).

to help others who are hardware experts, could you post:

```
dmesg | grep PCI
```

About desktop -> server:

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Remove virtualbox? It won't remove your VMs. (although make a copy first)

Just trying a process of elimination.

Btw, use:

```
less <file>
```

to view files, and if do use vi, to save &exit:
Esc
:wq

in that order.

To not save:

Esc
:q!

Thanks.

---

### Post by younglemon on 2012-01-16
Well it can't find the virtual box display/PCI card, as it comes up under the vbox guest additions sequence

---

### Post by younglemon on 2012-01-16
So I've posted this thread on the server section as well, to see if there were any differences of opinion.  Someone noted there that I would have had to installed the desktop GUI separately from the server edition install.  And as I think about it... I believe they are correct, although I do not remember exactly which one and asked them if they knew how I could find out.  Although I don't know how much help that will be right now, as I am upgrading software.  So, if I understand correctly what has and is happening is the following.  I updated software and it knocked out the GUI desktop.  I then attempted several things and am currently upgrading software in an attempt to reset the desktop gui, which will probably not work.  However, I can't interrupt it now as that may make it non-recoverable.  Batting a thousand today, but thank you for your input and assistance.  So now I'm left to wonder, what was the software update that blew out the desktop GUI and will I repeat the same mistake if I attempt to update software again?

---

### Post by MG&amp;TL on 2012-01-16
> **younglemon said:**
> So I've posted this thread on the server section as well, to see if there were any differences of opinion.  Someone noted there that I would have had to installed the desktop GUI separately from the server edition install.  And as I think about it... I believe they are correct, although I do not remember exactly which one and asked them if they knew how I could find out.  Although I don't know how much help that will be right now, as I am upgrading software.  So, if I understand correctly what has and is happening is the following.  I updated software and it knocked out the GUI desktop.  I then attempted several things and am currently upgrading software in an attempt to reset the desktop gui, which will probably not work.  However, I can't interrupt it now as that may make it non-recoverable.  Batting a thousand today, but thank you for your input and assistance.  So now I'm left to wonder, what was the software update that blew out the desktop GUI and will I repeat the same mistake if I attempt to update software again?

I don't know; and I don't think so. Software intended for release is typically very stable. If dpkg returns an error, I doubt that you'll be able to update.

---

### Post by younglemon on 2012-01-16
If you look at this same topic under the server listing, Charles replies with attempting to switch to tty7 by way of Ctrl + Alt + F7.  This ended up bringing back the missing desktop.  Still reporting a system error when it booted up, but the desktop did return

---

### Post by younglemon on 2012-01-28
MG&TL thank you again for all of your assistance.  So far, so good, still :)

---

