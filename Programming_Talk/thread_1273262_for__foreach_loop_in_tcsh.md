---
title: "for / foreach loop in tcsh?"
date: 2009-09-23
forum: Programming Talk
---

### Post by aytacd on 2009-09-23
Hello to all,

I have a for loop for accesing files in a folder, convert them into another format (.mgz) and save them into another folder. 

So here are the algorithmic steps: 

Read a list of files in a folder. 
Convert file extensions with (.mgz)
save files into a different folder.
 

here is the code that i used in bash script:
```
#!/bin/bash

cd /usr/local/freesurfer/subjects/$1/data_temp

temp=1;

for i in $(ls); do
mri_convert $i 00$temp.mgz
let temp=temp+1;
done
```



i have to write this in tcsh after hours of googling what i have found is the insufficient documentation about foreach command:

```

#!/bin/bash

cd /usr/local/freesurfer/subjects/$1/data_temp

set count=1

foreach i ( ` /usr/local/freesurfer/subjects/$1/data_temp * ` )

foreach? echo $i

foreach? do mri_convert $i /usr/local/freesurfer/subjects/$1/mri/orig/00$count.mgz

foreach? let count=count+1

foreach? done

 

```

final errors that we are taking are: 

/usr/local/freesurfer/subjects/rhsr/data_temp: Permission denied.
foreach: end not found. 

any help??

---

### Post by Arndt on 2009-09-23
> **aytacd said:**
> Hello to all,

I have a for loop for accesing files in a folder, convert them into another format (.mgz) and save them into another folder. 

So here are the algorithmic steps: 

Read a list of files in a folder. 
Convert file extensions with (.mgz)
save files into a different folder.
 

here is the code that i used in bash script:
```
#!/bin/bash

cd /usr/local/freesurfer/subjects/$1/data_temp

temp=1;

for i in $(ls); do
mri_convert $i 00$temp.mgz
let temp=temp+1;
done
```



i have to write this in tcsh after hours of googling what i have found is the insufficient documentation about foreach command:

```

#!/bin/bash

cd /usr/local/freesurfer/subjects/$1/data_temp

set count=1

foreach i ( ` /usr/local/freesurfer/subjects/$1/data_temp * ` )

foreach? echo $i

foreach? do mri_convert $i /usr/local/freesurfer/subjects/$1/mri/orig/00$count.mgz

foreach? let count=count+1

foreach? done

 

```

final errors that we are taking are: 

/usr/local/freesurfer/subjects/rhsr/data_temp: Permission denied.
foreach: end not found. 

any help??

After seconds of googling, I found the man page for tcsh, and the section about 'foreach' leads me to believe tcsh means it when it says "foreach: end not found".

---

### Post by aytacd on 2009-09-24
> **Arndt said:**
> After seconds of googling, I found the man page for tcsh, and the section about 'foreach' leads me to believe tcsh means it when it says "foreach: end not found".


meaning?

i need a solution and i cannot find anything sufficient? 
Can you guide me to somewhere a link or a command line?

---

### Post by Arndt on 2009-09-24
> **aytacd said:**
> meaning?

i need a solution and i cannot find anything sufficient? 
Can you guide me to somewhere a link or a command line?

I don't understand how you could google for hours without encountering the documentation for tcsh. Google again, for "documentation tcsh". You will find what is called a "manual page". In it, look for "foreach".

---

### Post by aytacd on 2009-09-25
> **Arndt said:**
> I don't understand how you could google for hours without encountering the documentation for tcsh. Google again, for "documentation tcsh". You will find what is called a "manual page". In it, look for "foreach".

i tried several ways to make this algorithm work. But couldn't find a working solution, including your "manual page". So i'm trying to use this forum for help. But all you doing is: critisim. I don't need that, i need a direction for my algorithm. If you're not helping i prefer not to write anything at all..

---

### Post by Arndt on 2009-09-25
> **aytacd said:**
> i tried several ways to make this algorithm work. But couldn't find a working solution, including your "manual page". So i'm trying to use this forum for help. But all you doing is: critisim. I don't need that, i need a direction for my algorithm. If you're not helping i prefer not to write anything at all..

Yes, it's criticism. It's also telling you what to do.

1) Did you do what I suggested? 2) Did you find the manual page? 3) Did you find the section about 'foreach'? 4) Did you compare what it says with what you have written?

At which step did you fail? That's where we can begin helping you.

---

### Post by aytacd on 2009-09-25
if you want to help you could easily copy the link to this thread but you still prefer not to. 
I solve my problems finally. 
Can somebody lock this Thread!

> **Arndt said:**
> Yes, it's criticism. It's also telling you what to do.

1) Did you do what I suggested? 2) Did you find the manual page? 3) Did you find the section about 'foreach'? 4) Did you compare what it says with what you have written?

At which step did you fail? That's where we can begin helping you.

---

### Post by Arndt on 2009-09-25
> **aytacd said:**
> if you want to help you could easily copy the link to this thread but you still prefer not to. 
I solve my problems finally. 
Can somebody lock this Thread!

So where did you find the information, if not where I pointed? That may be useful to know for others in the future.

---

### Post by aytacd on 2009-10-07
go and ask someone personally! 


> **Arndt said:**
> So where did you find the information, if not where I pointed? That may be useful to know for others in the future.

---

### Post by cebi000 on 2009-11-11
You use
#!/bin/bash
in your tcsh code, so maybe you accidentally try to run it with bash?

(Hello Ubuntu community! 1st post here :) )

---

### Post by aregjan on 2010-03-26
aytacd, I believe Arndt's point is this -- if you are gonna try Linux, you might as well learn its main principle: rtfm (google that:) ).

---

### Post by superarthur on 2010-03-26
I thought the Ubuntu community gave people an impression that is friendlier than other Linux community and won't ask people to rtfm. Maybe I am wrong.

---

### Post by Ratzlaff on 2010-04-13
Since this rather useless thread is one of the top google hits for 'tcsh loops' I would direct people to this page: [http://www.csem.duke.edu/Cluster/csh_basics.htm](http://www.csem.duke.edu/Cluster/csh_basics.htm) that helped me solve my issue.

---

