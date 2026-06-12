---
title: "ifort:command not found"
date: 2012-08-03
forum: Programming Talk
---

### Post by dimosaaaa on 2012-08-03
hello community !
I am very new to this forum and i don't have time to search for the exact topic to place my question if it's not here.(i am really sorry about that).
I just installed fortran 90 <l_fcompxe_intel64_2011.9.293.tgz> (i did that in user account not in the root, i don't know why). I already run a program and it works.
The problem is tha when i try ifort .... it says:: ifort:command not found.
PLEASE tell me what to do as soon as possible!!!
I have huge problem
thanks very much 
Have a good summer!!

---

### Post by Bachstelze on 2012-08-03
There is probably a README file of sorts in your archive with installation instructions. Read it.

---

### Post by dimosaaaa on 2012-08-03
> **Bachstelze said:**
> There is probably a README file of sorts in your archive with installation instructions. Read it.
there is nothing

---

### Post by Bachstelze on 2012-08-03
Then we can't really help you. Basically you need to copy the ifort executable somewhere in your PATH (typically /usr/local/bin), but it is possible that it requires other files to be copied as well. Why not just run it directly from the unarchived directory, since you said you have run it like that?

---

### Post by dimosaaaa on 2012-08-03
> **Bachstelze said:**
> Then we can't really help you. Basically you need to copy the ifort executable somewhere in your PATH (typically /usr/local/bin), but it is possible that it requires other files to be copied as well. Why not just run it directly from the unarchived directory, since you said you have run it like that?
I am searching for this file.
this happens because i have installed into the user account??

---

### Post by Bachstelze on 2012-08-03
I don't know what happens because I don't know what it is that you are trying to install. What I know is that when you want to run a command without a pathname, it must be in a directory listed in the PATH environment variable.

---

### Post by dimosaaaa on 2012-08-04
> **Bachstelze said:**
> Then we can't really help you. Basically you need to copy the ifort executable somewhere in your PATH (typically /usr/local/bin), but it is possible that it requires other files to be copied as well. Why not just run it directly from the unarchived directory, since you said you have run it like that?

i installed the fortran again this time to the root account.
Could you tell me where can i find the ifort executable and what should i do next?
thanks

---

### Post by Some Penguin on 2012-08-04
Read the man page for 'find'.

Or, of course, the man page for 'tar'; dump a file listing of the .tgz and go hunting.

---

### Post by steeldriver on 2012-08-04
I'm guessing these are the Intel compilers? there seems to be a fair bit of documentation here

[http://software.intel.com/en-us/articles/intel-compilers-linux-installation-help/](http://software.intel.com/en-us/articles/intel-compilers-linux-installation-help/)

and a user forum here

[http://software.intel.com/en-us/forums/intel-fortran-compiler-for-linux-and-mac-os-x/](http://software.intel.com/en-us/forums/intel-fortran-compiler-for-linux-and-mac-os-x/)

---

### Post by dimosaaaa on 2012-08-04
I finally found it.
i can compile using ifort..... 
but to do this i have to type 
source /opt/intel/composer_xe_2011_sp1/bin/compilervars.sh intel64
I read that i should type this in ./bashrc file.
I typed it in last line and it doesn't work
what exactly should i type????
And something else: how do i enable colors in vi??
thanks for all

---

### Post by spjackson on 2012-08-04
> **dimosaaaa said:**
> I finally found it.
i can compile using ifort..... 
but to do this i have to type 
source /opt/intel/composer_xe_2011_sp1/bin/compilervars.sh intel64
I read that i should type this in ./bashrc file.

That's the wrong filename. It should be ~/.bashrc (assuming you are using the bash shell, of course).
> 
And something else: how do i enable colors in vi??
[Here]("http://ubuntuforums.org/showthread.php?t=2029158") is recent thread on this topic which may help.

---

### Post by quincymrj on 2012-10-28
I had the same problem, and this looks to point us in the right direction.  

Thanks to the folks who helped find us an answer (I've always noted the helpful nature of the people in LANCS when I've been there, especially on football night in the pub!), and for your patience with the less-experienced.  Particularly after the first response was such a seemingly all inclusive negative.

---

