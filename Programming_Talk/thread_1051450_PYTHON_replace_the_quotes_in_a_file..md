---
title: "PYTHON: replace the quotes in a file."
date: 2009-01-26
forum: Programming Talk
---

### Post by trypeace2day on 2009-01-26
Hello,
I have a comma delimited file that is exported from one program. I want to use this text file in Python. 
Some of the fields have double quotes (") for the text.

If I go into the file itself and get rid of the double quotes, my script is very happy and works the way I want it to.

Now I have to deal with the quotes, as I have a lot of files that I cannot open manually.

Currently my reading of the file is:
#---------------------------------------
numberOfLines = 0
numberOfSkippedLines = 0
gpsLine = ""
coord = ""

try:
    f=open(gpsFile, 'r')
   
    while gpsLine.isalnum:
        gpsLine = f.readline()
        if not gpsLine: break
        numberOfLines = numberOfLines + 1
        linesp = gpsLine.split(',',14)
#----------------------------------------

I would like to add something to read the file and replace the double quotes with nothing. 

Any help would be appreciated!!!

Peace.:D:D

---

### Post by snova on 2009-01-26
> **trypeace2day said:**
> ```
numberOfLines = 0
numberOfSkippedLines = 0
gpsLine = ""
coord = ""

try:
    f=open(gpsFile, 'r')
   
    while gpsLine.isalnum:
        gpsLine = f.readline()
        if not gpsLine: break
        numberOfLines = numberOfLines + 1
        linesp = gpsLine.split(',',14)

```

Please use [noparse]```

```[/noparse] tags for code, it makes it easier to read. See?

Anyway, I'm not sure what you want, but if you're trying to remove quotes from each field, try adding something like this:

```
        for index in range(len(linesp)):
            linesp[index] = linessp[index].strip('"')
```

That can be shorted to this if you like:

```
        linesp = map(lambda x: x.strip('"'), linesp)
```

---

### Post by ghostdog74 on 2009-01-26
are you really sure you want to remove the double quotes? If you have CSV field that consists of say, first and last name, if you remove the quotes, they will have totally different meaning.

---

### Post by slavik on 2009-01-26
try this :)

```
sed 's/\"//g' < file > newfile
```

---

### Post by eye208 on 2009-01-27
> **slavik said:**
> try this :)

```
sed 's/\"//g' < file > newfile
```
Uh oh ... you just presented a solution that is

a) short

and

b) not Python.

Expect the Python fanboys to call you a troll in 3...2...1...

---

### Post by myrtle1908 on 2009-01-27
Wouldn't it be best to use the Python csv lib? ... [http://docs.python.org/library/csv.html](http://docs.python.org/library/csv.html)

---

### Post by trypeace2day on 2009-01-27
Thank you, Everyone, for your responses. You all have made my day. I learned some new ideas and solved my current issue.

I ended up using the code 


```
linesp = map(lambda x: x.strip('"'), linesp)
```


and it works great.

---

