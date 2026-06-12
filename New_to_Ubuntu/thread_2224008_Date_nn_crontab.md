---
title: "Date nn crontab"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by piros2 on 2014-05-14
Hi all,

I'm new to Linux and I'm trying to do some script.
In particular, a part of that script is the following one:

           #!/usr/bin/bash        
           DATA="$(date +\%Y-%m-%d)"
[COLOR=#ff0000]           date +%Y-%m-%d --date=" 90 days ago" >> input_list.txt[/COLOR]

My problem is that the highlighted line is not recognized on crontab.
What is the problem? How can i obtain the same result modifing the script?

Thank you all.

Piros

---

### Post by HiImTye on 2014-05-14
are you trying to put that line directly into crontab, or are you trying to have crontab run that script?
did you check for the existence of input_list.txt in the home folder of the crontab user?

---

### Post by Lars Noodén on 2014-05-14
Usually bash is found in /bin/bash on Ubuntu.  So the first line might be wrong.  Check with [which](http://manpages.ubuntu.com/manpages/trusty/en/man1/which.1.html)

```

which bash

```

Then about the last line, paths and environment variables can be different in cron's environment.  So, you probably want to provide the full path to the destination file just to be sure it's going where you want it to.  

```

date +%Y-%m-%d --date=" 90 days ago" >> /home/piros2/input_list.txt

```

---

### Post by piros2 on 2014-05-14
> **Lars Noodén said:**
> Usually bash is found in /bin/bash on Ubuntu.  So the first line might be wrong.  Check with [which]("http://manpages.ubuntu.com/manpages/trusty/en/man1/which.1.html")

```

which bash

```

Then about the last line, paths and environment variables can be different in cron's environment.  So, you probably want to provide the full path to the destination file just to be sure it's going where you want it to.  

```

date +%Y-%m-%d --date=" 10 days ago" >> /home/piros2/input_list.txt

```

Hi,

thank you for your answer.
The script (script.sh) is executed from crontab:

[COLOR=#000000]                54 11 * * * /home/piros2/script.sh[/COLOR]


 
However, i forgot to specify the full path of input_list.txt, and i've tryed to change the envirorment:

            #!/usr/local/bin/bash
            path_s="/home/piros2/"
            input_list=$path_s"input_list.txt"
            date +%Y-%m-%d --date=" 10 days ago" >> $input_list




The result is that, input_list.txt cointains the current date, so [COLOR=#ff0000]2014-05-14[/COLOR]. 
I need to have the date of 10 days ago. 
Any suggestions?

Piros

---

### Post by Habitual on 2014-05-16
First, you said 90, then you said 10, use either
```
date +%Y-%m-%d --date=" 10 days ago" >> /home/piros2/input_list.txt
```
or 
```
date +%Y-%m-%d --date=" 90 days ago" >> /home/piros2/input_list.txt
``` in [COLOR=#000000] /home/piros2/script.sh[/COLOR]

---

