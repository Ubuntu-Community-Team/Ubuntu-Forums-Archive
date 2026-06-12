---
title: "Delete weird characters on name files"
date: 2017-06-24
forum: New to Ubuntu
---

### Post by sed_faster on 2017-06-24
Hello everyone,

I intend rename various file with weird characters, here is an example:
[http://imgur.com/a/0qBUV](http://imgur.com/a/0qBUV)

The number, 07, which you see on this string it is referent to the number of the file. On an directory I have, more or less, two thousand files pdf. Each one of them has the number referent of this order. I need delete all this weird characters on all files. How can I do this?
I think create a cycle for and run the instruction on inside this cycle for. But I can't know how create this instruction. I am thinking some relative "delete all characters which don't belong the traditional alphabet.

---

### Post by papibe on 2017-06-24
Hi Edgar.

I've done that before. The command iconv is very useful. Instead of removing the special character, you can translate them to the closest ASCII relative.

Say á to a, Ñ to n, and ü to u.

```
#!/bin/bash

text_to_ascii()
{
    echo "$(iconv -t "ASCII//TRANSLIT" <<< "$1")"
}


for filename in ./*
do
    clean_filename="$(text_to_ascii "$filename")"

    **[COLOR="#FF0000"]echo[/COLOR]** mv -iv "$filename" "$clean_filename"

done
```
Note that this script does not actually rename files, just print the command. It is safe to run it. When you feel confortable with what it does remove the word **[COLOR="#FF0000"]echo[/COLOR]**.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by sed_faster on 2017-06-24
Thanks,

I can't understand why this instruction:
> 
"ASCII//TRANSLIT" <<< "$1"


The result of this script it is, for example, "saber_eletr++nica_n+?_183.pdf"
The script replace weird characters to signal ++ and signal ?

---

### Post by papibe on 2017-06-24
I imagine that your system is using UTF-8 (the modern default).

If you see those graphical characters on the the name, it means that the names are not encoded in UTF8 or ASCII.

Is that Portuguese? If you can determine the encoding, you may be able to get a better translation.

For instance, typical Spanish/Portuguese encodings can be windows-1252, ISO-8859-1, ISO-8859-3, ISO-8859-9, or ISO-8859-15. Thus you could do something like:
```
iconv -f ISO_8859-9 -t "ASCII//TRANSLIT"
```
You could try this to guess the encoding:
```
ls -1 saber* | file -
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by papibe on 2017-06-24
Alternatively, you could just delete all weird character by using:
```
iconv -t "ASCII//IGNORE" 
```
Regards.

---

### Post by HermanAB on 2017-06-25
Wow, this is a nice tip.

---

