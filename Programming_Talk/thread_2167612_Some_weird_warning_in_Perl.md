---
title: "Some weird warning in Perl"
date: 2013-08-14
forum: Programming Talk
---

### Post by Ninja&gt;Master on 2013-08-14
I made a program that translates English sentences to Pig Latin. It works fine when I type in: "Hello World!" as input. However, when I type in "I love to eat pizzas.", it gives an error: 
```

Use of uninitialized value in concatenation (.) or string at PELater.pl line 44, <STDIN> line 2.

```

Why is that so?

Here is the code"
```

#Copyright(c) 2013 - Ahnaf Tahmid

#This program is free software: you can redistribute it and/or modify
#it under the terms of the GNU General Public License as published by
#the Free Software Foundation, either version 3 of the License, or
#(at your option) any later version.

#This program is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.

#You should have received a copy of the GNU General Public License
#along with this program.  If not, see <http://www.gnu.org/licenses/>.

use 5.010;
use strict;
use warnings;


sub ends_with_symbol
{
    my @symbols = ('!', '@', '$', '%', '^', '&', '*', '(', ')', '+', ',', '=', '-', '_');
    my $word = shift;
    my $last_char = substr($word, length($word)-1, 1);
    if(grep(/^$last_char$/, @symbols))
    {
        return 1;
    }
    else
    {
        return 0;
    }
}


sub to_pl
{
    my $data = shift;
    my @words = split(' ', $data);
    my $translated = " ";
    my $any_symbol = " ";
    my $pl_word;
    my $capitalize = 0;
    
    foreach my $word(@words)
    {
        if(ends_with_symbol($word) == 1)
        {
            $any_symbol = substr($word, length($word)-1, 1);
            $word = substr($word, 0, length($word)-1);
        }
        my $first_letter = substr($word, 0, 1);
        if($first_letter eq uc($first_letter))
        {
            $capitalize = 1;
            $first_letter = lc($first_letter);
        }
        if($capitalize == 1)
        {
            $pl_word = uc(substr($word, 1, 1)).substr($word, 2, length($word)-2).$first_letter."ay";        
        }
        else
        {
            $pl_word = substr($word, 1, length($word)-1).$first_letter."ay";
        }
        if($any_symbol ne " ")
        {
            $translated = $translated.$pl_word.$any_symbol." ";
        }
        else
        {
            $translated = $translated.$pl_word." ";
        }
        $any_symbol = " ";
        $capitalize = 0;
    }
    return $translated;
}


say "English -> Pig Latin Converter v1.0 BETA.";
say "Copyright(c) 2013 - Ahnaf Tahmid.";
say "Licensed under GPL-v3";
say "-----------------------------------------";
print "\n";
say "[1] Read from a file.";
say "[2] Input text in prompt.";
say "[3] Exit.";
print "\n";
print "Enter an option: ";
my $option = <STDIN>;
chomp($option);


print "\n";
if($option eq "1")
{
    print "Enter the filename (eg: example.txt): ";
    my $file_name = <STDIN>;
    chomp($file_name);
    open(FILE, '<', $file_name) or die("Error processing file.");
    open(NEWFILE, '>', 'pig_latin.txt') or die ("Unexpected error.");
    while(<FILE>)
    {
        my $paragraphs = <FILE>;
        my $trans = to_pl($paragraphs);
        print NEWFILE "$trans\n";
    }
    close(FILE);
    close(NEWFILE);
    print "Press ENTER to exit...";
    my $exit_prompt = <STDIN>;
}
elsif($option eq "2")
{
    say "Type in as much as you want. Press ENTER when you are done.";
    print "-> ";
    my $paragraphs = <STDIN>;
    chomp($paragraphs);
    my $trans = to_pl($paragraphs);
    say "In Pig Latin: $trans";
    print "Press ENTER to exit...";
    my $exit_prompt = <STDIN>;
}
else
{
    print "Press ENTER to exit...";
    my $exit_prompt = <STDIN>;
}

```

---

### Post by spjackson on 2013-08-14
Your problem is with the substring expressions in
```

    $pl_word = uc(substr($word, 1, 1)).substr($word, 2, length($word)-2).$first_letter."ay";

```
When the word is "I" and has a length of 1, what do you think those substring expressions mean?

---

### Post by Ninja&gt;Master on 2013-08-14
> **spjackson said:**
> Your problem is with the substring expressions in
```

    $pl_word = uc(substr($word, 1, 1)).substr($word, 2, length($word)-2).$first_letter."ay";

```
When the word is "I" and has a length of 1, what do you think those substring expressions mean?

Ah, so that is the problem. Thanks.

---

