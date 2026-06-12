---
title: "Need help installing GeeXboX (media server for xbox 360)"
date: 2007-09-29
forum: Other OS Talk
---

### Post by blazini on 2007-09-29
I came across this media server app that's supposed to work with the 360, but the installation stuff is a little over my head. There are other apps reqiured for it to work that are listed on the site. 

[http://ushare.geexbox.org/]("http://ushare.geexbox.org/")

tia

---

### Post by RKCole on 2007-09-29
Hello.

I just installed the latest version of uShare on my system.  I'll map out what I did here, and hopefully it will help you out.  I'm not sure how far along you are, so I'll start from the beginning.

**Step 1**
Install the **build-essential** package which contains (usually) all necessary components for building packages from source.  All of the following commands must be executed in the Terminal (Applications->Accessories->Terminal)

```

sudo aptitude install build-essential

```

**Step 2**
Download the latest version of uShare from the site [here]("http://ushare.geexbox.org/").  The file is a compressed archive (.tar.bz2) which contains the source code of the uShare program.  I'd recommend extracting any archived files to the /usr/src directory.  some do this differently, but it's just easier to remember for me.  IN the terminal, change to the directory where you saved the ushare file (we'll assume it's saved on the desktop for the sake of this writing):

```

cd Desktop

```

Now extract the uShare archive to the /usr/src directory.

```

sudo tar -C /usr/src -jxvf ushare-1.0.tar.bz2

```

This will create a ushare-1.0 directory in the /usr/src directory.

**Step 3**
Download the file **libupnp-1.6.0.tar.bz2** from [here]("http://sourceforge.net/project/showfiles.php?group_id=166957&package_id=189913").  Follow the procedure in step 2 to extract the contents of this file to the /usr/src directory.

**Step 4**
Now it's time to compile libupnp.

First, change to the extracted libupnp directory in /usr/src/

```

cd /usr/src/libupnp-1.6.0

```

Run the **configure** script in this directory, telling it to install to the /usr/lib directory:

```

./configure --prefix=/usr

```

Make and install libupnp with the following commands:

```

make
sudo make install

```

**EDIT**
libupnp is installed into the /usr/local/lib directory, however we need it to be in the /usr/lib directory in order for uShare to work.  Use the following command to copy the file **libupnp.so.3** to /usr/lib/:

```

sudo cp /usr/local/lib/libupnp.so.3 /usr/lib/

```


**Step 5**
Now we'll get ready to compile ushare.  I don't knwo if this necessarily has to be done, but I did it anyway just in case--before going to compile ushare, update teh system database:

```

sudo updatedb

```

IF my knowledge is correct, this command updates the system so it is aware of various changes, such as new applications and such.

Now, change to the ushare-1.0 directory

```

cd /usr/src/ushare-1.0/

```

Run the following commands in succession to compile and install ushare.

```

./configure --prefix=/usr
make
sudo make install-strip

```

If all goes well, you should now have an installation of uShare on your computer.  This is a command-line based utility, so I'd recommend looking over the ushare manpage by using

```

man ushare

```

It's not too hard to configure, and it works very well with the Xbox 360.

Hope this helped you out.

Take care.

---

### Post by blazini on 2007-09-29
Thanks for the info, it was very helpful. I didn't even start to install it before I posted, so it'sd good you started from the beginning. The only hiccup I ran into was when you said "libupnp is installed into the /usr/local/lib directory, however we need it to be in the /usr/lib directory in order for uShare to work. Use the following command to copy the file libupnp.so.3 to /usr/lib/:"

libupnp.so.3 was not in /usr/local/lib, it was already in /usr/lib after I completed the previous steps, so there was nothing to copy. I'm pretty sure it installed correctly, I didn't get any errors after that.

I just can't figure out how to use it, I tried the manual, but I'm still lost. I've never used a media server before let alone a Linux one. When you say "command line" I figure you mean running scripts in the terminal, but I'm not sure where to start, an example would be helpful. I'm not sure how the 360 will recognize it either. If I could just get started I'm sure I could figure the rest out on my own

---

### Post by RKCole on 2007-09-29
No worries, blazini.  I'll help you as much as you need, and as much as I can.  I'm still (in my mind) not yet an advanced user, but I've messed with uShare a little, so I'll do what I can to help.

Oh...that's weird about the libupnp.so.3 file...Mine installed to /usr/local/lib.

Okay...there are basically a few options that we use with uShare to set it up to stream things to the Xbox 360.  For mine, I typically use the options: **-n, -p, -c, **and **-x**.  Here's what all of those mean:

**Name (-n)**  This is basically what you want the server to be seen as, or named...I use something like HomeServer.  The default is uShare, so if you'd like to leave ti as uShare you can exclude the -n option when running the command below.

**Port (-p)**  This will set a specific port for uShare to use.  uShare usually uses ports above 49152.  If you exclude this option, uShare will randomly use a port above 49152; I usually set the port to 49153 so I know what port it's running on.

**Content Directory (-c)**  This option will tell uShare which directory your content to be streamed/shared lies.  My content is located in (keep in mind that my partitions may be different compared to yours) **/share/Media/**.

**Use Xbox 360 Compliant Profile (-x)**  This one's pretty self-explanatory.  It just tells uShare to use a profile which is compliant with the Xbox 360 profile standards (whatever they may be).

So, to get this all up and running, you would run the following command in a terminal:

```

ushare -n HomeServer -p 49153 -c /share/Media/ -x

```

You will have to keep the terminal window open in order to keep ushare going.  You could alternative create a launcher icon on your Desktop that will start uShare when you double-click it.  To do this, simply right-click on your Desktop and select the Create Launcher option.  In the **Name** field, just type in uShare.  In the **Command** field, just copy and paste the command from above.  And there you go!

Now, there is a Web interface that allows you to see some statistics about the server.  To get to this, simply open Firefox and go to the following address:

http://<your_ip_address>:<port_used_in_command>/web/ushare.html

there you go!

Hopefully this will get you up and running.  If you need any further help, please feel free to post back.  And if you get it all up and running, post back anyhow to let me know if you'd like.

Take care and good luck.

---

### Post by blazini on 2007-09-29
Hey thanks again. I have it working now. I set it to start up with the computer. I have to sort out the folder I'm gonna share, the 360 doesn't like the way its setup now. Too bad it doesn't do transcoding, the only videos the 360 wants to play are the type you can play directly on the 360.

---

### Post by DaQdino on 2007-10-01
Hi to everyone! This is my first post, and sorry for my english (it's not my first language)  :)

However...

You are great RKCole!

I was searching for a guide like this by days! It works!
But there are a few questions:

in the Xbox 360 a see a list of songs with their file name (not with the id3 tag), and the list is of only 1000 songs, while i have a lot more...

Is there a solution for having all my songs in the list and seen with their id3 tag?

---

### Post by RKCole on 2007-10-01
DaQdino,

I'm not quite sure as to a solution to your issue.

When you start uShare in a terminal, it should tell you how many files/directories it finds.  Can you list that in a concurrent post?

blazini, hopefully one day they'll have something which does on-the-fly transcoding.  Would be nice.

Well, there IS a program called [Fuppes]("http://fuppes.ulrich-voelkel.de/") which seems to support on-the-fly transcoding, but I haven't compiled/tested it yet.  As soon as I get some time, I'll test it out and write back...No guarantee on how long ti will take me, though...Maybe this weekend I'll have a bit of spare time.

Thanks for the compliment on that guide, DaQdino.  Think I should go into writing documentation? (haha)  Nah..I just like to help when I can and when I have the knowledge to do so.

Take care.

---

### Post by DaQdino on 2007-10-02
This is what appear on the terminal

```
uShare (version 1.0), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on XX.XX.XX.XX:49155
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/HD2/Mp3/
Found 10736 files and subdirectories.

```

While on the 360 there are only 1000 songs...

---

### Post by RKCole on 2007-10-02
DaQdino,

It looks as though, right now, uShare has a 1000 file limit for the Xbox 360.  I'm sure this is something which will be changed soon enough.

---

### Post by DaQdino on 2007-10-02
Thanks for the answer.

Now i'm trying to compile Fuppes and see what it does.

---

### Post by aldenhg on 2007-10-11
It appears that ushare's 360 support is pretty rudementary at this point. I don't know what their release cycle is like, but hopefully it'll get better soon.

---

### Post by Timsy321 on 2007-10-31
Just wondering if anyone could help me out. I have everything installed and my xbox can read the folder. But i can't play any of the media. Not even mp3s or mp4 movies. I can see all of them, but i think i may be missing something. Thanks!

---

### Post by UrBaNAcID on 2007-12-24
Hey i was only wondering if it was possible to share more than one directory or are you limited to one.. For some reason im able to stream videos okay but if i attempt to stream both vids and mp3s from the same folder i cant.. any input would be helpful Thanks

---

### Post by antoniuk on 2007-12-30
Just so everyone knows, usahre now has ubuntu debian packages
If you go to their site, they explain how to add everything. The run down is:

Put this in your software sources
```
deb http://www.geexbox.org/debian/ unstable main
```

run apt-get update

now run apt-get install for ushare, libdlna, and libupnp2 (which is already a package btw)

Once everyhting is installed, you simply edit /et/ushare.conf and modify it accordingly.

Finally do an /etc/init.d/ushare restart and you are good to go.

Now all you have to do is type 
```
ushare -x 
```
at the console (still have to do this unfortunately)

To view the web interface, it is http://<ip>:<port>/web/ushare.html

I have to hand it to these guys, they made it super simple.

---

### Post by aldihu on 2008-01-02
hi i have a problem with ushare. i got it installed and i think configured correctly. i can view the webinterface and add shares but in the terminal it says that the network interface is down. but that cant be the case because the internet and lan works perfectly.
ipconfig and ipconfig -a doesnt show an error either. the xbox doesnt find any shares.

and i dont know what to try next. any ideas?

edit:
i to it to work!

---

### Post by scaine on 2008-01-20
Just to add that I'm also seeing the "eth0 is down" message, like aldihu.  Anyone else seen this behaviour?

---

### Post by ahh_dee on 2008-01-24
I am having the same issue with eth being down. I tried installing it from source and from the repro and I am getting the same errors.

---

### Post by K.Mandla on 2008-01-24
Moved to Other OS Talk.

---

### Post by fenrir12 on 2008-01-24
I also get that eth0 down message, however, it doesn't seem to effect the xbox from reading everything in the files I've shared. I've encountered two minor issues. First, ushare seems to filter out .avi files, which I know it can play. I just renamed each file to end in a .wmv, and the 360 immediately picked them up and started playing them. Also, even after editing the .config file to try and share multiple folders, it will only share the first folder I put in.

---

### Post by David Mulligan on 2008-01-27
I found the answer here: [http://ubuntuforums.org/showthread.php?p=4181463](http://ubuntuforums.org/showthread.php?p=4181463)

The problem is the configuration file at /etc/ushare.conf needs to be edited with your configuration information.

---

