---
title: "Piping output of wget"
date: 2015-03-09
forum: New to Ubuntu
---

### Post by Raman_Butta on 2015-03-09
I wish to pipe the output of wget <url> to wkhtmltopdf to save a website tree as a single pdf file. Can anyone help me with the proper syntax or suggest an alternative ?

---

### Post by Lars Noodén on 2015-03-09
If [wkhtmltopdf](http://wkhtmltopdf.org/usage/wkhtmltopdf.txt) can read from stdin like this:

```

cat index.html | wkhtmltopdf - index.pdf

```

Then you could get [wget](http://manpages.ubuntu.com/manpages/trusty/en/man1/wget.1.html) to dump to stdout:

```

wget -O http://foo.example.com/bar.html  |  wkhtmltopdf - bar.pdf

```

However, wkhtmltopdf is not in the Ubuntu repository so I can't check to be sure.

---

