---
title: "Music On SSH Server, Can't Load In Rhythmbox"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by tdrusk on 2008-11-08
I added the server under places, but when I drag the music I get "Could not open resource for reading". I had this working very easily in Hardy. I have a feeling it works the same, but I'm just doing something wrong. Any ideas?

---

### Post by tdrusk on 2008-11-08
bump

---

### Post by rampage355 on 2008-11-28
I have the same issue, have searched and search for a answer and can't find one, still looking though.

---

### Post by dfme on 2008-12-23
i have the same issue... i have not been able to find any solution as of yet on the net.
this was working fine with ubuntu 7.10 - 8.06 (until some update). since then playing any mp3 files over ssh on rhythmbox is impossible and i get the following error message:
"Could not open resource for reading"

i also vaguely remembering getting a "Internal Gstreamer Error" when doing the above with ubuntu 8.06.

i have no problems listening to music over ssh using totem or vlc.

---

### Post by jerome1232 on 2008-12-23
I just tried this and it works fine for me. I connected to my other box via ssh, copied a music file to it.

Opened rhythmbox, Music-Import File, browsed to the server (It shows up in the left hand panel) and it imported just fine, I'm listening to it right now.

---

### Post by dfme on 2008-12-23
i also set up my server with a samba share, and again trying to listen to music over smb does not work using rhythmbox. it works however with totem and vlc.
i again get the same error message as stated above.
i started rhythmbox in debug mode, but i don't really get more infos out of it. i can attach the output if anybody would like to have a look...

---

### Post by Drikus on 2009-01-03
If you got a tracelogfile you might want to up it here.

[https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/53005](https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/53005)

---

### Post by The MacNab on 2009-01-27
I am having the same problem. I have a laptop running 8.10 and a server running 8.04. The server's IP address is 192.168.1.112, and the music is in /mnt/80gig/Music, a directory that is owned by the group shares, to which all users belong, have write access etc.

If I use Nautilus to navigate to this directory, I can right-click on a song, open it with VLC and hear music. If I right-click and open it with Rhythmbox, I get the same error as noted above.

If I open Rhythmbox and try to import a folder from that server, I get a string of import errors like those described above. I tried running "rhythmbox -d $> rhythm" to see what resulted, but the resulting file (from opening Rhythmbox, choosing "import folder", clicking on the folder, getting the errors and quitting) is over four MB! Is there a more terse or exact way to get further information to help with debugging?

Any ideas that anyone has would be greatly appreciated.

---

### Post by geoffatmk on 2009-02-06
Hi

I had the same problem and I seem to have solved it as follows.  Please do not ask why it works but perhaps someone who understands it better could explain?

I navigated to my smb share using Nautilus and it listed the songs as mp4 files.

I right clicked and Rhythmbox is not a listed option so I used another application and entered rythmbox.  The file came into my library and it played OK.

I then highlighted the whole album and did the same (rythmbox is now listed as an option) and all the file details came across into the library and I can now select and play them or play the whole album.

I right clicked one of the files to look at the properties and it is in a folder called .gvfs in my home folder.  When I explored that folder it was like a nethood link to my smb share for iTunes.

I went back to Rhythmbox and selected import a folder then navigated to ~/.gvfs/itunes on solaris the share name for the folder on my server.  Rhythmbox then imported all the artists and files into its library.

I shut it down and restarted and they were all still there!

As I say, no idea why and all I can find on .gvfs on google is the following;

*****

What is the GVFS folder for?
It's just a mountpoint for non-gvfs applications.

****

Over to the experts and I hope this solution can work for you too.

Geoff

---

### Post by dfme on 2009-02-08
thanks for the reply! i don't quite understand what you mean with:
> **geoffatmk said:**
> 
I right clicked and Rhythmbox is not a listed option so I used another application and entered rythmbox. The file came into my library and it played OK.

whats the 'other application' and what did you use it for? (to play the song or to open rhythmbox??)

also another thing is: i always have rhythmbox listed as an application to play my mp3 files (over smb as over ssh) when i right click on them.

---

### Post by geoffatmk on 2009-02-09
Sorry dfme re-reading my note shows it is not very clear.  Rythmbox was not my default applcaiton so when I right clicked the music file it was not listed.  I had to use "Open With" then "Other Application" and select Rhytmbox.  Once I had done that it then came up as a standard option in my right click listing.  If you already have it set to be one of your default aplications you can avoid this step.

Did following my steps help you?

---

### Post by bitbot on 2009-02-10
whoot, just the information I needed.  

Seems rhythmbox gacks when trying to add directories through the nautilus network mount crap (you'll see the uri based syntax in the import failure for example sftp://blah blah)

However all such mounts are available directly through the filesystem under the .gvfs directory in your home directory.  You'll just need to right click to show hidden files and navigate to theses directories instead.

thanks for posting!

---

### Post by jonny_boy27 on 2009-05-03
I found this method didn't work.

On the other hand, mounting the drive using sshfs (FUSE) worked just dandy

---

