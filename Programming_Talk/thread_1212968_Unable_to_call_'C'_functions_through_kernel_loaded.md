---
title: "Unable to call 'C' functions through kernel loaded at sector 2"
date: 2009-07-14
forum: Programming Talk
---

### Post by zak100 on 2009-07-14
Hi,
I am using kernel code in which I have put the 'C' functions. This code is being loaded to the sector 2 after creating the bin file using exe2bin. 
I am also creating a stack but its not detected by the linker.
D:\nasm prog>alink -o kernel.exe test_kernel2.obj main1.o
ALINK v1.6 (C) Copyright 1998-9 Anthony A.J. Williams.
All Rights Reserved
Loading file test_kernel2.obj
Loading file main1.o
matched Externs
matched ComDefs
Warning - no stack
D:\nasm prog>
The complete kernel code is given below. 
I am also creating a stack but its not detected by loader
; call c function
extern _K_main
;--- test kernel.bin---
;    push cs
;    push cs
;    pop ds
;    pop es
 ..start:   mov ax, 7E0H
    mov ds,ax
    mov es,ax
    mov si, msg
    mov ah, 0Eh
    mov bx, 7
top:
    lodsb
    cmp al, 0
    jz blackhole
    int 10h
    jmp short top
blackhole:
    
    mov cx,1000
    Delay: Loop Delay
    call _K_main; this is in main.c
    hlt
    jmp blackhole
msg db 'Welcome to the Kernel!', 0
times 0x200-($-$$) db 0
        
--------------------------------------------------------------------------
The loader for this kernel is given below. I am also creating a stack but it is not detected by linker
-------------------------------------------------------------------------------
ORG 7c00h      ;Because BIOS loades the OS at 
                       ; address 0:7C00h so ORG 7C00h 
                       ; makes that the refrence to date 
                       ; are with the right offset (7c00h).

                       
   ; CS = 0 / IP = 7C00h // SS = ? / SP = ?
   ; You are now at address 7c00.
jmp start   ;Here we start the, BIOS gave us now the control.
 
;///////////////////////////////////////////
;//Here goes all the data of the program.
;///////////////////////////////////////////
xCursor db 0
yCursor db 0

nSector db 0
nTrack  db 0
nSide   db 0
nDrive  db 0
nTrays  db 0
;
szReady                db 'Are You Ready to start Loading the OS...',0
szErrorReadingDrive    db 'Error Reading Drive, Press any Key to reboot...',0
;//Done Reading a track.
szPlaceMarker          db  '~~~~',0
szDone                 db  'Done',0
pOS                    dw   7E00h
;//Points to where to download the Operating System. 
;//Disk Paremeter Table.
StepRateAndHeadUnloadTime                     db      0DFh
HeadLoadTimeAndDMAModeFlag                    db      2h
DelayForMotorTurnOff                          db      25h
;// (1 = 256) //(2 = 512 bytes)
BytesPerSector                                db      2h
;// 18 sectors in a track.
SectorsPerTrack                               db      18
IntersectorGapLength                          db      1Bh
DataLength                                    db      0FFh
IntersectorGapLengthDuringFormat              db      54h
FormatByteValue                               db      0F6h
HeadSettlingTime                              db      0Fh
DelayUntilMotorAtNormalSpeed                  db      8h
DisketteSectorAddress_as_LBA_OfTheDataArea    db      0
CylinderNumberToReadFrom                      db      0
SectorNumberToReadFrom                        db      0
DisketteSectorAddress_as_LBA_OfTheRootDirectory      db      0
;/////////////////////////////////
;//Here the program starts.
;/////////////////////////////////

start:
    CLI     ;Clear Interupt Flag so while setting 
        ;up the stack any interrupt would not be fired.
;----------------STACK
        mov AX,7B0h    ;lets have the stack start at 7c00h-256 = 7B00h
        mov SS,ax      ;SS:SP = 7B0h:256 = 7B00h:256
        mov SP,256     ;Lets make the stack 256 bytes.---------------STACK
;        Mov ax,CS      ;Set the data segment = CS = 0 
; suggest you use 0 here!
        
        XOR AX,AX      ;Makes AX=0.
        MOV ES,AX      ;Make ES=0
        mov DS,ax

    STI     ;Set Back the Interupt Flag after 
        ;we finished setting a stack frame.
       
        Call ClearScreen       ;ClearScreen()
        LEA AX,[szReady]         ;Get Address of szReady.
        CALL PrintMessage      ;Call PrintfMessage()
        CALL GetKey                    ;Call GetKey()
        
;        CALL SetNewDisketteParameterTable
        ;SetNewDisketteParameterTable()
        
    mov bp, 1 ; sectors to load
        CALL DownloadOS
        CALL GetKey                    ;Call GetKey()
        CALL GiveControlToOS  ;Give Control To OS.
;ret
;/////////////////////////////////////
;//Prints a message to the screen.
;/////////////////////////////////////
PrintMessage: ; PROC
        mov DI,AX      ;AX holds the address of the string to Display.
        Mov byte [xCursor],1  ;Column.
        
ContinuPrinting:
        cmp byte [DI],0    ;Did we get to the End of String.
        JE EndPrintingMessage  ;if you get to the end of the string return.
        
        mov AH,2               ;Move Cursor
        mov DH,[yCursor]         ;row.
        mov DL,[xCursor]         ;column.
        mov BH,0               ;page number.
        INT 10h
        INC byte [xCursor]
        
        mov AH,0Ah             ;Display Character Function.
        mov AL,[DI]            ;character to display.
        mov BH,0               ;page number.
        mov CX,1               ;number of times to write character
        INT 10h
        
        
               
        INC DI                 ;Go to next character.
        
        JMP ContinuPrinting    ;go to Print Next Character.
               
EndPrintingMessage:
        
        Inc byte [yCursor]            ;So Next time the message would
                               ;be printed in the second line.
        
        cmp byte [yCursor],25
        JNE dontMoveCorsurToBegin 
        Mov byte [yCursor],0
        
dontMoveCorsurToBegin:
        ret
        
               
;PrintMessage EndP 
;//////////////////////////////////////
;//Waits for the user to press a key.
;//////////////////////////////////////
GetKey: ; PROC
        mov ah,0
        int 16h ;Wait for a key press.
        Ret
        
;GetKey EndP 
;///////////////////////////////////////////
;//Gives Control To Second Part Loader.
;///////////////////////////////////////////
GiveControlToOS: ; PROC
        LEA AX,[szDone]
        Call PrintMessage
        CALL GetKey
        
;        db 0e9h        ;Far JMP op code.
;        dw 512         ;JMP 512 bytes ahead
    ;jmp 0:7E00h;-----------------------------------At this point we are going to Kernel code; for including C prog:test_kernel2.asm
        jmp 7D0h:100h
        ; jmp 0:7D00h
;       POP AX         ;//Another why to make 
                       ;the CPU jump to a new place.
;       POP AX
;       Push 7E0h      ;Push New CS address.
;       Push 0          ;Push New IP address.
               ;The address that comes out is 7E00:0000. 
; comment does not match code!

               ;(512 bytes Higher from were BIOS Put us.)
       retf
; you'd want "retf" here.
        
;GiveControlToOS EndP 
;///////////////////////////////////
;//Clear Screen.
;///////////////////////////////////
ClearScreen: ; PROC
        mov ax,0600h   ;//Scroll All Screen UP to Clear Screen.
        mov bh,07
        mov cx,0
        mov dx,184fh   
        int 10h
        
        Mov byte [xCursor],0  ;//Set Cursor Position So next 
                        ;//write would start in 
                        ;//the beginning of screen.
        Mov byte [yCursor],0
        Ret
        
;ClearScreen EndP
;/////////////////////////////////
;//PrintPlaceMarker.
;/////////////////////////////////
PrintPlaceMarker: ; PROC

        LEA AX,[szPlaceMarker]
        CALL PrintMessage  ;Call PrintfMessage()
        CALL GetKey        ;Call GetKey()
        ret
        
;PrintPlaceMarker EndP
;/////////////////////////////////////////
;//Set New Disk Parameter Table
;/////////////////////////////////////////
SetNewDisketteParameterTable: ; PROC
        LEA DX,[StepRateAndHeadUnloadTime]
        ;//Get the address of the Disk Parameters Block. 
        
               ;//Int 1E (that is in address 0:78h) 
               ;//holds the address of the disk parametrs 
               ;//block, so now change it to 
               ;//our parametr black.
        ;//DX holds the address of our Parameters block.
        MOV WORD  [CS:0078h],DX
        MOV WORD  [CS:007Ah],0000
; these should have labels on 'em. Where is this supposed to be???
        
        ;Reset Drive To Update the DisketteParameterTable.
        MOV AH,0
        INT 13H
       
        ret
        
;SetNewDisketteParameterTable EndP
;///////////////////////////////////
;//DownloadOS
;///////////////////////////////////
DownloadOS:  ;PROC
        mov byte [nDrive],0
        mov byte [nSide],0
        mov byte [nTrack],0
        mov byte [nSector],1
        
ContinueDownload:
        
        INC byte [nSector]            ;Read Next Sector.
        cmp byte [nSector],19         ;Did we get to end of track.
        JNE StayInTrack
        CALL PrintPlaceMarker  ;Print now '~~~~' so the user would 
                               ;now that we finished reading a track
        INC byte [nTrack]             ;If we get to end of track Move to next track.
        mov byte [nSector],1          ;And Read Next Sector.
        CMP byte [nTrack],5           ;Read 5 Tracks (Modify this value 
                               ;to how much Tracks you want to read).
        JE      EndDownloadingOS
        
StayInTrack:
        
        ;ReadSector();
        Call ReadSector
    dec bp
    jz EndDownloadingOS
        
        
        JMP     ContinueDownload
        ;If didn't yet finish Loading OS.
        
EndDownloadingOS:
        ret
        
;DownloadOS EndP 
;////////////////////////////////////////
;//Read Sector.
;////////////////////////////////////////
ReadSector: ; PROC
        mov byte [nTrays],0
        
TryAgain:
        mov AH,2               ;//Read Function.
        mov AL,1               ;//1 Sector.
        mov CH,[nTrack]
        mov CL,[nSector]         ;//Remember: Sectors start with 1, not 0.
        mov DH,[nSide]
        mov DL,[nDrive]
        Mov BX,[pOS]             ;//ES:BX points to the address 
                               ;to were to store the sector.
        INT 13h
        
    jnc EndReadSector
        CMP AH,0               ;Int 13 return Code is in AH.
        JE EndReadSector       ;if 'Sucsess' (AH = 0) End function.
        mov AH,0               ;Else Reset Drive . And Try Again...
        INT 13h
        cmp byte [nTrays],3           ;Chack if you tryed reading 
                               ;more then 3 times.
        
        JE DisplayError        ; if tryed 3 Times Display Error.
        
        INC byte [nTrays]
        
        jmp TryAgain       ;Try Reading again.
        
DisplayError:
        LEA AX,[szErrorReadingDrive]
        Call PrintMessage
        Call GetKey
        mov AH,0                       ;Reboot Computer.
        INT 19h
        
EndReadSector:
        ADD WORD [pOS],512  ;//Move the pointer 
                               ;(ES:BX = ES:pOS = 0:pOS) 512 bytes.
                               ;//Here you set the varible 
                               ;pOS (pOS points to were BIOS 
                               ;//Would load the Next Sector).
        Ret
        
;ReadSector EndP 
;////////////////////////////////////
;//
;////////////////////////////////////
times 510 - ($ - $$) db 0
db 55h, 0AAh
;-------------------

---------------------------------------------
And the 'C' prog file is:
--------------------------------------------------

#define WHITE_TXT 0x07
void K_clear_screen();
unsigned int K_printf(char *message, unsigned int line);
//void update_cursor(int row, int col);
K_main(){
K_clear_screen();
K_printf("Hi\n How is this for a starter OS?",0);
}
void K_clear_screen() {
char *vidmem=(char*) 0xb8000;
unsigned int i=0;
while(i<(80*25*2))
{
vidmem[i]=' ';
i++;
vidmem[i]=WHITE_TXT;
}
}
unsigned int K_printf(char *message, unsigned int line){
char *vidmem=(char *) 0xb8000;
unsigned int i=0;
i=(line*80*2);
while(*message!=0)
{
if(*message=='\n')
{
line++;
i=(line*80*2);
*message++;
}
else {
vidmem[i]=*message;
*message++;
i++;
vidmem[i]=WHITE_TXT;
i++;
}
}
return 1;
}
 
Can somebody plz help me with this prob.
Zulfi.

---

