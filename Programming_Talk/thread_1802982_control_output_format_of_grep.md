---
title: "control output format of grep"
date: 2011-07-12
forum: Programming Talk
---

### Post by decoherence on 2011-07-12
Hi everyone,

I wish to generate a list of active user accounts and the community they are in. For instance 

> london 12345
london 45621
dubai 98765
newyork 47238
mars 23487

Currently I have a job that looks like this 

```
ldapsearch "accountStatus=active" | grep 'mailHost\|uidNumber' | awk -F': ' '{print $2}' | awk -F'-' '{print $1}'
```

which generates 

> london
12345
london
45621
dubai
98765
newyork
47238
mars
23487

(for the record, 'mailHost' is of the form newyork-mail.myisp.com, etc. which is what the second awk is for)

I suspect that by substituting grep for an appropriate awk command (some variation of "awk '/mailHost|uidNumber/'"), i can get the formatting I want. Unfortunately, aside from pulling fields out of text, I'm clueless with awk. Is there an guru who can point me in the right direction?

Thanks a lot for any suggestions!

---

### Post by decoherence on 2011-07-12
a partial solution would be to pipe the output to ```
awk 'ORS=NR%2?" ":"\n"'
``` however since our ldap directory isn't perfectly clean, the list has the potential to be wrong. It would be ideal to work this in where grep command is (which would be substituted for an awk command)

---

### Post by dethorpe on 2011-07-13
If i've understood the format of the ldapsearch output, something like this might do:
```
 
 
ldapsearch "accountStatus=active" | awk -F': ' '/uidNumber/ {ORS="\n";print $2}
                                                /mailHost/  {ORS=" ";split ($2,fields,"-"); print fields[1]}'
 
 

```

---

### Post by decoherence on 2011-07-13
Wow, nice job dethorpe! It looks like that does exactly what I want -- thank you so much for your help!

EDIT: I may have spoken too soon. While the output is much better than piping to awk 'ORS=NR%2?" ":"\n"', our ldap is gnarly enough to cause some strangeness. Here is some fake output to illustrate

london 12345
london 45621
dubai newyork 98765
newyork mars 47238
mars 23487 

but you've got me on the right track! time for me to investigate the specific inconsistencies in our ldap and either fix them or make the appropriate adjustments to the awk job. thanks again!

---

### Post by dethorpe on 2011-07-13
Glad i could help.
 
Just post back if you need any more help, a sample of the ldapsearch output would be useful if you do.
 
(personally I'd reach for perl if it gets much more complex, but awk should be able to do it if thats what you have/want to use)
 
Good luck

---

