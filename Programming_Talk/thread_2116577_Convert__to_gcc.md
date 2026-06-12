---
title: "Convert  to gcc"
date: 2013-02-16
forum: Programming Talk
---

### Post by darvin on 2013-02-16
i have a problem with one script when i trying to compile, here is:
```

 
__declspec(naked) void CheckProtocol_AsmHelper_LDyn() { 
    __asm { 
        push esi 
        mov eax, pnet_from 
        push eax 
        call SV_CheckProtocol_rev 
        add esp, 8 
        test eax, eax 
        jz __dpfail2 
        mov eax, DSEngineData.CheckProto_GoodRet_addr 
        jmp eax 
 
        __dpfail2: 
        mov eax, DSEngineData.CheckProto_BadRet_addr 
        jmp eax 
    } 
} 
 
__declspec(naked) void CheckCDKey_Helper_LDyn() { 
    __asm { 
        mov eax, LastUserInfo 
        push eax 
        mov eax, DSEngineData.ConnectClient_CDKey_soff 
        add eax, ebp 
        push eax 
        mov eax, DSEngineData.ConnectClient_AuthProto_soff 
        add eax, ebp 
        mov eax, [eax] 
        push eax 
        mov eax, pnet_from 
        push eax 
        call SV_CheckCDKey_rev 
        add esp, 0x10 
        test eax, eax 
        jz __cdfail2 
        mov eax, DSEngineData.CheckCDKey_GoodRet_addr 
        jmp eax 
 
        __cdfail2: 
        mov eax, DSEngineData.CheckProto_BadRet_addr 
        jmp eax 
    } 
} 
 

 
__declspec(naked) void SendSrvInfo_WriteLongProto_LDyn() { 
    __asm { 
        mov eax, [esp+4] //sbuf 
        push eax 
        mov eax, [ebp+0xC] //client 
        push eax 
        call SendSrvInfo_WriteProto 
        retn 
    } 
} 
 
__declspec(naked) void DenyHelper_Hooked_WDyn() { 
    __asm { 
        mov eax, [esp+8] 
        cmp eax, 0xE 
        ja _ret 
        cmp eax, 7 
        jz _ret 
 
        mov eax, DSEngineData.GSClientDenyHelper_addr 
        jmp eax 
 
    _ret: 
        retn 0xC 
 
    } 
} 

```[FONT=monospace]

[/FONT]

i need someone to convert this windows lines to linux (gcc).
here is some info - [http://stackoverflow.com/questions/7937536/equivalent-of-declspec-naked-in-gcc-g](http://stackoverflow.com/questions/7937536/equivalent-of-declspec-naked-in-gcc-g)

---

### Post by greenpeace on 2013-02-16
Try the compiler "[clang]("http://en.wikipedia.org/wiki/Clang")".  It's compiler messages are often more useful than those from gcc.

What error messages are you getting when you try to compile?

---

### Post by pbrane on 2013-02-16
Porting assembly from windows to linux may not be that easy. The function calls that are made in the assembly, are those to windows DLLs or something else?

At this point you may just need to port the assembly to 'gas' (GNU Assembler) syntax and try again. That would give you more coherent error messages if there are any.

It's probably easier if you simply use C instead of assembler. I'm not sure why this has to be in assembly language anyway.

In your posts on other forums there are also some clues as to why this doesn't work. microsoft compiler specific extensions, etc.

---

### Post by schragge on 2013-02-16
> **pbrane said:**
> At this point you may just need to port the assembly to 'gas' (GNU Assembler) syntax and try again.There's a converter in Ubuntu repositories: [intel2gas]("http://manpages.ubuntu.com/manpages/precise/en/man1/intel2gas.1.html").

---

### Post by pbrane on 2013-02-16
> **schragge said:**
> There's a converter in Ubuntu repositories: [intel2gas]("http://manpages.ubuntu.com/manpages/precise/en/man1/intel2gas.1.html").

unless I'm mistaken that will require NASM source to convert to gas. This isn't NASM source, it's microsoft source I believe.

---

### Post by darvin on 2013-02-16
[http://dox.bg/files/dw?a=5c26bc5a7b ]("http://dox.bg/files/dw?a=5c26bc5a7b")- here is link to the source

The compile things located in **src **folder where makefile and all paths have been set, let someone fix errors through the files, please.

---

### Post by schragge on 2013-02-16
> **pbrane said:**
> unless I'm mistaken that will require NASM source to convert to gas. This isn't NASM source, it's microsoft source I believe.
Yes, you're right, but NASM like MASM uses Intel syntax, so relatively simple code snippets probably can be converted as is. Actually, newer GAS versions have *.intel_syntax* directive that makes it understand Intel syntax, too.

---

