---
title: "Bash uppercase after {. ! ?}"
date: 2014-01-31
forum: Programming Talk
---

### Post by Albert_U on 2014-01-31
how can i convert the first letter after ".", "!" and "?" and new line to an uppercase letter?
example: "hello. my name is newbe.can u help me?" to " Hello. My name is newbe.Can u help me?"

i tried something with sed but it just convert just the first letter from new line
sed 's/^\([A-Za-z]\)\([A-Z-a-z]\+\)/\U\1\L\2/'

---

### Post by Lars Noodén on 2014-01-31
There's a way to do it in perl:

```

echo "hello. my name is newbe.can u help me?"  | perl -e 'while (<>) { s/^(\s*.)/\U$1/;s/([[:punct:]]\s*.)/\U$1/g;print}'

```

There might be a more efficient way.  Basically that is a short program jammed into a single line.

```

while (<>) {                            # read from stdin until no more input
  s/^(\s*.)/\U$1/;                   # substitute
  s/([[:punct:]]\s*.)/\U$1/g;  # global substitute, pattern starts with punctuation
  print
}

```

All that takes effect on the default variable of perl, $_ which is implied if it is not written.

---

### Post by steeldriver on 2014-01-31
Possible slightly more compact version using lookbehinds?

```

perl -pe 's/((?<!.)|(?<=[[:punct:]])\W*)\w/\U$&/g'

```

(matches and uppercases any single word character that is preceded either by nothing or by punctuation and zero or more additional non-word characters)

---

### Post by trent.josephsen on 2014-01-31
Unnecessarily complex, I think. Perl's motto applies.

```
perl -pe 's/(^|[.!?])([a-z])/$1\U$2/g' # how I would write it using common idioms
perl -pe 's/(?<![^.!?])\w/\U$&/g'      # code golf version
```

---

### Post by Lars Noodén on 2014-01-31
trent and steeldriver, thanks.  I was looking for -p, it eliminates the while loop.

---

### Post by kurum! on 2014-01-31
```

# echo "hello. my name is newbe.can u help me?" | ruby -e 'puts gets.split(/\s*\.\s*/).map(&:capitalize).join(". ") '
Hello. My name is newbe. Can u help me?



```

---

