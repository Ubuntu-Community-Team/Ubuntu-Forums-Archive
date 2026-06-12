---
title: "What is Ascii, Fonts, Unicode, Character encoding ?"
date: 2007-02-08
forum: Programming Talk
---

### Post by akudewan on 2007-02-08
Being a newbie to programming, I was introduced to ASCII. Being a Linux user, I see the words Unicode and Character Encoding very often. But I've never managed to understand these concepts properly.

I know that every-thing on my keyboard needs to have a binary counterpart, since letters and words cannot be interpreted by a computer. Only binary numbers can...So the letter 'A' has the number 65 associated with it. When I press 'A' on my keyboard, the computer reads it as 1000001

ASCII supports only a few characters, but Unicode was designed to support many international characters, and its backward compatible with ASCII (or so I've heard).

So is the stuff that I'm typing from my keyboard Unicode or ASCII ? 

And what the heck is Character Encoding, where does it come into the picture?

A word processing software allows me to change the font of my text, this seems to be a "software" concept, not directly related to ASCII and Unicode...is this correct?

Now, there are also some places where I can't change the font. Like the console, for instance. So is there a font hidden somewhere, that I can't see? Does there HAVE to be a font? Does every operating system have a set of fonts that it uses everytime it wants to display something on my monitor ?


Thanks for reading...and thanks in advance for answering :)

---

### Post by meng on 2007-02-08
ASCII and Unicode are types of character encoding
[http://en.wikipedia.org/wiki/Character_encoding](http://en.wikipedia.org/wiki/Character_encoding)

---

### Post by Unterseeboot_234 on 2007-02-08
ASCII was just an agreement between the major manufactures to reserved hex numbers that mapped to a Latin-flavor of alphabet. 125 characters soon proved to be inadequate and extended ASCII followed. Cap "A" is 65 in hex and \u0065 in octal (the extended Latin-1).

Then, with MS leading the way, we have char charts for regions in the era of Win98. Open a MSOffice2000 doc from a WinXP box with a Win98 box and you have a lot of dropped characters, especially if the XP doc was German OS box and the Win98 was English OS. XP was a small improvement over extended ASCII. To be sure, XP is unicode, but it relied on the first 2 bits (usually invisible to the user) of every document to define a region alphabet subset. 

You can see in html encoding the char-set command. XML is still stuck on regional charsets. <HTML>, likewise is using EN or UTF-8 in the first line.

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

The current idea from w3.org compliant character encoding is a range of numbers that totals 65,500 to represent all the possible glyphs needed in computerland. You can download a wallchart

**[Unicode Wall Chart]("http://ian-albert.com/misc/unichart.php")**

So, I mention all this from practical experience. I brought American Windows over to Europe and discovered the two different language-based OS will corrupt Word Documents back and forth. This is more or less transparent on the internet.

My compliments to Ubuntu team for incorporating a world-wide view of computer documents. For the first time in my life I was able to view Japanese web pages because *butu includes a lot of foreign language fonts. I am able to install several language variations of Ubuntu from the single Live-CD. With MS, you have to purchase each language.

Which brings me to my final idea. Ahead of us is this joint alliance between Adobe and Microsoft. MS plans to introduce OpenType fonts with internal numbering grid-schemes to represent 65,500 possible characters for EVERY font. Good idea. However, Adobe annouced they have dropped all support for Linux and has teamed up with MS to bring totally new file formats for XML, web page standards and word processing docs.

============
To answer some of your other questions. Java is unicode-based. Flash is unicode-based (because its IDE is a modified MS IE6 web browser licensed by MS). My Latin-1 fonts limit what I can display on the monitor. The keyboard lets me type in \u00b5 to get the Greek micron -- **µ** . That's the thing, when we press a keycap on the keyboard we are in reality running a short-lived program.

You only have to worry about unicode when you want to format or display data from your program. Usually, whatever OS you have running is doing a lot of background work for you when just operating a computer.

Separate the concepts in your mind between character and glyph and you realize why a font consults the character to display the glyph.

Didn't mean to ramble. But this is a vast subject and mostly overlooked and neglected for the reasons I stated above. A dude in Malaysia might only keep his computer forever in Malaysia and never come across the need to evaluate the need for OpenType or Unicode.

---

### Post by akudewan on 2007-02-08
This is quite an interesting subject...I'm beginning to understand things now.

The things you gotto do to type stuff on a computer!! And nobody even notices...:o

---

### Post by pelagic on 2007-04-09
Hi,

you should read yourself into the topic. Maybe start with wikipedia:
[http://en.wikipedia.org/wiki/Character_encoding](http://en.wikipedia.org/wiki/Character_encoding)

Cheers,
pelagic

---

### Post by pmasiar on 2007-04-09
Start here: [The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets (No Excuses!)](http://www.joelonsoftware.com/printerFriendly/articles/Unicode.html)

---

### Post by rplantz on 2007-04-09
Yes, this is an interesting topic. The OP's original question is one I've thought about asking several times myself. To be honest, I was a little embarrassed to ask. After all, I'm a retired CS professor and supposed to know all this stuff. :oops:

This:
> **pmasiar said:**
> Start here: [The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets (No Excuses!)](http://www.joelonsoftware.com/printerFriendly/articles/Unicode.html)
looks pretty good. However, the author says > You probably think I'm going to talk about very old character sets like EBCDIC here. Well, I won't. EBCDIC is not relevant to your life. We don't have to go that far back in time.
According to wikipedia, ASCII and EBCDIC both appeared in 1963. EBCDIC was specifically designed to make life easier for punched card readers. Having written some ASCII <-> EBCDIC converters myself (in IBM Series/1 assembly language), I can tell you that ASCII is much easier to work with in a program.

Unterseeboot_234 has a couple of mathematical glitches in his/her post:
> 
ASCII was just an agreement between the major manufactures to reserved hex numbers that mapped to a Latin-flavor of alphabet. 125 characters soon proved to be inadequate and extended ASCII followed. Cap "A" is 65 in hex and \u0065 in octal (the extended Latin-1).
First, character codes use bit patterns. These patterns can be expressed with any notation. We commonly use numbers. Hexadecimal is a convenient notation for bit patterns. But it would be just as accurate to express the patterns in, say, base 5.

Second, cap 'A' is 0x41 in hex, 0101 in octal, 65 in decimal, and 0100 0001 in binary. I have used C/C++ syntax to express the hex, octal, and decimal numbers. There is no syntax for binary directly. Since I brought it up, cap 'A' in base 5 is 230.

If you wish to see the ASCII code in octal, decimal, and hex, use the ```
man ascii
``` command.

ASCII is actually a 7-bit code. The high-order bit is the parity bit. When hardware became reliable enough to ignore parity, people began using it for other things. For example, the Apple II system used it as a busy/done flag for keyboard and screen I/O. And some systems of that era used it to add another 128 special characters, often graphics.

---

