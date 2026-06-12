---
title: "'-n 3' vs '-n3' - is the space necessary?"
date: 2013-10-23
forum: Programming Talk
---

### Post by sha1sum on 2013-10-23
I have accidentally discovered that
```
tail -n3 story.txt
```
works just as well as
```
tail -n 3 story.txt
```

I used the command "tail" as an example, but I've tried it with a few other commands also, and there it worked fine also. 

So my question is: Is the space necessary? Or maybe formulated a bit more precisely: Are there commands that will not accept the version without the space?

---

### Post by Bachstelze on 2013-10-23
It obviously depends on how the program processes its parameters. If it uses [getopt()]("http://pubs.opengroup.org/onlinepubs/009695399/functions/getopt.html"), then the space is optional. Most programs you will encounter use it, but of course some may not...

P.S.: Note also that, in principle, you should always put a space. Omitting it is only permitted so as to not break old applications.

---

### Post by CharlesA on 2013-10-23
> **Bachstelze said:**
> 
P.S.: Note also that, in principle, you should always put a space. Omitting it is only permitted so as to not break old applications.

This. I've always included spaces in options. It's a good thing to get in the habit of.

---

### Post by Vaphell on 2013-10-24
i don't think ffmpeg would work with compressed parameters.
[http://linux.die.net/man/1/ffmpeg](http://linux.die.net/man/1/ffmpeg)
too many of them would be ambiguous if space was optional. It can only work when you have unique 1 char switches that can be optionally glued together and the value tacked at the end is assumed to be assigned to the last one, but ffmpeg uses shortparam convention of single - for words and that would mean many collisions (eg -s -ss -scodec)

---

### Post by sha1sum on 2013-10-24
Thanks guys, I understand. So in short, always use the space

---

### Post by trent.josephsen on 2013-10-24
There are a few cases where an option takes an argument, but it won't work if you use a space. I think sed's -i and Perl's -F (but not awk's) fall into this category.

When in doubt, read the manual.

---

### Post by Bachstelze on 2013-10-24
> **trent.josephsen said:**
> There are a few cases where an option takes an argument, but it won't work if you use a space. I think sed's -i and Perl's -F (but not awk's) fall into this category.

When in doubt, read the manual.

Yes, when the arguent is optional (as in *sed -i*), then the space is mandatory, otherwise the program can't distinguish between an option and its argument or several options put together (*sed -ibak* means *sed -i -b -a -k*, not *sed -i bak*).

(Also sed -i is non-standard. For standard-compliant programs, optional arguments are discouraged.)

---

### Post by Vaphell on 2013-10-24
> (sed -ibak means sed -i -b -a -k, not sed -i bak).

no, it's in fact -i bak. When switches are glued together -i has to be last because everything that goes after will be used as a filename suffix

```
$ touch sed-i.txt
$ ls sed-*
sed-i.txt
$ sed -i[COLOR="#0000FF"]nrbak[/COLOR] 's/$//' sed-i.txt
$ ls sed-*
sed-i.txt  sed-i.txt[COLOR="#0000FF"]nrbak[/COLOR]
$ sed -rni[COLOR="#0000FF"]bak[/COLOR] 's/$//' sed-i.txt
$ ls sed-*
sed-i.txt  sed-i.txt[COLOR="#0000FF"]bak[/COLOR]  sed-i.txtnrbak
```

---

### Post by Bachstelze on 2013-10-24
Oh, okay, as you can see I hadn't tested it...

(And sed -i is non-standard, rawr.)

---

