---
title: "readelf vs nm and objdump in calculating executive size"
date: 2008-03-24
forum: Programming Talk
---

### Post by tinhha2005 on 2008-03-24
Dear all,

I use the readelf for calculating the TextSize, RODataSize, DataSize, BssSize, TotalSize as follow:
Text sections: type PROBITS, flag AX (not contains W)
RO data sections : type PROBITS, flag A
Data sections : type PROBITS, flag WA
Bss data sections: (not contains AWX)
$TotalSize(from readelf) = $TextSize+$RODataSize+$DataSize+$BssSize

And I use nm for calculating the $TotalSize(from nm) by calculating the total size of variable and functions. 

the $TotalSize(from readelf) <> the $TotalSize(from nm) (1)

I double check by using objdump, I calculate the size of function by get the ending address - the starting address + 2( pc step). I saw that the 
the $TotalSize(from nm) == $TotalSize(from obj)

I don't know why (1). Could you please help me? 
I attached the elf, the log of readelf, the log of nm, and the log of objdump.

Thanks,
tinhha

---

