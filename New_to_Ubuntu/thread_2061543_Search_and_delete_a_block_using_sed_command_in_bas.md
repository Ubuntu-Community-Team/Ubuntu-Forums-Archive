---
title: "Search and delete a block using sed command in bash in ubuntu"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by AmirJamez on 2012-09-22
The thing I would like to perform is to 
1- Find
2- delete the whole definition block of (__c64):

```
unsigned long long __c64(unsigned int llvm_cbe_hi, unsigned int llvm_cbe_lo) {
unsigned long long llvm_cbe_retval;    /* Address-exposed local */
unsigned long long llvm_cbe_retval1;



  *(&llvm_cbe_retval) = (((((unsigned long long )(unsigned int )llvm_cbe_hi)) << 32ul) |  (((unsigned long long )(unsigned int )llvm_cbe_lo)));
  llvm_cbe_retval1 = *(&llvm_cbe_retval);
  return llvm_cbe_retval1;
}
```


in all but one .c files in a project. Since in the compilation phase of .o to the executable, I got the error "Multiple definition of __c64", I was thinking to delete all of those but one in order to solve the problem.

when I use :
```
":%s/unsigned long long __c64\(.\+\n\)\+\(\n\)\+\(.\+\n\)\+}//"
```

inside the vi editor for each file, everything is fine and it works but when I wanna embed it inside other bash script with sed -i :
```
sed -i 's/unsigned long long __c64\(.\+\n\)\+\(\n\)\+\(.\+\n\)\+}//' "$f"
```

It didn't change anything though :|

Might be the differences between the sed and vi, Any ideas?

Regards,

Amir

---

### Post by steeldriver on 2012-09-22
[NB just trying to answer the 'sed' question here - you may want to think about other ways to fix this e.g. using #ifdefs]

Unless you use branching, the sed pattern match doesn't span multiple lines like that - I think for this kind of thing the delete ('d') command is what you want, using regexes to define the start and end points

If the block always has the same number of lines, you could maybe do something like

```
sed '/^unsigned long long __c64/+10d'
```or you could try deleting BETWEEN two patterns, i.e.

```
sed '/^unsigned long long __c64/,/}/d'
```but it *might* do a greedy match (i.e. delete everything to the *final* '}' in the file) - not sure about that, try it (without the -i obviously) before deciding

---

### Post by AmirJamez on 2012-09-22
> **steeldriver said:**
> [NB just trying to answer the 'sed' question here - you may want to think about other ways to fix this e.g. using #ifdefs]

Unless you use branching, the sed pattern match doesn't span multiple lines like that - I think for this kind of thing the delete ('d') command is what you want, using regexes to define the start and end points

If the block always has the same number of lines, you could maybe do something like

```
sed '/^unsigned long long __c64/+10d'
```or you could try deleting BETWEEN two patterns, i.e.

```
sed '/^unsigned long long __c64/,/}/d'
```but it *might* do a greedy match (i.e. delete everything to the *final* '}' in the file) - not sure about that, try it (without the -i obviously) before deciding


Thanks for the reply ;) it did help with :
```
sed -i '/^unsigned long long __c64(unsigned int llvm_cbe_hi, unsigned int llvm_cbe_lo) {/,+8d' "$f" 

```

EDITED: Since I learn that those were not statically 8 lines, I tries the second solution and it did work as well ;)
Thanks;)


Amir

---

### Post by AmirJamez on 2012-09-23
> **AmirJamez said:**
> Thanks for the reply ;) it did help with :
```
sed -i '/^unsigned long long __c64(unsigned int llvm_cbe_hi, unsigned int llvm_cbe_lo) {/,+8d' "$f" 

```

EDITED: Since I learn that those were not statically 8 lines, I tries the second solution and it did work as well ;)
Thanks;)


Amir

Buddy, your solution did work very well with all the definition type like __c64, __s64 , etc which they started with :
```
unsigned long ....
```

the only definition left which I don't know why the solution can't applied to is the :
```
void __divrem64(unsigned long long llvm_cbe_a, unsigned long long llvm_cbe_b, unsigned long long *llvm_cbe_div, unsigned long long *llvm_cbe_rem) {
  unsigned long long llvm_cbe_a_addr;    /* Address-exposed local */
  unsigned long long llvm_cbe_b_addr;    /* Address-exposed local */
  unsigned long long *llvm_cbe_rem_addr;    /* Address-exposed local */
  unsigned long long llvm_cbe_tmp__44;
  unsigned long long llvm_cbe_tmp__45;
  unsigned long long *llvm_cbe_tmp__46;

  *(&llvm_cbe_a_addr) = llvm_cbe_a;
  *(&llvm_cbe_b_addr) = llvm_cbe_b;
  *(&llvm_cbe_rem_addr) = llvm_cbe_rem;
  *llvm_cbe_div = (((unsigned long long )(((unsigned long long )llvm_cbe_a) / ((unsigned long long )llvm_cbe_b))));
  llvm_cbe_tmp__44 = *(&llvm_cbe_a_addr);
  llvm_cbe_tmp__45 = *(&llvm_cbe_b_addr);
  llvm_cbe_tmp__46 = *(&llvm_cbe_rem_addr);
  *llvm_cbe_tmp__46 = (((unsigned long long )(((unsigned long long )llvm_cbe_tmp__44) % ((unsigned long long )llvm_cbe_tmp__45))));
  return;
}

```

Could you please explain the reason ??

Thanks,

Amir

---

### Post by AmirJamez on 2012-09-23
> **AmirJamez said:**
> Buddy, your solution did work very well with all the definition type like __c64, __s64 , etc which they started with :
```
unsigned long ....
```

the only definition left which I don't know why the solution can't applied to is the :
```
void __divrem64(unsigned long long llvm_cbe_a, unsigned long long llvm_cbe_b, unsigned long long *llvm_cbe_div, unsigned long long *llvm_cbe_rem) {
  unsigned long long llvm_cbe_a_addr;    /* Address-exposed local */
  unsigned long long llvm_cbe_b_addr;    /* Address-exposed local */
  unsigned long long *llvm_cbe_rem_addr;    /* Address-exposed local */
  unsigned long long llvm_cbe_tmp__44;
  unsigned long long llvm_cbe_tmp__45;
  unsigned long long *llvm_cbe_tmp__46;

  *(&llvm_cbe_a_addr) = llvm_cbe_a;
  *(&llvm_cbe_b_addr) = llvm_cbe_b;
  *(&llvm_cbe_rem_addr) = llvm_cbe_rem;
  *llvm_cbe_div = (((unsigned long long )(((unsigned long long )llvm_cbe_a) / ((unsigned long long )llvm_cbe_b))));
  llvm_cbe_tmp__44 = *(&llvm_cbe_a_addr);
  llvm_cbe_tmp__45 = *(&llvm_cbe_b_addr);
  llvm_cbe_tmp__46 = *(&llvm_cbe_rem_addr);
  *llvm_cbe_tmp__46 = (((unsigned long long )(((unsigned long long )llvm_cbe_tmp__44) % ((unsigned long long )llvm_cbe_tmp__45))));
  return;
}

```

Could you please explain the reason ??

Thanks,

Amir

P.S: Can I use static type for all of these instead of find/replace?

Amir

---

### Post by steeldriver on 2012-09-23
not sure what you mean? if you mean can you use a delete command (sed '/start/,/end/d') instead of a null substitute (sed 's/whole pattern//') then yes I think you can - provided you can define suitable /start/ and /end/ patterns

What is exactly is the problem? is the match too specific (fails to find any blocks) or not specific enough (finds blocks it shouldn't - because the /start/ and /end/ patterns can't be made specific enough?)

---

### Post by AmirJamez on 2012-09-24
> **steeldriver said:**
> not sure what you mean? if you mean can you use a delete command (sed '/start/,/end/d') instead of a null substitute (sed 's/whole pattern//') then yes I think you can - provided you can define suitable /start/ and /end/ patterns

What is exactly is the problem? is the match too specific (fails to find any blocks) or not specific enough (finds blocks it shouldn't - because the /start/ and /end/ patterns can't be made specific enough?)

Yes, It couldn't find the __dirvrem64 block like the others. I couldn't use the 
```
sed '/^void __divrem64(unsigned long long llvm_cbe_a, unsigned long long llvm_cbe_b, unsigned long long *llvm_cbe_div, unsigned long long *llvm_cbe_rem) {/,/}/d'
```

Cuz it did work for every other data definitions.

Secondly, could you please let me know what does "^" do here?

Third; If instead of this transformation, I use "static" keyword at the beginning of these function, do you think the problem of linking will be solved ? (as a recall, I was doing all these efforts since in the linking phase of compilation, I got multiple definitions for my functions).


Thanks,


Amir

---

