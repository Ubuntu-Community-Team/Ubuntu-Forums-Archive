---
title: "[BASH] File Editing"
date: 2011-11-08
forum: Programming Talk
---

### Post by hantechbl on 2011-11-08
Hello,
I have another question about bash scripting, I need to be able to remove lines from a file that contain the exact string, so that for example: when trying to remove string "1" it won't remove String "11" Is there a way that I can trim whole lines and have it so it only deletes the line if the whole string matches?  If not, is there a way to tack on the zeroes?

---

### Post by ofnuts on 2011-11-08
> **hantechbl said:**
> Hello,
I have another question about bash scripting, I need to be able to remove lines from a file that contain the exact string, so that for example: when trying to remove string "1" it won't remove String "11" Is there a way that I can trim whole lines and have it so it only deletes the line if the whole string matches?  If not, is there a way to tack on the zeroes?
```

grep -v "^${your_string}$" < $file > $filtered_file

```"grep -v" removes lines that match, and "^" and "$" (this is the "$" at the end) indicate beginning and end of lines, so this only removes lines that exactly match the input string.

---

### Post by markbl on 2011-11-08
Normally would use sed for this:
```

sed -i '/^text line to delete$/d' file

```

---

### Post by geirha on 2011-11-09
It sounds like this could be related to this question in the BashFAQ,
[How can I get all lines that are: in both of two files (set intersection) or in only one of two files (set subtraction)](http://mywiki.wooledge.org/BashFAQ/036), so I'll just leave that link here just in case.

At any rate, I'd go with grep -Fxv since you don't need to match the lines with a regular expression.

---

### Post by ofnuts on 2011-11-09
> **geirha said:**
> It sounds like this could be related to this question in the BashFAQ,
[How can I get all lines that are: in both of two files (set intersection) or in only one of two files (set subtraction)]("http://mywiki.wooledge.org/BashFAQ/036"), so I'll just leave that link here just in case.

At any rate, I'd go with grep -Fxv since you don't need to match the lines with a regular expression.
At least I got the "-v" right :)

---

