---
title: "[SOLVED] Can't Find TS Server"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Kenza on 2008-06-20
Just installed the Client and Server for Teamspeak, Found the Client Shortcut easy, but as for the server i can't find anything and i checked Synaptic to make sure it was installed. Looked on the "Run Application" list and don't see it listed there either.

---

### Post by azurepancake on 2008-06-20
Hmm, try this. Open up a terminal session and type the following..

```
teamspeak-server
```

If that works, you can then make a desktop shortcut. Right click on the desktop and click on "Create Launcher".. give it a name and in the "Command" form, type "teamspeak-server". Hit Ok.

Hope this helps.

---

### Post by Kenza on 2008-06-20
Tried to run in Terminal, copy and pasted what u said to put in it and typed it also and come up with the same thing:

kenza@kenza-desktop:~$ teamspeak-server
Exception EFCreateError in module teamspeak-server.real at 0806F095.
Cannot create file "/usr/lib/teamspeak-server/server.ini". Permission denied.

---

### Post by azurepancake on 2008-06-20
Okay, my mistake! 

What you need to do to start it, is to execute the script in the /etc/init.d directory. So in terminal, you would type..

```
sudo /etc/init.d/teamspeak-server start
```

This will start the server. Teamspeak-server has no GUI front-end so all configuration is done in the /etc/teamspeak-server/server.ini file. To edit, type the following into a terminal session..

```
sudo gedit /etc/teamspeak-server/server.ini
```

Normally, when you make a change to the configuration file, you'll want to restart the service like so..

```
sudo /etc/init.d/teamspeak-server restart
```

If your behind a firewall/NAT, just make sure the correct ports are open. After that you should be able to find your server from the client.

Hope this helps.

---

### Post by Kenza on 2008-06-20
Thanx for the replies Azure, i'm really the biggest n00b on here and a lot of what u say seems like Chinese to me, but i'll work on it and let ya' know how it works out =)

---

### Post by azurepancake on 2008-06-20
> **Kenza said:**
> Thanx for the replies Azure, i'm really the biggest n00b on here and a lot of what u say seems like Chinese to me, but i'll work on it and let ya' know how it works out =)

Sorry, I know how you feel. Trust me, with just a little time you'll learn a lot about Linux. 

Let me try to explain a little what exactly is going on in my last post.

It is very important for you to know what exactly "sudo" does. The command "sudo" stands for "superuser does" and gives you superuser privileges for that single command. With this, you can use certain commands, programs and access files owned by other users, as long as you know the root password.

When ever you encounter permission errors, normally all you need to do is throw a "sudo" before the command. Just be careful! 

Now, when you installed TeamSpeak server, it put a script in the directory "/etc/init.d". This script basically tells the program how to start-up and where everything is located for the server to run properly.

So to activate this script (start the program) you type..

```
sudo /etc/init.d/teamspeak-server start
```

This starts the server with the superuser privileges.

Because the server does not have a graphical user interface, you need to open its configuration file (located at /etc/teamspeak-server/server.ini) with a text editor. In this case, Gedit. You do this by typing the following command..

```
sudo gedit /etc/teamspeak-server/server.ini
```

Edit what you need to edit and save. Although, the server should run without configuration. You just need to forward the correct ports on your router (TCP: 8765, UDP: 8766).

EDIT: 
There is a much easier way to configure Teamspeak server. Simply follow this link, [http://www.howtoforge.com/how-to-install-a-teamspeak-server-on-ubuntu/](http://www.howtoforge.com/how-to-install-a-teamspeak-server-on-ubuntu/). This will allow you to configure the server through your browser. You can skip the installation part of the guide.

Good luck

---

### Post by Kenza on 2008-06-21
Well it's up and running, not getting any sound at all, but that's a case for another thread i think lol (actually just going to "search" around for it), The help is much appreciated Azure!

Take Care! Kenza

Edit: I see people have a Thanks and Thank X times in Y posts, i don't know how to do it or i would =)

---

### Post by azurepancake on 2008-06-21
Glad to hear its up and working! I'm sure you'll just need to tinker around a bit to solve the sound problem. 

If you can't hear anything from the client, it is possible it can be a problem with PulseAudio (the new sound driver for Ubuntu). Here is a link for your reference [http://ubuntuforums.org/showthread.php?t=776739/](http://ubuntuforums.org/showthread.php?t=776739/).

To thank people, just click on the little star on the bottom-right corner of a users post. 

Good luck

---

### Post by slaming on 2008-07-09
also trying to set up a ts server but i followed theinstructions on the link and i can't gte the passwords i installed it manually early (well i mean out of terminal) and i can get the passwords fo that but not this
 its just the other one doesn't wokr

---

### Post by azurepancake on 2008-07-12
> **slaming said:**
> also trying to set up a ts server but i followed theinstructions on the link and i can't gte the passwords i installed it manually early (well i mean out of terminal) and i can get the passwords fo that but not this
 its just the other one doesn't wokr

Hmm.. If I am understanding you correctly, it should work with no problem. Perhaps we should start from scratch?

First I'd recommend completely removing the program. Try this in terminal..

```
sudo apt-get remove --purge teamspeak-server
```

Then clean up any unnecessary packages, if there are any..

```
sudo apt-get autoremove
```

Now the application should hopefully be completely removed. Lets now reinstall the program..

```
sudo apt-get install teamspeak-server
```

The TeamSpeak server is now installed. Now it only needs to be configured. Like I stated in a previous post, it can be configured two ways. Through a raw configuration file or through your favorite browser, like FireFox.

To do it through the browser, your going to need the password. This can be found in the '/etc/teamspeak-server/passwords' file. Type the following into a terminal session to view it..

```
cat /etc/teamspeak-server/passwords
```

This will output the files contents to the terminal. Your password will be displayed. Now that you have the password, you can access the servers browser configuration. 

Open up FireFox and type the following into the URL bar..

```
http://127.0.0.1:14534/
```

The log-in menu should appear and you can enter in your credentials to configure your server. 

I hope this helps you. Good luck!

---

