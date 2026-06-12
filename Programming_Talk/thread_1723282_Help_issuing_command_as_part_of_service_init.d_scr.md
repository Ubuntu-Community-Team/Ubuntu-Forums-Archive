---
title: "Help issuing command as part of service init.d script"
date: 2011-04-06
forum: Programming Talk
---

### Post by mosquitogang201 on 2011-04-06
I have added the following line to my /etc/init.d/lirc so that I can automatically start the irexec daemon.

su daniel -c "/usr/bin/irexec -d /home/daniel/.lircrc"

I also have a command set to start mythfrontend from my remote. The section of my .lircrc is below:

begin
    remote = mceusb
    prog = irexec
    button = Home
    config = /usr/bin/mythfrontend &
    repeat = 0
    delay = 0
end

Now the problem is, when the computer boots up or when I do a "sudo service lirc restart", irexec does run, however it will not accept the command to start mythfrontend. The other commands I have programmed with irexec do work however (I programmed global volume commands).

If I do a "sudo /etc/init.d/lirc restart", irexec does run and I can launch mythfrontend correctly from my remote. However, this is not how Mythbuntu is calling it on boot...

So I'm not really sure how to fix it. I'm guessing this might be some sort of permissions problem..any ideas?

---

### Post by mosquitogang201 on 2011-04-07
Also I should add, I have changed the command in /etc/init.d/lirc to

/usr/bin/irexec -d /home/daniel/.lircrc

and changed the line in .lircrc to read

config = su daniel -c "/usr/bin/mythfrontend &"

Now, when starting lirc by "sudo service lirc restart", irexec starts but will not issue this particular command, as before. When starting lirc by "sudo /etc/init.d/lirc restart", irexec starts and issues the command correctly, so same problem as before.

I thought I could get around this whole issue by adding a sleep 15 command and then "/etc/init.d/lirc restart" to my rc.local so that lirc is restarted as I need it after the computer has finished booting. However rc.local is not executing this command on boot (although other commands in my rc.local do run). If I run rc.local manually the script works correctly.

---

