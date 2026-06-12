---
title: "bash: test if program is running"
date: 2007-07-01
forum: Programming Talk
---

### Post by jmc1024 on 2007-07-01
I have a cron job that runs 'xfdesktop --reload' every 10 mins.  If xfdesktop is not running 
then I get errors.  So I want to write a bash script that tests if xfdesktop is running before
running 'xfdesktop --reload'.  Is there something besides ps and awk that I can use?  
Thanks,
Mark

---

### Post by meatpan on 2007-07-01
Just curious, is there a specific reason why you don't want to use ps?  This is a very easy task if you use ps.

---

### Post by diatribe on 2007-07-01
> **meatpan said:**
> Just curious, is there a specific reason why you don't want to use ps?  This is a very easy task if you use ps.

indeed you are making a simple task more complicated

---

### Post by jyba on 2007-07-02
I agree with both replies above, ps is the right tool. A shorthand way of doing it would be would be...

```
ps -C "xfdesktop" >& /dev/null; [[ $? -eq 0 ]] && xfdesktop --reload || xfdesktop 
```

Or, if you prefer a slightly clearer version...

```
ps -C "xfdesktop" >& /dev/null
if [[ $? -eq 0 ]]; then
    xfdesktop --reload
else xfdesktop
fi
```

---

### Post by jmc1024 on 2007-07-02
Thanks for the replies.  ps -C is just what I needed.  I didn't know it was available.  Should have read
the man page...
Thanks again,

---

