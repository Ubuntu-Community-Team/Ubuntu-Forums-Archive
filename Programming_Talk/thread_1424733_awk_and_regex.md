---
title: "awk and regex"
date: 2010-03-08
forum: Programming Talk
---

### Post by Grenage on 2010-03-08
Greetings,

I've done some looking around, but haven't been able to solve my problem.  There is a good chance I'm going about this the wrong way, so feel free to steer me in the right direction.

I have a generic CSV; it's an exchange output with lots of superfluous data.  I want to take from this CSV all of $1-$9, but only what matches a regex from $10.  Example:

Line String:
```
Mailbox,JS,John Swith,JS,JS,DOM\JS,MAILSERVER,,"SMTP:js@ciaalarms.co.uk%X400:c=US;a= ;p=Sec
```

Desired Output:
```
Mailbox,JS,John Swith,JS,JS,DOM\JS,MAILSERVER,,js@domain.co.uk
```

My awk command is:

```
awk -F, /[a-zA-Z]*+@[a-zA-Z]*+\.co+\.uk/ {print $1","$2","$3","$4","$5","$6","$7","$8","$9} myfile.csv
```

Obviously this will print the full fields for every line that has a match, so how would I strip $10 down to just the e-mail address?

---

### Post by ebichete on 2010-03-08
```

awk -F, 'NF >= 9 {match($9,/[a-zA-Z]+@[a-zA-Z]+\.co+\.uk/); if (RSTART>=0) print $1","$2","$3","$4","$5","$6","$7","$8","substr($9,RSTART,RLENGTH)}' < myfile.csv

```

You appear to have 9, not 10, fields.

---

### Post by Grenage on 2010-03-08
It looks like I missed a field out in my example.  Thanks for your code, it does just what I need; I'll examine your syntax and see how it works, for future use.

Thanks!

---

