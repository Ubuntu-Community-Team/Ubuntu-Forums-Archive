---
title: "Beginners Programming Challenge 22"
date: 2011-08-18
forum: Programming Talk
---

### Post by ziekfiguur on 2011-08-18
With this challenge i'm going to try to get people to do some bit-fiddling, which means you will need to know how to use (at least some of)
the bitwise operators, and you will have to know something about how data is represented in your computer. At the same time i tried to come up with
 a challenge that is still quite beginner friendly and that shouldn't take too much time.

**The Challenge**
To create a program that can encode data to [_base64_]("https://secure.wikimedia.org/wikipedia/en/wiki/Base64"). Read the link for an explanation.

ubuntu by default comes with the base64 command, so testing your code should be easy, make sure to test with input of different sizes.

Note: I realize that it is possible to do this without using any of the bitwise operators. Unless your programming language of choice doesn't
support them, try to show that you know how to use them.

Extra points are for programs that can also decode and wrap the output lines (basically the same options the base64 programs has too) and
programs that support other, similar encodings like Base58, Base32 and Ascii85.

**Judging**
As usual judgement is based on if your code works and how readable it is. Another point of judgement will be how well your code works with (very)
large files.

---

### Post by Bachstelze on 2011-08-18
Obligatory Haskell. :) Yes, I know I'm not really a beginner, but no one ever does Haskell in those challenges anyway (and besides, I was a beginner at doing binary I/O and using the bitwise operators in Haskell :p). If you were going to do it, don't read this code.

```
import Data.Bits
import Data.Char
import System.Environment
import System.IO

-- Converts an Int between 0 and 63 to its representation in base64
base64Chr :: Int -> Char

-- Encodes the input String to base64
base64Enc :: String -> String

-- Writes the string passed in argument to the standard input, wrapping it
-- in lines of n characters
printBase64 :: String -> Int -> IO ()

base64Chr n = if n < 0 -- Invalid
                 then '#'
              else if n < 26 -- Uppercase alpha
                 then chr (ord 'A' + n)
              else if n < 52 -- Lowercase alpha
                 then chr (ord 'a' + n - 26)
              else if n < 62 -- Digit
                 then chr (ord '0' + n - 52)
              else if n == 62
                 then '+'
              else if n == 63
                 then '/'
              else '#' -- Invalid


-- Empty string
base64Enc []    = []

-- One-character string
base64Enc [i1]  = [o1, o2, '=', '=']
                  where o1 = base64Chr (shiftR (ord i1) 2)
                        o2 = base64Chr (shiftL (ord i1 .&. 3) 4)

-- Two-character string
base64Enc [i1, i2] = [o1, o2, o3, '=']
                     where o1 = base64Chr (shiftR (ord i1) 2)
                           o2 = base64Chr ((shiftL (ord i1 .&. 3) 4) .|.
                                           (shiftR (ord i2) 4))
                           o3 = base64Chr (shiftL (ord i2 .&. 15) 2)

-- Default (three or more character)
base64Enc s = [o1, o2, o3, o4] ++ base64Enc (drop 3 s)
              where o1 = base64Chr (shiftR (ord i1) 2)
                    o2 = base64Chr ((shiftL (ord i1 .&. 3) 4) .|.
                                    (shiftR (ord i2) 4))
                    o3 = base64Chr ((shiftL (ord i2 .&. 15) 2) .|.
                                    (shiftR (ord i3) 6))
                    o4 = base64Chr (ord i3 .&. 63)
                    [i1, i2, i3] = take 3 s


printBase64 [] _ = putStr ""
printBase64 s n  = do putStrLn (take n s)
                      printBase64 (drop n s) n

main = do args <- getArgs
          if null args || (args !! 0) == "-"
             -- Read from standard input
             then do hSetBinaryMode stdin True
                     s <- getContents
                     printBase64 (base64Enc s) 76

             -- Read from file
             else do ifile <- openBinaryFile (args !! 0) ReadMode
                     s <- hGetContents ifile
                     printBase64 (base64Enc s) 76
                     hClose ifile

```

Save as base64.hs and compile with

```
ghc --make base64.hs
```

Supports reading from a file and from standard input. If called with one argument, the argument is the name of the fileto read, or - to read from standard input. If no argument, reads from standard input. Wrapping length is hardcoded at 76 characters (default in base64 from the GNU coreutils). No error handling for file errors (e.g. non-existent or non-readable file), the Haskell runtime will print an informative error message anyway.

Gives the same result as base64, though performance is much less good on large files:

```

firas@aoba ~ % ls -lh /boot/initrd.img-2.6.38-11-generic 
-rw-r--r-- 1 root root 19M 2011-08-13 00:51 /boot/initrd.img-2.6.38-11-generic
firas@aoba ~ % time base64 /boot/initrd.img-2.6.38-11-generic > test1.txt 
base64 /boot/initrd.img-2.6.38-11-generic > test1.txt  0.10s user 0.30s system 92% cpu 0.434 total
firas@aoba ~ % time ./base64 /boot/initrd.img-2.6.38-11-generic > test2.txt
./base64 /boot/initrd.img-2.6.38-11-generic > test2.txt  11.39s user 0.90s system 99% cpu 12.317 total
firas@aoba ~ % diff test1.txt test2.txt 
firas@aoba ~ % 

```

---

### Post by Bachstelze on 2011-08-18
Or how about some assembly?

main.c:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define OUTPUT_LINE_LENGTH 76
#define INPUT_LINE_LENGTH  (((OUTPUT_LINE_LENGTH)*3)/4)

void usage(char*);
int base64enc(char*, unsigned char*, int);

void usage(char *s)
{
        fprintf(stderr, "Usage: %s [FILE]\n"
                        "If FILE is omitted or -, reads from the standard "
                        "input.\n", s);
        exit(EXIT_FAILURE);
}

int main(int argc, char **argv)
{
        if (argc > 2) {
                usage(argv[0]);
        }

        unsigned char ibuf[INPUT_LINE_LENGTH];
        char obuf[OUTPUT_LINE_LENGTH+1]; /* +1 for terminating null */

        FILE *ifile;
        if (argc == 1 || strcmp(argv[1], "-") == 0) {
                ifile = stdin;
        } else {
                ifile = fopen(argv[1], "r");
                if (ifile == NULL) {
                        perror("Could not open input file");
                        exit(EXIT_FAILURE);
                }
        }

        for (;;) {
                int bytes_read = fread(ibuf, 1, INPUT_LINE_LENGTH, ifile);
                if (bytes_read == 0) {
                        break;
                }
                int bytes_written = base64enc(obuf, ibuf, bytes_read);
                obuf[bytes_written] = '\0';
                puts(obuf);
        }
        fclose(ifile);
}

```

base64enc.S
```
.data
charmap:
        .long 0x44434241
        .long 0x48474645
        .long 0x4c4b4a49
        .long 0x504f4e4d
        .long 0x54535251
        .long 0x58575655
        .long 0x62615a59
        .long 0x66656463
        .long 0x6a696867
        .long 0x6e6d6c6b
        .long 0x7271706f
        .long 0x76757473
        .long 0x7a797877
        .long 0x33323130
        .long 0x37363534
        .long 0x2f2b3938

.text
.globl base64enc
        .type base64enc, @function

base64enc:

pushl   %ebp
movl    %esp, %ebp

# Callee-save registers
pushl   %ebx
pushl   %edi
pushl   %esi

# ebp-4 will be our temporary buffer
subl    $4, %esp

# eax is the return value, which is the number of bytes written to
# the output buffer.  Initialise it at 0.
movl    $0, %eax

# ecx is the number of bytes left to be read. It is the third parameter
# to the function, so we fetch it from ebp+16.
movl    16(%ebp), %ecx

# edi is the address of the input buffer
movl    12(%ebp), %edi

# esi is the address of the output buffer
movl    8(%ebp), %esi

# If %ecx is already non-positive, don't enter the loop at all.
andl    %ecx, %ecx
jle     endmainloop

mainloop:
addl    $4, %eax
movzbl  (%edi), %edx
movl    $0, %ebx

# More than one character?
cmpl    $1, %ecx
jle     nomorethanone
movzbl  1(%edi), %ebx
nomorethanone:
movb    %bl, -4(%ebp)

# First base64 character
shrl    $2, %edx
movzbl  charmap(%edx), %edx
movb    %dl, (%esi)

# Second base64 character
movzbl  (%edi), %edx
andl    $3, %edx
shll    $4, %edx
shrl    $4, %ebx
orl     %ebx, %edx
movzbl  charmap(%edx), %ebx
movb    %bl, 1(%esi)

# More than one character? (Yes, we must do the test twice.)
cmpl    $1, %ecx
jne     morethanone
movw    $0x3d3d, 2(%esi)
jmp     endmainloop
morethanone:

movzbl  -4(%ebp), %edx
movl    $0, %ebx

# More than two characters?
cmpl    $2, %ecx
jle     nomorethantwo
movzbl  2(%edi), %ebx
nomorethantwo:
movb    %bl, -4(%ebp)

# Third base64 character
andl    $15, %edx
shll    $2, %edx
shrl    $6, %ebx
orl     %ebx, %edx
movzbl  charmap(%edx), %edx
movb    %dl, 2(%esi)

# More than two characters? (Yes, again.)
cmpl    $2, %ecx
jne     morethantwo
movb    $0x3d, 3(%esi)
jmp     endmainloop
morethantwo:

# Fourth base64 character
movzbl  -4(%ebp), %edx
andl    $63, %edx
movzbl  charmap(%edx), %edx
movb    %dl, 3(%esi)

# Increment everything
addl    $3, %edi
addl    $4, %esi
subl    $3, %ecx

# Exit?
andl    %ecx, %ecx
jg      mainloop

endmainloop:

# Clean-up
addl    $4, %esp
popl    %esi
popl    %edi
popl    %ebx
popl    %ebp
ret

.size   base64enc, .-base64enc


```

And this Makefile:

```
CC=gcc
CFLAGS=-m32 -std=c99 -pedantic -Wall -Werror
ifdef DEBUG
	CFLAGS+=-g
endif
ASFLAGS=-m32
OBJECTS=main.o base64enc.o
OUTFILE=base64

$(OUTFILE): $(OBJECTS)
	$(CC) $(CFLAGS) -o $@ $+

clean:
	rm -f $(OUTFILE) $(OBJECTS)

```

Performance is comparable to base64 from coreutils:

```
firas@aoba base64 % make
gcc -m32 -std=c99 -pedantic -Wall -Werror   -c -o main.o main.c
gcc -m32   -c -o base64enc.o base64enc.S
gcc -m32 -std=c99 -pedantic -Wall -Werror -o base64 main.o base64enc.o
firas@aoba base64 % time base64 /boot/initrd.img-2.6.38-11-generic > test1.txt 
base64 /boot/initrd.img-2.6.38-11-generic > test1.txt  0.05s user 0.36s system 98% cpu 0.417 total
firas@aoba base64 % time ./base64 /boot/initrd.img-2.6.38-11-generic > test2.txt 
./base64 /boot/initrd.img-2.6.38-11-generic > test2.txt  0.15s user 0.35s system 90% cpu 0.550 total
firas@aoba base64 % diff test1.txt test2.txt 
firas@aoba base64 % 

```

I'm going to try and do it in MIPS assembly when I get my hands on my MIPS machine too. :p (Or maybe I should do a decoder...)

---

### Post by ziekfiguur on 2011-08-19
For some reason as doesn't recognize -m32 on my system, any ideas why this would be? its a 64bit system. It seems to work if i use `gcc -m32 base64enc.s main.c`' though.
Good commenting btw. This problem was actually one of the first i tried when i started learning assembly 2 years ago and when i read back my old code i have trouble understanding what happens. It probably has something to do with my lack of commenting :P

---

### Post by Bachstelze on 2011-08-19
> **ziekfiguur said:**
> For some reason as doesn't recognize -m32 on my system, any ideas why this would be? its a 64bit system. It seems to work if i use `gcc -m32 base64enc.s main.c`' though.

I'm on 64bit too, and it works fine. Do you get an error message?

---

### Post by ziekfiguur on 2011-08-19
This is what i get:
```
$ make
as -m32  -o base64enc.o base64enc.s
as: unrecognized option '-m32'
make: *** [base64enc.o] Error 1
```

So, if everyone else wants to try Bachstelzes code, if you get this error you can just use: ```
$ gcc -m32 -pedantic -Wall -Werror -std=c99 base64enc.s main.c
```

Edit: I just realized, i named the file base64enc.s instead of base64enc.S (note the capital S) I think when you use .S make doesn't realize it's a assembly file and still calls gcc instead of as, seeing that in your post make also uses gcc to build base64enc.S

---

### Post by Bachstelze on 2011-08-19
> **ziekfiguur said:**
> 
Edit: I just realized, i named the file base64enc.s instead of base64enc.S (note the capital S) I think when you use .S make doesn't realize it's a assembly file and still calls gcc instead of as, seeing that in your post make also uses gcc to build base64enc.S

Good catch. I didn't give the extension much thought. Apparently .S is for assembly that is supposed to be preprocessed with cpp yielding a .s, and .s for assembly which is to be assembled directly. So my guess is that since I had a .S, make realized it would have to both preprocess and assemble, and used gcc as a "shortcut" to perform both steps in one command.

---

### Post by unknownPoster on 2011-08-19
I'm not a beginner, but I just thought I would show off the "magic" of python. So don't judge this. :P

```

import base64

data = raw_input("Enter data to encode\n")

print base64.b64encode(data)

data = raw_input("Enter encoded data to decode\n")

print base64.b64decode(data)

```

base16 and base32 are equally trivial.

:P

---

### Post by Bachstelze on 2011-08-19
Oh, so impressive. I think I'm going to faint over how awesome that is.

---

### Post by The Cog on 2011-08-19
Oi! You just broke my sarcasmometer! Bent the needle right round!

---

### Post by stchman on 2011-08-19
Java solution:

[PHP]
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import javax.xml.bind.DatatypeConverter;

/*
 * @author BN
 */
public class Base64 {
    public static void main( String[] args ) {
        Base64 m = new Base64();
        m.convertToBase64();
        m.ConvertFromBase64();
    }
    
    public void convertToBase64() {
        BufferedReader input = new BufferedReader( new InputStreamReader( System.in ) );        
        System.out.print( "Enter an ASCII word to be converted to Base64 " );
        try {
            // get the ascii word from standard input
            String asciiWord = input.readLine();           
            
            // convert the ascii word into a base64 word and display
            String answer = DatatypeConverter.printBase64Binary( asciiWord.getBytes() );
            System.out.println( answer );
        } catch ( IOException ex ) {}
    }
    
    public void ConvertFromBase64() {
        BufferedReader input = new BufferedReader( new InputStreamReader( System.in ) );        
        System.out.print( "Enter a Base64 word to be converted to ASCII " );
        try {
            // get the base64 word from standard input
            String base64Word = input.readLine();

            // convert the byte[] into a readable String and display, note String constructor takes byte[]
            String answer = new String( DatatypeConverter.parseBase64Binary( base64Word ) );
            System.out.println( answer );
        } catch ( IOException ex ) {}        
    }
}
[/PHP]

---

### Post by Bachstelze on 2011-08-19
You missed the point. ;)

---

### Post by The Cog on 2011-08-19
Golang solution - reads from stdin
Pretty-much my first stab at this language so it took me ages. An index to the tutorials would have helped enormously.```
package main

import "os"


const dictionary = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/"



// This functions as an encoder, reading inch and writing outch
func encode(inch chan byte, outch chan byte) {
    var carry byte = 0
    var modin byte = 0  // track which byte of the triplet we're expecting
    var modout byte = 0 // track output byte count for line wrapping
    for byteIn := range inch {
        if modout > 75 {
            modout = 0
            outch <- '\r'
            outch <- '\n'
        }
        switch modin {
            case 0:
                outch <- dictionary[byteIn >> 2]
                carry = byteIn << 4
                modout += 1
            case 1:
                outch <- dictionary[(carry | (byteIn >> 4)) & 63]
                carry = byteIn << 2
                modout += 1
            case 2:
                outch <- dictionary[(carry | (byteIn >> 6)) & 63]
                outch <- dictionary[byteIn & 63]
                modout += 2
        }
        modin = (modin + 1) % 3
    }
    // clean up and finish off
    if modin > 0 {
        outch <- dictionary[carry & 63]
        outch <- '='
        if modin == 1 {
            outch <- '='
        }
    }
    outch <- '\r'
    outch <- '\n'
    close(outch)
}


// Print whatever comes out of the channel
func printout(bytes chan byte, finch chan int) {
    const bufsize = 1000
    var n int = 0
    var buf [bufsize]byte
    for b := range bytes {
        buf[n] = b
        n += 1
        // if n > bufsize { // Original code, off-by-one error overflows buf
        if n >= bufsize {    // Corrected code
            os.Stdout.Write(buf[0:n])
            n = 0
        }
    }
    if n > 0 {
        os.Stdout.Write(buf[0:n])
    }
    // tell main we're done
    finch <- 42
}


func main() {
    // create the comms channels
    chraw := make (chan byte)   // raw bytes to the encoder
    chenc := make (chan byte)   // encoded bytes from the encoder
    finch := make (chan int)    // finished signal from the printer
    // launch the encoder and printer
    go encode(chraw, chenc)
    go printout(chenc, finch)
    // squirt the raw bytes from stdin to the encoder
    const bufsize = 1000
    buf := make([]byte, bufsize)
    for { 
        n, err := os.Stdin.Read(buf)
        if err != nil {
            break
        }
        for i := 0 ; i < n ; i++ {
            chraw <- buf[i]
        }
    }
    close(chraw)
    // wait until the output has all been printed, or main exits and everything else dies
    <- finch
}


```

---

### Post by ziekfiguur on 2011-08-20
The Cog, I think there is something wrong with your solution, this is what i get:
```
$ 6g base64.go 
$ 6l base64.6 
$ ./6.out < base64.go
panic: runtime error: index out of range

runtime.panic+0xac /home/ziekfiguur/go/src/pkg/runtime/proc.c:1060
	runtime.panic(0x41da98, 0xf840001210)
runtime.panicstring+0xa3 /home/ziekfiguur/go/src/pkg/runtime/runtime.c:116
	runtime.panicstring(0x43c6ce, 0x0)
runtime.panicindex+0x25 /home/ziekfiguur/go/src/pkg/runtime/runtime.c:73
	runtime.panicindex()
main.printout+0x86 /tmp/base64.go:57
	main.printout(0xf8400119b0, 0xf840011960, 0x0, 0x0)
runtime.goexit /home/ziekfiguur/go/src/pkg/runtime/proc.c:178
	runtime.goexit()
----- goroutine created by -----
main.main+0xb7 /tmp/base64.go:79

goroutine 2 [1]:
runtime.gosched+0x5c /home/ziekfiguur/go/src/pkg/runtime/proc.c:603
	runtime.gosched()
runtime.chansend+0x3c7 /home/ziekfiguur/go/src/pkg/runtime/chan.c:223
	runtime.chansend(0xf8400119b0, 0x7f0f63f2af88, 0x0, 0x0, 0x0, ...)
runtime.chansend1+0x5b /home/ziekfiguur/go/src/pkg/runtime/chan.c:410
	runtime.chansend1(0xf8400119b0, 0x161)
main.encode+0xe1 /tmp/base64.go:23
	main.encode(0xf840011000, 0xf8400119b0, 0x0, 0x0)
runtime.goexit /home/ziekfiguur/go/src/pkg/runtime/proc.c:178
	runtime.goexit()
----- goroutine created by -----
main.main+0x96 /tmp/base64.go:78

goroutine 1 [1]:
runtime.gosched+0x5c /home/ziekfiguur/go/src/pkg/runtime/proc.c:603
	runtime.gosched()
runtime.chansend+0x3c7 /home/ziekfiguur/go/src/pkg/runtime/chan.c:223
	runtime.chansend(0xf840011000, 0x7f0f63f29f40, 0x0, 0x3e8, 0x7f0f63f29f38, ...)
runtime.chansend1+0x5b /home/ziekfiguur/go/src/pkg/runtime/chan.c:410
	runtime.chansend1(0xf840011000, 0xf840000068)
main.main+0x1a1 /tmp/base64.go:89
	main.main()
runtime.mainstart+0xf /home/ziekfiguur/go/src/pkg/runtime/amd64/asm.s:77
	runtime.mainstart()
runtime.goexit /home/ziekfiguur/go/src/pkg/runtime/proc.c:178
	runtime.goexit()
----- goroutine created by -----
_rt0_amd64+0x8e /home/ziekfiguur/go/src/pkg/runtime/amd64/asm.s:64
```
I used 6g to compile your program, but i don't know Go and i don't really understand where exactly it seems to go wrong...

---

### Post by The Cog on 2011-08-20
Stupid stupid stupid! 
Off by one error filling the buffer in the output printing routing. Only triggered with outputs > 1k chars.
Line 59, please replace:
```
        if n > bufsize {
```
with 
```
        if n >= bufsize {
```

I've corrected the code in post #13 in case anyone else copies it.

---

### Post by JDShu on 2011-08-20
This was a great exercise for me to start learning Java. Ugly and not many features, but nevertheless I'd appreciate any advice on how to improve my code.

```

import java.io.*;

class Base64App {
    public static void main(String[] args) throws IOException{
    if(args.length == 0) {
        System.out.println("format: Base64App {encode|decode} {input file} {output file if decoding}");
    }
    else if (args[0].equals("encode")) {
        encode(args);
    }
    else if (args[0].equals("decode")) {
        decode(args);
    }
    else {
        System.out.println("First argument must be 'encode' or 'decode'");
    }
    }

    private static void encode(String[] args) {
    try {
        System.out.print(Base64Converter.encode(args[1]));
    }
    catch (Exception e) {
        System.out.println("format: Base64App encode {input file}");
    }
    }

    private static void decode(String[] args) {
    try {
        Base64Converter.decode(args[1], args[2]);
    }
    catch (Exception e){
        System.out.println("format: Base64App decode {input file} {output file}");
    }
    }
}

class Base64Converter {
    private static int i = 0;
    private static int output_place = 0;
    
    private static StringBuffer result = new StringBuffer();
    public static String encode(String input_file) throws IOException {
    int current_ch;
    int previous_ch = 0;
    FileInputStream in = new FileInputStream(input_file);
    while ((current_ch = in.read()) > -1) {
        switch (i%3) {
        case 0: 
        append(int2base64(current_ch>>>2));
        break;
        case 1:
        append(int2base64(((previous_ch & 3)<<4) | (current_ch>>>4)));
        break;
        case 2:
        append(int2base64(((previous_ch & 15)<<2) | (current_ch>>>6)));
        append(int2base64(current_ch & 63));
        break;
        }
        previous_ch = current_ch;
        i++;
    }
    switch(i%3) {
    case 1:
        append(int2base64(((previous_ch & 3)<<4)));
        append('=');
        append('=');
        break;
    case 2:
        append(int2base64(((previous_ch & 15)<<2)));
        append('=');
        break;
    }
    result.append('\n');
    return result.toString();
    }

    public static void decode(String input_file, String output_file) throws IOException {
    int current_ch;
    int previous_ch = 0;
       
    FileReader f = new FileReader(input_file);
    FileOutputStream output = new FileOutputStream(output_file);
    while ((current_ch = f.read()) > -1) {

        if (current_ch == '=') {
        break;
        }
        else if(current_ch == '\n') {
        continue;
        }

        current_ch = base642int(current_ch);
        
        switch(i%4) {
        case 0: break;
        case 1:
        output.write((previous_ch << 2) | (current_ch >>> 4));
        break;
        case 2:
        output.write(((previous_ch & 15) << 4 )|(current_ch >>> 2));
        break;
        case 3:
        output.write(((previous_ch & 3) << 6) | current_ch);
        break;
        }
        previous_ch = current_ch;
        i++;
    }
    }
    
    private static void append(char data) {
    output_place++;
    result.append(data);
    if (output_place % 76 == 0) {
        result.append('\n');
    }
    }

    private static char int2base64(int i) {
        if (i < 26){
        return (char)((int)'A' + i);
    }
    else if (i < 52) {
        return (char)((int)'a' + (i-26));
    }
    else if (i < 62) {
        return (char)((int)'0' + (i-52));
    }
    else if (i == 62) {
        return '+';
    }
    else {
        return '/';
    }
    }
    
    private static int base642int(int i) {
    char c = (char)i;
    if (c >= 'A' && c <= 'Z') {
        return (c-'A');
    }
    else if (c >= 'a' && c <= 'z') {
        return (c-'a'+26);
    }
    else if (c >= '0' && c <= '9') {
        return (c-'0'+52);
    }
    else if (c == '+'){
        return 62;
    }
    else {
        return 63;
    }
    }
}

```Hmmm, it doesn't indent in the post the way I see it in my editor apparently, can anybody explain?

---

### Post by Bachstelze on 2011-08-20
How are you compiling this code? Because javac throws 5 errors.

---

### Post by JDShu on 2011-08-20
Wow, that was pretty stupid of me. I had a random case statement when I tried to change the if-else to case but then realized it wasn't that simple. Fixed now.

---

### Post by Bachstelze on 2011-08-20
Your program works correctly on ASCII files, but not on binary files. I am not big on Java, so check your I/O functions, maybe they're emant to be used on ASCII data only.

---

### Post by JDShu on 2011-08-20
Thanks, I didn't realize base64 worked equally well on binary files. Changed the stream class.

---

### Post by Bachstelze on 2011-08-20
> **JDShu said:**
> Thanks, I didn't realize base64 worked equally well on binary files.

That's the whole point. ;) For ASCII files, you don't need base64 at all, you can just send them as is in e.g. an email.

OK, now it works. Two things:

1. You don't need to instantiate Base64Converter.
2. The output is not pretty right now, try to wrap it in lines of acceptable length and add a newline at the end (as base64 does).

---

### Post by JDShu on 2011-08-20
> **Bachstelze said:**
> That's the whole point. ;) For ASCII files, you don't need base64 at all, you can just send them as is in e.g. an email.


Yeah XD feel stupid now.

> 
OK, now it works. Two things:

1. You don't need to instantiate Base64Converter.
2. The output is not pretty right now, try to wrap it in lines of acceptable length and add a newline at the end (as base64 does).

Again, thanks :D I realized that the above two points were related such that I don't need crazy refactoring either, which prevented me from implementing the second point. I'll update my code in the next few minutes.

---

### Post by b0whunter on 2011-08-23
I guess im even more a beginner than the beginner standard for these challenge, havent been able yet to write my own encoding/decoding functions, but im still trying. Heres what I have done using the Base64 module, until i can write my own :s

```

#!/usr/bin/perl -w

$num_args = $#ARGV + 1;
$option=$ARGV[0];
$string_file_flag=$ARGV[1];
$file=$ARGV[2];
$dest_file=$ARGV[3];

# Functions
sub helptxt
{
  print "\nUsage:\tchallenge22.pl [options] [-s] string\n";
  print "\tchallenge22.pl [options] [-f] filename destination_filename\n\n";
  print "Options: [-b64e] base64 encode\n";
  print "         [-b64d] base64 decode\n";
  exit;
}

sub b64e_string
{
  use MIME::Base64;
  $encoded = encode_base64($file);
  print "\"$file\" encoded in base64 is:\n$encoded";
}

sub b64e_file
{
  use MIME::Base64 qw(encode_base64);
    
  open(FILE, "+<$file") or die "$!";
  open(ENCODED_FILE, ">$dest_file") or die "$!";
  while (read(FILE, $buf, 60*57)) {
    print ENCODED_FILE encode_base64($buf); 
  }
  print "Encoded $file into $dest_file\n";  
}

sub b64d_string
{
  use MIME::Base64;
  $decoded = decode_base64($file);
  print"$file decoded with base64 is:\n$decoded\n";
}

sub b64d_file
{
  use MIME::Base64 qw(decode_base64);
    
  open(FILE, "+<$file") or die "$!";
  open(DECODED_FILE, ">$dest_file") or die "$!";
  while (read(FILE, $buf, 60*57)) {
    print DECODED_FILE decode_base64($buf); 
  }
  print "Decoded $file into $dest_file\n";  
}

# main

# quit unless we have the minimum number of command-line args
if ($num_args < 3) {
  &helptxt;
}    

# Encode a single word string in base64
elsif ($option eq "-b64e"&& $string_file_flag eq "-s") {
  &b64e_string;
}

# Encode a file in base64
elsif ($option eq "-b64e" && $string_file_flag eq "-f") {
  if ($num_args < 4) {
    &helptxt;
  }      
  else {
    &b64e_file;
  }
}

# Decode a base64 string
elsif ($option eq "-b64d" && $string_file_flag eq "-s") {
  &b64d_string;
}

# Decode a base64 file
elsif ($option eq "-b64d" && $string_file_flag eq "-f") {
  if ($num_args < 4) {
    &helptxt;
  }      
  else {
    &b64d_file;
  }
}

else {
 &helptxt;
}    
```

---

### Post by red_Marvin on 2011-08-25
gforth variant:

```

\ outputs the proper representation of a 0..63 integer
: output-char
    dup 26 <
    if
        65 +
    else
        dup 52 < if
            71 +
        else
            dup 62 < if
                4 -
            else
                dup 62 = if
                    drop 43
                else
                    drop 47
                then
            then
        then
    then
    emit
;

\ takes an address and a length (1..3) and converts and outputs the b64 representation
: b64-print
    swap
    over 1 >= if
        dup c@ dup 252 and 2 rshift
        output-char
        3 and 4 lshift

        2 pick 2 >= if
            over char+ c@ swap over 240 and 4 rshift or
            output-char
            15 and 2 lshift

            rot 3 = if
                over 2 chars + c@ swap over 192 and 6 rshift or
                output-char
                63 and output-char
            else
                output-char
                61 emit
            then

        else
            output-char
            61 dup emit emit
        then
    then
    drop
;

\ reads from stdin and outputs the bytes, tries to read 3 bytes at a time
\ converting them and stopping the loop if <3 bytes were read
: b64-stdio-loop
    3 chars allocate throw dup 3
    begin
        2dup stdin read-file 0= over 0<> and while
        2 pick swap
        b64-print
    repeat
    2drop drop
    free throw
    cr
;

b64-stdio-loop
bye
```

example run:
**echo some text | gforth b64.fs**
*c29tZSB0ZXh0Cg==*

---

### Post by Queue29 on 2011-09-05
Another Go solution...

[PHP]
package base

import "fmt"
import "math"
import "os"

const B64 = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/"

func Encode_it(input []byte, width int) string {
	nb := int(math.Ceil((float64(len(input)) * 8.0) / 6.0))
	nnl := 2*(nb/width) + 1 // rough estimate of # newlines
	output := make([]byte, nb+nnl+2, nb+nnl+2)
	ib := -1
	bb := byte(0x00)
	ii := 0 // takes into account newlines
	for i := 0; i < nb; i++ {
		if width != 0 && i%width == 0 && i != 0 {
			output[ii] = '\n'
			ii++
		}
		switch i % 4 {
		case 0:
			ib++
			bb = input[ib]
			output[ii] = B64[((bb & 0xFC) >> 2)]

		case 1:
			old_bb := bb
			ib++
			if ib < len(input) {
				bb = input[ib]
				output[ii] = B64[((old_bb&0x03)<<4)|((bb&0xF0)>>4)]
			} else {
				output[ii] = B64[((old_bb & 0x03) << 4)]
				ii++
				output[ii] = '='
				ii++
				output[ii] = '='
			}

		case 2:
			old_bb := bb
			ib++
			if ib < len(input) {
				bb = input[ib]
				output[ii] = B64[(((old_bb & 0x0F) << 2) | ((bb & 0xC0) >> 6))]
			} else {
				output[ii] = B64[((old_bb & 0x0F) << 2)]
				ii++
				output[ii] = '='
			}

		case 3:
			output[ii] = B64[(bb & 0x3F)]
			if ib >= len(input) {
				ii++
				output[ii] = '='
			}
		}
		ii++
	}
	return string(output[0:ii])
}

func Decode_it(input []byte, ignore_garbage bool) string {
	nb := int(math.Ceil((float64(len(input)) * 6.0) / 8.0))
	output := make([]byte, nb, nb)
	oi := -1
	m := gen_decode_map()
	i := -1
	for _, n := range input {
		i++
		// check for garbage, act accordingly
		if n == '\n' { // || n == '\r' {
			i--
			continue // just skip it
		} else if (n >= 'a' && n <= 'z') || (n >= 'A' && n <= 'Z') || (n >= '0' && n <= '9') || (n == '+') || (n == '/') {
			// act normal
		} else if int(n) == int('=') {
			break // actually stop
		} else {
			if ignore_garbage {
				continue
			} else {
				fmt.Printf("Invalid encoding detected: '%v'\n", string(n))
				os.Exit(-1)
			}
		}
		// decode all the things
		z := byte(m[int(n)])
		switch i % 4 {
		case 0:
			oi++
			output[oi] = z << 2

		case 1:
			output[oi] |= ((z & 0x30) >> 4)
			oi++
			output[oi] = ((z & 0x0F) << 4)

		case 2:
			output[oi] |= ((z & 0x3C) >> 2)
			oi++
			output[oi] = ((z & 0x03) << 6)

		case 3:
			output[oi] |= (z & 0x3F)
		}

	}

	if output[oi] == 0 {
		oi--
	}
	return string(output[0:oi+1])
}

func gen_decode_map() map[int]int {
	m := make(map[int]int, 26*2+2)
	for b := 'A'; b <= 'Z'; b++ {
		m[b] = b - 'A'
	}
	for b := 'a'; b <= 'z'; b++ {
		m[b] = b - 'a' + 26
	}
	for b := '0'; b <= '9'; b++ {
		m[b] = b - '0' + 52
	}
	m['+'] = 62
	m['/'] = 63
	m['='] = -1
	return m
}

[/PHP]


```
[22]$ time cat /boot/initrd.img-2.6.39-2-amd64 | base64 > test1.txt

real	0m0.069s
user	0m0.036s
sys	0m0.036s
[22]$ time cat /boot/initrd.img-2.6.39-2-amd64 | ./base64 > test2.txt

real	0m0.168s
user	0m0.128s
sys	0m0.048s
[22]$ diff test1.txt test2.txt 
[22]$ 
```




Updated with decode functionality. I'm gonna test it some more and then stick it in /usr/bin/base64
Updated again with bugfix and ability to read input file instead of just using stdin

---

### Post by ziekfiguur on 2011-09-17
Well, it seems like there aren't going to be a lot more entries. I'm going to give it one more week, and then i'll judge the solutions.

---

### Post by ziekfiguur on 2011-10-01
First of all, sorry for the delay. 

As the winner of this challence i have chosen **red_Marvin** for his gforth variant 
which i found to be surprisingly easy to read (even though I don't really know forth). 

One word to some of the other programmers: A lot of you store the output in a 
string or some other kind of growing buffer. When processing very large files this 
will result in very high memory usase, and every time the buffer runs out of space 
there is a chance it will have to be reallocated and copied to another location in 
memory. If you just output after every so many bytes your memory usage stays the 
same no matter how big your input and you won't lose time unnecessarily copying
output around.

---

### Post by red_Marvin on 2011-10-05
I am both flattered and a little worried that my forth code of all things of all could be considered readable (:
I have some labs and exams coming up the next weeks and will not have time to
organize a challenge for a couple of weeks, if somebody has an idea for a challenge
you can put it up, otherwise I will try to come up with something as soon as I get more
time.

---

### Post by schauerlich on 2011-10-27
> **red_Marvin said:**
> I am both flattered and a little worried that my forth code of all things of all could be considered readable (:
I have some labs and exams coming up the next weeks and will not have time to
organize a challenge for a couple of weeks, if somebody has an idea for a challenge
you can put it up, otherwise I will try to come up with something as soon as I get more
time.

Any news on a new challenge?

---

### Post by cgroza on 2011-10-27
> **schauerlich said:**
> Any news on a new challenge?
I can't wait for another one. I got a some knowledge and a few languages in my toolbox and can't wait to use them. :D :D :D

---

### Post by red_Marvin on 2011-10-27
I was approached two weeks ago by Bodsda who offered that the beginners
team could take care of the next challenge and I gave the go ahead.
There were some ideas for topics for the challenge, but the beginners
team has other responsibilities I assume, which could account for the delay.

---

### Post by jerenept on 2011-11-01
> **red_Marvin said:**
> I was approached two weeks ago by Bodsda who offered that the beginners
team could take care of the next challenge and I gave the go ahead.
There were some ideas for topics for the challenge, but the beginners
team has other responsibilities I assume, which could account for the delay.

I do hope they hurry.

---

### Post by schauerlich on 2011-11-01
If necessary, I could probably run the challenge.

---

### Post by Bodsda on 2011-11-20
Please accept my sincerest apologies for the delay in getting the next challenge up. I'm am writing it up at the moment, and will post the link here when it's ready.

EDIT: Challenge up - [http://ubuntuforums.org/showthread.php?t=1883907](http://ubuntuforums.org/showthread.php?t=1883907)

Bodsda
Ubuntu Beginners Team

---

