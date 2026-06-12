---
title: "abcde: get artist/album info for further use in shell script"
date: 2011-08-27
forum: Programming Talk
---

### Post by CryptKeeper777 on 2011-08-27
I've just discovered abcde for cd ripping and it works like a charm. Now I'd like to write a short shell script for the whole ripping process to automatize some standard changes I'd like to do to the just ripped mp3 files. That's mainly changing the ID3 album tag from "<album name>" to "<year> - <album name>" (I do that to have the albums always sorted by year, not by name). 

But how can I get the information from abcde about which album has just been imported (artist and album name)? What I actually need to do it the way I intend to is the path to the new album folder.

Or is there even a way to automatically do this inside abcde (via the config file)? I can manually edit the tags before importing, but is it possible to automatize this?

PS: As I'm just talking about abcde: Does anyone know hot to use vim instead of nano to edit the tag information before importing?

---

### Post by sanderd17 on 2011-08-27
You could use this utility I guess: [http://packages.ubuntu.com/natty/id3v2](http://packages.ubuntu.com/natty/id3v2)

---

### Post by CryptKeeper777 on 2011-08-27
> **sanderd17 said:**
> You could use this utility I guess: [http://packages.ubuntu.com/natty/id3v2](http://packages.ubuntu.com/natty/id3v2)
Thanks for the answer, but that's not what I want to know. Changing the ID3 tags isn't the problem; my problem is that I don't know hot to get the album/artist-info from abcde. I want to make a script in which abcde is executed and then a ID3-tag utility, but I don't know how to get information about what was imported from abcde to use as input infor for the tag utility...

---

### Post by AlphaLexman on 2011-08-27
I also like my albums sorted by release year...

In your ~/.abcde.conf file change the '**OUTPUTFORMAT=**' line to...
```
OUTPUTFORMAT='${ARTISTFILE}/[COLOR="Red"]${YEAR}[/COLOR].${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
```
Just adjust the other variables and separators to your own liking.

---

### Post by CryptKeeper777 on 2011-08-28
> **AlphaLexman said:**
> I also like my albums sorted by release year...

In your ~/.abcde.conf file change the '**OUTPUTFORMAT=**' line to...
```
OUTPUTFORMAT='${ARTISTFILE}/[COLOR=Red]${YEAR}[/COLOR].${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
```Just adjust the other variables and separators to your own liking.
I've already done that... That only changes the folder name, but what I want now is changing the ID3 tags, too. Thanks for your reply though.

---

### Post by AlphaLexman on 2011-08-28
Add,
```
SHOWCDDBFIELDS='year,genre'
```
To your ~/.abcde.conf file.

Some good examples of the abcde.conf can be found [here.]("http://www.andrews-corner.org/abcde.html")

The abcde executable is actually just a bash script that you can read.
```
cp /usr/bin/abcde ~/bin
```

---

