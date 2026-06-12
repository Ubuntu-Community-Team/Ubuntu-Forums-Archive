---
title: "use of source command in .bashrc"
date: 2012-03-29
forum: Programming Talk
---

### Post by matteo-carli on 2012-03-29
Hi guys

I am doing some computational stuff using intel compiler and
open foam (CFD)

Following Intel instructions, I added the following line at the
end of the .bashrc :

source /opt/intel/composerxe-2011.4.191/bin/compilervars.sh ia32 

compiler is working properly (i.e. using icc command from the command line)

Recently, I have installed open foam program, which require the following line at the end of the .bashrc : 

source /opt/openfoam210/etc/bashrc

Problem is that now the icc command does not work any more (Open Foam does).

The end of my .bashrc file looks this way:

source /opt/intel/composerxe-2011.4.191/bin/compilervars.sh ia32 
source /opt/openfoam210/etc/bashrc

If I copy and paste the first source command in the shell the icc command is working

Am I using the source command in the wrong way? Maybe is the second source "erasing" the first one?

---

### Post by Habitual on 2012-03-29
Did you ```
source ~/.bashrc
``` after editing/saving?

---

### Post by Bachstelze on 2012-03-29
> **matteo-carli said:**
>  Maybe is the second source "erasing" the first one?

That's probably what happens, yes. I suspect the second script is setting your PATH variable regardless of what is previously there. Can you post the script, or at least any line containing "PATH"?

---

### Post by ofnuts on 2012-03-30
> **Bachstelze said:**
> That's probably what happens, yes. I suspect the second script is setting your PATH variable regardless of what is previously there. Can you post the script, or at least any line containing "PATH"?
I wouldn't bet on PATH, most scripts tend to add things to it instead of bluntly replacing it, but the use of "source" indeed hints at some environment variable being overwritten.

---

### Post by djerlo on 2013-02-07
Hi all,

Has anyone found a solution to this problem?

Thanks!

---

