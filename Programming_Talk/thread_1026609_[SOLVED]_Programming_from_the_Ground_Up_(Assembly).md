---
title: "[SOLVED] Programming from the Ground Up (Assembly)"
date: 2008-12-31
forum: Programming Talk
---

### Post by Stoodle on 2008-12-31
I hate it when you copy and paste from a book and the program doesn't work like it should. I have the book Programming from the Ground Up and I copy and paste the programs and see them work, then I read the description. However, I had 3 errors.

Here's the program they gave:
```

#PURPOSE:     This program converts an input file to an output file with all
#             letters converted to uppercase.
#
#PROCESSING:  1) Open the input file
#             2) Open the output file
#             4) While we’re not at the end of the input file
#                a) read part of the file into our piece of memory
#                b) go through each byte of memory
#                     if the byte is a lower-case letter, convert it to uppercase
#                c) write the piece of memory to the output file
  .section .data
#######CONSTANTS########
  #system call numbers
  .equ SYS_OPEN, 5
  .equ SYS_WRITE, 4
  .equ SYS_READ, 3
  .equ SYS_CLOSE, 6
  .equ SYS_EXIT, 1
  #options for open() (look at /usr/include/asm/fcntl.h for
  #                    various values. You can combine them
  #                    by adding them)
  .equ O_RDONLY, 0
  .equ O_CREAT_WRONLY_TRUNC, 03101
  #standard file descriptors
  .equ STDIN, 0
  .equ STDOUT, 1
  .equ STDERR, 2

 #system call interrupt
 .equ LINUX_SYSCALL, 0x80
 .equ END_OF_FILE, 0         #This is the return value of read() which
                             #means we’ve hit the end of the file
 .equ NUMBER_ARGUMENTS, 2
.section .bss
 #Buffer - this is where the data is loaded into from
 #           the data file and written from into the output file.       This
 #           should never exceed 16,000 for various reasons.
 .equ BUFFER_SIZE, 500
 .lcomm BUFFER_DATA, BUFFER_SIZE
 .section .text
 #STACK POSITIONS
 .equ ST_SIZE_RESERVE, 8
 .equ ST_FD_IN, -4
 .equ ST_FD_OUT, -8
 .equ ST_ARGC, 0             #Number of arguments
 .equ ST_ARGV_0, 4          #Name of program
 .equ ST_ARGV_1, 8          #Input file name
 .equ ST_ARGV_2, 12          #Output file name
 .globl _start
_start:
 ###INITIALIZE PROGRAM###
 #save the stack pointer
 movl %esp, %ebp
 #Allocate space for our file descriptors on the stack
 subl $ST_SIZE_RESERVE, %esp
open_files:
open_fd_in:
 ###OPEN INPUT FILE###
 movl $SYS_OPEN, %eax                    #open syscall
 movl ST_ARGV_1(%ebp), %ebx          #input filename into %ebx
 movl $O_RDONLY, %ecx                #read-only flag
 movl $0666, %edx                    #this doesn’t really matter for reading
 int     $LINUX_SYSCALL              #call Linux
store_fd_in:

 movl  %eax, ST_FD_IN(%ebp)   #save the given file descriptor
open_fd_out:
 ###OPEN OUTPUT FILE###
 movl $SYS_OPEN, %eax                    #open the file
 movl ST_ARGV_2(%ebp), %ebx          #output filename into %ebx
 movl $O_CREAT_WRONLY_TRUNC, %ecx    #flags for writing to the file
 movl $0666, %edx                    #mode for new file (if it’s created)
 int   $LINUX_SYSCALL                #call Linux
store_fd_out:
 movl %eax, ST_FD_OUT(%ebp)        #store the file descriptor here
 ###BEGIN MAIN LOOP###
read_loop_begin:
 ###READ IN A BLOCK FROM THE INPUT FILE###
 movl $SYS_READ, %eax
 movl ST_FD_IN(%ebp), %ebx      #get the input file descriptor
 movl $BUFFER_DATA, %ecx        #the location to read into
 movl $BUFFER_SIZE, %edx        #the size of the buffer
 int   $LINUX_SYSCALL           #Size of buffer read is
                                #returned in %eax
 ###EXIT IF WE’VE REACHED THE END###
 cmpl $END_OF_FILE, %eax        #check for end of file marker
 jle   end_loop                 #if found or on error, go to the end
continue_read_loop:
 ###CONVERT THE BLOCK TO UPPER CASE###
 pushl $BUFFER_DATA             #location of the buffer
 pushl %eax                     #size of the buffer
 call convert_to_upper
 popl %eax                      #get the size of the read back
 addl $4, %esp                  #move the stack the rest of the
                                #way back
 ###WRITE THE BLOCK OUT TO THE OUTPUT FILE###
 movl %eax, %edx                #size of the buffer
 movl $SYS_WRITE, %eax
 movl ST_FD_OUT(%ebp), %ebx     #file to use
 movl $BUFFER_DATA, %ecx        #location of the buffer
 int   $LINUX_SYSCALL

  ###CONTINUE THE LOOP###
  jmp    read_loop_begin
end_loop:
  ###CLOSE THE FILES###
  #NOTE - we don’t need to do error checking on these, because
  #        error conditions don’t signify anything special here
  movl $SYS_CLOSE, %eax
  movl ST_FD_OUT(%ebp), %ebx
  int    $LINUX_SYSCALL
  movl   $SYS_CLOSE, %eax
  movl   ST_FD_IN(%ebp), %ebx
  int    $LINUX_SYSCALL
  ###EXIT###
  movl $SYS_EXIT, %eax
  movl $0, %ebx
  int    $LINUX_SYSCALL
#PURPOSE:      This function actually does the conversion to upper case for a block
#
#INPUT:        The first parameter is the location of the block of memory to convert
#              The second parameter is the length of that buffer
#
#OUTPUT:       This function overwrites the current buffer with the upper-casified
#              version.
#
#VARIABLES:
#              %eax - beginning of buffer
#              %ebx - length of buffer
#              %edi - current buffer offset
#              %cl - current byte being examined (first part of %ecx)
#
  ###CONSTANTS##
  .equ LOWERCASE_A, a                 #The lower boundary of our search
  .equ LOWERCASE_Z, z                 #The upper boundary of our search
  .equ UPPER_CONVERSION, ’A’ - ’a’      #Conversion between upper and lower case
  ###STACK STUFF###
  .equ ST_BUFFER_LEN, 8                 #Length of buffer
  .equ ST_BUFFER, 12                    #actual buffer

convert_to_upper:
 pushl %ebp
 movl %esp, %ebp
 ###SET UP VARIABLES###
 movl ST_BUFFER(%ebp), %eax
 movl ST_BUFFER_LEN(%ebp), %ebx
 movl $0, %edi
 #if a buffer with zero length was given us, just leave
 cmpl $0, %ebx
 je    end_convert_loop
convert_loop:
 #get the current byte
 movb (%eax,%edi,1), %cl
 #go to the next byte unless it is between ’a’ and ’z’
 cmpb $LOWERCASE_A, %cl
 jl    next_byte
 cmpb $LOWERCASE_Z, %cl
 jg    next_byte
 #otherwise convert the byte to uppercase
 addb $UPPER_CONVERSION, %cl
 #and store it back
 movb %cl, (%eax,%edi,1)
next_byte:
 incl %edi               #next byte
 cmpl %edi, %ebx         #continue unless we’ve reached the end
 jne   convert_loop
end_convert_loop:
 #no return value, just leave
 movl %ebp, %esp
 popl %ebp
 ret

```

If you copy and paste this into an editor to see the line numbers, I had an error at 134, 135, and 136.
At 134, it says
```

Error: undefined symbol `’A’' in operation setting `UPPER_CONVERSION'
Error: undefined symbol `’a’' in operation setting `UPPER_CONVERSION'

```
I changed that line to
```

.equ UPPER_CONVERSION, ’-32

```

and it assembles.

I link it and get this:
```

toupper.o: In function `convert_loop':
(.text+0xa6): undefined reference to `’a’'
toupper.o: In function `convert_loop':
(.text+0xab): undefined reference to `’z’'

```

Can I have some help here? Thanks!

---

### Post by pp. on 2008-12-31
I'd think that all those errors you mention lie in that part of the code:
```
  ###CONSTANTS##
  .equ LOWERCASE_A, a                 #The lower boundary of our search
  .equ LOWERCASE_Z, z                 #The upper boundary of our search
  .equ UPPER_CONVERSION, ’A’ - ’a’      #Conversion between upper and lower case
```

In order to learn something about Assembly, I'd suggest to study closely what the .equ statement does and how letters can be used as "numerical" values in this context, i.e. in Assembly arithmetics.

Also, you might want to check if your text editor somehow changes single quotes into other characters.

---

### Post by Stoodle on 2008-12-31
They do lie in that part of the code. I realize that .equ makes a string of letters a constant with a numeric value. I also realize that letters have ASCII values which are numbers. My problem is that it's straight copy and paste and it doesn't work. I'm using gedit and assembling with as and linking with ld as intructed. Maybe it's a problem with gedit but that's how it is in the book.

Here's the book I'm reading. It's available free online.
[http://nongnu.askapache.com/pgubook/ProgrammingGroundUp-1-0-booksize.pdf](http://nongnu.askapache.com/pgubook/ProgrammingGroundUp-1-0-booksize.pdf)

It's from pages 57 to 61 but in a pdf reader, that's 63 to 67.

---

### Post by pp. on 2008-12-31
Sorry, I thought you wanted help with learning the Assembly language when you wanted to complain about the examples in the book not being executable.

Anyway, being a bit bored right now I went and had a look at the PDF you linked to in your post above. 

I presume that the code example is the one on page 92 in the PDF doc (the one with the page number '86' printed on the bottom of the page).

I find the following bit of code there:

```
###CONSTANTS##
#The lower boundary of our search
.equ LOWERCASE_A, ’a’
#The upper boundary of our search
.equ LOWERCASE_Z, ’z’
#Conversion between upper and lower case
.equ UPPER_CONVERSION, ’A’ - ’a’
```

which is not quite the same as in your first post.

Again, you might want to read up on how to use letters when you want to refer to their ordinal values as opposed to using them as "symbols" or "identifiers".

---

### Post by pmasiar on 2008-12-31
> **pp. said:**
> Sorry, I thought you wanted help with learning the Assembly language when you wanted to complain about the examples in the book not being executable.

That's common problem with computer books that typesetting will mess up syntax. Get used to it. Good authors provide website where you can download the code as plain text files, and run validation tests to make sure code works.

---

### Post by Stoodle on 2009-01-03
Ah! The problem was that you must refer to single characters with one single quote such as 'a or 'b.

---

### Post by slavik on 2009-01-03
it's actually 'a' or 'b' (enclosed by single quotes), this also works the same way in C.

---

### Post by Stoodle on 2009-01-03
No, not in GAS assembly. You can only use one single quote. I was assembling with as and linking with ld. Copy and paste it.

---

### Post by rplantz on 2009-01-06
I hope that I'm not offending Stoodle here, but he has made a mistake that I (and I'm sure many others) have made many times in the past. His/her solution to the problem works and is correct, but for the wrong reason.

We all copy/paste source code as a learning tool. To help avoid the frustrations similar to Stroodle's, I have posted a "HOWNOTTO" at [http://ubuntuforums.org/showthread.php?p=6508156#post6508156](http://ubuntuforums.org/showthread.php?p=6508156#post6508156)

---

### Post by Mr.Fluke on 2009-02-19
Rplantz wins with most courteous and informative post.

If you're just glancing over the thread and have the same problem as stoodle (as I did) the **problem is &#8217; vs '** you want a vertical apostrophe not an angled one.

---

