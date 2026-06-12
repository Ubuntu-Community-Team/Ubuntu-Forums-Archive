---
title: "ld command not found"
date: 2007-03-04
forum: Programming Talk
---

### Post by Carnavan7 on 2007-03-04
Hi all, not sure if this is the correct forum but here goes.

I have been following an assembly tutorial, converted the file with nasm etc but when I have to type : ld -o myprog myprog.obj to link it, it just says command not found.

I am running the x86 version of dapper. The only thing I have installed to do this project is nasm. Im guessing there are some dev tools I might need? I have googled and searched the forums but cannot seem to find a solution.

Thanks in advance for any help.

---

### Post by hod139 on 2007-03-04
You should be able to use gcc for the linking.  Make sure you have the package build-essential installed.

---

### Post by Carnavan7 on 2007-03-04
Thanks allot. That solved the problem. Pity it wasnt mentioned in the tutorial lol. Cheers :)

---

