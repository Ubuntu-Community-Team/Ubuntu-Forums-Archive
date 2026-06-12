---
title: "correct folder location?"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by moviebug on 2011-12-23
I am new to Mythbuntu...
I come from windows 7 background
I have just set-up Mythbuntu 11.10

I'm using MythTV...

I am trying to access
videos stored on a 2nd drive(named ATLANTIS) 
under a folder called'movie' 
so I went to..Utilities/Setup->Setup->Media Settings->Video Settings->General
and put in 'movie' folder location as .. /media/atlantis/movie

and then hit M(when trying to display the videos)
and I did a rescan for any changes

it doesnt see any of my movies..which are mostly .mkv files
What am I doing wrong???

The location is taken from whats shown when I use
Thunar file manager...and look at the 'movie' folder under the drive ATLANTIS

---

### Post by Jack Brown on 2011-12-23
might be case sensitive.

if drive is ATLANTIS, type all caps.

also
the separate drive might not be mounted automatically

---

### Post by moviebug on 2011-12-23
> **Jack Brown said:**
> might be case sensitive.

if drive is ATLANTIS, type all caps.

also
the separate drive might not be mounted automatically

Yep..thats the thing... I have AHCI activated...
Atlantis is a SATA Drive....
so in Thunar File Manager...Atlantis is being shown as a mounted drive
ie because its AHCI..it can be mounted and unmounted

So ATLANTIS is showing as mounted hard drive on the Desktop

So I dont know if that makes a difference on how I record its location..???

---

### Post by moviebug on 2011-12-23
I realised I was trying to alter the storage directories
with MythTV frontend set-up..
but dont I have to do this change in the MythTV backend setup area??

I tried going into the MythTV backend setup area and setting it up there ...
but its not recognising the folder path I gave it..

I think I need to take a screenshot of the file set-up in Thunar File manager
..so you guys can see where the folders are in the Atlantis drive
..because I'm not getting the path correct..I'm missing something
and I need help from someone who has
more experience with Linux file/folder structure??

How do I get a screenshot in Ubuntu?

---

### Post by moviebug on 2011-12-23
So attached is screenshot of the 
file manager showing.. Atlantis drive
and the 'movie' folder for videos
and 'recorded tv' folder for TV recordings

Hope this can help ...
I installed Gimp to do this..

---

### Post by moviebug on 2011-12-23
I just realised this ATLANTIS drive is still formatted in 
Windows NTFS system...

so I can only read from it ..correct?

so I cant record to it..ie for Live TV??

---

### Post by moviebug on 2011-12-23
Will this affect Myth TV being able to play/read the Movies(from ATLANTIS) 
via the Video selection
under the Main Menu..because its formatted in NTFS?

---

### Post by moviebug on 2011-12-23
So I went into the backend setup and created a group ..
pointing to /media/ATLANTIS/movie
but I still cant get the front end to populate the movie folder with the M command

I had gone in and told the internal player to recognise the .mkv ext

---

### Post by moviebug on 2011-12-23
I dropped five movies into the video folder 
under MythTv on the OS drive...
including 
a normal avi
a 720p avi
a 720p mkv
and a 1080p mkv

and then went into the Video area under MythTv..ie started up MythTV
and voila!! ..they were all appearing there without scanning
I did the M command anyway...
and made avi and mkv associated with the internal player..of MythTV

but now I cant get the internal player to playback any of the five movies
it sits there ..saying wait

Is the MythTV internal player not fully equipped?
ie does it use Vdpau?
does it support playback of avi and mkv?
What do I need to alter??

or do I need to setup an external player like SMplayer?

or is this to do with the group issue ..and the internal player??

when I look at the properties of the individual movies...
they all say ...Open with...SMplayer..
will that affect playback with the internal player in MythTV?

---

