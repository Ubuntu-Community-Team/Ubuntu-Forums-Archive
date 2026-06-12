---
title: "Trouble Producing a Segmentation Fault"
date: 2013-02-16
forum: Programming Talk
---

### Post by dansofe0r on 2013-02-16
Hello everyone. Hope all is well. I am currently trying to produce a segmentation fault with the following program: 

notesearch.c
```

#include <stdio.h>
#include <string.h>
#include <fcntl.h>
#include <sys/stat.h>
#include "output1.h"

#define FILENAME "/var/notes"

int print_notes(int, int, char *);
int find_user_note(int, int);
int search_note(char *, char *);
void fatal(char *);

int main(int argc, char *argv[]) {
    int userid, printing=1, fd; // File descriptor
    char searchstring[100];

    if(argc > 1)
    strcpy(searchstring, argv[1]);
    else
    searchstring[0] = 0;
    userid = getuid();
    fd = open(FILENAME, O_RDONLY); // Open the file for read-only access.
    if(fd == -1)
    fatal("in main() while opening file for reading");
    while(printing)
    printing = print_notes(fd, userid, searchstring);
    printf("-------[ end of note data ]-------\n");
    close(fd);
}

int print_notes(int fd, int uid, char *searchstring) {
    int note_length;
    char byte=0, note_buffer[100];

    note_length = find_user_note(fd, uid);
    if(note_length == -1) // If end of file reached,
        return 0;

    read(fd, note_buffer, note_length); // Read note data.
    note_buffer[note_length] = 0;    // Terminate the string.
    
    if(search_note(note_buffer, searchstring)) // If searchstring found,
        printf("%s", note_buffer);
    return 1;
}

int find_user_note(int fd, int user_uid) {
int note_uid=-1;
unsigned char byte;
int length;
while(note_uid != user_uid) {
if(read(fd, &note_uid, 4) != 4) // Read the uid data.
return -1; // If 4 bytes aren't read, return end of file code.
if(read(fd, &byte, 1) != 1) // Read the newline separator.
return -1;
byte = length = 0;
while(byte != '\n') { // Figure out how many bytes to the end of line.
if(read(fd, &byte, 1) != 1) // Read a single byte.
return -1;
// If byte isn't read, return end of file code.
length++;
}
}
lseek(fd, length * -1, SEEK_CUR); // Rewind file reading by length bytes.
printf("[DEBUG] found a %d byte note for user id %d\n", length, note_uid);
return length;
}

int search_note(char *note, char *keyword) {
int i, keyword_length, match=0;
keyword_length = strlen(keyword);
if(keyword_length == 0) // If there is no search string,
return 1;
// always "match".
for(i=0; i < strlen(note); i++) { // Iterate over bytes in note.
if(note[i] == keyword[match]) // If byte matches keyword,
match++;
// get ready to check the next byte;
else {
//otherwise,
if(note[i] == keyword[0]) // if that byte matches first keyword byte,
match = 1; // start the match count at 1.
else
match = 0; // Otherwise it is zero.
}
if(match == keyword_length) // If there is a full match,
return 1;
// return matched.
}
return 0; // Return not matched.
}


```

included is output1.h
```

#include <stdlib.h>
// A function to display an error message and then exit
void fatal(char *message) {
    char error_message[100];
    
    strcpy(error_message, "[!!] Fatal Error ");
    strncat(error_message, message, 83);
    perror(error_message);
    exit(-1);
}

// An error-checked malloc() wrapper function
void *ec_malloc(unsigned int size) {
    void *ptr;
    ptr = malloc(size);
    if(ptr == NULL)
        fatal("in ec_malloc() on memory allocation");
    return ptr;
}

// Dumps raw memory in hex byte and printable split format
void dump(const unsigned char *data_buffer, const unsigned int length) {
    unsigned char byte;
    unsigned int i, j;
    for(i=0; i < length; i++) {
        byte = data_buffer[i];
        printf("%02x ", data_buffer[i]);    // Display byte in hex
        if(((i%16)==15) || (i==length-1)) {
            for(j=0; j < 15-(i%16); j++)
                printf(" ");
            printf("| ");
            for(j=(i-(i%16)); j <= i; j++) {    // Display printable bytes from line.
                byte = data_buffer[j];
                if((byte > 31) && (byte < 127))    // Outside printable char range
                    printf("%c", byte);
                else
                    printf(".");
            }
            printf("\n");    // End of the dump line (each line is 16 bytes)
        }    //End if
    }
}

```

and here is a file that I use to cat to SHELLCODE to eventually output "Hello, world!" but for now am only trying to produce a segmentation fault called helloworld1.s:
```

BITS 32            ; Tell nasm this is 32-bit code.

    call mark_below    ; Call below the string to instructions
    db "Hello, world!", 0x0a, 0x0d    ; with newline and carriage return bytes. 

mark_below:
; ssize_t write(int fd, const void *buf, size_t count);
  pop ecx    ; Pop the return address (string ptr) into ecx.
  mov eax, 4    ; Write syscall #.
  mov ebx, 1    ; STDOUT file descriptor
  mov edx, 15    ; Length of the string
  int 0x80    ; Do syscall: write(1, string, 14)

; void _exit(int status);
  mov eax, 1    ; Exit syscall #
  mov ebx, 0    ; Status = 0
  int 0x80    ; Do syscall: exit(0)

```

Here is another file that I use called getenvaddr.c
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[]) {
    char *ptr;

    if(argc < 3) {
        printf("Usage: %s <environment var> <target program name> \n", argv[0]);
        exit(0);
    }
    ptr = getenv(argv[1]);    /* Get environment variable location. */
    ptr += (strlen(argv[0]) - strlen(argv[2]))*2;    /* Adjust for program name */
    printf("%s will be at %p\n", argv[1], ptr);
}

```

I have already tried to compile notesearch.c using:

$ gcc -fno-stack-protector -o notesearch notesearch.c 

which compiles as it should. Then to try to produce the segmentation fault I use the following:

export SHELLCODE=$(cat helloworld1)

./getenvaddr SHELLCODE ./notesearch

./notesearch $(perl -e 'print "\xc6\xf9\xff\xbf"x40)

Which does not produce a segmentation fault but instead just finds a note and then exits the program. When I try to compile without using -fno-stack-protector it produces a stack smash detection which is not the outcome that we  want to get. 

I would appreciate any help. Thank you!

---

### Post by trent.josephsen on 2013-02-16
That's a lot of poorly formatted and sparsely commented code to poke through looking for whatever line you think should be causing a segfault, and then (of all things) try to figure out how to make it do so. And, good grief, code in a header file? Never mind. Looks like you're just trying to do some weird exploit anyway. Have fun.

---

### Post by Bachstelze on 2013-02-17
> **trent.josephsen said:**
> That's a lot of poorly formatted and sparsely commented code to poke through looking for whatever line you think should be causing a segfault, and then (of all things) try to figure out how to make it do so. And, good grief, code in a header file? Never mind. Looks like you're just trying to do some weird exploit anyway. Have fun.

From the name of the program, I suspect he's going through the book of [Erickson](http://www.amazon.com/dp/1593271441/).

But that's all I can say. :p Normally the goal is not to produce a segfault, it is to obtain a shell with the privileges of the user the program runs as.

---

### Post by dansofe0r on 2013-02-17
It is Erickson's book lol. It is from 2007 so many of the libraries that it uses have had their versions changed which has led to many issues that need fixing in order to keep going through the book's examples.

---

### Post by Bachstelze on 2013-02-17
You should use the provided Live CD (in VirtualBox if you do not want to be stuck in it. ;)).

---

### Post by dansofe0r on 2013-02-19
I should haha. I just wanted to get into using the methods in an updated environment but for learning purposes I suppose a cd boot is okay.

---

### Post by Bachstelze on 2013-02-20
> **dansofe0r said:**
> I should haha. I just wanted to get into using the methods in an updated environment but for learning purposes I suppose a cd boot is okay.

Try to get it to work in the Live CD first. ;) Then on a current system you will generally at least need to compile with [font=monospace]-fno-stack-protector[/font] and also [font=monospace]-z execstack[/font] if you want to execute code on the stack (which is what you want to do for most shellcodes).

---

