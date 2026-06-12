---
title: "Grep highlight possible with full output?"
date: 2009-07-25
forum: Programming Talk
---

### Post by Gen2ly on 2009-07-25
Hey guys.  I'd like to be able to get the output of a command and have a certain part of it highlighted but like to have the whole output displayed.  I know grep is for search lines and I looked at the man page so using grep probably isn't the way to go.  Any idea on how to highlight just one line or certain text on a full output??

---

### Post by sanderj on 2009-07-25
Maybe you mean something like this:

> grep -i --color -A 111111 -B 99999999 -e elburg -e son namenlijst.txt 

This will highlight all words "elburg" and "son" (case-insensitive) in the file namenlijst.txt, and will send that output to the stdout.





```
ubuntu@ubuntu:~$ grep -i --color -A 111111 -B 99999999 -e elburg -e son namenlijst.txt 
              <option value="almere">Almere </option>
              <option value="bathmen">Bathmen </option>

              <option value="berkel">Berkel en Rodenrijs</option>
              <option value="deventer">Deventer</option>
              <option value="dordrecht">Dordrecht</option>
              <option value="dronten">Dronten</option>
              <option value="[COLOR="Red"]elburg[/COLOR]">[COLOR="Red"]Elburg[/COLOR]</option>
              <option value="enschede">Enschede</option>

              <option value="haaksbergen">Haaksbergen</option>
              <option value="hilversum">Hilversum</option>
              <option value="holten">Holten</option>
              <option value="lochem">Lochem</option>
              <option value="nijkerk">Nijkerk</option>
              <option value="nijmegen">Nijmegen</option>

              <option value="rijssen">Rijssen</option>
              <option value="schijndel">Schijndel</option>
              <option value="oedenrode">Sint-Oedenrode</option>
              <option value="[COLOR="Red"]son[/COLOR]">[COLOR="Red"]Son[/COLOR] en Breugel</option>
              <option value="uden">Uden</option>
              <option value="veenendaal">Veenendaal</option>

              <option value="veghel">Veghel</option>
              <option value="zeewolde">Zeewolde</option>


ubuntu@ubuntu:~$ 
```

---

### Post by Gen2ly on 2009-08-17
Yikes! I thought I responded to this.  Ohhhhh.

Dam, sanderj, very nice.  Very very useful.  Thank you.

---

### Post by deadroot on 2011-09-02
**_ look at a general purpose highlighting tool called histring_**[I]

 Highlighting strings in text output with histring:[/I]

histring simply highlights strings using ANSI terminal escape  codes.  It is extremely small and lighting fast. I almost use it  everywhere in my script where I need a quick peek into large output.   Moreover, you almost don't need to learn it, as its syntax is almost  identical to grep.

A Debian package is available through the grml repository:

  just add one of the following to your /etc/apt/sources.list

# stable repository:
deb     [http://deb.grml.org/](http://deb.grml.org/) grml-stable  main   
deb-src [http://deb.grml.org/](http://deb.grml.org/) grml-stable  main  

# testing/development repository:
deb     [http://deb.grml.org/](http://deb.grml.org/) grml-testing main
deb-src [http://deb.grml.org/](http://deb.grml.org/) grml-testing main


then:

sudo apt-get update && sudo apt-get install histring



* I use to find PID for example:*

top | histring firefox 

*to find the PID of firefox-bin process for killing (just k the PID + signal  instead of ps aux|grep firefox and kill command ! ) and so on...*




***for more :***
[http://www.debian-administration.org/articles/464](http://www.debian-administration.org/articles/464)
man histring
histring --help

---

### Post by ofnuts on 2011-09-02
> **deadroot said:**
> 

* I use to find PID for example:*

top | histring firefox 

*to find the PID of firefox-bin process for killing (just k the PID + signal  instead of ps aux|grep firefox and kill command ! ) and so on...*


Hmmmm.
```

>>> pidof firefox-bin[I]
13706[/I]

```
:)

---

