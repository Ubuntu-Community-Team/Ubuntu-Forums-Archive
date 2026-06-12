---
title: "Is there a Linux application that can compare two binary files?"
date: 2007-01-25
forum: Programming Talk
---

### Post by jbus on 2007-01-25
What I need is a hex editor type application that can take two binary files and show the difference between the two files. Does such an application exist for Linux?

---

### Post by lnostdal on 2007-01-25
[http://www.daemonology.net/bsdiff/](http://www.daemonology.net/bsdiff/)

sudo aptitude search bsdiff

edit:
uhm .. or no; bsdiff isn't quite what you're looking for i think .. after some googling this turned up:

[http://www.dettus.net/dhex/](http://www.dettus.net/dhex/)

..i haven't tried it though..

edit2:
ok, just tried it .. lol ..  had to apt down ncurses-dev first then make a small change in the Makefile before it compiled .. it seems to work

---

### Post by jbus on 2007-01-25
> **lnostdal said:**
> [http://www.daemonology.net/bsdiff/](http://www.daemonology.net/bsdiff/)

sudo aptitude search bsdiff

edit:
uhm .. or no; bsdiff isn't quite what you're looking for i think .. after some googling this turned up:

[http://www.dettus.net/dhex/](http://www.dettus.net/dhex/)

..i haven't tried it though..

I don't think bsdiff will work for me, but I'll check if there any good documentation for using it. I did try fldiff, but it doesn't work with binary files. A hex editor that could open two files and show the differences/similarities would be ideal. I may have to look at win32 applications that I could run under WINE for this.

---

### Post by jbus on 2007-01-25
Thanks for the heads up on dhex... I'll try it out.

---

### Post by phossal on 2007-01-25
You can't possibly be up to any good using a tool like *that.* Why would you want to look for changes in the hex of two binary files? :D

---

### Post by jbus on 2007-01-25
> **phossal said:**
> You can't possibly be up to any good using a tool like *that.* Why would you want to look for changes in the hex of two binary files? :D

Just some research O:)

---

### Post by Grey on 2007-01-25
Actually, there are legitimate uses for such things, if you are doing some low level development of binary formats.  I wrote a database application once that did low level changes to a binary file.  I simply used a hex editor to do the job, but a hex differ might have been useful in that case.

But yeah, I agree he's up to no good.  :P  (I can't really help out though, as I don't know of any such tools.  All I know is that ghex chokes if you feed it a really large file).

---

### Post by naylorjs on 2007-01-25
You could always use cmp(1), it's been a part of UNIX for a very long time indeed.

Jonathan

---

### Post by Wybiral on 2007-01-25
Yeah, you could probably write a small program to read byte-by-byte and point out all of the bytes which are different...

---

### Post by phossal on 2007-01-25
> **Wybiral said:**
> Yeah, you could probably write a small program to read byte-by-byte and point out all of the bytes which are different...

You haven't *written* one of those yet? Of all people, I would expect you to be to *provide it.* lol This thread might turn into the biggest collection of deviants yet.

I recommend visiting [OpenRCE]("http://openrce.org"). You're likely to find what you're looking for there, or find someone who can help you help yourself. :D

---

### Post by Wybiral on 2007-01-25
ha ha ha, I have now... It only took a minute to type out and I figure it will come in handy for me too.

Just compile this with c++ and execute it with "./a.out filea fileb" as parameters... It will show the hex dump of file A on the left, the hex dump of file B on the right, and the difference between them in the center. Any bytes that aren't the same will be replaced by "__" then all you have to do is look at that byte in fileA and fileB for the difference.

```

#include <iostream>
#include <fstream>
#include <iomanip>

using namespace std;

// Read unsigned char (byte)
unsigned char readByte(ifstream &thisFile){
	char buffer;
	thisFile.get(buffer);
	return (unsigned char)buffer;
}

int main(int argc, char** argv)
{
   ifstream binFileA(argv[1]);
   ifstream binFileB(argv[2]);

   int offset = 0;
   unsigned char byteA;
   unsigned char byteB;

   cout << hex;

   while(!binFileA.eof() && !binFileB.eof())
   {
      // Display file A
      for(int i=0; i<6; i++)
      {
         byteA = readByte(binFileA);
         cout << setw(3) << (int)byteA << " ";
      }

      cout << "|  |";

      // Display both files with "__" as difference
      binFileA.seekg(-6, ios::cur);
      for(int i=0; i<6; i++)
      {
         byteA = readByte(binFileA);
         byteB = readByte(binFileB);
         if(byteA != byteB){
            cout << " __ ";
         }
         else
         {
            cout << setw(3) << (int)byteA << " ";
         }
      }

      cout << "|  |";

      // Display file B
      binFileB.seekg(-6, ios::cur);
      for(int i=0; i<6; i++)
      {
         byteB = readByte(binFileB);
         cout << setw(3) << (int)byteB << " ";
      }

      cout << endl;
   }

   binFileB.close();
   binFileB.close();
}

```

BTW, it's easiest to redirect the output to a file, so use this when you execute is "./a.out fileA fileB>compareFile"

And it will send it all to "compareFile"

---

### Post by jblebrun on 2007-01-25
Hmm... maybe this will turn into a programming challenge thread ;-)

---

### Post by Wybiral on 2007-01-25
> **jblebrun said:**
> Hmm... maybe this will turn into a programming challenge thread ;-)

lol, well I do a lot of work with binary files too and I've never really thought about using a technique like this. Plus it was pretty easy to write, it's just comparing bytes.

---

### Post by phossal on 2007-01-25
Perl has a module for it. I've just used that. For some of the work I've done, it's not helpful though. Reproducing what should be the same binary file results in changes do to compression and encryption from the target. It would be helpful for something simple.

---

### Post by ghostdog74 on 2007-01-25
> **jbus said:**
> What I need is a hex editor type application that can take two binary files and show the difference between the two files. Does such an application exist for Linux?

you can use cmp , coupled with the -l switch to see the results.

---

### Post by Wybiral on 2007-01-25
I just tried cmp and it does work pretty well. But it outputs decimal bytes instead of hex bytes. They should really make a hex flag for cmp!

---

### Post by ghostdog74 on 2007-01-25
there is also hexdump utility. I have not tried but i am sure it can done somehow.
[here]("http://256.com/gray/docs/misc/hexdump_manual_how_to.html")

---

### Post by lingnoi on 2007-01-26
Maybe I'm missing something here but can't you just do an MD5 comparison between the two files? Or are you looking for the actual differences?

---

### Post by amo-ej1 on 2007-01-26
For a byte level diff i tend to abuse the following applications:
```

hexdump -C file1 > file1.txt
hexdump -C file2 > file2.txt

diff file1.txt file2.txt 


```

---

### Post by jblebrun on 2007-01-27
Ok, so I have a question. I haven't really used any of these binary differencing tools/libraries. Consider a case like this:

File 1:
01 45 6a 89 12 46 78 99

File 2:
45 6a 89 12 45 ff 78 99

Do the differencing tools have a method for reporting a "missing" or "added" byte?

Showing how file 2 is different from file 1 would be:
1 -01 
5 -46 +45
6 +ff

---

### Post by Wybiral on 2007-01-27
I don't think so... However you do bring up a very interesting feature that could be added to a binary differing tool... Especially with assembly... That would probably be very helpful!

Good idea.

This inspires me to work on a small toolkit for dealing with binary files...

jblebrun, do you mind if I steal your idea?

---

### Post by jblebrun on 2007-01-27
> **Wybiral said:**
> I don't think so... However you do bring up a very interesting feature that could be added to a binary differing tool... Especially with assembly... That would probably be very helpful!

Good idea.

This inspires me to work on a small toolkit for dealing with binary files...

jblebrun, do you mind if I steal your idea?

Go for it! I stole it from the way text diffing works, anyway. If you do a diff on a text file, it can detect inserted or removed lines... I just transfered that concept to individual bytes. I never come up with my own ideas... I just shuffle other people's ideas around ;-)

---

### Post by Lux Perpetua on 2007-01-27
> **jblebrun said:**
> Ok, so I have a question. I haven't really used any of these binary differencing tools/libraries. Consider a case like this:

File 1:
01 45 6a 89 12 46 78 99

File 2:
45 6a 89 12 45 ff 78 99

Do the differencing tools have a method for reporting a "missing" or "added" byte?

Showing how file 2 is different from file 1 would be:
1 -01 
5 -46 +45
6 +ffThat problem has a name: "edit distance." The edit distance between two strings is the minimum number of character insertions, deletions, and mutations required to transform one into the other. IIRC, computational biologists make good use of this to compare DNA sequences.

**edit:** As a workaround, you can use a combination of diff and hexdump to detect inserted and deleted bytes:
> hexdump -e "1 1 \"%02x\n\"" file1 > temp1
hexdump -e "1 1 \"%02x\n\"" file2 > temp2
diff temp1 temp2

---

### Post by jblebrun on 2007-01-27
> **Lux Perpetua said:**
> That problem has a name: "edit distance." The edit distance between two strings is the minimum number of character insertions, deletions, and mutations required to transform one into the other. IIRC, computational biologists make good use of this to compare DNA sequences.


Thanks for giving me the official name for that. Defining a metric like edit distance makes the problem much more clear! 

I'm gonna guess that you recalled correctly: if you ask me, it sounds like a problem that's 100% applicable to DNA.

---

### Post by Scott Rose on 2007-01-28
The answer sort of depends what you want to know about the files, and how large they are. 

If all you care about is whether they differ at all, then use the md5sum program to compute a hash of each file, and compare the hashes.

diff will compare binary files, but like the md5sum approach only tells you if they differ.

cmp will- if called with -l- tell you where and how the files differ.

---

### Post by wangrui on 2008-03-09
I need to compare very large files. Which need several hour. diff don't print any progress. I wrote a very simple java program to do the thing.

```

import java.io.BufferedInputStream;
import java.io.File;
import java.io.FileInputStream;

public class Test {

	public static void main(String[] args) throws Exception {
		String name = "backup.part1.rar";
		File file1 = new File("/home/bak/1/" + name);
		File file2 = new File("/mnt/" + name);
		java.io.BufferedInputStream fi1 = new BufferedInputStream(
				new FileInputStream(file1));
		java.io.BufferedInputStream fi2 = new BufferedInputStream(
				new FileInputStream(file2));
		byte[] bs1 = new byte[1024 * 1024];
		byte[] bs2 = new byte[1024 * 1024];
		long pos = 0;
		while (true) {
			System.out.format("%,d\n", pos);
			int len1 = fi1.read(bs1);
			int len2 = fi2.read(bs2);
			if (len1 != len2)
				throw new Error();
			if (len1 < 0)
				break;
			for (int i = 0; i < bs1.length; i++) {
				if (bs1[i] != bs2[i]) {
					System.out.println(pos + i);
					throw new Error();
				}
			}
			pos += len1;
		}
		fi1.close();
		fi2.close();
	}
}

```

---

### Post by cb951303 on 2008-03-10
I recently needed to compare binary files to reverse engineer a homebrew file format. What I needed was a program to find big blocks that are same in each file. For binary, a line by line comparison like diff doesn't mean much. But then again, it may be what you need :)

---

### Post by Endolith on 2008-07-11
Edit and compare giant binary files with lfhex

[http://www.linux.com/feature/135690](http://www.linux.com/feature/135690)

(Edit: After installing 80 MB of dependencies, it still won't install.  I give up.)


My application is two almost-identical .wav files that I created a long time ago and stored in different places.  They are not binary-equal, though, so some errors must have occurred in transmission or storage.  I want to see if I can figure out which is the original.  :)

```
cmp -l Untitled.wav Untitled2.wav 
  4973185 125 135
 93124225 155 145
 93212289 361 371
100802177 274 264

```

So they only differ in four places, by single bits?

---

### Post by fie on 2009-02-18
VBINDIFF(1)                                                                               Christopher J. Madsen                                                                               VBINDIFF(1)

NAME
       vbindiff - hexadecimal file display and comparison

SYNOPSIS
       vbindiff file1 [ file2 ]

DESCRIPTION
       Visual Binary Diff (VBinDiff) displays files in hexadecimal and ASCII (or EBCDIC).  It can also display two files at once, and highlight the differences between them.  Unlike diff, it works well with large files (up to 4 GB).

:wink:

---

### Post by Krupski on 2009-02-20
> **jbus said:**
> What I need is a hex editor type application that can take two binary files and show the difference between the two files. Does such an application exist for Linux?

Hey... look at this thread. It *might* be what you need.

[http://ubuntuforums.org/showthread.php?t=1075459](http://ubuntuforums.org/showthread.php?t=1075459)

-- Roger

---

### Post by Alasdair on 2009-02-20
Have you tried using vbindiff? It's in the Ubuntu repositories and works very well.

Edit: Looks like it's already been mentioned, I should really read the whole thread more throughly before replying...

---

### Post by nobodysbusiness on 2009-05-03
Was just looking at a problem that needed this, and found this little command-line that gives the number of differing bytes between two files (from commandlinefu):
cmp -l file1 file2 |wc -l

Then just use "ls -l" to get the filesize in bytes, and you get your percentage.

---

### Post by soltanis on 2009-05-03
Why not do

```

cat f1 | od -x > hex1 && cat f2 | od -x > hex2
diff hex1 hex2

```

?

---

### Post by trahojen on 2009-08-24
Upon reading this thread, I delved into my old backup discs and found this little utility I wrote while being stuck in the world of Windows. It does what *cmp -l*, except it will also display the *difference in value*.

Especially useful if the value change is known, but the location isn't.

Invoked as follows: ```
bcmp file1 file2
``` where file1 and file2 are binary files of equal size.

Its' output is something like this for every difference it finds:
```
Difference at 0x6C14.
        file 1:    0x0D    013
        file 2:    0xFE    254
Difference in numbers: +241
```And here is the code:
```

/*
    Author:    Samuel Rydén, trahojen (at, no abuse) gmail.com
    Copyright: 2002, 2009
    Purpose:   To compare two binary files of equal size, and display
               differences in BYTES in a helpful matter for further
               processing.

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
*/

#include <stdio.h> 
#include <stdlib.h> 
 
void fp_cleanup(FILE** f) 
{ 
    int c; 
    for (c = 0; c < 2; c++) 
    { 
        if (f[c] != NULL) 
        { 
            fclose(f[c]); 
        } 
    } 
    free(f); 
}

void usage()
{
    printf("Usage: bcmp file1 file2\n");
} 
 
int main(int argc, char** argv) 
{ 
    FILE** file; 
    long len[2]; 
    unsigned int t[2]; 
    int c; 
 
    if (argc < 3) 
    {
        usage(); 
        return 1; 
    } 
     
    file = (FILE**) calloc(2, sizeof(FILE *)); 
 
    for (c = 0; c < 2; c++) 
    { 
        file[c] = fopen(argv[c + 1], "rb"); 
        if (file[c] == NULL) 
        { 
            fprintf(stderr, "Unable to open %s.\n", argv[c + 1]); 
            fp_cleanup(file); 
            return 1; 
        } 
        fseek(file[c], 0, SEEK_END); 
        len[c] = ftell(file[c]); 
        fseek(file[c], 0, SEEK_SET); 
        len[c] -= ftell(file[c]); 
    } 
 
    if (len[0] != len[1]) 
    { 
        fprintf(stderr, "Error: File lengths are not equal.\n"); 
        fp_cleanup(file); 
        return 1; 
    } 
 
    for(c = 0; c < len[0]; c++) 
    { 
        t[0] = fgetc(file[0]); 
        t[1] = fgetc(file[1]); 
 
        if (t[0] != t[1]) 
        { 
            fprintf(stdout, "Difference at 0x%04X.\n", c); 
            fprintf(stdout, "\tfile 1:\t0x%02X\t%03d\n", t[0], t[0]); 
            fprintf(stdout, "\tfile 2:\t0x%02X\t%03d\n", t[1], t[1]); 
            fprintf(stdout, "Difference in numbers: %c%d\n", (t[0] > t[1]) ? '-' : '+', abs(t[0] - t[1]));
            fprintf(stdout, "\n");
        } 
 
    } 
 
    fp_cleanup(file); 
 
    return 0; 
}

```Also attached for convenience.

Please note that this is a byte by byte comparition, so large integers and endianness is not taken into account. But if you are big enough to use these tools, you are big enough to do the math. :)

I built this tool to cheat in the old Sid Meyer's Civilization, where the amount of gold were searched for in two savefiles. It has also been used in old games as Excalibur and for various emulators' savegames, such as VisualBoyAdvance. The output was used, at the time, as an aid for binary editing in applications such as PSPad in hex edit mode.
I find myself sometimes using this as a tool still, when reverse engineering stupid undocumented protocols, for instance. :mad:

I am fully aware this makes me a bad person. :roll:

I think this may have been somewhat what the original poster was after, athough it was posted in 2007. I hope someone will find it useful. :)

edit: Actually, I just used it myself and realised changing the output to a one-liner makes it a whole lot more powerful, for instance in conjunction with *grep*:
```
fprintf(stdout, "0x%08X:\t0x%02X -> 0x%02X\t%03d -> %03d\t%c%d\n", c, t[0], t[1], t[0], t[1], (t[0] > t[1]) ? '-' : '+', abs(t[0] - t[1]));
```

Will produce lines like this:
```
0x00006C14      0x0D -> 0xFE    013 -> 254    +241
```

---

### Post by v.cecchetto on 2009-10-09
> **Endolith said:**
> Edit and compare giant binary files with lfhex

[http://www.linux.com/feature/135690](http://www.linux.com/feature/135690)

(Edit: After installing 80 MB of dependencies, it still won't install.  I give up.)


Compiled on Hardy Heron 64 bit:

1. 

Install qt3-... libqt3-... packages

2.

$ PATH=/usr/share/qt3/bin:$PATH

$ export PATH
 
$ QTDIR=/usr/share/qt3 ./configure

$ QTDIR=/usr/share/qt3 make

--------------------------------------

With this old version you are also able to compare two files:

$ lfhex -c file1 file2

It works on Jaunty 64bit too. 
:popcorn:

You find it compiled in the attached files.

---

### Post by giantpune on 2010-02-03
sorry to be reviving such an old thread, but i think I've found the best answer to the question.  i found all of the other suggestions to be much more annoying than the nice hex editors available in windows.  so i found a way to get one of those to actually work in linux.  (Hex Workshop 6.0.1)

[IMG]http://img651.imageshack.us/img651/5280/screenshot1tx.png[/IMG]

it turns out that the program itself runs fine in wine, but its the installer which crashes.  so i just installed this thing in windows XP and then switched to my ubuntu installation and copied the program files folder over to wine.  and now just link to the HWorks32.exe and its all golden.  I hope this helps anybody who stumbles on it.

---

### Post by l0xin on 2010-03-05
There's [HxD](http://mh-nexus.de/en/hxd/) as well. It works perfectly under Wine.

---

### Post by sdaau on 2010-09-14
Hi all, 

Just wanted to post my version of this: 

> **Lux Perpetua said:**
> 
**edit:** As a workaround, you can use a combination of diff and hexdump to detect inserted and deleted bytes:
```

hexdump -e "1 1 \"%02x\n\"" file1 > temp1
hexdump -e "1 1 \"%02x\n\"" file2 > temp2
diff temp1 temp2

```

It should be noted, that the *hexdump* manual mentions:
[quote=man hexdump]
```

     -v      Cause hexdump to display all input data.  Without the -v option,
             any number of groups of output lines, which would be identical to
             the immediately preceding group of output lines (except for the
             input offsets), are replaced with a line comprised of a single
             asterisk.

```[/quote]

So, what I end up using is: *hexdump* to generate a textual representation of each byte one a single line, as in the original example by Lux Perpetua - and then I use *meld* to visualise the differences; this is because *meld* seems to be able to handle single row deletions/insertions well; which translates to handling _single byte insertions/deletions_ well - unlike, say, *vbindiff* or *dhex* (which cannot display single byte changes well). In a bash one-liner, it looks like this: 
```

meld <(hexdump -v -e "1/1 \" %02x\"" -e "1/1 \" %_c \n\" " file1.bin) <(hexdump -v -e "1/1 \" %02x\"" -e "1/1 \" %_c \n\" " file2.bin)

```... or, if you just want the byte in hex displayed per line - without the character representation in the second column - just delete the second '*-e "..."*' format unit in the format string in the *hexdump* call (and add a line break to the first one):
```

meld <(hexdump -v -e "1/1 \" %02x\n\"" file1.bin) <(hexdump -v -e "1/1 \" %02x\n\"" file2.bin)

```However, this tends to be a bit slow process - even for moderately large files (note, around a megabyte would of course generate some one million lines - one line per byte :) ) 

Cheers!

---

### Post by ozone702 on 2011-04-21
> **phossal said:**
> You can't possibly be up to any good using a tool like *that.* Why would you want to look for changes in the hex of two binary files? :D

You're joking right?  If not, you should be because I can think of a thousand reasons to compare binary files without any malintent.

---

### Post by slavik on 2011-04-22
there is no reason to need this thread anymore.

---

