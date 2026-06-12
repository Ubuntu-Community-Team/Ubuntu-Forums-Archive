---
title: "Setting environment variable path"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by oli.kerr on 2011-12-08
I am trying to compile an mfix subroutine using Intel fotran. Once selected to compile, the follow error shows:

[PHP]make -f mfix_l_not.make compare.o eosg.o discretize.o 
ifort   -c -I. -w -w95 -i_dynamic -ip -convert big_endian -assume byterecl -FR -O3 -axKW -tpp7    param_mod.f 
make: ifort: Command not found
make: *** [param.mod] Error 127

Please wait . . .
make -f mfix_l_not.make mfix.exe
ifort   -c -I. -w -w95 -i_dynamic -ip -convert big_endian -assume byterecl -FR -O3 -axKW -tpp7   param_mod.f 
make: ifort: Command not found
make: *** [param.mod] Error 127[/PHP]

I therefore assumed I must set an environment variable path. This is the code I put into my bashrc file:

[PHP]export PATH="~/opt/intel/composer_xe_2011_sp1.7.256/bin/ia32/ifort": ${PATH}[/PHP]

As the original ifort executable is found here (there are 3/4 more shortcut versions scattered around other folders that link to this file). Can someone identify what is wrong with my code?

Thanks in advance,
Oli

---

