---
title: "HOWTO: Read UPnP Media Server with another computer using djmount"
date: 2008-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by itix on 2008-05-03
djmount is a program that will mount a media server to your system just like any other file system. It's perfect for small laptops on which you can't store music but still want to be able to play media like movies, pictures and music from (that's the exact reason why I battled, learned and shared this with you).

That means, if you have one computer with a fairly large hard drive with a lot of media, that computer can act as a media server (don't worry, It won't render your computer inoperable). That way, all other computers in the local area network can access this computers media files through your network.

First of all you need a good media server. If you don't have any good media server, you can try MythTV or as I would reccommend: MediaTomb (installing instructions can be found [**here**]("http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/"))

Enough rambling for now, let's get going.

**1) Download and install FUSE**
FUSE is required by djmount to function properly. To be exact, djmount is actually built upon FUSE but with a simpler interface.

Download FUSE from [COLOR="Silver"]**[here]("http://sourceforge.net/project/showfiles.php?group_id=121684&package_id=132802")**[/COLOR]. Extract FUSE to some convenient location like your home folder. Open a terminal and navigate to where you extracted your archive (if you extracted them in your home folder, no change is needed). Navigation is done via the command [COLOR="Green"]*cd*[/COLOR] which means change directory. [COLOR="Green"]*cd ..*[/COLOR] (cd space period period) will take you to a higher level in the folder tree and [COLOR="Green"]*cd [COLOR="Navy"]directoryname[/COLOR]*[/COLOR] will take you to the folder named [COLOR="Navy"]directoryname[/COLOR]. For seeing which files and folders are contained in the current location, type [COLOR="Green"]*ls*[/COLOR].

Type [COLOR="Green"]*cd fuse-2.7.3*[/COLOR] and hit enter (or if you have another version, swap "2.7.3" to that version). Type [COLOR="Green"]* ./configure*[/COLOR]. You'll see a lot if text rolling up the terminal by now. If you get errors at this stage, see footnote 1). When that text is done (and hopefully without errors) type [COLOR="Green"]*sudo make*[/COLOR] (and enter your password... don't worry about not seeing character representation like stars or dots, it's designed that way) and more text will run up the terminal. When that text is done rolling up the screen (again hopefully without errors), type [COLOR="Green"]*sudo make install*[/COLOR].

If these procedures succeeded, you have now installed FUSE.

**2) Downloading and installing djmount**
djmount is the actual program that will mount your media server on to your local computer. That means that it will link a directory of your choice to the media server's index which make the folder look like it's full of media files even though they're on a different computer.

Download djmount [COLOR="Silver"]**[here]("http://sourceforge.net/project/showfiles.php?group_id=142039&package_id=155981")**[/COLOR]. Now we need to repeat what we did with FUSE. Extract your archive to a convenient location. Navigate to that location through the terminal. Type [COLOR="Green"]*cd djmount-0.71*[/COLOR] (or if you have a different version, change 0-71 to that version). Type [COLOR="Green"]*./confiure*[/COLOR]. Wait until it is done and type [COLOR="Green"]*sudo make*[/COLOR]. Now wait until it's done again and type *sudo make install*.

You have now installed djmount

**3) Using djmount**
First start up your media server. Then go to the terminal. Type [COLOR="Green"]*modprobe -l -t [COLOR="Navy"]the-directory-you-want-to-have-your-mediaserver-in[/COLOR] fuse*[/COLOR]. Then type [COLOR="Green"]*djmount [COLOR="Navy"]the-directory-you-want-to-have-your-mediaserver-in[/COLOR]*[/COLOR].

DONE! You can now navigate to *[COLOR="Navy"]the-directory-you-want-to-have-your-media-in[/COLOR]* either by terminal or with thunar/nautilus/konqueror (your file browser) and use the media from there.

**4) Autostart (optional)**
*Regular Ubuntu: Go to *system => Preferences => Sessions*, click add, type a name (like UPnP or MediaServer) in the name section, in the command section, enter [COLOR="Green"]*sleep 20 && modprobe -l -t [COLOR="Navy"]the-directory-you-want-to-have-your-media-in[/COLOR] fuse && djmount [COLOR="Navy"]the-directory-you-want-to-have-your-media-in[/COLOR]*[/COLOR], and optionally enter a comment in the comment section

*EeeXubuntu: go to *applications => settings => autostarted applications*. Type a name (like UPnP or MediaServer) in the name section, in the command section, enter [COLOR="Green"]*sleep 20 && modprobe -l -t [COLOR="Navy"]the-directory-you-want-to-have-your-media-in[/COLOR] fuse && djmount [COLOR="Navy"]the-directory-you-want-to-have-your-media-in[/COLOR]*[/COLOR], and optionally enter a comment in the comment section.


**5a) Cleaning up**
The folders you extracted is no longer needed. They can't be deleted directly since you have fiddled around with them as something called root (one can say that it is an administrator). That makes root the owner and you are not allowed to edit or delete them. The easy way to fix this is to us the terminal where you put the previous commands and type [COLOR="Green"]*sudo [COLOR="Navy"]your file browser[/COLOR]*[/COLOR]. On regular ubuntu (not kubuntu or xubuntu) that file browser is *nautilus*, and on xubuntu it is *thunar*, and on kubuntu it is *konqueror*. Now you are in the root browser and can delete the files easily. Your home folder is located in the *home* directory.


**5b) Alternative cleanup**
This can also be fixed by navigating in the terminal to the folder directly above the djmount folder and type *sudo chown -R djmount-0.71*. chown changes the ownership of an item. -R means recursive (i.e. the folder, all it's subfolders and files). sudo means "as root, do". If you have a different version, just change 0.71 to that version. 
Now the repeat procedure for the FUSE folder but change djmount-0.71 to fuse-2.7.3 (again if you have a different version, change 2.7.3 to that version).

Happy watching/listening =)





**Footnotes**
1) You might encounter problems with your C compiler. It'll say something like "[I]configure: error: C compiler cannot create executables
See `config.log' for more details.[/I]". If so, install the rather huge package [COLOR="Green"]*build-essential*[/COLOR] from the synaptic package manager.

2) If you find the password thingy difficult and would like to keep track of how many characters you've entered, just swap [COLOR="Green"]*sudo*[/COLOR] for [COLOR="Green"]*gksudo*[/COLOR].

3) The folder paths can easily be obtained by navigating to them in your file browser and pressing *[COLOR="Green"]ctrl + l[/COLOR]*

4) Most MediaServers work with sony's PlayStation 3, and so will MediaTomb to which I linked above.

**Credits**
Thank you:

__________________________________________________________
*Rob-e for solving the almost unsolvable autostart-problem
__________________________________________________________

*Fixman for the C compiler help
*linuxowns@wordpress for the media server instructions.
*joshsmith for helping dumb 'ol me with my fight against the Synaptic pkg mgr on my Eee when I didn't realize that the problem was that it tried to fetch the package from the CD

Some credit goes to the slightly incomprehensible offical installing and using instructions which can be found [[COLOR="Silver"]here[/COLOR]]("http://fuse.sourceforge.net/") and [[COLOR="Silver"]here[/COLOR]]("http://djmount.sourceforge.net/").

---

### Post by say2sky on 2008-05-04
sshfs+fuse can used to mount remote directory to local machine and play media file on it. I think the djmount method should have some difference feature but I don't know what is the difference between them.

---

### Post by itix on 2008-05-04
I don't either but this works wonderful for me ;)
It has the option of searching for playlists and showing only playlists which might make it easier for non library base media players to find and play music.

---

### Post by itix on 2008-05-04
idk what sshfs does, but don't you need to know the exact hostname and stuff to do that?
A good media server creates folders called audio, video and picture like my mediatomb server. Those are quite easy to access...
This is sort of the lazy mans method I think.

---

### Post by say2sky on 2008-05-04
> **itix said:**
> I don't either but this works wonderful for me ;)
It has the option of searching for playlists and showing only playlists which might make it easier for non library base media players to find and play music.

Using sshfs indeed need to know IP or hostname of machine on which media file is stored. 

So the djmount don't want client/player know the server IP/hostname because it use UPnP, is that right?

---

### Post by itix on 2008-05-04
That is probably the right way to interpret the differences. It doesn't require any root access and it doesn't need a login on a different host, but it's also restricted to the local network. You can't find a media server in your neighbors apartment unless you're on the same network.

With your method, one might mount a folder to the local machine from the other side of the world if necessary.

---

### Post by trickyD on 2008-05-11
I've got fuse and djmount working ok. Works a treat with Twonkyvision on my NSLU2 at home, there's just one thing that I'm struggling with and that's to get it to mount at boot.

I've added a line to /etc/fstab and verified it with mount -av, but it just won't mount on boot.

Was thinking that it was something to do with the way that mountall.sh in /etc/init.d works, but I've drew a blank.

Any ideas - running 8.04 at the moment.

Ta,

TD.

---

### Post by itix on 2008-05-11
Yeah, thanx buddy, I have the same problem myself. I have been fighting for weeks now with all sorts of different methods. I have no idea why it won't work.

I was going to extend this with a "lauch at startup"-part but I wanted to get it working first. I have tried all sorts of diffrenet things like modifying rc.local, editing the "official" startup-launcher of xfce4 and a desktop launcher which didn't work. It feels good that I'm not the only one with this problem (not to be mean or anything ;) )

Here is the thread i started on the subject: [http://ubuntuforums.org/showthread.php?t=778901](http://ubuntuforums.org/showthread.php?t=778901)

---

### Post by Rob-e on 2008-05-23
hey, thanks for the tut, it worked nicely

i think the problem youre having with mounting it on boot, is that the network isnt running and connected when you run the program, insted of putting 1 command in the command box, i just wrote a bash script... notice that it waits for 20 seconds first, and this works perfectly

```

#!/bin/bash

sleep 20
modprobe -l -t /home/rob/upnp fuse
djmount /home/rob/upnp

```

you could probobly use something like "sleep 20 && modprobe -l -t /home/rob/upnp fuse && djmount /home/rob/upnp

let me know how it works

---

### Post by itix on 2008-05-23
Nice ;)
I'll add that to the original howto straight away.

---

### Post by itix on 2008-05-24
Sorry pal. Can't comprehend Chinese.
I do know some Japanese kanji though...

---

### Post by billgoldberg on 2008-06-06
For those intrested, I did a post on it yesterday in my blog, simple copy/paste work, could be easier to follow then this.

[http://linuxowns.wordpress.com/2008/06/05/accessing-upnp-server-from-ubuntu/](http://linuxowns.wordpress.com/2008/06/05/accessing-upnp-server-from-ubuntu/)

---

### Post by itix on 2008-06-06
I've found something that might be of interest to people. It's an option called -f to djmount that makes it a foreground application rather than a deamon. It's good for debuging and analyzing since it says exactly what it's doing. You can also shut it down by pressing *ctrl + c* by using it as a foreground app.

[COLOR="Green"]*modprobe -l -t /home/examplepath fuse && djmount -f /home/examplepath*[/COLOR] is the way to use it.

EDIT: However, you can't shut your terminal down after having entered the line of code since it will kill djmount by doing so.

---

### Post by jonnywombat on 2008-09-25
Many thanks :guitar:

I have been wasting a lot of time trying to stream media between two hardy machines... this works perfectly, apart from the autostart on boot... Firstly I had a typo..but then still not working..but if I copy and paste command minus the sleep 20 && bit it works fine.. 

Thankyou again

---

### Post by fastpakr on 2008-09-25
Hmm...

I can step all the way through mounting the media servers with the djmount command, and see them when I run an 'ls' command on the mount folder.  However, the servers themselves show no files whatsoever.  Not sure what's going on - I can connect to the devices with the PS3 just fine, but with djmount they don't appear to be sharing anything.

Any ideas what I'm missing?

---

### Post by jonnywombat on 2008-09-25
ok got this to auto start now... this is how i did it

first created a script in my favorite text editor that looked like this

> #!/bin/sh
sleep 50 && modprobe -l -t /home/jonny/Streams fuse && djmount /home/jonny/Streams

I increased the sleep time because sometimes it takes a while for my laptop to establish a wireless connection

I then save this file as startstream.sh and made sure it is in my home folder

and the in terminal ran

> chmod 777 startstream.sh

to make it executable

then I went to sessions and added a new start item.

I called it start stream for the command I entered 

> ./startstream.sh

this works like a charm.. where the method in the how-to did not work for me.

jonny

---

### Post by bluesmoke on 2008-10-28
Hi, 

   I have installed djmount on my ubuntu pc. I like its feature which allow user to select the favorite player.

 But the problem I am facing is ...It detects my Media server (Mediatomb) and I can play the files but after some time it is (media server) erased (do not know why) from the mounted directory. and then It again comes on display but only for a short interval......

Can any body have solution

---

### Post by itix on 2008-10-28
It might be that your router is to slow and won't allow large transfers. I had this problem as well. Whenever I lost connection with the network, I had the same problem as you.

It has to do with the network, I'm fairly sure since my PS3 loose contact with MediaTomb every now and then as well...

---

### Post by bluesmoke on 2008-11-06
Hi,
 
  I am running djmount on a Ubuntu pc whic is acting as an Access Point (and hence connected with two networks A and B). The problem is I can see the UPnP devices on Network A but cannot see at network B (My target UPnP server is at network B). Even when i put the network A down (by #ifdown eth0), network B cannot be mounted.

I want to mount both networks or at least Network B. Any suggestion is strongly appreciated

---

### Post by Jose Catre-Vandis on 2009-07-07
This works very nicely, and I see that GeeXBox uses djmount to access uPnP shares as well.

In a world of connectivity, it strikes me as odd that there is very little in the way of programs or scripts for accessing media in this way, as it is so simple. I am even more incredulous that there doesn't really appear to be anything for a Windows (XP) machine (for free) to use to access uPnP.

I use ushare as the server, very simple as well once up and running, and much less taxing than mythtv or mediatomb.

Thanks **itix** for this howto.

---

### Post by fouserge on 2009-07-25
> **bluesmoke said:**
> Hi, 

   I have installed djmount on my ubuntu pc. I like its feature which allow user to select the favorite player.

 But the problem I am facing is ...It detects my Media server (Mediatomb) and I can play the files but after some time it is (media server) erased (do not know why) from the mounted directory. and then It again comes on display but only for a short interval......

Can any body have solution


I'm having this same problem and I'm quite sure that it's not my router being to slow b/c my ps3 has no problems. I loose the Mediatomb folder within like 3 minutes and it doesn't matter whether I'm streaming anything or not.

Also I found a fix for the whole startup process in this tutorial:
[http://linuxowns.wordpress.com/2008/06/05/accessing-upnp-server-from-ubuntu/](http://linuxowns.wordpress.com/2008/06/05/accessing-upnp-server-from-ubuntu/)

which leads you here for a script that starts up djmount when the network is established:
[http://michael-peeters.blogspot.com/2008/06/upnp-client-under-ubuntu-djmount.html](http://michael-peeters.blogspot.com/2008/06/upnp-client-under-ubuntu-djmount.html)

So now that I have the script that starts up djmount when the network is established I can bring back my Mediatomb folder by turning my network off then on again but I want a more permanent solution.

---

### Post by ugm6hr on 2009-07-26
> **Jose Catre-Vandis said:**
> In a world of connectivity, it strikes me as odd that there is very little in the way of programs or scripts for accessing media in this way, as it is so simple. I am even more incredulous that there doesn't really appear to be anything for a Windows (XP) machine (for free) to use to access uPnP.

XBMC can access UPnP servers.

---

### Post by Jose Catre-Vandis on 2009-08-08
> **ugm6hr said:**
> XBMC can access UPnP servers.

Bit of a sledgehammer to crack a nut though :P

---

### Post by GixerPoD on 2010-04-18
> **fastpakr said:**
> Hmm...

I can step all the way through mounting the media servers with the djmount command, and see them when I run an 'ls' command on the mount folder.  However, the servers themselves show no files whatsoever.  Not sure what's going on - I can connect to the devices with the PS3 just fine, but with djmount they don't appear to be sharing anything.

Any ideas what I'm missing?

This is a fault that affects a library used by djmount when running on a 64-bit machine. This is the fault referred to by the thread [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1352727](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1352727) which may help you.

---

### Post by naveenhg on 2010-07-19
Hi All,

I'm new to this djmount and the process. So please bear with my naive questions.

I've installed the djmount and able to browse through the contents/files in the mounted directory. But my next step is to select a particular file to play in a player.

So I would like to know, how to select a particular player/renderer in the network and also how to issue a command for the play??

Please let me know.

Thanks,
Naveen

---

### Post by locketine on 2010-09-14
With Ubuntu 10.10, all I had to do was install djmount using the Ubuntu Software Center, make a directory to mount to and then run:

```
djmount MyMediaDirectory
```

---

### Post by kcdgbc on 2010-12-22
> **fouserge said:**
> I'm having this same problem and I'm quite sure that it's not my router being to slow b/c my ps3 has no problems. I loose the Mediatomb folder within like 3 minutes and it doesn't matter whether I'm streaming anything or not.

Also I found a fix for the whole startup process in this tutorial:
[http://linuxowns.wordpress.com/2008/06/05/accessing-upnp-server-from-ubuntu/](http://linuxowns.wordpress.com/2008/06/05/accessing-upnp-server-from-ubuntu/)

which leads you here for a script that starts up djmount when the network is established:
[http://michael-peeters.blogspot.com/2008/06/upnp-client-under-ubuntu-djmount.html](http://michael-peeters.blogspot.com/2008/06/upnp-client-under-ubuntu-djmount.html)

So now that I have the script that starts up djmount when the network is established I can bring back my Mediatomb folder by turning my network off then on again but I want a more permanent solution.

Has anyone found a solution to this problem. I've been trying to use djmount with MediaTomb as well and I too am seeing the directory dissapear after 3 minutes. 

I have seen in the debugging output from djmount that MediaTomb has an expiration of 180 (assumming seconds that's 3 minutes) but I have found no way to have djmount either ignore this expiration time or to refresh when the time is up.

Also, djmount behaves the same with my other media server: MythTV has an expiration of 3600 and it's directory dissapears after an hour.

Has anyone else experienced this prolem, or perhaps know what I may be doing wrong?

---

