---
title: "Super basic/simple scripting question for mathematics operation"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by ebodnaruk on 2012-08-15
Hi Ubuntu users!  

I'm new to Bash Scripting and was wondering if someone could help me with a very simple task I have.  

I have two texts files.  Each file has only one column of data, and many rows.  Each row is simply a number.  What I want to do is essentially perform the pythagorean formula for the first entry in file A and file B, producing a new number for newly created file C.  Then the same for the second entry in file A and file B, producing a new number for file C.  

I know there's got to be a super elegant and fast way of doing that in Ubuntu without using a loop.  I'd appreciate it if someone could share with me a  command that would do that.  (Is awk the best?)

Thanks!

For example,

File A               File B                              FileC
3                       4                                       5
5              +      10                --------->      12  
6                       8                                       10

---

### Post by steeldriver on 2012-08-16
you could use 'paste' to columnize the input and then 'awk' do do the line by line math

---

### Post by spjackson on 2012-08-16
> **steeldriver said:**
> you could use 'paste' to columnize the input and then 'awk' do do the line by line math
Indeed
```

paste FileA FileB | awk '{print sqrt($1*$1 + $2*$2}' > FileC

```

---

### Post by Hadaka on 2012-08-16
```
 
paste FileA FileB | awk '{print sqrt($1*$1 + $2*$2**)**}' > FileC 
```you forgot to close the door to keep the little sq. roots from escapeing :p

---

