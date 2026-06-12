---
title: "Has anybody tried to run Remote Desktop over the Internet?"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by bwallum on 2008-10-26
Hi

I am trying to run Remote desktop over the Internet. Has anybody tried that? I just want to connect up to Ubuntu users (I've converted a few but would like to save petrol) and help them when they get stuck (which is quite rare, it has to be said.) Problems usually revolve around losing files or false assumptions such as 'it was emailed to me so why is it not in pictures'. in these sort of scenarios it's good to show them how to navigate the system and driving their pc for a few seconds, then getting them to replicate the moves, would be great.

Anybody tried this? The network forum is very quiet (no response) so it may be that it can't be done.

Kind Regards
Bob

---

### Post by Xiong Chiamiov on 2008-10-26
As long as the appropriate ports are opened, I see no reason why not.  I've used [other]("http://www.crossloop.com/") similar-type applications over the internet successfully without too much lag.

---

### Post by taqkavar on 2008-10-26
on their box:
System > Preferences > Remote desktop
If they have a router, forward the port that it indicates in it. mine is 5901
then go to : [http://www.showmyip.com/](http://www.showmyip.com/) and write down the ip

On your box
Applications > Internet > Remote Desktop Viewer
use the ip address to access their computer

---

### Post by issih on 2008-10-26
Generally the vnc protocol can be fairly easily eavesdropped, so for security a lot of people use ssh to log into the remote box and forward the remote port via an ssh tunnel to a local port, then connect the vnc viewer to the lcoal port. Doing this increase the security of the transmission. You should really ensure that the user passwords are reasonabley strong and use a program like deny hosts to stop people using dictionary attacks on your internet exposed box.

Worth being careful, if you open the door to the internet, make sure you still have the lock and key :)

Hope that helps

---

### Post by bwallum on 2008-10-27
If I use the Remote Desktop Viewer in Ubuntu does it automatically set up a ssh tunnel for me?

---

### Post by cozmicharlie on 2008-10-27
Yes you can do this.  Follow the instructions from post #5 by superprash2003 in this thread ([http://ubuntuforums.org/showthread.php?t=747979](http://ubuntuforums.org/showthread.php?t=747979)).  I did it and it was very easy to set up and it worked great.

Enjoy

---

### Post by random turnip on 2008-10-27
I never thought of this, if you get it working i could always get someone to sought my problems out for me over the internet.

---

### Post by cozmicharlie on 2008-10-30
Go here for the complete instructions on how to do this.
[http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html](http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html)

---

