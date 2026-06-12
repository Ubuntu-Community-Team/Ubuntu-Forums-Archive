---
title: "Sed/Awk Rearrange"
date: 2012-03-05
forum: Programming Talk
---

### Post by mastermindg on 2012-03-05
How do I get this:

<TABLE>
<TR>
<TD></TD>
</TR>
</TABLE>

to this:

<TABLE><TR><TD></TD></TR></TABLE> 

using Sed or AWK? Thanks :confused:

---

### Post by Lars Noodén on 2012-03-05
Looking around I found this recipe to remove newlines:
```

sed ':a;N;$!ba;s/\n//g'

```

There are a lot of sed one-liners out there.

---

### Post by mastermindg on 2012-03-05
Thanks for the quick response!

Unfortunately I always seem to oversimplify my posts :)

I have a table with many rows that looks like this:

<TABLE>
<TR>
<TD></TD>
</TR>
<TR>
<TD></TD>
</TR>
</TABLE>

and needs to looks like this:


<TABLE>
<TR><TD></TD></TR>
<TR><TD></TD></TR>
</TABLE>

---

### Post by ofnuts on 2012-03-05
Oversimplification question: are the <TD> empty, or do they have content?

---

### Post by Khayyam on 2012-03-05
Yes, as ofnuts asked ... but this should protect whatevers between '<TD></TD>' ..  

```
awk -v RS='' '{print $1"\n"$2$3$4"\n"$5$6$7"\n"$8}' input.txt
```

If the input has other tags then the following will select only the '<TABLE>*</TABLE>'

```
awk -v RS='' '/<TABLE>/,/<\/TABLE>/{print $1"\n"$2$3$4"\n"$5$6$7"\n"$8}' input.txt
```

best .. khay

EDIT: actually, it won't work as expected, I solved one problem only to create another. I'll work on a possible solution.

---

### Post by mastermindg on 2012-03-06
All of the tags have content including <TR><TD> and <TABLE> (though <TABLE> isn't really required for awk). Thanks!

---

### Post by Khayyam on 2012-03-06
> **mastermindg said:**
> All of the tags have content including <TR><TD> and <TABLE> (though <TABLE> isn't really required for awk).

If it "isn't required for awk" then your actually not looking to do what you first asked. I suspect there is some other reason you want those tags aligned as why would they need to be ... other than it suites how your plan to parse it (a la awk).

best ... khay

---

