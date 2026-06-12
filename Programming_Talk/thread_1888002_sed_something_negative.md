---
title: "sed something negative"
date: 2011-11-28
forum: Programming Talk
---

### Post by maclenin on 2011-11-28
Quick question.

I have declared the following variable within a bash script...

```
iP=[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}
```

...which I have used in conjunction with sed to whittle the contents of a file down to a single **line**, similar to:

```
,'laptop1','192.168.1.100','MA:CA:DD:RE:SS:00','21:40:12','100'
```

I am now trying, using sed, to whittle the **line**, further, to a single **string**:

```
192.168.1.100
```

This is one [method]("http://www.cyberciti.biz/faq/sed-remove-all-except-digits-numbers/") with which I have been toying:

```
sed -r 's/[^\('$iP')//g' -i file
```

Essentially, I'd like to remove (using sed) all from the **line**, but for the '$iP' **string**....

Thanks for any suggestions!

---

### Post by mörgæs on 2011-11-28
Moved to Programming Talk.

---

### Post by gmargo on 2011-11-28
I could not get this to work with sed, since I think sed is always "greedy".

However, here it is in Perl.  Note the quotes around the iP definition, to keep the backslashes:

```

$ iP='[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}'
$ echo ",'laptop1','192.168.1.100','MA:CA:DD:RE:SS:00','21:40:12','100'" | perl -p -e "s/.*?($iP).*/\$1/"
192.168.1.100

```

---

### Post by maclenin on 2011-11-28
**mörgæs:** þakka þér - 

**gmargo:** thank you - will give perl a go (being a perl virgin, this is all very exciting).... I'll keep wondering, however, whether there's a sed option - and if I encounter one, will post it back.

This also came to mind: [http://xkcd.com/208/](http://xkcd.com/208/)....

---

### Post by mörgæs on 2011-11-28
Það var lítið.

---

### Post by Arndt on 2011-11-28
I seem to need to escape the { and }, but this way almost works:

```
sed 's/.*[^0-9.]\([0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\).*/\1/'
```

Why almost? Because it fails if the address is at the start of the line.

grep has an option to output only the matching part:

```
grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}'

```

---

### Post by Vaphell on 2011-11-28
you can go with -r for sed, which makes the regex related symbols work without escaping
```
$ echo ",'laptop1','192.168.1.100','MA:CA:DD:RE:SS:00','21:40:12','100'" | sed -r 's/.*[^0-9.]([0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}).*/\1/'
192.168.1.100
```

perl -pe and sed are pretty much equivalent in this case (there are only minute syntax differences)

---

### Post by Simian Man on 2011-11-29
My mom always sed that if you can't sed something positive, you shouldn't sed anything at all.

---

### Post by maclenin on 2011-11-29
...also sed **Arndt**, **Vaphell** and **Simian Man**.... Thank you for the comments.

One final (and related) query.

Why does...
```
sed -r 's/.*('$iP').*/\1/'
```
...yield: **8.1.100**

...and...

```
sed -r 's/.***[COLOR="DarkOrange"][^0-9.][/COLOR]**('$iP').*/\1/'
```
...yield: **192.168.1.100**

Great help and wisdom, all!

---

### Post by Vaphell on 2011-11-29
because of a little screwup with . :-)
. means any char so it matched stuff other than dots and whole thing went bonkers (your \. wasn't preserved because you didn't put the ip in quotes to prevent the change from \. to .)
```
$ ip=1\.1\.1\.1; echo $ip
1.1.1.1
$ ip='1\.1\.1\.1'; echo $ip
1\.1\.1\.1
```

[.] is more foolproof, you explicitly enumerate dot and problem with proper escaping goes away
```
$ echo ",'laptop1','192.168.1.100','MA:CA:DD:RE:SS:00','21:40:12','100'" |
         sed -r 's/.*([0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}).*/\1/'
8.1.100
$ echo ",'laptop1','192.168.1.100','MA:CA:DD:RE:SS:00','21:40:12','100'" |
         sed -r 's/.*([0-9]{1,3}[.][0-9]{1,3}[.][0-9]{1,3}[.][0-9]{1,3}).*/\1/'
2.168.1.100
```
but there is another issue - * is greedy (it consumes as much as possible) so it ate '19' and the pattern was still matched

```
[COLOR="Blue"].*[/COLOR][COLOR="Red"]([/COLOR][COLOR="Green"][0-9]{1,3}[/COLOR][.][0-9]{1,3}[.][0-9]{1,3}[.][0-9]{1,3}[COLOR="Red"])[/COLOR].*
[COLOR="Blue"]some gibberish 19[/COLOR][COLOR="Red"]([/COLOR][COLOR="Green"]2[/COLOR].168.1.100[COLOR="Red"])[/COLOR] ...
```
everything is ok - that 1 digit is matched by [0-9]{1,3}
version with bare dots worked like this
```
.*[COLOR="Blue"][0-9]{1,3}[/COLOR][COLOR="Red"].[/COLOR][COLOR="Blue"][0-9]{1,3}[/COLOR][COLOR="Red"].[/COLOR][COLOR="Blue"][0-9]{1,3}[/COLOR][COLOR="Red"].[/COLOR][COLOR="Blue"][0-9]{1,3}[/COLOR]
gibberish 19[COLOR="Blue"]8[/COLOR][COLOR="Red"].[/COLOR][COLOR="Blue"]1[/COLOR][COLOR="Red"].[/COLOR][COLOR="Blue"]1[/COLOR][COLOR="Red"]0[/COLOR][COLOR="Blue"]0[/COLOR]
```


You prevent that by specifying that the last char before $ip has to be "non-digit,non-dot" thus removing ambiguity completely and pushing '19' into the $ip territory. It also works with those shoddily specified dots almost by accident (though not rly, not enough 'moving parts' to produce very different result) :)
Another option is to play with non-greedy version of * (but sadly it appears it is not supported by sed). Question mark changes the behavior so non-greedy version of 'string made of anything' is **.*?** which was used in the perl example

---

