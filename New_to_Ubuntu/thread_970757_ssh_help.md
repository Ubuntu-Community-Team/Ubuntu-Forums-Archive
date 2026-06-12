---
title: "ssh help"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by user2000 on 2008-11-04
hi,

i am trying to use ssh and login to my remote ubuntu server. once i do that i am running a program (which has an infinite loop) and does some functionality. however, when i close my ssh screen, it automatically closes the program also. i want to keep the program running on my server.

how is this accomplished? do i need to run it as a service or something?

thank you

---

### Post by Peter09 on 2008-11-04
As a service or you can run it as within a script called /etc/rc.local. This script is run at boot time as user root. Anything running in there will run continuously (make sure you run it in the back ground). Beware that any error could prevent your machine completing its boot.

---

### Post by pmsumner on 2008-11-04
The simplest way would be to use a program called "screen".  This basically allows you to have virtual screens running in a terminal.

You may need to install screen first by typing:
> sudo apt-get install screen

For detailed info, see:
> man screen

Basically, log in and start your program using the command 
> screen programName

And the program will start running in a new "virtual" terminal.  This terminal can then be "detached" and left running in the background while you log out or do anything else.

To detach the screen press "CTRL+a" then "d".
To reattach to the screen, in a terminal type:
> screen -r

There's so much more you can do with screen, but there's the basics.

---

### Post by Sarmacid on 2008-11-04
You can also do it using an '&' at the end of the line
```
./mycommand &
```
Or just run it, press ctrl + z, then input bg and press enter. If you want to go back to the program just input fg and press enter.

---

### Post by bodhi.zazen on 2008-11-04
> **Sarmacid said:**
> You can also do it using an '&' at the end of the line
```
./mycommand &
```Or just run it, press ctrl + z, then input bg and press enter. If you want to go back to the program just input fg and press enter.

No, that will not work Sarmacid. When you close the ssh session the apps will close.

You can use nohup

nohup <command>

+1 for screen though.

[http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

---

### Post by user2000 on 2008-11-06
thankyou for your replies. can you guide me how to run my simple perl script as a process in the background which loads when linux loads and exits when it ends. also i should be able to remotely login and exit it as well as start it. (very similar to how an apache service works)

thank you very much.

---

### Post by bodhi.zazen on 2008-11-06
> **user2000 said:**
> thankyou for your replies. can you guide me how to run my simple perl script as a process in the background which loads when linux loads and exits when it ends. also i should be able to remotely login and exit it as well as start it. (very similar to how an apache service works)

thank you very much.

Sounds like you want an init script.

[http://www.novell.com/coolsolutions/feature/15380.html](http://www.novell.com/coolsolutions/feature/15380.html)

[http://www.linux.com/articles/46892](http://www.linux.com/articles/46892)

most of these are bash scripts, I see no reason you could not use perl.

---

### Post by cicatrix1 on 2008-11-06
You'll need to look at how to daemonize also.  There is a check list of things you need to do to successfully create something that won't cause havok by constantly running.  It's not really that hard to do in perl.  Just google for daemonize and perl and you should find some examples.

---

