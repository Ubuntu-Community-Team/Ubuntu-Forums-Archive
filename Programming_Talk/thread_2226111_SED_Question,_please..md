---
title: "SED Question, please."
date: 2014-05-25
forum: Programming Talk
---

### Post by ylafont on 2014-05-25
I have the following  sed  line



```
sed -nr \
      -e '/^SCANNING:/{s///; s/\(us-irc:|\(us-hrc:|\(us-cable:/\t/; s/,/\t/; s/us-cable://; s/\)/\t/;h}' \
      -e '/^PROGRAM/{s///; /: 0$/d; s/:/\t/; s/\//-/; s/MC://; s/ \(encrypted\)//; G;s/(.*)\n(.*)/\2\1/p}' "$HDHomeID".log | sort -k5n > "$HDDATA"

```

Sed is supposed to parse out the following log file:

```
[COLOR=#000000][FONT=Lucida Grande]SCANNING: 681000000 (us-irc:105, us-cable:105)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]LOCK: qam256 (ss=100 snq=100 seq=100)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]TSID: 0x021B[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 340: 340 STARZ (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 341: 341 STZCI (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 342: 342 STZK (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 343: 343 STZE (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 344: 344 STZB (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 345: 345 STZw (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 346: 346 STZCO (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 350: 350 ENC (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 351: 351 ENCA (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 352: 352 ENCS (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 353: 353 ENCWS (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 354: 354 ENCC (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 355: 355 ENCB (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 356: 356 ENCF (encrypted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PROGRAM 357: 357 ENCw (encrypted)[/FONT][/COLOR]
```

and produce a line for each channel entry like this. 

```
 681000000 	105	 105	 340	 340 STARZ
 681000000 	105	 105	 341	 341 STZCI
 681000000 	105	 105	 342	 342 STZK
 681000000 	105	 105	 343	 343 STZE
 681000000 	105	 105	 344	 344 STZB
 681000000 	105	 105	 345	 345 STZw
 681000000 	105	 105	 346	 346 STZCO
 681000000 	105	 105	 350	 350 ENC
 681000000 	105	 105	 351	 351 ENCA
 681000000 	105	 105	 352	 352 ENCS
 681000000 	105	 105	 353	 353 ENCWS
 681000000 	105	 105	 354	 354 ENCC
 681000000 	105	 105	 355	 355 ENCB
 681000000 	105	 105	 356	 356 ENCF
 681000000 	105	 105	 357	 357 ENCw

```

But, instead i get 

```
681000000 	105	 105	
 340	 340 STARZ
 681000000 	105	 105	
 341	 341 STZCI
 681000000 	105	 105	
 342	 342 STZK
 681000000 	105	 105	
 343	 343 STZE
 681000000 	105	 105	
 344	 344 STZB
 681000000 	105	 105	
 345	 345 STZw
 681000000 	105	 105	
 346	 346 STZCO
 681000000 	105	 105	
 350	 350 ENC
 681000000 	105	 105	
 351	 351 ENCA
 681000000 	105	 105	
 352	 352 ENCS
 681000000 	105	 105	
 353	 353 ENCWS
 681000000 	105	 105	
 354	 354 ENCC
 681000000 	105	 105	
 355	 355 ENCB
 681000000 	105	 105	
 356	 356 ENCF
 681000000 	105	 105	
 357	 357 ENCw

```

Can anyone explain the extra line feed?

---

### Post by Slim Odds on 2014-05-25
sed is a line oriented program. You need something like awk. Personally, I'd write a quick ruby program.

---

### Post by steeldriver on 2014-05-25
Although your sed expression does actually work for me (using your sample input) I agree with Slim Odds - it's an ugly (and more importantly, fragile) way to handle structured data. Something like

```

awk -v OFS='\t' '/^SCANNING/ {fr=$2; split($3,rc,":|,"); split($4,ca,":|)")}; /^PROGRAM/ {split($2,a,":"); print fr,rc[2],ca[2],a[1],$3,$4}' *yourfile*

```

should be more robust.

---

### Post by ylafont on 2014-05-25
So many methods of the doing these things, i wish i had time to learn them all.   

to use the awk method i would have to re-write the entire script, something to consider though while learning awk.

---

### Post by steeldriver on 2014-05-25
I was actually impressed by your use of h and G . It's the very specific text replacements that are likely to make it flaky. It looks like the final 

```

G;s/(.*)\n(.*)/\2\1/p

```

is failing to eliminate the newline after you stitch the lines together with G. But as I said, it appears to work for me (GNU sed version 4.2.1 on Ubuntu 12.04), so I don't really know how to help you debug it beyond that.

---

### Post by ylafont on 2014-05-25
Hum, You stating that it worked for you, gave me an idea to cut and paste the file info into a new unix file. Apparently it did not like the file encoding. 

Now i got the results, i was expecting!

---

