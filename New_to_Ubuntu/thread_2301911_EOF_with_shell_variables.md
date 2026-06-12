---
title: "EOF with shell variables?"
date: 2015-11-06
forum: New to Ubuntu
---

### Post by CrewDK on 2015-11-06
Is it passible to use EOF command instead "echo >" with shell variables in bash scripts? 

I mean i have, for example, this script: 

```
#!/bin/bash
hi="Hello World"

echo ${hi} > ./hello.txt

```

Is it possible to use something like this?

```
#!/bin/bash
hi="Hello World"

cat <<"EOF" > ./hello.txt
 ${hi}
EOF 
```

---

### Post by steeldriver on 2015-11-06
What you seem to be talking about is a shell feature called a *here document* (rather than a "command" called EOF)

Shell variables within a here document are expanded if you don't quote any part of the delimiter word. Specifically, the bash manual says:

   ```

Here Documents
       This type of redirection instructs the shell to  read  input  from  the
       current source until a line containing only delimiter (with no trailing
       blanks) is seen.  All of the lines read up to that point are then  used
       as the standard input for a command.

The format of here-documents is:

              <<[-]word
                      here-document
              delimiter

       No  parameter  and variable expansion, command substitution, arithmetic
       expansion, or pathname expansion is performed on word.  If any  charac&#8208;
       ters  in  word are quoted, the delimiter is the result of quote removal
       on word, and the lines in the here-document are not expanded. [B] If  word
       is  unquoted, all lines of the here-document are subjected to parameter
       expansion[/B], command substitution, and arithmetic expansion, the  charac&#8208;
       ter  sequence  \<newline>  is  ignored, and \ must be used to quote the
       characters \, $, and `.

```

i.e. you just need to replace

```

cat <<"EOF" > ./hello.txt

```

with
```

cat <<EOF > ./hello.txt

```

---

### Post by CrewDK on 2015-11-06
Oh. Thank you. :)

---

