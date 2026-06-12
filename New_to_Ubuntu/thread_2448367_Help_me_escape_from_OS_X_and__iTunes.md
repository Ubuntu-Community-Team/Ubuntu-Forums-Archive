---
title: "Help me escape from OS X and  iTunes"
date: 2020-08-06
forum: New to Ubuntu
---

### Post by willholmania on 2020-08-06
Hi. I've tried a couple of times over the years to leave Mac OS behind and switch to Ubuntu, but one thing always stops me. I have numerous playlists going back many years on iTunes, and I don't want too lose them. I currently use a Gigabyte MB based I5 Hackintosh that I've just rebuilt to run Mac High Sierra OS. I also have another Gigabyte machine running Mac Yosemite, but I could obviously stick Windows on it if this was deemed a necessary stage in transferring iTunes playlists into a format that something like Clementine could use. 

So my question is, does anyone know how I can export my iTunes library, keeping all the playlists intact, into a form that a music player that runs on Ubuntu can read? 

Any help would be greatly appreciated.

---

### Post by TheFu on 2020-08-06
You made the bed.

I've never used iTunes, but on every other platform a playlist is separate from the music files, so exporting and importing a playlist doesn't touch any music files.  Those have to be handled separately.  Not sure if iTunes works that way or not.

[https://www.wikihow.com/Export-an-iTunes-Playlist](https://www.wikihow.com/Export-an-iTunes-Playlist) has export instructions to an m3u playlist.

Most music players support the m3u/pls playlist formats.  That is just a list of files with either relative of absolute paths.  They are trivial to make on any Unix system.  Trivial.

```
posc:/R/Music/Rock/f/Foreigner/4$ ls > Foreigner-Four.m3u
```
Now that album has a playlist:
```
$ more *u
Foreigner-4-01-Night_Life.mp3
Foreigner-4-02-Juke_Box_Hero.mp3
Foreigner-4-03-Break_It_Up.mp3
Foreigner-4-04-Waiting_for_a_Girl_Like_You.mp3
Foreigner-4-05-Luanne.mp3
Foreigner-4-06-Urgent.mp3
Foreigner-4-07-Im_Gonna_Win.mp3
Foreigner-4-08-Woman_in_Black.mp3
Foreigner-4-09-Girl_on_the_Moon.mp3
Foreigner-4-10-Dont_Let_Go.mp3
Foreigner-4-11-Juke_Box_Hero_unplugged.mp3
Foreigner-4-12-Waiting_for_a_Girl_Like_You_unplugged.mp3

```
Pretty simple.   If I want a playlist for all Foreigner albums, 
```
posc:/R/Music/Rock/f/Foreigner$ find . -type f -iname \*3 | sort| tee Foreigner.m3u
```
Now Foreigner.m3u has a list of all files that end with a '3' character, relative path to each. For example:
```
./Records/Foreigner-Records-01-Cold_As_Ice.mp3 
./Records/Foreigner-Records-02-Double_Vision.mp3
...

```

I can randomize them, sort them, look for specific words in the title. Some music players will do that stuff too.  Unix is designed from the beginning for text processing and manipulation.  

BTW, some people keep all their music in a single directory.  That's a bad idea for performance and possible corruption issues.  100 files isn't a problem, but much more than 400 files and performance will suffer.  If the music tags are correct, we have tools that will create a directory structure and move the files into the correct location for us.  Or if the directories are correct, those can be used to set the id3 tags.

---

### Post by willholmania on 2020-08-07
Thank you TheFu. Your level of knowledge is clearly way ahead of mine so please bear with me. Yes, iTunes uses a central library with all the music files in it, and the playlists are xml files. So I guess I need to convert these to m3u files (Google tells me there are scripts to do this), import the library of songs to something like Clemetine (suggestions for the best music software are very welcome) and then add the playlists.

---

### Post by TheFu on 2020-08-07
It looks like iTunes has an export to m3u capability for playlists. That would be easier for point-n-click people.  

That isn't me. I use **cmus** as my music player. No GUI.  I tried Clementine, xmms, Amarock, and 20 others. For a long time, I'd just provide a playlist to mplayer or mpv (both nearly universal media players that run from a shell).  We are all different users.  Unix allows that flexibility.  ;)

---

### Post by willholmania on 2020-08-07
Any suggestions as to a suitable music player? All I need is the basic functions of iTunes - the ability to make and save playlists, and add them to my iPhone.

---

### Post by ActionParsnip on 2020-08-07
[https://www.groovypost.com/howto/howto/sync-your-iphone-or-ipod-touch-in-ubuntu/](https://www.groovypost.com/howto/howto/sync-your-iphone-or-ipod-touch-in-ubuntu/)

Possibly Rhythmbox.

Not an iPhone user as I use Ubuntu and Apple refuses to support the OS so I don't support them.

---

### Post by willholmania on 2020-08-08
My other issue is getting the pictures and albums out of Mac Photos and into a new photo manager. Can anyone suggest how I'd go about this?

---

### Post by TheFu on 2020-08-08
> **willholmania said:**
> My other issue is getting the pictures and albums out of Mac Photos and into a new photo manager. Can anyone suggest how I'd go about this?

I'd use **sftp**, **scp**, **rsync**.  Every popular file manager program on Linux supports using sftp:// in the URL to access local and remote stuff, assuming an ssh server is running on the other side.  It might be easier to install an ssh-server on OSX, then use Linux file manager to copy/paste the files and directories over.  For a few directories, that would be fine. 

If you have hundreds and thousands of files/directories, things can fail sometimes in the middle. It won't automatically restart where that failure happened.  That's why **rsync** is great. There is a GUI for rsync - **grsync**.

Every OS with networking has good sftp, scp, and rsync clients.

---

### Post by Quarkrad on 2020-08-09
I've been here myself so do sympathise.  Another way of looking at this is to install Virtualbox in Ubuntu and run a Win10 guest - then install itunes in win10 for your music. Temporarily set up a shared folder with the win10 guest and a folder outside virtualbox and transfer your itunes folder from your Windows environment to your ubuntu environment (there are a number a ways of doing this).  I use this set up myself - migrated away from native win10 to a win10 environment in virtualbox/inside Ubuntu and use itunes to manage my music that I play on a generic mp3 player. It works and saves all the investment you have put into itunes over the years.

---

### Post by TheFu on 2020-08-09
Can't believe I didn't mention this - use NFS.  Unix systems share storage in a native way using NFS.  This usually isn't point-n-click setup and the uid/gui numbers need to match on all clients. For Linux systems, that usually isn't too hard, but OSX starts uids at 500, so you'll need to change one side of the client/server so either the Ubuntu uids are 500+ or the OSX uids are 1000+.
On both systems, type 'id' into a terminal. See the uid and primary gid numbers?  NFS needs for those to match.

For if you are dropping OSX completely, just use rsync.  This is a 3 minute effort, 1-time, and you are done.

```
$ rsync -avz --stats --progress SOURCE  TARGET
```
Either the SOURCE or the TARGET can be local or remote or both can be remote.

So, something like
```
$ rsync -avz --stats --progress /myMusic/  thefu@hadar:/media/Music
```
will efficiently copy everything from the machine where the rsync command is running to another machine, with a different username.  If the usernames match on both systems (the uid doesn't need to match), then you can leave that off the command.  Just install rsync and ssh on both systems first.  Be certain that a plain ssh connection works first.   So ... **ssh thefu@hadar** connects to the 'hadar' server. Easy peasy.

People from Windows never think to use ssh or sftp, though they are by-far the easiest ways to move files around between systems.

---

