---
title: "help I'm getting a segmentation fault in c"
date: 2010-11-24
forum: Programming Talk
---

### Post by technmom on 2010-11-24
My program gets a segmentation fault when I print. I added the "you are here statements" if I uncomment the last one the one before it prints but as it is the one before it is where it faults.

 printf("\n after Decode "); 
       printf( "\nafter Decode,  opcode %d address %d    PC_cntl = %d", opcode_D,  address_D, 
                   PC_cntl ); 
      printf("\n you are here"); 
// printf("\n you are here"); 
         if ( opcode_D == 0b1011 ) { 
            inst_F = inst_D; 
            halt = 1;

---

### Post by spjackson on 2010-11-25
The problem is not in this code but elsewhere in your program. Please post a minimal compete example that demonstrates the problem.

---

### Post by Arndt on 2010-11-25
> **technmom said:**
> My program gets a segmentation fault when I print. I added the "you are here statements" if I uncomment the last one the one before it prints but as it is the one before it is where it faults.

 printf("\n after Decode "); 
       printf( "\nafter Decode,  opcode %d address %d    PC_cntl = %d", opcode_D,  address_D, 
                   PC_cntl ); 
      printf("\n you are here"); 
// printf("\n you are here"); 
         if ( opcode_D == 0b1011 ) { 
            inst_F = inst_D; 
            halt = 1;

Try 'valgrind'.

---

### Post by jamesbon on 2010-11-25
Post the complete code so that we can understand what is happening.

---

### Post by trent.josephsen on 2010-11-25
If I understand correctly your comment about printing, be aware that you need to add "\n" to make sure a line of output actually prints.  (Otherwise it can be overwritten by the prompt, or even (I think) skipped entirely.)

---

