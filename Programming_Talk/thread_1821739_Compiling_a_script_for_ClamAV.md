---
title: "Compiling a script for ClamAV"
date: 2011-08-09
forum: Programming Talk
---

### Post by geoff13 on 2011-08-09
Hey all,

I'm pretty new to ubuntu (currently running Ubuntu 11.04) and just installed clamav antivirus...

What is the best way to configure ubuntu to run automatically every day, scan all files and directories, and then print infected files to a file and my email?

can i use $ at [time] (day)   ...? or is it better to edit the conf file?

no experience with scripting or anything like that. any info is appreciated

---

### Post by geoff13 on 2011-08-09
what i pretty much want a scrip to say is

run freshclam  //update virus definitions

when freshclam is complete    
   {                          **after update run scan
    run clamscan
       
        if infectedFiles > 1  **if infected files are found...
           {
            print infected files  **print those files

            on user input: sudo clamscan -r --remove /
          
            else exit                     **remove file or exit
           }
   }

---

### Post by SoFl W on 2011-08-09
See this thread:
[http://ubuntuforums.org/showthread.php?t=631293](http://ubuntuforums.org/showthread.php?t=631293)

---

### Post by geoff13 on 2011-08-09
thanks very much!

also found this...

[http://www.tldp.org/LDP/abs/html/]("http://www.tldp.org/LDP/abs/html/")

solved!

---

### Post by geoff13 on 2011-08-09
will post my script and a walkthrough when finished

---

