---
title: "Parsing command line options in C"
date: 2007-06-26
forum: Programming Talk
---

### Post by WebDrake on 2007-06-26
Can anyone recommend a C library to use for parsing command line options?

I imagine there are several out there so any comparison, discussion or general advice on the topic would be welcome.

Thanks in advance for any replies.

---

### Post by bunker on 2007-06-26
[getopt()](http://www.gnu.org/software/libc/manual/html_node/Getopt.html)

---

### Post by WebDrake on 2007-06-26
> **bunker said:**
> [getopt()](http://www.gnu.org/software/libc/manual/html_node/Getopt.html)
Looks great!  Thank you very much. :)

---

### Post by moma on 2007-06-26
Hello,

He is a small getopt() sample with short (-x) and long (--xxxx) options.
[http://www.futuredesktop.org/tmp/getopt_test.c](http://www.futuredesktop.org/tmp/getopt_test.c)

Compile it:
$[COLOR="SeaGreen"] gcc  -Wall getopt_test.c -o getopt_test[/COLOR]

Run it
$ [COLOR="SeaGreen"]./getopt_test -h [/COLOR]
$ [COLOR="SeaGreen"]./getopt_test --help [/COLOR]
$ [COLOR="SeaGreen"]./getopt_test  -u pekka --password=abc [/COLOR]
---------

ps. I think the example is from "Advanced Linux Programming" book. It's freely available in pdf format. 
Check this great resource: [http://www.futuredesktop.org/opportunities.html](http://www.futuredesktop.org/opportunities.html)  The link is there.

---

