---
title: "Regular expression searching not working"
date: 2017-03-27
forum: Programming Talk
---

### Post by s3a on 2017-03-27
Hello, everyone. :)

I'm to trying to find words containing *shelf* or *self*, and I tried using the commands, but none of them worked:
*grep s[h?]elf /usr/share/dict/words*
*grep s[h\?] /usr/share/dict/words*
*grep sh\?elf /usr/share/dict/words*

I also tried using the -e and -E parameters and/or adding (double) quotation marks, but the commands still don't work with them.

Later I want to try with the "or" way, but for now, I am stuck with the above.

Could someone please help me figure out what I am doing wrong?

---

### Post by steeldriver on 2017-03-27
Any of

```

grep 'sh\?elf'

grep -E 'sh?elf'

grep 'sh\{0,1\}elf'

grep -E 'sh{0,1}elf'

```

should do it - don't include the quantifier inside a range expression [ ] and remember to always quote the regex so that it is not subject to expansion by the shell

---

### Post by s3a on 2017-03-27
That was very helpful! Thanks!

---

