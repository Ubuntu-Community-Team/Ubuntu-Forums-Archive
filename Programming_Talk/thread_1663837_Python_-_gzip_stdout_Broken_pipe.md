---
title: "Python - gzip: stdout: Broken pipe"
date: 2011-01-10
forum: Programming Talk
---

### Post by wallywally on 2011-01-10
I've recently begun trying to teach myself Python to pass the time whilst stuck at home with kids and to this end I have been working through Think Python. I have no programming experience other than that gained from this text in the last few weeks.

Unfortunately I have come up against a problem with exercise 7 in chapter 14 of the book which I have been unable to solve.

The exercise is here: [http://en.wikibooks.org/wiki/Think_Python/Files#Exercises](http://en.wikibooks.org/wiki/Think_Python/Files#Exercises)

The problem I have is in trying the following example given by the author:

```
import imdb

def print_info(actor, date, title, role):
    print actor, date, title, role

imdb.process_file('actors.list.gz', print_info)
```

For me produces 62 lines of appropriate text before ending with gzip: stdout: Broken pipe

These are the last few lines of output:

[I]'t Joen, L&#65533;on (1971) Jack l'&#65533;ventreur  [Jack the Ripper]
'The Jeweler', Jacob (2008) Blind Thoughts  [Mike]
'The Jeweler', Jacob (2002) Paper Soldiers  [Joshua Rosen]
'The Jeweler', Jacob (2002) State Property  [Eli]
'The Onion' Editorial Staff (2005) The Aristocrats  [Themselves]
'Ulaleo, Ka'olelo (1990) Pele's Appeal  None
'&#65533;', Oswald (1987) Skate - O Esporte Emo&#65533;&#65533;o  [Himself]

gzip: stdout: Broken pipe[/I]


If I adjust the example to work on actresses.list.qz instead then all is fine and so I assume that the problem is with the actors file rather than anything else. That said, I am at a complete loss as to what to do next to find a solution. Please help!

FWIW I am using Ubuntu 10.10 and Python 2.6.6

---

### Post by gmargo on 2011-01-10
You can use the -t option on gzip to test the downloaded actors file.

---

### Post by psusi on 2011-01-10
It sounds like imdb.process_file() is deciding it is done before reaching the end of the file, and so it hangs up on gzip, which is complaining that it got hung up on before it finishes decompressing the whole file.

---

### Post by wallywally on 2011-01-11
gzip -t -z reports that the file is OK.

psusi's explanation sounds likely but what can I do about it?

Anyway I've decided that I can complete the exercise in the book using a different compressed list from the IMDB (directors or producers etc) and so I'll do that rather than getting hung up on problems with gzip.

---

### Post by aliking on 2011-02-03
By coincidence, I reached the same place in ThinkPython just this week and came up against the same issue. This doesn't match with my definition of '[SOLVED]' so I had a bit of a dig into imdb.py (which is here [http://thinkpython.com/code/imdb.py]("http://thinkpython.com/code/imdb.py") by the way)

Anyway the culprit is this:
```
for line in fp:
        line = line.rstrip()
        if line == '': continue
        if line[0] == '-': break
```
which was designed to catch the end of the actors in the IMDB text archive, but which now chokes near the beginning because of three actors who are apparently called Amy -, Manolo - and Isaiah Entsua-Mensah.

I've updated my copy of the imdb.py to have this instead:
```
for line in fp:
        line = line.rstrip()
        if line == '': continue
        if line[0:5] == '------': break
```

which should solve the problem until IMDB change their formatting or and actor called Charles ------ becomes famous.

I guess I'll let the people at green tea press know too...

a

---

