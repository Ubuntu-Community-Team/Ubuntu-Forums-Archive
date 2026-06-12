---
title: "Basic Shell Script (or maybe C++)"
date: 2007-03-02
forum: Programming Talk
---

### Post by xMemphisx on 2007-03-02
Alright, i've got a lot of music, and the first time i pulled it from my Zen (using Gnomad), it pulled them down as ArtistName - SongTitle, and i really didn't want them saved that way. Well now the mp3 player was formatted, but the music is still on my computer. Basically i was going to make a shell script that went through and got the track # of the song, and the song title, and just did a simple 'cp w/e'. It might be easier to do with C++ than shell, i'm not totally sure... but basically i'd like to know how i can get the MetaTag information (trackname and track number) of an mp3 file.

---

### Post by lloyd_b on 2007-03-02
You'll want to install the package "mp3info".  In a terminal, "mp3info {file}" will display all of the metadata for that file.

Using the "-p" option, you can easily extract the various elements of metadata, and generate a new file name.  For example:
```
mp3info -p "%t (%n)" file.mp3
```
Will generate this:
```
Song Title (Track No)
```
("man mp3info" for more details on the formats available with "-p")

So you could create a script called "mp3rename":
```
#!/bin/sh 
INFO=`mp3info $1 -p "%t (%n)"`
cp "$1" "$INFO.mp3"
```

Note: on the "INFO=" line, those are backticks (the key with the ~, left of the number 1).

Then, run "mp3rename somefile.mp3", and it will take the file "somefile.mp3", and  copy it to "song name (track no).mp3", with the song name and track number extracted from the metadata.

I'm sure that there's some way to get it to process all of the files in the directory at once, but I have no clue what it is.  Maybe someone else will jump in with a way to finish the script.  

Lloyd B.

---

### Post by xMemphisx on 2007-03-02
Wow man, thanks! You did pretty much all of the work for me :) 

Maybe i can just do a "mp3rename *.mp3"


[Edit]
Nope, it get's real bitchy that there are spaces in the file name, and it isn't overly well accepting if if i don't use the * wildcard 

(e.g., Taking Back Sunday - You're So Last Summer.mp3 ---- Error File 'Taking' Doesn't Exist, Error File 'Back' Doesn't Exist, etc)

---

### Post by lloyd_b on 2007-03-02
> Maybe i can just do a "mp3rename *.mp3"


[Edit]
Nope, it get's real bitchy that there are spaces in the file name, and it isn't overly well accepting if if i don't use the * wildcard

"mp3rename *.mp3" won't work, for the simple reason that the script only handles one argument - that's what I meant when I said that maybe someone else would know how to finish the script (so that it could handle multiple arguments).

To get around those spaces problems, you need to quote the file name:
mp3rename "Some Artist-Some Song.mp3"

If it were something I was doing, I would handle it as follows:

1. Create the mp3rename script in the directory with the mp3 files.
     (Make the script)

2. Run "ls -Q *.mp3 > files.dat"
     (Create a file called "files.dat", which contains a list of mp3 files with the filenames in quotation marks)

3. "vi files.dat"
     (Edit "files.dat" using the "vi" editor)

4. ":1,$s/\&/.\/mp3rename /<enter>"
    (Thats <colon>1<comma><dollar sign>s<slash><backslash><ampersand><slash><dot><backslash><slash>mp3rename<space><slash><enter>
    (Prepends "./mp3rename " onto each line of the file list)

5. ":wq<enter>"
     (Save and exit from "vi")

6. "chmod 700 files.dat"
     (Make the edited file executable)

7. "files.dat"
    (Run it)

Since this is a "do once" type job (at least I HOPE it is), it's probably not worth the effort of perfecting the script - with that "vi" command, it's pretty easy to edit the file list into a script that calls the mp3rename script.  You can have the job done in about two minutes.

Lloyd B.

---

### Post by Choad on 2007-03-02
theres an xfce utility called "bulk rename" that does this for you. its probably installable from the repositories.

---

### Post by po0f on 2007-03-02
```

for mp3 in *.mp3; do
    mp3rename \"$mp3\"
done
```

---

### Post by lloyd_b on 2007-03-03
> ```
for mp3 in *.mp3; do
    mp3rename \"$mp3\"
done
```

Ah, so THAT'S how you make a shell script handle multiple arguments.  I knew it was possible, just didn't know exactly how it was done.  Cool.

Now to roll it all into one:
```
#!/bin/sh
for FILE in *.mp3; do
     NEWFILE=`mp3info "$FILE" -p "%d (%n)"`
     cp "$FILE" "$NEWFILE.mp3"
done
```

Lloyd B.

---

### Post by xMemphisx on 2007-03-04
Wow... there's actually a repository program... mp3rename... all i had to do was 

mp3rename -s '&t - &k'

mp3rename *.mp3

Did it all for me.... heh, thanks for the help though guys. :lolflag:

---

