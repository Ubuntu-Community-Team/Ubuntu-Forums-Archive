---
title: "Non-English Alphabetics in File-Names Display &#65533;"
date: 2012-07-29
forum: New to Ubuntu
---

### Post by rich1842 on 2012-07-29
This particularly happens for me in music files, where the names could be French, German or Spanish etc etc so not just one language. 

I have been searching and have read:

[http://cdburnerxp.se/help/appendices/filesystem](http://cdburnerxp.se/help/appendices/filesystem)

and

[http://www.joelonsoftware.com/articles/Unicode.html](http://www.joelonsoftware.com/articles/Unicode.html)

so I know it is because I need more or a different character set but which one and how do I get it into kubuntu?

Windows seems to handle this ok but it's a pain to have to export there to fix something and import back. 

Another thing is sometimes I cant do this: kubuntu tells me the file doesn't exist! And I have a pile of files I cannot move or delete because they don't exist...  

I have been searching but none of the threads here or elsewhere seems to match mine.

What's in a name?

---

### Post by Zorael on 2012-07-29
What filesystem is this on?

Also, can you paste the contents of **/etc/mtab**?

---

### Post by Paddy Landau on 2012-07-29
Please also tell us how you get the files onto your system. Ripped from CD? Downloaded from the 'net? Obtained via torrent? Imported from a Windows file system?

---

### Post by rich1842 on 2012-07-29
Thanks for responses.

Zorael:  My drives are ext4. 

I tried '[B]/etc/mtab' with sudo and got '/etc/mtab: command not found'

Paddy: Usually from Usenet[/B]**  or ****d/l by torrent**[B] .

[/B]

---

### Post by Zorael on 2012-07-31
> **rich1842 said:**
> Zorael:  My drives are ext4. 

I tried '/etc/mtab' with sudo and got '/etc/mtab: command not found'
Yes, it's just a normal text file and not an executable script. Had it been a FAT or NTFS drive, there would have been a mount option that would force UTF-8 charsets.

Open up a terminal and enter '**echo $LANG**' (no need for sudo). Copy/paste the output here. Does it say **UTF-8** after your language code, like **lang_LANG._UTF-8_**?

To illustrate the effect;
```
zorael@laughlyn /tmp/test $ echo **$LANG**
**[COLOR="RoyalBlue"]en_US._UTF-8_[/COLOR]**  *# my standard locale is Unicode en_US*

zorael@laughlyn /tmp/test $ mkdir '[COLOR="green"]**1:** &#35023;&#24237;&#12395;&#12399;&#20108;&#32701;&#24237;&#12395;&#12399;&#20108;&#32701;&#40335;&#12364;&#12356;&#12427;[/COLOR]'
zorael@laughlyn /tmp/test $ mkdir '[COLOR="green"]**2:** åäöÅÄÖ@&#322;€ªßð«»©“&#273;®þ&#331;”n&#295;&#8592;&#8595;&#312;[/COLOR]'

zorael@laughlyn /tmp/test $ **LANG=[COLOR="Sienna"]en_US[/COLOR]**  *# dumbing down locale to non-Unicode*
zorael@laughlyn /tmp/test $ ls -1
**[COLOR="Red"][B]1:** ?????????????????????????????????????????????
**2:** ????????????@???????????????????????????????n??????????[/COLOR][/B]

zorael@laughlyn /tmp/test $ **LANG=[COLOR="RoyalBlue"]en_US._UTF-8_[/COLOR]**  *# restoring*
zorael@laughlyn /tmp/test $ ls -1
[COLOR="Green"]**1:** &#35023;&#24237;&#12395;&#12399;&#20108;&#32701;&#24237;&#12395;&#12399;&#20108;&#32701;&#40335;&#12364;&#12356;&#12427;
**2:** åäöÅÄÖ@&#322;€ªßð«»©“&#273;®þ&#331;”n&#295;&#8592;&#8595;&#312;
[/COLOR]
```

---

### Post by rich1842 on 2012-07-31
This really does work! Lets you delete these files.

'gksudo nautilus /home/carl/Desktop/' --- example --- takes you to where your file/folder is.

[http://ubuntuforums.org/showthread.php?t=1123479](http://ubuntuforums.org/showthread.php?t=1123479)

That's where I got it.

                                                  ****************************************

Zorael (thanks for reply) :   en_GB.UTF-8

I am not sure if that was there before: I have been trying different things like

convmv -r --notest -f windows-1255 -t UTF-8 *

and

convmv -r --notest -f windows-1252 -t UTF-8 *

(1252 is Latin, 1255 is Hebrew)

and

sudo apt-get install unifont

I am hoping these will help avoid problems in future. And the files are gone. I was sure it was to do with character sets.

When I d/l the files I used pypar2 to verify/repair them and I think it is pypar2 that is the problem.

I d/l the same set on XP and it's fine - par files did their job etc. 

Just to see, I re-d/l on kubuntu pc and all the files are ok BUT when I   opened pypar2 to verify/repair I could see the 'bad' names in pypar2  (and stopped it).  So the par files and the data/music files are ok when  I get them but the latter are being corrupted by pypar2. 

I can pass the  files to XP to verify/repair but it's a pity pypar2 doesn't seem to  cope.

---

### Post by Vaphell on 2012-07-31
[http://ubuntuforums.org/showthread.php?t=1236012](http://ubuntuforums.org/showthread.php?t=1236012)

convmv should be able to convert windows specific encoding (usually win-125x with x depending on region) to utf8 used by ubuntu.

---

### Post by rich1842 on 2012-07-31
Thanks Vaphell - I have already used convmv to update. I actually think it told me I had not needed to (it brought up a list of files/folders with non-English alphabetics and told me something like 'these are already ok'). As you will see in my previous reply I think now it is pypar2 that is the culprit.

---

