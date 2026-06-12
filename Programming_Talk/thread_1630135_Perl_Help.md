---
title: "Perl Help"
date: 2010-11-24
forum: Programming Talk
---

### Post by alphaamanitin on 2010-11-24
Hey Guys,

So I am writing a perl program to clean up fasta files.  At this point I need help with merging all the files in a directory to one new file.

I would like the program to ask the user where to save the file, using full pathway and name.  It would open the directory, merge all the files into on file (but not delete the original files), then clean that new file with a cleaning subroutine I have finished, then save the file where the user wants it.

Here is the code I have so far.

```
#!/usr/bin/perl

use strict;
use warnings;


#Descibe Software to User

print "This program will create nicely formated fasta files.  It will fix a fasta file containing one or more sequences to have the correct syntax and line breaks.  It can alternatively take a directory of fasta files, and combine them into one file with pretty formating.\n";

#Prompt user for input

print "Will you be working on a file or directory (please type 'F' for file or 'D' for directory, the press enter)?\n";

#Get user's input and remove the line break

chomp (my $choice = <STDIN>); # 

# die if the User does not enter F or D, otherwise run appropriate subroutine

if ( ($choice ne "F") && ($choice ne "D") ) {
    die "Those are not the choices, better try again!\n";
    } elsif ($choice eq "F") {
        &file;
            } else {
        &directory;
        &file;
        } 

#################
# SUB FILE      #
#################

sub file {
my ($file, $new_file, @file);

print "Please enter the FULL pathway of the fasta file.\n";

#Users input is file & Removes the user's line break

chomp ($file = <STDIN>); 
#Open the user's file or die

open (FASTA, "$file") || die ("Oh, no! I can't open the file; I just don't have the power!");

#Read user's file into an array

print "@file\n";

#Prompt user for file name to save cleaned fasta file top

print "Please enter file name, using the full pathway, to save your cleaned fasta file to:\n";
chomp ($new_file = <STDIN>);
open (New_File, "+>$new_file") || die "Couldn't create file.\n";

#process the file line by line, chomping all lines that do not contain ">" and removing all white space from lines that do not contain ">"

while (my $lines = <FASTA>) {
    foreach ($lines) {
        if (!/>/) { 
            chomp ($lines);
            $lines =~ s/ //g;
            print New_File "$lines";
        } else {
            print New_File "\n$lines";
            next;
            }
        }
     }    
}

#Close the files

close FASTA;
close New_File;


#################
# SUB DIRECTORY #
#################

sub directory {

#Prompt User

print "Please enter name of Directory using the FULL path.\n";

#Users directory & Removes user's line break

chomp (my $directory = <STDIN>); 
opendir (DIR, "$directory") || die ("Oh, no! I can't open the directory; I just don't have the power!");

    
}
```Thanks for the help guys.  I know my program is not perfect, but it works.  I really am not looking for help with what I already have done unless you see great problems with the code.  Okay I just noticed there is a large error.  I stupidly called up the file subroutine after the directory subroutine which will want user input and the like again.  I know that is wrong.  I will need to rewrite the code to use the information I get to save the merged file from the user to also clean up that file, so that it is done seemlessly to the user's point of view. 

AlphaA

I see I had put it in the wrong forum.  Thanks for moving.

---

