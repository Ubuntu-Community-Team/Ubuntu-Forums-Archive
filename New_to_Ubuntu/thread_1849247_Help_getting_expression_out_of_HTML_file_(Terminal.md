---
title: "Help getting expression out of HTML file (Terminal)"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by Dr_Frost on 2011-09-24
I really need some help with this, im trying to make a price check script for watching prices on a day to day basic, maybe even log them to see progress...

Now im trying to get a specific line out of an HTML file, i have isolated the line and i can get grep to find it, well sort of

the line in the source where the price is:
```
<span class="Stil4aa"> 139,40&nbsp;&euro;</span>
```(from today when im writing this post the price is 139.40euro)


what i did first was to download the html for local storage with ```
curl http://direkt.jacob-computer.de/Festplatten_SSD_S-ATA_OCZ_Vertex_2_Series_-_Solid-State-Disk_-_120GB_-_intern_-_6%2C4_cm_%282%2C5%22%29_-_SATA-300_%28OCZSSD2-2VTXE120G%29_artnr_776079.html >> "Vertex 2 - 120GB (2.5)"
```when i use ```
grep -o '<span class="Stil4aa">' "Vertex 2 - 120GB (2.5)"
 - I get
<span class="Still4aa">
```so far so good, i get the matching string as you would expect, but when i use ```
grep '<span class="Stil4aa">' "Vertex 2 - 120GB (2.5)"
``` without -o i get a lot of cr*p, like 100's of lines from the HTML starting at some point far above the line im searching for, and even adding **| grep** after does not help

what i want to achive here is just getting the full line like ```
 <span class="Stil4aa"> 139,40&nbsp;&euro;</span>
``` cause then it is just a question of AWK to get the price out of the HTML....

Do anybody have any ideas to this, it's driving me MAD..., i know im just missing something simple, i have tried all commands i can find from **man grep** and still no luck.


Source:
[http://direkt.jacob-computer.de/Festplatten_SSD_S-ATA_OCZ_Vertex_2_Series_-_Solid-State-Disk_-_120GB_-_intern_-_6%2C4_cm_%282%2C5%22%29_-_SATA-300_%28OCZSSD2-2VTXE120G%29_artnr_776079.html](http://direkt.jacob-computer.de/Festplatten_SSD_S-ATA_OCZ_Vertex_2_Series_-_Solid-State-Disk_-_120GB_-_intern_-_6%2C4_cm_%282%2C5%22%29_-_SATA-300_%28OCZSSD2-2VTXE120G%29_artnr_776079.html)

---

### Post by staticd on 2011-09-24
The grep -o returns only the part that matched.
Try 
```

grep -o '<span class="Stil4aa">[^<]*</span>'

```

---

### Post by sanderd17 on 2011-09-24
The file is encoded using windows end of lines.

So to grep the entire file is only one line, while text editors like gedit might see this and read it correctly.

---

### Post by sisco311 on 2011-09-24
You can't realistically parse tag-based markup languages like HTML and XML using Bash or utilities such as grep, sed or cut. For parsing out pieces of data, see tidy and xmlstarlet or xmlgawk or xpath or xml2, or learn xslt. See: [http://www.codinghorror.com/blog/archives/001311.html](http://www.codinghorror.com/blog/archives/001311.html)

---

### Post by Dr_Frost on 2011-09-24
damm that was some fast responses.

When using gedit, the html is looking fine, the same with cat.

But the **grep -o '<span class="Stil4aa">[^<]*</span>' **worked just fine 

Thank you so much :) :)

can't believe that it was that simple, but i knew it would be something simple i missed....

Think ill mark this as solved.

---

### Post by Dr_Frost on 2011-09-24
by doing
```
grep -o '<span class="Stil4aa">[^<]*0' "Vertex 2 - 120GB (2.5)" | awk '{print $3}'
```
i get the actual value :)

just changed the end of the grep to *0 instead of *</span>, all their prices end with 0 anyway

---

