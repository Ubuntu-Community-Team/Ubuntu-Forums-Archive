---
title: "UTF-8 in PERL source stops code running"
date: 2010-11-05
forum: Programming Talk
---

### Post by vince-vlara on 2010-11-05
OK, I must be an idiot. I have been trying to get a simple ¨Hello World¨ running on my 10.10 installation and PERL just throws the following error:-

[B]Unrecognized character \xC2 in column 7 at ./hello.pl line 2
[/B]
The character it is complaining about is the first double quote character that I typed before the H in Hello.

hexdump -C hello.pl shows what I actually have in my source file. Oh dear, where have the double quotes that I typed in nano gone? I thought I was hitting the double quote key, but the hex output shows 0xC2 0xA8 which is DIAERESIS in UTF-8.

00000000  23 21 2f 75 73 72 2f 62  69 6e 2f 70 65 72 6c 0a  |#!/usr/bin/perl.|
00000010  70 72 69 6e 74 20 c2 a8  48 65 6c 6c 6f 20 57 6f  |print ..Hello Wo|
00000020  72 6c 64 21 5c 6e c2 a8  3b 0a 23 20 45 6e 64 20  |rld!\n..;.# End |
00000030  6f 66 20 66 69 6c 65 0a                           |of file.|
00000038

My locale is:-

LANG=en_GB.utf8
LC_CTYPE="en_GB.utf8"
LC_NUMERIC="en_GB.utf8"
LC_TIME="en_GB.utf8"
LC_COLLATE="en_GB.utf8"
LC_MONETARY="en_GB.utf8"
LC_MESSAGES="en_GB.utf8"
LC_PAPER="en_GB.utf8"
LC_NAME="en_GB.utf8"
LC_ADDRESS="en_GB.utf8"
LC_TELEPHONE="en_GB.utf8"
LC_MEASUREMENT="en_GB.utf8"
LC_IDENTIFICATION="en_GB.utf8"
LC_ALL=

Can someone explain to me how I can write a simple Hello World in PERL on my British installation of Ubuntu 10.10 and get it to run?

Is there a special magic key combination that I need to press to get Double Quotes (0x22) in my code?

I also cannot run PERL one liners from the command line because of UTF-8 translating my keystrokes.

---

### Post by DanielWaterworth on 2010-11-05
I'm also using a british installation of ubuntu and it works fine for me.

First off, the problem isn't with perl. I'm fairly sure that it would work for you if you copied and pasted this quotation mark " . There's something in you installation that's mapping the quotation mark on your keyboard to the wrong unicode character. What keyboard map are you using?

---

### Post by shawnhcorey on 2010-11-05
Try add these to the top of your script:
```
use utf8;

binmode STDOUT, ':encoding(utf8)';
```

See:
perldoc utf8
perldoc -f binmode
perldoc perluniintro
perldoc perlunicode
perldoc perlunifaq
perldoc perlunitut

---

### Post by vince-vlara on 2010-11-05
I found a solution. I was typing using an American keyboard that has no British Pound sign. My keyboard definition was set to 'USA International (with dead keys)'. Using the Ubuntu desktop program for specifying keyboards, I replaced the 'dead keys' keyboard setting that was detected at install time with just plain 'USA' and the double quote key now enters a double quote character when pressed. I edited my Hello World code accordingly and it now runs.

In conclusion, if the key being pressed doesn't enter the character that you expected, then you are probably using the wrong keyboard driver.

---

### Post by DanielWaterworth on 2010-11-05
congratulations, remember to set the thread as solved.

---

