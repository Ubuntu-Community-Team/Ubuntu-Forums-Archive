---
title: "Running a MATLAB script from within a shell script"
date: 2008-06-10
forum: Programming Talk
---

### Post by Bdeen on 2008-06-10
The title is self-explanatory: I want to call a MATLAB script from within a Linux shell script, and don't know exactly how.

To run some MATLAB command, something along the lines of 

matlab -nodesktop -nosplash - nojvm -r "[command];"

should work.  But when "[command];" is replaced by something of the form "Matlabscript.m", it doesn't seem to work.

Any idea how I can do this?

---

### Post by bobbocanfly on 2008-06-10
What is the error message you are getting running the command?

---

### Post by Bdeen on 2008-06-10
??? Undefined variable "RSCorrelation" or class "RSCorrelation.m".

RSCorrelation.m is the name of my script.

---

### Post by rye_ on 2008-06-10
A daft question but.....

Have you opened the terminal in the same folder as the .m files are located?

---

### Post by bobbocanfly on 2008-06-10
> **Bdeen said:**
> ??? Undefined variable "RSCorrelation" or class "RSCorrelation.m".

RSCorrelation.m is the name of my script.

That sounds more like a problem with the MATLAB script, not the shell script. Have you tried running it with a different MATLAB script and seeing if it works.

---

### Post by Bdeen on 2008-06-10
I'm running the terminal from the same folder that the Matlab script is in.  Also, the Matlab script works fine when I run it straight from the Matlab GUI, so I don't think this is the problem.

---

### Post by fedorauser_guy on 2008-10-11
I'm using fedora but the following worked for me:

matlab -nodesktop -nosplash -r "matlab_script;quit;"

Apparently you don't have to put the file extension!

Hope that solves your problem.

---

### Post by walkalot on 2009-06-10
I had the same problem, but I got rid of the quit matlab command and it worked.

---

### Post by alireza.kazemi on 2010-06-19
If you want to run a matlab script (say <thescript>.m  from within MATLAB GUI, you should hit"

>> run <the-script>.m

but if you do not use the .m extension, matlab will run the script if it can find in the path

>> <the-script>

the first style is useful when you want to run a matlab script in a different path:

>> run <the/path>/<the-script>.m


So within shell you can use above methods as follows:

matlab -nojvm -nodesktop -r "run <the-script>.m"

matlab -nojvm -nodesktop -r "<the-script>"

matlab -nojvm -nodesktop -r "run  <the/path>/<the-script>.m"

---

### Post by Roohy on 2011-03-04
It is an example to write a matlab code inside a bash script!  

#!/bin/bash
filename=mat_prog_1.m;
cat > $filename  << EOF
   % It is matlab script
   disp('Hello World')
   A=zeros(3,3);
   if size(A)==3
       disp('Hello again')
   end
EOF
chmod +x $filename
matlab -nodesktop -nosplash -nodisplay -r "run ./$filename ; quit;"

---

### Post by Nikolazigic on 2012-04-09
I have problems with my bash script,it can not see matlab:
./proba: line 3: matlab: command not found
./proba: line 4: matlab: command not found
Symbolic link exists!
How should I solve this?

#!/bin/bash

matlab -nojvm -nodesktop -r "scale1.m"
matlab -nojvm -nodesktop -r "scale2.m"

---

### Post by Vaphell on 2012-04-09
when you call 'matlab', system expects matlab executable to be located in one of the places specified in PATH variable
```
echo $PATH
```
if you have symlink to matlab in that spot you need to call it with ./matlab (current_dir/matlab) or use full path to the executable

---

### Post by Nikolazigic on 2012-04-09
/opt/intel/bin/ifortvars.sh ia32:/home/milenko/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

OK this means I should add path where?
/usr/local/MATLAB/R2011a/bin/matlab
script file for invoking matlab?
here?

---

