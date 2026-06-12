---
title: "Switching from Windows xp to Ubuntu for some server: Ran into some problems"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by lyianx on 2013-06-30
Greetings all. 

I'm pretty new to Linux and decided when i built my new home server to replace my aging one, that i would use Linux to control it instead of Windows. The big disadvantage to this for me is of course, the learning curve and seemingly the lack of support. 

Im having display and sound issues, but nothing that i cant put off till later (its on a generic display driver so the resolution is crap). The Key things i want to get going are the servers i currently have running on my XP box. Namely Teamspeak 3 and Trackmania. My first hurdle is getting TS3 server up and running. Ive seen mixed instructions that are rather confusing and wasnt sure if their was something more offical. What few youtube vids i could find are in another language so i cant really follow them.

Im running 13.04 (desktop version, not server cause im a noob) on a brand new machine. I have 2 WD Red 3tb drives on the way that will be for file storage (aka NAS) and plan to add Squid at a later date as well as setup an FTP server for remote access.

But as i said, my first step is the TS3 server. If anyone could help, that would be great. 

Thanks

---

### Post by oldfred on 2013-06-30
Are those Windows games? That is one thing that has not worked in Linux. Some games are now being ported to Linux. Most will not work in wine, so forget about that. One alternative may be to run a virtual install of Windows.

       Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)
[http://www.linuxalt.com/](http://www.linuxalt.com/)


 Linux is not Windows:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

   Ubuntu is not Windows
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by lyianx on 2013-06-30
Teamspeak 3 isnt a game, its a voice chat program. There is a Linux version of the server, which i have downloaded and extracted, but right now its just a bunch of files. 

Trackmania i havent looked much into yet cause im focused on TS3, but yes it is a windows game, tho im not sure if the server itself requires windows or not (its just a server, it doesnt 'run' the game itself to host).

---

### Post by oldfred on 2013-06-30
I use synaptic & looked.

It came up with this in the Ubuntu software repository which then makes it easy to install. Both server & client were shown.

teamspeak-server (2.0.24.1+debian-1.1ubuntu1)

> TeamSpeak is a quality, scalable application which enables people to speak
with one another over the Internet. TeamSpeak consists of both client and
server software

---

### Post by ikt on 2013-06-30
> **lyianx said:**
> Teamspeak 3 isnt a game, its a voice chat program. There is a Linux version of the server, which i have downloaded and extracted, but right now its just a bunch of files.

Coming from a windows world you expect to download all your programs from random executables spread all over the web and download.com etc, in linux land you have repo's which have all the programs we generally need with a few exceptions, you can see all the programs available in the Ubuntu Software Centre, but in this case Team Speak 3 specifically isn't available from the repo, so we're going to have to do it the windows way.

You're going to need to know a tiny amount about the command line.

ls = list files
cd = change directory
And use TAB key to autocomplete the rest of the command/file/directory, for example once you extract the files from the tar.gz file (like a .zip), instead of typing cd ts3serveretcetcetc, just type ts3<TAB> and it will autocomplete the rest.

So here is the commands I used to run it, however this will not fully install it, this will just get it running.

[IMG]http://ikt.id.au/blog/wp-content/uploads/2013/06/installts3.png[/IMG]
[IMG]http://ikt.id.au/blog/wp-content/uploads/2013/06/installts32.png[/IMG]

Red box is just for emphasis.

Final result: (using the linux team speak 3 client)

[http://ikt.id.au/blog/wp-content/uploads/2013/06/connectedoknp.png](http://ikt.id.au/blog/wp-content/uploads/2013/06/connectedoknp.png)

I would do the above, (then you should be able to see what the admin "privilege" key is, and you can connect to your team speak server when you put in your servers IP address into a Team Speak client, which I can only assume is running on your windows desktop.

Hit CTRL+C to stop the program running in terminal, and to get it running in the background, do "./ts3server_startscript.sh start" instead of ./ts3server_minimal_runscript.sh and you'll not get any screen output, you'll need to look at the logs in the logs folder but your Team Speak server is now running in the background, now you just need to find a way to get ubuntu to automatically do ./ts3server_startscript.sh start when you start the PC, but that's something else entirely :P

---

### Post by HermanAB on 2013-07-01
Rather use Mumble and Murmur instead.  The packages should be in the software installer.

---

