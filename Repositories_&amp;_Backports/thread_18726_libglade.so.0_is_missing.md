---
title: "libglade.so.0 is missing"
date: 2005-03-08
forum: Repositories &amp; Backports
---

### Post by flashdog on 2005-03-08
Hello,
I can't find **libglade.so.0** for my printer Canon i550.

```

# cd /bjfiltercups-2.2/usr/local/bin
# bjcupsmon
bjcupsmon: error while loading shared libraries: libglade.so.0: cannot open shared object file: No such file or directory 

``` 

How can I find this libary?

regards

---

### Post by bored2k on 2005-03-08
[QUOTE=flashdog]Hello,
I can't find **libglade.so.0** for my printer Canon i550.

```

# cd /bjfiltercups-2.2/usr/local/bin
# bjcupsmon
bjcupsmon: error while loading shared libraries: libglade.so.0: cannot open shared object file: No such file or directory 

``` 

How can I find this libary?

regards[/QUOTE]
 > root@noir:/home/user # locate libglade.so.0
root@noir:/home/user #

It's not here either .

You should learn how to use updatedb, updated, it will find you're files in less than 0.5 seconds, as it looks them up in a database created for it.

> man updatedb; man locate

---

### Post by flashdog on 2005-03-08
I make:

```

root@laptop:/home/flashdog # locate libglade.so.0
warning: locate: could not open database: /var/lib/slocate/slocate.db: No such file or directory

``` 

Before I install :

```

alien --to-deb bjfiltercups-2.2-1.i386.rpm
alien --to-deb bjfilterpixus550i-2.2-1.i386.rpm
dpkg -i bjfiltercups_2.2-2_i386.deb
bjfilterpixus550i_2.2-2_i386.deb 
ldconfig
/etc/init.d/cupsys restart

# alien -g bjfiltercups-2.2-1.i386.rpm
Directories bjfiltercups-2.2 and bjfiltercups-2.2.orig prepared.

# alien -g bjfilterpixus550i-2.2-1.i386.rpm
Directories bjfilterpixus550i-2.2 and bjfilterpixus550i-2.2.orig prepared. 

```

---

### Post by bored2k on 2005-03-08
[QUOTE=flashdog]I make:

```

root@laptop:/home/flashdog # locate libglade.so.0
warning: locate: could not open database: /var/lib/slocate/slocate.db: No such file or directory

``` 

[/QUOTE]

Ubuntu has by default locate disabled.

you have to:

> #touch /var/lib/slocate/slocate.db
then do > updatedb

This will index you're files, u will see the terminal doing "nothing" but ur pc's LED screaming like wild. After thats done

Try locate again.


You have to do updatedb every couple of days or so to keep the index updated. Its a lot better than "find" or anything else.

---

### Post by Kimm on 2005-03-08
if you are missing a library file you can go to rpm.pbone.net and make a search for the missing file. The site will then list all packages (that it knows of) that contains this file... you have to use alien to convert it to a .deb package

I would be carefull though, installing libraries downloaded from there ruined my linux completely two times... (secund time, I was unable to run programs or commands what so ever...)

so... ehm... never mind, dont use that site :P just serach for the file on google or something, I'm sure some library will show up that you can install, perhaps from source? (for some reason that feels safer...)

---

### Post by bored2k on 2005-03-08
[QUOTE=Kimm]if you are missing a library file you can go to rpm.pbone.net and make a search for the missing file. The site will then list all packages (that it knows of) that contains this file... you have to use alien to convert it to a .deb package

I would be carefull though, installing libraries downloaded from there ruined my linux completely two times... (secund time, I was unable to run programs or commands what so ever...)

so... ehm... never mind, dont use that site :P just serach for the file on google or something, I'm sure some library will show up that you can install, perhaps from source? (for some reason that feels safer...)[/QUOTE]
 lol 

Only app id download from bone would be amsn skins no arch .

---

### Post by flashdog on 2005-03-10
Hello,
I made the following:

```

# touch /var/lib/slocate/slocate.db
# updatedb
# cd bjfiltercups-2.2/usr/local/bin
# bjcupsmon
# bjcupsmon bjcupsmon: error while loading shared libraries: libglade.so.0: cannot open shared object file: No such file or directory

``` 
but the error remained.

Where does the error lie with me?

I found the following 
[page](http://linux2ch.bbzone.net/index.php?FAQ%2FPrinting) 

```

# alien -d libglade-0.17-12.2.i386.rpm
# alien -d libxml-1.8.17-10.1.2.i386.rpm
# dpkg -i libglade_0.17-13.2_i386.deb libxml_1.8.17-11.1_i386.deb
bjfilterpixus560i_2.4-1_i386.deb bjfiltercups_2.4-1_i386.deb


``` 

Who can I find this rpm?

---

### Post by flashdog on 2005-03-11
I found the packege on rpmfind.net!

Now I don't have errors!

---

