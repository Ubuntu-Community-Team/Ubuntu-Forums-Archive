---
title: "HOWTO: Setup ngird on Dapper"
date: 2006-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Haegin on 2006-12-06
This guide should help you install ngircd (an irc server) on Ubuntu Dapper. To do this we will need a text editor, apt-get and access to the internet. The text editor I use is vim, if you prefer something else such as gedit, kate or nano just use the command for that editor wherever I use vim.
The first thing you need to do is install the package
```
sudo apt-get install ngircd
```
Then you need to configure it but before we can do this we need to chmod some stuff so get your chmodding shoes on and
```
sudo chmod a+rwx -R /etc/ngircd
```
and then take your chmodding shoes off again and get your configurating gloves on and
```
sudo vim /etc/ngircd.conf
```
and you are ready to configure your server.
Set the name to something you want to use - It's displayed before the motd when you connect
Set the info - just like name its displayed when you connect
Set up your admin details etc in the obvious area.
You can leave ports alone and use them easily enough - change them if you have a reason.
The rest can be left unless you are desperate to change it. If you only want to use it on your local network then change the Listen line.
You can also set a limit on the users if you wish.
Now scroll right down and set up a channel to talk in.
Finally save and close the file and open the motd file
```
sudo vim /etc/ngircd/ngircd.motd
```
And set up your message of the day.

Once the server is configured you will probably want to start it on boot but on ubuntu this is currently broken so to fix this we need to
```
sudo vim /etc/init.d/ngircd
```
then change line 20 so that it reads " --pidfile /var/run/ngircd.pid \" (notice that the ngircd directory has been removed from the path). This done save and close and run:
```
update-rc.d ngircd defaults
```

This is all I have done with my server so I can't help much more but have fun.
Oh, and don't forget to forward ports on your router if you want to give access to the world beyond your network

To undo the changes you have made you just need to stop the irc daemon and uninstall it. The following command stops the irc daemon.
```
sudo /etc/init.d/ngircd stop
```
and you can then remove the ngircd program choosing to keep or remove the config files.
To keep them:
```
sudo apt-get remove ngircd
```
To remove them:
```
sudo apt-get remove --purge ngircd
```

---

### Post by venik212 on 2007-01-18
Could you  please provide an example of your ngircd.conf?
Thanks,

---

### Post by Haegin on 2007-01-19
I will post it when I get home as I have turned off the dyndns at the moment - should be up here at about 9.00 pm GMT provided I have electricity (no power at the moment)

---

### Post by Haegin on 2007-01-19
Voila!

---

### Post by venik212 on 2007-01-19
Thanks so much for your help!  
I still have some questions:
1) What are the lines with a ; at the beginning?  SHould I remove it? Are these optional?
2) Must the server name be a NAME or can it be an IP address?  I have DHCP

---

### Post by venik212 on 2007-01-19
I tried to run it, was told that it is already running, but I do not see it as a process in the Sytem Monitor...
Sorry to be so dense, but I am just starting with Linux.

---

### Post by Haegin on 2007-01-20
I don't know if the server name can be an IP - check the man pages or the online documentation for the project or just try it and see.

The lines beginning in ";" are just more comments - I use them to show that they could be used as lines the program would recognise where as lines beginning with "#" are just human comments to explain stuff. That way if I want to specify the motd in the config file I can easily see what I have to do rather than find out how on the net for example.

If you followed my guide the irc daemon is set to start on boot so you don't need to start it manually but if you did want to you should use:
```

sudo /etc/init.d/ngircd {start|stop|restart}

```
to start it, stop it or reload it (you just use one of those three words).

Hope this helps

---

### Post by venik212 on 2007-01-20
I rebooted, but still could not see the ngircd in the process list of the System Monitor, although when I tried to START it I was told that it is already running.  I was unable to connect to the server, but I suspect that my system adminidtrator had shut down all IRC channels.  I have to find out about that.
Thanks.

---

### Post by Haegin on 2007-01-20
If your system admin has been a boring oppressor try running it on a different port.

---

### Post by venik212 on 2007-01-20
Regardless of the system oppreminator, it should still appear as a process in the System Monitor, shouldn't it?

---

### Post by Haegin on 2007-01-21
I don't know - I access my server using ssh so I dont use the gui much. Currently I don't have ngircd installed but I would think ps a -e would show it.

---

### Post by Offoffoff on 2007-12-02
Well. Server works, BUT it works after I always see this: "Starting Next generation IRC server: start-stop-daemon: Unable to open pidfile `/var/run/ngircd/ngircd.pid' for writing: No such file or directory (No such file or directory)" and make in /var/run/ngircd/ngircd.pid manually.
 It is not good. How to allow program ngircd make this file?

---

