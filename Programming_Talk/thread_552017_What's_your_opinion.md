---
title: "What's your opinion?"
date: 2007-09-15
forum: Programming Talk
---

### Post by eph1973 on 2007-09-15
I am learning Perl.  I just finished the book, Learning Perl, and plan on probably pursuing the Alpaca book by O'Reilly (Learning Perl References, Objects, and Modules).  So anyhow, I decided to try to write a command line calculator.  Yes, I know there's a bazillion calculators out there, and it's not like I am really doing anything new here.  And I am aware of the possibility that there is a module or something that makes all this moot.  But, before I develop any really bad habits, or am going about things in a bad way, I would like anyone knowledgeable to Perl to give me any feedback on the way I have written this.  Also, no offense to the Python coders out there, but I am trying to learn Perl at the moment, so I am not currently interested to know how to do it in Python (I'll try to learn that later).  This little program just pretty much sums up most of what I have learned from the Llama book, which is why I did it.  Thank you guys for any feedback you give me.
```
#!/usr/bin/perl
# Turned warnings off to keep the compiler from crying about using zeroes in comparisons
use strict;

my $error;      # used in &errorCode to determine if and what type of unreasonable input the user has entered

print "Enter equations while you want to use the calculator, or enter 'exit' or 'quit' to leave\n";
print "\nEnter your equation: ";
while(<STDIN>){
    chomp;
    last if /\s*exit\s*|\s*quit\s*/i;
    s/=\s*$//;
    s/\)\s*\(/)*(/g;
    s/(\d)\s*\(/$1*(/g;
    my $answer = &parseString($_);
    if($error){
        &errorCode;
        print "Enter your next equation: ";
        next;
    }
    print "$_ = $answer\n";
    print "Enter your next equation: ";
}

print "Thank you for using the Command Line Calculator\n";

# Begin subroutine definitions

# The purpose of this subroutine is to parse out any parenthesis and send those expressions to calcStr first
# then send the remainder of the expression to calcStr
sub parseString{
    my $total;
    my $string = " ";           # makes sure that the first element of $string cannot be "(" to prevent errors in
    my $openParen;              # the parenthesis parsing section in the infinite loop below
    my $lastOpenIndex;
    my $closeParen;
    $string .= $_;
    while(1){
        if($string =~ /\)/ && !($string =~ /\(/)) {
            $error = 1;
            return $error;
        }
        $openParen = index($string, "(", $lastOpenIndex + 1) if !(defined($closeParen));
        $lastOpenIndex = $openParen if $openParen > 0;
        $lastOpenIndex = undef if $lastOpenIndex < 0;
        next if $openParen > 0;
        $closeParen = index($string, ")", $lastOpenIndex + 1);
        if(defined($lastOpenIndex) && $closeParen > 0){
            my $subString = substr($string, $lastOpenIndex, $closeParen-$lastOpenIndex+1);
            my $subTotal = &calcStr($subString);
            substr($string, $lastOpenIndex, $closeParen-$lastOpenIndex+1) = "$subTotal";
            $lastOpenIndex = undef;
            $closeParen = undef;
            next;
        }
        if($string =~ /\(/){
            next if($string =~ /\)/);
            $error = 1;
            return $error;
        }
        $total = &calcStr($string);
        last;
    }
    return $total;
}

# This subroutine does the calculations, taking in account order of operations for a given expression
sub calcStr{
    my $base;       # I used different names for each mathmatical function.  In reality, you could reduce all these
    my $power;      # scalars down to just $num1, $num2, $answer, and $equation.  I used so many names just to keep
    my $result;     # them all straight in my head while I was writing this.
    my $factor1;
    my $factor2;
    my $product;
    my $dividend;
    my $divisor;
    my $quotient;
    my $addend1;
    my $addend2;
    my $sum;
    my $minuend;
    my $subtrahend;
    my $difference;
    my $equation;
    
    my $str = shift @_;
    $str =~ s/\(//;          # parenthesis no longer needed at this point
    $str =~ s/\)//;
# Infinite loop to step through the expression, going by order of operations, and replacing each part of the expression
# as it steps through.  The final step is to remove the spaces from the answer, and it breaks the loop if unreasonable
# input is given
    while(1){
        # checking for the exponent symbol "^", and whether if a negative is used,
        # if it is at the beginning of the string or a space is used right before to prevent confusion with substraction
        if($str =~ (/^-?\d+\.?\d*\s*\^\s*-?\d+\.?\d*|\s+-\d+\.?\d*\s*\^\s*-?\d+\.?\d*|\d+\.?\d*\s*\^\s*-?\d+\.?\d*/)) {
            $equation = $&;
            $equation =~ /^-?\d+\.?\d*/;
            $base = $&;
            $equation =~ /-?\d+\.?\d*$/;
            $power = $&;
            $result = $base ** $power;
            $str =~ s/^-?\d+\.?\d*\s*\^\s*-?\d+\.?\d*|\s+-\d+\.?\d*\s*\^\s*-?\d+\.?\d*|\d+\.?\d*\s*\^\s*-?\d+\.?\d*/ $result /;
        }
        # checking for the multiplication symbol "*"
        elsif($str =~ (/^-?\d+\.?\d*\s*\*\s*-?\d+\.?\d*|\s+-\d+\.?\d*\s*\*\s*-?\d+\.?\d*|\d+\.?\d*\s*\*\s*-?\d+\.?\d*/)) { 
            $equation = $&;
            $equation =~ /^-?\d+\.?\d*/;
            $factor1 = $&;
            $equation =~ /-?\d+\.?\d*$/;
            $factor2 = $&;
            $product = $factor1 * $factor2;
            $str =~ s/^-?\d+\.?\d*\s*\*\s*-?\d+\.?\d*|\s+-\d+\.?\d*\s*\*\s*-?\d+\.?\d*|\d+\.?\d*\s*\*\s*-?\d+\.?\d*/ $product /;
        }
        # division symbol "/"
        elsif($str =~ (/^-?\d+\.?\d*\s*\/\s*-?\d+\.?\d*|\s+-\d+\.?\d*\s*\/\s*-?\d+\.?\d*|\d+\.?\d*\s*\/\s*-?\d+\.?\d*/)) { 
            $equation = $&;
            eval {
                $equation =~ /^-?\d+\.?\d*/;
                $dividend = $&;
                $equation =~ /-?\d+\.?\d*$/;
                $divisor = $&;
                $quotient = $dividend / $divisor;
            };
            if($@){
                $error = 2;
                return $error;
            }
            $str =~ s/^-?\d+\.?\d*\s*\/\s*-?\d+\.?\d*|\s+-\d+\.?\d*\s*\/\s*-?\d+\.?\d*|\d+\.?\d*\s*\/\s*-?\d+\.?\d*/ $quotient /;
        }
        # subtraction symbol "-"
        elsif($str =~ (/^-?\d+\.?\d*\s*-\s*-?\d+\.?\d*|\s+-?\d+\.?\d*\s*-\s*-?\d+\.?\d*|\d+\.?\d*\s*-\s*-?\d+\.?\d*/)) { 
            $equation = $&;
            $equation =~ /^-?\d+\.?\d*/;
            $minuend = $&;
            $equation =~ /\d+\.?\d*$/;
            $subtrahend = $&;
            $subtrahend *= -1 if $equation =~ /-\s*-/;      # If subtrahend is negative, it puts the minus sign back on
            $difference = $minuend - $subtrahend;
            $str =~ s/^-?\d+\.?\d*\s*\-\s*-?\d+\.?\d*|\s+-?\d+\.?\d*\s*-\s*-?\d+\.?\d*|\d+\.?\d*\s*-\s*-?\d+\.?\d*/ $difference /;
        }
        # addition symbol "+"
        elsif($str =~ (/^-?\d+\.?\d*\s*\+\s*-?\d+\.?\d*|\s+-\d+\.?\d*\s*\+\s*-?\d+\.?\d*|\d+\.?\d*\s*\+\s*-?\d+\.?\d*/)) { 
            $equation = $&;
            $equation =~ /^-?\d+\.?\d*/;
            $addend1 = $&;
            $equation =~ /-?\d+\.?\d*$/;
            $addend2 = $&;
            $sum = $addend1 + $addend2;
            $str =~ s/^-?\d+\.?\d*\s*\+\s*-?\d+\.?\d*|\s+-\d+\.?\d*\s*\+\s*-?\d+\.?\d*|\d+\.?\d*\s*\+\s*-?\d+\.?\d*/ $sum /;
        }
        
        elsif($str =~ /\s+/){
            $str =~ s/\s+//;
        }
        else{
            last;
        }
    }
    $error = 3 unless $str =~ /^-?\d+\.?\d*$/;
    return $str;
}

sub errorCode{
    print "Error: ";
    print "Mismatched parenthesis\n" if $error == 1;
    print "Divide by 0\n" if $error == 2;
    print "Non mathmatical characters used\n" if $error == 3;
    $error = 0;
}
```

---

### Post by pmasiar on 2007-09-16
as you found yourself, Python community is more vibrant that Perl. PerlMonks is (or was years ago when I participated) vibrant  community of Perl hackers witha flavor of "seeking enlightment" posts. maybe you want to ask there.

Good luck!

PS. Or maybe really just cut your losses and switch to Python. There is nothing what Perl can do and Python cannot - but Python is the language with more future, IMNSHO.

---

### Post by dugh on 2007-09-16
You might check out ruby.    You can even do so in your web browser: [http://tryruby.hobix.com/](http://tryruby.hobix.com/)


If you want to develop desktop or rich internet applications, see jvm-based languages such as java and scala and javafx.  Netbeans is a free GPL development environment (IDE) that supports java, javafx, and ruby.

The other main alteranative for desktop applications (but not applets) is mono/.net.  There is a mono IDE that runs in ubuntu called monodevelop, and it supports a nice python-like language called boo.

---

