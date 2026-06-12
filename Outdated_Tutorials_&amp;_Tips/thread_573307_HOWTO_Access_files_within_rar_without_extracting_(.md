---
title: "HOWTO: Access files within rar without extracting (perfect for video streaming)"
date: 2007-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by andreeh on 2007-10-11
This is a guide on how to grab files inside a rar archive without actually extracting them (perfect for video streaming)
**Disclaimer**: I'm not responsible for your system, everything in here is done by you and you're responsible for the things that might happen to your system.
Comments on how to make this guide better is very welcome, since I'm not all that good on user permits and these commands might compromise your system security (although I'm almost 100% it shouldn't).

Get the required packages (note that fuse-utils probably already is installed)
```

sudo apt-get install subversion automake1.9 fuse-utils libfuse-dev

```

Get the source code for our main attraction rarfs, which is a virtual filesystem based on fuse
```

svn co https://rarfs.svn.sourceforge.net/svnroot/rarfs/trunk/rarfs/ rarfs

```

Lets build that code!
```

cd rarfs
./configure
make
sudo make install

```

Since fusermount comes pre-installed as root-only, we need to change group owner and execution permits.
First off, add your user to the "fuse" group.
**NOTE:** The user need to relog to update it.
```

sudo adduser <user> fuse

```

Next up, make the group "fuse" owner on these fukes so we can access them.
```

sudo chgrp fuse /dev/fuse
sudo chgrp fuse /bin/fusermount

```

Make fusermount command available to users
```

sudo chmod u+s /bin/fusermount

```

Now try
```

mount.fuse rarfs#/location/of/.rar/file /my/mount/dir

```
If no errors appear, you're all set!

You can unmount your rars by typing
```
fusermount -u /my/mount/dir
```

Here's a basic script that I'm using to just right click those .rar files and stream them directly.
```

#!/bin/sh
DIR=/home/`whoami`/rar.mount/
mount.fuse rarfs#$1 $DIR
gmplayer -fs -zoom $DIR`ls $DIR`
fusermount -u $DIR

```

Good luck! :P

Edit 1: Fixed typos and such.

---

### Post by bshakil on 2008-04-26
very good tutorial ... Works Perfect under linux...

Just a question...

I mounted a rar Archive to a Folder /media/sda1/rardrive
and i also added this Folder in smb.conf ...

But its not accessible... It keeps on asking the password if an archive is mounted ..
if i umount the archive .. i can access the Empty Folder

---

### Post by hardik123 on 2010-01-25
thanks for help but i cant understand how to mount multiple rar archive ?:confused:

---

### Post by hardik123 on 2010-01-25
> **hardik123 said:**
> thanks for help but i cant understand how to mount multiple rar archive ?:confused:

thanks its now work with multiple archive also :popcorn:

but may be your script not mount and play file #!/bin/sh

---

### Post by hardik123 on 2010-01-25
I found the way just add script copy in terminal 
```
gedit ~/.gnome2/nautilus-scripts/Mount

```
and past this code change path as your this add mount to your rar in right click menu and play on player you like
```

#!/bin/sh
DIR=/home/'your name'/Desktop/rar
mount.fuse rarfs#$1 $DIR

```
Save and close the gedit window, and then execute the following command to make the script executable:
```
chmod u+x ~/.gnome2/nautilus-scripts/Mount
```

For unmont
```
gedit ~/.gnome2/nautilus-scripts/Unmount

```


This will add Unmount script add in right click
```
#!/bin/sh
DIR=/home/hardik/Desktop/rar
fusermount -u $DIR
```

Save and close the gedit window, and then execute the following command to make the script executable:
```
chmod u+x ~/.gnome2/nautilus-scripts/Unmount
```

---

### Post by JBAlaska on 2010-01-25
If you want to view and stream avi's from inside rar's..Just use VLC Player.

---

### Post by MattiJ on 2010-02-28
Very useful thanks!
There is a segfault on some rar's and here is the fix.
[http://bugs.gentoo.org/attachment.cgi?id=220703&action=diff]("http://bugs.gentoo.org/attachment.cgi?id=220703&action=diff")
```
	
char buf[4];
file->read(buf,3);

//for some rar files there are seeks past file end, then directly to file end
//which makes file->good() return true, but there is nothing to read
//so with file->gcount() we check if we actually read something
//otherwise we use old bufer and crash somewhere

if(file->gcount()==0)
break;
file->seekg (-3, std::ios::cur);				switch( buf[2] )

```

---

### Post by Gfy on 2010-07-07
This is how you get it working in openSUSE:

Get the required packages. Only one missing for me on openSUSE 11.2.
```
sudo zypper install fuse-devel
```

Grab rarfs-0.0.8.tar.gz or newer from [http://sourceforge.net/projects/rarfs/files/](http://sourceforge.net/projects/rarfs/files/) and extract it.

Build and install the code. (see first post)

No need to mess with users and permissions. Also for Ubuntu 10.04 this isn't necessary anymore.


For easy access in Nautilus, see the post from hardik123, but place this in the two files:

```
#!/bin/sh
DIR=/home/`whoami`/rarfs
/sbin/mount.fuse rarfs#$1 $DIR
```

```
#!/bin/sh
DIR=/home/`whoami`/rarfs
/usr/bin/fusermount -u $DIR
```

And the same changes for the original basic script:
```
#!/bin/sh
DIR=/home/`whoami`/rar.mount/
/sbin/mount.fuse rarfs#$1 $DIR
gmplayer -fs -zoom $DIR`ls $DIR`
/usr/bin/fusermount -u $DIR
```

The advantage of this method over VLC is that you can use whatever player you want. e.g. SMPlayer. Also, this tread is older than VLC had support for playing rars. If you still have an older VLC version, you can get the plugin here: [http://www.shapeshifter.se/code/vlc-unrar/](http://www.shapeshifter.se/code/vlc-unrar/)

You can also use this script and associate it as default program to open a rar file. If the rar file has a certain size, it will be opened with vlc. Otherwise the archival program will be used.

```
#!/bin/bash
#get the size of the file
SIZE=`stat -c %s "$@"`

#if the file is a rar file from a scene rar
if [[ "$SIZE" -eq 15000000 || "$SIZE" -eq 20000000 || "$SIZE" -eq 50000000 ||  "$SIZE" -eq 100000000 ]] 
then
	#play the rar file with vlc
	vlc "$@"
elif [ -f $1 ] #file exists and is a regular file
then
	#open the file with the preferred archival programm
	file-roller "$@"
fi
```

I recently switched to openSUSE on my laptop because of a couple of bugs I couldn't fix that I didn't have in hardy. VLC 1.1.0 often indicates an avi is broken while I had no problems with older vlc versions + the plugin. Thus I use rarfs to solve it.

---

### Post by NexX.swe on 2010-08-29
I keep getting errors when trying to compile

when i try *./configure*
```
config.status: error: cannot find input file: doc/Makefile.in
```

when i try *make*
```
nexx@lemur:~/rarfs$ make
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/home/nexx/rarfs'
Making all in .
make[2]: Entering directory `/home/nexx/rarfs'
make[2]: Leaving directory `/home/nexx/rarfs'
Making all in src
make[2]: Entering directory `/home/nexx/rarfs/src'
Makefile:297: .deps/archiveblock.Po: No such file or directory
Makefile:298: .deps/fileblock.Po: No such file or directory
Makefile:299: .deps/main.Po: No such file or directory
Makefile:300: .deps/markerblock.Po: No such file or directory
Makefile:301: .deps/rararchive.Po: No such file or directory
Makefile:302: .deps/rarblock.Po: No such file or directory
make[2]: *** No rule to make target `.deps/rarblock.Po'.  Stop.
make[2]: Leaving directory `/home/nexx/rarfs/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nexx/rarfs'
make: *** [all] Error 2

```

I'm running Ubuntu 10.04.1 LTS
please help.

---

### Post by Gfy on 2010-08-30
Do the files exist on your hard drive?
.deps/rararchive.Po ect.

Download the archive and try again.
If the files do exist, then the error message is not very helpful.

---

### Post by orrche on 2010-09-18
Use the tar.gz file instead of svn, gives lots less headaches while compiling

[https://sourceforge.net/projects/rarfs/]("https://sourceforge.net/projects/rarfs/")

---

### Post by fadec on 2010-12-18
Mounts/unmounts perfectly, but shows me rar-structure (directories) only, _**not files.**_

Rar-archive has internal fs codepage=866 so it's mounted with options:
**-o modules=iconv,from_code=866,to_code=UTF8**
and very long directory names (100 chars and more). 

Do you have any suggestions on automated long-names truncation or extraction of original long-names without cutting them off?

Link for that arch (just in case): [http://mo.uhta.net/gkh/files/Dom.rar](http://mo.uhta.net/gkh/files/Dom.rar)

What might be wrong? How to make FUSE to show file content of rar-arcs, not directories only?

What do you think about Archivemount [http://www.cybernoia.de/software/archivemount/](http://www.cybernoia.de/software/archivemount/)?

---

### Post by kll on 2011-07-27
Check out PyarrFS, it's a RAR reading filesystem written using FUSE which allow you to transparently read .rar files as they were directories. [http://labs.spritelink.net/pyarrfs](http://labs.spritelink.net/pyarrfs)

---

