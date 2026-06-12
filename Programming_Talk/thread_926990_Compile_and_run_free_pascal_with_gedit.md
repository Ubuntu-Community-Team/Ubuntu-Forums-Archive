---
title: "Compile and run free pascal with gedit ?"
date: 2008-09-22
forum: Programming Talk
---

### Post by BXCracer on 2008-09-22
Hi.
I am trying to use Gedit to compile and run that program in terminal using the external tools plugin, there is already a tool to build C programs, how do i modify it to build pascal using fpc ? And other tool i need is that gedit run that program that was just compiled in terminal.

BXC

---

### Post by cmay on 2008-09-23
i read your post last night. i tried to see what options there where.
 the first thing is if it is a merely question about compile and run pascal code from within the IDE then  you can use geany since it has these two features to begin with. the other is that if you know how to use zenity as some of the tools in gedit also uses then i assume one can just make a script that does these two things. i have no idea as of how to do that. but i am very happy that you posted since i did not know of the zenity package before. so i was very exited to find out about it.even that i did not come up with any real solution i decided to post this anyway to let you know someone found out somethings he did not know about before.and if in case you find a solution i would be very happy to learn about as well since i sometimes also would like  to use gedit for pascal or perl .
thanks for the post and good luck to you.

---

### Post by BXCracer on 2008-09-23
Thanks for your reply cmay.
With my basic scripting knowledge i managed to wrote two scripts, that can build and run programs written in pascal with gedit external tools plug

build 
```

#!/bin/sh
cd $GEDIT_CURRENT_DOCUMENT_DIR
fpc ${GEDIT_CURRENT_DOCUMENT_NAME%\.pas}
```

Build and run
```
#!/bin/bash
FILE_NAME=$GEDIT_CURRENT_DOCUMENT_NAME
if [ `echo $FILE_NAME | cut -d "." -f 2` = "pas" ] 
then
FILE_NAME_LEN=`expr ${#FILE_NAME} - 4`
FILE_NAME_BASE=${FILE_NAME:0:$FILE_NAME_LEN}
if fpc $GEDIT_CURRENT_DOCUMENT_NAME | awk '$1 > 0 && /compiled/ && /sec/{print "ok"}' | grep ok > /dev/null
then
# Check if file extension is .pas
gnome-terminal -e ./$FILE_NAME_BASE
else
fpc $GEDIT_CURRENT_DOCUMENT_NAME
fi
fi
exit 0
```

Build and run script updated. Now it check if source was compiled successfully and if yes then it starts newly compiled program in terminal. And if there was an error while compiling it shows you an error. Sure /dev/null part may look lame but it works :D

Thanks to ghostdog74 for help.

---

### Post by cmay on 2008-09-23
thank you for sharing this. i was up the whole nigth trying to figure something like that out but i have zero skills at bash scripting so it did not work . but i also  found i could call zenity as one of the tools in gedit uses from perl so when i figure out how to use it in perl scripts i am certain it would become handy in the future. so thanks for your post and thanks for posting the solution you came up with.

---

### Post by Sunga on 2008-11-25
hey

first, thanks for that script its gonna help me a lot :)

but a i got a problem, compiling is fine but when i compile and run in a console, the terminal close automatically and i can't see the results of the program, do you know how to avoid that ?

(sorry my English is not perfect)

---

