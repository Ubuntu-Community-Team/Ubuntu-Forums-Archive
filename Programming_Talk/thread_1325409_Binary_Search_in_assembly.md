---
title: "Binary Search in assembly"
date: 2009-11-13
forum: Programming Talk
---

### Post by nikhilbhardwaj on 2009-11-13
i'm trying to implement binary search in assembly
and this is how far i've gotten 

```

;to perform binary search on an array

.model    small
.386

.data
    d1    db    13,10,'Enter Array Size :$'
    siz    db    ?
    d2    db    13,10,'Enter Number :$'
    d3    db    13,10,'Enter Number to find :$'
    num    db    ?
    d4    db    13,10,'FOUND'
    d5    db    13,10,'NOT FOUND'
    arr    db    10    dup(?)
    hi    db    ?
    lo    db    ?
    mid    db    ?
    
.code
.startup
    ;get the array size
    mov    dx,offset d1
    mov    ah,9
    int    21h
    
    call get_no
    mov    siz,dl
    ;input the array
    xor    si,si
    mov    cl,siz
    
    L1:
        mov    dx,offset d2
        mov    ah,9
        int    21h
        
        call get_no
        mov    arr[si],dl
        inc    si
    loop L1
    ;get the number to be searched
    mov    dx,offset d3
    mov    ah,9
    int    21h
    
    call    get_no
    mov    num,dl
    ;now search the array
    ;first initialize lo,hi and mid
    xor    eax,eax
    mov    bl,siz
    mov    hi,bl
    mov    lo,0
    mov    al,hi
    add    al,lo
    shr    al,1
    mov    mid,al
    ;at most size/2 passes
    mov    cl,mid
    L2:
        xor    dx,dx
        mov    dl,mid
        mov    si,dx
        mov    bh,arr[si]
        mov    bl,num
        cmp    bh,bl
        je    FOUND
        jb    LESS
        ;bh > bl or arr[mid] > num
        mov    lo,dl
        mov    al,lo
        add    al,hi
        shr    al,1
        mov    mid,al

        LESS:
        mov    hi,dl
        mov    al,hi
        add    al,lo
        shr    al,1
        mov    mid,al
    loop L2
    
    ;if it reaches here then the number wasn't found
    NOT_FOUND:
        mov    dx,offset d5
        mov    ah,9
        int    21h
        jmp    FINISH
    
    FOUND:
        mov    dx,offset d4
        mov    ah,9
        int    21h
    
    FINISH:
.exit

get_no    proc    near
    MOV    AH,01H
    INT    21H
    SUB    AL,30H
    MOV    DL,AL
    SHL    DL,4
  
    INT    21H
    SUB    AL,30H
    ADD    DL,AL
    ret
get_no    endp

end

```

we have to use masm611
could someone help me figure what's wrong with it??

---

### Post by Arndt on 2009-11-13
> **nikhilbhardwaj said:**
> i'm trying to implement binary search in assembly
and this is how far i've gotten 

```

;to perform binary search on an array

.model    small
.386

.data
    d1    db    13,10,'Enter Array Size :$'
    siz    db    ?
    d2    db    13,10,'Enter Number :$'
    d3    db    13,10,'Enter Number to find :$'
    num    db    ?
    d4    db    13,10,'FOUND'
    d5    db    13,10,'NOT FOUND'
    arr    db    10    dup(?)
    hi    db    ?
    lo    db    ?
    mid    db    ?
    
.code
.startup
    ;get the array size
    mov    dx,offset d1
    mov    ah,9
    int    21h
    
    call get_no
    mov    siz,dl
    ;input the array
    xor    si,si
    mov    cl,siz
    
    L1:
        mov    dx,offset d2
        mov    ah,9
        int    21h
        
        call get_no
        mov    arr[si],dl
        inc    si
    loop L1
    ;get the number to be searched
    mov    dx,offset d3
    mov    ah,9
    int    21h
    
    call    get_no
    mov    num,dl
    ;now search the array
    ;first initialize lo,hi and mid
    xor    eax,eax
    mov    bl,siz
    mov    hi,bl
    mov    lo,0
    mov    al,hi
    add    al,lo
    shr    al,1
    mov    mid,al
    ;at most size/2 passes
    mov    cl,mid
    L2:
        xor    dx,dx
        mov    dl,mid
        mov    si,dx
        mov    bh,arr[si]
        mov    bl,num
        cmp    bh,bl
        je    FOUND
        jb    LESS
        ;bh > bl or arr[mid] > num
        mov    lo,dl
        mov    al,lo
        add    al,hi
        shr    al,1
        mov    mid,al

        LESS:
        mov    hi,dl
        mov    al,hi
        add    al,lo
        shr    al,1
        mov    mid,al
    loop L2
    
    ;if it reaches here then the number wasn't found
    NOT_FOUND:
        mov    dx,offset d5
        mov    ah,9
        int    21h
        jmp    FINISH
    
    FOUND:
        mov    dx,offset d4
        mov    ah,9
        int    21h
    
    FINISH:
.exit

get_no    proc    near
    MOV    AH,01H
    INT    21H
    SUB    AL,30H
    MOV    DL,AL
    SHL    DL,4
  
    INT    21H
    SUB    AL,30H
    ADD    DL,AL
    ret
get_no    endp

end

```

we have to use masm611
could someone help me figure what's wrong with it??

How far does it get?

---

### Post by nikhilbhardwaj on 2009-11-13
i can input all the data
and when i search for a number
i always get not found even when the number is present

---

### Post by Arndt on 2009-11-13
> **nikhilbhardwaj said:**
> i can input all the data
and when i search for a number
i always get not found even when the number is present

```
       xor    dx,dx
        mov    dl,mid
        mov    si,dx
        mov    bh,arr[si]

```

I may be mistaken, but doesn't the above zero dx, then use it for indexing the array, while the midpoint dl isn't used?

I have actually never programmed assembler for x86.

---

### Post by nikhilbhardwaj on 2009-11-13
> **Arndt said:**
> ```
       xor    dx,dx
        mov    dl,mid
        mov    si,dx
        mov    bh,arr[si]

```I may be mistaken, but doesn't the above zero dx, then use it for indexing the array, while the midpoint dl isn't used?

I have actually never programmed assembler for x86.

i wanted 
mov bh,arr[mid]
but thats not allowed
cant add up two relocatable labels
then 
mov bh,arr[dl]
that doesnt work out since dl isn't an index register
hence the complexity above

---

### Post by nikhilbhardwaj on 2009-11-13
say is there some tool
that can show you the step by step execution
or a debugger like gdb so that i could set breakpoints for masm 611
and check out where the problem
it's quite hard to figure out just by the naked eye

---

