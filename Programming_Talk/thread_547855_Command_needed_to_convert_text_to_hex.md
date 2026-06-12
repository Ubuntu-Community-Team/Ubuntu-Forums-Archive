---
title: "Command needed to convert text to hex"
date: 2007-09-10
forum: Programming Talk
---

### Post by Metacarpal on 2007-09-10
Hello,

Does anyone know a standard unix/linux command to convert a text string to hexidecimal?

I've tried hexdump, but I need a single, unified hex string rather than the broken-up format hexdump gives.

If there is a command to do this without my having to parse hexdump output, that would be great.  (I'd also be happy with perl code, though I'm less adept at perl than unix shell.)

Thank you in advance!

---

### Post by [h2o] on 2007-09-10
The problem is that string->hexadecimal can be done in a great number of ways depending on encoding.

I don't know of any standard command, but it should be pretty easy to code in whatever language you prefer. Loop through all characters and then translate to integer which you then display as hexadecimal.

---

### Post by xlinuks on 2007-09-10
If I understand you correctly you could use ghex2 and then save the hex as html, just be sure to save into a separate folder.

---

### Post by Wybiral on 2007-09-10
You could always hack up a small python program for it...

```

in_string = raw_input("Text: ")
out_string = ""
for c in in_string:
    out_string += hex(ord(c)).split("x")[1] + " "
print(out_string)

```

---

### Post by bashologist on 2007-09-10
This might work, but it definitely looks neat!
```
hexdump<<<"testing hex conversion" | sed "s/ *//g;s/^.\{7\}//;s/\(..\)\(..\)/\2\1/g" | tr -d "\n"; echo
```
[http://www.nickciske.com/tools/hex.php](http://www.nickciske.com/tools/hex.php)

---

### Post by nanotube on 2007-09-10
here's another solution in python (sample session shown below)

```
>>> import binascii
>>> binascii.hexlify('blabla')
'626c61626c61'

```
if you need to read from a file or from stdin, obviously you'd add that... :)

---

### Post by bogolisk on 2007-09-11
> **Metacarpal said:**
> Hello,

Does anyone know a standard unix/linux command to convert a text string to hexidecimal?

I've tried hexdump, but I need a single, unified hex string rather than the broken-up format hexdump gives.

If there is a command to do this without my having to parse hexdump output, that would be great.  (I'd also be happy with perl code, though I'm less adept at perl than unix shell.)

Thank you in advance!

Not really a single line but will do until 256 octets (that is 512 hex characters per line)
```

cat file |  xxd  -c 256 -ps

```
The *-ps* option is for *plain style*. I believe that's what you're after.

---

### Post by Metacarpal on 2007-09-13
> **bogolisk said:**
> Not really a single line but will do until 256 octets (that is 512 hex characters per line)
```

cat file |  xxd  -c 256 -ps

```
The *-ps* option is for *plain style*. I believe that's what you're after.

That's prefect - Thanks!!!

---

