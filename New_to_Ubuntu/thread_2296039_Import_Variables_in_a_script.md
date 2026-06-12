---
title: "Import Variables in a script"
date: 2015-09-23
forum: New to Ubuntu
---

### Post by Danial_Rana on 2015-09-23
Hello!
I am new to ubuntu, kindly inform me is there any method in ubuntu that would allow me to import varaiables inside my script?

for example 

My first script in linux is shown below, now what i want to do is to import the values of v1,v2 and v3 rather than assigning the values for them myself.

  
```
#!/bin/bash
# First Script
clear
v1=40
v2=60
v3=80
echo 'Uploading in process!'
echo -e "engine oil pressure= $v1 \n " > sample.txt
echo -e "engine coolent temperature= $v2 \n" >> sample.txt
echo -e "engine coolent level= $v3 \n" >> sample.txt
curl -T sample.txt [ftp://ftp.byethost32.com/htdocs/](ftp://ftp.byethost32.com/htdocs/) --user b32_16683736:Allahis1
echo 'uploading completed'
```


Looking forward to hear from all of you.
Have a good day

---

### Post by Lars Noodén on 2015-09-23
Before running your script you have to mark the variable for '[export](http://manpages.ubuntu.com/manpages/trusty/en/man1/bash.1.html)'  to make them available to programs and scripts launched from that environment.  

```

v1=40;
export v1;
./myscript

```

or

```

export v1=40;
./myscript

```

The export only has to be done once, though, and then the variable will be placed in the environment exported to any following programs or scripts.

Another way would be to specify the variables explicitly each time the script gets run.

```

v1=40 v2=60 v3=80 ./myscript

```

---

### Post by Lars Noodén on 2015-09-23
PS.  the script above was readable but would be more so with the help of [****code] and [/****code] before and after

---

### Post by Danial_Rana on 2015-09-23
Dear Mr. Nooden!
  thank you for your abrupt and complete reply.

p.s i would now remember to insert ```
 and 
```

---

