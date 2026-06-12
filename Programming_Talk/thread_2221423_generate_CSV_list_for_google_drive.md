---
title: "generate CSV list for google drive"
date: 2014-05-02
forum: Programming Talk
---

### Post by MikeCyber on 2014-05-02
Hi
I want to create a CSV list for google drive and have those data (thunderbird export eml) for ~40 contacts:

X-Mozilla-Status: 0001 
X-Mozilla-Status2: 00800000 
X-Mozilla-Keys:                                                                                  
BCC: Ryan F <test@YAHOwaO.COM>, [email]teestmfawdj@gmail.com[/email],  
 Peter Wls <testpwm@yahoo.co.wauk>, 
 [email]testmike@ru.co.nz[/email], [email]testgwka@gmail.caom[/email], Paolo Boa <btessoa.apwaolo@gmail.com>,  
 Dennis Luck <dklcwtestak@mac.com>,
etc.
many more lines to skip. I only need name and email. If no name is given probably something else, a number whatever. Or skip the names and only extract the emails.
I guess csv should look alike for google drive?

overthere        [email]overthere@gmail.com[/email],
next               [email]next@there.com[/email],
thrid              [email]third@thee.com[/email],
etc.

does it need a comma after the email? How to extract those with bash?
Many thanks indeed.

---

### Post by Vaphell on 2014-05-02
script that is nothing more than a wrapper for awk
```
#!/bin/bash

awk 'BEGIN { RS="[ \t\n]*[:,][ \t\n]*"; FS="[ \t\n]*[<>][ \t\n]*"; }
       /@/ { printf "\"%s\",\"%s\"\n", (NF>1?$1:"<unknown>"), (NF>1?$2:$1); }' "$@"
```

```
$ cat eml.txt
X-Mozilla-Status: 0001
X-Mozilla-Status2: 00800000
X-Mozilla-Keys:
BCC: Ryan F <test@YAHOwaO.COM>, teestmfawdj@gmail.com,
Peter Wls <testpwm@yahoo.co.wauk>,
testmike@ru.co.nz, testgwka@gmail.caom, Paolo Boa <btessoa.apwaolo@gmail.com>,
Dennis Luck <dklcwtestak@mac.com>
$ ./eml.sh eml.txt
"Ryan F","test@YAHOwaO.COM"
"<unknown>","teestmfawdj@gmail.com"
"Peter Wls","testpwm@yahoo.co.wauk"
"<unknown>","testmike@ru.co.nz"
"<unknown>","testgwka@gmail.caom"
"Paolo Boa","btessoa.apwaolo@gmail.com"
"Dennis Luck","dklcwtestak@mac.com"
```

---

### Post by MikeCyber on 2014-05-03
Great. Many thanks indeed.

---

