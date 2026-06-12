---
title: "Unlocking the mysteries of UTF-8"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by George Heine on 2012-05-07
This question arose because of a recent need to put some Hangeul (Korean) characters in a document.
I have a file constisting of the  following text string:  ampersand, pound sign, "51060" , semicolon.   
Sending this file to my browser  (Firefox v. 12.0 for Ubuntu, with character encoding set to UTF-8), produces
the Hangeul representation of the syllable "i" (the number 2 in Korean).

When I use cut-and-paste to copy the browser display to a text file, the Hangeul script is still visible (for example, using "cat"), but the contents of the file look like

```
$ od -x i.txt
0000000 9dec 0ab4
0000004
```Try as I may, I can't figure out how the sixteen-bit number 51060 (0xC774) in the HTML file translates to the thirty-two bits in the text file.   Guessing that the "0a" byte is an end-of-file marker, but beyond that, am lost. 

OS is Ubuntu 10.04 LTS.  The  /etc/defaults/ file looks like
```
LANG="en_US.UTF-8"
```Thanks for any clues.

---

### Post by Vaphell on 2012-05-07
[https://en.wikipedia.org/wiki/UTF-8#Description](https://en.wikipedia.org/wiki/UTF-8#Description)
to avoid collision between chars of different byte length there are additional bit sequences added which indicate the length of the char (otherwise you wouldn't be able to differentiate between [51060]/[c774] and [199][116]/[c7][74]).

51060 is in 3-byte range, padded with 8 bits total.

```
$ echo "obase=2; 51060" | bc
1100011101110100
```
according to utf8 spec this gets padded with
**1110**1100**10**011101**10**110100

```
$ echo "ibase=2; 111011001001110110110100" | bc
15506868
$ echo "obase=16; 15506868" | bc
EC9DB4
```

0000000 **[9d][ec]** [0a]**[b4]**
printed in different order, 0a = newline (if you run od with -c it will be clearly visible)

```
$ od -c hangul.txt
0000000 354 235 264  **\n**
0000004
```

354 is octal for 236/EC, 235=157/9D, 264=180/B4

---

### Post by George Heine on 2012-05-07
Thank you, Vaphell, for a clear explanation.
Thanks also for the Wikipedia link.  
(Don't know why my own web search didn't find it.)
  
Have marked this thread solved.

---

