---
title: "Cannot login (Authentication Failed)"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by blazercist on 2008-06-13
So its a weird weird problem....

I had the auto-login feature enabled to login to my user account since its a single user machine....well, it was.  But I got tired of wifey snooping around and decided I would create an account for her and disable auto-login, I added her account, changed the login screen to the pretty one with the "user browser" and rebooted.

Everything went well until the login screen popped up with a message "authentication failure", so I press "OK" and it just comes right back.

If I try to drop to term using ctrl+alt+f1 the screen goes black with no term,  weird thing is that the terminal is actually there, just the screen is black because if I type commands in the dark they actually work....

So I logged in (in the dark) then issued $sudo /etc/init.d/gdm stop
$entered my password
$startx

and wouldn't you know it I got that screen where its little white and black squares with the "X" cursor for the mouse, but it just stays there, I can move the mouse so I know it didn't hang but I cant get any further.

If i try to use recovery mode my screen goes black AGAIN, but im assuming its actually there just in the dark as before...

now that I think about it, I haven't tried $startx in the dark from recovery mode which I think I should.

But before I get home from work and try that does anyone have any other suggestions?

---

### Post by lswest on 2008-06-13
if you need to get into a gnome session to play with it do this:
```
nano ~/.xinitrc
``` then enter (blindly if you must)```
#!/bin/bash
gnome-session
``` (the file should not exist at the moment) and then save with <ctrl>+x then y then enter.  Try to run startx and it might boot into the gnome-session for you.  Don't know if it works with the GDM installed. *edit* **I'm not sure how well this would work, only do this if you can check if the file exists beforehand.  Possibly mount your drive in a liveCD and create the file that way.**

Otherwise you can try booting to the liveCD, then mounting your drive and doing ```
sudo chroot [path to mounted drive]
``` and doing ```
sudo apt-get install --reinstall gdm
```If that doesn't work I'm out of ideas.

---

### Post by aktiwers on 2008-06-13
Maybe this will be helpful:
[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

---

### Post by blazercist on 2008-06-13
thanks for the suggestions I'll give it a try wen I get home at 6pm and post the results.

---

### Post by blazercist on 2008-06-16
a combination of these methods did that trick, aktiwers method gave me the ability to see what i was typing I had to reinstall gdm and delete .Xauthoriy

---

