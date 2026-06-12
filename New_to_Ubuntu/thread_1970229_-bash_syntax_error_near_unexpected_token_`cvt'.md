---
title: "-bash: syntax error near unexpected token `cvt'"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by AmirJamez on 2012-04-30
Hi Guys,

I am trying to install the R package with Psych to do some statistical analysis, but as I read [http://personality-project.org/r/book/overview.pdf](http://personality-project.org/r/book/overview.pdf)  page 4, the syntax doesn't work on the Ubuntu 10.04. I am trying to execute :

install.packages("ctv")
library(ctv)
task.views("Psychometrics")

but the system keeps saying :

-bash: syntax error near unexpected token `cvt'

Any ideas ?

Thanks,

Amir

---

### Post by jtarin on 2012-04-30
the command uses "ctv" not 'cvt'. Make sure you entered the command correctly.

---

### Post by steeldriver on 2012-05-01
sounds like you are trying to execute these directly in a terminal / bash shell, whereas what it is asking you to do is start R in the terminal, and then run those commands within R?

See this snip from the R user manual - try entering your commands at step 3 when you see the R prompt (>)

> In using R under UNIX the suggested procedure for the first occasion is as follows:       

1. Create a separate sub-directory, say work, to hold data files on which you will use R for this problem.  This will be the working directory whenever you use R for this particular problem. 

$ mkdir work           
$ cd work

2. Start the R program with the command                 
$ R

3. At this point R commands may be issued (see later). 

4. To quit the R program the command is                 
> q()


---

### Post by AmirJamez on 2012-05-01
Thanks for all replies.

Yes, but in this case I have to install each package one by one ? why task.views("Psychometrics") doesn't work which is said to install all packages automatically ?

Thanks 

Amir



> **steeldriver said:**
> sounds like you are trying to execute these directly in a terminal / bash shell, whereas what it is asking you to do is start R in the terminal, and then run those commands within R?

See this snip from the R user manual - try entering your commands at step 3 when you see the R prompt (>)

---

