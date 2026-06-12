---
title: "[SOLVED] zenity: Gtk-WARNING **: cannot open display"
date: 2008-04-19
forum: Programming Talk
---

### Post by Jeff294 on 2008-04-19
Howdy!  
I'm using a script that is called by UDEV whenever I mount my USB thumb drive, which automatically makes a backup of the thumb drive. It works fine. I thought I'd add a question dialog using zenity, to ask the user (me) whether to skip the backup this time.  My zenity question dialog works just fine when run from a test script on my desktop, but when added to the UDEV script (which I think runs as root) the zenity call gets this error message: 
(zenity:8596): Gtk-WARNING **: cannot open display: 

From reading posts here and thru Google, I think the script running as root doesn't have access to my xterm or GUI display, but here my knowledge runs out and I don't know how to fix that.  I'm guessing maybe setting an environment variable at the beginning of my script, but I don't really know what variable or value.  

Anybody know how to fix this?  (I'm using Hardy beta, with up-to-date updates).

Thanks so much!
Ubuntu rocks!
...Jeff

---

### Post by x1a4 on 2008-04-19
Try running the script using **sudo** (or gksudo) with the **-s** option.  For example: 
```
sudo -s -u username script
```

I'm not 100% certain if this will work, but I've always been able to run X applications whenever I use **sudo -s**.

In order to avoid having to type a password, using /usr/sbin/visudo, add this to your sudoers file: 
```
username ALL=(ALL) NOPASSWD:/path/to/script
```

---

### Post by Jeff294 on 2008-04-19
Actually, I'm not running the script, it is being automatically run by the UDEV utility, which can be set up to run user supplied scripts when certain events take place, like when a thumb drive is mounted.  It always runs its scripts as root, and I don't think I can change that.  I think what's happening is that I've coded the script to throw up a message and wait for a reply (using zenity), but since the script is running as root, it doesn't know how to access my gui desktop, and so the message/reply fails.  I'm thinking there must be something I need to add to the script so it knows how to access my gui display when it needs to.

---

### Post by x1a4 on 2008-04-19
Inside the script try using sudo (or gksudo) to run zenity.  See if this works: 
```
sudo -u $USER zenity
```

---

### Post by Jeff294 on 2008-04-19
That seemed like a really good idea, but unfortunately it didn't work.  I tried both sudo and gksudo, and got the same error message.  Thanks for the suggestion though!

---

### Post by happyhamster on 2008-04-19
Take a look at:
[http://bbs.archlinux.org/viewtopic.php?pid=291934](http://bbs.archlinux.org/viewtopic.php?pid=291934)

---

### Post by x1a4 on 2008-04-19
Try running ```
xhost local:*user*
``` before gksudo.  Where *user* is the name of the user you want to run as.

---

### Post by Jeff294 on 2008-04-19
Thanks for that suggestion as well:  I read the thread you sent me the link for, and I tried adding this to the script:

     export DISPLAY=:0.0 

It still doesn't work (zenity, that is), but now I get a new error message: 

     No protocol specified

in addition to the Gtk warning message I was getting before.  Is that significant of something?  

Thank you for your time trying to help!

---

### Post by Jeff294 on 2008-04-19
I tried the  xhost local:user  -- still getting the same errors:

No protocol specified

(zenity:7522): Gtk-WARNING **: cannot open display: :0.0

---

### Post by Jeff294 on 2008-04-20
Yippee!    With a little repeated testing I finally got it to work, using a combination of the clues you good people have given me.  
Here's what I eventually coded in the script (which is executed by UDEV):

```

su $USER -c 'xhost local:$USER; zenity --question --text "Continue or cancel?" '

```

I couldn't tell you WHY it works, but it does!  Now when I plug in the USB thumb drive, the zenity question box appears and waits for an answer. 

Thanks to all who responded!
Ubuntu Forums Rock!

---

### Post by tthorb on 2009-09-25
I had problems with sending messages with Crontab to a user, since there are 20 LTSP-thin clients (Edubuntu) here. But - the solution was quite easy.

To find the correct display number, you can do this:

```
ps -ef |grep ^USERNAME|grep screensa| awk '{ print $2 }'| strings   /proc/`xargs`/environ |grep DISPLAY 
```

This checks the number of a a process for the correct user (in this case, I picked screensaver)

In the bash script, I've used this like this:

```
dispp=`ps -ef |grep ^USERNAME|grep screensa| awk '{ print $2 }'`
dispn=`strings /proc/$dispp/environ |grep DISPLAY|sed 's/.*=\(.*\)\..*/\1/' `
DISPLAY="$dispn" su USERNAME -c '/usr/bin/zenity --question --text "Question" '
```

---

### Post by rosencrantz on 2011-09-05
> **Jeff294 said:**
> Thanks for that suggestion as well:  I read the thread you sent me the link for, and I tried adding this to the script:

     export DISPLAY=:0.0 



it works for me with 
env DISPLAY=:0.0 zenity --question
running from a root text console.

---

