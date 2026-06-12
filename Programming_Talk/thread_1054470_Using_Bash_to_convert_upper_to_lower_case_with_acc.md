---
title: "Using Bash to convert upper to lower case with accented letters"
date: 2009-01-29
forum: Programming Talk
---

### Post by phenest on 2009-01-29
How is it done?

```
echo "Prélude À L'Après-Midi D'Un Faune" | tr [:upper:] [:lower:]
prélude À l'après-midi d'un faune
```
As you can see, the À is still capitalized because tr doesn't seem to handle accented letters.

An even better idea would be to convert all accented letters to lower case without the accents at all.

Any one know how? To do it with tr is quite lengthy.

---

### Post by stylishpants on 2009-01-29
Python 3 has very good native unicode support.
How about this?

```


fhanson@fhanson:/tmp$ sudo aptitude install python3
...

fhanson@fhanson:/tmp$ echo "Prélude À L'Après-Midi D'Un Faune"  | python3 -c 'import sys; print( sys.stdin.read().lower() )'
prélude à l'après-midi d'un faune




```

---

### Post by phenest on 2009-01-29
Nice one. Can it be used for removing the accents?

---

### Post by stylishpants on 2009-01-29
Hmm.  I'm sure it can but I don't know how.

I got this far:

```
fhanson@fhanson:/tmp$ echo "Prélude À L'Après-Midi D'Un Faune" | python -c 'import sys, unicodedata; print unicodedata.normalize("NFKD", unicode(sys.stdin.read()).encode("ASCII","replace") )'
Traceback (most recent call last):
  File "<string>", line 1, in <module>
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 2: ordinal not in range(128)

```

Perhaps some of the local python gurus can fix it.  I'm out of time.

---

### Post by unutbu on 2009-01-29
```
apt-cache search accent

```
yields
```

unaccent - Replace accented letters by their unaccented equivalent
```
```

apt-cache show unaccent

```
yields
```

Description: Replace accented letters by their unaccented equivalent
 read data from stdin, replace accented letters by their unaccented
 equivalent and write the result on stdout.
```

```

apt-file list unaccent
```

yields```


unaccent: /usr/bin/unaccent
```

---

### Post by phenest on 2009-01-30
Who'd of thought the package would be called unaccent? ;)

Anyway, so:
```
 echo "Prélude À L'Après-Midi D'Un Faune" | unaccent UTF-8 | tr [:upper:] [:lower:]
prelude a l'apres-midi d'un faune
```
...pretty much does the job.

Thanks all.

---

### Post by PierreJourlin on 2012-03-27
> **phenest said:**
> To do it with tr is quite lengthy.

Not that lengthy :

```
tr 'A-ZÂÁÀÄÊÉÈËÏÍÎÖÓÔÖÚÙÛÑÇ' 'a-zâáàäêéèëïíîöóôöúùûñç'
```

---

### Post by Arndt on 2012-03-28
> **PierreJourlin said:**
> Not that lengthy :

```
tr 'A-ZÂÁÀÄÊÉÈËÏÍÎÖÓÔÖÚÙÛÑÇ' 'a-zâáàäêéèëïíîöóôöúùûñç'
```

You forgot Å.

And the original poster may not read this thread anymore.

---

