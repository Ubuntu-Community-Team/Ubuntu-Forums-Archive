---
title: "&quot;Read&quot; for a fraction of a second? Possible?"
date: 2009-02-06
forum: Programming Talk
---

### Post by pbotros1234 on 2009-02-06
I'm writing a script in BASH (I know... bash. gotta start somewhere) that will look up a question, get the lines to print, and print each line letter by letter. Everything works fine, except I also need the script to be able to stop anytime during the printing when the user presses a key.

In order for me to print each letter, I am spacing each letter out with a "sleep .075", which works fine. But, if I could do something to the effect of "read -t .075 -sn 1 KEY", that would work even better. But, I get a ```
bash: read: .5: invalid timeout specification
``` when I try that.

Suggestions? Sorry for the vagueness. :(

---

### Post by Krupski on 2009-02-06
> **pbotros1234 said:**
> I'm writing a script in BASH (I know... bash. gotta start somewhere) that will look up a question, get the lines to print, and print each line letter by letter. Everything works fine, except I also need the script to be able to stop anytime during the printing when the user presses a key.

In order for me to print each letter, I am spacing each letter out with a "sleep .075", which works fine. But, if I could do something to the effect of "read -t .075 -sn 1 KEY", that would work even better. But, I get a ```
bash: read: .5: invalid timeout specification
``` when I try that.

Suggestions? Sorry for the vagueness. :(

I'm not sure I understand what you want.

Do you want to read a text file, display it to standard out and be able to interrupt it instantly by pressing any key?

Let me know what you're after... I might be able to help.

-- Roger

---

### Post by geirha on 2009-02-07
Interesting problem! If I understand you correctly, you want the question to be slowly revealed, and when the user/player thinks he knows what the question and its answer is, he/she should be able guess the answer, in which case the printing of the question should be paused.

One way I can think of is to first start a read in the background, however, once the read is in the background, the variable it writes to will not be available in the main script, so I propose using a temporary file.

```
tmp=$(tempfile)
{ IFS=$'\0'; read -sn1 KEY; echo -n "$KEY" > "$tmp"; } <&0 &

# question-printing loop here

```

Inside the loop, you can now use stat to check the size of the temporary file and break out of the loop to read the user/player's answer.

```
[ $(stat -c %s "$tmp") -gt 0 ] && break
```

The temporary file will not be removed automatically when the script exits, so you should do an rm "$tmp" when the file is no longer needed. A trap that triggers on EXIT would be a good idea for that.

---

