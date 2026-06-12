---
title: "If statement to look in another directory"
date: 2007-10-23
forum: Programming Talk
---

### Post by Mbengi Bongi on 2007-10-23
How can i get bash to look for a file in another directory if the file specified does not exist in the current directory?

Basically i have a shell script that looks for a file and reads it if its there, otherwise displays an error message.

I want to extend it so that if the file isnt found, it then looks in another directory, and then if its not found an error message is displayed.

Any help would be appreciated.:)

---

### Post by kast on 2007-10-23
[B]if [ ls | grep file > /dev/null ] then
   
    echo "File not in directory"
    cd /newdirectory

else
if [ ls | grep secondfile > /dev/null ] then
   
   echo "wrong again!"
  
 fi
fi
[/B]

---

### Post by kaamos on 2007-10-23
```

if [ -a "$THEFILE" ]; then
    cat "$THEFILE"
else 
    if [ -a "$OTHERDIR/$THEFILE" ]; then
        cat "$OTHERDIR/$THEFILE"
    else
        echo "$YOURERROR"
    fi
fi

```

---

### Post by kast on 2007-10-23
I apologize in advance if the syntax is off, i don't have access to a Shell right now to test it.

---

### Post by kast on 2007-10-23
Oh much better way kaamos  thanks

---

### Post by Mbengi Bongi on 2007-10-23
I should have mentioned my current if statement, which finds and executes an existing shell script if its found:

[B]read FILE 
FILE=${FILE}".sh" 
if [ -f ${FILE} ]; then 
    ./${FILE} 
else
    echo "File not found." 

[/B]

How do I integrate what you have just writen Kast/Kaamos?

---

### Post by ghostdog74 on 2007-10-23
you can use find command
```

read FILE 
find /startingpath -type f -name $FILE -exec yourscript.sh {} \;

```

---

