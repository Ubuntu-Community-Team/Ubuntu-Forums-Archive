---
title: "upgrade gcc to 4.2"
date: 2008-04-11
forum: Programming Talk
---

### Post by leg on 2008-04-11
How do I safely upgrade my version of gcc from 4.1.3 that I have to 4.2. I have gone into synaptic and installed the 4.2 versions but my system is still using the 4.1 version. What do I do to tell my system to use the 4.2 version of gcc.

---

### Post by arkangel on 2008-04-11
you can  have both   whihc is always good idea 

download  the  version of gcc you want  and follow the instructions

when run configure  specify the  path you want to install 

%sources_to_GCC/configure  --prefix=/opt/gcc_4.2   --Otheor options
%make 
%sudo make install 

for building gcc you need to do it from another directory(sources_to_GCC) , just read the README /INSTALL  file 

the prefix tells to the script  where to install , it can be any subdirectory (for outside your home  you need to use root or sudo permissions)


then to use it  simple modifiy the PATH and LD_LIBRARY_PATH  env. variables

%export PATH=/opt/gcc_4.2/bin:$PATH 
alternatively 
%export PATH=wherever_you_install_gcc/bin:$PATH 

and 

%export LD_LIBRARY_PATH=/opt/gcc_4.2/lib:$LD_LIBRARY_PATH 
alternatively 
%export LD_LIBRARY_PATH=wherever_you_install_gcc/lib:$LD_LIBRARY_PATH


If  all is OK 

% gcc -v  

to check which version ..


you can also  look for precompiled version (i think there is for i32, x64, etc)  then you copy the directories where you want and you only have to do the PATH and LD_LIBRARY_PATH stuff

---

### Post by leg on 2008-04-11
So if I have already installed the 4.2 version from synaptic do I just need to do the path bits and I can then use gcc 4.2?

---

### Post by Jessehk on 2008-04-11
I'm an Arch Linux user, so I  hope that I remember this right.

Enter the following command with root privileges (ie, sudo):
```

update-alternatives --config gcc

```

update-alternatives is a Debian tool that allows you to choose which version of a specific program or service you want to use. You should see a list of different installed gcc versions and you'll be able to select the one you want. Paths should be updated apropriately.

---

### Post by arkangel on 2008-04-11
> **leg said:**
> So if I have already installed the 4.2 version from synaptic do I just need to do the path bits and I can then use gcc 4.2?

yes   ,  for every bash session you open

---

### Post by lnostdal on 2008-04-11
> **leg said:**
> So if I have already installed the 4.2 version from synaptic do I just need to do the path bits and I can then use gcc 4.2?


go down the other path instead .. the one Jessehk mentions ...

---

### Post by leg on 2008-04-11
> **Jessehk said:**
> I'm an Arch Linux user, so I  hope that I remember this right.

Enter the following command with root privileges (ie, sudo):
```

update-alternatives --config gcc

```

update-alternatives is a Debian tool that allows you to choose which version of a specific program or service you want to use. You should see a list of different installed gcc versions and you'll be able to select the one you want. Paths should be updated apropriately.Except that I already tried that and it tells me that there are no alternatives for gcc so I must have done something wrong. Any idea what I could have wrong. Is there a howto for this anywhere I wonder.

---

