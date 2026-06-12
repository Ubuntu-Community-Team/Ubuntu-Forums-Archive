---
title: "sorting a word file based on word length"
date: 2012-11-08
forum: Programming Talk
---

### Post by Mia_tech on 2012-11-08
guys, I have a text file with words, and I want to put them into an array and sort them based on string length/size of every word. I wonder if there's a command that would allow me to do this, so I don't have to write an algorithm that does this. I was looking into "sort" command, but I don't think that sort has an option for this.

I was thinking something like
```
array=($(cat $file))
sort_array=$(for i in ${arra[@]}; do echo $i; done | sort)
```

---

### Post by schauerlich on 2012-11-08
There are almost certainly better ways of doing this, but:

```
$ cat ~/foo.txt
abcdef
abcdefghijklmnopqrstuvwx
abcde
abcdefghijklmn
abcdefghijklmnopqrs
abcdefghijklm
abcd
abcdefgh
abcdefghijklmnopqrstuvwxyz
abcdefghijkl
a
abcdefghijklmno
abcdefghijklmnopqrstuv
abcdefghijklmnopqrstuvwxy
abcdefghijklmnopqr
abcdefghijklmnopq
abcdefghijklmnop
abc
abcdefghijklmnopqrstu
abcdefghi
abcdefghijklmnopqrstuvw
abcdefg
ab
abcdefghij
abcdefghijklmnopqrst
abcdefghijk
$ cat ~/foo.txt | awk '{ printf("%s %s\n", $1, length($1)) }' | sort -nk2 | awk '{ print($1) }'
a
ab
abc
abcd
abcde
abcdef
abcdefg
abcdefgh
abcdefghi
abcdefghij
abcdefghijk
abcdefghijkl
abcdefghijklm
abcdefghijklmn
abcdefghijklmno
abcdefghijklmnop
abcdefghijklmnopq
abcdefghijklmnopqr
abcdefghijklmnopqrs
abcdefghijklmnopqrst
abcdefghijklmnopqrstu
abcdefghijklmnopqrstuv
abcdefghijklmnopqrstuvw
abcdefghijklmnopqrstuvwx
abcdefghijklmnopqrstuvwxy
abcdefghijklmnopqrstuvwxyz

```

---

