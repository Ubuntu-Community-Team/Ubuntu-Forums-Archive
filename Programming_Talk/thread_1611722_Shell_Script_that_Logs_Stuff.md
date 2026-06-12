---
title: "Shell Script that Logs Stuff"
date: 2010-11-02
forum: Programming Talk
---

### Post by CrusaderAD on 2010-11-02
I built a shell script that fetches a file via ftp, then appends a line to a text file logging it. I have a feeling it would write the line regardless of the success of the previous command. How do I write it so I can get some more details? Write one line if successful, another line if it fails? Is that possible?

---

### Post by DaithiF on 2010-11-02
something like:
```
somecommand
[[ $? -eq 0 ]] && echo "It worked" || echo "It failed"

```

---

### Post by epicoder on 2010-11-02
EDIT: Looks like someone beat me to it, but I'll just leave mine here. :P

There is a variable, $?, which is the exit status of the previous command. Most programs exit with a status of 0 on success, so you could add something like this immediately after the ftp get command: 
```
if [ "$?" == "0" ]
then
  echo "Success"
else
  echo "Failure"
fi
```

---

### Post by CrusaderAD on 2010-11-02
Excellent! I'll give these a shot and post my results. Thanks!

---

### Post by CrusaderAD on 2010-11-02
I tried both recommdations. With this shell script:

> #!/bin/sh
ping -c 2 downloads.com
if [ "$?" == "0" ]
then
  echo "Success"
else
  echo "Failure"
fi
>> /home/user/pingtest.log


I get this message: 

> 2 packets transmitted, 2 received, 0% packet loss, time 5041ms
rtt min/avg/max/mdev = 24.000/24.433/24.866/0.433 ms
[: 8: 0: unexpected operator
Failure

With Daith's solution, I get this:

> 2 packets transmitted, 2 received, 0% packet loss, time 5058ms
rtt min/avg/max/mdev = 21.859/33.293/44.728/11.435 ms
/bin/pingtest: 3: [[: not found


Any ideas?

---

### Post by DaithiF on 2010-11-02
you're running it under the dash shell rather than bash.

ssh228's solution fails under dash because == is not a supported comparison operator for the [ test command in dash and mine fails because [[ is a bash construct only, it doesn't exist in dash.

make things easier on yourself and use #!/bin/bash as your shebang.

---

### Post by epicoder on 2010-11-02
My tendency to use "==" instead of "=" comes from my days of using python and php. :P "=" works in both bash and sh, so you should use that instead.
```
if [ "$?" = "0" ]
then
  echo "Success"
else
  echo "Failure"
fi
```

---

### Post by CrusaderAD on 2010-11-02
Awesome! It works great, thanks! I don't suppose either of you knows how to append the line to the top of the text file when I do this?

> >> /home/user/pingtest.log

Rather than it appending to the bottom?

---

### Post by DaithiF on 2010-11-02
> **CerealCypher said:**
> I don't suppose either of you knows how to append the line to the top of the text file when I do this?
Rather than it appending to the bottom?
Thats usually not a good idea ... log files almost always grow from the bottom.  May I ask why you want to add it to the top?  Usually you can achieve what you want using tools like tail or tac without changing the order the file is written.

---

### Post by CrusaderAD on 2010-11-02
I just want to read the latest line first without having to scroll down. Is there another way to achieve this?

---

### Post by DaithiF on 2010-11-02
```
tail -1 thefile
```

also very useful is:
```
tail -f thefile
```
which watches the file continuously (-f means 'follow') and outputs any changes as the happne.

---

### Post by epicoder on 2010-11-02
Using sed, you can prepend lines to a file by using an insert command restricted to the first line. Say the text I want to prepend is in variable $text:
```
sed -i "1 i$text" logfile.txt
```
Note that the i command in sed automatically adds a newline, so don't put one in the variable.

---

### Post by CrusaderAD on 2010-11-04
Both work great. I ended up using tail. Thanks for all the help guys!

---

