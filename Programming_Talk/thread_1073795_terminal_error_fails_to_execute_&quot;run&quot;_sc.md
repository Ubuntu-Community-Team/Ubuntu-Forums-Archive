---
title: "terminal error fails to execute &quot;run&quot; script in gedit for cpp files"
date: 2009-02-18
forum: Programming Talk
---

### Post by Shpongle on 2009-02-18
im trying to compile and run cpp files in gedit, the scripts work grand because i got them from my lecturer as he uses them on his machine , it compiles fine and creates the object file ect... but when i go to run it i get an error saying terminal failed to create child process?

il post the scripts any way , 



C/C++ Compile
#!/bin/bash
# Store the file name in a variable
echo "Compiling " $GEDIT_CURRENT_DOCUMENT_PATH
FILE_NAME=$GEDIT_CURRENT_DOCUMENT_NAME
# Check if file extension is .cpp
if [ `echo $FILE_NAME | cut -d "." -f 2` = "cpp" ]
then
FILE_NAME_LEN=`expr ${#FILE_NAME} - 4`
FILE_NAME_BASE=${FILE_NAME:0:$FILE_NAME_LEN}
g++ -o $FILE_NAME_BASE $GEDIT_CURRENT_DOCUMENT_NAME
fi
# Check if the file extension is c
if [ `echo $FILE_NAME | cut -d "." -f 2` = "c" ]
then
FILE_NAME_LEN=`expr ${#FILE_NAME} - 2`
FILE_NAME_BASE=${FILE_NAME:0:$FILE_NAME_LEN}
gcc -o $FILE_NAME_BASE $GEDIT_CURRENT_DOCUMENT_NAME
fi
exit 0


Running:
cat > runit.sh << datatag
#!/bin/bash
${GEDIT_CURRENT_DOCUMENT_NAME%.*}
read -p"Program finished. Press any key to exit..." -n1
datatag
chmod u+x runit.sh
gnome-terminal --command="runit.sh" --working-directory=$GEDIT_CURRENT_DOCUMENT_DIR --title="${GEDIT_CURRENT_DOCUMENT_NAME%.*}"


ny ideas any1??

---

### Post by dwhitney67 on 2009-02-18
I have no ideas what is causing your grief.

I created plugins for both of the scripts you posted (Edit -> Preferences -> Plugins), where I named the first plugin "Compile", the second plugin "Run Application".

I then compiled my application and then ran it, by referencing the appropriate menu item in the "Tools" menu.

Everything worked fine.

P.S.  Not that it makes any difference in sorting out your system's problem, but you should consider using an "elif" in your script; after all, you cannot possibly be compiling a C++ source file _and_ a C source file.
```

#!/bin/bash
# Store the file name in a variable
echo "Compiling " $GEDIT_CURRENT_DOCUMENT_PATH
FILE_NAME=$GEDIT_CURRENT_DOCUMENT_NAME

# Check if file extension is .cpp
if [ `echo $FILE_NAME | cut -d "." -f 2` = "cpp" ]
then
FILE_NAME_LEN=`expr ${#FILE_NAME} - 4`
FILE_NAME_BASE=${FILE_NAME:0:$FILE_NAME_LEN}
g++ -o $FILE_NAME_BASE $GEDIT_CURRENT_DOCUMENT_NAME

# Check if the file extension is c
elif [ `echo $FILE_NAME | cut -d "." -f 2` = "c" ]
then
FILE_NAME_LEN=`expr ${#FILE_NAME} - 2`
FILE_NAME_BASE=${FILE_NAME:0:$FILE_NAME_LEN}
gcc -o $FILE_NAME_BASE $GEDIT_CURRENT_DOCUMENT_NAME
fi

exit 0

```

---

### Post by Shpongle on 2009-02-22
yea i know man im only compiling c++, its just what my lecturer had written, any one any other ideas??

---

### Post by Shpongle on 2009-02-23
I fixed it with the help from my lecturer, the path wasnt set correctly

this code was added to fix the path to the ect/profile


PATH=.:$PATH

---

