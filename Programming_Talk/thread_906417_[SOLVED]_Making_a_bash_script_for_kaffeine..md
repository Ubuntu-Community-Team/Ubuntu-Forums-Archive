---
title: "[SOLVED] Making a bash script for kaffeine."
date: 2008-08-31
forum: Programming Talk
---

### Post by Rany Albeg on 2008-08-31
Hi,

I saw that there is an option to play a few songs in kaffeine by typing the command : kaffeine 'song1' 'song2' 'song3'...

so i thought about a bash script which will concatenate all songs name from a file into one string named ,lets say, SONGS , and then execute the cmd :

kaffeine "$SONGS"

the songs file looks like this:
song1
song2
song3
...

so in c++ i'll do something like this

[PHP]string cSong // variable to hold the current song.
string SONGS // variable to hold all songs.

ifstream songsFile; // the file which contains all songs.

while(!songsFile.eof()) //continue while there is more data to read from file.
{
   getline(songsFile,cSong,'\n'); // write a single line to cSong.
   cSong+=" "; // add space after song name.
   SONGS+=cSong; // concatenate cSong to SONGS string.
}
[/PHP]

Can some one help me with an idea of making this algorithm in bash script?

Thanks,
Have a nice day ;)

---

### Post by odyniec on 2008-08-31
Here's how you can do it with awk:
```
SONGS=`awk -vORS=' ' '{print "\47" $1 "\47"}' songs_file`
```

---

### Post by ghostdog74 on 2008-08-31
```

SONG=$(awk '{$1=$1}1' RS="" ORS="  " file)

```

---

### Post by rikxik on 2008-09-01
```

SONGS=`cat songsFile |tr -s "\n" " "`

```

---

### Post by ghostdog74 on 2008-09-01
> **rikxik said:**
> ```

SONGS=`cat songsFile |tr -s "\n" " "`

```

```

SONGS=`tr -s "\n" " " < songfile`

```

---

### Post by Rany Albeg on 2008-09-01
Thank you everyone,

I appreciate all answers.

Have a nice day;)

---

