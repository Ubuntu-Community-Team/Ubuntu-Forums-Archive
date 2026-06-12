---
title: "zenity --scale and decimal separator"
date: 2009-08-11
forum: Programming Talk
---

### Post by sarduwie on 2009-08-11
Hi everyone.

I'm writing a shell script to encode a number of .flac files to .oga/Vorbis. I want the user to be able to pick a value for oggenc's --quality argument (-1 to 10, fractional values allowed) using a zenity scale dialog.

```
zenity --scale --min-value=-1 --max-value=10 --step=0.01 --value=4.5 --print-partial
``` doesn't work

The result is a localized error message that roughly translates to "This option is not available. See --help for all possible uses."

--help is of little help :(

I've tried to replace . with , (which is the decimal separator in my locale) but that didn't work either.

I could leave out the --step and --print-partial argument but I'd prefer to keep it for finer granularity.

Can anyone help me? Is what I'm trying to do even possible?

---

### Post by unutbu on 2009-08-11
I could be wrong but it appears that zenity --scale is limited to integers. If so, perhaps just scale everything up by 100:

```
zenity --scale --min-value=-100 --max-value=1000 --step=1 --print-partial --value=450
```

and divide the result by 100.

---

