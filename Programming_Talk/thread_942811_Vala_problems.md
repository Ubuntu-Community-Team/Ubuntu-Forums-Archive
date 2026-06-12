---
title: "Vala problems"
date: 2008-10-09
forum: Programming Talk
---

### Post by Emill on 2008-10-09
Hello. I have some problems with Vala. I want to read a file and store it in a string that is not utf-8 encoded, because it is some binary data and the substring-function thinks it is an utf-8-encoded string...
[http://live.gnome.org/Vala/Tutorial#head-f2b5a7a55957645fb83905eea9660f9293bd1a70](http://live.gnome.org/Vala/Tutorial#head-f2b5a7a55957645fb83905eea9660f9293bd1a70)
It's that code I use:
```

string filename = "file";
string content;
ulong len;
FileUtils.get_contents (filename, out content, out len);

```
Is there any way to tell it it's not an utf-8-string? I also have some problems that if it contains a null-character, it cuts the string at that point if I do this:
```

string content2 = content;

```
content2 will be the shorter string.

---

### Post by Quikee on 2008-10-10
> **Emill said:**
> Hello. I have some problems with Vala. I want to read a file and store it in a string that is not utf-8 encoded, because it is some binary data and the substring-function thinks it is an utf-8-encoded string...
[http://live.gnome.org/Vala/Tutorial#head-f2b5a7a55957645fb83905eea9660f9293bd1a70](http://live.gnome.org/Vala/Tutorial#head-f2b5a7a55957645fb83905eea9660f9293bd1a70)
It's that code I use:
```

string filename = "file";
string content;
ulong len;
FileUtils.get_contents (filename, out content, out len);

```
Is there any way to tell it it's not an utf-8-string? I also have some problems that if it contains a null-character, it cuts the string at that point if I do this:
```

string content2 = content;

```
content2 will be the shorter string.

Strings in Vala are always utf-8 as far as I know. Try to use gio (FileInputStream for example) that can read it as a void* or play with IConv and convert() if you will be able to convert to another character set (ascii). 

I will try to play with this problem later as it seems interesting (I have not yet done something like this in Vala).

---

