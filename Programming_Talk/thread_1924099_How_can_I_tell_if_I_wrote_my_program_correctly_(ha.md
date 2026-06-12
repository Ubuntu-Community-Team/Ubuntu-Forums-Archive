---
title: "How can I tell if I wrote my program correctly (has to deal with the MBR)"
date: 2012-02-12
forum: Programming Talk
---

### Post by venom104 on 2012-02-12
[B]
[/B]

                   Here is my program [http://pastebin.com/9Stdg5yc](http://pastebin.com/9Stdg5yc)   . I wrote the entire thing, and it compiles just fine in g++, but I  don't understand how to check if everything is correct. The only thing I  understand how to check is the bootable flag. How do I check the CHS  addresses, the first sectors LBA address, and the number of blocks.

Here is the assignment

Input and output

You may assume the input is redirected from the command line. You  program must check to make sure that you can read at least 512 bytes  from stdin, as the MBR is exactly 512 bytes.

The output is sent to stdout. Be sure to follow the format as specified  below, as the automated grader will try to match exactly with the  standard answer.
Reference

Just in case the wikipedia page gets modified, here is a saved version in PDF.

Since the program will be compiled as a C (instead of C++) program, you  probably want to learn how to use "printf" to print formatted numbers.  Use "man printf" or Google to learn more about printf.

As a suggestion, you can write an MBR "generator" program to generate  MBRs of various types to test your mbrviewer program. This way, you can  generate intentionally malformed MBRs and see if your mbrviewer program  reports problems as it should. Such a program can be easy to write  (initialized char array of 512 bytes) or more challenging (to allow  options). You should use the "write" function to write an entire block  of 512 bytes, and redirect the file to an output file.

"hexdump" can be a useful command to examine the contents of a binary  (non-text) file. Use "man hexdump" to learn how to use this command line  program.

You will find bit-wise operator quite useful. "&" is bitwise and,  "|" is bitwise or, "<<" is left shift, and ">>" is right  shift.

Depending on your implementation, you may also find type casting useful.  For example, you can cast a char pointer to an integer (32-bit) point,  then reference it to get a 32-bit integer value.
Behavior of your program

Your program should perform the following tasks (in the specified order):

    Read 512 bytes from stdin, and treat that as the MBR. If stdin  encounters end-of-file too early, print "MBR too small" on a single line  and do not proceed with any further processing.
    Ignore the first 440 bytes, which are designated as "Code Area".  objdump can be used to disassemble it from outside your program.
    Check the MBR signature.
        If the signature is correct, print "MBR signature confirmed" on a line, proceed to further analysis
        Otherwise, print "Invalid MBR signature 0xmnop" on a line.  "mnop" is the value of the signature bytes in 0-filled 4-digit  hexadecimal. After printing the message, do not proceed to any further  processing.
    For each partition record of the partition table:
        Print the partition number as "Partition #x" on a single line (x should be replaced by 0 to 3)
        Print whether the partition is bootable "This partition is  bootable" or "This partition is not bootable" on a single line. You  should also check for an error condition and print "0xab is an invalid  value for bootable status" on a single line, in which "ab" is the  0-filled 2-digit hexadecimal representation of the status byte.
        Print the first block CHS address as "First block @ C=x, H=y, S=z" on a single line, x, y and z are decimal numbers.
        Print the last bock CHS address as "Last block @ C=x, H=y, S=z" on a single line, x, y and z are decimal numbers.
        Print the first sector LBA address as "First sector @ 0xabcdefgh", "abcdefgh" is a 0-filled 8-digit hexadecimal number.
        Print the number of blocks as "Length=0xabcdefgh", "abcdefgh" is a 0-filled 8-digit hexadecimal number.

---

### Post by Bachstelze on 2012-02-12
You probably want

```
(sudo) cfdisk -P t /dev/sda
```

---

### Post by venom104 on 2012-02-12
> **Bachstelze said:**
> You probably want

```
(sudo) cfdisk -P t /dev/sda
```

Well on my ubuntu machine, I get this

FATAL ERROR: Bad primary partition 1: Partition ends in the final partial cylinder

On my debian machine in virtualbox I get this
Partition Table for /dev/sda

         ---Starting----      ----Ending-----    Start     Number of
 # Flags Head Sect  Cyl   ID  Head Sect  Cyl     Sector    Sectors
-- ----- ---- ---- ----- ---- ---- ---- ----- ----------- -----------
 1  0x00   32   33     0 0x83  212   34  2610        2048    41940992
 2  0x00    0    0     0 0x00    0    0     0           0           0
 3  0x00    0    0     0 0x00    0    0     0           0           0
 4  0x00    0    0     0 0x00    0    0     0           0           0


I see the bootable flag is set to zero but I still don't understand how do I check the CHS  addresses, the first sectors LBA address, and the number of blocks?

---

### Post by Bachstelze on 2012-02-12
> **venom104 said:**
> 
I see the bootable flag is set to zero but I still don't understand how do I check the CHS  addresses, the first sectors LBA address, and the number of blocks?

Uh? What do you think "Starting Head/Sect/Cyl", "Ending Head/Sect/Cyl", "Start Sector" and "Number of Sectors" mean?

---

### Post by venom104 on 2012-02-12
> **Bachstelze said:**
> Uh? What do you think "Starting Head/Sect/Cyl", "Ending Head/Sect/Cyl", "Start Sector" and "Number of Sectors" mean?

Okay, thanks? I think it's kind of obvious I don't really have much of a clue in what I'm doing. Anyway, I edited my program to display the proper CHS addresses for the FIRST block, but the numbers don't come up at all for the last block (and I've checked the entire hexdump of the mbr.bin file).  THis is my hex dump file. I don't see the eqivalent of 212, 34, 2610, 2048, or    41940992 in there. 

ramon@deblive:~/cisp453/mbrviewer$ hexdump -C mbr.bin 
00000000  fa b8 00 10 8e d0 bc 00  b0 b8 00 00 8e d8 8e c0  |................|
00000010  fb be 00 7c bf 00 06 b9  00 02 f3 a4 ea 21 06 00  |...|.........!..|
00000020  00 be be 07 38 04 75 0b  83 c6 10 81 fe fe 07 75  |....8.u........u|
00000030  f3 eb 16 b4 02 b0 01 bb  00 7c b2 80 8a 74 01 8b  |.........|...t..|
00000040  4c 02 cd 13 ea 00 7c 00  00 eb fe 00 00 00 00 00  |L.....|.........|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  ee d6 0e 00 00 00 00 20  |............... |
000001c0  21 00 83 fe ff ff 00 08  00 00 00 f8 7f 02 00 00  |!...............|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by venom104 on 2012-02-12
Mods please forgive me, this is due tomorrow so i don't have much time. /Bump

---

