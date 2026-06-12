---
title: "Beginners Challenge #6"
date: 2009-06-25
forum: Programming Talk
---

### Post by ibuclaw on 2009-06-25
OK. I've had a think about it, and after some exchange of views with people. I have come up this week/fortnight challenge.

the previous challenge is linked here: [http://ubuntuforums.org/showthread.php?t=1176793](http://ubuntuforums.org/showthread.php?t=1176793)


[SIZE="4"]**This Week's Beginners Challenge**[/SIZE]

This week the challenge is to make a simple **grep** application.

The basics for completing this task are as follows:
[LIST]
[*]The application must take at least one string input for matching.
[*]The application may take input from either a file, or stdin, or both. But it must be able to take an input from at least one source.
[*]The application must print all lines that have the matching string, with the exception of additional features, such as quiet or inverse matching.
[*]The application should print the line number too, although this can be added as an optional switch.
[*]Features such as colour highlighting matches, printing a count of matching lines, and a summary of the job carried out are optional, and only count as bonus points to your application.
[*]Features such as regex pattern matching, inverted matches, and case insensitive matches are also optional, and only count as bonus points to your application, though may not give you more of a leading edge against other applicants.
[/LIST]

A general idea of the usage of the application is as follows:
```
./simple-grep mystring file
Line 1: this is a mystring test
Line 7: yet another mystring test
Line 28: mystring was here

```

Of course, you are not limited to this, and can use any print format you wish.

Depending on coverage, enthusiasm and the number of entries, this challenge will deadline on **Monday 6th July**.
Good Luck!

Regards
Iain

---

### Post by poisonkiller on 2009-06-25
My C++ code:
```
#include <iostream>
#include <fstream>
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

#define MAX_SIZE 1024
string szColour, szBold = "0";
bool bDisplayLine = false, bCaseSensitive = false, bReverseFind = false;

string ReadLine(ifstream &inFile)
{
    char cLine[MAX_SIZE];
    string szLine;

    do
    {
        inFile.clear();
        inFile.getline(cLine, MAX_SIZE);
        szLine += cLine;
        if (inFile.eof())
            break;
    } while (inFile.fail());

    return szLine;
}

void PrintText(int nLocation, string szMatch, int nAlreadyCut, string &szBuffer)
{
    cout << szBuffer.substr(nAlreadyCut, nLocation);
    cout << "\033[" << szBold << ";" << szColour << "m";
    cout << szBuffer.substr(nAlreadyCut + nLocation, szMatch.length());
    cout << "\033[0m";
}

void FindMatches(string &szBuffer, vector<vector<string> > &vMatch, vector<int> &nLineCount)
{
    bool bFoundMatch[3];
    bFoundMatch[2] = false;
    int nAlreadyCut;
    string szLine[2];
    szLine[0] = szBuffer;
    if (bCaseSensitive == false)
    {
        transform(szLine[0].begin(), szLine[0].end(), szLine[0].begin(), ::tolower);
    }

    for (unsigned int i = 0; i < vMatch.size(); i++)
    {
        if (bCaseSensitive == false)
        {
            transform(vMatch[i][0].begin(), vMatch[i][0].end(), vMatch[i][0].begin(), ::tolower);
            if (bReverseFind == true)
                transform(vMatch[i][1].begin(), vMatch[i][1].end(), vMatch[i][1].begin(), ::tolower);
        }

        szLine[1] = szLine[0];
        string::size_type stLocation[2];
        nAlreadyCut = 0;
        bFoundMatch[0] = false;
        do
        {
            stLocation[0] = szLine[0].find(vMatch[i][0], 0);
            if (stLocation[0] != string::npos)
            {
                if (bFoundMatch[0] == false)
                {
                    if (bDisplayLine == true)
                        cout << "Line " << nLineCount[0] << ": ";
                }
                PrintText(stLocation[0], vMatch[i][0], nAlreadyCut, szBuffer);
                szLine[0].erase(0, stLocation[0] + vMatch[i][0].length());
                nAlreadyCut += (stLocation[0] + vMatch[i][0].length());
                bFoundMatch[0] = true;
            } else {
                if (bFoundMatch[0] == true)
                    cout << szLine[0] << endl;
            }
        } while (stLocation[0] != string::npos);
        szLine[0] = szLine[1];

        bFoundMatch[1] = false;
        if (bReverseFind == true)
        {
            nAlreadyCut = 0;
            do
            {
                stLocation[1] = szLine[1].find(vMatch[i][1], 0);
                if (stLocation[1] != string::npos)
                {
                    if (bFoundMatch[1] == false)
                    {
                        if (bDisplayLine == true)
                            cout << "Line " << nLineCount[0] << " (reverse): ";
                    }
                    PrintText(stLocation[1], vMatch[i][1], nAlreadyCut, szBuffer);
                    szLine[1].erase(0, stLocation[1] + vMatch[i][1].length());
                    nAlreadyCut += (stLocation[1] + vMatch[i][1].length());
                    bFoundMatch[1] = true;
                } else {
                    if (bFoundMatch[1] == true)
                        cout << szLine[1] << endl;
                }
            } while (stLocation[1] != string::npos);
        }
        if ((bFoundMatch[0] == true) || (bFoundMatch[1] == true))
            bFoundMatch[2] = true;
    }
    if (bFoundMatch[2] == true)
        nLineCount[1]++;
}

int main(int argc, char *argv[])
{
    ifstream fFile;
    vector<int> nLineCount(2, 0);
    string szBuffer, szArg, szFile;
    vector<vector<string> > vMatch;
    vector<string> vBuffer;

    nLineCount[0] = 1;
    if (argc < 3)
    {
        cout << "Need at least two arguments!" << endl;
        return 0;
    }

    for (int i = 1; i < argc; i++)
    {
        szArg = argv[i];
        if (szArg == "--line")
            bDisplayLine = true;
        else if (szArg == "--casesensitive")
            bCaseSensitive = true;
        else if (szArg == "--reverse")
            bReverseFind = true;
        else if (szArg.find("--file=", 0) != string::npos)
        {
            szArg.erase(0, 7);
            szFile = szArg;
        } else if (szArg == "--bold")
            szBold = "1";
        else if (szArg.find("--colour=", 0) != string::npos)
        {
            szArg.erase(0, 9);
            if (szArg == "red")
                szColour = "31";
            else if (szArg == "green")
                szColour = "32";
            else if (szArg == "yellow")
                szColour = "33";
            else if (szArg == "blue")
                szColour = "34";
            else if (szArg == "purple")
                szColour = "35";
            else if (szArg == "cyan")
                szColour = "36";
            else if (szArg == "grey")
                szColour = "37";
            else
                cout << "Unknown colour for --colour argument, defaulting to terminals default colour." << endl;
        } else {
            vBuffer.clear();
            vBuffer.push_back(szArg);
            reverse(szArg.begin(), szArg.end());
            vBuffer.push_back(szArg);
            vMatch.push_back(vBuffer);
        }
    }

    fFile.open(szFile.c_str());
    if (fFile.is_open())
    {
        while (!fFile.eof())
        {
            szBuffer = ReadLine(fFile);
            FindMatches(szBuffer, vMatch, nLineCount);
            nLineCount[0]++;
        }
        cout << endl << "Found the searched string(s) on " << nLineCount[1] << " line(s)!" << endl;
    } else {
        cout << "Couldn't open specified file!" << endl;
    }
    return 0;
}
```
It can use the following arguments:
--file=my_file   Uses my_file to search for string(s).
--line           Prints the line number.
--casesensitive  Enables case-sensitive search.
--reverse        Enables reverse search.
--colour=red/green/yellow/blue/purple/cyan/grey Highlights the string(s) in the specified colour.
--bold Highlighted string(s) will be in bold font.

All other arguments will be search in the specified file.

For example:
```
./simple-grep This is A --line test --file=my_file --casesensitive
Line 1: this is a mystring test
Line 7: yet another mystring test
```

---

### Post by sdennie on 2009-06-25
```

#!/usr/bin/perl

use strict;
use Getopt::Long;
use Term::ANSIColor;

my $NONE = "NONE";
my $DEFAULT_COLOR = "bold red";

# Defaults
my @regexes;
my $quiet = 0;
my $line_numbers = 0;
my $color = $NONE;
my $count_only = 0;
my $ignore_case = 0;
my $inverted = 0;
my $highlight = 0;

my $options = GetOptions(
        "e|regex=s@"      => \@regexes,
        "q|quiet"         => \$quiet,
        "l|line-numbers"  => \$line_numbers,
        "c|color:s"       => \$color,
        "n|count_only"    => \$count_only,
        "i|ignore-case"   => \$ignore_case,
        "v|inverted"      => \$inverted,
        "h|highlight"     => \$highlight,
);

$color = $DEFAULT_COLOR if $highlight and $color eq $NONE;

my $reset;
if($color ne $NONE)
{
    # Handle "sgrep -c expr file" correctly.  This isn't perfect but, it's
    # the most common case.
    eval { color $color };
    if($@)
    {
        unshift @ARGV, $color;
        $color = $DEFAULT_COLOR;
        $@ = "";
    }

    $color = $color ? color $color  : color $DEFAULT_COLOR;
    $reset = color "reset";
}
else
{
    $color = "";
    $reset = "";
}

push @regexes, (shift @ARGV) if not @regexes;
my @files = @ARGV;
my $count;

if(@files)
{
    foreach my $file (@files)
    {
        open FILE, "< $file" or warn "Can't open $file: $!";
        next if $@;

        process_file(\*FILE, $file);
        close FILE;
    }
}
else
{
    process_file(\*STDIN);
}

print "$count\n" if $count_only;

exit not $count;


sub process_file
{
    my ($fh, $file) = @_;
    my $line_number;

    while(my $line = <$fh>)
    {
        my $matched;

        chomp $line;
        $line_number++;

        if($ignore_case)
        {
            $matched += ($line =~ s/($_)/\n$1\n/gi ? 1 : 0) for @regexes;
        }
        else
        {
            $matched += ($line =~ s/($_)/\n$1\n/g ? 1 : 0) for @regexes;
        }

        if($matched == @regexes and not $inverted)
        {
            $count++;
            print_line($file, $line_number, $line);
        }
        elsif($matched != @regexes and ($inverted or $highlight))
        {
            print "$line\n" unless $count_only;
            $count++;
        }
    }
}


sub print_line
{
    my ($file, $line_number, $line) = @_;
    my $output;

    return if $quiet or $count_only;

    print "".($file ? "$file:" : "")
        .($line_numbers ? "$line_number:" : "") if not $highlight;

    my $count;
    for(split /\n/, $line)
    {
        print "".($count % 2 ? $color : "").$_.$reset;
        $count++;
    }
    print "\n";
}

```

Usage is similar to normal grep, normal perl regular expressions can be used (Though / needs to be \/) and multiple files can be specified.  Some examples:

```

sgrep foo bar # Find foo in file bar
sgrep ^[fF]oo bar # Finds all lines contain foo or Foo at the start of the line
sgrep -c foo bar # Find foo in bar and print it in bright red
sgrep -c blue foo bar # Find foo in bar and print it in blue
sgrep -l foo bar # Print line numbers for matches
sgrep -n foo bar # Prints the number of occurrences of foo in bar
sgrep -v foo bar # Prints all lines not containing foo in bar
sgrep -e foo -e bar baz # Prints lines containing foo and bar in baz
sgrep foo bar | sgrep -v baz # Prints lines in bar containing foo but not baz
sgrep -h foo bar # Print bar and highlight every occurrence of foo

```

---

### Post by ibuclaw on 2009-06-26
Since sdennie has posted, I'll post my solution in D to retort against him: 

```

import std.file;
import std.stdio;
import std.regexp;
import std.getopt;

bool colour, icase, invert, hlight, quiet;

int main(string[] args)
{
    string match, attr;
    int i = 1;
    int count = 0;
    getopt(args,
            "c|colour", &colour,
            "i|ignorecase", &icase,
            "v|inverted", &invert,
            "e|regexp", &match,
            "h|highlight", &hlight,
            "q|quiet", &quiet
          );
    if(!match.length)
        match = args[i++];
    if(icase)
        attr = "i";
    for(; i < args.length; i++)
    {
        int lcount;
        string input;
        input = cast(string)read(args[i]);
        foreach(line; RegExp(r"(.*)\n").search(input))
        {
            lcount++;
            auto m = search(line.match(1), match, attr);
            if(m && !invert)
            {
                count++;
                if(quiet)
                    continue;
                if(colour || hlight)
                {
                    if(!hlight)
                        writef("\33[35m%s\33[36m:\33[32m%d\33[36m:",
                                args[i], line);
                    writef("\33[0m%s\33[1;31m%s\33[0m",
                            m.pre, m.match(0));
                    auto a = search(m.post, match);
                    auto b = a;
                    if(a)
                    {
                    while(a)
                    {
                        if(a.match(0).length == 0)
                        {
                            stderr.writefln("Caught infinite loop, exiting...");
                            return 1;
                        }
                        writef("%s\33[1;31m%s\33[0m", a.pre, a.match(0));
                        b = a;
                        a = search(a.post, match);
                        if(!a)
                        writefln("%s", b.post);
                    }
                    }
                    else
                    writefln("%s", m.post);
                }
                else
                writefln("%s:%d:%s", args[i], lcount, line.match(1));
            }
            else if(!m && (invert || hlight))
            {
                count++;
                if(quiet)
                    continue;
                writefln("%s", line.match(1));
            }
        }
    }
    return !count;
}

```

Supports regular expressions out of the box (there is a bug in the * operator that may cause the above application to hang because it always returns true, so instead of matching, ie: "**\S***", match "**\S+**", but this is just common sense. :))

accepts the following arguments (works with either - or --):
```

c colour
h highlight
i ignorecase
v inverted
e regexp
q quiet

```

Examples
```

dgrep write testfile # Prints all matched lines with "write" in.
dgrep "\S+" testfile # Finds and prints all lines with "\S+" (non-whitespace)
dgrep -c write testfile # Finds "write" and colours all matches
dgrep -h write testfile # Prints the whole file "testfile" highlighting matches of "write"
dgrep -v write testfile # Prints all non-matched lines.
dgrep -e write testfile # Same as `dgrep write testfile`

```

To compile:
```
dmd dgrep.d
```
You require DMD-2.0 in order to compile this.

Regards
Iain

---

### Post by Nemooo on 2009-06-27
Here's a really basic one in C. I don't feel like adding a bunch of commandline arguments right now, so it just takes the string to be searched for as the first argument (and therefore can't include spaces) and the input file as the second argument.

```
#include <stdio.h>

#define BUF 100

/* Check if the line is longer than 'BUF' and read anything that's out of bound. */
void check_bound(const char *str, FILE *stream)
{
	while (*str != '\n' && *str != '\0')
		++str;

	if (*str != '\n')
		while (getc(stream) != '\n');
}

/* Compare two strings and return non-zero if they're equal. */
int str_comp(const char str_one[], const char str_two[])
{
	int i = 0;

	while (str_one[i] != '\0' && str_two[i] != '\0') {
		if (str_one[i] == str_two[i])
			++i;
		else
			return 0;
	}
	return i;
}

/* Check if 'str' is a substring of 'text'. */
int match(const char *text, const char *str)
{
	while (*text != '\0') {
		if (str_comp(text, str))
			return 1;

		++text;
	}
	return 0;
}

/* Search for 'str' in 'read_file' and print the line(s) of 'read_file', where 'str'
 * is found. */
void grep(const char *str, const char *read_file)
{
	FILE *input;
	char text[BUF];
	int line;

	input = fopen(read_file, "r");

	if (input == NULL) {
		perror("Error");
		return;
	}
	printf("Lines containing '%s':\n\n", str);

	for (line = 1; fgets(text, BUF, input) != NULL; ++line) {
		check_bound(text, input);

		if (match(text, str))
			printf("%d:\t%s", line, text);

	}
	fclose(input);
}

/* Just seperated from grep(), so arguments parsing is easier to add later. */
int main(int argc, char *argv[])
{
	/* Add arguments parsing */
	grep(argv[1], argv[2]);

	return 0;
}
```

The thing I'm wondering, is whether you should try to allocate space for the longest line in the input file, or just set a fixed point for searching and skip the rest of the line (as is the case now)?

---

### Post by soltanis on 2009-06-27
K&R have an example of this program (very limited) in their book. I assume using that is not allowed.

---

### Post by ibuclaw on 2009-06-28
> **soltanis said:**
> K&R have an example of this program (very limited) in their book. I assume using that is not allowed.

Plagiarism isn't allowed.

---

### Post by ghostdog74 on 2009-06-28
```

BEGIN{
  # simple search for 1 word only
  pat = ARGV[1]
  filename = ARGV[2]
  patlen = length(pat)
  while(( getline line < filename)>0){
    m=split(line,li ,"")
    for(i=1;i<=m;i++){
       s=substr(line,i,patlen)
       if (s == pat){
            print "found: "line
            break
       }
    }
  }
}

```
usage:
```
$ awk -f search.awk <pattern> <filename>
```

---

### Post by conehead77 on 2009-06-28
Trying some Scala:
```
import scala.io.Source

object simpleGrep {
  def main(args : Array[String]) : Unit = {
    val filePath = args(1)
    val pattern = args(0)
    
    val file = Source.fromFile(filePath).getLines
    file.foreach(line => if (line.contains(pattern)) {print(line)})
  }
}
```

---

### Post by WRDN on 2009-06-28
My entry (C++):

```
#include <iostream>
#include <fstream>
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

static bool COLOR_ENABLED = true;
static bool QUIET = false;
static bool CASE_INSENSITIVE = false;
static const char* PROGRAM_NAME;
static char* INPUT_CONTENT; // File or string
static char* MATCH; // string to search for


// Structure to hold the line and word count for searching
struct LineWord_INFO
{
    int LineCount;
    int WordCount;
};

// Available text colors
enum TextColors
{
    Black,
    Red,
    Green,
    White
};

class StringManipulation
{
public:
    static string StringToUpper(string s)
    {
        for(int i=0;i<s.length();i++)
        {
            s[i] = toupper(s[i]);
        }

        return s;
    }
};

class Color
{
public:
static string SetTextColor(TextColors col, string text)
{
    if(!COLOR_ENABLED) return text;

    switch(col)
    {
        case Black:
        return "\033[22;30m"+text;

        case White:
        return "\033[01;37m"+text;

        case Red:
        return "\033[22;31m"+text;

        case Green:
        return "\033[22;32m"+text;
    }
}
};

class FileIO
{
public:
static vector<string> ReadFile(char* filename)
{
    vector<string> vec;

    ifstream fileStream(filename);

    string line;

    if(fileStream.is_open())
    {
        while(!fileStream.eof())
        {
            getline(fileStream, line);
            vec.push_back(line);
        }

        fileStream.close();
    }

    return vec;
}

static string ReadLine(char* filename, uint Line)
{
    int lineCount = 0;

    ifstream fileStream(filename);

    string line = "";

    if(fileStream.is_open())
    {
        while(!fileStream.eof())
        {
            lineCount++;
            getline(fileStream, line);

            if(lineCount == Line)
            {
                return line;
            }
        }

        fileStream.close();
    }

    return line;
}

static bool FileExists(char* filename)
{
    ifstream fileStream(filename);

    if(fileStream.is_open())
    {
        fileStream.close();
        return true;
    }

    return false;
}

static void PrintFileContents(char* filename)
{
    vector<string> vec = FileIO::ReadFile(filename);

    for(int i=0;i<vec.size();i++)
    {
        string tmp = vec[i];
        cout<<tmp<<endl;
    }
}

static void PrintVectorContents(vector<string> &vec)
{
    for(int i=0;i<vec.size();i++)
    {
        string tmp = vec[i];
        cout<<tmp<<endl;
    }
}

static const char* FormatFileLoc(char* fileloc)
{
    string s = fileloc;
    int pos = s.find_last_of("/");
    int pos2 = s.find_last_of("\\");

    if(pos>pos2)
    {
        s = s.substr((size_t)pos+1,(size_t)s.size());
    }
    else if(pos2>pos)
    {
        s = s.substr((size_t)pos2+1,(size_t)s.size());
    }

    return s.c_str();
}
};

class Search
{
public:
static LineWord_INFO FindMatch(string stringToFind, vector<string> &s)
{
    LineWord_INFO lw = {0}; // set all elements of struct to 0 (if not, numbers at end are rubbish).

    for(int i=0;i<s.size();i++)
    {
        bool foundOnLine=false;
        size_t wordPos = 0;

        string tmp = s[i];
        string caseIStr = StringManipulation::StringToUpper(tmp); // uppercase version of the string being searched

        string caseIStrFind = StringManipulation::StringToUpper(stringToFind);  // upercase version of string to find

        vector<int> myVec;

        while(wordPos != string::npos)
        {
            if(CASE_INSENSITIVE)
            {
                wordPos = caseIStr.find(caseIStrFind,wordPos);
            }
            else
            {
                wordPos = tmp.find(stringToFind,wordPos);
            }

            // If youre not at the end of the string, and have found an instance, add its position to the vector
            // and increment the word count by one. Set the word position to word position + length of string to find.
            if(wordPos != string::npos)
            {
                lw.WordCount++;
                myVec.push_back(wordPos);
                wordPos += stringToFind.length();
                foundOnLine=true;
            }
            else   // at end of file
            {
                string final;
                if(foundOnLine)   // if you found 1 or more instances of string to find
                {
                    final += tmp.substr(0,myVec[0]); // First, add the string from position 0 to the start of the first instance

                    // For each of the instances found, add it to the final string
                    for(int j=0;j<myVec.size();j++)
                    {
                        final += Color::SetTextColor(Green,tmp.substr(myVec[j],stringToFind.length()));  // Add the instance of string to find
                        int nextword = myVec[j] + stringToFind.length(); // End of current instance
                        int nw = myVec[j+1] - nextword; // Where the next word is

                        final+= Color::SetTextColor(Black,tmp.substr(nextword,nw)); // Add the text from the end of the current instance, to start of next
                    }

                    if(!QUIET)
                    {
                        cout<<"Line "<<i+1<<": "<<final<<endl;
                    }

                    lw.LineCount++;
                }
            }
        } // End of while loop (loop while not at end of line)
    } // End of loop of vector contents

    return lw;
    }
};

void PrintUsageInfo(const char* PROGRAMNAME)
{
    cout<<"Usage:\t"<<PROGRAMNAME<<" [options] [stringToMatch] [input]\n"
    <<"1)\t-h -h Display usage information\n"
    <<"2)\t-nc Disable colored text\n"
    <<"3)\t-q Quiet mode. File contents containing the location of the string to match are not printed\n"
    <<"4)\t-ci Case Insensitive Search enabled\n\n"
    <<"Options 2, 3 and 4 can be executed together. For example, to run a Case Insensitive Search in Quiet mode, use the option -qci\n";
}

void ProcessArgs(int argc, const char* argv[])
{
    PROGRAM_NAME = FileIO::FormatFileLoc((char*)argv[0]);

    if(argc == 1) exit(0); // If only 1 argument (program name), exit

    if(argc == 2)
    {
        string tmp = argv[1];
        if(tmp == "-h") // if theres 2 arguments, check the second to see if its "-h". If so, print usage info and exit, else exit immediately.
        {
            PrintUsageInfo(FileIO::FormatFileLoc((char*)argv[0]));
            exit(0);
        }
        exit(0);
    }

    if(argc == 3)
    {
        MATCH = (char*)argv[1];
        INPUT_CONTENT = (char*)argv[2];
        return;
    }

    if(argc >= 4)
    {
        string tmp = (string)argv[1];

        const char* myChar = tmp.c_str();

        if(myChar[0] != '-')
        {
            cout<<"The character \"-\" must precede any options\n"<<endl;
            PrintUsageInfo(FileIO::FormatFileLoc((char*)argv[0]));
            exit(0);
        }

        size_t foundQ, foundNC, foundCI;

        foundQ = tmp.find("q");
        foundNC = tmp.find("nc");
        foundCI = tmp.find("ci");

        if(foundQ != string::npos) QUIET = true;
        if(foundNC != string::npos) COLOR_ENABLED = false;
        if(foundCI != string::npos) CASE_INSENSITIVE = true;

        MATCH = (char*)argv[2];
        INPUT_CONTENT = (char*)argv[3];
    }
}

int main(int argc, const char* argv[])
{
    ProcessArgs(argc,argv);

    vector<string> inputVector; // vector for the file to be read and/or the string entered (both checked)

    if(FileIO::FileExists(INPUT_CONTENT))
    {
        cout<<"A file with the name "<<INPUT_CONTENT<<" was found. This will be searched\n";
        if(!QUIET) cout<<endl;  // If not in quiet mode, add another line (improves readability)
        inputVector = FileIO::ReadFile(INPUT_CONTENT);
        LineWord_INFO lw = Search::FindMatch(MATCH, inputVector);

        if(lw.WordCount > 0)
        {
            if(!QUIET) cout<<endl;  // If not in quiet mode, add another line (improves readability)
            cout<<lw.WordCount<<" instance(s) of the string "<<MATCH<<" were found in the file "
            <<INPUT_CONTENT<<" on "<<lw.LineCount<<" lines"<<endl;

        }
    }

    inputVector.clear();

    inputVector.push_back(INPUT_CONTENT);
    LineWord_INFO lwINFO = Search::FindMatch(MATCH, inputVector);

    if(lwINFO.WordCount > 0)
    {
        cout<<lwINFO.WordCount<<" instance(s) of the string "<<MATCH<<" were found in the input string "<<INPUT_CONTENT<<endl;
    }

    return 0;
}

```

Usage (from Usage command):

```
Usage:	grepchallenge [options] [stringToMatch] [input]
1)	-h -h Display usage information
2)	-nc Disable colored text
3)	-q Quiet mode. File contents containing the location of the string to match are not printed
4)	-ci Case Insensitive Search enabled

Options 2, 3 and 4 can be executed together. For example, to run a Case Insensitive Search in Quiet mode, use the option -qci
```

---

### Post by matmatmat on 2009-06-30
Extremely simple one:
```

import re
import sys
if len(sys.argv) == 3:
        f = open(sys.argv[2], "r")
        count = 1
        ocount = 0
        for line in f.readlines():
                if re.search(sys.argv[1], line):
                        ocount += 1
                        print "LINE %i: %s" % (count, line.strip('\n'))
                count += 1
        print "### %i orcurrences of string %s" % (ocount, sys.argv[1])

```
trying to work out optparse now!

---

### Post by johnl on 2009-06-30
Hacked this together; compile with -std=gnu99 on gcc. 

```

#define _GNU_SOURCE /* getline */

#include <stdlib.h>
#include <stdio.h>
#include <unistd.h>
#include <stdbool.h>
#include <regex.h>


/* maximum number of files we will search */
#define MAX_FILES 512
/* number of files specified on CLI */
static int   file_count = 0;
static const char* file[MAX_FILES];

/* colorize matches ? */
static bool  color = false;
/* invert matches ? */
static bool  invert = false;

static bool check_match (const char* hay, regex_t* needle, const char* file,
                         size_t line);


static void show_usage(const char* prog) 
{
    printf("usage: %s -f <input-file> -s <search> [-i -c -v]\n", prog);
    printf("-f <input-file>   file to search. more than one -f is allowed\n");
    printf("-s <search>       search pattern (regular expression)\n");
    printf("-i                [optional] ignore case\n");
    printf("-c                [optional] highlight match\n");
    printf("-v                [optional] invert match (print non-matches)\n");
}


int main(int argc, char* argv[]) 
{
    int opt;
    regex_t rex;
    const char* search = NULL;
    int regex_opts = 0;
    
    while((opt = getopt(argc, argv, "f:s:civ")) != -1) {
        switch(opt) {
        case 'f':
            /* store argument as an input file */
            file[file_count++] = optarg;
            break;
        case 's':
            /* store search pattern */
            search = optarg;
            break;
        case 'c':
            /* set color flag */
            color = true;
            break;
        case 'i':
            /* set ignore case */
            regex_opts = REG_ICASE;
            break;
        case 'v':
            /* set invert flag */
            invert = true;
            break;
        default:
            show_usage(argv[0]);
            return -1;
        }
    }

    /* make sure we got a search pattern */
    if (!search) {
        printf("you must specify a search expression with -s\n");
        return 1;
    }
    /* make sure it's a valid search pattern */
    if (regcomp(&rex, search, REG_EXTENDED | regex_opts)) {
        printf("invalid regular expression: '%s'\n", search);
        return 1;
    }
            
    /* total number of times we match the pattern */
    size_t total_matches = 0;
    /* number of files that that match the pattern */
    size_t file_matches  = 0;
    
    /* foreach input file, check line-by-line for a match */
    for(int i = 0; i < file_count; ++i) {
        FILE* fp = fopen(file[i], "r");
        if (!fp) {
            perror(file[i]);
            continue;
        }
        char* buf = NULL;
        size_t size = 0;
        size_t line = 1;
        bool   this_file_matches = false;
        /* getline will malloc() and realloc() as necessary */
        while(getline(&buf, &size, fp) != -1) {
            if (check_match(buf, &rex, file[i], line)) {
                total_matches++;
                this_file_matches = true;
            }        
            line++;
        }
        /* free memory allocated by getline() */
        if (buf) {
            free(buf);
        }
        fclose(fp);

        if (this_file_matches) {
            file_matches++;
        }
    }

    /* print a summary */
    printf("%zu line%s match; %zu file%s match%s\n",
           total_matches, (total_matches != 1 ? "s" : ""),
           file_matches,  (file_matches  != 1 ? "s" : ""),
           (file_matches  != 1 ? "" : "es"));
    
    regfree(&rex);
    
    return 0;
}

static bool check_match(const char* hay, regex_t* needle, const char* file,
                        size_t line) 
{
    regmatch_t match;
    int result = regexec(needle, hay, 1, &match, 0);

    /* if we matched (or didn't match with -v), print the result */
    if (result != REG_NOMATCH || (result == REG_NOMATCH && invert)) {

        printf("%s:%zu\t", file, line);
        
        if (color) {
            /* if color is specified, highlight the matching string in green */
            for(int i = 0; i < match.rm_so; ++i) {
                putchar(hay[i]);
            }
            
            printf("\033[0;40;32m");
            for(int i = match.rm_so; i < match.rm_eo; ++i) {
                putchar(hay[i]);
            }
            printf("\033[0m");
            
            for(int i = match.rm_eo; hay[i]; ++i) {
                putchar(hay[i]);
            }
        } else {
            /* otherwise just print it. */
            printf("%s", hay);
        }
        return true;
    }

    return false;
}

```

Features:

* Match multiple files
* Uses regular expression matching
* Match highlighting
* Ignore case option
* Invert match option


Example:
```

ledbettj@reznor:~/Projects/mygrep$ ./mygrep -f /usr/share/dict/american-english -s "^z(w|y)" -c -i

/usr/share/dict/american-english:18088  [COLOR="Lime"]Zw[/COLOR]ingli
/usr/share/dict/american-english:18089  [COLOR="Lime"]Zw[/COLOR]ingli's
/usr/share/dict/american-english:18090  [COLOR="Lime"]Zw[/COLOR]orykin
/usr/share/dict/american-english:18091  [COLOR="Lime"]Zw[/COLOR]orykin's
/usr/share/dict/american-english:18092  [COLOR="Lime"]Zy[/COLOR]rtec
/usr/share/dict/american-english:18093  [COLOR="Lime"]Zy[/COLOR]rtec's
/usr/share/dict/american-english:18094  [COLOR="Lime"]Zy[/COLOR]uganov
/usr/share/dict/american-english:18095  [COLOR="Lime"]Zy[/COLOR]uganov's
/usr/share/dict/american-english:98550  [COLOR="Lime"]zw[/COLOR]ieback
/usr/share/dict/american-english:98551  [COLOR="Lime"]zw[/COLOR]ieback's
/usr/share/dict/american-english:98552  [COLOR="Lime"]zy[/COLOR]gote
/usr/share/dict/american-english:98553  [COLOR="Lime"]zy[/COLOR]gote's
/usr/share/dict/american-english:98554  [COLOR="Lime"]zy[/COLOR]gotes
13 lines match; 1 file matches

```

---

### Post by Psycam on 2009-07-01
Threw this together. Trying to learn PHP, so bear with me...

(Copy into php file, run on any php-enabled server).

[PHP]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Challenge Six</title>
</head>

<body>
<!-- This is the form itself for uploading and searching -->
<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="post" enctype="multipart/form-data">
<label for="file">Filename:</label>
<input type="file" name="file" id="file" /> 
<br />
Search String: <input type="text" name="string" />
<br />
Line numbers: <input type="checkbox" value="Yes" name="lineNum">
Inverted: <input type="checkbox" value="Yes" name="inverted">
Case Insensitive: <input type="checkbox" value="Yes" name="caseIgnore">
Job Summary: <input type="checkbox" value="Yes" name="summary"><br />
<input type="submit" name="submit" value="PHP-Grep it!"/>
</form>

<br /><br />

<?php
	/* The following code will be run if the form has been submitted */
	if (isset($_POST['submit']))
	{
		/* Uploaded file, check for errors, otherwise returns information */
		if ($_FILES["file"]["error"] > 0)
 		{
  			echo "Error: " . $_FILES["file"]["error"] . "<br />";
			echo "Something went wrong, did you upload a readable file?";
			die();
  		}elseif ($_FILES["file"]["size"] > 2000000)
		{
			echo "Try to keep file under 2mb";
			die();
                }
		/* Didn't put anything as search term warning */
		elseif ($_POST["string"] == "")
		{
			echo "Put something in the search string!";
			die();
		}
		else // Now run search
  		{
  			echo "Uploaded: " . $_FILES["file"]["name"] . "<br />";
  			echo "Size: " . ($_FILES["file"]["size"] / 1024) . " Kb<br /><br/>";
			$file = fopen($_FILES["file"]["tmp_name"], "r");
  		}
		/* Declare variables based on input */
		$string = $_POST["string"];
		$lineNum = $_POST["lineNum"];
		$summary = $_POST["summary"];
		$inverted = $_POST["inverted"];
		$caseIgnore = $_POST["caseIgnore"];
		$line = "";
		$lineCounter = 0; // counter for lines searched
		$numMatched = 0; // counter for lines matched
		
		/* Loop while not at end of file */
		while(!feof($file))
 		{
			$lineCounter++;
			$line = fgets($file); // Read next line 
			if($inverted != "")
			{
				if($caseIgnore != "")
				{
					if(!preg_match("/" . $string . "/i",$line))
					{
						if($lineNum == "Yes")
						{
						echo "Line " . $lineCounter . ": ";
						}
						echo $line . "<br />";
						$numMatched++;
					}
				}else
				{
					if(!preg_match("/" . $string . "/",$line))
					{
						if($lineNum == "Yes")
						{
						echo "Line " . $lineCounter . ": ";
						}
						echo $line . "<br />";
						$numMatched++;
					}
				}
			}else
			{
				if($caseIgnore != "")
				{
					if(preg_match("/" . $string . "/i",$line))
					{
						if($lineNum == "Yes")
						{
						echo "Line " . $lineCounter . ": ";
						}
						echo $line . "<br />";
						$numMatched++;
					}
				}else
				{
					if(preg_match("/" . $string . "/",$line))
					{
						if($lineNum == "Yes")
						{
						echo "Line " . $lineCounter . ": ";
						}
						echo $line . "<br />";
						$numMatched++;
					}
				}
			}
		}
		echo "<br /><br />";
		
		/* Job Summary Stuff */
		if($summary != "")
		{
			echo "Job Summary:<br />";
			echo "Search query: " . $string . "<br />";
			echo "Options used: ";
			if($lineNum != "") echo "(Line numbers) ";
			if($inverted != "") echo "(Inverted) ";
			if($caseIgnore != "") echo "(Case Insensitive) ";
			echo "(Job Summary)";
			echo "<br />";
			echo "Total number of lines in file: " . $lineCounter . "<br />";
			echo "Total number of lines matched: " . $numMatched . "<br />";
			
		}
	}
?>

</body>
</html>[/PHP]

---

### Post by Nemooo on 2009-07-01
Okay here is my final entry. Still basic C, but with some more options.

My main focus wan't a lot of features, but a simple working implementation - well moduralised and commented. Just for learning I didn't use any libraries, but stdio.h so there are a few homemade string functions.

[php]#include <stdio.h>

struct grep_opt {
	char *str;
	char *file;
	FILE *in;
	FILE *out;
	int case_sens;
	int invert;
	int bufsize;
};

/* Name str_len - str (cont char *)
 *
 * Purpose: Find the length of str, discluding the terminating '\0'.
 *
 * Return: The length of str.
 *
 */
int str_len(const char str[])
{
	int len = 0;

	while (str[len] != '\0')
		++len;

	return len;
}

/* Name: str_intify - str (const char *)
 *
 * Purpose: Convert the string to an integer.
 *
 * Return: The converted number.
 *         -1 if an nondigit is encountered.
 */
int str_intify(const char str[])
{
	int num = 0;
	int len = str_len(str) - 1;
	int factor = 1;

	while (len >= 0) {
		if (str[len] < '0' || str[len] > '9')
			return -1;

		num += ((str[len] - '0') * factor);
		--len;
		factor *= 10;
	}
	return num;
}

/* Name: str_copy - src (const char *)
 *                  dst (const char *)
 *
 * Purpose: Copy the string src to dst.
 */
void str_copy(const char *src, char *dst)
{
	while ((*dst++ = *src++) != '\0');
}

/* Name: str_comp - str_one (const char *)
 *                  str_two (const char *)
 *
 * Purpose: Compare two strings for equality. Comparison will only last as far
 *          as the shortest string.
 *
 * Return: The number of equal letters, if the strings are equal.
 *         0 otherwise.
 */
int str_comp(const char str_one[], const char str_two[])
{
	int i = 0;

	while (str_one[i] != '\0' && str_two[i] != '\0') {
		if (str_one[i] == str_two[i])
			++i;
		else
			return 0;
	}
	return i;
}

/* Name: str_lower - str (char *)
 *
 * Purpose: Lowercase str.
 */
void str_lower(char *str)
{
	while (*str++ != '\0')
		if (*str >= 'A' && *str <= 'Z')
			*str += ('a' - 'A');
}

/* Name: str_sub - text (const char *)
 *                 str (const char *)
 *                 case_sens (const int)
 *
 * Purpose: Check if str is a substring of text.
 *
 * Return: 1 if str is a substring of text.
 *         0 otherwise.
 */
int str_sub(const char *text, const char *str)
{
	while (*text++ != '\0')
		if (str_comp(text, str))
			return 1;

	return 0;
}

/* Name: check_bound - str (const char *)
 *                     stream (FILE *)
 *
 * Purpose: Check if there is in left in stream, and "eat" it, so it isn't
 *          read in next time (use with grep).
 *
 * Return: 1 if an occurence of '\n' was found in str.
 *         0 otherwise.
 */
int check_bound(const char *str, FILE *stream)
{
	while (*str != '\n' && *str != '\0')
		++str;

	if (*str != '\n') {
		while (getc(stream) != '\n');
		return 0;
	}
	return 1;
}

/* Name: grep - conf (const struct grep_opt *)
 *
 * Purpose: Lower the strings if case sensitivity is off, and feed sub_str with
 *          lines from in. Print results to conf->out.
 *
 * Return: The number of mathces found in the file.
 */
int grep(const struct grep_opt *conf)
{
	char text[conf->bufsize];
	char lower_text[conf->bufsize];
	char lower_str[conf->bufsize];
	int matches = 0;
	int line, newline;

	for (line = 1; fgets(text, conf->bufsize, conf->in) != NULL; ++line) {
		newline = check_bound(text, conf->in);
		str_copy(text, lower_text);
		str_copy(conf->str, lower_str);

		if (conf->case_sens == 0) {
			str_lower(lower_text);
			str_lower(lower_str);
		}
		if (str_sub(lower_text, lower_str) != conf->invert) {
			fprintf(conf->out, "%d:\t%s", line, text);
			++matches;

			if (newline == 0)
				putchar('\n');
		}
	}
	return matches;
}

/* Name: help - prg_name (const char *)
 *
 * Purpose: Print help information.
 */
void help(const char *prg_name)
{
	printf("Usage:\t%s 'string' file [options]\n\n", prg_name);

	printf("Search for 'string' in file and print the lines");
	printf(" where 'string' occurs.\n\n");

	printf("Options:\n");
	printf("\t-h\t\tDisplay this information.\n");
	printf("\t-o <file>\tOutput results to <file> (default is stdout).\n");
	printf("\t-c\t\tSearch is case sensitive (default is insensitive).\n");
	printf("\t-i\t\tOutput the lines where 'string' does not occur.\n");
	printf("\t-l <num>\tSet the maximum length of a line");
	printf(" (default is 512).\n");
}

/* Name: main - argc (int)
 *              argv (char **)
 *
 * Purpose: Process commandline arguments and send them to grep.
 *
 * Return: 0 if files were opened succesfully.
 *         1 if an error occured.
 */
int main(int argc, char *argv[])
{
	struct grep_opt conf;

	if (argc < 3 && !str_comp(argv[1], "-h")) {
		fprintf(stderr, "Too few arguments. Try %s -h.\n", argv[0]);
		return 1;
	}
	conf.str = argv[1];
	conf.file = argv[2];
	conf.in = fopen(argv[2], "r");
	conf.out = stdout;
	conf.invert = 0;
	conf.case_sens = 0;
	conf.bufsize = 513;

	for (int i = 1; i < argc; ++i) {
		if (str_comp(argv[i], "-h") || str_comp(argv[i], "--help")) {
			help(argv[0]);
			return 0;
		} else if (str_comp(argv[i], "-o")) {
			conf.out = fopen(argv[++i], "w");
		} else if (str_comp(argv[i], "-c")) {
			conf.case_sens = 1;
		} else if (str_comp(argv[i], "-i")) {
			conf.invert = 1;
		} else if (str_comp(argv[i], "-l")) {
			conf.bufsize = str_intify(argv[++i]) + 1;
		}
	}
	if (conf.in == NULL || conf.out == NULL) {
		perror("Error");
		return 1;
	}
	fprintf(conf.out,
		"Lines containing '%s' in %s:\n\n",
		conf.str, conf.file);
	fprintf(conf.out,
		"\n%d occurences of '%s' was found in %s.\n",
		grep(&conf), conf.str, conf.file);
	fclose(conf.in);
	fclose(conf.out);

	return 0;
}[/php]

```
Usage:	my-grep 'string' file [options]

Search for 'string' in file and print the lines where 'string' occurs.

Options:
	-h		Display this information.
	-o <file>	Output results to <file> (default is stdout).
	-c		Search is case sensitive (default is insensitive).
	-i		Output the lines where 'string' does not occur.
	-l <num>	Set the maximum length of a line (default is 512).
```

---

### Post by jimi_hendrix on 2009-07-04
heres mine:

```

(require 'cl-ppcre)

(defun grep (regex)
 (loop for line = (read-line *standard-input* nil)
    for i from 0
    while line do
      (when (not (eql (cl-ppcre:scan regex line) nil)) ;easier to test against not nil (false) here
    (format t "Found on line ~D in: ~A~%" i line))))

(defun main ()
  (when (< (length *posix-argv*) 2)
    (write-line "USAGE: grep <regex>"))
  (grep (second *posix-argv*)))

;;;not part of the actual code, instead it will stop your sbcl session and save it as an executable
(sb-ext:save-lisp-and-die
 "lispgrep"
 :toplevel #'main
 :executable t)

```it will run anywhere you have cl-ppcre installed.  The last bit is sbcl specific, it will save the lisp session as an executable.  However, these tend to be big for small programs because the compiler and debugger is packed in there

EDIT: mine works like normal grep so:
```

cat file | ./lispgrep

```

---

### Post by ratmandall on 2009-07-05
[php]
import sys

if len(sys.argv) != 3:
    print "Please provide at least/most 2 arguments\ne.g. %s string2find file2search" % sys.argv[0]
    sys.exit(1)
    
else:
    string = sys.argv[1]
    file = sys.argv[2]

buffer, found, lines = open(file).read().split("\n"), [], 0

for str in buffer:
    lines += 1
    if str.find(string) != -1:
        found.append("Line %s: %s" % (lines, str))

print '\n'.join(found)
[/php]

```

search.py string file

```

---

### Post by ghostdog74 on 2009-07-05
> **ratmandall said:**
> [php]
...
    if str.find(string) != -1:
        found.append("Line %s: %s" % (lines, str))

...
[/php]

```

search.py string file

```

the more pythonic way nowadays is just the "in" operator, instead of find()
```

if "pattern" in line:

```

---

### Post by baizon on 2009-07-05
Java:
```
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.LineNumberReader;
import java.io.Reader;
import java.net.URI;
import java.net.URISyntaxException;

public class JavaGrep {

	public static void main(String[] args) {
		if ((args.length == 0) || (args.length > 2)) {
			System.out.println("Usage: java JavaGrep <string> [<filename>]");
			System.exit(0);
		}
		try {
			Reader d;
			if (args.length == 2) {
				URI uri = ClassLoader.getSystemClassLoader().getResource(args[1]).toURI();
				File f = new File(uri);
				d = new FileReader(f);
			} else {
				d = new InputStreamReader(System.in);
			}
			LineNumberReader reader = new LineNumberReader(d);
			String text;
			while ((text = reader.readLine()) != null) {
				if (text.indexOf(args[0]) == 0) {
					System.out.println("Line: "+ reader.getLineNumber() + ": " + text);
				}
			}
		} catch (IOException e) {
			System.err.println(e);
		} catch (URISyntaxException e) {
			System.err.println(e);
		} catch (NullPointerException e) {
			System.err.println("Wrong File: "+ args[1]);
		}
	}
}

```
Saw today the challenge, so it's a quick solution(15min) and not the most beautiful :p
Execution:
```
java JavaGrep String File
```

---

### Post by sdennie on 2009-07-06
[s]Second submission before tinivole closes it:

[noparse]```

#!/bin/sh

grep $@

```[/noparse][/s]

---

### Post by jimi_hendrix on 2009-07-06
> **sdennie said:**
> [s]second submission before tinivole closes it:

[noparse]```

#!/bin/sh

grep $@

```[/noparse][/s]

rofl

---

### Post by ibuclaw on 2009-07-07
Okie Doke.

Challenge is now over, and the thread is closed while I sift through them. :)

Will re-open the thread announcing the winner shortly.

Regards
Iain

---

### Post by ibuclaw on 2009-07-07
**Winner**: **[sdennie]("http://ubuntuforums.org/showpost.php?p=7516954&postcount=3")** for his submission in Perl.
Perhaps not a beginner as this thread title suggests, but it is certainly the most feature rich and bug-free implementation that is in a world of it's own, quite literally.

Your punishment, think of what to do for the next challenge. :D


**Runner up**: **[johnl]("http://ubuntuforums.org/showpost.php?p=7542098&postcount=12")** for his submission in GNU99 C.
This program made me smile. I mean, even whitespace gets highlighted! (possibly an accidental feature).
The only thing stopping it from winning this competition was that it didn't search lines recursively. So if a pattern was present on a line more than once, only the first instance would get highlighted, which is a shame, as other than that it is a very solid application.

For everyone else, I am impressed. Except for **[jimi_hendrix]("http://ubuntuforums.org/showpost.php?p=7560270&postcount=15")**, to whom wins nothing as his submission was the only one that I couldn't get running/working.


Regards
Iain

---

### Post by sdennie on 2009-07-07
> **tinivole said:**
> **Winner**: **[sdennie]("http://ubuntuforums.org/showpost.php?p=7516954&postcount=3")** for his submission in Perl.
Perhaps not a beginner as this thread title suggests, but it is certainly the most feature rich and bug-free implementation that is in a world of it's own, quite literally.

Your punishment, think of what to do for the next challenge. :D


```

#!/usr/bin/perl

push @mouth, $foot and say "Ugh";

```

---

### Post by jimi_hendrix on 2009-07-07
> **tinivole said:**
> 
For everyone else, I am impressed. Except for **[jimi_hendrix]("http://ubuntuforums.org/showpost.php?p=7560270&postcount=15")**, to whom wins nothing as his submission was the only one that I couldn't get running/working.


i blame you for not googling how to install a common lisp library via asdf-install

---

