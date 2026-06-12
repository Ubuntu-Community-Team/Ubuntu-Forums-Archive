---
title: "How do I use grep to match end of words, rather than after words or end of lines?"
date: 2017-03-29
forum: Programming Talk
---

### Post by s3a on 2017-03-29
Hello, everyone. :)

I believe I can use $ for end of lines and \> for after words, but I want to see if there is at least one word on any given line where that/those word(s) end(s) in *nix*.

_I tried doing the following.:_
```
grep -E "nix/>"
```

and

```
grep -E "/>nix"
```

, but neither of those worked.

Could someone please help me figure out what it is that I need to type so that the grep tool works as I intend it to?

---

### Post by sudodus on 2017-03-29
Try the following command lines and use the color code to see what the commands are finding

```

echo "testline unix linux"|grep --color 'x '
echo "testline unix linux"|grep --color 'x$'
echo "testline unix linux"|grep --color -e 'nix ' -e 'nux$'
echo "testline unix linux"|grep --color -e 'x ' -e 'x$'
echo "testline unix linux trix truxa"|grep --color -e 'x ' -e 'x$'

```

---

### Post by spjackson on 2017-03-29
> **s3a said:**
> Hello, everyone. :)

I believe I can use $ for end of lines and \> for after words, but I want to see if there is at least one word on any given line where that/those word(s) end(s) in *nix*.

_I tried doing the following.:_
```
grep -E "nix/>"
```

/> is not \<

---

### Post by vasa1 on 2017-03-29
It could be useful to provide a small text file illustrating what you want.

For example, here's something, with *nux*, not *nix*, which I've saved as nix.txt:

> I use Linux on my laptop.
My laptop runs on Linux.
Does your laptop run on Linux?
Linux, Unix, and Asterix are all words but what is Linux?
Linux; Linux! Linux? Linux= Linux-lite/ArchLinux

When I run
```
grep -E --color "nux(\s|\-|\?|\;|\.|\,|\!|\=)" nix.txt
```What I see with that code is in the first image but [spjackson pointed out in post#3]("https://ubuntuforums.org/showthread.php?t=2357010&p=13626655#post13626655") that ```
grep -E --color 'nux\>' nix.txt
``` is what you need. See "second-image.png".

---

