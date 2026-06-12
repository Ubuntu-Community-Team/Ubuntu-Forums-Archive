---
title: "Bash scripting with variables"
date: 2012-01-18
forum: Programming Talk
---

### Post by bubbly193 on 2012-01-18
How do you log a variable

IE
> #!/bin/bash
ECHO "insert some string, please"
read var
??????
##?????? is an unknown code for logging $var to ~/.results/testlogs/test-mechanics-test.log

---

### Post by Lars Noodén on 2012-01-18
Do you mean something like this, using a [redirect](http://mywiki.wooledge.org/BashGuide/InputAndOutput#Redirection)?

```

#!/bin/bash
read -p "insert some string, please" var
echo ${var} >> ~/.results/testlogs/test-mechanics-test.log 

```

---

