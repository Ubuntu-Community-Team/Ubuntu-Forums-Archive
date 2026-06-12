---
title: "[SOLVED] Sed and unrecognised characters"
date: 2008-01-10
forum: Programming Talk
---

### Post by flightless bird on 2008-01-10
I'm a bit stuck with sed at the moment. I'm trying to get it to edit the output of a modified version of the perl cddbget script ([http://pastebin.com/f11aa9a72]("http://pastebin.com/f11aa9a72")) as it tends to come out with extended characters for accented letters (eg: [http://pastebin.com/f56c5850a]("http://pastebin.com/f56c5850a")). I've given myself a crash course on sed but I can't seem to get it to work well with this output.

As expected, the artist field is replaced by the following very happily: ```
sed 's/\(ist="\).*\(":al\)/\1'"$artist"'\2/g'
```, so I would have expected the following to work for the album field too:
```
sed 's/\(bum="\).*\(":na\)/\1'"$album"'\2/g'
```, and yet it doesn't seem to come up with any matches. I can happily come up with searches to pick any other bit of the line as long as it doesn't contain the extended character.

Where it gets wierd is when I copied the offending word into a new line of text to experiment ([http://pastebin.com/f4f07a4ee]("http://pastebin.com/f4f07a4ee")) I found to my confusion that ```
sed 's/Sy.*es/WORD/g'
``` worked fine on the new line (line2) but it didn't pick up the original. Infact I could very easily perfom any selection/substitution I wanted in line2, but not line1, using .* .I then thought it might have something to do with the quotes or colons in line1, but as I mentioned, it does not seem to be a problem with any other string. 

Any ideas?

---

### Post by flightless bird on 2008-01-10
Just checked what happens if I set the terminal character encoding to WESTERN (iso-8859-1, and iso-8859-15) and the character displays correctly (as ô) which is all well and good, but I still can't get sed to find it even when it displays correctly.

---

### Post by stroyan on 2008-01-10
I don't see the problem here using the unicode utf8 sequence efbfbd for the ô character.  Sed matches it with ".*".  Exactly what byte sequence to you see for the bad character using "od -x" or "xxd" to format it in hex?

---

### Post by flightless bird on 2008-01-10
The problem word (iso-8859=Symptômes) in hex gives: ```
0000000 7953 706d f474 656d 0a73
0000012

```, while the character ô isolated gives:```
0000000 0af4
0000002

```. Thanks for the help.

---

### Post by stroyan on 2008-01-10
I think I have it.  That 0xF4 'sequence' is valid for encoding the ô character in the ISO-8859-1 charmap and other ISO-8859-* charmaps.  But it is an invalid input sequence in the UTF8 charmaps.  You are probably using a UTF8 locale.  (You can check your current locale by running "locale".)  I tested and confirmed that sed will not match ".*" to an invalid sequence.  (I don't know if that should be considered a defect or design decision.)  I can get your test case to fail to match by using "LANG=en_US.utf8" and get it to succeed with "LANG=C".  You could translate a file or string from ISO_8859-1 to UTF8 with the iconv command-```
 iconv -f ISO_8859-1 -t UTF8 | sed 's/\(bum="\).*\(":na\)/\1'"$album"'\2/g'
```

---

### Post by flightless bird on 2008-01-11
Thank you so much - that is simple and ingenious. Very useful. Have a good one :)

---

