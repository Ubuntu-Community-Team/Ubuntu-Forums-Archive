---
title: "Scripting help to parsing searching results from webpages"
date: 2008-03-05
forum: Programming Talk
---

### Post by HyperY2K on 2008-03-05
I'm trying to parse the results of a directory search ([http://www.kvno.de/buerger/arztsuche/index.html](http://www.kvno.de/buerger/arztsuche/index.html)) 
I'm already able to get a list of all search results via a bash script. For example, such a list:

[http://www.kvno.de/buerger/arztsuche/detail1.php?id=162894190](http://www.kvno.de/buerger/arztsuche/detail1.php?id=162894190)
[http://www.kvno.de/buerger/arztsuche/detail1.php?id=162893864](http://www.kvno.de/buerger/arztsuche/detail1.php?id=162893864)
[http://www.kvno.de/buerger/arztsuche/detail1.php?id=162888239](http://www.kvno.de/buerger/arztsuche/detail1.php?id=162888239)
[http://www.kvno.de/buerger/arztsuche/detail1.php?id=162863689](http://www.kvno.de/buerger/arztsuche/detail1.php?id=162863689)
[http://www.kvno.de/buerger/arztsuche/detail1.php?id=162835264](http://www.kvno.de/buerger/arztsuche/detail1.php?id=162835264)

I've found a thread "[Parsing HTML]("http://ubuntuforums.org/showthread.php?t=649379")", but I need a fast solution. I woulrd prefer a solution via bash (with sed and/or awk).
In the end, i need a result list, which retriebs from each detailpage (see above) the following date:

name of doctor (Name des Arztes)
area of expertise (Tätigkeitsbereiche/Fachgebiete)
adress (Straße - Praxis, PLZ - Praxis, Ort   Praxis)

The perfect solution would be to get directly an excel spreadsheet.

Any help is wanted :)

---

### Post by mssever on 2008-03-05
Using sed to parse HTML will be very difficult, because regular expressions are poorly suited to HTML. You need to use a library that allows you to manipulate the DOM. As far as I know, there isn't such a library for bash. You'll have to switch to some other language.

---

### Post by Cappy on 2008-03-05
```
wget -q -O- 'http://www.kvno.de/buerger/arztsuche/detail1.php?id=162894190' | sed -e 's/>/>\
/g' | sed -n '/<!-- zelle 1 -->/,/<!-- EO zelle 1 -->/p' | sed 's/<.*>//g' | grep '[[:alnum:]]' | grep -v '&nbsp;'

```
Prints out:
```

Herr
 Michael Appelshoffer
Humboldtstr. 1
 53115 Bonn-Zentrum
Tel.: (0228) 651666
T&#65533;tigkeitsbereiche
Psychotherapeutische Medizin
Psychotherapie
fach&#65533;rztlich t&#65533;tig
Fremdsprachenkenntnisse
Englisch
Spanisch

```

That's about the best you can do with bash.

---

### Post by nanotube on 2008-03-05
i would suggest python, and the beautifulsoup module.

---

### Post by HyperY2K on 2008-03-06
thank you, for the fast reply, but the solution didn't work for me. I get the following error:

debWebserver:/tmp/test# wget -q -O- 'http://www.kvno.de/buerger/arztsuche/detail1.php?id=162894190' | sed -e 's/>>\//' | sed -n '/<!-- zelle 1 -->/,/<!-- EO zelle 1 -->/p' | sed 's/<.*>//g' | grep '[[:alnum:]]' | grep -v '&nbsp;'
sed: -e expression #1, char 7: unterminated `s' command
debWebserver:/tmp/test#

---

### Post by Cappy on 2008-03-06
You have to copy and paste directly as it is. The newline needs to be included just as it is in the code.

Also, that link you provided no longer works so it will need to be replaced with a working link.

---

### Post by HyperY2K on 2008-03-06
thank you for your help. Yes it works.

---

