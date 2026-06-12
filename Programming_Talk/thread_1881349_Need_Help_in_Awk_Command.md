---
title: "Need Help in Awk Command"
date: 2011-11-15
forum: Programming Talk
---

### Post by rohit verma on 2011-11-15
hi all,
please look into this:

command] echo -e "hello \t$5.6" | awk -F'\t' '{print $0;}'
output     ] hello   .6
expected ] hello   $5.6


is there any switch or option that i can use in awk to print "$5.6", rather than escaping it in input.


Thanks & Regards,
R Verma
2011-11-15

---

### Post by s.fox on 2011-11-15
Thread moved to [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by dethorpe on 2011-11-15
Your problem is the shell not awk. The shell is expanding $5 as an environment variable, which dosn't exist so comes out blank.
 
Two options:
 
1) Quote the $
 
echo -e "hello \t\$5.6" | awk -F'\t' '{print $0;}'
 
2) Use single quotes to prevent shell expansion:
 
echo -e 'hello \t$5.6' | awk -F'\t' '{print $0;}'

---

### Post by rohit verma on 2011-11-16
thanks buddy! :)

---

