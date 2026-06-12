---
title: "Need help to create a bash script"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2014-01-19
Hi Friends,


I need help to create a bash script. I use exiftool command to update metadata of a pdf file in following format


```
exiftool -Subject="Some Text:DD-MMM-YYYY" -Title="Some Text: DD-MMM-YYYY"-[COLOR=#000000][FONT=helvetica]ModDate[/FONT][/COLOR][COLOR=#000000][FONT=helvetica]=&#8221;YYYY:mm:dd HH:MM:SS&#8221; -CreationDate=&#8221;YYYY:mm:dd HH:MM:SS&#8221; filenameDDMMYYYY.pdf[/FONT][/COLOR]



```
[COLOR=#000000][FONT=helvetica]
I need to create a bash script which get current date and time and replace DD with date in format like 04, MM in format  like 01, MMM informat like Jan, HH:MM:SS, in format like 08:45:34 and YYYY in format like 2014 and script replace all DD, MM, MMM, YYYY, HH:MM:SS and then execute the command[/FONT][/COLOR]


[COLOR=#000000][FONT=helvetica]Canany one help me create the script?[/FONT][/COLOR]


[COLOR=#000000][FONT=helvetica]Thanksin advance[/FONT][/COLOR]

---

### Post by codemaniac on 2014-01-19
***date*** command is your friend. Few examples below. :)

```

fego@production:~$ date +%b
Jan
fego@production:~$ date +%d
20
fego@production:~$ date +%m
01
fego@production:~$ date +%T
00:33:44

```

---

### Post by sujitrjadhav on 2014-01-19
Thanks very much. codemaniac. I did not know anything about bash programming. But after some trial and error I am able to create a script that does what I want.

---

