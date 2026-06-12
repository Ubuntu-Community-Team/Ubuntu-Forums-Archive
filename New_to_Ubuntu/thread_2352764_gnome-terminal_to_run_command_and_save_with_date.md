---
title: "gnome-terminal to run command and save with date"
date: 2017-02-15
forum: New to Ubuntu
---

### Post by vineshv on 2017-02-15
I am trying to open multiple gnome-terminal terminal, execute some command in each terminal and save the log for each terminals with current date and time. Kindly suggest a solution.

gnome-terminal -x bash -c "script log.txt | tee log; date;"

---

### Post by sisco311 on 2017-02-15
Hi, vineshv and welcome to the forums!

Thread moved to "New to Ubuntu"


Do you want to append the date to the file name of the log file?
```
some command | tee "log file $(date)"
```

Or you want to add the date to the content of the log file? In which case the easiest option would be to modify the script which creates the log.

---

### Post by vineshv on 2017-02-15
I tried with the following options but it's not working.

gnome-terminal -x bash -c "script log.txt | tee log.txt; $date;"
gnome-terminal -x bash -c "script log.txt | tee log.txt; $(date);"
gnome-terminal -x bash -c "script log.txt | tee log.txt; $(date)"
gnome-terminal -x bash -c "script log.txt | tee log.txt $(date)"
gnome-terminal -x bash -c "script log.txt" | tee "log.txt $(date)"

---

### Post by vineshv on 2017-02-16
waiting for the resolution....

---

### Post by wildmanne39 on 2017-02-16
Please be patient you can only bump your thread once every twelve hours.

---

### Post by vasa1 on 2017-02-16
How does```
"$(date +%Y%m%d%H%M%S)"log.txt
```work for you?

---

### Post by vineshv on 2017-02-16
Tried all the options but no success...

gnome-terminal -x bash -c "$(date +%Y%m%d%H%M%S)"log.txt
Illegal variable name.

gnome-terminal -x bash -c "(date +%Y%m%d%H%M%S)"log.txt

gnome-terminal -x bash -c "(date +%Y%m%d%H%M%S)log.txt"

gnome-terminal -x bash -c "$(date +%Y%m%d%H%M%S)log.txt"
Illegal variable name.

I have requirement like...to open a new 'gnome-terminal'. And as soon as new terminal is opened, it starts capturing everything typed in new terminal and store in log file with starting date with time.

---

### Post by vasa1 on 2017-02-16
Have you looked at *man script*?```
DESCRIPTION
       script makes a typescript of everything displayed on your terminal.  It is
       useful for students who need a hardcopy record of an  interactive  session
       as proof of an assignment, as the typescript file can be printed out later
       with lpr(1).

       If the argument file is given, script saves the dialogue in this file.  If
       no filename is given, the dialogue is saved in the file typescript.

```

---

### Post by vineshv on 2017-02-16
Is there any option to start new gnome-terminal and save its log into a file with date and time...(date and time are mandatory)

---

### Post by Keith_Helms on 2017-02-16
Here's an example of writing the output from a command to a file with date as part of the name:
```

today=`date +"%Y%m%d"`
somecommand > /home/myid/outputfile_$today.txt

```

---

### Post by Habitual on 2017-02-16
> **vineshv said:**
> Tried all the options but no success...

```
gnome-terminal -x bash -c "$(date +%Y%m%d%H%M%S)"log.txt
Illegal variable name.

gnome-terminal -x bash -c "(date +%Y%m%d%H%M%S)"log.txt

gnome-terminal -x bash -c "(date +%Y%m%d%H%M%S)log.txt"

gnome-terminal -x bash -c "$(date +%Y%m%d%H%M%S)log.txt"
Illegal variable name.
```


Quotes aren't necessary to $(shell_out) so try one of these:
```
gnome-terminal -x bash -c $(date +"%Y%m%d%H%M%S")log.txt
gnome-terminal -x bash -c $(date +"%Y%m%d%H%M%S")log.txt
gnome-terminal -x bash -c $(date +"%Y%m%d%H%M%S")log.txt
gnome-terminal -x bash -c $(date +%Y%m%d%H%M%S")log.txt
```

and you can test with 
```
echo $(date +"%Y%m%d%H%M%S")log.txt
```
The "+" sign and the quotes... The quotes can be in front of the + sign or as shown.
and see [https://help.ubuntu.com/community/Links](https://help.ubuntu.com/community/Links) for some valuable resources.

---

### Post by vineshv on 2017-02-16
date should be printed inside the log file

---

### Post by Habitual on 2017-02-17
> **vineshv said:**
> date should be printed inside the log file
Sorry, I didn't realize you wanted someone to write it too ;)
Please remember, we are volunteers, Thank You.

Please try
```
gnome-terminal -x bash -c $(echo $(date) > $(date +"%Y%m%d%H%M%S")log.txt)
```


Testing:
```
$(echo $(date) > $(date +"%Y%m%d%H%M%S")log.txt)
```makes ```
 20170217064617log.txt
```
and has this content:
```
 Fri Feb 17 06:46:17 EST 2017
``` Yours will be ***similar***.

---

### Post by vineshv on 2017-02-20
i am not looking to include the date in log file name. i am looking to print date inside the log file.

---

### Post by Habitual on 2017-02-20
> **vineshv said:**
> i am not looking to include the date in log file name. i am looking to print date inside the log file.

[http://www.tldp.org/LDP/abs/html/io-redirection.html](http://www.tldp.org/LDP/abs/html/io-redirection.html)

---

