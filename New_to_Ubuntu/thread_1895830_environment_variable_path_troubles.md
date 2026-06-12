---
title: "environment variable path troubles"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by oli.kerr on 2011-12-15
Dear all,

I am compiling a subroutine using intel fortran, and when I try to execute the file the error message is shown as follows:

[PHP]make -f mfix_l_not.make compare.o eosg.o discretize.o 
ifort   -c -I. -w -w95 -i_dynamic -ip -convert big_endian -assume byterecl -FR -O3 -axKW -tpp7    param_mod.f 
make: ifort: Command not found
make: *** [param.mod] Error 127

Please wait . . .
make -f mfix_l_not.make mfix.exe
ifort   -c -I. -w -w95 -i_dynamic -ip -convert big_endian -assume byterecl -FR -O3 -axKW -tpp7   param_mod.f 
make: ifort: Command not found
make: *** [param.mod] Error 127[/PHP]

This can be avoided by using the following code:

> source /home/oli/intel/composer_xe_2011_sp1.7.256/bin/compilrevars.sh ia32

However, I would like to set up a permanent environment path, as I have to bash in this code every time I want to compile!

Thanks in advance,
Oli

---

### Post by matt_symes on 2011-12-17
Hi

Have you considered adding it to .bashrc in your home folder ?

It will then get sourced every time you open a terminal.

You could also set up an alias for it if you wanted to do that instead. That can also be placed in your .bashrc file.

Kind regards

---

### Post by oli.kerr on 2012-01-17
Please excuse my lack of knowledge, but where exactly do I enter this in my bashrc file? and is there any amends I need to make to the code?

---

### Post by yetiman64 on 2012-01-17
At the very end of the .bashrc file try adding a new line with the code,

```
export PATH=$PATH:$HOME/intel/composer_xe_2011_sp1.7.256/bin
```Close any open instances of terminal you are running the script from, or open a new terminal, and try the previous task that was failing. Also after changing the .bashrc file, another way to check the folder is in the system PATH is with the code,
```
echo $PATH
```Regards, yetiman64.

---

### Post by Raff1 on 2012-01-17
I would rather use the command intel is suggesting. (It actually adds two different folders to path afaik.)

Go to your home directory, press Ctrl+H to show hidden files, and open the file .bashrc with gedit. Now add this to the end of the file and save it:

```
#Adding ifort to path for every terminal session
source /home/oli/intel/composer_xe_2011_sp1.7.256/bin/compilrevars.sh ia32                      
```Now you won't have to do it every time you open a terminal :-)

---

### Post by yetiman64 on 2012-01-17
Ah, yes OP, go with the intel command directly in the as Raff1 suggests. I seem to have misread/misunderstood your needs (now I have reread the thread) and wrongly suggested adding the script folder to the system path to access the command directly in terminal, sorry.

---

