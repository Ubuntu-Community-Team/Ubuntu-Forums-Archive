---
title: "[Beginner] Programming Challenge: 3"
date: 2008-08-08
forum: Programming Talk
---

### Post by LaRoza on 2008-08-08
The last challenge had more entries fail than succeed, which shows that the challenge was harder than it looks. User input is a pain. I recommend everyone go try that just for the experience of the hell of dealing with users. Interestingly, the best user is a programmer, so it was actually unfair for me to test. I am sure I could find an average person to crash each one of the "working" versions and take the entire operating system with it, however, I cannot be that clueless.

Here is the last challenge: [http://ubuntuforums.org/showthread.php?t=881152](http://ubuntuforums.org/showthread.php?t=881152)

For this one, I ask non beginners to not give solutions that give away too many hints to those trying.


[size=+1]The Challenge:[/size]
Now that we dealt with user input, lets deal with program output. All put output to a prompt or in one case a GUI. Lets put somethings out to files. While we are at it, lets read from files also.

**This is important! Follow the following instructions to the letter**
Make a file named "**bhaarat.text**" with this content:
```

1. Assamese/Asomiya
2. Bengali/Bangla
3. Bodo
4. Dogri
5. Gujarati
6. Hindi
7. Kannada
8. Kashmiri
9. Konkani
10. Maithili
11. Malayalam
12. Manipuri
13. Marathi
14. Nepali
15. Oriya
16. Punjabi
17. Sanskrit
18. Santhali
19. Sindhi
20. Tamil
21. Telugu
22. Urdu

```

Write a program that reads this file, and takes the languages that begin with "H" or "S" and writes them to another file, named "**out.text**". The output can be more flexible. It can be one line (with spaces between names) or on a new line. I don't want the original numbers, but extra credit goes to those who number the lines correctly (begin with 0, if you are a geek)

Then have this program write "**23. English**" to the end to continue the list in bhaarat.text.

In short:
[list]
[*] Read **bhaarat.text** and read the language names beginning with an "S" or "H", and write them (only the language names!) to a file named **out.text**
[*] Output can be flexible, however, it cannot include the original numbers and some sort of whitespace should separate the words (newlines if you are going for extra credit). Extra credit for correctly numbered lines.
[*] The language "English" and its number and period is then added to the original file in continuation of the list.
[/list]

[size=+1]Extra Credit[/size]
[list]
[*] Line numbers in output
[*] Use of the native script for (any) languages (shows unicode support). You can get the script for Hindi from its wikipedia page. Either version will work. I will be using gedit, unicode enabled for reading with standard packages.
[/list]

[size=+1]Rules:[/size]
Do not copy code, but you can obviously read it :-)

Try not to comment on other submissions. It will be hard to judge changing entries. If you edit your code, post the new version and make it clear there is a new code.

[size=+1]How it will be judged[/size]
This task is very technical. There is no user input to deal with, and I will be using the correct file, so feel free to exclude error handling, unless you forsee errors.

[list]
[*] It has to do what it is specified.
[/list]

As before, try to follow the following (although I think it won't come down to judging on this, as the challenge will be tricky for beginners):
[list]
[*] Clean code. Readable code is a must for being a programmer who wishes to possibly interact with others. Some languages can be more readable than others, so it will be judged on the effort of writing clean code, not which language is easier to read by design.
[*] Logical code. Be a programmer, not a code monkey :-)
[*] Commented code. If something is possibly unclear (like an obscure use of math), let the readers know. Do not over comment, and let the code speak for itself whenever you can. Have logical variable names and function names. (Excessive commenting is a minus factor)
[*] Working code. It has to work as it is posted. The codw will be read on the forum, so remember to use this guide to paste code if you don't know how: [http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)
[/list]

[size=+1]Hints:[/size]
[list]
[*] Most languages have all the functions you need to do this, so explore standard libraries.
[*] You will have to readlines (hint, that is the name of the function you may be using in the std lib), and writelines. Also, you will be getting rid of line numbers, so you'll have to deal with string functions or regular expressions (Python users, split() will do this for you with no problem, explore it)
[*] Using this challenge to try out a new language brings you bonus points, so please state when you are using the language for the first time if you are.
[/list]

---

### Post by slavik on 2008-08-09
read and rip :)

```

#!/usr/bin/perl
#
#       untitled.pl
#       
#       Copyright 2008 Vyacheslav Goltser <slavikg@gmail.com>
#       
#       This program is free software: you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation, either version 3 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       
#       You should have received a copy of the GNU General Public License
#       along with this program.  If not, see <http://www.gnu.org/licenses/>.
#       

use strict;
use warnings;

open IN, "bhaarat.text" or die $!; #+>> means read/append
open OUT, ">out.text" or die $!;

my $counter = 0;

my @input = <IN>;
close IN;

print OUT map { $counter++.". ".$1."\n" if (/((?:S|H).*)$/) } @input;

close OUT;

# what is the point of this?
open IN, ">>bhaarat.text" or die $!;
print IN "23. English\n";
close IN;

```

The code is a mix of procedural and functional programming :)

---

### Post by ghostdog74 on 2008-08-09
> **slavik said:**
> 

print OUT map { $counter++.". ".$1."\n" if (/((?:S|H).*)$/) } @input;

```

print  map { $.++.". ".$1."\n" if (/((?:S|H).*)$/) } @input;

```

---

### Post by Jessehk on 2008-08-09
I tried to make it clear, but it **is** Haskell.
Since Haskell can be so esoteric, I don't feel I'm giving
away much. :)

```

-- By Jessehk
-- On Saturday, August 9th 2008

module Main where

import System.IO

-- Given an ordered list of languages,
-- return a list of valid languages with
-- the numbers stripped.
extractLangs :: [String] -> [String]
extractLangs lines = filter validLang $ map (head . tail . words) lines
    where validLang = flip elem ['H', 'S'] . head

-- Return an enumerated list
-- of an array of strings.
enumerate :: [String] -> String
enumerate items = unlines $ zipWith makeItem [1..] items
    where makeItem n s = show n ++ ". " ++ s

main :: IO ()
main = do
  contents <- readFile "bhaarat.text"
  writeFile "out.text" $ enumerate $ extractLangs (lines contents)
  appendFile "bhaarat.text" "23. English"

```

Run with either

```

runhaskell <file>.hs

```

or 

```

ghc --make <file>
./<file>

```

---

### Post by Sinkingships7 on 2008-08-09
C++

v0.1
v0.2 (added code to append to bhaarat.text)
v0.3 (added code to print appropriate line numbers to out.text)
[PHP]
#include <iostream>
#include <fstream>
using namespace std;

#define IGNORE_LIMIT 10
#define MAX_READ_LENGTH 15

int main(){
    // create pointers & open files for reading and writing.
    ifstream read_ptr; read_ptr.open("bhaarat.text", ios::in);
    ofstream write_ptr; write_ptr.open("out.text", ios::out);

    char lang[MAX_READ_LENGTH]; // string to store extracted language text.

    if (read_ptr.is_open()){
        int line_number;
        while (!(read_ptr.eof())){
            read_ptr.ignore(IGNORE_LIMIT, ' ');  // ignore line until first space.
            read_ptr.get(lang, MAX_READ_LENGTH); // write text to string 'lang'.
            read_ptr.ignore(IGNORE_LIMIT, '\n'); // go to the next line.
            if (lang[0] == 'S' || lang[0] == 'H'){
                write_ptr << line_number << ". " << lang << endl; 
                line_number++;
            }
        }
        // close opened files
        read_ptr.close();
        write_ptr.close();
        
        // create pointer for appending to file; write text; close file.
        ofstream write_ptr; write_ptr.open("bhaarat.text", ios::app);
        write_ptr << "\n23. English";
        write_ptr.close();
        
        cout << "Operation completed successfully.\n" <<
                "Press Enter to continue...\n"; getchar(); return (0);
    }
    cout << "Error opening file.\n"; getchar(); return (1);
}
[/PHP]

---

### Post by slavik on 2008-08-09
> **ghostdog74 said:**
> ```

print  map { $.++.". ".$1."\n" if (/((?:S|H).*)$/) } @input;

```
I don't get it ...

---

### Post by ghostdog74 on 2008-08-09
> **slavik said:**
> I don't get it ...
no need for $counter.

---

### Post by slavik on 2008-08-09
I don't think it would be a good idea to use $.

---

### Post by Def13b on 2008-08-09
In python, I wasn't to sure about the whole unicode bit, never used it, I'll have to do some reading.

[PHP]#!/usr/bin/env python

output = open('out.text', 'w')
line = 1
for lang in open('bhaarat.text', 'r').read().split():
    if lang.startswith('S') or lang.startswith('H'):
        output.write('%d. %s\n' % (line, lang))
        line += 1
output.close()

open('bhaarat.text', 'a').write('23. English\n')
[/PHP]

---

### Post by ghostdog74 on 2008-08-09
> **Def13b said:**
> In python, I wasn't to sure about the whole unicode bit, never used it, I'll have to do some reading.

[PHP]#!/usr/bin/env python

output = open('out.text', 'w')
line = 1
for lang in open('bhaarat.text', 'r').read().split():
    if lang.startswith('S') or lang.startswith('H'):
        output.write('%d. %s\n' % (line, lang))
        line += 1
output.close()

open('bhaarat.text', 'a').write('23. English\n')
[/PHP]

open() by default is read. Therefore , 
```

for lang in open("bhaarat.txt")

```
another way to iterate a file also getting its line number
```

for linenum, line in enumerate(open("bhaarat.txt")):
   print linenum , line

```

---

### Post by ghostdog74 on 2008-08-09
> **slavik said:**
> I don't think it would be a good idea to use $.

why not?

---

### Post by xnevermore on 2008-08-09
Although I was tempted to use perl for this exercise, I do want to continue to use a new language and become more familiar with OO programming. So here is another ruby entry:

```

#!/usr/bin/ruby

class Language
  def initialize (file_in, file_out)
    @in = File.new(file_in, 'r+')
    @out = File.new(file_out, 'w')
    @in_count 
    @out_count = 1
  end
  def process
    @in.each_line do |line|
      @in_count, name = line.chomp.split('. ')
      if name =~ /^(H|S)/
	@out.puts @out_count.to_s + '. ' + name 
  	@out_count += 1	
      end
    end
  end
  def add_entry (name)
    @in_count = @in_count.to_i + 1
    @in.puts @in_count.to_s + '. ' + name
  end
end

language = Language.new('bhaarat.text', 'out.text')
language.process
language.add_entry('English')

puts "Done!"

```

---

### Post by stchman on 2008-08-09
Here is my version of the program written in C.

[PHP]
#include <stdio.h>
#include <string.h>

int main(int argc, char *argv[])
{
   	
	/* file pointer declaration */
	FILE *fileout, *filein;
	
	/* variables declaration */
	short end_of_file = 0;
	char line_num[10];
	char Lang[30];

	/* start of code */
	if(argc != 3)
	{
		printf("Usage:\n");
		printf("ch3 <input file> <output file>\n");
		return 1;
	}
	
	/* open file */
	if((filein = fopen( argv[1], "r" ) ) == NULL)
	{
		printf("Cannot Open Input file %s\n", argv[1]);
		return 1;
	}
	
	/* open file for writing */
	if((fileout = fopen( argv[2], "w" ) ) == NULL)
	{
		printf("Cannot Open Output file %s\n", argv[2]);
		return 1;
	}
	
	/* assume the file is populated */	
	end_of_file = 1; 

	/* start scanning in all the lines from the file using fscanf
	fscanf returns 0 when EOF is encountered */
	while( end_of_file == 1 )
	{
		
		end_of_file = fscanf(filein, "%s", &line_num);
		end_of_file = fscanf(filein, "%s", &Lang);
				
		/* scan each Country to see if there is an "H" or "S" as their first letter */
		if( Lang[0] == 'H' || Lang[0] == 'S')
		{
			fprintf(fileout, "%s  %s\n", line_num, Lang);
		}

	} /* end while */
	
	/* close files */
	fclose(filein);
	fclose(fileout);
	
	return (0);

}

[/PHP]

Compile using gcc:
```

gcc -o challenge3 -challenge3.c

```

You run the program by doing the following:

```

challenge3 <input filename with path> <output file with path>

```

I have compiled the program and it gives you line numbers in which the 'H' or 'S' occur as the first letter of the language.  Of course choose out.txt for the output filename.

Cheers.

---

### Post by jimi_hendrix on 2008-08-09
do we have to create a new text file for the output in the program or is that done manually

also do you mean save it as bhaarat.text or bhaarat.txt?

---

### Post by bobbocanfly on 2008-08-09
See [http://ubuntuforums.org/showthread.php?p=5560006#post5560006](http://ubuntuforums.org/showthread.php?p=5560006#post5560006)

---

### Post by ghostdog74 on 2008-08-09
> **bobbocanfly said:**
> Much longer than the other python entries i have seen, but I wanted to keep it as readable as possible.

its indeed very long. Some of them are unnecessary, like calling touch. If you want to simulate touching an empty file, there's also no need to use system touch. 
```

open("empty_file","w").write("")

```

---

### Post by nvteighen on 2008-08-09
**Python**

A nice exercise for a language I'm just beginning to learn. This script prints line numbers into the output file and, as a special feature, prevents the input file to append "23. English" more than once (if you, for example, run the script twice consecutively).

Released into Public Domain.

EDIT: Changed filenames (bhaarat.txt, out.txt) to the correct ones (bhaarat.text, out.text)!

[PHP]
#!/usr/bin/env python

# Beginner Programming Challenge 3
#
# Copyright (C) 2008 Eugenio M. Vigo (aka "nvteighen")
#
# Released into the public domain in countries where this is legally possible. 
# Where not, I grant explicit permission to use this work for any purpose, in 
# any medium with no conditions.

try:
    inputfile = open("bhaarat.text", "r+")
except IOError:
    print "Ouch! File doesn't exist!"
    quit()
    
outputfile = open("out.text", "w")
out_line_num = 0
    
for line in inputfile:
    line_num, line_string = line.split(". ")
    if line_string[0] == "H" or line_string[0] == "S":
        out_line_num += 1
        outputfile.write(str(out_line_num) + ". " + line_string)

outputfile.close()
            
inputfile.seek(0, 2) # Go to the file's end.

if int(line_num) < 23: # Don't repeat English if already included.
    inputfile.write("23. English\n")
            
inputfile.close()
[/PHP]

---

### Post by iofthemourning on 2008-08-09
```
cat bhaarat.text | tr -d [1-9.' '] | grep -E 'H|S' > out.text && echo "23. English" >> bhaarat.text
```

---

### Post by Bachstelze on 2008-08-09
My C version. For the sake of learning, I used only the low-level functions (read/write) for file operation. Obviously, fscanf/fprintf would have been more efficient here.

[PHP]#include <stdio.h>                
#include <stdlib.h>               
#include <fcntl.h>                
#include <unistd.h>               
#include <string.h>               

#define MAX_LINE_LENGTH 50


int readNextLine(int fd, char* nextLine)
{                                       
    /*  Reads the next line from the file pointed by the descriptor fd
     *  and stores it at the location pointed by nextLine, including the
     *  new line character (if any).                                    
     *  Returns zero on success, non-zero on failure.                   
     */                                                                 

    int ok = 0, curPos = 0;

    do
    { 
        char* nextChar = calloc(1, sizeof(char));

        ok = read(fd, nextChar, sizeof(char));
        if(ok == -1)                          
            perror("read");                   

        nextLine[curPos] = *nextChar;

        if(*nextChar == '\n')
        {                    
            free(nextChar);  
            return 0;        
        }                    

        curPos += 1;
        free(nextChar);
    }                  
    while(ok != 0);    

    return -1;
}             


int processLine(char* inputLine, int lineNumber)
{                                               
    char* languageName = calloc(MAX_LINE_LENGTH, sizeof(char));
    int tmp = 0;                                               
    int ok;                                                    

    sscanf(inputLine, "%u. %s", &tmp, languageName);

    if(languageName[0] == 'H' || languageName[0] == 'S')
    {                                                   
        sprintf(inputLine, "%u. %s\n", lineNumber, languageName);
        ok = 0;                                                  
    }                                                            
    else                                                         
        ok = 1;                                                  
    free(languageName);                                          
    return ok;                                                   
}                                                                


int main(void)
{             
    int inputFile, outputFile;

    inputFile = open("bhaarat.text", O_RDWR);
    if(inputFile == -1)                      
    {                                        
        perror("open");
        exit(-1);
    }

    outputFile = open("out.text", O_WRONLY | O_CREAT, 0644);
    if(outputFile == -1)
    {
        perror("open");
        exit(-1);
    }

    int curLineNumber = 1;
    char* nextLine = calloc(MAX_LINE_LENGTH, sizeof(char));

    while(!readNextLine(inputFile, nextLine))
    {
        if(!processLine(nextLine, curLineNumber))
        {
            write(outputFile, nextLine, strlen(nextLine)*sizeof(char));
            curLineNumber += 1;
        }
    }

    sprintf(nextLine, "%s", "23. English\n");
    write(inputFile, nextLine, strlen(nextLine)*sizeof(char));

    close(inputFile);
    close(outputFile);
    free(nextLine);
    return 0;
}

[/PHP]

It's funny to compare it to the Bash one-liner above ;) I guess now you know why it's so important to know your way around it.

---

### Post by ghostdog74 on 2008-08-09
> **iofthemourning said:**
> ```
cat bhaarat.text | tr -d [1-9.' '] | grep -E 'H|S' > out.text && echo "23. English" >> bhaarat.text
```

then you are deleting off the numbers. 
```

awk '$2 ~ /^(H|S)/{print d++". "$2 }END{ print "23. English" >> "bhaarat.text"}' bhaarat.text > out.text

```

---

### Post by M_the_C on 2008-08-09
Here's my entry.

Python:
```
import re

f = open('bhaarat.text').read()

#  Search for sequences containing one or more numbers,
#  then a full stop, then white-space, then words beginning
#  with H and S.
sh = re.compile(r'\d+.\s(H\D+|S\D+)')
list = sh.findall(f)

out = open('out.text', 'w')

a = len(list)
while a > 0:
  list.insert(a-1,'. ')
  list.insert(a-1,str(a),)
  a = a - 1

b = "".join(list)
out.write(b)
out.close

bh = open('bhaarat.text', 'a')
bh.write('23. English\n')
bh.close()
```

---

### Post by iofthemourning on 2008-08-09
> **ghostdog74 said:**
> then you are deleting off the numbers. 
```

awk '$2 ~ /^(H|S)/{print d++". "$2 }END{ print "23. English" >> "bhaarat.text"}' bhaarat.text > out.text

```

That was the point.

"Output can be flexible, however, it **cannot include the original numbers** and some sort of whitespace should separate the words (newlines if you are going for extra credit). Extra credit for correctly numbered lines."

I am, admittedly, new to linux/unix command line though, so I'm sure there is a better way to do it.

edit: In fact, I'm gonna have to learn about awk now. That was cool.

---

### Post by LaRoza on 2008-08-09
> **jimi_hendrix said:**
> do we have to create a new text file for the output in the program or is that done manually

also do you mean save it as bhaarat.text or bhaarat.txt?

bhaarat.text is the input file, and I don't understand the first question. You don't have a choice in the matter I think, you will have to create it.

---

### Post by thirddeep on 2008-08-09
Well, my awk is not THAT ubber, so I used a simpler method:

```
cat bhaarat.text | awk '{print $2}' | egrep "^H|^S" | while read line; do echo $count $line; ((count++)); done | sed 's/Hindi/0 Hindi/' > out.text
echo "23. English" >> bhaarat.txt
```

Going to read those python examples now ...

Thd.

---

### Post by greps5 on 2008-08-09
In Java:

[PHP]
// Beginner Challenge 3 in Java
// by greps5 8/9/08

import java.io.*;

public class Challenge3 {

	public static void main(String[] args) {

		BufferedReader fileIn;
		BufferedWriter fileOut;
		int count = 1;
		String txtRecord;
		
		// initialize the file input and output streams
		try {
			fileIn = new BufferedReader(new FileReader("bhaarat.text"));
			fileOut = new BufferedWriter(new FileWriter("out.text"));
		}
		catch (FileNotFoundException ex) {
			System.out.println("Error: file 'bhaarat.text' not found.");
			System.out.println("Please make sure that the filename is " +
					"spelled correctly and that the file resides in the " +
					"same location as the Challenge3.class file.");
			return;
		}
		catch (IOException ex) {
			System.out.println("Error: unable to initialize file I/O");
			return;
		} // end try-catch
		
		try {
			txtRecord = fileIn.readLine();
			
			System.out.println("File I/O in progress...");
			
			while (txtRecord != null) {
				// trim record number from txtRecord
				if (txtRecord.charAt(1) == '.') {
					txtRecord = txtRecord.substring(1);
				}
				else {
					txtRecord = txtRecord.substring(2);
				} // end if
				
				// check first letter of the language and write to file
				if (txtRecord.charAt(2) == 'H' || txtRecord.charAt(2) == 'S') {
					txtRecord = "" + count + txtRecord;
					fileOut.write(txtRecord);
					fileOut.newLine();
					count++;
				} // end if
				
				txtRecord = fileIn.readLine();
			} // end while
			
			// close file I/O streams
			fileIn.close();
			fileOut.close();
			
			// append new record to bhaarat.text
			fileOut = new BufferedWriter(new FileWriter("bhaarat.text", true));
			fileOut.write("23. English");
			fileOut.newLine();
			fileOut.close();
		}
		catch (IOException ex){
			System.out.println("Error during file I/O");
			return;
		} // end try-catch
		
		System.out.println("File I/O finished sucessfully.");
	} // end main

}
[/PHP]

---

### Post by chandru on 2008-08-09
I tried to do this in C++ which is a new language for me. 

So this program checks for two unicode characters I chose randomly in my native tongue. The test data is the same list in tamil, which I have attached. Change line 39 if you want to use different criteria.

EDIT 1: Bug fixed in the next post (#27)

```

#include <iostream>
#include <fstream>

using namespace std;

// removes the serial numbers from the beginning of the line
wstring getlanguage(wstring line) {
  // find the space in the string
  wchar_t delim = ' ';
  wstring::size_type delim_loc = line.find(delim, 0);

  // get substring from the first character after space till the end
  if (delim_loc != wstring::npos) 
    return line.substr(delim_loc + 1);
  else
    return line;
}

int main() {
  wifstream infile;      //input file
  wofstream outfile;     //output file
  wstring line;        //line of data
  int index = 1;        //serial number for output file
  locale loc("");       //unicode

  // open file and proceed if file exists
  infile.open("bhaarat.txt");
  infile.imbue(loc);

  if (infile.is_open()) {
    outfile.open("out.txt");
    outfile.imbue(loc);

    // read a line
    while (getline(infile, line)) {
      wstring lang = getlanguage(line);
      //if first character is one of two unicode chars write to file 
      if (lang.at(0) == L'&#2965;' or lang.at(0) == L'&#2980;')
        outfile << index++ << ". " << lang << endl;
    }

    // free resources
    infile.close();
    outfile.close();
  }

  // write a line to the original file
  outfile.open("bhaarat.txt", ios::app);
  if (outfile.is_open())
    outfile << "23. &#2950;&#2969;&#3021;&#2965;&#3007;&#2994;&#2990;&#3021;" << endl;
  outfile.close();

  return 0;
}

```

---

### Post by chandru on 2008-08-09
Bug in the last program (post #26), where the original file was not modified.

Corrected version

```

#include <iostream>
#include <fstream>

using namespace std;

// removes the serial numbers from the beginning of the line
wstring getlanguage(wstring line) {
  // find the space in the string
  wchar_t delim = ' ';
  wstring::size_type delim_loc = line.find(delim, 0);

  // get substring from the first character after space till the end
  if (delim_loc != wstring::npos) 
    return line.substr(delim_loc + 1);
  else
    return line;
}

int main() {
  wifstream infile;      //input file
  wofstream outfile;     //output file
  wstring line;        //line of data
  int index = 1;        //serial number for output file
  locale loc("");       //unicode

  // open file and proceed if file exists
  infile.open("bhaarat.txt");
  infile.imbue(loc);

  if (infile.is_open()) {
    outfile.open("out.txt");
    outfile.imbue(loc);

    // read a line
    while (getline(infile, line)) {
      wstring lang = getlanguage(line);
      //if first character is one of two unicode chars write to file 
      if (lang.at(0) == L'&#2965;' or lang.at(0) == L'&#2980;')
        outfile << index++ << ". " << lang << endl;
    }

    // free resources
    infile.close();
    outfile.close();
  }

  // write a line to the original file
  outfile.open("bhaarat.txt", ios::app);
  outfile.imbue(loc);
  if (outfile.is_open()) 
    outfile << L"23. &#2950;&#2969;&#3021;&#2965;&#3007;&#2994;&#2990;&#3021;" << endl;
  outfile.close();

  return 0;
}

```

---

### Post by OutOfReach on 2008-08-09
Here is mine, I might add that unicode thing after I do some reading, so expect some changes, Again suggestions would be appreciated. 

[PHP]import os

def main():
    if not os.path.exists("bhaarat.text"):
        print "Error: 'bhaarat.text' does not exist! The program cannot continue!"
        exit(1)
    elif os.path.exists("bhaarat.text"):
        inFile = open("bhaarat.text")
        outFile = open("out.text", "w" )
        lineNumber = 0
        for line in inFile:
            line = line.split()[1]
            if line.startswith("H") | line.startswith("S"):
                result = "%i. %s\n" % (lineNumber, line)
                outFile.write(result)
                lineNumber += 1
        outFile.close()
        inFile = open("bhaarat.text", "a")
        inFile.write("23. English\n")
            
            
if __name__ == "__main__":
    main()[/PHP]

---

### Post by arsenic23 on 2008-08-09
I had no idea that there was any effort behind unicode strings in python.  I thought all I'd have to do was put a 'u' before the strings when I first declared them.  Good fun.  Hopefully I haven't missplaced an error like last time.  I'm fairly sure this is good to go though.

Code could be a little more compact, a few lines could be combined into something smaller, but I think this is easier on the eyes.

[PHP]#!/usr/bin/env python
# -*- coding: utf-8 -*-
# coding=UTF-8

Hindi=u"&#2361;&#2367;&#2344;&#2381;&#2342;&#2368;"
Sanskrit=u"&#2360;&#2306;&#2360;&#2381;&#2325;&#2371;&#2340;&#2366; &#2357;&#2366;&#2325;"
langs=[]
inputText=""	# incase of IOError
try:	inputText=open('bhaarat.text','r').readlines()
except IOError:	print "Whoa whoa, where's your bhaarat.text?"
for items in inputText:
	langs.append(items.split('. ')[1].split('\n')[0])

outputText=u""
att=0		# Generic counter
for items in langs:
	if items[0].lower() == 's' or items[0].lower() == 'h':
		if items.lower() == 'hindi': outputText += "%i. %s (%s)\n" %(att,items,Hindi)	
		elif items.lower() == 'sanskrit': outputText += "%i. %s (%s)\n" %(att,items,Sanskrit)	
		else:	outputText+="%i. %s\n" %(att,items)
		att+=1

open('out.text','w').write(outputText.encode("UTF-8"))
if inputText[-1].startswith('23'): None	# Don't want to do this more then once
else:	open('bhaarat.text','a').write("23. English")[/PHP]

---

### Post by badperson on 2008-08-09
here's mine:
I realized I blew it on the last one...d'oh...so stupid, but I think this one works correctly. 

```
/**

Ubuntu forum challenge #2
File i/o


*/

import java.util.*;
import java.io.*;
import java.util.regex.Pattern;
import java.util.regex.Matcher;

public class UbuntuFileReaderChallenge{

	ArrayList<String> newFileList;
	ArrayList<String> revisedOldFileList;
	BufferedReader br;
	BufferedWriter newFileBR;


	public void readInputFile(File file){

		System.out.println("reading file input...");
		try{
			newFileList = new ArrayList<String>();
			revisedOldFileList = new ArrayList<String>();
			br = new BufferedReader(new FileReader(file));
		
			String line = "";
			// read input from text file
		while((line=br.readLine()) != null){
		// pick out number, figure out what letter each word begins with  and add text to arrayLists
		populateAndAnalyzeList(line);
		}
		System.out.println("writing new file...\n");		
		writeNewFile();

		// now overwrite old file and add English at the end
		System.out.println("re-writing original file...");
		BufferedWriter bw = new BufferedWriter(new FileWriter(file));
		
		bw.write("List of Languages\nFile modified by " + this.getClass() + "\nfor Ubuntu Forum Challenge #3\nWritten by Badperson\n\n");
		int counter = 1;
		for(Iterator i = revisedOldFileList.iterator(); i.hasNext();){
		String language = (String)i.next();
		bw.write(counter + ". " + language + "\n");
		counter++;

		}

		bw.write(counter + ". " + "English");
		bw.close();	
		System.out.println("done.");
		} catch(IOException e){
		System.err.println("problem reading input file...make sure bhaarat.text is in the same directory in which the app is run...");
		e.printStackTrace();
		}


	} // end read input file method

	public void populateAndAnalyzeList(String text){
	



	// regex to pick out number
	Pattern lineFormat = Pattern.compile("\\d+\\.");
	Matcher lineFormatMatcher = lineFormat.matcher(text);
		while(lineFormatMatcher.find()){

		// take number out of line
		text = lineFormatMatcher.replaceAll("");
		// eliminate leading space
		text = text.replace(" ", "");
		revisedOldFileList.add(text);
			// pick out words that start with h or s and add them to their own list
			if(text.startsWith("S") || text.startsWith("s") || text.startsWith("H") || text.startsWith("h")){
			newFileList.add(text);
			}

		
		}




	} // end populateAndAnalyzeList method

	public void writeNewFile(){

		try{

		
		BufferedWriter newFileBR = new BufferedWriter(new FileWriter(new File("out.txt")));
		newFileBR.write("Output File for Ubuntu Forum Programming Challenge #3\nWritten by Badperson\n\n");
		// write out new file:
		int counter = 1;

		for(Iterator i = newFileList.iterator(); i.hasNext();){
		String language = (String)i.next();
		newFileBR.write(counter + ". " + language + "\n");
		counter++;
		}
		newFileBR.close();


		} catch(IOException e){
		System.err.println("problem writing new files...");
		e.printStackTrace();
		}
		


		


	

	}

	


//main
	public static void main(String[] args){
	new UbuntuFileReaderChallenge().readInputFile(new File("bhaarat.text"));
	}



} // end class
```

bp

---

### Post by badperson on 2008-08-09
Is there a prize for most lines of code? LOL I'll probably get that one...

---

### Post by thirddeep on 2008-08-09
Most lines of code might be a bit silly (quick do this in ASM), but that AWK line should win the shortest code :-)

Thd.

---

### Post by jimi_hendrix on 2008-08-09
> **LaRoza said:**
> bhaarat.text is the input file, and I don't understand the first question. You don't have a choice in the matter I think, you will have to create it.

i mean do i open up my text editor of choice and make the output file or do i have to code the program to create an output file

---

### Post by badperson on 2008-08-09
> **jimi_hendrix said:**
> i mean do i open up my text editor of choice and make the output file or do i have to code the program to create an output file


the output file should be generated by your code...unless I've misunderstood...

---

### Post by LaRoza on 2008-08-09
> **jimi_hendrix said:**
> i mean do i open up my text editor of choice and make the output file or do i have to code the program to create an output file

Um, your program makes it. I am not sure what language you are going to use, but in the languages I have studied, opening a file for writing will create it if it doesn't exist (and will overwrite it if it does)

---

### Post by PandaGoat on 2008-08-09
My second program in lisp.  It assumes the input file is in your current directory and there is no new line at the end (or 23. English will have a new line between it and 22).  It was a struggle not to talk like a gangster this time.
```

(defun open-input-file-read (filename)
  "returns the file descriptor of filename to be read"
  (open filename))

(defun open-input-file-write (filename)
  "returns the file descriptor of filename to write to"
  (open filename :direction :output :if-exists :append :if-does-not-exist :create))

(defun strip-number (line)
  "strips the number from the beginning"
  (let ((index (search "." line)))
    (if index (return-from strip-number (subseq line (+ index 2))) 
	(return-from strip-number nil))))

(defun check-fixed-line (line)
  "if line begins with H or S return true, else nil"
  (if (STRING-EQUAL (subseq line 0 1) "H") (return-from check-fixed-line t)
      (if (STRING-EQUAL (subseq line 0 1) "S") (return-from check-fixed-line t)  (return-from check-fixed-line nil))))


(defun build-vector ()
  "build a vector of the language we want to output"
  (let ((file (open-input-file-read "bhaarat.text")) (v (make-array 5 :fill-pointer 0 :adjustable t)) fixed-line)
    (loop for line = (read-line file nil)
       while line do (setq fixed-line (strip-number line)) 
			   (if (check-fixed-line fixed-line) (vector-push-extend fixed-line v) ()))
    (close file) 
    (return-from build-vector v)))
  
(defun write-output ()
  "write the the language we want to out.text"
  (let ((file (open-input-file-write "out.text")) (num 1))
    (loop for lang across (build-vector)
       do (format file "~A. ~A~%" num lang)     
	 (setq num (+ num 1)))
    (close file)))

(defun add-english ()
  "append 23. English to the input"
  (let ((file (open-input-file-write "bhaarat.text")))
    (file-position file :end)
    (write-line "23. English" file)
    (close file)))



(write-output)
(add-english)

```

---

### Post by shae on 2008-08-09
This is my entry once again in C++; this is my second time using C++.  It expects bhaarat.text to be in the same directory as the binary and for it not to end in extraneous lines (Or there will be blank lines between 22 and 23).

[PHP]#include <iostream>
#include <string>
#include <fstream>

using namespace std;

void write_output()
{
    ifstream input("bhaarat.text");
    ofstream output("out.text");
    int number = 0;
    while(!input.eof())
    {
        string line;
        getline(input, line);
        line.erase(0, line.find_first_not_of("1234567890. "));
        if(line[0] == 'S' || line[0] == 'H')
        {
            number++;
            output << number << ". " << line << endl;
        }
    }
    input.close();
    output.close();
}

void write_english()
{
    ofstream output("bhaarat.text", ios::app);
    output << "23. English";
    output.close();
}

int main()
{
    write_output();
    write_english();
    return 0;
}[/PHP]

Edit: Defined the variables when they are declared.

---

### Post by linkmaster03 on 2008-08-09
I really liked this one, I learned File I/O which is going to be really useful!

[php]#!/usr/bin/env python
# listio.py
#Bhaarat Copier by LinkMaster03
import os.path, sys
if not os.path.exists("bhaarat.text"): 
    print "bhaarat.text is not available. Make sure it is in the working directory."
    sys.exit()
bhaarat,i,temp,langs,a=open("bhaarat.text","r"),0,"",[],1
bhaarat=bhaarat.readlines()
while i<22:
    temp=bhaarat[i].lstrip("1234567890. ")
    if temp.startswith("H") or temp.startswith("S"): 
        langs.append("%s. %s" % (a,temp))
        a=a+1
    i=i+1
out=open("out.text","w")
out.writelines(langs)[/php]

---

### Post by cprofitt on 2008-08-09
OK... I am not 100% happy with this code... because if I were to do something similar to the second list my line numbers would be off... but it works for the scenario given and the extra credit.

```

#!/usr/bin/env python

#  challeng3.py
#       bhaarat.text file handler
#       read and write
#  by PrivateVoid

output = open('out.text', 'w')
line = 0
try:
    for lang in open('bhaarat.text', 'r').read().split():
        line += 1
        if lang.startswith('S') or lang.startswith('H'):
            output.write('%d. %s\n' % (line / 2, lang))
    output.close()
except:
    print "There is not a file named bhaarat.text or the file is already open."


open('bhaarat.text', 'a').write('23. English\n')

```I will be trying to make this better.

---

### Post by Bachstelze on 2008-08-09
> **LaRoza said:**
> Um, your program makes it. I am not sure what language you are going to use, but in the languages I have studied, opening a file for writing will create it if it doesn't exist (and will overwrite it if it does)

In Python, you can open it so the written data will be appended to the end of the file instead of overwiting it altogether:

```
f = open(filename, mode='a')
```

---

### Post by LaRoza on 2008-08-09
> **HymnToLife said:**
> In Python, you can open it so the written data will be appended to the end of the file instead of overwiting it altogether:

```
fd = os.open(filename, os.O_APPEND, 0644)
```

Yes, I know (although that is a big of a round about way to do it), and appending is in the challenge, much to the confusion of slavik.

---

### Post by yabbadabbadont on 2008-08-09
I haven't read the whole thread yet.  Has anyone supplied a solution using bash and the various command line tools?

---

### Post by Bachstelze on 2008-08-09
> **yabbadabbadont said:**
> I haven't read the whole thread yet.  Has anyone supplied a solution using bash and the various command line tools?

A few people have, yes.

---

### Post by yabbadabbadont on 2008-08-09
> **HymnToLife said:**
> A few people have, yes.

I guess it's time to learn how to use nasm... :D

---

### Post by LaRoza on 2008-08-09
> **yabbadabbadont said:**
> I haven't read the whole thread yet.  Has anyone supplied a solution using bash and the various command line tools?

Yes, they are pretty cool one liners. 

This challenge is very simple and is meant to help beginners learn basic skills, so that is why some of the requirements are so simple.

---

### Post by linkmaster03 on 2008-08-09
Oops, the last version didn't put English in bhaarat.text! I've updated it.

[php]#!/usr/bin/env python
# listio.py
#Bhaarat Copier by LinkMaster03
import os.path, sys
if not os.path.exists("bhaarat.text"): 
    print "bhaarat.text is not available. Make sure it is in the working directory."
    sys.exit()
i,temp,langs,a=0,"",[],1
bhaarat=open("bhaarat.text","r").readlines() #put bhaarat.text into a list with entries by line
while i<22:
    temp=bhaarat[i].lstrip("1234567890. ") #take the line in the current iteration and strip the numbering
    if temp.startswith("H") or temp.startswith("S"): 
        langs.append("%s. %s" % (a,temp))
        a=a+1
    i=i+1
open("out.text","w").writelines(langs) #output the list of H and S languages to out.text
open("bhaarat.text","a").write("23. English\n")[/php]

---

### Post by ghostdog74 on 2008-08-09
> **PrivateVoid said:**
> 
```
        if lang.startswith('S') or lang.startswith('H'):
```
   

you might want to use ```

lang[0] in ["S","H"]

```
its shorter.

---

### Post by Def13b on 2008-08-09
> **LaRoza said:**
> Yes, they are pretty cool one liners.

There are some extremely bad ones too, (albeit 2 liners, 3 with the #!) like this one in python :)

Couldn't get it to 1 line and I'm willing to bet it could be done better, pretty sure it will also make alot of people cringe but I figured I'd post it for interests sake anyway. I like to do this sort of thing to most things I write to see where shortcuts can be made (not necessarily where they should be made).

[PHP]#!/usr/bin/env ptyhon
print >> open('out.text', 'w'), '\n'.join(i[0] + i[1] for i in zip((str(i) + '. ' for i in range(len(filter(lambda x: x[0] in ('S', 'H'), open('bhaarat.text', 'r').read().split())))), filter(lambda x: x[0] in ('S', 'H'), open('bhaarat.text', 'r').read().split())))
print >> open('bhaarat.text', 'a'), '23. English'[/PHP]

---

### Post by ghostdog74 on 2008-08-09
> **OutOfReach said:**
> 
            if line.startswith("H") | line.startswith("S"):
            
this is not really correct. Its a bitwise or. Use "or" ,eg
```

if line.startswith("H") or line.startswith("S"):

```
or ```

line[0] in ["S","H"]

```

---

### Post by ghostdog74 on 2008-08-09
> **Def13b said:**
> 

[PHP]#!/usr/bin/env ptyhon
print >> open('out.text', 'w'), '\n'.join(i[0] + i[1] for i in zip((str(i) + '. ' for i in range(len(filter(lambda x: x[0] in ('S', 'H'), open('bhaarat.text', 'r').read().split())))), filter(lambda x: x[0] in ('S', 'H'), open('bhaarat.text', 'r').read().split())))
print >> open('bhaarat.text', 'a'), '23. English'[/PHP]

why do you want to lump everything together like that? i am also not sure you need a lambda function as well.
```

o=0
for line in open("file"): 
    line=line.strip().split()
    if line[1][0] in ["S","H"]:
        print o,line[1]; o=o+1
open("out.txt","a").write("23. English")

```

---

### Post by cprofitt on 2008-08-09
Here is the second version... I modified the code some more so simple math did count lines to get the right line number.

[php]
#!/usr/bin/env python

#  challeng3v2.py
#       bhaarat.text file handler
#       read and write
#  by PrivateVoid

output = open('out.text', 'w')
line = 0

try:
    for lang in open('bhaarat.text', 'r').read().replace('.',' ').split():
        if lang.isdigit():
            line = lang
        if lang.startswith('S') or lang.startswith('H'):
            output.write('%d. %s\n' % (int(line), lang))
    output.close()

    open('bhaarat.text', 'a').write('23. English\n')
except:
    print "There is not a file named bhaarat.text or the file is already open."
[/php]

In addition I pulled the append function in to the try block.

---

### Post by LaRoza on 2008-08-09
> **Def13b said:**
> 
[PHP]#!/usr/bin/env ptyhon
print >> open('out.text', 'w'), '\n'.join(i[0] + i[1] for i in zip((str(i) + '. ' for i in range(len(filter(lambda x: x[0] in ('S', 'H'), open('bhaarat.text', 'r').read().split())))), filter(lambda x: x[0] in ('S', 'H'), open('bhaarat.text', 'r').read().split())))
print >> open('bhaarat.text', 'a'), '23. English'[/PHP]

You have an interpreter named "ptyhon"? :-)

> **ghostdog74 said:**
> why do you want to lump everything together like that? i am also not sure you need a lambda function as well.


I think she was just trying to get one line (well, 2 in this case)

---

### Post by Def13b on 2008-08-09
> **ghostdog74 said:**
> why do you want to lump everything together like that? 

More an exercise to see if I can then anything else, I know it's not something that would ever be used but I find it a great way to learn things like lambdas, zip etc because it forces you to use everything and anything available.

As for the ptyhon, I'm gonna go with it was intentional because code that looks like that shouldn't be associated with Python, yeah, that sounds good :)

---

### Post by Jessehk on 2008-08-09
> **PandaGoat said:**
> My second program in lisp.


Look into the WITH-OPEN-FILE macro and get rid of the redundant functions. :)

---

### Post by cardboardtoast on 2008-08-09
Well, here's my try (hope it works right)...:) still learning

Python!
[PHP]
#!/usr/bin/env python

#challenge 3
#read and write files:
readfile = open("bhaarat.text", "r+")
out = open("out.text", "w")

filelines = []
outline = []
linenumber = 0

for line in readfile:
    filelines.append(line)
for line in filelines:
    line = line.split(" ")[1]
    if line.startswith("H") or line.startswith("S"):
        outline.append(line)
for line in outline:
    linenumber += 1
    out.write(str(linenumber) + ". " + line)

readfile.write("\n23. English")

readfile.close()
out.close()
[/PHP]
it's bhaarat**.text** and not **.txt**, right?

---

### Post by Darkade on 2008-08-09
Here is mine, in bash. I've written some bash scripts but it's not something I'm proficient. I'm now writing it in Python and it will be my first python script LOL
And as LaRoza asked not too much hints

```

#!/bin/bash

#clear or create out.text
	> out.text

number=0

#for each line in bhaarat.text do commands
cat bhaarat.text | while read linea; do

	pos=$(echo `expr index "$linea" " "`) #get position of first space in line
	pchar=${linea:pos:1}

	if [ "$pchar" = "H" ] ; then
		echo "$number ${linea:pos}" >> out.text
		number=$((number + 1))
	elif [ "$pchar" = "S" ] ; then	
		echo "$number ${linea:pos}" >> out.text
		number=$((number + 1))
	fi

done

**echo "23. English" >> bhaarat.text**

```

Damn! forgot the last 23 english... just added it

---

### Post by -grubby on 2008-08-10
```
[color=#408080]*#/usr/bin/python*[/color]

[color=#408080]*# Preparing the files for later use..*[/color]
bhar [color=#666666]=[/color] [color=#008000]open[/color]([color=#BA2121]"bhaarat.text"[/color]) 
bharwrite [color=#666666]=[/color] [color=#008000]file[/color]([color=#BA2121]"bhaarat.text"[/color], [color=#BA2121]"a"[/color])
output [color=#666666]=[/color] [color=#008000]file[/color]([color=#BA2121]"out.text"[/color], [color=#BA2121]"a"[/color]) 

[color=#008000]**def**[/color] [color=#0000FF]main[/color]() : 
    [color=#408080]*# Check every line in bhar *[/color]
    [color=#008000]**for**[/color] line [color=#AA22FF]**in**[/color] bhar[color=#666666].[/color]readlines() : 
        [color=#408080]*# Remove numbers from the listing*[/color]
        line [color=#666666]=[/color] line[color=#666666].[/color]split()[[color=#666666]1[/color]]
        
        [color=#408080]*# Check if each line starts with 'H' or 'S'*[/color]
        [color=#008000]**if**[/color] line[color=#666666].[/color]startswith([color=#BA2121]"H"[/color]) [color=#AA22FF]**or**[/color] line[color=#666666].[/color]startswith([color=#BA2121]"S"[/color]) : 
            output[color=#666666].[/color]write(line [color=#666666]+[/color][color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]) 
    
    bharwrite[color=#666666].[/color]write([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]23. English"[/color])
        
[color=#008000]**if**[/color] __name__ [color=#666666]==[/color] [color=#BA2121]"__main__"[/color] : 
    main()
    
    [color=#408080]*# Close the files when we are done*[/color]
    bhar[color=#666666].[/color]close()
    bharwrite[color=#666666].[/color]close()
    output[color=#666666].[/color]close()

```

---

### Post by ghostdog74 on 2008-08-10
> **nathangrubb said:**
> [color=#AA22FF]**in**[/color] bhar[color=#666666].[/color]readlines() : 
        [color=#408080]*# Remove numbers from the listing*[/color]
        line [color=#666666]=[/color] line[color=#666666].[/color]split([color=#BA2121]" "[/color])[[color=#666666]1[/color]]
        
  [/code]
split() splits on spaces by default. Therefore split(" ") can be shortened to split() and if data has more spaces, they will be ignored. Unless of course if you specifically want to split on exactly 1 space.

---

### Post by LaRoza on 2008-08-10
> **ghostdog74 said:**
> split() splits on spaces by default. Therefore split(" ") can be shortened to split() and if data has more spaces, they will be ignored. Unless of course if you specifically want to split on exactly 1 space.

Also, the original file had tabs, not spaces, so I wouldn't want anyone's code to fail for that!

(The file I am going to use will have a space, in case anyone is worried)

---

### Post by ghostdog74 on 2008-08-10
> **Darkade said:**
> 
cat bhaarat.text | while read linea; do

	pos=$(echo `expr index "$linea" " "`) #get position of first space in line
	pchar=${linea:pos:1}

	if [ "$pchar" = "H" ] ; then
		echo "$number ${linea:pos}" >> out.text
		number=$((number + 1))
	elif [ "$pchar" = "S" ] ; then	
		echo "$number ${linea:pos}" >> out.text
		number=$((number + 1))
	fi

done
cat is unnecessary. The while read loop will iterate the file for you. Also you can use bash's IFS internal variable to split the lines for you.
```

while IFS=" " read a b; do
    case $b in
     [HS]*)         
        echo $number $b
        number=$(( number+1 ))
        ;;
    esac
done  < bhaarat.text

```

---

### Post by Bodsda on 2008-08-10
wow, i noticed in this challenge and the previous one that you beginner programmers are very good (much better then me) lol

---

### Post by LaRoza on 2008-08-10
> **Bodsda said:**
> wow, i noticed in this challenge and the previous one that you beginner programmers are very good (much better then me) lol

Not everyone posting is a beginner.

---

### Post by nvteighen on 2008-08-10
> **LaRoza said:**
> Not everyone posting is a beginner.
:)

---

### Post by lisati on 2008-08-10
Although I'm not a "beginner" (been programming off and on for nearly 30 years) I read some of the posts for the challenges, it's a good way of brushing up.....

---

### Post by M_the_C on 2008-08-10
I'm surprised no-one else writing Python has used re yet.

I don't know whether it was the wording of the challenge or just my strange introduction to the language but re seemed almost asked for.  But then I suppose that's the beauty of programming, so many different ways of doing things, even in a single language.

Also, is it generally considered good programming to include the
```
#!/usr/bin/env python
```
line?  That is my major weakness, programming conventions.

---

### Post by Darkade on 2008-08-10
> **ghostdog74 said:**
> cat is unnecessary. The while read loop will iterate the file for you. Also you can use bash's IFS internal variable to split the lines for you.
```

while IFS=" " read a b; do
    case $b in
     [HS]*)         
        echo $number $b
        number=$(( number+1 ))
        ;;
    esac
done  < bhaarat.text

```
I didn't quite Get it:confused:

---

### Post by ghostdog74 on 2008-08-10
> **Darkade said:**
> I didn't quite Get it:confused:

which parts are you not getting it? I suggest you read the bash link in my sig also.

---

### Post by nvteighen on 2008-08-10
> **M_the_C said:**
> 
Also, is it generally considered good programming to include the
```
#!/usr/bin/env python
```
line?  That is my major weakness, programming conventions.

Yes, because Python's installation place can be different depending on what system you use. /usr/bin/env python will check the interpreter's location for you.

---

### Post by bobbocanfly on 2008-08-10
Decided my other one was terrible so rewrote it:

```
#!/usr/bin/env python

out = open("output.text", 'w')

count = 0
for line in open("bhaarat.text"):
    if line.split(" ")[1][0] in ["H", "S"]:
        out.write(str(count) + ". " + line.split(" ")[1])
        count += 1
        
open("bhaarat.text", 'a').write("23. English\n")

```

@LaRoza: Please accept this one as my Python entry

---

### Post by cprofitt on 2008-08-10
OK -- I thought the 'extra credit' was for writing the original line numbers in the new file... it appears as though that is incorrect; which makes this much, much easier to do. What is the proper interpretation? Languages in new file with original numbers or with new in sequence numbers?

edit:

[LIST]
[*] Line numbers in output
[/LIST]
The original does not specify new or old numbers so I made an assumption. The specification is vague.

---

### Post by NovaAesa on 2008-08-10
Here we go. In C++

[PHP]#include <fstream>
#include <iostream>
#include <string>

using namespace std;

int main() {

    ifstream inputFile("bhaarat.text"); //the input file
    string num; //holds the numbers as they are gotten from the file
    string lang; //holds the languages as they are gotten from the file

    ofstream outFile("out.text"); //the output file
    int lineNum = 0; //keeps track of which line in the output we are up to

    /* parts of the file are read one at a time, deliminated by whitespace */
    while (inputFile >> num) {
        inputFile >> lang;
        if (lang[0] == 'S' || lang[0] == 'H') {
            outFile << lineNum << ". " << lang << endl;
            lineNum++;
        }
    }
    inputFile.close();
    outFile.close();

    /* appends "23. English" to the file" */
    ofstream appendFile("bhaarat.text", ios::app);
    appendFile << "23. English" << endl;
    appendFile.close();

    cout << "done" << endl;
}    [/php]

Now stop posting these addictive challenges so I can get some *real* homework done :P

---

### Post by bobbocanfly on 2008-08-10
This is my first ever attempt to do anything in Perl, so bear with me if it is awful:

```
#!/usr/bin/perl

$count = 0;
$in_data = "";

open INPUT, "< bhaarat.text" or die "can't open datafile: $!"; 
open OUTPUT, "> output.text" or die "can't open datafile: $!";

# Get the input data from the file into a string
while (read(INPUT, $char, 1))
{
    $in_data .= $char;
}

# Go through each line, check if it started with (H|S)
foreach (split(/\n/, $in_data))
{
    @line = split(/\s+/, $_);
    if ($line[1] =~ /^(H|S)/)
    {
        print OUTPUT $count.". ".$line[1]."\n";
        $count++;
    }
}

# Write 23. English to the input file
open FINAL_OUT, ">> bhaarat.text" or die "can't open datafile: $!";
print FINAL_OUT "23. English\n";

```

I am almost certain there is a better way to read the file than that, but it works.

Ps. God Perl is awful....but it is sooo addictive.

---

### Post by cprofitt on 2008-08-10
OK... after seeing that the original spec called for not using the original line numbers... but there was extra credit for using line numbers it is now clear that the line numbers should be new ones.

my modified code:

[php]
#!/usr/bin/env python

#  challeng3v2.py
#       bhaarat.text file handler
#       read and write
#  by PrivateVoid

output = open('out.text', 'w')
line = 0

try:
    for lang in open('bhaarat.text', 'r').read().split():
        if lang.startswith('S') or lang.startswith('H'):
            output.write('%d. %s\n' % (line, lang))
            line += 1
    output.close()

    open('bhaarat.text', 'a').write('23. English\n')
except:
    print "There is not a file named bhaarat.text or the file is already open."
[/php]I personally would have wanted to know the original line numbers... even if I had new line numbers... I will try to post a non-entry that does that in a little bit.

here is the code with the original line kept but not used as line numbering ((THIS IS NOT MY ENTRY -- ABOVE IS THE ENTRY))

[php]
#!/usr/bin/env python

#  challeng3v2.py
#       bhaarat.text file handler
#       read and write
#  by PrivateVoid

output = open('out.text', 'w')
line = 0
newline = 0

try:
    for lang in open('bhaarat.text', 'r').read().replace('.',' ').split():
        if lang.isdigit():
            line = lang
        if lang.startswith('S') or lang.startswith('H'):
            output.write('%d. %s original line %d\n' % (newline, lang, int(line)))
            newline += 1
    output.close()

    open('bhaarat.text', 'a').write('23. English\n')
except:
    print "There is not a file named bhaarat.text or the file is already open."
[/php]

---

### Post by DaymItzJack on 2008-08-10
Will the bhaarat.text that you're using have a new line at the end already?

---

### Post by mssever on 2008-08-10
> **DaymItzJack said:**
> Will the bhaarat.text that you're using have a new line at the end already?
Why not make your program cope with either situation?

---

### Post by lisati on 2008-08-10
> **mssever said:**
> Why not make your program cope with either situation?

And what if the line numbers are out of sequence?

---

### Post by mssever on 2008-08-10
> **lisati said:**
> And what if the line numbers are out of sequence?
They won't be, since LaRoza specified the input file already. She didn't specify whether or not there is a newline at the end.

---

### Post by Bodsda on 2008-08-10
> **LaRoza said:**
> Not everyone posting is a beginner.

Doesn't that defeat the object of having a 'Beginners' programming challenge?

---

### Post by LaRoza on 2008-08-10
> **Bodsda said:**
> Doesn't that defeat the object of having a 'Beginners' programming challenge?

They won't be counted when I test the results.

---

### Post by Bodsda on 2008-08-10
> **LaRoza said:**
> They won't be counted when I test the results.

OOhh -- That makes me feel better, i think i might attempt this now

Thanks LaRoza

---

### Post by NovaAesa on 2008-08-10
> **Bodsda said:**
> Doesn't that defeat the object of having a 'Beginners' programming challenge?

Some people might just want to brush up on their skills or use it as an exercise to get more familiar with a new(ish) language (like I am). Btw, I don't really think I'm a beginner with C++ anymore... I can now do... classes!

---

### Post by cprofitt on 2008-08-10
For me it is a new language... my only other programming was using Visual Studio and C#

---

### Post by HotCupOfJava on 2008-08-10
OK, here is my version. It is a bit more verbose than some I have read, but it does meet all of the requirements, including the extra credit. My language of choice is Java (and I'm still a relative noob to it - been studying it for 6 months).

[PHP]//TextFileConverter.java

import java.io.*;

public class TextFileConverter{

	public static void main(String args[])throws IOException{
		
		FileInputStream input;
		FileOutputStream output;
		FileOutputStream newBhaarat;		

		//open the file to read
		input = new FileInputStream("bhaarat.text");
			
		//read the file as bytes into an array
		byte[] byteArray = new byte[input.available()];	
		input.read(byteArray);

		//close the input file
		input.close();

		//convert the byte array into a String
		String inputString = new String(byteArray);

		//get length of the inputString
		int length = inputString.length();

		//construct the output for "out.text"
		String outputString = new String();
		int holder = inputString.lastIndexOf("H");
		int subStringStart = 0;
		int subStringEnd = 0;
		int lineCounter = 1;
		while(subStringStart<holder){
			subStringStart=inputString.indexOf("H", 
				subStringEnd);
			subStringEnd=inputString.indexOf("\n", 
				subStringStart);
			outputString=outputString+lineCounter+
				".\t"+inputString.substring(
				subStringStart, subStringEnd)+"\n";
			lineCounter++;
		}
		holder = inputString.lastIndexOf("S");
		subStringStart = 0;
		subStringEnd = 0;
		while(subStringStart<holder){
			subStringStart=inputString.indexOf("S", 
				subStringEnd);
			subStringEnd=inputString.indexOf("\n", 
				subStringStart);
			outputString=outputString+lineCounter+
				".\t"+inputString.substring(
				subStringStart, subStringEnd)+"\n";
			lineCounter++;
		}

		//now we write
		output = new FileOutputStream("out.text");
		byte[] outputBytes = outputString.getBytes();
 		output.write(outputBytes);
                output.close();
		
		//now we append the original file
		String newBhaaratString = inputString + "\n23. English";
		newBhaarat = new FileOutputStream("bhaarat.text");
		byte[] newBhaaratBytes = newBhaaratString.getBytes();
		newBhaarat.write(newBhaaratBytes);
		newBhaarat.close();
	}
}[/PHP]

---

### Post by Bodsda on 2008-08-10
I only know a wee bit of python, so it means most people posting here have a couple more languages under their belt giving them more experience. I just wanted to know that we (first timers) would be given a chance. And we are! woot!!  

;~)

---

### Post by iofthemourning on 2008-08-10
Did a little more fooling around and I would like this to be my official submission.

```
cat bhaarat.text | tr -d [1-9.] | egrep 'H|S' | nl -s. -w 1 > out.text && echo "23. English" >> bhaarat.text
```

---

### Post by ghostdog74 on 2008-08-10
> **iofthemourning said:**
> Did a little more fooling around and I would like this to be my official submission.

```
cat bhaarat.text | tr -d [1-9.] | egrep 'H|S' | nl -s. -w 1 > out.text && echo "23. English" >> bhaarat.text
```

remove the cat
```

 tr -d [1-9.] < bhaarat.txt | egrep 'H|S' | nl -s. -w 1 > out.text && echo "23. English" >> bhaarat.text

```

---

### Post by iofthemourning on 2008-08-10
cool! Didn't even think to do that. Thanks for the insight :D

I followed the awk/sed link in your sig after your first response. Really cool stuff. Still chugging through it.

---

### Post by ibuclaw on 2008-08-10
I am just here for sakes of producing obfuscated code :)

[PHP]#!/bin/bash
[ "$1" ] || exec echo "usage: $0 file.text";o="out.text";n=1;echo -n "" >$o;for i in $(perl -wnl -e 'print $1 if (/((?:S|H).*)$/)' $1);do printf "%d. %s\n" $n $i >> $o;let "n++";done;ruby -ne 'END {print $.+1, ". English\n" unless /English/}' $1 >> $1[/PHP]
It uses a mixture of bash, perl and ruby... mostly because I had 5 minutes to spare.
Partly because I have never fused two or more languages together before.

Tell you what, though. I'm having a read through on OpenMP at the moment...
I've make a parallelism C implementation of it before the end of the week ;)

Regards
Iain

---

### Post by mssever on 2008-08-10
> **tinivole said:**
> It uses a mixture of bash, perl and ruby... mostly because I had 5 minutes to spare. That's an abuse of Ruby. :)

---

### Post by ibuclaw on 2008-08-10
> **mssever said:**
> That's an abuse of Ruby. :)

Haha, I'm only taking your advice from last week and am getting my feet wet with it...

It is pretty much Perl, so I am liking it very much, thanks :)

---

### Post by jacensolo on 2008-08-11
This challenge is very good for me because I set out to learn regular expressions a week ago but gave up. I went over it tonight and put this together. I know I could have made the pattern shorter and used re.search() and/or re.findall() modules, but I wanted to use groups to get a better understanding.  Plus I could match the whole match and copy it to a new file if the end of lines got corrupted somehow this way.
[PHP]#Do whatever you want with this, besides claiming you wrote it
import re
#Pattern: Any digit repeated, then any digit any number of times
#or none at all. Then a '.', followed by any whitespace character
#any number of times (or none at all). Then S or H, followed by
#any lower case letter any number of times
pattern = re.compile('\d\d*[.]\s*([SH][a-z]*)')
#Note: I could have made this easier by re.compile('[SH][a-z]*')
#and using the re.search or re.findall

readfile = open('bhaarat.text')
writefile = open('out.text', 'w')

outLine = 0

for line in readfile:
    match = pattern.match(line)
    if match:
        outLine += 1
        #Print the line #, '.', a space, and group#1 of the pattern - Between the ()
        string = "%i. %s\n" % (outLine, match.group(1))
        writefile.write(string)

readfile.close()
appendfile = open('bhaarat.text', 'a')

appendfile.write('23. English')
writefile.close()
[/PHP]
Thanks for this challenge!!! Can't wait for the next one.

What's with all these "line.split"'s and "lang.startswith"!? Taking the easy route I see... I'm watching you guys ;)
I didn't know that was there (lang.startswith). I don't fully understand how they are splitting it. I've used it plenty before though. Maybe I need sleep. :(

Edit: I get it now. Some split the whole file into the list which, basically, ends up being the same as what I did for my for loop. I don't see how lang.startswith isn't picking up the numbers if they aren't splitting the line though.

---

### Post by linkmaster03 on 2008-08-11
I used lstrip("1234567890. ") to strip all numbers, spaces, and periods off the beginning of each line. So I just had the languages unnumbered. Then I searched for S and H.

---

### Post by M_the_C on 2008-08-11
> **nvteighen said:**
> Yes, because Python's installation place can be different depending on what system you use. /usr/bin/env python will check the interpreter's location for you.Thanks, so it's considered proper to put it at the start of any scripts you write?
> **jacensolo said:**
> This challenge is very good for me because I set out to learn regular expressions a week ago but gave up. Finally, someone else has used it as well.  :D

---

### Post by nvteighen on 2008-08-11
> **M_the_C said:**
> Thanks, so it's considered proper to put it at the start of any scripts you write?

Yes, it will ensure that the script is executed by the proper interpreter (in a Unix/Unix-like system, of course...). For example, there are Linux distros that place python in /usr/local/bin (Fedora?).

---

### Post by cprofitt on 2008-08-11
I have used reg-ex in the past, but only in C#... I will have to explore doing it in Python soon as well.

---

### Post by TreeFinger on 2008-08-11
If anyone could offer advice on how I could improve my program I would appreciate it.

[php]
import re
f = open('bhaarat.text', 'r')
output = open('out.text', 'w')
split_pattern = re.compile(' ')
count = 0
for line in f:
	maybe = re.split(split_pattern, line)[1]
	if maybe[0] == 'H' or maybe[0] == 'S':
		count += 1
		output.write(str(count) + '. ' + maybe)

output.close()
f.close()
f = open('bhaarat.text', 'a')
f.write('\n23. English')
f.close()
[/php]

---

### Post by ghostdog74 on 2008-08-11
> **TreeFinger said:**
> If anyone could offer advice on how I could improve my program I would appreciate it.

[php]
import re
f = open('bhaarat.text', 'r')
output = open('out.text', 'w')
split_pattern = re.compile(' ')
count = 0
for line in f:
	maybe = re.split(split_pattern, line)[1]
	if maybe[0] == 'H' or maybe[0] == 'S':
		count += 1
		output.write(str(count) + '. ' + maybe)

output.close()
f.close()
f = open('bhaarat.text', 'a')
f.write('\n23. English')
f.close()
[/php]

you don't have to use re for such simple task. just use the split() string method. 
```

for line in f:
    maybe = line.split()[1]

```

---

### Post by kaatil on 2008-08-11
first time i ever tries to program to write, read, and append the file in C. :) It nice to have a challenge so i can do something and learn from it! :)

[PHP]
/*
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 * 
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU Library General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin Street, Fifth Floor Boston, MA 02110-1301,  USA
 */
 
 
/* Beginner's Programming Challenge #3!! */

#include <stdio.h>

int main(void)
{
	int lineNum;
	int lineCounter;
	char language[20];
	char buffer[20];
	FILE *bhaaratFile, *outputFile;

	if ((bhaaratFile = fopen("bhaarat.text", "ra+")) == NULL) 
	{
		printf("ERROR: cannot open \'bhaarat.text\' file!");
		return 1;
	}
	
	if ((outputFile = fopen("output.text", "w")) == NULL)
	{
		printf("ERROR: cannot open \'output.text\' file!");
		return 1;
	}
	
	lineCounter = 1;
	
	while (fgets(buffer, sizeof(buffer), bhaaratFile) != NULL)
	{ 
		sscanf(buffer, "%d. %s", &lineNum, language);
		if (language[0] == 'H' || language[0] == 'S')
		{
			fprintf(outputFile, "%d. %s\n", lineCounter, language);
			lineCounter++;
		}
	}
	
	fprintf(bhaaratFile, "23. English\n");
	fclose(bhaaratFile);
	fclose(outputFile);
	return 0;
}
[/PHP]

---

### Post by nvteighen on 2008-08-12
> **kaatil said:**
> first time i ever tries to program to write, read, and append the file in C. :) It nice to have a challenge so i can do something and learn from it! :)

There are some issues:
1. The input file will be called "bhaarat.**txt**", not "bhaarat.text". It would be a pity to be disqualified for that a silly mistake.
2. Compile using -Wall flag and you'll catch a warning in your sscanf() line (hint: what type of arguments does sscanf() expect? what kind of arguments are you giving?).

Fixing that two issues, your program works fine and it's really good, to me.

---

### Post by LaRoza on 2008-08-12
> **nvteighen said:**
> There are some issues:
1. The input file will be called "bhaarat.**txt**", not "bhaarat.text". It would be a pity to be disqualified for that a silly mistake.


No, it will be bhaarat.text.

---

### Post by nvteighen on 2008-08-12
> **LaRoza said:**
> No, it will be bhaarat.text.

](*,) (I've changed my entry... Sorry for the confusion)

---

### Post by badperson on 2008-08-12
sorry if I missed this, but when does this challenge close? 
also, are there any intermediate challenges? 

that matrix mulitiplication thing seemed a little over my head. 
bp

---

### Post by kaatil on 2008-08-12
> **LaRoza said:**
> No, it will be bhaarat.text.


> **nvteighen said:**
> ](*,) (I've changed my entry... Sorry for the confusion)

phew seem i am still in the challenge game! heh. Nvteighen, i noticed that -Wall warning just now.. i wonder what possibly could go wrong? last time i check i ran that program and it look okay just for bhaarat.text. mhmm. Mind enlighten me?

---

### Post by LaRoza on 2008-08-12
> **badperson said:**
> sorry if I missed this, but when does this challenge close? 

Wednesday (didn't say so before, but I am now that you asked).


> 
also, are there any intermediate challenges? 

Not by me.

---

### Post by nvteighen on 2008-08-12
> **kaatil said:**
> Nvteighen, i noticed that -Wall warning just now.. i wonder what possibly could go wrong? last time i check i ran that program and it look okay just for bhaarat.text. mhmm. Mind enlighten me?

The line in question is:
[PHP]
sscanf(buffer, "%d. %s", &lineNum, &language);
[/PHP]

You know sscanf() needs pointers to data. &lineNum is a pointer to an integer. &language is a pointer to a string. What is a string in C? An array. What is an array in C? A pointer to the array's first element.

Ergo, &language is a pointer to a pointer (a double-pointer). As language is an array (i.e. a pointer), you don't need the & operator to use it in sscanf()... Look at the buffer variable (also a string) in the same sscanf() statement, which yourself wrote without the ampersand! (I know it's the input string, but at the end, is the same).

So:
[PHP]
sscanf(buffer, "%d. %s", &lineNum, language);
[/PHP]

is the right thing to do.

It's quite amazing that you didn't run into a memory corruption error because of that. You were changing the string's memory address to somewhere else, who knows where... 

Also, get into the habit of using -Wall when compiling. It's always adviceable to make the compiler warn you as much as possible so you can be aware of any silly compile-time error.

---

### Post by kaatil on 2008-08-12
> **nvteighen said:**
> The line in question is:
[PHP]
sscanf(buffer, "%d. %s", &lineNum, &language);
[/PHP]

You know sscanf() needs pointers to data. &lineNum is a pointer to an integer. &language is a pointer to a string. What is a string in C? An array. What is an array in C? A pointer to the array's first element.

Ergo, &language is a pointer to a pointer (a double-pointer). As language is an array (i.e. a pointer), you don't need the & operator to use it in sscanf()... Look at the buffer variable (also a string) in the same sscanf() statement, which yourself wrote without the ampersand! (I know it's the input string, but at the end, is the same).

So:
[PHP]
sscanf(buffer, "%d. %s", &lineNum, language);
[/PHP]

is the right thing to do. 

Also, get into the habit of using -Wall when compiling. It's always adviceable to make the compiler warn you as much as possible so you can be aware of any stupid compile-time error.

Ah i see, that how it went. Thank you very much, Glad i learn something about it! Thanks!

---

### Post by conehead77 on 2008-08-13
Another Haskell solution (I hope it works this time :) ):
[PHP]
import System.IO

main = do
  content <- readFile "bhaarat.text"
  writeFile "out.text" $ sieve content
  appendFile "bhaarat.text" "23. English\n"
  
sieve :: String -> String
sieve s =  unlines $ enumerate (filter beginsWithBorS $ words s) [1..]

enumerate :: [String] -> [Int] -> [String]
enumerate [] _ = []
enumerate (s:ss) (i:is) = (show i ++ ". " ++ s) : enumerate ss is

beginsWithBorS :: String -> Bool
beginsWithBorS s
  | head s == 'B' || head s == 'S' = True
  | otherwise = False
[/PHP]

---

### Post by Stunts on 2008-08-13
Hi all!
I saw this challenge and decided to participate.
It's my 1st coding in python, so please cut me some slack. =-)
I did some Perl programming in the past, but python 'feels' a lot better (at least for me).
Anyway, here's my entry, hope I'm not too late.
```

#!/usr/bin/python

#Open the needed files.
infile = open("bhaarat.text")
outfile = open("output.text",'w')

#Read the infile, strip the numbers and write
#the appropriate languages to the outfile.
for lines in infile:
    indx = lines.find(" ")
    lines = lines[(indx + 1):]
    if lines.startswith('H') or lines.startswith('S'):
        outfile.write(lines)

#Close all files.    
outfile.close()
infile.close()

#Add '23. English' to the infile.
append = open("bhaarat.text",'a')
append.write('23. English')
append.close()

```

Since the closing is today I didn't find the time to number the output entries. I also didn't have the time to read trough the whole thread, but I hope I didn't miss anything important.
Let me know what you think when it's over. =-)

BTW, LaRoza, this is a great idea!

---

### Post by z0idberg on 2008-08-13
Do you still take entries? I haven't read the whole thread yet, so someone may have posted something similar...

Anyway, I'm new to Python (actually, I've never written anything useful in *any* language). Went of on the regular expression path before I even read the hint about split... Doesn't really matter, as finding out that re.findall returns lists of the groups inside the regular expression if there are any made my day (my hour... or my ten minutes at least). No error checking, no comments, no closing of the files; here goes:
[PHP]
import re

infile = open('bhaarat.text', 'r+')
outfile = open('out.text', 'w')

matches = re.findall(re.compile('\d+\. ([SH].*)'), infile.read())

for i, line in enumerate(matches):
        outfile.write('%s. %s\n' % (i+1, line))
        
infile.write('23. English')                              
[/PHP]

---

### Post by LaRoza on 2008-08-13
Thread Closed for grading (should be done tonight).

---

### Post by LaRoza on 2008-08-14
I will do the grading eventually, but I am later than I expected...

---

### Post by yabbadabbadont on 2008-08-14
> **LaRoza said:**
> ...  I am later than I expected...

Not something guys usually want to hear...  :twisted:

---

### Post by Ed J on 2008-08-14
```

#!/usr/bin/env python

class counter:
    def __init__(self):
        self.value = 0
    def inc(self):
        self.value = self.value + 1

outfile = open('out.text', 'w')
ctr = counter()

for line in open('bhaart.text').xreadlines():
    line = line.split()[1]
    if line[0] == "S" or line[0] == "H":
        line = repr(ctr.value) + ". " + line + '\n'
        ctr.inc()
        outfile.write(line)

outfile.close()

```
crap
too late?

---

### Post by Mr_Chapendi on 2008-08-14
Well, I'm late, but even if it's not graded I want to post what I worked on.

Ruby
```
input = File.open('bhaarat.text', 'r+')
output = File.new('out.text', 'w+')

linematch = /^[0-9][0-9]*\.\s(H|S)/
hsmatch = /(H|S)[a-z]*/
count = 0

input.each do |line|
  if line =~ linematch
    output.puts "#{count}. #{hsmatch.match(line)}"
    count += 1
  end
end

input.puts "23. English"

input.close
output.close

```

---

### Post by LaRoza on 2008-08-15
> **yabbadabbadont said:**
> Not something guys usually want to hear...  :twisted:

I am sure the participants don't mind. It is obvious which ones work or not.

---

### Post by linkmaster03 on 2008-08-15
Are you grading them?

---

### Post by LaRoza on 2008-08-15
> **linkmaster03 said:**
> Are you grading them?

No. Not now.

---

### Post by cprofitt on 2008-08-17
Will you at least list the people who submitted working code?

---

### Post by LaRoza on 2008-08-17
> **PrivateVoid said:**
> Will you at least list the people who submitted working code?

I am not going to be grading anymore. Instead of having times when people aren't supposed to comment, I am going to have these challenges be free for alls to learn or instruct (which is best fitting)

I will test the ones later, but I think most or all do work.

---

### Post by JupiterV2 on 2008-10-02
Always last to the party... =)

[PHP]#!/bin/sh

input_file="bhaarat.text"
output_file="out.text"

# if $output_file exists remove it to have a clean slate to work with
if [ -e $output_file ]; then 
    rm -f $output_file 
fi

# Search for lines which contain (start with) either 'H' or 'S'. Strip the
# line numbers, decimal point(dot) and trailing space. Then, output the result
# to $output_file.
grep 'H' $input_file | sed 's/[123456789]*. //' >> $output_file
grep 'S' $input_file | sed 's/[123456789]*. //' >> $output_file

# Add "23. English" to the end of the $input_file if it doesn't already exist
if [ ! "$(grep '23. English' $input_file)" ]; then
    echo "23. English" >> $input_file;
else
    echo "Unable to write \"23. English\" to $input_file! Already exists!"
fi

exit 0[/PHP]

---

### Post by jtuchscherer on 2008-10-03
First of all: Thanks, LaRoza, for doing this.

I am late, too. But I was just preparing myself for a job interview tomorrow and thought it won't hurt to implement this challenge. I did it in Java. It lacks comments and is not quite readable, but it works.

```

import java.io.*;

public class Challenge {

	
	public static void main(String[] args) throws FileNotFoundException, IOException {
		// in Java 
		BufferedWriter writer1 = new BufferedWriter(new FileWriter(new File("output.txt")));
		BufferedReader reader = new BufferedReader(new InputStreamReader(new FileInputStream(new  File("bhaarat.txt")),"UTF-8" ));
		int counter = 0;
		while (reader.ready()) {
			String language = reader.readLine().split(" ")[1]; 
			if (language.startsWith("S") || language.startsWith("H") ) writer1.write(counter++ + ". " + language +"\n");  
		}
		reader.close();
		writer1.close();
		BufferedWriter writer2 = new BufferedWriter(new FileWriter(new File("/home/johannes/bhaarat.txt"),true));
		writer2.write("23. English");
		writer2.close();		
	}
}

```

---

### Post by ratmandall on 2008-10-17
Eh a little late but I still want to post it :\
[php]
#Opens specified file.
fileopen = open("bhaarat.txt", "a")
outlang = open("out.txt", "w")
fileopen.writelines("23. English\n")
#Close file
fileopen.close()
fileopen = open("bhaarat.txt")

for language in fileopen.read().split():

 #If a line in file opened starts with said character/s.   
 if language.startswith('S') or language.startswith('H'):

     #Write languages starting with S and H to a text file.
     outlang.writelines(language+"\n")

#Close bhaarat.txt
fileopen.close()    
#Close out.txt     
outlang.close()
[/php]

I like python makes my programs and doesn't afraid of anything.

---

### Post by Nemooo on 2008-11-01
My entry in C. It doesn't check for errors when opening the file.

[php]/* Beginner Programming Challenge 2

   Write a program that reads bhaarat.text, and takes the languages that begin 
   with "H" or "S" and writes them to another file, named "out.text". The output 
   can be more flexible. Then have this program write "23. English" to the end 
   to continue the list in bhaarat.text. */

#include <stdio.h>
#include <stdlib.h>

/* Remove all numbers, punctuations and spaces from the string. */
void rem_nums(char *string)
{
	const char *src = string;
	char *dst = string;

	do {
		while (*src == '0'
		    || *src == '1'
		    || *src == '2'
		    || *src == '3'
		    || *src == '4'
		    || *src == '5'
		    || *src == '6'
		    || *src == '7'
		    || *src == '8'
		    || *src == '9'
		    || *src == '.'
		    || *src == ' ')
			++src;
	} while ((*dst++ = *src++) != '\0');
}

/* Opens bhaarat.text and while it hasn't reached the end of the file. For each 
   line it reads, it removes the numbers and punctuations and checks if the 
   first letter is S or H. If this is the case, the language name is appended to
   out.text.

   Finally it appends '23. English' to bhaarat.text. */
int main()
{	
	char *input_file = "bhaarat.text";
	char *output_file = "out.text";
	char file_input[50];
	FILE *read_append;
	FILE *append;

	read_append = fopen(input_file, "r+a");

	while(fgets(file_input, 50, read_append) != NULL) {
		rem_nums(file_input);

		if(file_input[0] == 'H'
		|| file_input[0] == 'S') {
			append = fopen(output_file, "a");
			fputs(file_input, append);
			fclose(append);
		}
	}

	fputs("\n23. English", read_append);
	fclose(read_append);

	return 0;
}[/php]

While making this I tried to write a function, which would assign a filepointer to fopen(). If it returned NULL, the program should print an error message:

[php]#include <stdio.h>
#include <stdlib.h>

void openfile(FILE *f, char *filename, char *fileop)
{
	if((f = fopen(filename, fileop)) == NULL) {
		puts("Error.");
		exit(1);
	}
}

int main()
{
	FILE *f;

	openfile(f, "filename.txt", "r");
	fclose(f);

	return 0;
}[/php]

It works fine, when an error is occuring. However if the file exists the program crashes.

---

### Post by jimi_hendrix on 2008-11-01
> **Nemooo said:**
> It works fine, when an error is occuring. However if the file exists the program crashes.

lol

---

### Post by Nemooo on 2008-11-02
Now it works, though my openfile function returns the stream instead of passing file pointer. It was more convenient that way. In the above function the first argument should've have been a pointer to a pointer (FILE **f).

[php]/* Beginner Programming Challenge 3

   Write a program that reads bhaarat.text, and takes the languages that begin
   with "H" or "S" and writes them to another file, named "out.text". The output
   can be more flexible. Then have this program write "23. English" to the end
   to continue the list in bhaarat.text. */

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

/* Remove all numbers, periods and spaces from the string. */
void rem_nums(char *string)
{
	const char *src = string;
	char *dst = string;

	do {
		while(isdigit(*src) == 1
		|| *src == '.'
		|| *src == ' ')
			src++;
	} while((*dst++ = *src++) != '\0');
}

/* Open a file with the specified mode. If an error occured print the filename
   which caused the error and exit. Otherwise return the stream. */
FILE *openfile(char *filename, char *op)
{
	FILE *stream = fopen(filename, op);

	if(stream == NULL) {
		printf("Error opening %s.", filename);
		exit(1);
	}

	return stream;
}

/* Opens bhaarat.text and while it hasn't reached the end of the file. For each
   line it reads, it removes the numbers and periods and checks if the first 
   letter is S or H. If this is the case, the language name is appended to
   out.text.

   Finally it appends '23. English' to bhaarat.text. */
int main()
{
	char *input_file = "bhaarat.text";
	char *output_file = "out.text";
	char file_input[50];
	FILE *read_append;
	FILE *append;

	read_append = openfile(input_file, "r+a");

	while(fgets(file_input, 50, read_append) != NULL) {
		rem_nums(file_input);

		if(file_input[0] == 'H'
		|| file_input[0] == 'S') {
			append = openfile(output_file, "a");
			fputs(file_input, append);
			fclose(append);
		}
	}

	fputs("\n23. English", read_append);
	fclose(read_append);

	return 0;
}[/php]

---

### Post by RobOrr on 2009-06-02
Started learning Python at the weekend, and thought I'd stick my first effort at these challenges out there that I know works (my own code didn't hold up to error checks for challenge 2, so had to browse the other code submissions to help me out. )
Will hopefully have an entry for the next challenges up soon.

[php]#!/usr/bin/python
#Filename challenge3.py
#Author: Robert Orr

import sys

#check the file exists in same directory as this program.
try:
    langfile = open('bhaarat.text', 'r')
except IOError:
    print 'Cannot locate "bhaarat.text".'
    sys.exit()
    
outfile = file('out.text', 'w')

a = 1 
while True: #while loop checks every line
    line = langfile.readline()
    if line.find('H') != -1:#look for Capital H
        linenumber, linelang = line.split('. ')
        outfile.write('%d. %s' % (a, linelang))
        a = a + 1
    if line.find('S') != -1:#look for Capital S
        linenumber, linelang = line.split('. ')
        outfile.write('%d. %s' % (a, linelang))
        a = a + 1
    if len(line) == 0:
        break

langfile.close() # it's in read mode at the moment. close and open in write.
outfile.close()
langfile = file('bhaarat.text', 'w')
langfile.seek(0, 2)
langfile.write('23. English\n')
langfile.close[/php]

---

### Post by ibuclaw on 2009-06-04
We are hosting new challenges [here.]("http://ubuntu.ubuntuforums.org/showthread.php?t=1176793") You can participate in that competition instead, rather than revive dead programming challenges.

Regards
Iain

---

