---
title: "Bash variable"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by raphaelsaldanha on 2012-03-30
Hi!

I'm using pdfjam to adjust some PDFs inside a batch. The basic command goes like this:

```
pdfjam input.pdf --trim '1cm 2cm 1cm 2cm' --clip true --a5paper --outfile output.pdf
```Where the 1cm etc after --trim are margins. I would like to pass these margins by a variable.

I've tried this:

```
MARGINS="'1cm 2cm 1cm 2cm'"
pdfjam input.pdf --trim $MARGINS --clip true --a5paper --outfile output.pdf
```But I receive:

```
pdfjam ERROR: no PDF file found at 2cm
```I would like to create a variable for each margins, and then pass to the command. How can I do this?

---

### Post by SeijiSensei on 2012-03-30
Try this:

```

MARGINS='1cm 2cm 1cm 2cm'
pdfjam input.pdf --trim "$MARGINS" --clip true --a5paper --outfile output.pdf

```

If for some reason that doesn't work replace the MARGINS declaration with

```
MARGINS="1cm\ 2cm\ 1cm\ 2cm"
```

---

### Post by raphaelsaldanha on 2012-03-30
Hi SeijiSensei, thanks for the tip!

Another way I discovered is:

```
eval pdfjam input.pdf --trim $MARGINS --clip true --a5paper --outfile output.pdf
```

---

