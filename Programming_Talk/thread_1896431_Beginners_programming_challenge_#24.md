---
title: "Beginners programming challenge #24"
date: 2011-12-16
forum: Programming Talk
---

### Post by epicoder on 2011-12-16
_[SIZE=4][COLOR=Red]Welcome to the 24th Beginners programming challenge.[/COLOR][/SIZE]_

The challenge is to create a text content analyzer. This is a tool used by writers to find statistics such as word and sentence count on essays or articles they are writing.

Write a program that analyzes input from a file, essay.txt, and compiles statistics on it.
The program should output:

[LIST=1]
[*]The total word count
[*]The count of unique words
[*]The number of sentences
[/LIST]
Example output, using the attached essay.txt:
```
analyze
Total word count: 468
Unique words: 223
Sentences: 38
```
_**Cookie points**_

Cookie points will be awarded for the following extras:

[LIST=1]
[*]The ability to calculate the average sentence length in words
[*]The ability to find often used phrases (a phrase of 3 or more words used over 3 times)
[*]A list of words used, in order of descending frequency
[*]The ability to accept input from STDIN, or from a file specified on the command line.
[/LIST]

_***Disqualified Entries:***_

Any overly obfuscated code will be immediately disqualified without   account for programmer's skill. Please remember that these challenges are   for beginners and therefore the code should be easily readable and  well  commented.

Any non-beginner entries will not be judged. Please use common sense   when posting code examples. Please do not give beginners a copy paste   solution before they have had a chance to try this for themselves.

BASH programmers are NOT allowed to use wc. :P

If your program calculates the lexical density or gunning fog index, then you are not a beginner and your entry won't be judged.


_***Assistance:***_

If you require any help with this challenge please do not hesitate to   come and chat to the development focus group. They have a channel on   irc.freenode.net #ubuntu-beginners-dev

---

### Post by schauerlich on 2011-12-17
What defines a "sentence"? A string that ends in [.?!] possibly inside quotation marks?

---

### Post by lisati on 2011-12-17
> **schauerlich said:**
> What defines a "sentence"? A string that ends in [.?!] possibly inside quotation marks?

That's part of the fun/challenge of coming up with solutions, deciding how to define how your program copes with different situations.

---

### Post by schauerlich on 2011-12-17
> **lisati said:**
> That's part of the fun/challenge of coming up with solutions, deciding how to define how your program copes with different situations.

But should this count as one sentence or two?

> "'This is Unix, I know this!' exclaimed the girl as as the raptors clawed at the door, bringing her ever closer to her inevitable demise."

It could be argued either way, and if we're being judged on correctness, having a definition of correct is important.

---

### Post by schauerlich on 2011-12-17
No wc you say? Challenge accepted.

```
#!/bin/bash

# NF contains the number of "fields" (whitespace delimited strings) in each line. Summing
# this for every line will give you the word count.
awk '{w += NF} END {print "Total word count: " w}' $1

# For every word on each line, print it (ie separate it on stdin with a newline)
# change all upper case to lower case
# remove all punctuation
# sort it
# remove duplicates
# print the number of words left
awk '{for (i = 1; i <= NF; i++) print $i}' $1 | tr '[A-Z]' '[a-z]' | tr -d '[:punct:]' | sort | uniq | awk '{l += 1} END {print "Unique words: " l}'

# find all occurrences of '.', '!' or '?' optionally followed by any number of quotes. Print
# how many there are.
grep -o '[.!?]['\''"]*' $1 | awk '{l += 1} END {print "Sentences: " l}'
```

```

$ 24.sh essay.txt 
Total word count: 468
Unique words: 223
Sentences: 38
```

---

### Post by schauerlich on 2011-12-17
And in python:

```
import os
import sys
import re
import string

def clean_text(s):
    """Make text lower case, and remove all punctuation."""
    return re.sub("[%s]" % re.escape(string.punctuation), '', s.lower())

def main():
    words = []

    # Make a list of each word in the file
    with open(sys.argv[1], "r") as f:
        for line in f:
            words.extend(line.split())
            
    print "Total word count:", len(words)

    # We need to "clean" the text in order to remove potential duplicates.
    # for example, "Cat", "cat", and "cat." would all show up as different
    # when for our purposes they are the same. appling clean_text will make
    # all of these "cat" so they appear identical.
    words_clean = map(clean_text, words)
    
    # By turning it into a set, we remove all duplicates. Therefore, the
    # length of this set is the number of unique words in the file.
    print "Unique words:", len(set(words_clean))

    sentences = 0
    for word in words:
        # If a word ends in ".", "!" or "?" (potentially followed by any 
        # number of quotation marks), we should count it as the end of a 
        # sentence.
        if re.search(r'[.!?][' "'" '"]*', word):
            sentences += 1

    print "Sentences:", sentences

if __name__ == "__main__":
    main()
```

---

### Post by epicoder on 2011-12-17
> **schauerlich said:**
> But should this count as one sentence or two?



For the purposes of this challenge, I'll count it as two sentences. 
@schauerlich If your earlier entries differ, don't worry about it. The whole point is to get people programming, and not to worry about insignificant discrepancies between the entries.

---

### Post by cgroza on 2011-12-17
My solution in Haskell.
Compile with ghc filename.hs
Written in point free style as much as possible :D.
```

module Main where 
import Control.Monad.Instances
import Data.Char
import Data.List
import System.IO
import System (getArgs)

-- Removes punctuation marks. Words function could count them too.
removePunctuation :: String -> String
removePunctuation = filter (not . isPunctuation)

countWords, countUniqueWords, countSentences :: String -> Int
-- Counts words, removing punctuation first.
countWords = length . words . removePunctuation

-- Counts unique words, removing punctuation first.
countUniqueWords = length . nub . words . map toLower . removePunctuation

-- Counts sentences by looking for ";.?!" marks.
countSentences = length . filter (`elem` ";.?!")

-- Analyzes input using above functions.
analyze :: String -> [(String, Int)]
analyze = zip attributes . sequence [countWords, countUniqueWords, countSentences]
            where attributes = ["Total Word Count: ", "Unique Words: ", "Sentences: "]

main :: IO ()
main = do args <- getArgs
          analyzeAndPrint =<< (if null args then hGetContents stdin else readFile $ head args)
            where analyzeAndPrint :: String -> IO ()
                  analyzeAndPrint = mapM_ (putStrLn . \(a,v) -> a ++ show v) . analyze



```

---

### Post by roccivic on 2011-12-17
My entry in PERL:

```
**[COLOR="Gray"]#!/usr/bin/perl -s[/COLOR]**
**use** warnings;

[COLOR="Gray"]# Buffer the input here[/COLOR]
**my** [COLOR="DarkGreen"]$buffer[/COLOR];

[COLOR="Gray"]# Function to process the buffer and output statistics[/COLOR]
**sub** process {
    [COLOR="Gray"]# Create an array of words, including ones with ' and - in them.[/COLOR]
    **my** [COLOR="DarkGreen"]@arr[/COLOR] = [COLOR="DarkGreen"]$buffer[/COLOR] =~ [COLOR="Red"]m/\w+'?-?\w*/g[/COLOR];
    [COLOR="DarkRed"]print[/COLOR] [COLOR="Magenta"]"Words: "[/COLOR] . [COLOR="DarkRed"]scalar[/COLOR][COLOR="DarkGreen"] @arr[/COLOR] . [COLOR="Magenta"]"\n"[/COLOR]; [COLOR="Gray"]# print number of array elements

    # Map the array onto a hash. Since hash keys (which are converted to lowercase)
    # cannot have duplicates we get number of uniques words. As the values for each key
    # we use the number of occurences of the word[/COLOR]
    **my** [COLOR="DarkGreen"]%hash[/COLOR];
   [COLOR="DarkGreen"] %hash[/COLOR] = [COLOR="DarkRed"][/COLOR][COLOR="DarkRed"]map[/COLOR] { [COLOR="DarkRed"]lc[/COLOR]([COLOR="DarkGreen"]$_[/COLOR]), ++[COLOR="DarkGreen"]$hash{ [COLOR="DarkRed"]lc[/COLOR][COLOR="Black"]([/COLOR][COLOR="DarkGreen"]$_[/COLOR][COLOR="Black"])[/COLOR] }[/COLOR] } [COLOR="DarkGreen"]@arr[/COLOR];
    [COLOR="DarkRed"]print[/COLOR] [COLOR="Magenta"]"Unique Words: "[/COLOR] . [COLOR="DarkRed"]keys[/COLOR] ([COLOR="DarkGreen"]%hash[/COLOR]) . [COLOR="Magenta"]"\n"[/COLOR];[COLOR="Gray"] # print number of keys

    # The number of sentences is given by the number of regex matches.
    # Match at least one of ".!?", but potentially more consequent
    # occurences, so that we don't count stuff like "..." or "!?"
    # as mulitple sentences. =()= is the goatse operator used to
    # assign values coming from the right to an anonymous array and
    # then getting the number of elements of that array from the left.[/COLOR]
    **my**[COLOR="DarkGreen"] $sentences[/COLOR] =()= [COLOR="DarkGreen"]$buffer[/COLOR] =~ [COLOR="Red"]m/[\.\!\?]+/g[/COLOR];
    [COLOR="DarkRed"]print[/COLOR] [COLOR="Magenta"]"Sentences: [COLOR="DarkGreen"]$sentences[/COLOR]\n"[/COLOR];

    [COLOR="Gray"]# Print the most used words if the user called
    # the program with the -f switch at command line[/COLOR]
    **if** ([COLOR="DarkGreen"]$f[/COLOR]) {
        [COLOR="DarkRed"]print[/COLOR] [COLOR="Magenta"]"Most used words:\n"[/COLOR];
       [COLOR="Gray"] # reverse sort the hash of words by value, which the number of occurences[/COLOR]
        **foreach** ([COLOR="DarkRed"]reverse sort[/COLOR] { [COLOR="DarkGreen"]$hash{$a}[/COLOR] <=> [COLOR="DarkGreen"]$hash{$b}[/COLOR] } [COLOR="DarkRed"]keys[/COLOR] [COLOR="DarkGreen"]%hash[/COLOR]) {
            [COLOR="DarkRed"]print[/COLOR] [COLOR="Magenta"]"[COLOR="DarkGreen"]$_[/COLOR]\t[COLOR="DarkGreen"]$hash{$_}[/COLOR]\n"[/COLOR];
[COLOR="Gray"]            # break out of the foreach loop if decrementing
            # the value of $f makes it zero[/COLOR]
            **last unless** --[COLOR="DarkGreen"]$f[/COLOR];
        }
    }
}

[COLOR="Gray"]# Check type of invocation[/COLOR]
**if** ([COLOR="DarkGreen"]@ARGV[/COLOR]) {
[COLOR="Gray"]    # There were some command line arguments other than the optional -f
    # So we use perl's diamond operator to get the content of the files
    # pointed to by the given filenames and buffer them.[/COLOR]
    **while** (<>) {
        [COLOR="DarkGreen"]$buffer[/COLOR] .= [COLOR="DarkGreen"]$_[/COLOR];
    }
    process [COLOR="DarkGreen"]$buffer[/COLOR];
} **elsif** (! -t STDIN) {
[COLOR="Gray"]    # Looks like STDIN is connected to something, let's buffer up that input[/COLOR]
    **while** (<STDIN>) {
        [COLOR="DarkGreen"]$buffer[/COLOR] .= [COLOR="DarkGreen"]$_[/COLOR];
    }
    process [COLOR="DarkGreen"]$buffer[/COLOR];
} **else** {
   [COLOR="Gray"] # Incorrect invocation - print help[/COLOR]
    [COLOR="DarkRed"]print[/COLOR] [COLOR="Magenta"]"Usage: [COLOR="DarkGreen"]$0[/COLOR] [-f[={number}]] file.txt\n"[/COLOR];
    [COLOR="DarkRed"]print[/COLOR] [COLOR="Magenta"]"or:    echo \"text\" | [COLOR="DarkGreen"]$0[/COLOR] [-f={number}]\n\n"[/COLOR];
    [COLOR="DarkRed"]print[/COLOR] [COLOR="Magenta"]"OPTIONS: -f          : print the most used word\n"[/COLOR];
    [COLOR="DarkRed"]print[/COLOR] [COLOR="Magenta"]"         -f={number} : show the list of {number} most used words\n"[/COLOR];
}
```

Sample executions:

```
roccivic@roccivic-pc:~/Desktop$ ./wa.pl
Usage: ./wa.pl [-f[={number}]] file.txt
or:    echo "text" | ./wa.pl [-f={number}]

OPTIONS: -f          : print the most used word
         -f={number} : show the list of {number} most used words
```
```
roccivic@roccivic-pc:~/Desktop$ ./wa.pl essay.txt
Words: 468
Unique Words: 223
Sentences: 38
```
```
roccivic@roccivic-pc:~/Desktop$ ./wa.pl -f essay.txt
Words: 468
Unique Words: 223
Sentences: 38
Most used words:
cats	25
```
```
roccivic@roccivic-pc:~/Desktop$ ./wa.pl -f=4 essay.txt
Words: 468
Unique Words: 223
Sentences: 38
Most used words:
cats	25
the	20
a	15
are	13
```

[EDIT]: fixed bug where the total count of words was incorrectly computed

---

### Post by lisati on 2011-12-17
> **sh228 said:**
> For the purposes of this challenge, I'll count it as two sentences. 
@schauerlich If your earlier entries differ, don't worry about it. The whole point is to get people programming, and not to worry about insignificant discrepancies between the entries.

Exactly why I didn't go into more details with my comment earlier. :D

---

### Post by highspider on 2011-12-18
C++;
[COLOR=Red][COLOR=SlateGray]  
[COLOR=Red]Edit 9 Change a lot code to get rid of globals and added -l sentences and length and average length [/COLOR]
Edit 8 fixed all memory leaks
[/COLOR] [/COLOR]
```
[COLOR=DarkGreen]/**********************************************************************
* Name        : 24challange.cpp
* Author      : Highspider
* Version     : 9 - sentences length
* Description: Write a program that analyzes input from a file, essay.txt, and
*                   compiles statistics on it. The program should output:
*                    1. The total word count
*                    2. The count of unique words
*                    3. The number of sentences
*
* Changes  :        Added Display mode -l
*                   Removed -w mode (strange debug because had trouble with
*                     step into-step out- debuging)
*                   Got rid of all non-const globals vars
*                   Made funcs cleaner -- had to without globals
*                   Fixed all memory leaks
*                   Added two more dynamic arrays for sim words and there count
*                   Added A bubble sort for similar words order
*                   Added Display Mode -s.
*                   Added Display Mode -p
*                   Use command line arg's for a cookie points.
*                   Added Display Mode -d and -n
*****************************************************************************/
//Declarations[/COLOR]
#include <cstring>      [COLOR=DarkGreen]//for strcmp strlen strcpy strcmp[/COLOR]
#include <iostream>     [COLOR=DarkGreen]//for Std in out[/COLOR]
#include <stdlib.h>   [COLOR=DarkGreen]  //for atoi[/COLOR]
#include <fstream>     [COLOR=DarkGreen] //for files[/COLOR]
using std::cout;       [COLOR=DarkGreen] //iostream: std out[/COLOR]
using std::endl;       [COLOR=DarkGreen] //iostream: end line + return[/COLOR]
using std::ifstream;    [COLOR=DarkGreen]//fstream:  open read only mode

//const globals[/COLOR] 
const int MAX = 256;        [COLOR=DarkGreen]//MAX buffer size[/COLOR]

[COLOR=DarkGreen]//funcs Declarations[/COLOR]
int GetWords(char buffer[MAX], char **&words, ifstream &wordfile, int &num_words,
             char **&sent, int&num_sent);
int SimWords(char ** words, int num_words, char **&simwords, int &num_simwords,
             char **&simcount, int &num_simcount);
void Phrases(char buffer[MAX], char ** words, char **&phrases, int &num_phrases,
             int num_words);
void avgslen(char ** sent, int num_sent, char ** words, int num_words);
void DisplayWords(char ** words, int num_words, bool mode);
void DisplaySimWords(char ** simwords,char ** simwordscount, int num_simwords);
void sort(char **&simwordscount, char **&simwords, int num_simwordscount );
void DynamicAllocate(char buffer[MAX], char **&temp, char **&words, int & num_words);
void Deallocate(char **&words,  int num_words);

[COLOR=DarkGreen]//main with commandline args[/COLOR]
int main (int argc, char* argv[])
{
   [COLOR=DarkGreen] //vars[/COLOR]
    char buffer[MAX];           [COLOR=DarkGreen]//buffer place holder used for getline() and strcmp()[/COLOR]
    int sentence  = 0;          [COLOR=DarkGreen]//count of sentences[/COLOR]
    int similar = 0;           [COLOR=DarkGreen] //count of found similar words[/COLOR]

   [COLOR=DarkGreen] //Pointer of pointers and there count for dynamic allocating[/COLOR]
    int num_words = 0;          [COLOR=DarkGreen]//count of words listed in the array words[/COLOR]
    char ** words = 0;         [COLOR=DarkGreen] //pointer of pointers for the word list array[/COLOR]
    int num_sent = 0;           [COLOR=DarkGreen]//count number of sentences[/COLOR]
    char ** sent = 0;           [COLOR=DarkGreen]//pointer of pointers for sentences counts[/COLOR]
    int num_simwords = 0;       [COLOR=DarkGreen]//count of simwords listed in the array[/COLOR]
    char ** simwords = 0;       [COLOR=DarkGreen]//pointer of pointer for similar words[/COLOR]
    int num_simcount = 0;       [COLOR=DarkGreen]//count of counters put on similar words[/COLOR]
    char ** simcount = 0;      [COLOR=DarkGreen] //pointer of pointer for the count of similar words[/COLOR]
    int num_phrases = 0;       [COLOR=DarkGreen] //count of words listed in the array phrasewords[/COLOR]
    char ** phrases = 0;        [COLOR=DarkGreen]//pointer of pointers for the phrase list array[/COLOR]

    [COLOR=DarkGreen]//check for command line args[/COLOR]
    if ( argc > 1 && argc < 4 )
    {
    [COLOR=DarkGreen]    //open the word list[/COLOR]
        ifstream wordfile;
      [COLOR=DarkGreen]  //wordfile is [1] from command line[/COLOR]
        wordfile.open ( argv[1] );

     [COLOR=DarkGreen]   //if file is found and opened[/COLOR]
        if (wordfile.is_open() ){

           [COLOR=DarkGreen] //call func getwords and sentence count[/COLOR]
            sentence = GetWords(buffer, words, wordfile, num_words, sent, num_sent);

       [COLOR=DarkGreen]     //close the word file[/COLOR]
            wordfile.close();

         [COLOR=DarkGreen]   //call func get similar words and the count of them[/COLOR]
            similar = SimWords(words, num_words, simwords, num_simwords,
                                simcount, num_simcount);

            [COLOR=DarkGreen]//set bool Display modes  for DisplayWords from argv[2][/COLOR]
            if ( argc == 3){
                if(!strcmp( *(argv + 2 ), "-d" ))
                   DisplayWords(words, num_words, true);
                else if(!strcmp( *(argv + 2 ), "-n" ))
                  DisplayWords(words, num_words, false);
                else if(!strcmp( *(argv + 2 ), "-s" )){
                  [COLOR=DarkGreen]  //sort list before diplaying it[/COLOR]
                    sort(simcount, simwords, num_simcount);
                    [COLOR=DarkGreen]//display list and have x for analyze[/COLOR]
                    DisplaySimWords(simwords, simcount, num_simwords);
                }
                else if(!strcmp( *(argv + 2 ), "-p" )){
                     [COLOR=DarkGreen]//phrases()[/COLOR]
                    Phrases(buffer, words, phrases, num_phrases, num_words);
                    [COLOR=DarkGreen]//Display the phrases[/COLOR]
                    DisplayWords(phrases, num_phrases, true);
                   [COLOR=DarkGreen] //Deallocate memory for phrases[/COLOR]
                    Deallocate(phrases, num_phrases);
                    delete [] phrases;
                }
               [COLOR=DarkGreen] //-l avgerage sentences length and their words[/COLOR]
                else if(!strcmp( *(argv + 2 ), "-l" ))
                    avgslen(sent, num_sent, words, num_words);
             }[COLOR=DarkGreen]//end if command line arguments[/COLOR]


           [COLOR=DarkGreen] //Display the words
            //display header for analyze first[/COLOR]
            cout << "analyze\n"
             << "Total word count: "<< num_words << endl
             << "Unique words: " << num_words - similar << endl
             << "Sentences: " << sentence << endl;

           [COLOR=DarkGreen] //Deallocate memory for words array[/COLOR]
            Deallocate(words, num_words);
            delete [] words;
           [COLOR=DarkGreen] //Deallocate memory for similar words array[/COLOR]
            Deallocate(simwords, num_simwords);
            delete [] simwords;
           [COLOR=DarkGreen] //Deallocate memory for similar words count numbers array[/COLOR]
            Deallocate(simcount, num_simcount);
            delete [] simcount;
            [COLOR=DarkGreen]//Deallocate memory for sentences length count[/COLOR]
            Deallocate(sent, num_sent);
            delete [] sent;

        }
      [COLOR=DarkGreen]  //if their is an error opening the file[/COLOR]
        else{
            cout << "\n!Error!\n!Error!\t" << argv[1]
                 << "\n!Error!\tFile not found or unable to open\n!"
                 << "Error!\n" << endl;;
        }
    }
    else
            [COLOR=DarkGreen]//Display Usage if no command line args or to many args[/COLOR]
            cout << "\n\n[COLOR=DarkOrange]Usage[/COLOR]: " << argv[0] << " [COLOR=DarkOrange]<filename> [/COLOR][ arg ]\n"
            << "\t\t [COLOR=DarkOrange]-d: [/COLOR] [COLOR=DarkOrange](d)isplay words of the file[/COLOR]\n"
            << "\t\t [COLOR=DarkOrange]-n:[/COLOR] [COLOR=DarkOrange] display words (n)ot formated[/COLOR]\n"
            << "\t\t [COLOR=DarkOrange]-s:[/COLOR]  [COLOR=DarkOrange]display (s)imilar words[/COLOR]\n"
            << "\t\t [COLOR=DarkOrange]-p:[/COLOR]  [COLOR=DarkOrange]display similar (p)hrases[/COLOR]\n"
            << "\t\t [COLOR=DarkOrange]-l: [/COLOR] [COLOR=DarkOrange]display average (l)ength of sentences[/COLOR]\n"
            << endl;
}[COLOR=DarkGreen]//end main[/COLOR]

[COLOR=DarkGreen]/***********************************************************************
*NAME: GetWords()
*PURPOSE: Get words out of a text file and build array for words
*PARAM: char **&words, ifstream the text file, num_words
*        all by ref, bool watch, buffer by value
*Return: int total number of sentences found
***********************************************************************/[/COLOR]
int GetWords(char buffer[MAX], char **&words, ifstream &wordfile,
        int &num_words, char **&sent, int&num_sent)
{
    char ** temp  = 0;       [COLOR=DarkGreen]//temp for 3-way swap dynamic allocation[/COLOR]
    int buflen = 0;        [COLOR=DarkGreen]  //temp for buffer len[/COLOR]
    int sentences = 0;       [COLOR=DarkGreen]//return for sentences[/COLOR]
    char tempbuff[MAX];

    do{
        [COLOR=DarkGreen]//read from text file and use ' 'a blank space for delimator[/COLOR]
        wordfile.getline(buffer,256,' ');

       [COLOR=DarkGreen] //how many chars are in the buffer[][/COLOR]
        buflen = strlen(buffer);

       [COLOR=DarkGreen] //loop for each char in buffer[][/COLOR]
        for (int i = 0; i < buflen; ++i){
            [COLOR=DarkGreen]//change to upper case to lower case[/COLOR]
            if (buffer[i] >= 65 && buffer[i] < 90)
                buffer[i] = buffer[i] + 32;
           [COLOR=DarkGreen] //get rid of commas,[/COLOR]
            else  if ( buffer[i] == 44 )
                   buffer[i] = '\0';
           [COLOR=DarkGreen] //if start "quote[/COLOR]
            else if (buffer[i] == 34 && buflen > i + 1){
               [COLOR=DarkGreen] //push bach char the start quote ["quote/0] to be [quote/0][/COLOR]
                for (int s = 0; s < buflen; ++s)
                    buffer[s] = buffer[s + 1];
                   [COLOR=DarkGreen] //bufer len change[/COLOR]
                    buflen = strlen(buffer);
                    [COLOR=DarkGreen]//set back the main loop to reloop;[/COLOR]
                    i = -1;
            }

          [COLOR=DarkGreen]  //count sentence and add terminator char in place
            //46 = . 33 = ! 63 = ?[/COLOR]
            else if ( buffer[i] == 46 || buffer[i] == 33 || buffer[i] == 63 ){
                 sentences++;
                
                 [COLOR=DarkGreen]//copy the count of words to a temp buffer[/COLOR]
                 sprintf(tempbuff, "%d", num_words);
               [COLOR=DarkGreen]  //build array of these counts to use for sentence lengths[/COLOR]
                 DynamicAllocate(tempbuff, temp, sent, num_sent);

             [COLOR=DarkGreen]    //num_words[/COLOR]
                 buffer[i] = '\0';
             }
            [COLOR=DarkGreen]//NOT 13 a carriage return its 10 newline[/COLOR]
            else if (buffer[i] == 10){
                buffer[i] = '\0';
               [COLOR=DarkGreen] //build the extra array[/COLOR]
                DynamicAllocate(buffer,temp, words, num_words);
              [COLOR=DarkGreen]  //there may be one two or more newlines[/COLOR]
                do {
                    i++;
                } while ( buffer[i] == 10 );

                [COLOR=DarkGreen]//copy the new word over[/COLOR]
                for (int s = 0; s < buflen; ++s)
                {
                    buffer[s] = buffer[i + s];
                    buflen = strlen(buffer);
                }
               [COLOR=DarkGreen] //Reloop the main loop to check the new word[/COLOR]
                i = -1;
             }

        }[COLOR=DarkGreen]//end for loop
        //build arrays[/COLOR]
        DynamicAllocate(buffer,temp, words, num_words);

    }while ( !wordfile.eof()); //end of do while loop end of file

    return sentences;
}
[COLOR=DarkGreen]/***********************************************************************
*NAME: SimWords()
*PURPOSE: Check for similar words
*PARAM: char ** words, int num_words by value. char simwords,
*     : char num_simwords, char simcount, int num_simcount ref
*RETURN: int total number of simwords found
***********************************************************************/[/COLOR]
int SimWords(char ** words, int num_words, char **&simwords, int &num_simwords,
        char **&simcount, int &num_simcount){

   char ** temp  = 0;     [COLOR=DarkGreen]//temp for dynamic allocate[/COLOR]
   int number = 0;       [COLOR=DarkGreen] //temp for converting string to int back to string[/COLOR]
   int count = 0;        [COLOR=DarkGreen] //total count of similar words[/COLOR]
   bool addnew = true;    [COLOR=DarkGreen]//bool true/false flag for adding new entries[/COLOR]
   char GE[] = "2     ";  [COLOR=DarkGreen]/* OVERSIZED array default number used simcount
                          *  if not oversized program leaks memory when changing
                          *  values of char** simcount
                          */[/COLOR]

[COLOR=DarkGreen]   //loop m main for each word in the list[/COLOR]
   for (int m = 0; m < num_words; m++ ){
      [COLOR=DarkGreen] //loop s sub to compare with words left in the list[/COLOR]
       for (int s = m + 1; s < num_words; s++){
        [COLOR=DarkGreen] //if they are the same word[/COLOR]
         if (!strcmp(words[m], words[s] )){
           [COLOR=DarkGreen] //add a new entry (might change later)[/COLOR]
            addnew = true;
        [COLOR=DarkGreen]    //add one to similar words found[/COLOR]
            count++;

          [COLOR=DarkGreen]  //check if allready in the list[/COLOR]
            for (int ct = 0; ct < num_simwords; ct++){
               [COLOR=DarkGreen]//if same word already in simwords list[/COLOR]
               if(!strcmp( words[m], simwords[ct])) {
                  [COLOR=DarkGreen]//update that entries count
                  //cast array to int and add one to the count[/COLOR]
                  number = atoi( simcount[ct] ) + 1;
            [COLOR=DarkGreen]     /*
                  * sprintf() is used as itoa
                  * Strange Linux version of itoa
                  * itoa is windows proprietary
                  * It took a long to figure this out
                  *///update the entry with new count[/COLOR]
                  sprintf(simcount[ct], "%d", number);

                [COLOR=DarkGreen] //set the bool flag that entry has been edited[/COLOR]
                 addnew = false;
                 [COLOR=DarkGreen]//break this CT Count Twice loop[/COLOR]
                 ct = num_words;
               }
            }
            [COLOR=DarkGreen]//if no odd entry was updated bool flag is true
            //and we are adding new entry[/COLOR]
            if (addnew){
               DynamicAllocate(words[m], temp, simwords, num_simwords);
               DynamicAllocate(GE, temp, simcount, num_simcount);
            }
             [COLOR=DarkGreen]//break the compare words left list loop
            //to prevent over reads[/COLOR]
            s = num_words;
         }[COLOR=DarkGreen]//end if same word[/COLOR]
      }[COLOR=DarkGreen]//end for() s[/COLOR]
   }[COLOR=DarkGreen]//end for() m[/COLOR]


   return count;
}[COLOR=DarkGreen]//end func[/COLOR]
[COLOR=DarkGreen]/************************************************************************
*NAME phrases()
*PURPOSE: Find similar phrases in a list of words
*PARAM:    char buffer, char words, int number by value, char phrase
*     :   int num_phrase by ref
*RETURN: NONE
*************************************************************************/[/COLOR]
void Phrases(char buffer[MAX], char **words, char **&phrases, 
                     int &num_phrases, int num_words){

    char buffer2[MAX];        [COLOR=DarkGreen]//temp buffer for compareing words[/COLOR]
    char ** temp;             [COLOR=DarkGreen]//temp need for allocate 3-way swap[/COLOR]
    bool addnewflag = false;  [COLOR=DarkGreen]//add a new entry true or false[/COLOR]

    cout << "phrases" << endl;
    for ( int i = 0; i < num_words - 2; ++i ){

        addnewflag = true;  [COLOR=DarkGreen]// t/f for add new entry to found array[/COLOR]

        [COLOR=DarkGreen]//build a buffer of 3 words[/COLOR]
        strcpy(buffer, words[i]);
        strcat(buffer," "); [COLOR=DarkGreen]//add spaces for display reasons[/COLOR]
        strcat(buffer, words[i + 1]);
        strcat(buffer," ");
        strcat(buffer, words[i + 2]);

        [COLOR=DarkGreen]//loop a buffer of the next 3 words[/COLOR]
        for ( int l = i + 2; l < num_words - 2; ++l ){
            //build buffer3 of the next 3 words
            strcpy(buffer2, words[l]);
            strcat(buffer2," ");
            strcat(buffer2, words[l + 1]);
            strcat(buffer2," ");
            strcat(buffer2, words[l + 2]);
[COLOR=DarkGreen]
            //if match of the 3 words[/COLOR]
            if(!strcmp( buffer, buffer2 )){
                [COLOR=DarkGreen]//loop the array of phrases already found[/COLOR]
                for (int f = 0; f < num_phrases; f++){
               [COLOR=DarkGreen] //if phrase is already in - don't add it again[/COLOR]
                    if(!strcmp( buffer, *(phrases + f) )){
                        addnewflag = false;
                    }
                }
                [COLOR=DarkGreen]//if not updated entry flag is true add it[/COLOR]
                if (addnewflag){
                    DynamicAllocate(buffer, temp, phrases, num_phrases);
                }
            }
        }[COLOR=DarkGreen]//end l loop[/COLOR]
    }[COLOR=DarkGreen]//end i loop[/COLOR]

}[COLOR=DarkGreen]//end func[/COLOR]
[COLOR=DarkGreen]/***********************************************************************
*NAME: avgslen();  average sentence length
*PURPOSE: find average length of sentences
*PARAM: char ** sent,words, int num_sent,num_words by value
*RETURN: none
***********************************************************************/[/COLOR]
void avgslen(char ** sent, int num_sent, char ** words, int num_words){
    float average = 0;

    [COLOR=DarkGreen]//display length of first sentence out side of the loop
    //if there is at least one[/COLOR]
    if ( num_sent > 0 ){
     [COLOR=DarkGreen] //the first count [x][/COLOR]
      cout << "\n\n1) [" << atoi(sent[0]) +1 << ']';
      [COLOR=DarkGreen]//the sentence words inside that count[/COLOR]
      for (int l = 0; l <= atoi(sent[0]); l++)
          cout << ' ' << words[l];
      [COLOR=DarkGreen]//cleaner display[/COLOR]
      cout << endl;

      [COLOR=DarkGreen]//add to the average[/COLOR]
      average =    atoi(sent[0]) + 1;
[COLOR=DarkGreen]
      //loop the remaining[/COLOR]
      for (int i = 1; i < num_sent; i++){
        [COLOR=DarkGreen]//the next counter [x][/COLOR]
          cout << i + 1 << ") ["
             << atoi(sent[i]) - atoi(sent[i - 1]) << ']';
        [COLOR=DarkGreen]//the words inside that count[/COLOR]
        for (int l = (atoi(sent[i - 1]) + 1); l <= atoi(sent[i]); l++)
                  cout << ' ' << words[l];
       [COLOR=DarkGreen] //cleaner display[/COLOR]
        cout << endl;
        [COLOR=DarkGreen]//calc the total for average length[/COLOR]
        average = average + (atoi(sent[i]) - atoi(sent[i - 1]));
     }
     [COLOR=DarkGreen] //divid to find average[/COLOR]
      average = average / num_sent;
     [COLOR=DarkGreen] //display the results[/COLOR]
      cout << "\nThe average sentence length is: ["
           << average << "] words long\n\n";
    }
}

[COLOR=DarkGreen]/***********************************************************************
*NAME: DisplayWords()
*PURPOSE: cout << display words to screen
*PARAM: char ** words, int num_words bool mode by value
*RETURN: NONE
***********************************************************************/[/COLOR]
void DisplayWords(char ** words, int num_words, bool mode){
   [COLOR=DarkGreen] // bool not formated display[/COLOR]
    if (!mode){
        for ( int i = 0; i < num_words; ++i )
        cout << *(words + i);
    }
    [COLOR=DarkGreen]// else formated display[/COLOR]
    else{
        for ( int i = 0; i < num_words; ++i )
        cout << '\t' << i + 1 << '[' << *(words + i) <<  ']' << endl;
    }
    cout << endl;
}
[COLOR=DarkGreen]/***********************************************************************
*NAME: DisplaySimWords()
*PURPOSE: display similar words and corresponding count to screen
*PARAM: char ** simwords, char ** simwordscount, num_words by value
*RETURN: NONE
***********************************************************************/[/COLOR]
void DisplaySimWords(char ** simwords, char ** simwordscount, int num_simwords){
    [COLOR=DarkGreen]//Display header[/COLOR]
    cout << "\n\n\t\tDescending frequency most used words:\n\n";

    [COLOR=DarkGreen]//loop and display both word and its count[/COLOR]
    for ( int i = 0; i < num_simwords; ++i){
        cout << i + 1 << "  [" << *(simwords + i) <<"] * "
             << *(simwordscount + i) << endl;
    }
}
[COLOR=DarkGreen]/************************************************************************
*NAME sort(char **&simwordscount, char **&simwords, int num_simwordscount )
*PURPOSE: Resort the simwords arrays by frequency
*PARAM:   char ** simwordscount, char ** simwords by ref,
*     :   int num_simwords by value
*NOTE:    Bubble sort algorithm.
*RETURN: NONE
*************************************************************************/[/COLOR]
void sort(char **&simwordscount, char **&simwords, int num_simwordscount )
{
    char * temp;  [COLOR=DarkGreen]//place holder for 3-way swap[/COLOR]

    [COLOR=DarkGreen]//nested loops NOT while(FLAG)[/COLOR]
    for ( int i = 0; i < num_simwordscount; i++)
        {
            for ( int i = 0; i < num_simwordscount - 1; i++)
                 [COLOR=DarkGreen]//if less than then swap
                 //this way back-words compared to how others do it with while flags[/COLOR]
                if ( atoi(simwordscount[i]) < atoi(simwordscount[i + 1])) {

               [COLOR=DarkGreen]  //3-way swap
                 //sort for simwordscount count up one cell in the array[/COLOR]
                 temp = simwordscount[i];
                 simwordscount[i] = simwordscount[i + 1];
                 simwordscount[i + 1] = temp;

                 [COLOR=DarkGreen]//3-way swap
                 //sort for simwordscount the corresponding i in simwords[/COLOR]
                 //to match cells of the array
                 temp = simwords[i];
                 simwords[i] = simwords[i + 1];
                 simwords[i + 1] = temp;
            }
        }
}

[COLOR=DarkGreen]/***********************************************************************
*NAME: DynamicAllocate()
*PURPOSE: Build arrays dynamically
*PARAM: char buffer by value, char temp, char words,num_words by ref
*RETURN: NONE
***********************************************************************/[/COLOR]
void DynamicAllocate(char buffer[MAX], char **&temp, char **&words,
        int &num_words){
    [COLOR=DarkGreen]//pointer of pointers    Notice NEW char * [][/COLOR]
    temp = new char * [num_words + 1];    //temp for word array

    [COLOR=DarkGreen]//copy all previously entered words to our temp array
    //note first time loop doesn't runs i=0 < num_words=0
    //"(0<0)not true"[/COLOR]
    for ( int i = 0; i < num_words; i++){
        temp[i] = words[i];
    }
   [COLOR=DarkGreen] //make new temp array the size of the string[/COLOR]
    temp[num_words] = new char[strlen( buffer ) + 1];

   [COLOR=DarkGreen] //copy buffer to temp[/COLOR]
    strcpy( temp[num_words], buffer );

   [COLOR=DarkGreen] //deallocate old words[/COLOR]
    delete [] words;

   [COLOR=DarkGreen] //copy address of temp to words[/COLOR]
    words = temp;

    [COLOR=DarkGreen]//add one to number entries [/COLOR]
    num_words++;
}
[COLOR=DarkGreen]/***********************************************************************
*NAME: Deallocate()
*PURPOSE: Delete / de-allocate memory used by the program
*PARAM: char words by ref, int num_words by value
*RETURN: NONE
***********************************************************************/[/COLOR]
void Deallocate(char **&words, int num_words){
        [COLOR=DarkGreen]//delete | de-allocate each array of words two star char **[/COLOR]
        for ( int i = 0; i < num_words; ++i)
            delete [] words[i];
}
```[COLOR=SandyBrown]./24challenge[/COLOR]
```

Usage: ./24challange <filename> [ arg ]
         -d:  (d)isplay words of the file
         -n:  display words (n)ot formated
         -s:  display (s)imilar words
         -p:  display similar (p)hrases
         -l:  display average (l)ength of sentences

```[COLOR=MediumTurquoise]
[COLOR=SandyBrown]./24challenge /home/username/Desktop/essay.txt[/COLOR][/COLOR]
```

analyze
Total word count: 468
Unique words: 223
Sentences: 38

```[COLOR=SandyBrown]./24challenge /home/username/Desktop/essay.txt -s[/COLOR]
```
Descending frequency most used words:

1  [cats] * 25
2  [the] * 20
3  [a] * 15
[COLOR=MediumTurquoise]<sikped>[/COLOR]

analyze
Total word count: 468
Unique words: 223
Sentences: 38


```[COLOR=MediumTurquoise]
[COLOR=SandyBrown]./24challenge /home/username/Desktop/essay.txt -p[/COLOR][/COLOR]
```

phrases
    1[a cat is]
    2[are civilized members]
    3[civilized members of]
[COLOR=MediumTurquoise]<skipped>[/COLOR]

```[COLOR=SandyBrown]./24challenge /home/username/Desktop/essay.txt -d[/COLOR]
 ```
    1[a]
    2[dog]
    3[is]
    4[man's][COLOR=MediumTurquoise]
<skip>[/COLOR]
    466[the]
    467[ideal]
    468[housepet]

```[COLOR=SandyBrown]./24challenge /home/username/Desktop/essay.txt -l[/COLOR]
```

1) [6] a dog is man's best friend
2) [19] that common saying ...[COLOR=MediumTurquoise] <skip>[/COLOR]
3) [9] for many people a cat is their best friend
[COLOR=MediumTurquoise]<skip>[/COLOR]
38) [8] in many ways cats are the ideal housepet

The average sentence length is: [12.3158] words long
[COLOR=MediumTurquoise]<skip>[/COLOR]

```

---

### Post by Petrolea on 2011-12-23
This is my entry in D. I tried to make the code as easy to read as possible. 

It only finds phrases that are 3 words long, the rest is OK. It accepts the filename as a first argument.

If you have 'dmd' installed then just use the command below to run the program.

```
./program.d file.txt
```


[PHP]
#!/usr/bin/rdmd -w
import std.stdio;
import std.array;
import std.regex;
import std.string;
import std.algorithm;
import std.conv;
import std.file;
pragma(msg, "Compiling, please wait...");

//returns array of unique words
string[] Unique(string[] arr)
{
	int count = 0;
	string[] unique;

	foreach(s; arr)
	{
		count = 0;
		foreach(s2; unique)
		{
			//compare all entries
			if(icmp(s2, s) == 0) count += 1;
		}
		
		//count equals 0 if the word does not yet exist in "unique"
		if(count == 0)
		{
			unique ~= s;
		}
	}
	
	return unique;
}


//writes a list of commonly used words
//"amount" limits the output of function
void List(string[] arr, string[] unique, int amount)
{
	int count = 0;
	string[] hits_s;
	
	foreach(s; unique)
	{		
		count = 0;
		foreach(s2; arr)
		{
			//count how many times a word repeats
			if(icmp(s2, s) == 0) count += 1;
		}
		
		//add words to array
		if(count < 10) hits_s ~= ("0" ~ text(count) ~ " - " ~ s);
		else hits_s ~= (text(count) ~ " - " ~ s);
	}
	
	sort!("a > b")(hits_s);
	
	for(int i = 0; i < hits_s.length; i++)
	{
		if(i == amount) break;
		writefln("%s", hits_s[i]);
	}
}

void Phrases(string[] arr)
{
	string[] phrases;
	string tmp;
	string tmp2;
	int count = 0;
	int length = arr.length;
	bool exists = false;
	
	//save phrases of 3 words into array
	foreach(int i, string s; arr)
	{
		if(i < length-2) //stop before reaching end of array
			tmp = (arr[i] ~ " " ~ arr[i+1] ~ " " ~ arr[i+2]); //make a phrase	
		else break;	
			
		count = 0;
		exists = false;
		
		foreach(int j, string s2; arr) //compare each phrase to whole text
		{
			if(j < length-2)
				tmp2 = (arr[j] ~ " " ~ arr[j+1] ~ " " ~ arr[j+2]);
			else break;
			
			if(icmp(tmp, tmp2) == 0) count += 1;
		}
		
		if(count >= 3) 
		{
			//if phrase already exists in array, don't add it
			foreach(s2; phrases)
			{
				if(icmp(s2, tmp) == 0) exists = true;
			}
			
			if(!exists) phrases ~= tmp;
		}	
	}		
	
	foreach(s; phrases)
	{
		writeln(s); //write them out
	}
	
}

int main(string[] args)
{
	File file;
	
	//open file specified in argument
	if(args.length > 1)
	{
		if(exists(args[1])) file = File(args[1], "r");
		else 
		{
			writeln("Incorrect file name or file doesn't exist!");
			return 1;
		}
	}
	else
	{
		writeln("First argument must not be empty!");
		return 1;
	}
	
	char[] buf;
	string[] matches;
	char[] content;
	
	int count_w = 0;
	int count_s = 0;
	
	while (file.readln(buf) != 0)
	{
		buf = tr(buf, "\n", " "); //remove new lines from text and add it to array
		content ~= buf;	
	}
	
	foreach(m; match(content, regex(`[\w']+`))) //matches any word character and ' repeated one or more times
	{
		count_w += 1;
		matches ~= cast(string)toLower(m.hit);
	}
	
	foreach(m; match(content, regex(`[.?!]`))) //matches all . and ? and ! - sentences
		count_s += 1;
	
	
	
	//Writing it all out
	string[] unique = Unique(matches);
	
	writefln("Total word count: %s", count_w);
	writefln("Unique words: %s", unique.length);
	writefln("Sentences: %s", count_s);
	if(count_s != 0) writefln("Average sentence length: %s", count_w / count_s);
	else writefln("Average sentence length: %s", count_w);
	
	writeln();
	writeln("Common words:");
	List(matches, unique, 9);
	writeln();
	writeln("Common phrases:");
	Phrases(matches);
	
	return 0;
}
[/PHP]

Sample output from a modified text file:
```

Compiling, please wait...
Total word count: 563
Unique words: 226
Sentences: 38
Average sentence length: 14

Common words:
35 - lala
25 - cats
24 - kaj
20 - the
15 - a
13 - are
12 - they
12 - of
10 - to

Common phrases:
kaj kaj kaj
cats can be
lala lala lala

```

---

### Post by epicoder on 2012-01-03
Unless anyone asks for an extension, this challenge will be judged on January 7th.

---

### Post by epicoder on 2012-01-07
I'm sorry, but I was hit with an unexpected schedule change today and I was unable to judge the challenge. I will attempt to do so tomorrow. If I still don't manage it, I may ask someone else to do it.

---

### Post by epicoder on 2012-01-09
**HIGHSPIDER **wins for his clean code, implementation of all cookie points, excellent commenting, and that I was able to compile and run his program on Windows. That saved me a good amount of time. :)

I may or may not hand out assorted extra awards later. We'll see. In the meantime, congratulations to highspider.

</challenge>

---

### Post by Queue29 on 2012-01-09
Using flex and a bit of C

Compile and run with:
```

flex lexer.lex
gcc -c set.c
gcc lex.yy.c set.o -lfl

```

lexer.lex
```
/* UFPC 24 */

%option nodefault

%{
#include "set.h"
  int words = 0;
  int uwords = 0;
  int sent = 0;
%}

%%

[a-zA-Z]+ {
  words++;
  uwords += put(yytext);
}

[\.?!] {
  sent++;
}

.|\n {
}

%%

int
main(int argc, char** argv) {
init_set();
  if(argc > 1) {
    if(!(yyin = fopen(argv[1], "r"))) {
      perror(argv[1]);
      return 1;
    }
  }

  yylex();

  printf("words: %d\n", words);
  printf("uwords: %d\n", uwords);
  printf("sents: %d\n", sent);
  return 0;
}
```

set.h
```
#ifndef SET_H
#define SET_H

#define TABLESIZE 2048

char* table[TABLESIZE];

void init_set();
int put(char*);
int contains(char*);
int count();

#endif
```

set.c
```
#include <string.h>
#include "set.h"

void
init_set() {
  size_t i;
  for(i=0; i<TABLESIZE; i++)
    table[i] = NULL;
}

int
contains(char* s) {
  size_t i = 0;
  while(i<TABLESIZE && table[i]!=NULL) {
    if(strcmp(table[i], s) == 0)
      return 1;
    i++;
  }
  return 0;
}

int
put(char* s) {
  char* dup = strdup(s);
  if(!contains(dup)) {
    size_t i=0;
    while(i<TABLESIZE) {
      if(table[i]==NULL) {
        table[i] = dup;
        return 1;
      }
      i++;
    }
  } else
    return 0;
}

int
count() {
  int n = 0;
  size_t i = 0;
  while(i<TABLESIZE) {
    if(table[i] != NULL)
      n++;
    i++;
  }
  return n;
}
```

Please excuse the ghetto hashset implementation :-$

---

### Post by Bodsda on 2012-01-17
I have attempted to make contact with Highspider, but s/he hasn't been online for a week or so. If I haven't received a reply by the 23rd then the beginners team will take over the posting and judging of the next challenge.

Bodsda,
Ubuntu Beginners Team

---

### Post by highspider on 2012-01-24
Well its the 23rd and im respoding.  I spent along time codeing this because it was college break for xmas.
 
Sorry
I was away from town and no internet is why I took so long to respond.
 
woohoo cool beans.
 
The reason it works on both windows and linux is because I wrote it with eclipse on ubuntu and then debuged mem leaks with visual studio c++. 
 
I final found out that one has to manule install a new version of eclispe "indigo" and then use Valigrid for unbuntu in order to use valgrind memory leak check.

---

### Post by cgroza on 2012-01-24
I really look forward to programming challenge #25.

Hope that becomes a reality as soon as possible.

---

### Post by Bodsda on 2012-01-26
highspider has asked me to post the next challenge on his behalf, so keep your RSS readers running, it will be up soon!

Bodsda,
Ubuntu Beginners Team

---

### Post by Bodsda on 2012-01-29
Challenge up!
[http://ubuntuforums.org/showthread.php?p=11648773](http://ubuntuforums.org/showthread.php?p=11648773)

Bodsda
Ubuntu Beginners Team

---

