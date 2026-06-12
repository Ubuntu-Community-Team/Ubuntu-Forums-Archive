---
title: "double whitespaces in variable"
date: 2010-02-10
forum: Programming Talk
---

### Post by editorreilly on 2010-02-10
I have a script that needs to be able to preserve double/triple/quadrupal whitespaces in a variable.  When I run my script 'file_mover.sh':


```

#!/bin/bash
input2=$(ls -t ~/Desktop/*.mov)  ####$input2 has 4 whitespaces###
scp -p ~/Desktop/"$input2" root@remoteserver://home/user/Desktop/
ssh root@remoteserver mv /home/user/Desktop/"$input2" /home/user/Desktop/uploads/"$input2" 

```

An error pops up saying it cant find file, it only reads the last part of the filename after the whitespaces.

Any ideas why the whitespaces aren't preserved through an SSH command?

Thanks for the help!

---

### Post by editorreilly on 2010-02-11
I found the answer  I must have the variable "$input2" inside single quotes as well.  "'$input2'"

---

