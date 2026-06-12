---
title: "Wordlist Compiler [perl]"
date: 2010-05-05
forum: Programming Talk
---

### Post by lonewaster on 2010-05-05
Last couple of days i have been trying to make a Wordlist Generator.
After getting bored with permutation modules, i decided to just make a program that compiles other wordlists into ONE.
This script takes a folder as a SOURCE, and outputs into <user_provided_filename>

So far it has TWO modes. 0 && 1

0   =>   Standard Compile. Takes a PATH to a directory as INPUT and OUTPUTS to the path/filename provided.
1   =>   Same as above except it asks YES/NO at each file (compile OR not)

**SYNTAX:   perl wordlist-compiler.pl -s /Path/To/Source/Directory -o /Path/To/Output/File.txt**

***YOU CAN USE **perl wordlist-compiler.pl --help **FOR MORE INFORMATION =]***

I am planning on expanding on this, and maybe even implementing it into my toolkit [swedger toolkit  =  [http:///www.swedger.com/swedgertoolkit-1.6.tgz]("http://www.swedger.com/swedgertoolkit-1.6.tgz") ]

But for now, i will put any updates here.
Please keep in mind that I have my site to work on, amongst a few other little scripts/projects I am doing.

Hope someone finds it useful ---> i sure do >=]
Not that i crack WPA or anything *whistles*

***Please let me know what you think!!***

[CENTER][B]- SOURCE -
[/B][LEFT]```

#!/usr/bin/perl
# # # # # # # # # # # # #
#    Wordlist Compiler    #
#            v2            #
#      www.swedger.com        #
# # # # # # # # # # # # #
use constant VERSION => 'v2.0';
use File::Basename; # use the File::Basename module - used to split up the OUTPUT path later, to run file tests on it
system('clear'); # clears the terminal, so it looks nice and neat
use Getopt::Std; # use the getopt standard module
$Getopt::Std::STANDARD_HELP_VERSION = 1; # for using the sub main::HELP_MESSAGE
getopts("m:s:o:",\%flag); # get options. s{SOURCE}    +    o{OUTPUT}    +    m{MODE}
my $src=$flag{s};my $out=$flag{o};my $mode=$flag{m}; # set each of the --flags into a $variable
if($mode eq "") { die("\n\t\t<X]---------<<   =========   >>---------[X>\nYou Have Not Chosen A Mode!!\nWhat do you want me to do?\nMaybe if you ask nicely, or even say PLEASE, I might just 'work' - no questions asked!!\n\t\t<X]---------<<   =========   >>---------[X>\n\n"); }
elsif($mode ne "0" && $mode ne "1") { die("\n\t\t<X]---------<<   =========   >>---------[X>\nYou Have Selected An INVALID Mode (-m <mode>)\nThe Following Are The Accepted Modes-\n   0\t-=>\tSTANDARD- Compiles Every File From The Source Into One File.\n   1\t-=>\tSame As Option 0 Except You Must Select YES/NO On Each File.\n\t\t<X]---------<<   =========   >>---------[X>\n\n"); }
if($src eq "") { die("\n\t\t<X]---------<<   =========   >>---------[X>\nYou MUST Provide A Source Directory!\nWhat did you expect to happen?\nTell you what- Why don't you shut your eyes, clasp your hands, and PRAY for it?\nThat will do about as much good as passing me no input!!\n\t\t<X]---------<<   =========   >>---------[X>\n\n"); }
elsif(!-e $src) { die("\n\t\t<X]---------<<   =========   >>---------[X>\nThe Specified Source Directory DOES NOT EXIST!!\nPlease check that it does and check you spelled it correctly.\nThen try again.\n\t\t<X]---------<<   =========   >>---------[X>\n\n"); }
elsif(!-d $src) { die("\n\t\t<X]---------<<   =========   >>---------[X>\nThe Specified Source IS NOT A DIRECTORY!!\nPlease check your selection is correct and check you spelled it correctly.\nThen try again.\n\t\t<X]---------<<   =========   >>---------[X>\n\n"); }
if($out eq "") { die("\n\t\t<X]---------<<   =========   >>---------[X>\nYou Need To Specify An Output PATH + FILENAME\nWhat do you want me to do?\nMaybe if you ask nicely, or even say PLEASE, I might just 'work' - no questions asked!!\n\t\t<X]---------<<   =========   >>---------[X>\n\n"); }
else { # if the user actually provided an output path
    ($filename,$path,$suffix)=fileparse($out); # parse it into vars for testing
    if(!-e $path) { die("\n\t\t<X]---------<<   =========   >>---------[X>\nThat Directory (".$path.") Doesn't Exist!!\nPlease check it, make sure it's spelled correctly, and try again\n\t\t<X]---------<<   =========   >>---------[X>\n\n"); }
    elsif(-e $filename.".".$suffix) { die("\n\t\t<X]---------<<   =========   >>---------[X>\nThe File You Want To Output Into (".$filename.".".$suffix.") Already Exists.\nFor safety reasons, You may only use me to write into a NEW file.\nPlease try again.\n\t\t<X]---------<<   =========   >>---------[X>\n\n"); }
    else { # and, so long as the specified folder EXISTS - move on with the process
        if(substr($src,(length($src)-1),1) ne "/") { $src=$src.'/'; }
        print "The Following Files Have Been Prepped For Compiling:\n"; # alert the user
        @files = <$src*.*>; # get a list of every FILE in the directory
        foreach $file (@files) { # and for each of those files-
            #$fn=fileparse($file); # parse it into vars for testing. (commented out. depracated as I now use -1 in the substr() function.
            if(substr($file,-1,1) eq "#") { # if the filename begins with a # symbol (so that 'comment files' will not be added to the RESULT file)
                print $file." was IGNORED(#Comment.file)\n"; # then print the file and note that it was excluded as a 'comment file'
            }
            else { # otherwise, if the file passed the checking routine, then
                push(@combi,$file); # add it to the list used to read and compile all the files together
                print "\t+   ".$file."\n"; # print it on the screen, so the user can decide whether to continue/cancel after this loop
            }
        }
        print "\nPlease Check Over The List Above.\nIf You Want To Cancel, Press CTRL+C & To Continue, Press ENTER...";my $waitForEnter=<>;print "\n";
        my $linefeed=$/; # backup the line ending recognition character
        undef $/; # then undefine it, so we can read each file, in its entirety, into one, scalar, variable
        open(RESULT,">".$out); # create & open the desired output file for WRITING [>]
        print RESULT "# # # # # # # # # # # # # # # # # # # # # # # # # # # #\n";
        print RESULT "#   Wordlist Compiler   [WordCompi]   v2\n";
        print RESULT "#   createdBy   darksider\n";
        print RESULT "#   emailAddy   darksider@swedger.com\n";
        print RESULT "#   siteAddy    www.swedger.com\n";
        print RESULT "# # # # # # # # # # # # # # # # # # # # # # # # # # # #\n";
        print RESULT "#     This Wordlist Was Compiled From Multiple Files\n";
        print RESULT "#     The names of these files are printed at\n";
        print RESULT "#     the top of the compiled list of words taken from them.\n";
        print RESULT "# # # # # # # # # # # # # # # # # # # # # # # # # # # #\n\n";
        %hash=(); # create a hash to store all the words in (using a hash is easier because it means no dittos [duplicates] will be in the final file)
        foreach $file (@combi) { # for each of the files in the @combi list we compiled from the files (above)
            if($mode eq "1") { # if the user chose mode #1, ask YES/NO at each file ---> gives them more control over which files are added
                $/=$linefeed; # restore the line ending recognition character variable to it's former value, so the program recognises the user's choice
                # NOTE: WITHOUT THE LINE ENDING RECOGNITION CHARACTER VARIABLE BEING SET, THE SCRIPT WOULDN'T KNOW WHEN THE USER HAD PRESSED ENTER!!
                ASK: # label for jumping back if the user gives a wrong answer (yes/no)
                print "Compile ".$file." ?? [yes/no]: ";my $answer=lc(<>);chomp($answer);print "\n";# ask(yes/no) whether to add the file(lowercase the answer)
                if($answer eq "no") { next; } # if they don't want to add the current file, then jump to the next foreach $file (@combi) iteration
                elsif($answer ne "yes") { print "Answer yes OR no !!\n";goto ASK; } # if they haven't chosen either yes OR no, then jump back to the ASK label
            }
            print RESULT "# File Compiled: ".$file."\n";
            undef $/; # remove the line ending recognition character again for reading the file(s) into one, scalar, variable
            open(SRC,"<".$file); # open the file,
            $source=<SRC>; # read all it's contents into a scalar variable,
            $source =~ s/\n/ /g; # get rid of every newline char (\n) and replace them all with a space (so the split() call below works properly)
            @words=split(' ',$source); # then split the file into words. (the bit above also means that if a file is one-word-per-line - it will still compile)
            foreach $word (@words) { # and then, for each word in this file -
                $hash{$word}=1; # put the word into the hash
            } # move onto the next word and repeat until every word from this file has been added to it
        } # and then loop through again and again until every word from ever one of the files has been added to the hash
        print RESULT "\n";
        $/=$linefeed; # restore the line ending recognition character back to normal. good practice =]
        foreach $key (keys %hash) { # for each element in the hash containing all of the words to go into the final RESULT
            print RESULT $key."\n"; # print the new word into the RESULT file, and go to the next line
        }
    }
}

#    WordCompi Subroutines
sub HELP_MESSAGE { # function ran when the user calls the --help flag
    my $fh = shift;
    print $fh "\t--------- ========= ---------\n";
    print $fh "\t-m (#)\t\tMode Setting\n";
    print $fh "\t\t--->\t0 - Standard Compile (automatic)\n";
    print $fh "\t\t--->\t1 - Standard Compile(Yes/No At Each File)\n";
    print $fh "\t-s (path)\tSOURCE Directory Path\n";
    print $fh "\t\t--->\tThis must be the FULL PATH (relative)\n";
    print $fh "\t-o <path>\tOutput FULL PATH & FILENAME\n";
    print $fh "\t\t--->\tMust also be FULL PATH (relative)\n";
    print $fh "\t--help\t\tPulls Up This Help Text\n";
    print $fh "\t--version\tDisplays The Program Version Info\n";
    print $fh "\t--------- ========= ---------\n";
}
sub VERSION_MESSAGE { # this function is called using the --version flag
    my $fh = shift;
    print $fh "\t--------- ========= ---------\n";
    print $fh "\t\tWordlist Compiler ".VERSION."\n";
    print $fh "\tcreatedBy\tdarksider\n";
    print $fh "\temailAddy\tdarksider\@swedger.com\n";
    print $fh "\tsiteAddy\twww.swedger.com\n";
    print $fh "\t--------- ========= ---------\n";
}
#    WordCompi Subroutines

```[/LEFT]
[B]- SOURCE -
[/B][/CENTER]

---

### Post by trent.josephsen on 2010-05-05
And my supervisor complained about *my* use of whitespace...

Seriously, do you usually code consecutive statements on the same line or is it a copy/pasting problem?

---

### Post by myrtle1908 on 2010-05-05
You have posted a "wall of code" :)

1. Always use strict and warnings.  There are rare ocassions where you should not but this is not one of them.

2. Consider breaking your program up into logical subroutines to improve readability and maintenance.

3. Instead of constantly "dying" in-line, consider creating a "error" routine where you can deal with your *interesting* headers ...

```
("\n\t\t<X]---------<<   =========   >>---------[X>)
```


4. Declaring vars with 'my'.  Sometimes you do, sometimes not.  Using strict and warnings will help you there.

5. Consider using heredocs for text walls.

6. IMO it is bad practice to blind clear the console.

7.  Multi-column coding ... don't do that.

I haven't run your program so there may be other issues but those jumped out at me.

Good Luck!

---

### Post by soltanis on 2010-05-05
Perl: the lossy compression of programming languages.

---

### Post by lonewaster on 2010-05-06
hey all.
uhm...**thanks** for the replies. didn't expect **this** much response to my silly little bit of code =]
Thanks for all the replies, I will try and have a go at them...now!!

> **trent.josephsen said:**
> And my supervisor complained about *my* use of whitespace...

Seriously, do you usually code consecutive statements on the same line or is it a copy/pasting problem?

***supervisor ?*** what do you work as? if it involves programming - [I]i want it !!
[/I]if you look at the code you'll notice that I only (for the most part) have one statement per line, but the ones where I'm doing more on one singular line are all part of the first statement.
For instance, If I'm taking some user input, 

[LIST=1]
[*]I print the message asking for it,
[*]I get the input and store it in a variable,
[*]And I print a line feed character to finish it off.
[/LIST]
I know it isn't that great, and to be honest the only reason it's like that is because I completely forgot to alter the version I paste on here to be more...***other ****people friendly* :p
I have some ... weird .. programming habits that help me be more efficient, but that, overall, are probably the complete opposite of that.

> **myrtle1908 said:**
> You have posted a "wall of code" :)

1. Always use strict and warnings.  There are rare ocassions where you should not but this is not one of them.

2. Consider breaking your program up into logical subroutines to improve readability and maintenance.

3. Instead of constantly "dying" in-line, consider creating a "error" routine where you can deal with your *interesting* headers ...

```
("\n\t\t<X]---------<<   =========   >>---------[X>)
```
4. Declaring vars with 'my'.  Sometimes you do, sometimes not.  Using strict and warnings will help you there.

5. Consider using heredocs for text walls.

6. IMO it is bad practice to blind clear the console.

7.  Multi-column coding ... don't do that.

I haven't run your program so there may be other issues but those jumped out at me.

Good Luck!

woah..thank you =]
I realise my code looks really messy to others. As i mentioned above, I forgot to change it for **human** consumption :guitar:
Anyway, I learned perl from "Perl For Dummies" - years ago..when I was about 11.
It never taught me to use warnings **or** strict, and therefore I'm having trouble getting into that habit.
Similar problem with defining variables in the proper fashion.
You'll notice I do it properly **sometimes,** and then without the *my* part on other occasions.
I will **most definitely **make an error() subroutine to compact my code and also make it that little bit more efficient.
What is bad about clearing the console ??
I just thought that it makes the program look a bit..neater...
I will also convert the script into subroutines and make it a little bit nicer-to-look-at.

> **soltanis said:**
> Perl: the lossy compression of programming languages.
i was supposed to learn about lossy compression...for my next interview for membership to what.cd ... uhm...yeah.. not a clue :p

So uhm..yeah...thanks for all the comments. Much appreciated.
I will be sure and address this stuff when I'm working on this script.
For now, though, I'm playing the PS3 :lolflag:
Just got ***Darksiders **&& **Saint's Row 2** *over the weekend.
So...tis time to rock `n` roll !!
:guitar:
-darksider-

---

### Post by lonewaster on 2010-05-06
okay...It was bugging me so I decided to have a go at cleaning this code up a little.
In this version increment-

[LIST]
[*]Subroutines are being used to make the script more...efficient? What's the word for a program that is made to work around functions/subs ?? ***Modular?***
[*]I have added the ***use warnings*** && ***use strict **includes* - and I am going to try my best to continue using them. I might start using **templates** with my IDE, and make my own one that has the perl location string, comment block and basic includes...
[*]I have spread the code out on the page, sort of putting it into **blocks** of related code. Separated most of the one-liners and also added comments where there were none before. (some of the one-liners are still there. for instance, if statements that run only **one** command IF the expression is met).
[/LIST]
 The reason my code is so compressed normally, is because when I was younger and learning all the different languages that I use today, I was told by other programmers that my code was "too spaced out" because I used to split it all up so that it was easier to read..
I figure it must just be a case of spacing it out ***appropriately*** to make it easier to read, whilst not losing too much of the compression ?
Thanks again for the input/comments/constructive criticisms !!! :lolflag:
Please let me know what you think now, folks!!
[I][B]-darksider-

P.S.-[/B][/I] for those of you who already have the script(v2) saved on your box-
I have prepared a **patch**.
It is being hosted at my site (not online yet) courtesy of my mate Thetan, who has provided me with some temp hosting until my server is complete.
[http://www.swedger.com/patch.diff](http://www.swedger.com/patch.diff)

Otherwise, feel free to use/look at the source- Posted **below...**
 [CENTER][I][B]-SOURCE-
[/B][/I] [LEFT]```

#!/usr/bin/perl
# # # # # # # # # # # # #
#    Wordlist Compiler    #
#            v3            #
#      www.swedger.com        #
# # # # # # # # # # # # #
use strict;
use warnings;
use constant VERSION => 'v2.0';
use File::Basename; # use the File::Basename module - used to split up the OUTPUT path later, to run file tests on it
system('clear'); # clears the terminal, so it looks nice and neat
use Getopt::Std; # use the getopt standard module
$Getopt::Std::STANDARD_HELP_VERSION = 1; # for using the sub main::HELP_MESSAGE
my %flag=(); # define the hash for storing flag calls(MODE, SOURCE && OUTPUT) and their respective contents
getopts("m:s:o:",\%flag); # get options. s{SOURCE}    +    o{OUTPUT}    +    m{MODE}
my $src=$flag{s}; # SOURCE path flag
my $out=$flag{o}; # OUTPUT path flag
my $mode=$flag{m}; # MODE flag.   --->   move these into variables

if($mode eq "") { # if the user didn't specify a mode
    &fatal_err("You Have Not Chosen A Mode!!\nWhat do you want me to do?Maybe if you ask nicely, or even say PLEASE, I might just 'work' - no questions asked!!");
}
elsif($mode ne "0" && $mode ne "1") { # if the user chose an INVALID mode
    &fatal_err("You Have Selected An INVALID Mode (-m <mode>)\nThe Following Are The Accepted Modes-\n0\t-=>\tSTANDARD- Compiles Every File From The Source Into One File.\n1\t-=>\tSame As Option 0 Except You Must Select YES/NO On Each File.");
}
if($src eq "") { # if the user didn't specify a SOURCE path
    &fatal_err("You MUST Provide A Source Directory!\nWhat did you expect to happen?\nTell you what- Why don't you shut your eyes, clasp your hands, and PRAY for it?\nThat will do about as much good as passing me no input!!");
}
elsif(!-e $src) { # if the specified SOURCE doesn't exist
    &fatal_err("The Specified Source Directory DOES NOT EXIST!!\nPlease check that it does and check you spelled it correctly.\nThen try again.");
}
elsif(!-d $src) { # if the specified SOURCE is not a directory
    &fatal_err("The Specified Source IS NOT A DIRECTORY!!\nPlease check your selection is correct and check you spelled it correctly.\nThen try again.");
}
if($out eq "") { # if the user didn't specify an OUTPUT path
    &fatal_err("You Need To Specify An Output PATH + FILENAME\nWhat do you want me to do?\nMaybe if you ask nicely, or even say PLEASE, I might just 'work' - no questions asked!!");
}
else { # if the user actually provided an output path
    my ($filename,$path,$suffix)=fileparse($out); # parse it into vars for testing

    if(!-e $path) {
        &fatal_err("That Directory (".$path.") Doesn't Exist!!\nPlease check it, make sure it's spelled correctly, and try again");
    }
    elsif(-e $filename.".".$suffix) {
        &fatal_err("The File You Want To Output Into (".$filename.".".$suffix.") Already Exists.\nFor safety reasons, You may only use me to write into a NEW file.\nPlease try again.");
    }
    else { # and, so long as the specified folder EXISTS - move on with the process
        if(substr($src,(length($src)-1),1) ne "/") {
            $src=$src.'/';
        }

        print "The Following Files Have Been Prepped For Compiling:\n"; # alert the user
        my @files = <$src*.*>; # get a list of every FILE in the directory
        my @combi=(); # define the (empty) list for putting all the files in the SOURCE directory into

        foreach my $file (@files) { # and for each of those files-
            #$fn=fileparse($file); # parse it into vars for testing. (commented out. depracated as I now use -1 in the substr() function.
            if(substr($file,-1,1) eq "#") { # if the filename begins with a # symbol (so that 'comment files' will not be added to the RESULT file)
                print $file." was IGNORED(#Comment.file)\n"; # then print the file and note that it was excluded as a 'comment file'
            }
            else { # otherwise, if the file passed the checking routine, then
                push(@combi,$file); # add it to the list used to read and compile all the files together
                print "\t+   ".$file."\n"; # print it on the screen, so the user can decide whether to continue/cancel after this loop
            }
        }

        print "\nPlease Check Over The List Above.\nIf You Want To Cancel, Press CTRL+C & To Continue, Press ENTER...";my $waitForEnter=<>;print "\n";
        my $linefeed=$/; # backup the line ending recognition character
        undef $/; # then undefine it, so we can read each file, in its entirety, into one, scalar, variable
        &compLine("# # # # # # # # # # # # # # # # # # # # # # # # # # # #\n",$out);
        &compLine("#   Wordlist Compiler   [WordCompi]   v3\n",$out);
        &compLine("#   createdBy   darksider\n",$out);
        &compLine("#   emailAddy   darksider\@swedger.com\n",$out);
        &compLine("#   siteAddy    www.swedger.com\n",$out);
        &compLine("# # # # # # # # # # # # # # # # # # # # # # # # # # # #\n",$out);
        &compLine("#     This Wordlist Was Compiled From Multiple Files\n",$out);
        &compLine("#     The names of these files are printed at\n",$out);
        &compLine("#     the top of the compiled list of words taken from them.\n",$out);
        &compLine("# # # # # # # # # # # # # # # # # # # # # # # # # # # #\n\n",$out);
        my %hash=(); # create a hash to store all the words in (using a hash is easier because it means no dittos [duplicates] will be in the final file)
        my $file=""; # define the variable used in the foreach() loop, below

        foreach $file (@combi) { # for each of the files in the @combi list we compiled from the files (above)
            if($mode eq "1") { # if the user chose mode #1, ask YES/NO at each file ---> gives them more control over which files are added
                $/=$linefeed; # restore the line ending recognition character variable to it's former value, so the program recognises the user's choice
                # NOTE: WITHOUT THE LINE ENDING RECOGNITION CHARACTER VARIABLE BEING SET, THE SCRIPT WOULDN'T KNOW WHEN THE USER HAD PRESSED ENTER!!
                ASK: # label for jumping back if the user gives a wrong answer (yes/no)
                print "Compile ".$file." ?? [Y/N]: ";my $answer=lc(<>);chomp($answer);print "\n";# ask(yes/no) whether to add the file(lowercase the answer)
                if($answer eq "n") { next; } # if they don't want to add the current file, then jump to the next foreach iteration
                elsif($answer ne "y") { print "Answer Y OR N !!\n";goto ASK; } # if the user gives an INVALID choice, then jump back to the ASK label
            }

            &compLine("# File Compiled: ".$file."\n",$out);
            undef $/; # remove the line ending recognition character again for reading the file(s) into one, scalar, variable
            open(SRC,"<".$file); # open the file,
            my $source=<SRC>; # read all it's contents into a scalar variable,
            $source =~ s/\n/ /g; # get rid of every newline char (\n) and replace them all with a space (so the split() call below works properly)
            my @words=split(' ',$source); # then split the file into words. (the bit above also means that if a file is one-word-per-line - it will still compile)
            my $word=""; # define the variable used in the foreach() loop in the line below

            foreach $word (@words) { # and then, for each word in this file -
                $hash{$word}=1; # put the word into the hash
            } # move onto the next word and repeat until every word from this file has been added to it
        } # and then loop through again and again until every word from ever one of the files has been added to the hash

        &compLine("\n",$out); # print a newline into the OUTPUT file
        $/=$linefeed; # restore the line ending recognition character back to normal. good practice =]
        my $key=""; # define the var used in the loop below

        foreach $key (keys %hash) { # for each element in the hash containing all of the words to go into the final RESULT
            &compLine($key."\n",$out); # print the new word into the RESULT file, followed by a linefeed character
        }
    }
}

#    WordCompi Subroutines    #
sub compLine { # this subroutine opens the desired output file, writes the specified line into it, and closes it.
    my $line=shift(@_); # store the provided line into a variable for tidiness
    my $out=shift(@_); # store the desired output file into a variable as well
    open(RESULT,">>".$out); # create & open the desired output file for APPENDING [>] (so that this works - opening & closing all the time)
    print RESULT $line; # print the provided line(s) into the RESULT file
    close(RESULT); # and close the desired RESULT file
}
sub fatal_err { # this error sub is called when the error needs to terminate the program
    my $errmsg=shift(@_);
    print "\n\t\t<X]---------<<   =========   >>---------[X>\n"; # print my strange header - because i can!!
    print $errmsg; # print the error message passed to function
    print "\n\t\t<X]---------<<   =========   >>---------[X>\n"; # print my equally-strange footer - because if i don't my family will die!!
    exit; # and terminate the program
}
sub HELP_MESSAGE { # function ran when the user calls the --help flag
    my $fh = shift;
    print $fh "\t--------- ========= ---------\n";
    print $fh "\t-m (#)\t\tMode Setting\n";
    print $fh "\t\t--->\t0 - Standard Compile (automatic)\n";
    print $fh "\t\t--->\t1 - Standard Compile(Yes/No At Each File)\n";
    print $fh "\t-s (path)\tSOURCE Directory Path\n";
    print $fh "\t\t--->\tThis must be the FULL PATH (relative)\n";
    print $fh "\t-o <path>\tOutput FULL PATH & FILENAME\n";
    print $fh "\t\t--->\tMust also be FULL PATH (relative)\n";
    print $fh "\t--help\t\tPulls Up This Help Text\n";
    print $fh "\t--version\tDisplays The Program Version Info\n";
    print $fh "\t--------- ========= ---------\n";
}
sub VERSION_MESSAGE { # this function is called using the --version flag
    my $fh = shift;
    print $fh "\t--------- ========= ---------\n";
    print $fh "\t\tWordlist Compiler ".VERSION."\n";
    print $fh "\tcreatedBy\tdarksider\n";
    print $fh "\temailAddy\tdarksider\@swedger.com\n";
    print $fh "\tsiteAddy\twww.swedger.com\n";
    print $fh "\t--------- ========= ---------\n";
}
#    WordCompi Subroutines    #


```
[/LEFT]
 [I][B]-SOURCE-
[/B][/I][/CENTER]

---

### Post by trent.josephsen on 2010-05-06
Yeah, I am a programmer at a university.  Mostly Perl, some SQL, some HTML, and every once in a while I encounter something odd.  Too little whitespace is something I've been admonished for.

Anyway, about your code... it seems to work well enough, but it isn't very... Perl-ish, I guess.  For example you use
```
if($mode eq "") { # if the user didn't specify a mode
    &fatal_err("some error string");
}
```
instead of the more idiomatic
```

$mode or die "some error string";

```

You can use heredocs or multi-line strings to clean up the hodgepodge of prints and escape characters, e.g. in &fatal_err:
```

sub fatal_err {
    my $errmsg=shift;
    print "

        <X]---------<<   =========   >>---------[X>
$errmsg
        <X]---------<<   =========   >>---------[X>
";
    exit;
}
```
Much cleaner, no?  (I took the liberty of editing shift(@_) to just shift.)  For another thing, you probably want to die instead of just exit when you encounter a fatal error -- it will print a standard Perl error message (along with your addendum if provided) and return a nonzero value for you.

You seem to cram as much as you can onto each line.  I stick to 80 columns most of the time, and follow the One True Brace Style almost without fail.  Using all caps for &HELP_MESSAGE (which I would probably call &usage) and &VERSION_MESSAGE is a little unusual, as well.

EDIT: never mind, didn't realize those names were special to Getopt::Std.

There's nothing *wrong* with your code; it's just, well, I'll say "stylistically unique". ;)  If you want to get a job programming Perl, may I strongly suggest getting a copy of O'Reilly's book *Programming Perl*, which was written in part by Larry Wall and will help you grasp some of the conventions that are usually followed.  Else, just lay hands on other people's code and get used to reading it, which will give you a new appreciation for readability.

If you just enjoy writing code for yourself, that's okay too, but you probably won't get much help from others ;)

---

### Post by lonewaster on 2010-05-06
hey man, thanks for the advice/comments,.
No way in hell I could be a perl programmer rofl.. I don't enjoy it THAT much =P
Thanks for the notes, I will be sure and take them onboard when I am working on this script again.
Just made another script that takes the URL of a contents page (of one of those online-ebook things?) and loops through each of the links on the page and saves it to the defined folder.
(if the user uses ***-m 1*** then it asks for Y/N at each file, too. Giving you lots of control over which files are actually saved.
Very basic..If you fancy a looksee then ask an I will post you some source.
I don't think there's even places in Scotland where you **can** get paid to program in perl...
Anyway- I would much rather learn C++ and get into games development or AI Programming, or get a job using my PHP, CSS, HTML & JS knowledge.
Thanks for the input though!!
I will definately have a look athrough what you said tomorow or at some point when i feel like coding..been at it all day now- gonna play the PS3 and watch TV and eat chocolate & ice cream >=]

laters

***-darksider-***

---

