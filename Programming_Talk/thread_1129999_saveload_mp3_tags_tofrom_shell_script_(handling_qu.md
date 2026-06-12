---
title: "save/load mp3 tags to/from shell script (handling quotes and newlines)???"
date: 2009-04-19
forum: Programming Talk
---

### Post by kung fu buntu on 2009-04-19
I want to dump mp3 tags to a file and then restore then latter (not necessarily on the same computer).
I'm using mp3info2 to handle mp3 tags.

Since I want to restore my tags latter on, I was thinking on using shell variables, which would allow me to do:
mp3info2 -y $MP3_YEAR  foobar.mp3

Now, the problem is that mp3 tags can have quotes (both single and double) and newlines (consider the comment field).
So I need to dump my tags in a decent format, like this:

MP3_TRACKNAME='the end of all you\'ll know'
MP3_COMMENT='this is a comment

and this is a newline'


With the help from people from #bash, I'm now able to do this.

```
MP3_FILE=foobar.mp3
META_FILE=foobar.metamp3
echo "MP3_ARTIST='$(mp3info2 -p "%a" "$MP3_FILE" | sed "s/['\"]/\\\\\0/g" | sed 's/$//')'" > "$META_FILE"
```

The problem is that I have to check each tag at a time, which means sloooooooooooooooooooooooowwwwnnnneeeesssss, 1.5 seconds for a single track :(


I can dump all tags with just a single mp3info2 execution, but the results don't get properly formated (ie, problems with quotes and newlines).
```
mp3info2 -p "MP3_ARTIST='%a'\nMP3_COMPOSER='%{TCOM}'\nMP3_ALBUM='%l'\nMP3_YEAR='%y'\nMP3_TRACKNUM='%n'\nMP3_TRACKNAME='%t'\nMP3_COMMENT='%c'\nMP3_GENRE='%g'\n"   "$MP3_FILE"
```



Any ideas on the best way to do this?

---

### Post by ghostdog74 on 2009-04-19
please dump all tags, then show a small sample of the dumped file, and describe how you want the output to look like.

---

### Post by kung fu buntu on 2009-04-19
```
$ mp3info2 -p "MP3_ARTIST=%a\nMP3_COMPOSER=%{TCOM}\nMP3_ALBUM=%l\nMP3_YEAR=%y\nMP3_TRACKNUM=%n\nMP3_TRACKNAME=%t\nMP3_COMMENT=%c\nMP3_GENRE=%g\n"      01\ -\ the\ end\ of\ all\ you\'ll\ know.mp3

MP3_ARTIST=Scott Matthew
MP3_COMPOSER=foooooooobar
MP3_ALBUM=Ghost In The Shell: Stand Alone Complex O.S.T. 3
MP3_YEAR=2005
MP3_TRACKNUM=1
MP3_TRACKNAME=the end of all you'll know
MP3_COMMENT=this is a comment
with some "double quotes" and 'quotes'
and this is a newline
MP3_GENRE=Anime
```
note that using mp3info2 gives me a bit of freedom, for example I have to put \n for printing purposes here, and I can put my tags between "" or '' if I wish so.
I could also have done: mp3info2 -p "%a%{TCOM}%l%y\n"


My desired output is this in a text file:
```
MP3_ARTIST='Scott Matthew'
MP3_COMPOSER='foooooooobar'
MP3_ALBUM='Ghost In The Shell: Stand Alone Complex O.S.T. 3'
MP3_YEAR='2005'
MP3_TRACKNUM='1'
MP3_TRACKNAME='the end of all you\'ll know'
MP3_COMMENT='this is a comment
with some \"double quotes\" and \'quotes\'
and this is a newline'
MP3_GENRE='Anime'

```

---

### Post by ghostdog74 on 2009-04-19
```

awk -F= 'BEGIN{q="\047";dq="\042";slash="\134"}
{ gsub(q,slash q); gsub(dq,slash dq)}
/^MP3/{$2=q $2 q}1' OFS="=" file

```
output
```

# ./test.sh
MP3_ARTIST='Scott Matthew'
MP3_COMPOSER='foooooooobar'
MP3_ALBUM='Ghost In The Shell: Stand Alone Complex O.S.T. 3'
MP3_YEAR='2005'
MP3_TRACKNUM='1'
MP3_TRACKNAME='the end of all you\'ll know'
MP3_COMMENT='this is a comment'
with some \"double quotes\" and \'quotes\'
and this is a newline
MP3_GENRE='Anime'


```

---

### Post by kung fu buntu on 2009-04-20
Thanks for the help ghostdog74.
But the output with the gawk script differs from the desired output; take a look at the MP3_COMMENT and you can see that the quotes show at different places.
On another note, neither was my desired output the correct one (since I couldn't use it in a shell script).

So again...

My input:
```
MP3_ARTIST=Scott Matthew
MP3_COMPOSER=foooooooobar
MP3_ALBUM=Ghost In The Shell: Stand Alone Complex O.S.T. 3
MP3_YEAR=2005
MP3_TRACKNUM=1
MP3_TRACKNAME=the end of all you'll know
MP3_COMMENT=this is a comment
with some "double quotes" and 'quotes'
and this is a newline
MP3_GENRE=Anime
```

Desired output:
```
MP3_ARTIST="Scott Matthew"
MP3_COMPOSER="foooooooobar"
MP3_ALBUM="Ghost In The Shell: Stand Alone Complex O.S.T. 3"
MP3_YEAR="2005"
MP3_TRACKNUM="1"
MP3_TRACKNAME="the end of all you'll know"
MP3_COMMENT="this is a comment
with some \"double quotes\" and 'quotes'
and this is a newline"
MP3_GENRE="Anime"
```

I never used gawk but will take a look at it from your script and see if I can get something... If I do, I'll post here.

---

### Post by ghostdog74 on 2009-04-20
so you only want to put escape slash among your MP3_COMMENT, correct? what language are you familiar with then?

---

### Post by kung fu buntu on 2009-04-20
No, not that.
I need to put escape slashes whenever the original output has then. Additionally I need put double quotes on the beginning and end of a tag.
A track name can have a double quote as well, for example it could be named: *"viva la vida"*

If you grab my desired output, put it in a shell script and echo the variables, you will see that it prints the exact same information than the original input.

```
#!/bin/bash

MP3_ARTIST="Scott Matthew"
MP3_COMPOSER="foooooooobar"
MP3_ALBUM="Ghost In The Shell: Stand Alone Complex O.S.T. 3"
MP3_YEAR="2005"
MP3_TRACKNUM="1"
MP3_TRACKNAME="the end of all you'll know"
MP3_COMMENT="this is a comment
with some \"double quotes\" and 'quotes'
and this is a newline"
MP3_GENRE="Anime"

echo "MP3_ARTIST=$MP3_ARTIST"
echo "MP3_COMPOSER=$MP3_COMPOSER"
echo "MP3_ALBUM=$MP3_ALBUM"
echo "MP3_YEAR=$MP3_YEAR"
echo "MP3_TRACKNUM=$MP3_TRACKNUM"
echo "MP3_TRACKNAME=$MP3_TRACKNAME"
echo "MP3_COMMENT=$MP3_COMMENT"
echo "MP3_GENRE=$MP3_GENRE"

```

I know C, C++, Java and "some" shell script (a bit of sed too, I just never touched awk before).
I just need something that works and I thought it made sense to have something in shell script (that may include the use of sed and awk).

---

### Post by kung fu buntu on 2009-04-20
I was able to work around the issue, but to my dismay mp3info2 isn't updating tags, it complains about:
*Writing of ID3v2.4 is not fully supported (prohibited now via `write_v24').*

This is sad =(


Anyway, my solution was:
```
token="MP3INFO2_END_OF_TAG"
mp3info2 -p "MP3_ARTIST=%a$token\nMP3_COMPOSER=%{TCOM}$token\nMP3_ALBUM=%l$token\nMP3_YEAR=%y$token\nMP3_TRACKNUM=%n$token\nMP3_TRACKNAME=%t$token\nMP3_COMMENT=%c$token\nMP3_GENRE=%g$token\n"   "$MP3_FILE"  |  sed "s/\"/\\\\\"/g"  |  sed "s/$token/\"/g"  |  sed "s/\(MP3_.*=\)/\1\"/g"  >> "$META_FILE"
```

Now I'll have to find another tool that allows me to dump/restore the mp3 tags to/from a file =(

back to square zero...

---

