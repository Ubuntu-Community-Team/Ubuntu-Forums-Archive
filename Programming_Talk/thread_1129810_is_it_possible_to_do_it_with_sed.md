---
title: "is it possible to do it with sed?"
date: 2009-04-19
forum: Programming Talk
---

### Post by StOoZ on 2009-04-19
or awk.
I have something like this :
> Published by: Lucic PAPA
Developed by: XXXXXXXX
Release Date: 
December 18, 2008
Genre:
Third-Person
Shooter



what I want to do is , whenever I have a Line without any :'s (like line 3 and 5,6) , I want to concatenate these lines to the first line above them which has a ':' 

for this example , I need it to be :
> Published by: Lucic PAPA
Developed by: XXXXXXXX
Release Date: December 18, 2008
Genre: Third-Person , Shooter


is it possible?

---

### Post by ghostdog74 on 2009-04-19
awk:
```

# awk 'ORS=/:$/?" ":"\n"' file
Published by: Lucic PAPA
Developed by: XXXXXXXX
Release Date: December 18, 2008
Genre: Third-Person
Shooter

```

if you prefer Perl
```

# perl -ne 'chomp;print if $\=/:$/?" ":"\n";' file
Published by: Lucic PAPA
Developed by: XXXXXXXX
Release Date: December 18, 2008
Genre: Third-Person
Shooter

```

---

### Post by odyniec on 2009-04-19
For the record, an ugly sed oneliner:
```
% (cat input; echo ":") | sed -n ':1 /:$/{:2 H;n;/:/{x;y/\n/ /;s/^ //;p;s/.*//;x;b 1};b 2};p' 
Published by: Lucic PAPA
Developed by: XXXXXXXX
Release Date: December 18, 2008
Genre: Third-Person Shooter
```

---

