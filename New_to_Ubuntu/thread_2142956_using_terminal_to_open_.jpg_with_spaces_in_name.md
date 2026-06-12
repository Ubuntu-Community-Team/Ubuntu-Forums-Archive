---
title: "using terminal to open .jpg with spaces in name"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-05-07
okay what am i doing wrong trying to open with last .jpg with gpciview . first i used tab competition and got the following results
THIS IS A LINUX COMPUTER HAVE FUN
HAVE A GREAT DAY
ray@ray-GC660AA-ABA-SR5123WM:~$ gpicview / T
ray@ray-GC660AA-ABA-SR5123WM:~$ gpicview / T
Templates/
thanksgiving wallpapers/
timezone
toon175y25 (1).jpg
top-ten-3d-wallpapers-1.jpg
Tux Happy Holidays Wallpapers Christmas Penguin in the Snow.jpg
ray@ray-GC660AA-ABA-SR5123WM:~$ gpicview / T

then lost can use qpicview "Tux etc" wont work. tks

---

### Post by PowerBarry43 on 2013-05-07
[HR][/HR]Hi there

Remember linux is Case sensetivve with a capital "C" ;) try using a lower case t with tab completion. You can get around spaces in a filename by adding a \ before them or quoting the whole string eg. 

filename-with-a\ space-in-it.jpg

"filename-with-a space-in-it.jpg"

Hope this helps!!

Barry

Edit: sorry i didn't see that last jpg. Capital T is indeed correct. Try this:

```
gpicview ~/Tux\ Happy\ Holidays\ Wallpapers\ Christmas\ Penguin\ in\ the\ Snow.jpg
```

---

### Post by rburkartjo on 2013-05-07
power tks but is there a easier way by using a wild card like * to cut down on the typing? i know there is but i just cant recall.

---

### Post by 3rdalbum on 2013-05-07
You can also drag and drop files to the terminal to fill in their file path. That saves you having to type such a long filename! It also ensures that the spaces in the filename are escaped out (Tux\ Happy\ Holidays etc) or that the filename is fully quoted ("Tux Happy Holidays" etc).

---

### Post by 3rdalbum on 2013-05-07
> **rburkartjo said:**
> power tks but is there a easier way by using a wild card like * to cut down on the typing? i know there is but i just cant recall.

I just posted an easy way to cut down on the typing, but yes you can use wildcards. Especially handy when opening more than one file.

```
gpicview Tux*
```

---

### Post by rburkartjo on 2013-05-07
3rd that was what i was looking for tks

---

### Post by pqwoerituytrueiwoq on 2013-05-07
you can use quotes also
[FONT=courier new]gthumb "/home/$USER/Pictures/My Picture.jpg"
gthumb /home/$USER/Pictures/"My Picture.jpg"[/FONT]

---

### Post by rburkartjo on 2013-05-07
and also tks pq

---

### Post by PowerBarry43 on 2013-05-10
in this situation I think the easiest way would be to type 
gpicview ~/T 
then hit TAB

Hope this helps!
Barry

---

