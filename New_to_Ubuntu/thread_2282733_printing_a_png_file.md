---
title: "printing a png file"
date: 2015-06-16
forum: New to Ubuntu
---

### Post by wimpy2 on 2015-06-16
I have a network printer on a home LAN, controlled by an old WinXP PC. So far I can print documents easily from any linux PC on the home LAN, using apps such as leafpad. I have a png file on a lubuntu PC, which I would like to print. None of the image viewing apps in lubuntu seem to have a Print function. How do I get to print it?
Any help or suggestions would be greatly appreciated.

---

### Post by steeldriver on 2015-06-16
One fairly easy way would be to drop it into a blank document in whatever word-processing application, and print it from there e.g. in LibreOffice, Insert --> Image --> From file...

---

### Post by Dennis N on 2015-06-16
> None of the image viewing apps in lubuntu seem to have a Print function. How do I get to print it?
For the .png file, I use Gimp for printing such things. On Lubuntu, you would need to install Gimp.

---

### Post by wimpy2 on 2015-06-16
Thank you, **steeldriver**and** Dennis N**. I didn't have gimp or Libreoffice on this PC, but it did have Abiword. I tried that and it worked just fine.
I'm really grateful for your help and suggestions. I'll mark this as solved.

---

### Post by howefield on 2015-06-16
You could also use the command line using the lpr command, eg

```
lpr path/to/file
```

would send to the default printer in the absence of specifying one.

See 

```
man lpr
```

for more info.

---

### Post by ajgreeny on 2015-06-16
For maximum flexibility and ease of use, have a look at **photoprint** from the repos, which gives you lots of options regarding the number of pics per page, their printed size, and their layout on the page.  I have found it very useful in the past, though I print very little these days.

---

### Post by wimpy2 on 2015-06-18
@**howefield** Thanks for the reply. I tried **lpr** with the png file but it kept coming back with a "file or folder not found" message, which was odd, since the file was definitely in the folder. Trying **lpr** with other png files in the folder elicited the same response. **lpr** had no difficulty in printing a text file in the folder to the network printer.
@**ajgreeny** Thanks for the reply. I will try **photoprint** at some stage but this is not an exercise I often do, so it may be some time before it needs to be done again.

---

