---
title: "grep unicode"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-03-27
In the Lubuntu terminal which I access via ctrl-alt-t, I don't seem to be able to use grep with unicode characters such as chinese.

```
grep "&#19993;" ~/Documents/d/*.htm
```

gives me nothing, yet I know there should be heaps of hits.

The directory contains dual language dictionary htm files. If I grep in English, the chinese comes up in the terminal as &#65533;&#65533;&#65533;&#821;&#65533;&#65533;&#65533;&#65533;&#65533;&#1452;

Any ideas?

---

### Post by d2btoo on 2012-03-27
Hi,

Although I'm not 100% certain but did you checked the file type.... utf-8 files are search-able by grep while utf-16 is not, me guess...

There is a old thread about this here : [http://www.unix.com/unix-dummies-questions-answers/34129-grep-unicode-utf-16-file.html](http://www.unix.com/unix-dummies-questions-answers/34129-grep-unicode-utf-16-file.html)

see if that's helps you.... good luck  :)

Please let me know if my hunch was correct....thanks!

---

### Post by Kevin McCready on 2012-03-27
I've searched these forums for unicode's behaviour in the terminal/console. There is nothing approaching a FAQ.

BUT many posts with the same problem have no replies. This shows me it is an area that Canonical may want to give some attention to.

The basic issue is getting the terminal to work properly with unicode.

I'm using LXTerminal and the console in Lubuntu and the problem is the same in each: unicode characters don't display. You get little squares in the console and ????? in the terminal. When you try to search for a unicode character both the terminal and the console simply come up with a negative result.

---

### Post by Kevin McCready on 2012-03-27
Thanks, I think you may be on the right track. Because I was successful on another file I know is unicode. But when I checked the "file type" of the problem files with

```
file
```

It told me it was "HTML Document Text"

When I tried to convert the file with
```
iconv -f UTF-16 -t UTF-8 
```
I got
iconv: illegal input sequence at position 1644

---

### Post by d2btoo on 2012-03-27
> **Kevin McCready said:**
> 
It told me it was "HTML Document Text"


hmm! if you open that html file in your text-editor ( I believe gedit is default), what does it shows for the encoder utf-8 or utf-16? 

(In gedit after opening the file, rest your mouse over the tab and it will show name, mime-type & encoding in the tool-tips)

---

### Post by Kevin McCready on 2012-03-27
leafpad is default for lubuntu I think. Anyway it gave

<html><head>
<meta http-equiv="Content-Type" content="text/html; charset=gb2312">
then a whole lot of gobbledigook

---

### Post by Vaphell on 2012-03-27
is there the encoding mentioned in html source?

edit: it is :-)

try this

```
iconv -f GB2312 -t UTF-8
```

---

### Post by Kevin McCready on 2012-03-27
the encoding is gb2312 I think. The a search of the source doesn't find the terms utf or encoding or coding

---

### Post by d2btoo on 2012-03-27
gb2312 is not utf-16 so no wonder, that the above command gave you trouble.... 

I don't know if iconv could properly handle gb2312 but when I did 
```

iconv -l

```
it does list gb2312, so it may work.... ;)

please see:
[http://spin.atomicobject.com/2011/07/13/some-useful-iconv-functionality/](http://spin.atomicobject.com/2011/07/13/some-useful-iconv-functionality/)

and also the man page

thanks!

---

### Post by Kevin McCready on 2012-03-27
Thanks heaps. My version of iconv didn't list gb  but when I did

```
iconv -f GB2312 -t UTF-8 <filename>
```

It worked. Now I just have to figure out how to convert a whole directory full of files.

---

### Post by d2btoo on 2012-03-27
>>convert a whole directory full of files.

Ah! hints : for loops... bash script perhaps ;)

---

### Post by Kevin McCready on 2012-03-27
I've heard the term but don't know how to make a bash script.

---

### Post by Kevin McCready on 2012-03-27
This post is just recording what I've learned so that others following might find it useful.

The terminal may not work properly with non-unicode files such as Windows-1250, GB2312, Shift-JIS, EBCDIC. 

To find the "file type" of your file:
```
file <filename>
```

But that may not tell you correctly because there may be other encoding inside the file. Another way to do it is open the file in a simple text editor (eg leafpad, nano, gedit) and search for the charset (character set) which will tell you the encoding.

A solution may be to convert the encoding of your files with iconv.
For example,

```
iconv -f GB2312 -t UTF-8
```
but I cannot make this conversion permanent with an html file.

Another solution may be to open the file in leafpad and in the open file dialogue box select the type of encoding before you open it. Then manually alter the charset information.

Hope this helps.

---

### Post by Vaphell on 2012-03-28
script will be trivial once you find out how to recognize files to convert
are these only html files with explicitly defined encoding?

lets say you are interested only in files with gb2312 occuring inside

```
while read f; do echo iconv -f GB2312 -t UTF-8 "$f"; done < <( grep -lir gb2312 . )
```
with echo it will print out commands that would execute without

---

### Post by Ms. Daisy on 2012-03-29
edit: now that the threads were merged my comment made no sense.  Second time that happened today...
[]("http://manpages.ubuntu.com/manpages/lucid/man1/uterm.1.html")

---

### Post by lisati on 2012-03-29
Threads merged.

For the staff: [http://ubuntuforums.org/showthread.php?t=1948126](http://ubuntuforums.org/showthread.php?t=1948126)

---

### Post by Kevin McCready on 2012-04-02
> **Vaphell said:**
> script will be trivial once you find out how to recognize files to convert
are these only html files with explicitly defined encoding?

lets say you are interested only in files with gb2312 occuring inside

```
while read f; do echo iconv -f GB2312 -t UTF-8 "$f"; done < <( grep -lir gb2312 . )
```
with echo it will print out commands that would execute without
I did it and it took ages. Then I realised it was doing my whole computer. How can I limit it to just the directory where the offending files reside?

This is what I got:

grep: warning: ./.wine/dosdevices/z:/lib/recovery-mode/recovery-mode: recursive directory loop
iconv -f GB2312 -t UTF-8 ./.cache/chromium/Default/Cache/data_2
iconv -f GB2312 -t UTF-8 ./.cache/chromium/Default/Cache/f_000b39
iconv -f GB2312 -t UTF-8 ./.cache/chromium/Default/Cache/f_0000a5
iconv -f GB2312 -t UTF-8 ./.cache/chromium/Default/Cache/f_00045d
iconv -f GB2312 -t UTF-8 ./.cache/chromium/Default/Cache/f_000b37
iconv -f GB2312 -t UTF-8 ./.cache/chromium/Default/Cache/data_3
iconv -f GB2312 -t UTF-8 ./.cache/chromium/Default/Cache/data_1
iconv -f GB2312 -t UTF-8 ./.bash_history
grep: ./.wine/dosdevices/z:/lib/modules/3.0.0-12-generic/build/include/asm: No such file or directory
iconv -f GB2312 -t UTF-8 ./.wine/dosdevices/z:/lib/modules/3.0.0-12-generic/modules.alias
grep: ./.wine/dosdevices/z:/lib/modules/3.0.0-12-generic/build/source: No such file or directory
grep: ./.wine/dosdevices/z:/lib/modules/3.0.0-17-generic/build/include/asm: No such file or directory
iconv -f GB2312 -t UTF-8 ./.wine/dosdevices/z:/lib/modules/3.0.0-12-generic/build/fs/nls/Kconfig
iconv -f GB2312 -t UTF-8 ./.wine/dosdevices/z:/lib/modules/3.0.0-12-generic/kernel/fs/nls/nls_cp936.ko
iconv -f GB2312 -t UTF-8 ./.wine/dosdevices/z:/lib/modules/3.0.0-17-generic/modules.alias
grep: ./.wine/dosdevices/z:/lib/modules/3.0.0-17-generic/build/source: No such file or directory

AND I tried to wipe out wine a few days ago. Seems that might not have worked.

---

### Post by Vaphell on 2012-04-02
. in <( grep -lir gb2312 . ) defines the directory (. = current dir)
i assume you ran it from your home so it went through everything you own
You need to either 'cd ~/Documents' before running it or replace . with ~/Documents

uninstalling doesn't necessarily mean that the configuration dir in your home gets wiped out. You can do it by hand (ctrl+h) to unhide dotfiles and remove .wine

---

