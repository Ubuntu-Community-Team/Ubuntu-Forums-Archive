---
title: "Is my script executing?"
date: 2014-01-21
forum: Programming Talk
---

### Post by bob-schaffstein on 2014-01-21
**How can I tell if my script is executing?**

 
 When I wake my computer from sleep or suspend mode it does not automatically connect to the internet.  I was advised to write a script and place it in the [FONT=arial]*/etc/pm/sleep.d/ directory*[/FONT].  I have written the script *rosewill.sh* as shown below, placed it in the */etc/pm/sleep.d/* directory, and given it execute permission with* sudo chmod a+x*.  But the computer still does not connect automatically.   

  Here is the script:


 #/bin/bash
 #
 #script to connect Rosewill to mifi
 #
 echo "Rosewill shell script is starting"
 echo "Variable recieved is: " $1
 echo "Case sequence is starting"
 case "$1" in
    thaw)
         sudo modprobe -r r8712u; echo "removed"; sleep 3; sudo modprobe r8712u

         ;;

 esac
echo "Rosewill script is complete"

 

Additional note: To test the command I have typed into a terminal the line
           *sudo modprobe -r r8712u; echo "removed"; sleep 3; sudo modprobe r8712u*
and the computer will connect, but it takes about 80 to 90 seconds to connect.

---

### Post by Dave_L on 2014-01-21
I think the parameter value should be  "resume", not "thaw".

Also, the first line should be:

```
#!/bin/bash
```

You left out the "!".

For testing purposes, you could add the following to the script after the #! line:

```
LOG='/tmp/resume_script.log'
date >>"$LOG"
echo "$0" "$1" >>"$LOG"
```

You could direct your other echo's to the log file too.

Also, when posting code, it's helpful to use the [ code ] ... [ /code ] tags (without the spaces). It makes the code easier to read.

---

