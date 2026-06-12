---
title: "can't delete files"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by bth73 on 2008-06-03
I've got some "FINDER.DAT" files left in my mp3 folder.
this seems to be some programming errors:
I turn on View Hidden files and no finder.dat files are shown.
I load all my mp3's into movie player and the finder.dat files not only show up but they also error out the player.
I do the search in nautilus for finder.dat and there they are but I can't delete from there.
The finder.dat files are microsoft bread crumbs right?

The primary purpose of a computer is to manipulate files. Why is it so difficult to delete files in linux? Please give me full access. Any file, any hard drive, any time, all the time.
Is it possible to be root all the time?
Thanks, bt

---

### Post by KingTermite on 2008-06-03
I'm not sure if its possible to be root all the time, but you wouldn't want to. Too risky, security wise.

Now...it sounds like a Nautalis problem (or lack of understanding). I'm not that familiar with Natualis (relative newbie myself). If you navigate to directory in a command shell and type "ls -al", what are the contents/privileges for the files in the directory. Also, what about the privs on the folder itself?

---

### Post by billgoldberg on 2008-06-03
> **bth73 said:**
> I've got some "FINDER.DAT" files left in my mp3 folder.
this seems to be some programming errors:
I turn on View Hidden files and no finder.dat files are shown.
I load all my mp3's into movie player and the finder.dat files not only show up but they also error out the player.
I do the search in nautilus for finder.dat and there they are but I can't delete from there.
The finder.dat files are microsoft bread crumbs right?

The primary purpose of a computer is to manipulate files. Why is it so difficult to delete files in linux? Please give me full access. Any file, any hard drive, any time, all the time.
Is it possible to be root all the time?
Thanks, bt

all root all the time is why windows has security issues

you need sudo (root) access to delete some files

press alt+f2 (or open a terminal) and type

```
gksudo nautilus
```

navigate to the file and press delete

---

### Post by newbuntuxx on 2008-06-03
or open terminal and type:

```
sudo nautilus
```

once you delete the file, close the nautilus window! You dont want to be deleting system files by accident.

---

### Post by bth73 on 2008-06-03
OK, somebody screwed up.
YOU CAN NOT DELETE ANYTHING FROM A SEARCH FIELD IN NAUTILUS.
VIEW HIDDEN FILES DOES NOT WORK.
MPLAYER CAN SEE THESE FINDER.DAT FILES AND ERRORS ON THEM.

SO, I REPEAT, HOW CAN I DELETE THESE FILES WITHOUT USING WINDOWS (sic)?

---

### Post by Darkade on 2008-06-03
Just calm down man :P

Ok first open a terminal and write
```
ls /media 
```
now in the list there's a folder with your mp3 player name
do
```
cd /media/whateverisyourmp3playername 
```
so far so good? ok
now do 
```
find |egrep *.dat 
```
you will see where your .dat files are
finally do
```
sudo nautilus /media 
```
look for the location of your .dat files and delete them

DON'T FORGET TO CLOSE THIS WINDOW you could delete a system folder by accident
also you REALLY don't want to be root all the time, accidents happen and beeing root all the time accidents tend to be permanent like in windows :P

---

### Post by bth73 on 2008-06-03
here is what happened:
bt@bt-desktop:~$ ls /media
cdrom  cdrom0  cdrom1  floppy  floppy0
bt@bt-desktop:~$ cd /media/movie player
bash: cd: /media/movie: No such file or directory
bt@bt-desktop:~$ 

now I don't think you understand.
the only way to see these files is to use the search field in nautilus and you can NOT delete anything from that field.

---

### Post by bth73 on 2008-06-03
Oh, and by the way, is there a player that will let you delete files directly from the player off the hard drive?

---

### Post by Darkade on 2008-06-03
i dunno if there's a video player that can do that last thing but i'm sure there must be

ok ok, well if you can se the .dot files in the finder could you please take a screenshot and post it
it will be a lot easier to help you since in the finder you can see the route to the file and thus you will be able to delete it from some other pleace

and sorry for the bad english

---

### Post by bth73 on 2008-06-03
This is the rest of it:

bt@bt-desktop:~$ find |egrep *.dat
./.tomboy/addin-db-000/fdb-update-lock
./.tomboy/addin-db-000/addin-dir-data
./.tomboy/addin-db-000/addin-dir-data/usr_lib_tomboy_c760bb4e.data
./.tomboy/addin-db-000/addin-dir-data/usr_lib_tomboy_addins_b07dc18e.data
./.tomboy/addin-db-000/addin-data
./.tomboy/addin-db-000/addin-data/Tomboy.StickyNoteImportAddin,0.1.maddin
./.tomboy/addin-db-000/addin-data/Tomboy.Tomboy,0.7_ff7b1edf.mroot
./.tomboy/addin-db-000/addin-data/Tomboy.WebDavSyncServiceAddin,0.1.maddin
./.tomboy/addin-db-000/addin-data/Tomboy.BacklinksAddin,0.1.maddin
./.tomboy/addin-db-000/addin-data/Tomboy.ExportToHtmlAddin,0.1.maddin
./.tomboy/addin-db-000/addin-data/Tomboy.BugzillaAddin,0.1.maddin
./.tomboy/addin-db-000/addin-data/Tomboy.FixedWidthAddin,0.1.maddin
./.tomboy/addin-db-000/addin-data/Tomboy.NoteOfTheDayAddin,0.1.maddin
./.tomboy/addin-db-000/addin-data/Tomboy.SshSyncServiceAddin,0.1.maddin
./.tomboy/addin-db-000/addin-data/Tomboy.FileSystemSyncServiceAddin,0.1.maddin
./.tomboy/addin-db-000/addin-data/Tomboy.PrintNotesAddin,0.1.maddin
./.tomboy/addin-db-000/addin-data/Tomboy.EvolutionAddin,0.1.maddin
./.gnome2/evince/ev-metadata.xml
./.cache/tracker/file-update-index.db
./.wapi/shared_data-bt-desktop-Linux-x86_64-328-11-0
./.update-notifier
./Music/ALBUMS/Dan Fogelberg Live - Disk 2/Intimidation.wma
./Music/music to edit/Eumir Deodato - (Deodato 2 02) Rhapsody in Blue.mp3
./Music/music to edit/Ramones - Anthology - 23 - I Wanna Be Sedated.mp3
./Music/music to edit/ACDC - Shake Your Foundations.mp3
./Music/music to edit/The Offspring - I Wanna be Sedated (Ramones Cover)(1).mp3
./.local/share/tracker/data
./.local/share/tracker/data/common.db
./.mozilla/firefox/m024v40i.default/history.dat
./.mozilla/firefox/m024v40i.default/formhistory.dat
./.mozilla/firefox/m024v40i.default/compreg.dat
./.mozilla/firefox/m024v40i.default/xpti.dat
./.mozilla/firefox/pluginreg.dat
bt@bt-desktop:~$ 

This didn't find them.

---

### Post by bth73 on 2008-06-03
/home/bt/Music/ALBUMS/Aerosmith Greatest Hits/FINDER.DAT
/home/bt/Music/ALBUMS/Bob Marley_Natty Dread/FINDER.DAT
/home/bt/Music/ALBUMS/Boston_Third Stage/FINDER.DAT
/home/bt/Music/ALBUMS/Cheap Trick_Heaven Tonight/FINDER.DAT
/home/bt/Music/ALBUMS/Chicago 17/FINDER.DAT
/home/bt/Music/ALBUMS/Chicago 19-1988/FINDER.DAT
/home/bt/Music/ALBUMS/Chicago III/FINDER.DAT
/home/bt/Music/ALBUMS/Donald Fagen_Kamakiriad/FINDER.DAT
/home/bt/Music/ALBUMS/Dwight Yoakam_Guitars, Cadillacs Etc- Etc-/FINDER.DAT
/home/bt/Music/ALBUMS/ELO's Greatest Hits/FINDER.DAT
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/FINDER.DAT
/home/bt/Music/ALBUMS/Flying Burrito Bros. Seattle Pop Fest 1969/FINDER.DAT
/home/bt/Music/ALBUMS/George Thorogood & the Destroyers_Haircut/FINDER.DAT
/home/bt/Music/ALBUMS/Paramount/FINDER.DAT
/home/bt/Music/ALBUMS/Paramount/cali allman/FINDER.DAT
/home/bt/Music/ALBUMS/Patsy Cline - A Collection Of Country Classics/FINDER.DAT
/home/bt/Music/ALBUMS/Pointer Sisters_Greatest Hits/FINDER.DAT
/home/bt/Music/ALBUMS/Randy Newman/FINDER.DAT
/home/bt/Music/ALBUMS/Robin Trower_Bridge of Sighs/FINDER.DAT
/home/bt/Music/ALBUMS/Rockin' The Blues/FINDER.DAT
/home/bt/Music/ALBUMS/Rory Galiger - A blue day for the blues/FINDER.DAT
/home/bt/Music/ALBUMS/The Alan Parsons Project_I Robot/FINDER.DAT
/home/bt/Music/ALBUMS/The Alan Parsons Project_Tales of Mystery and Imagination/FINDER.DAT
/home/bt/Music/ALBUMS/The Alan Parsons Project_The Best of the Alan Parsons Project/FINDER.DAT
/home/bt/Music/ALBUMS/ The Allman Brothers Band_A Decade of Hits/FINDER.DAT
/home/bt/Music/ALBUMS/The Allman Brothers Band_Beginnings/FINDER.DAT
/home/bt/Music/ALBUMS/The Allman Brothers Band_Eat A Peach/FINDER.DAT
/home/bt/Music/ALBUMS/The Band_The Best of The Band/FINDER.DAT
/home/bt/Music/ALBUMS/The Band_To Kingdom Come - Disc 2/FINDER.DAT
/home/bt/Music/ALBUMS/The Band_To Kingdom come-dsk1/FINDER.DAT
/home/bt/Music/ALBUMS/The Beatles_Abbey Road/FINDER.DAT
/home/bt/Music/ALBUMS/The Beatles_Help!/FINDER.DAT
/home/bt/Music/ALBUMS/The Beatles_Let It Be...Naked/FINDER.DAT
/home/bt/Music/ALBUMS/The Beatles_Magical Mystery Tour/FINDER.DAT
/home/bt/Music/ALBUMS/The Beatles_Please Please Me/FINDER.DAT
/home/bt/Music/ALBUMS/The Beatles_Revolver/FINDER.DAT
/home/bt/Music/ALBUMS/The Best Of Freddie King/FINDER.DAT
/home/bt/Music/ALBUMS/The Black Crowes_The Southern Harmony And Musical Companion/FINDER.DAT
/home/bt/Music/ALBUMS/The Byrds Box Set  (Disc 1 - We Have Ignition)/FINDER.DAT
/home/bt/Music/ALBUMS/The Byrds Box Set  (Disc 2 -Cruising Altitude)/FINDER.DAT
/home/bt/Music/ALBUMS/The Byrds_Box Set (disc 3) Full Throttle/FINDER.DAT
/home/bt/Music/ALBUMS/The Byrds Box Set - (Disc4 -Final Approach)/FINDER.DAT
/home/bt/Music/ALBUMS/The Cars_Heartbeat City/FINDER.DAT
/home/bt/Music/ALBUMS/The Dave Matthews Band_Remember Two Things/FINDER.DAT
/home/bt/Music/ALBUMS/The Doors_L.A. Woman/FINDER.DAT
/home/bt/Music/ALBUMS/The Doors_The Soft Parade/FINDER.DAT
/home/bt/Music/ALBUMS/The Doors_Waiting for the Sun/FINDER.DAT
/home/bt/Music/ALBUMS/The Gourds_Bolsa de Agua/FINDER.DAT
/home/bt/Music/ALBUMS/The Police_Every Breath You Take - The Singles/FINDER.DAT
/home/bt/Music/ALBUMS/TheRascals/FINDER.DAT
/home/bt/Music/ALBUMS/The Rock n Roll Era 1957/FINDER.DAT
/home/bt/Music/ALBUMS/The Rolling Stones_Beggars Banquet/FINDER.DAT
/home/bt/Music/ALBUMS/The Rolling Stones_Steel Wheels/FINDER.DAT
/home/bt/Music/ALBUMS/Warptones_J.J.'s Livingroom/FINDER.DAT
/home/bt/Music/ALBUMS/Warptones_Sketchpad/FINDER.DAT
/home/bt/Music/ALBUMS/ZZ Top_One Foot In the Blues/FINDER.DAT

---

### Post by Darkade on 2008-06-03
:lolflag: it did find them but others since you are no t in  the location you want see :P:P:lolflag:

> **bth73 said:**
> This is the rest of it:
./.mozilla/firefox/m024v40i.default/history.dat
./.mozilla/firefox/m024v40i.default/formhistory.dat
./.mozilla/firefox/m024v40i.default/compreg.dat
./.mozilla/firefox/m024v40i.default/xpti.dat
./.mozilla/firefox/pluginreg.dat
bt@bt-desktop:~$ 

This didn't find them.

---

### Post by Darkade on 2008-06-03
So are these the files you want to delete?
> **bth73 said:**
> /home/bt/Music/ALBUMS/Aerosmith Greatest Hits/FINDER.DAT
/home/bt/Music/ALBUMS/Bob Marley_Natty Dread/FINDER.DAT
/home/bt/Music/ALBUMS/Boston_Third Stage/FINDER.DAT
/home/bt/Music/ALBUMS/Cheap Trick_Heaven Tonight/FINDER.DAT
/home/bt/Music/ALBUMS/Chicago 17/FINDER.DAT
/home/bt/Music/ALBUMS/Chicago 19-1988/FINDER.DAT
/home/bt/Music/ALBUMS/Chicago III/FINDER.DAT
/home/bt/Music/ALBUMS/Donald Fagen_Kamakiriad/FINDER.DAT
/home/bt/Music/ALBUMS/Dwight Yoakam_Guitars, Cadillacs Etc- Etc-/FINDER.DAT
/home/bt/Music/ALBUMS/ELO's Greatest Hits/FINDER.DAT
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/FINDER.DAT
/home/bt/Music/ALBUMS/Flying Burrito Bros. Seattle Pop Fest 1969/FINDER.DAT
/home/bt/Music/ALBUMS/George Thorogood & the Destroyers_Haircut/FINDER.DAT
/home/bt/Music/ALBUMS/Paramount/FINDER.DAT
/home/bt/Music/ALBUMS/Paramount/cali allman/FINDER.DAT
/home/bt/Music/ALBUMS/Patsy Cline - A Collection Of Country Classics/FINDER.DAT
/home/bt/Music/ALBUMS/Pointer Sisters_Greatest Hits/FINDER.DAT
/home/bt/Music/ALBUMS/Randy Newman/FINDER.DAT
/home/bt/Music/ALBUMS/Robin Trower_Bridge of Sighs/FINDER.DAT
/home/bt/Music/ALBUMS/Rockin' The Blues/FINDER.DAT
/home/bt/Music/ALBUMS/Rory Galiger - A blue day for the blues/FINDER.DAT
/home/bt/Music/ALBUMS/The Alan Parsons Project_I Robot/FINDER.DAT
/home/bt/Music/ALBUMS/The Alan Parsons Project_Tales of Mystery and Imagination/FINDER.DAT
/home/bt/Music/ALBUMS/The Alan Parsons Project_The Best of the Alan Parsons Project/FINDER.DAT
/home/bt/Music/ALBUMS/ The Allman Brothers Band_A Decade of Hits/FINDER.DAT
/home/bt/Music/ALBUMS/The Allman Brothers Band_Beginnings/FINDER.DAT
/home/bt/Music/ALBUMS/The Allman Brothers Band_Eat A Peach/FINDER.DAT
/home/bt/Music/ALBUMS/The Band_The Best of The Band/FINDER.DAT
/home/bt/Music/ALBUMS/The Band_To Kingdom Come - Disc 2/FINDER.DAT
/home/bt/Music/ALBUMS/The Band_To Kingdom come-dsk1/FINDER.DAT
/home/bt/Music/ALBUMS/The Beatles_Abbey Road/FINDER.DAT
/home/bt/Music/ALBUMS/The Beatles_Help!/FINDER.DAT
/home/bt/Music/ALBUMS/The Beatles_Let It Be...Naked/FINDER.DAT
/home/bt/Music/ALBUMS/The Beatles_Magical Mystery Tour/FINDER.DAT
/home/bt/Music/ALBUMS/The Beatles_Please Please Me/FINDER.DAT
/home/bt/Music/ALBUMS/The Beatles_Revolver/FINDER.DAT
/home/bt/Music/ALBUMS/The Best Of Freddie King/FINDER.DAT
/home/bt/Music/ALBUMS/The Black Crowes_The Southern Harmony And Musical Companion/FINDER.DAT
/home/bt/Music/ALBUMS/The Byrds Box Set  (Disc 1 - We Have Ignition)/FINDER.DAT
/home/bt/Music/ALBUMS/The Byrds Box Set  (Disc 2 -Cruising Altitude)/FINDER.DAT
/home/bt/Music/ALBUMS/The Byrds_Box Set (disc 3) Full Throttle/FINDER.DAT
/home/bt/Music/ALBUMS/The Byrds Box Set - (Disc4 -Final Approach)/FINDER.DAT
/home/bt/Music/ALBUMS/The Cars_Heartbeat City/FINDER.DAT
/home/bt/Music/ALBUMS/The Dave Matthews Band_Remember Two Things/FINDER.DAT
/home/bt/Music/ALBUMS/The Doors_L.A. Woman/FINDER.DAT
/home/bt/Music/ALBUMS/The Doors_The Soft Parade/FINDER.DAT
/home/bt/Music/ALBUMS/The Doors_Waiting for the Sun/FINDER.DAT
/home/bt/Music/ALBUMS/The Gourds_Bolsa de Agua/FINDER.DAT
/home/bt/Music/ALBUMS/The Police_Every Breath You Take - The Singles/FINDER.DAT
/home/bt/Music/ALBUMS/TheRascals/FINDER.DAT
/home/bt/Music/ALBUMS/The Rock n Roll Era 1957/FINDER.DAT
/home/bt/Music/ALBUMS/The Rolling Stones_Beggars Banquet/FINDER.DAT
/home/bt/Music/ALBUMS/The Rolling Stones_Steel Wheels/FINDER.DAT
/home/bt/Music/ALBUMS/Warptones_J.J.'s Livingroom/FINDER.DAT
/home/bt/Music/ALBUMS/Warptones_Sketchpad/FINDER.DAT
/home/bt/Music/ALBUMS/ZZ Top_One Foot In the Blues/FINDER.DAT

---

### Post by Darkade on 2008-06-03
If that's the case (that this are the files that you want to delete) just copy pase the following in a terminal

```
sudo rm -f /home/bt/Music/ALBUMS/Aerosmith Greatest Hits/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Bob Marley_Natty Dread/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Boston_Third Stage/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Cheap Trick_Heaven Tonight/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Chicago 17/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Chicago 19-1988/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Chicago III/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Donald Fagen_Kamakiriad/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Dwight Yoakam_Guitars, Cadillacs Etc- Etc-/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/ELO's Greatest Hits/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Flying Burrito Bros. Seattle Pop Fest 1969/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/George Thorogood & the Destroyers_Haircut/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Paramount/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Paramount/cali allman/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Patsy Cline - A Collection Of Country Classics/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Pointer Sisters_Greatest Hits/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Randy Newman/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Robin Trower_Bridge of Sighs/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Rockin' The Blues/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Rory Galiger - A blue day for the blues/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Alan Parsons Project_I Robot/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Alan Parsons Project_Tales of Mystery and Imagination/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Alan Parsons Project_The Best of the Alan Parsons Project/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/ The Allman Brothers Band_A Decade of Hits/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Allman Brothers Band_Beginnings/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Allman Brothers Band_Eat A Peach/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Band_The Best of The Band/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Band_To Kingdom Come - Disc 2/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Band_To Kingdom come-dsk1/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Beatles_Abbey Road/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Beatles_Help!/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Beatles_Let It Be...Naked/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Beatles_Magical Mystery Tour/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Beatles_Please Please Me/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Beatles_Revolver/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Best Of Freddie King/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Black Crowes_The Southern Harmony And Musical Companion/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Byrds Box Set (Disc 1 - We Have Ignition)/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Byrds Box Set (Disc 2 -Cruising Altitude)/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Byrds_Box Set (disc 3) Full Throttle/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Byrds Box Set - (Disc4 -Final Approach)/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Cars_Heartbeat City/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Dave Matthews Band_Remember Two Things/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Doors_L.A. Woman/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Doors_The Soft Parade/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Doors_Waiting for the Sun/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Gourds_Bolsa de Agua/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Police_Every Breath You Take - The Singles/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/TheRascals/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Rock n Roll Era 1957/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Rolling Stones_Beggars Banquet/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/The Rolling Stones_Steel Wheels/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Warptones_J.J.'s Livingroom/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/Warptones_Sketchpad/FINDER.DAT
sudo rm -f /home/bt/Music/ALBUMS/ZZ Top_One Foot In the Blues/FINDER.DAT
```

---

### Post by bth73 on 2008-06-03
YES, but only the finder.dat files, not the mp3/wma file it's attached to.

---

### Post by Darkade on 2008-06-03
then try just ONE line from my last post, the ones that were kindda
```
sudo rm -f /home/music/etcetera
```
and make sure it just delte the .dat file
but i can almost garantee it
just try the .mp3 file asosiated with it and then go ahead

---

### Post by bth73 on 2008-06-03
this is after - still there:

/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - Bennie and the Jets.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - Candle in the Wind.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - Funeral for a Friend-Love Lies Bleeding.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - Goodbye Yellow Brick Road.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - Grey Seal.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - I've Seen That Movie Too.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - Jamaica Jerk Off.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - This Song Has No Title.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/FINDER.DAT

---

### Post by Darkade on 2008-06-03
hey but kindda worked didn't it? :lolflag: I'm sorry but I'm at the office right now and I gotta go :P I will login at home so hope you can get it solved in the next hour and a half and i'll will help you as soon as I arrive

> **bth73 said:**
> this is after - still there:

/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - Bennie and the Jets.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - Candle in the Wind.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - Funeral for a Friend-Love Lies Bleeding.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - Goodbye Yellow Brick Road.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - Grey Seal.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - I've Seen That Movie Too.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - Jamaica Jerk Off.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/Elton John - This Song Has No Title.mp3
/home/bt/Music/ALBUMS/Elton John_Goodbye Yellow Brick Road/FINDER.DAT

---

### Post by bth73 on 2008-06-03
this is from your 2nd term. command: - still there 

/home/bt/Music/ALBUMS/Aerosmith Greatest Hits/01 - Dream On.wma
/home/bt/Music/ALBUMS/Aerosmith Greatest Hits/02 - Same Old Song And Dance.wma
/home/bt/Music/ALBUMS/Aerosmith Greatest Hits/03 - Sweet Emotion.wma
/home/bt/Music/ALBUMS/Aerosmith Greatest Hits/04 - Walk This Way.wma
/home/bt/Music/ALBUMS/Aerosmith Greatest Hits/05 - Last Child.wma
/home/bt/Music/ALBUMS/Aerosmith Greatest Hits/06 - Back In The Saddle.wma
/home/bt/Music/ALBUMS/Aerosmith Greatest Hits/07 - Draw The Line.wma
/home/bt/Music/ALBUMS/Aerosmith Greatest Hits/08 - Kings And Queens.wma
/home/bt/Music/ALBUMS/Aerosmith Greatest Hits/09 - Come Together.wma
/home/bt/Music/ALBUMS/Aerosmith Greatest Hits/10 - Remember (Walking In The Sand).wma
/home/bt/Music/ALBUMS/Aerosmith Greatest Hits/FINDER.DAT

Why can't I delete from the search field? This seems like a glaring oversite. Why have a search field that you can't do anything from???

---

### Post by The Cog on 2008-06-03
That screenshot would really help us know what's occuring.

---

### Post by Fixman on 2008-06-03
Finder.dat is a Mac "folder properties" file. Do you have/had a Mac partition? (OS X, etc)

---

### Post by bth73 on 2008-06-03
I don't know how to take a screen shot. Just a newbee.
But, what about not being able to do anything from the search field? A nautilus fix would solve this problem SIMPLY!
And while I'm bashing programmers, Where is the undo button?

---

### Post by bth73 on 2008-06-03
never been on a Mac, thought these were like bread crumbs from micro sloff so it could find it's way back.

---

### Post by The Cog on 2008-06-03
Press the PrintScreen key to take a screenshot. A popup asks where to save it.

---

### Post by bth73 on 2008-06-03
Here you go:

/home/bt/Desktop/Screenshot.png

well, I guess I need more instructions.

---

### Post by The Cog on 2008-06-03
That only posted the file name, didn't attach the file. Never mind, I just had a little play wth search, and nautilus can delete files found with search - at least, it normally can. Why can't you delete them? What happens when you highlight an icon and press the delete key, or right-click and chose to move to the deleted items folder?

Where are these files located that you can't delete? If you right click the found file icon and choose Properties, you will see the location of the files.

---

### Post by SteveNorman on 2008-06-03
if you want to get rid of all .DAT files, cd in to the directory they are in and do

```
rm *.DAT
```

make sure there is no space between the asteric and .dat

---

### Post by The Cog on 2008-06-03
Duplicate post - sorry

---

### Post by bth73 on 2008-06-03
I've tried other folders and the delete option does not activate at all - never
These files are in my music folder in my home folder on the main hard drive.

Steve, I don't understand what cd means.

---

### Post by bth73 on 2008-06-03
here is the results from me trying:

bt@bt-desktop:~$ rm *.DAT
rm: cannot remove `*.DAT': No such file or directory
bt@bt-desktop:~$ cd
bt@bt-desktop:~$ cd bt/music
bash: cd: bt/music: No such file or directory
bt@bt-desktop:~$ cd home/bt/music
bash: cd: home/bt/music: No such file or directory
bt@bt-desktop:~$ 

also tried thunar, but it has no search option that I could find.
I've got over 10,000 music files and to do this manually will take days or weeks.
Why can't I delete from the search field?????????????????????????????????????
can anybody fix Nautilus???????????????????????

---

### Post by The Cog on 2008-06-03
I'm about to go to bed, but maybe someone else can carry on with this.


First, open a command prompt (Applications->Terminal) and type in the following command:
rm /home/bt/Music/ALBUMS/TheRascals/FINDER.DAT
If this succesfully removes the file then you will just get the prompt again with no error message. In this case, you can try this command. Make sure to type it exactly. Best is to copy it from the browser and paste it into the terminal. It tries to find every file called FINDER.DAT and tries to remove it.
```
find /home/bt/Music -name 'FINDER.DAT' -exec rm {} \;
```

If your first command above gave an error message, post it here. If it is a permission denied error, also post the output from this command:
ls -l /home/bt/Music/ALBUMS/TheRascals


I wonder if you copied the files from a read-only medium so they are marked read-only. If that were the case, this command might fix your inability to delete them, but then I would have expected the icons to have padlocks on them. This command will make everyting writeable so the command in the above box should work:
```
chmod -R +w /home/bt/Music
```

---

### Post by SteveNorman on 2008-06-03
cd is change directory

so do
```
cd /home/bt/Music/ALBUMS
```

then type 
```
ls -a *.DAT
``` 

and list what it says please

---

### Post by bth73 on 2008-06-03
THANKS EVERYONE, this newbee solved this problem all by myself.
DID THE SEARCH OUT OF THE PLACES "SEARCH FOR FILES" INSTEAD OF OUT OF THE BROWSER WINDOW, THEN CLICKED ON TOP FILE AND SHIFT ENTER ON THE LAST FILE THEN MOVE TO TRASH - GONE - THEN EMPTIED TRASH.

SOMEONE NEEDS TO FIX THE BROWSER WINDOW SEARCH BECAUSE IT IS WORTHLESS AS YOU CAN'T DO ANYTHING FROM THERE.

---

### Post by SteveNorman on 2008-06-03
Killer..nice work
Its important that you learn some of the command line stuff,,as this will help you understand the logic of what the point and click/ drag and drop stuff is doing. The power you get when you learn it is what makes linux better than windows (IMHO).

here is a good linux tutorial if your interested,,it covers most of the basics that are in this thread

[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

---

### Post by bth73 on 2008-06-03
Don't Want To Rub Salt In Anyone's Wound But It Is Sad When An Retired Car Stereo Installer Can Fix Stuff The Experts Can't. But Don't Feel Bad Cause I Do It All The Time.

Thanks Again For Trying,
Bt

---

### Post by bth73 on 2008-06-03
THANKS STEVE, I should learn more but I'm so clogged up with solving problems that it's hard to learn anything new that I don't absoutly need to know.
I mostly solve auto electric problems on hot rods, but my partner keeps getting into other fields. Like finding a distributor for a ford 302 that's under 8" tall, or fixing a wast oil heater, installing neon on buildings and signs, wiring up a sound system for a karokee club, ect.

My biggest use for computers is to build and manage my multimedia collection.
I've been researching on the net for a multimedia player device to play off a usb hard drive. I'm using a buffalo link dvd media server that works ok but has a 999 item folder limitation. looking for another without that limitation.
Also looking for a 3 wheeler, that's enclosed and offerers good performance and gas mileage.

---

### Post by SteveNorman on 2008-06-04
Most of us are just other users,,not experts. Also the stuff listed where all fixes,,but its hard to communicate like this (typed paragraph or 2).
Have you ever called microsoft help?  good luck.

There are several ways to fix the same problem,,and without knowing your experience level it was difficult to communicate. In windows you probably would not have seen all those little files and they would build up like cholesterol until your system bogs down and chokes to death.

In linux you learn ways to manipulate your system. In windows the system learns to manipulate you!! (cue organ and lightening effects)

good job on the fix.

---

