---
title: "Assembly"
date: 2011-03-05
forum: Programming Talk
---

### Post by amiller2571 on 2011-03-05
I'm currently in a assembly class for Windows. The teacher is having us write directly to video memory on cmd. The reason is that he wants us to learn to printer characters to the screen the hard way. In order to do this we have to put cmd into real mode, other wise we could not access the memory. My question is how would I go about doing this in Linux? I would like to learn how to write directly to the terminal's memory.

---

### Post by Queue29 on 2011-03-05
Huh? I'm no expert in Windows, but I'm pretty sure there are quite a few layers of abstraction between the cmd and writing to memory... What exactly is it you are doing?

---

### Post by cgroza on 2011-03-05
> **amiller2571 said:**
> I'm currently in a assembly class for Windows. The teacher is having us write directly to video memory on cmd. The reason is that he wants us to learn to printer characters to the screen the hard way. In order to do this we have to put cmd into real mode, other wise we could not access the memory. My question is how would I go about doing this in Linux? I would like to learn how to write directly to the terminal's memory.
Do you need to open stdout in assembly and push characters there??

---

### Post by amiller2571 on 2011-03-05
I am new to assembly so I don't know the correct terms to use, Here is one of the programs I wrote for the class.

```
MyStack SEGMENT STACK

     DW 256 DUP (?)

ENDS

;----------------------------------------------------------------------
MyData SEGMENT

     CRTMemSeg EQU 0B800h         ; Segment for video RAM
     ESCKEY EQU   27


ENDS
;----------------------------------------------------------------------
MyCode SEGMENT
     ASSUME CS:MyCode, DS:MyData
StartHere:

     MOV  AX, MyData
     MOV  DS, AX

     MOV  AX, CRTMemSeg            ; Move video segment address into AX
     MOV  ES, AX                   ; Move AX into ES so that ES points to video segment

     MOV CX, 2000                  ; Moves 2000 into CX, use to loop throw the video segment
     MOV BX, 0                     ; Move 0 into BX

ClearScreenLoop:                   ; loop to fill as video segment spaces with black background and blank text

     MOV  ES:[BX+1], BYTE PTR 00001111b ; set video memory to black background
     MOV  ES:[BX], BYTE PTR 00000000b   ; set video memory to blank text
     ADD  BX, 2                         ; advance BX by 2, to point to the next video segment space
     loop ClearScreenLoop               ; if CX is not 0, repeat

     MOV AX, 0                     ; clears AX for next loop

MyLoop:

     MOV  AH, 12h             	   ;Get shift status
     INT  16h                      ;Makes system call
     AND  AX, 0000100000000000b    ;check if right alt key is down
     CMP  AX, 0			   ;
     JE   ShowSpace                ;if so jump to ShowSpace
     MOV  ES:[542], BYTE PTR 'X'   ;if not display 'X'
     MOV  ES:[543], BYTE PTR 00100100b
     JMP BottomLoop                ; jump to bottom of loop

ShowSpace:			   ; if right alt key is down, display B

     MOV  ES:[542], BYTE PTR 'B'
     MOV  ES:[543], BYTE PTR 01000010b

BottomLoop:			   ; check if the esc key has be pressed
				   ; if so exit the program
     MOV  AH, 11h		   ; else jump to the top of the loop
     INT  16h

     JZ   MyLoop 
     MOV  AH, 10h
     INT  16h
     CMP  AL, ESCC
     JNE MyLoop

     MOV            AH, 4Ch
     INT            21h

ENDS
;----------------------------------------------------------------------

END StartHere
```

As you can see in the program I write either X or B to the video segment for the console. I would like to be able to do this with the Linux terminal. How would you write to the screen segment with out using system calls/interrupts?

---

### Post by ceclauson on 2011-03-07
Interesting question, because it's one that I tried to figure out a while ago.

The short answer, as best as I could figure out, is that it's more complicated on Linux.  I don't think user mode programs have access to that low a level of the system like they used to in DOS.  There might be a way to do it by writing a custom device driver, though, not sure.

Just to clarify what I'm talking about: old school DOS systems allowed user programs to either communicate through the kernel, communicate with the BIOS, or talk to the hardware directly.  The latter two are what I don't you can do on Linux with user programs, but again, there's probably a solution that involves writing a device driver.

---

### Post by Zugzwang on 2011-03-07
@OP: What you want cannot be done in Linux *nor* in Windows. However, for a DOS program, Windows' emulation layer will behave as if it could be done. In Linux, there's no such thing as an automatic emulation layer, so I suppose that you execute your program in a DosBOX, which should do the trick.

---

