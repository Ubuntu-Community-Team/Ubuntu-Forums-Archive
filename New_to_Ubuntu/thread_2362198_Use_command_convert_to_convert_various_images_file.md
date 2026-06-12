---
title: "Use command convert to convert various images files on pdf with order growing"
date: 2017-05-25
forum: New to Ubuntu
---

### Post by sed_faster on 2017-05-25
Hello folks,

I intend use this command to convert jpg file to a pdf file, but this images should be on growing.
```

convert *.jpg file.pdf

```

this command works but the pages didn't be on order. The output ls is:
```

large-1097724-10.pdf  large-1097724-24.pdf  large-1097724-38.pdf
large-1097724-11.pdf  large-1097724-25.pdf  large-1097724-39.pdf
large-1097724-12.pdf  large-1097724-26.pdf  large-1097724-3.pdf
large-1097724-13.pdf  large-1097724-27.pdf  large-1097724-40.pdf
large-1097724-14.pdf  large-1097724-28.pdf  large-1097724-41.pdf
large-1097724-15.pdf  large-1097724-29.pdf  large-1097724-42.pdf
large-1097724-16.pdf  large-1097724-2.pdf   large-1097724-43.pdf
large-1097724-17.pdf  large-1097724-30.pdf  large-1097724-44.pdf
large-1097724-18.pdf  large-1097724-31.pdf  large-1097724-4.pdf
large-1097724-19.pdf  large-1097724-32.pdf  large-1097724-5.pdf
large-1097724-1.pdf   large-1097724-33.pdf  large-1097724-6.pdf
large-1097724-20.pdf  large-1097724-34.pdf  large-1097724-7.pdf
large-1097724-21.pdf  large-1097724-35.pdf  large-1097724-8.pdf
large-1097724-22.pdf  large-1097724-36.pdf  large-1097724-9.pdf
large-1097724-23.pdf  large-1097724-37.pdf 

```

How can I do to use command convert and convert all this images on a pdf file with order?
I tried create a loop for, on shell script, but didn't works!

[UPDATE]
Innitial I has a images file, but I convert all images jpg to pdf, because I though user this command to convert pdf file with order growing:
```

pdftk file1.pdf file2.pdf cat output mergedfile.pdf

```
But the result it was the same!

Thanks

---

