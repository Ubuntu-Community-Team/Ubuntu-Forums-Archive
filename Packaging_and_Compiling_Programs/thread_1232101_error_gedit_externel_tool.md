---
title: "error gedit externel tool"
date: 2009-08-05
forum: Packaging and Compiling Programs
---

### Post by jndlsnl on 2009-08-05
hi,

i make a new tool via externel tool in gedit to compile and run java programs

in this tool i give a command----


#!/bin/sh
cd $GEDIT_CURRENT_DOCUMENT_DIR
if javac $GEDIT_CURRENT_DOCUMENT_NAME;
then
java ${GEDIT_CURRENT_DOCUMENT_NAME%\.java}
else
echo "Failed to compile"
fi



but this command is not working...when i run this tool it display tht javac couldn't found...

can anyone tell me how can fix this problem....

---

### Post by Leslie Viljoen on 2009-08-06
If I run "which javac" on the command line I get "/usr/bin/javac". Perhaps if you do the same and then put the full path to javac in your script, it will be found. You'll need to do the same for "java".

---

