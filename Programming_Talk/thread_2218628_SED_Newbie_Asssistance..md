---
title: "SED Newbie Asssistance."
date: 2014-04-21
forum: Programming Talk
---

### Post by ylafont on 2014-04-21
Forgive my ignorance, I am new to SED and it is not easy to wrap your head around it. I have he following file.

```
SCANNING: 997750000 (us-hrc:158)
LOCK: none (ss=69 snq=0 seq=0)
SCANNING: 993000000 (us-irc:157, us-cable:157)
LOCK: none (ss=69 snq=0 seq=0)
SCANNING: 991750000 (us-hrc:157)
LOCK: none (ss=70 snq=0 seq=0)
SCANNING: 609000000 (us-irc:88, us-cable:88)
LOCK: qam256 (ss=100 snq=100 seq=100)
TSID: 0x0132
PROGRAM 286: 366 Showtime W (encrypted)
PROGRAM 288: 368 Showtime Showca (encrypted)
PROGRAM 290: 370 Showtime Too W (encrypted)
PROGRAM 292: 372 Showtime Beyond (encrypted)
PROGRAM 294: 374 Showtime Extrem (encrypted)
PROGRAM 302: 386 TMC W (encrypted)
PROGRAM 304: 388 TMC Xtra W (encrypted)
PROGRAM 306: 391 Flix West (encrypted)
PROGRAM 314: 427 Thriller Max We (encrypted)
PROGRAM 356: 409 HBO Comedy West (encrypted)
PROGRAM 358: 411 HBO Zone West (encrypted)
PROGRAM 505: 107 BBC World (encrypted)
SCANNING: 603000000 (us-irc:87, us-cable:87)
LOCK: qam256 (ss=100 snq=100 seq=100)
TSID: 0x0200
PROGRAM 195: 211 MTV 2 (encrypted)
PROGRAM 197: 213 MTV Jams (encrypted)
PROGRAM 198: 214 MTV Hits (encrypted)
PROGRAM 201: 218 VH1 Classics (encrypted)
PROGRAM 202: 219 VH1 Soul (encrypted)
PROGRAM 203: 187 Logo (encrypted)
PROGRAM 207: 222 CMT Pure Countr (encrypted)
PROGRAM 225: 253 Nick Too (encrypted)
PROGRAM 226: 254 Nick Toons (encrypted)
PROGRAM 227: 255 Teen Nick (encrypted)
PROGRAM 324: 273 MTV MUSICA Y MA (encrypted)
PROGRAM 512: 339 Barker 4 - Merc
PROGRAM 513: 0
PROGRAM 514: 500 Barker 6 - Quan
PROGRAM 527: 1508 WAPA TV (encrypted)

```

I have managed to create the two sed lines that will isolate the frequency (997750000 ) number  and the channel listing  (512: 339 Barker 4 - Merc) for each frequency. 

```
#!/bin/sh


sed -nr '
	s/.*SCANNING: ([0-9]+{6,12}).*/\1/p
	s/ \(encrypted\)// ; s/: 0/d ; s/://; s/.*PROGRAM ([0-9]{1,7})+/\1/p


' FileToSearch

```

I have been  playing around without success in trying to store the first line in the buffer and printing along each of the channel listing lines.  Ideally, i would like to delete frequencies that do not have channels. Is this possible? or should i be using a different tool?

Final output should look like this


609000000 286 366 Showtime W
609000000 288 368 Showtime Showca
609000000 290 370 Showtime Too W
603000000 195 211 MTV 2
603000000 197 213 MTV Jams
603000000 198 214 MTV Hits
603000000 201 218 VH1 Classics
603000000 202 219 VH1 Soul
603000000 203 187 Logo

---

### Post by erind on 2014-04-21
> **ylafont said:**
> [...]

I have been  playing around without success in trying to store the first line in the buffer and printing along each of the channel listing lines.  Ideally, i would like to delete frequencies that do not have channels. Is this possible? or should i be using a different tool?

[...]


With sed that might be a strech, so try this awk code instead: 

```
awk  '/^SCANNING:/{ s=$2 }
      /^PROGRAM/ && !/: 0$/ { 
            gsub(/PROGRAM|[ \t]*\(encrypted\)|:/,"");  print s " " $0 
      } ' filename
```

Note that the code is based strictly on your input format and your posted output doesn't fully match your requirement, so I'm guessing a typo up there.

---

### Post by steeldriver on 2014-04-21
It's *possible *in sed, I think - but IMHO definitely not a sed newbie assignment. You'd need to store the most recently matched frequency in the sed *hold buffer* e.g.

```

sed -nr \
'/^SCANNING: ([0-9]+).*$/{s//\1/;h}' 

```

This makes use of a *capture group* ([0-9]+) enclosing the sequence of one or more digits which is then back substituted in place of the whole pattern and copied into the hold buffer {s//\1/;h}. When you match the ^PROGRAM string, first make all the substitutions / deletions on the matched pattern space

```

/^PROGRAM/{s///; /: 0$/d; s/://; s/ \(encrypted\)//; 

```

and then append the contents of the hold buffer (i.e. the most recently matched frequency value) to it; and finally rearrange the result to get the frequency at the start of the line
```

G;s/(.*)\n(.*)/\2\1/p}

```
The last step is necessary because AFAIK there's not a direct way to *prepend *the hold buffer to the pattern space. 

Putting it all together:
```

#!/bin/sh

sed -nr \
-e '/^SCANNING: ([0-9]+).*$/{s//\1/;h}' \
-e '/^PROGRAM/{s///; /: 0$/d; s/://; s/ \(encrypted\)//; G;s/(.*)\n(.*)/\2\1/p}' "$1"

```

where "$1" is the filename argument passed on the script command line. Testing it with your supplied listing text:

```

$ ./ylafont.sh listing.txt
609000000 286 366 Showtime W
609000000 288 368 Showtime Showca
609000000 290 370 Showtime Too W
609000000 292 372 Showtime Beyond
609000000 294 374 Showtime Extrem
609000000 302 386 TMC W
609000000 304 388 TMC Xtra W
609000000 306 391 Flix West
609000000 314 427 Thriller Max We
609000000 356 409 HBO Comedy West
609000000 358 411 HBO Zone West
609000000 505 107 BBC World
603000000 195 211 MTV 2
603000000 197 213 MTV Jams
603000000 198 214 MTV Hits
603000000 201 218 VH1 Classics
603000000 202 219 VH1 Soul
603000000 203 187 Logo
603000000 207 222 CMT Pure Countr
603000000 225 253 Nick Too
603000000 226 254 Nick Toons
603000000 227 255 Teen Nick
603000000 324 273 MTV MUSICA Y MA
603000000 512 339 Barker 4 - Merc
603000000 514 500 Barker 6 - Quan
603000000 527 1508 WAPA TV

```

---

### Post by ylafont on 2014-04-21
Thank you erind!  Looks amazing. 

Now I have to go and read awk, after playing with sed for week. I thought i was getting close!

---

### Post by ylafont on 2014-04-21
SteelDriver, Thank you.  and thank you for the explanation. Will be butting it to use. Definitely  learning more on sed this way.  Thank you.

---

