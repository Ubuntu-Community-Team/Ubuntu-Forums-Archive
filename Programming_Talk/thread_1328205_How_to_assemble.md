---
title: "How to assemble"
date: 2009-11-16
forum: Programming Talk
---

### Post by tah_206207 on 2009-11-16
Hello
I want to assemble these codes with gas && nasm in linux i assemble these codes with masm in windows but i can't assemble thse codes with as & nasm command in linux please help me
```

       Page  60,132 
TITLE Add String1 & String2 TO String3
;-----------------------------------------------------------
       .MODEL  SMALL
       .STACK  64
;-----------------------------------------------------------
       .DATA
STR1    DB   'Hell0'          
STR2    DB   'W0rld'
STR3    DB      ?
                     ;----------------------------
;--------------------------CODE AUTHOR : Taher Atashbar---------------------------------
                          ;----------------------------
        .CODE
ADDMAIN    PROC  FAR         
           MOV  AX , @data           
           MOV  DS , AX              
           MOV  ES , AX                 

           MOV  CX , 05                                                    
           LEA  SI , STR1          
           LEA  DI , STR3          

FOR:
           MOV  AL , [SI]            
           MOV  [DI],AL              
           INC  SI                   
           INC  DI                   
           DEC  CX                   
           JNZ  FOR                  


       MOV  CX , 05                                                     
           LEA  SI , STR2          
           
WHILE:
       MOV  AL , [SI]            
           MOV  [DI],AL              
           INC  SI                   
           INC  DI                   
           DEC  CX                   
           JNZ  WHILE                  
      
   
       MOV AL,'$'
       MOV [DI],AL

                                     
           MOV  AH,09H               
           LEA  DX,STR3            
           INT  21H                             
                     
           MOV  AX,4C00H             
           INT  21H
ADDMAIN    ENDP
           END ADDMAIN      

```

```

       Page  60,132 
TITLE SWAP 2 string
;-----------------------------------------------------------
       .MODEL  SMALL
       .STACK  64
;-----------------------------------------------------------
       .DATA
STR1    DB   'Hell0','$'          
STR2    DB   'w0rld','$' 
              ;----------------------------          
;--------------------------CODE AUTHOR : Taher Atashbar---------------------------------
              ;----------------------------
       .CODE
SWAPMAIN    PROC  FAR         
           MOV  AX , @data           
           MOV  DS , AX              
           MOV  ES , AX                 

           MOV  CX , 05                                                     
           LEA  SI , STR1          
           LEA  DI , STR2          

SWAP:
           MOV  AL , [SI]            
       XCHG [DI],AL
           MOV  [SI],AL              
           INC  SI                   
           INC  DI                   
           DEC  CX                   
           JNZ  SWAP                  
                                     
           MOV  AH,09H               
           LEA  DX,STR1            
           INT  21H 

 
       MOV  AH,09H               
           LEA  DX,STR2            
           INT  21H                                 
                     
           MOV  AX,4C00H             
           INT  21H
SWAPMAIN    ENDP
           END SWAPMAIN      

```
thx

---

### Post by Zugzwang on 2009-11-16
MASM, NASM and GAS all have different syntax for "control commands", e.g., those commands that tell the assembler into which segment some code should go. Therefore they are essentially incompatible.

But even if you learn how to re-write your code in order to compile well on NASM (for example), the code will not run in Linux as you use system calls that are DOS-specific.

You probably want to use DOSBOX and install either TASM or MASM there. This also gives you an environment for running your programs. Note that you can still use the Linux text editors if you do it that way.

---

### Post by rCXer on 2009-11-16
Zugzwang is right about installing dosbox. To install it, type into the terminal...
```

sudo apt-get install dosbox

```

Here is your 1st  program converted to nasm. (I like nasm's clean syntax better than MASM ;) )  Just save it as "add.asm"

```

           ORG 100h

           MOV  AX , DS           
           MOV  DS , AX              
           MOV  ES , AX                 

           MOV  CX , 05                                                    
           LEA  SI ,[STR1]          
           LEA  DI ,[STR3]         

FOR:
           MOV  AL , [SI]            
           MOV  [DI],AL              
           INC  SI                   
           INC  DI                   
           DEC  CX                   
           JNZ  FOR                  

           MOV  CX , 05                                                     
           LEA  SI ,[STR2]          
           
WHILE:
           MOV  AL , [SI]            
           MOV  [DI],AL              
           INC  SI                   
           INC  DI                   
           DEC  CX                   
           JNZ  WHILE                  
      
           MOV AL,'$'
           MOV [DI],AL
                                     
           MOV  AH,09H               
           LEA  DX,[STR3]            
           INT  21H                             
                     
           MOV  AX,4C00H             
           INT  21H

STR1    DB   'Hell0'          
STR2    DB   'W0rld'
STR3    RESB 20    ;Reserves 20 bytes for string

```

To assemble it...
```

nasm add.asm -o add.com 

```

To run it in dosbox...
```

dosbox -noautoexec add.com

```

Here is your 2nd program converted to nasm...
```

           ORG 100h      

           MOV  AX , ds           
           MOV  DS , AX              
           MOV  ES , AX                 

           MOV  CX , 05                                                     
           LEA  SI , [STR1]          
           LEA  DI , [STR2]          

SWAP:
           MOV  AL , [SI]            
           XCHG [DI],AL
           MOV  [SI],AL              
           INC  SI                   
           INC  DI                   
           DEC  CX                   
           JNZ  SWAP                  
                                     
           MOV  AH,09H               
           LEA  DX,[STR1]
           INT  21H
 
           MOV  AH,09H               
           LEA  DX,[STR2]            
           INT  21H                                 
                     
           MOV  AX,4C00H             
           INT  21H

STR1    DB   'Hell0','$'         
STR2    DB   'w0rld','$'

```
...assemble and run it in the same way as your 1st program.

By the way, a better place to ask asm questions is the [ASM Community Forum](http://www.asmcommunity.net/board/). Good Luck :popcorn:

---

### Post by WitchCraft on 2009-11-17
Have you tried yasm?

---

### Post by samjh on 2009-11-17
> **WitchCraft said:**
> Have you tried yasm?

Yasm won't help.  The OP's assembly code is written in MASM for Windows/DOS.  He'll need to convert his syscalls to Linux before there is any chance of his code working on Linux.

---

### Post by WitchCraft on 2009-11-23
> **samjh said:**
> Yasm won't help.  The OP's assembly code is written in MASM for Windows/DOS.  He'll need to convert his syscalls to Linux before there is any chance of his code working on Linux.

Wouldn't wine do the trick, or is wine just for the API's, not the syscalls ?

---

### Post by Aayu on 2009-11-23
> **WitchCraft said:**
> Wouldn't wine do the trick, or is wine just for the API's, not the syscalls ?
 
I don't think so.  I doubt any form of emulation could emulate a DOS/Windows syscall to run on Linux..

---

### Post by tarek89 on 2011-04-02
thank you for the description i spent days and nights to look for it, but i still want to change to linux assembly am running a 64 os but i dont know how to start, i would be grateful if anybody can send me any useful tip

---

