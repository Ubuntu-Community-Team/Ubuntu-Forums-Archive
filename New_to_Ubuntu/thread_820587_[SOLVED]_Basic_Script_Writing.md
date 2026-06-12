---
title: "[SOLVED] Basic Script Writing"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by dwally89 on 2008-06-06
Hi,

I was wondering how hard would it be to write a script that I could run that would go through every file in a certain folder (and its subfolders) and write to a text file a list of the files that have been created in the past month.

Thanks

---

### Post by HalPomeranz on 2008-06-06
Unix doesn't store file creation time.  The best that you can do is find all files that have been modified/updated within the last month:

```

find /some/dir -mtime -30 >someoutputfile

```

Replace "/some/dir" with the directory you wish to search and "someoutputfile" with the name of the file you want the list recently modified files to end up in.

---

### Post by dwally89 on 2008-06-06
Wow thanks thats amazing :-)

Just one little thing I forgot to mention, it is possible I could make it ignore .jpg files?

Thanks

---

### Post by HalPomeranz on 2008-06-06
> **dwally89 said:**
> Just one little thing I forgot to mention, it is possible I could make it ignore .jpg files?

```

find /some/dir -mtime -30 | egrep -vi '\.jpg$' >someoutputfile

```

---

### Post by dwally89 on 2008-06-06
Thanks :-)

Sorry to be picky, but I notice its also writing the names of all the folders its searching through.

Is it possible it could just right the names of the files that meet the condition, as opposed to including the folders too?

Thanks

---

### Post by HalPomeranz on 2008-06-06
```

find /some/dir -mtime -30 -exec basename {} \; | egrep -vi '\.jpg$' >someoutputfile

```

:-)

---

### Post by dwally89 on 2008-06-06
> **HalPomeranz said:**
> ```

find /some/dir -mtime -30 -exec basename {} \; | egrep -vi '\.jpg$' >someoutputfile

```

:-)

Sorry not quite what I wanted.
Before with ```
find /some/dir -mtime -30 | egrep -vi '\.jpg$' >someoutputfile
```

It gave an output of 
> /home/user/Music/iTunes Music
/home/user/Music/iTunes Music/3 Doors Down/Away From The Sun
/home/user/Music/iTunes Music/AC_DC/Back In Black
/home/user/Music/iTunes Music/AC_DC/For Those About To Rock
/home/user/Music/iTunes Music/AC_DC/High Voltage
/home/user/Music/iTunes Music/AC_DC/Highway to Hell
/home/user/Music/iTunes Music/Aerosmith/Aerosmith_ Gold
/home/user/Music/iTunes Music/Aerosmith/O Yeah! Ultimate Hits
/home/user/Music/iTunes Music/AFI/Decemberunderground
/home/user/Music/iTunes Music/Alien Ant Farm/ANThology
/home/user/Music/iTunes Music/Arctic Monkeys/Favourite Worst Nightmare
/home/user/Music/iTunes Music/Arctic Monkeys/Whatever People Say I Am, That's What I'
/home/user/Music/iTunes Music/Audioslave/Audioslave
/home/user/Music/iTunes Music/Avenged Sevenfold/City of Evil
/home/user/Music/iTunes Music/Bhangra Knights & Husan/Husan
/home/user/Music/iTunes Music/Biffy Clyro
/home/user/Music/iTunes Music/Black Sabbath/Paranoid
/home/user/Music/iTunes Music/Blur/Blur
/home/user/Music/iTunes Music/Bob Marley & The Wailers/Legend
/home/user/Music/iTunes Music/Bon Jovi/Crossroad
/home/user/Music/iTunes Music/Bon Jovi/Crush
/home/user/Music/iTunes Music/Bon Jovi/Slippery When Wet
/home/user/Music/iTunes Music/Choir/Unknown
/home/user/Music/iTunes Music/Chuck Berry/Roll over Beethoven
/home/user/Music/iTunes Music/Coheed and Cambria/Good Apollo, I'm Burning Star IV, Volume
/home/user/Music/iTunes Music/Coldplay
/home/user/Music/iTunes Music/Coldplay/Viva La Vida Or Death And All His Friends
/home/user/Music/iTunes Music/Coldplay/Viva La Vida Or Death And All His Friends/07 - Viva La Vida.mp3
/home/user/Music/iTunes Music/Coldplay/Viva La Vida Or Death And All His Friends/08 - Violet Hill.mp3
/home/user/Music/iTunes Music/Compilations/Familiar to Millions
/home/user/Music/iTunes Music/Coolio/Gangsta's Paradise
/home/user/Music/iTunes Music/Cream

Whereas all I want the command to do is to produce:
> /home/user/Music/iTunes Music/Coldplay/Viva La Vida Or Death And All His Friends/07 - Viva La Vida.mp3
/home/user/Music/iTunes Music/Coldplay/Viva La Vida Or Death And All His Friends/08 - Violet Hill.mp3

Hope that's a bit more clear.

Thanks

---

### Post by HalPomeranz on 2008-06-06
Ah, you want just the file names, not the directories.  Gotcha:

```

find /some/dir -mtime -30 -type f | egrep -vi '\.jpg$' >someoutputfile

```

Btw, your music library looks a lot like mine.  :-)

---

### Post by dwally89 on 2008-06-06
Thanks so much :-)
Just what I wanted.

---

### Post by dwally89 on 2008-06-07
Hi,

One other request please.

Is there a script I could run that would search through a specified file, and replace certain text with other text?

e.g. Search the file myfile.txt for the text "hello" and replace it with "goodbye"

Thanks

---

### Post by HalPomeranz on 2008-06-07
Generally you use sed for this:

```

sed 's/hello/goodbye/g' myfile.txt >newfile.txt

```

---

### Post by dwally89 on 2008-06-07
> **HalPomeranz said:**
> Generally you use sed for this:

```

sed 's/hello/goodbye/g' myfile.txt >newfile.txt

```

I just tried to run:
```
 sed 's/"/home/user/Music/iTunes Music/"/""/g' recentlyadded
```
But I got the error:
```
sed: -e expression #1, char 10: unknown option to `s'
```

What have I done wrong?

Thanks

---

### Post by ibuclaw on 2008-06-07
> **dwally89 said:**
> I just tried to run:
```
 sed 's/"/home/user/Music/iTunes Music/"/""/g' recentlyadded
```
But I got the error:
```
sed: -e expression #1, char 10: unknown option to `s'
```

What have I done wrong?

Thanks

Hello.

You've nearly got it. But unfortunately sed doesn't work like that.

Because the "/" forward slash is part of the command, you need to apply the "\" ignore symbol in all instances of "/" in the string your trying to match in order for it to run successfully.

If you want to edit the file you already have, run the command
```
sed -i 's/\/home\/user\/Music\/iTunes Music\///g' recentlyadded
```

If you'd rather save it to a new file (to make sure that the output is what you want) then run this command
```
sed 's/\/home\/user\/Music\/iTunes Music\///g' recentlyadded > recentlyadded.new
```

Regards
Iain

---

### Post by mike2357 on 2008-06-07
cat myfile.txt | mawk '{sub(/hello/,"goodbye");print}'

The syntax of awk and mawk can be tortuous.  Entire books are devoted to mawk (and awk, on which it's based), grep and other UNIX features.  It sounds like you're a good candidate for one.  I'm not trying to discourage you from posting, but ultimately it will be more satisfying to you if you learn how to write your own commands.

---

### Post by dwally89 on 2008-06-08
> **tinivole said:**
> Hello.

You've nearly got it. But unfortunately sed doesn't work like that.

Because the "/" forward slash is part of the command, you need to apply the "\" ignore symbol in all instances of "/" in the string your trying to match in order for it to run successfully.

If you want to edit the file you already have, run the command
```
sed -i 's/\/home\/user\/Music\/iTunes Music\///g' recentlyadded
```

If you'd rather save it to a new file (to make sure that the output is what you want) then run this command
```
sed 's/\/home\/user\/Music\/iTunes Music\///g' recentlyadded > recentlyadded.new
```


Regards
Iain

Thanks :-)

---

