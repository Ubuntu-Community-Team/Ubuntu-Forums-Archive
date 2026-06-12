---
title: "Help using cat EOF with lines containing $ as char and not variable..."
date: 2016-04-28
forum: Programming Talk
---

### Post by john_reyes2 on 2016-04-28
Hey all

ive got at problem i need a solution to;

ive got a 

```
cat <<EOF > file
text
text
text
.23424rfs$asdf.234.
EOF

```
there $asdf is not a variable, but actual text (a hassword hash containing $)

how do i get around this?

---

### Post by spjackson on 2016-04-28
One way is to escape the $ with \, i.e.
```

cat <<EOF > file
text
text
text
.23424rfs\$asdf.234.
EOF

```

---

### Post by steeldriver on 2016-04-28
Alternatively, you can add quotes to the EOF delimiter i.e.

```

cat <<"EOF" > file

```

as explained in the bash manpage

```

       No  parameter  and variable expansion, command substitution, arithmetic
       expansion, or pathname expansion is performed on word.  **If any  charac&#8208;**
       **ters  in  word are quoted**, the delimiter is the result of quote removal
       on word, and the **lines in the here-document are not expanded**.  If  word
       is  unquoted, all lines of the here-document are subjected to parameter
       expansion, command substitution, and arithmetic expansion, the  charac&#8208;
       ter  sequence  \<newline>  is  ignored, and \ must be used to quote the
       characters \, $, and `.

```

---

