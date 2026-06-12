---
title: "Need help with script! (any language welcome)"
date: 2007-02-13
forum: Programming Talk
---

### Post by Wybiral on 2007-02-13
Hi!

I'm trying to write a script that will essentially turn a file that looks like this...

```

.LFB1456:
	pushl	%ebp
.LCFI0:
	movl	%esp, %ebp
.LCFI1:
	movl	8(%ebp), %edx
	movl	$0x00000000, %eax
	movl	%eax, (%edx)
	movl	8(%ebp), %edx
	movl	$0x00000000, %eax
	movl	%eax, 4(%edx)
	movl	8(%ebp), %edx
	movl	$0x00000000, %eax
	movl	%eax, 8(%edx)
	popl	%ebp
	ret

```

Into this...

```

.LFB1456:
	pushl	%ebp
.LCFI0:
	movl	%esp, %ebp
.LCFI1:
	movl	8(%ebp), %edx
	movl	$0x00000000, (%edx)
	movl	8(%ebp), %edx
	movl	$0x00000000, 4(%edx)
	movl	8(%ebp), %edx
	movl	$0x00000000, 8(%edx)
	popl	%ebp
	ret

```

But, naturally... That's just an example, it wont always look like that.

1. Basically, whenever a line begins with "movl" and ends with "%eax"
2. And the next line begins with "movl %eax, "
3. I want to take the first operand from the first "movl" op, and replace the "%eax" on the next line with that value.
4. Then delete the previous line.

I know that this shouldn't be too hard with BASH or python... But I'm not used to this kind of parsing. I could write it out manually, but if there is a more elegant way to do this I would definitely rather not waste a bunch of time typing some state-machine based parser.

In case you're wondering... Yes, this is a small post-compile pre-assemble optimization for GCC.

I've been doing this manually and then I said... Wait a minute... WTF am I doing??? I need a script...

Anyway... If anyone has a good direction to go for doing this, I would love to hear it. Thanks!

---

### Post by highneko on 2007-02-13
Edit: Nvm. Error I made. I'll try again.

---

### Post by Wybiral on 2007-02-13
Oh yeah... The lines begin with a tab, and there's a tab between "movl" and the first operand.

---

### Post by phossal on 2007-02-13
```
#!/usr/bin/perl

##########################
# Assembly Parser
# 2/13/2007 
# phossal/wybiral
###########################

#File to parse; 
$file = $ARGV[0];

#Read in the file contents
open (INF, "<$file") or die "Cannot open file";
@contents = <INF>;


#Loop through file contents
$count = 0;
foreach (@contents) {
	
	$line = $_; #Current Line
	
	if ($skip != 1) { #If not skipping this line...
		
		#...test to see if it matches format (movl $value, %eax)
		if ($line =~ /^\s+movl\s+(.*)\s+\%eax/) { #If it matches, test to see if the next line matches...
	
			$preceeding = $line;
			$value = $1;

		
			#Does next line match format (movl %eax, ...)
			if ($contents[$count + 1] =~ /^\s+movl\s+\%eax,\s+(.*)/) { 
				
				#If both lines matched the search, we make the substitution
				#and add a single line to the new content array 
				$next = $contents[$count + 1];
				$next =~ s/%eax,/$value/;
				push(@newcontents, $next);
				
				chomp($preceeding);
				print "Adjusted line: $count $preceeding\n";

				$skip = 1;
	
			} else { 
				#If the second line didn't match, we just add both lines
				push(@newcontents, $line);
				$next = $contents[$count + 1];
				push(@newcontents, $next);
			}
	
		} else { #If the first line didn't even match, we simply add it
			push(@newcontents, $line);
		}

	} else { #If we skipped a line, reset $skip so that we don't skip next line.
		$skip = 0;
	}
	
	$count ++; #Increment counter to stay in unison.
}


#########################
##### UPDATED 3/5/2007 ########
#########################
#
# To overwrite the file in question, remove 
# the x following the argument.
# instead of the line: 
# 
# open (OUF, ">${file}***[COLOR="Red"]x[/COLOR]***")or die "Cannot Open File";
#
# replace it with:
#
# open (OUF, ">${file}")or die "Cannot Open File";

#Write the new file with the same name as old file, and an x appended.
open (OUF, ">${file}x")or die "Cannot Open File";
foreach (@newcontents) {
	print OUF $_;	
}

```

---

### Post by highneko on 2007-02-13
I can't do the operand thing. Very tired. Maybe this will help someone help you:
```
sed '/%eax$/ s/%eax/(%edx)/g;/%eax/ s/.*//g' test.txt
.LFB1456:
        pushl   %ebp
.LCFI0:
        movl    %esp, %ebp
.LCFI1:
        movl    8(%ebp), %edx
        movl    $0x00000000, (%edx)

        movl    8(%ebp), %edx
        movl    $0x00000000, (%edx)

        movl    8(%ebp), %edx
        movl    $0x00000000, (%edx)

        popl    %ebp
        ret
```

---

### Post by Wybiral on 2007-02-13
> **phossal said:**
> What about this?
```
#!/usr/bin/perl

$file = $ARGV[0];

open (INF, "<$file") or die "Cannot open file";
@contents = <INF>;

$count = 0;

foreach (@contents) {
	$line = $_;
	
	if ($skip != 1) {


	if ($line =~ /^\s+movl\s+(.*)\s+\%eax/) {
		$preceeding = $line;
		$value = $1;
		print $preceeding;
		
		if ($contents[$count + 1] =~ /^\s+movl\s+\%eax,\s+(.*)/) {
			$next = $contents[$count + 1];
			$next =~ s/%eax,/$value/;
			print "Adding Next: $next";
			push(@newcontents, $next);
			
			$skip = 1;

		} else {

			print "Adding Line: $line";
			push(@newcontents, $line);
			$next = $contents[$count + 1];
			push(@newcontents, $next);
		}

		 


	} else {
		print "Adding Line: $line";
		push(@newcontents, $line);
	}
	
	#increase the count for each loop

	} else {
		$skip = 0;
	}
	$count ++;
}

open (OUF, ">${file}x")or die "Cannot Open File";
foreach (@newcontents) {
	print OUF $_;	
}
```

Damn... It works great, thanks!

Now I only have one problem... 

Situations like:
```

	movl	12(%ebp), %eax
	movl	%eax, (%edx)

```
CANT be turned into...
```

	movl	12(%ebp), (%edx)

```
Because you can't move the address into the address... It would have to leave those alone.

But, It does work, I can always correct the address issue manually (unless you get bored!)

Once again, thanks.

EDIT:

Is there a way to modify your code so that it only works when the first operand of the first line begins with a "$" ?

---

### Post by phossal on 2007-02-13
I modified the posted code to search for the *$* preceeding the value.

---

### Post by Wybiral on 2007-02-13
> **phossal said:**
> I modified the posted code to search for the *$* preceeding the value.

Brilliant! It works great. Thanks a bunch! I usually do it when I go over the assembly to manually optimize things, but this script will save me a lot of time! You'd be surprised how many bytes you can chop off a program with this... And how many operations you can shave off in a tight loop. Very useful, thanks agaim.

---

### Post by phossal on 2007-02-13
> **Wybiral said:**
> **Brilliant! It works great.** Thanks a bunch! I usually do it when I go over the assembly to manually optimize things, but this script will save me a lot of time! You'd be surprised how many bytes you can chop off a program with this... And how many operations you can shave off in a tight loop. Very useful, thanks again.
You're welcome, of course. Cheers! See you around.

---

### Post by phossal on 2007-02-13
I edited it a final time to print out the line number to the terminal when it "edits" a line.

---

### Post by WW on 2007-02-13
For kicks, here's a Python variation.  It reads from stdin, and writes the optimized code to stdout.
```

#!/usr/bin/python
#
# This file reads stdin, and copies most lines to stdout.
# When a pair of lines of the form
#   [tab]movl[tab]$[anything1],[space][anything2]
#   [tab]movl[tab][anything2],[space][anything3]
# is encounted, only the single line
#   [tab]movl[tab]$[anything1], [anything3]
# is output.
#
# (The original requirement was for the case where anything2=%eax.
# I don't know if this version is an improvement, or a source of
# potential problems.)

import sys
import re

#
# The only difference between re1 and re2 is the explicit $ in re1.
# (The use of regular expressions is probably overkill--the code could
# probably be written just as easily by slitting the lines into pieces
# with, say, split().)
#
re1 = re.compile(r"""\tmovl\t\$(\S*),\s*(\S*)""")
re2 = re.compile(r"""\tmovl\t(\S*),\s*(\S*)""")

count = 0
prev = False
for line in sys.stdin:
    if not prev:
        m1 = re1.match(line)
        if m1:
            # The line matched pattern re1; save the 'from' and 'to'
            # fields, and the line itself.  Don't print it (yet).
            from1 = m1.group(1)
            to1   = m1.group(2)
            prev = True
            prevline = line
        else:
            # No match, just print the line
            print line,
    else:
        # The previous line matched pattern re1; see if this line
        # matches pattern re2.
        m2 = re2.match(line)
        if m2:
            from2 = m2.group(1)
            to2   = m2.group(2)
            if to1 == from2:
                # Match!  Compress the previous line and this one into
                # one line.
                print "\tmovl\t$"+from1+", "+to2
                prev = False
                count = count + 1
            else:
                # This line matches the movl pattern, but the 'to' field
                # of the previous line does not match the 'from' field of
                # this line.
                if from2[0] == '$':
                    # This line also matches re1, so we print the previous
                    # line, and save the current line as previous.
                    print prevline,
                    from1 = from2[1:]
                    to1   = to2
                    prevline = line
                else:
                    # No match; print both lines.
                    print prevline,
                    print line,
                    prev = False
        else:
            # This line is not a movl. Print the previous line and this one.
            print prevline,
            print line,
            prev = False
if prev:
    print prevline,

# Print the total to stderr.
sys.stderr.write("Found "+str(count)+" optimizations.\n")

```

---

### Post by Wybiral on 2007-02-13
Cool. Tools like these are pretty helpful... This is probably the number one method I use when I need to remove some bytes from a soon-to-be object file. It may not seem like much, but when there's a lot of them, it really does shave a lot off the object file. And when you're working on something that you need to be as small and fast as possible... Even just a few hundred bytes makes a big difference (especially when you do it with every object file in a project). I'm not really sure why GCC doesn't do this on it's own.

---

### Post by phossal on 2007-03-05
Here it is, it accepts any number of files as arguments with an invocation like this (assuming I save the code as *opt*):
```
perl opt file1 file2 file3
``` (up to any number)

It also will write over the files if you make the change noted in the code. With a few minutes work, we could make it accept an argument to decide whether or not to overwrite the files. Maybe later.

```
#!/usr/bin/perl

##########################
# Assembly Parser
# 2/13/2007 
# phossal/wybiral
###########################

#File to parse; 
foreach (@ARGV) {
	$file = $_;
	&process_file;
}

sub process_file () {

#Read in the file contents
open (INF, "<$file") or die "Cannot open file";
@contents = <INF>;


#Loop through file contents
$count = 0;
foreach (@contents) {
	
	$line = $_; #Current Line
	
	if ($skip != 1) { #If not skipping this line...
		
		#...test to see if it matches format (movl $value, %eax)
		if ($line =~ /^\s+movl\s+(.*)\s+\%eax/) { #If it matches, test to see if the next line matches...
	
			$preceeding = $line;
			$value = $1;

		
			#Does next line match format (movl %eax, ...)
			if ($contents[$count + 1] =~ /^\s+movl\s+\%eax,\s+(.*)/) { 
				
				#If both lines matched the search, we make the substitution
				#and add a single line to the new content array 
				$next = $contents[$count + 1];
				$next =~ s/%eax,/$value/;
				push(@newcontents, $next);
				
				chomp($preceeding);
				print "Adjusted line: $count $preceeding\n";

				$skip = 1;
	
			} else { 
				#If the second line didn't match, we just add both lines
				push(@newcontents, $line);
				$next = $contents[$count + 1];
				push(@newcontents, $next);
			}
	
		} else { #If the first line didn't even match, we simply add it
			push(@newcontents, $line);
		}

	} else { #If we skipped a line, reset $skip so that we don't skip next line.
		$skip = 0;
	}
	
	$count ++; #Increment counter to stay in unison.
}


#########################
##### UPDATED 3/5/2007 ########
# 		phossal/wybiral
#########################
#
# To overwrite the file in question, remove 
# the x following the argument.
# instead of the line: 
# 
# open (OUF, ">${file}***[COLOR="Red"]x[/COLOR]***")or die "Cannot Open File";
#
# replace it with:
#
# open (OUF, ">${file}")or die "Cannot Open File";


#Write the new file with the same name as old file, and an x appended.
open (OUF, ">${file}x")or die "Cannot Open File";
foreach (@newcontents) {
	print OUF $_;	
}

}

```

---

### Post by Mr. C. on 2007-03-05
Ah, you young programmers.  So much to learn...  :-)

This solves the problem much more elegantly.

-----

#!/usr/bin/perl -i.orig

undef $/;
$_ = <>;

s/\tmovl\t(\$[^,]*), +%eax\n\tmovl\t%eax, +(.*)/\tmovl\t$1, $2/g ;

print "$_";

---------

MrC

---

### Post by phossal on 2007-03-06
That's funny. Right after I posted my last response, I was thinking of the annual conference that the Russians often win for solving such problems with a single line. That, in a nutshell, is the beauty of perl. But it's often much *easier and faster*, to write (and work with) a page full of code that solves a complicated problem one step at a time, than to generate a single line. 1 line elegant, 2 weeks late. You old programmers delay in everything. ;)

---

### Post by Mr. C. on 2007-03-06
There are some some very, very gifted, talented, and well-educated students competing worldwide.  I've been getting more and more concerned over the years as I watch our leading ranked institutions falling further behind.

Anyway, these are great challenges.

Its easy to start falling into the build-a-state-machine trap, where thinking outside the box brings more simplicity and in the end, that means reliability.

One thing that I like about solutions like I posted, is the triviality of further extensions.  I'm sure our very bright Wybiral will find many more optimizations that will require said extensions - and most likely one more line of s/.../.../ will work just fine.

Anyway,
Enjoy!
MrC

---

### Post by phossal on 2007-03-06
Regarding Wybiral, it's *likely*, and it's *likely*. I don't disagree with anything you've posted. What you've written is *deceptively* simple. It isn't perfect, though, and editing single line programs like that is often frustrating - if you can break down "what you've written in a night of caffeine-induced genius". 

By the way, your program works on Wyb's posted problem, but it would fail on a non-tab spaced line, wouldn't it? Or would it? It's too tough to tell.

---

### Post by Mr. C. on 2007-03-06
> **phossal said:**
> I don't disagree with anything you've posted. What you've written is *deceptively* simple. It isn't perfect, though, and editing single line programs like that is a bitch. 

This can be true, but perhaps generalizations are best left to politicians.  Perfect, no, nothing is (neither is yours - there are a couple of failure points); however, the soul seeking perfection is doomed to a life of failure.

The key is to knowing your tools, understanding the problem space, and applying a solution that meets the always conflicting requirements of time, space, functionality, cost, and reliability.

Perl was designed with these problems in mind, and Mr. Wall is superbly brilliant, as are other contributors such as Tom Christiansen.  I used the language as it was designed to be used, in all its power, whilst avoiding obfuscation.

> **phossal said:**
> 
By the way, your program works on Wyb's posted problem, but it would fail on a non-tab spaced line, wouldn't it? Or would it? It's too tough to tell.

Its a simple one line regular expression.  RE folks use much more complicated ones frequently.

Ah, but my program meets the *requirements* of the problem, and allows for trivial additions; it is very simply extensible.  Assembler output is VERY structured, and the problem defined that it was.

It would be very easy to modify to various output formats.  The trick is to get out of the line-by-line thinking, and realize what you have is simply a well-formated, well-defined stream of bytes, and you are simply looking for a very easy pattern.  One could argue that your method broke apart the problem into two unnecessary states.

Let's now turn the tables; how would you add a modification that required 3 lines of assembler code matching, or four?  Each one is one more state to the state machine.

All in fun,
MrC

---

### Post by WW on 2007-03-06
MrC.: Very nice.  The key line is **undef $/;**, which allows the program to read multiple lines as a single record.

---

### Post by pmasiar on 2007-03-06
> **Mr. C. said:**
> 
This solves the problem much more elegantly.
(...)
s/\tmovl\t(\$[^,]*), +%eax\n\tmovl\t%eax, +(.*)/\tmovl\t$1, $2/g ;


Your solution might be shorter, but hardly anyone except hardcore perl hacker would call it elegant. Archetypical perl golf solution. IMHO it is rather hard to develop (you cannot easy print parts of one-liner), maintain, non-obvious and chaotic - in sense that small changes in input can make dramatic changes in output Solution appreciated by old hackers, but definitely not intended for eyes of impressionable young beginners :-)

For me, "elagant" is defined not only and not mainly by legth of the solution, but most important it should be obvious and easy to explain. As short as it can be, but not shorter.

IMHO, YMMV. I coded in Perl before, but i am recovering. :-)

---

### Post by phossal on 2007-03-06
> **Mr. C. said:**
> Ah, but my program meets the *requirements* of the problem, and allows for trivial additions; it is very simply extensible.  Assembler output is VERY structured, and the problem defined that it was.

It would be very easy to modify to various output formats.  The trick is to get out of the line-by-line thinking, and realize what you have is simply a well-formated, well-defined stream of bytes, and you are simply looking for a very easy pattern.  One could argue that your method broke apart the problem into two unnecessary states.

Your solution is better, faster, stronger. I would use it. It's delightful, and I learned something useful. Thank you. 

[Edit] I sort of lied. I didn't learn anything. I have no idea how that program works. Seriously. It does solve Wyb's problem though. That's nifty. Perhaps you'll take the time, as you did in writing that program, and as you did in responding to me, to break that down *line by line*. ;) I'd be interested in the lesson.

---

### Post by WW on 2007-03-06
For still more kicks, here is a Python program that uses the same regular expression used by MrC.  This program reads from the file given as the first command line argument, and writes the output to stdout.
```

#!/usr/bin/python

import sys
import re

f = open(sys.argv[1]).read()

fnew = re.sub(r'\tmovl\t(\$[^,]*), +%eax\n\tmovl\t%eax, +(.*)',
              r'\tmovl\t\1, \2', f)

sys.stdout.write(fnew)

```

---

### Post by Mr. C. on 2007-03-06
> **WW said:**
> For still more kicks, here is a Python program that uses the same regular expression used by MrC.  This program reads from the file given as the first command line argument, and writes the output to stdout.

That's cool.  Just for the record, mine also:

 - takes any number of files on the command line
 - edits the files in place 
 - creates a backup of the original files (in case of error)
 - accepts STDIN and writes to STDOUT, so can be used in a pipeline

MrC

---

### Post by Mr. C. on 2007-03-06
> **phossal said:**
> Your solution is better, faster, stronger. I would use it. It's delightful, and I learned something useful. Thank you. 

[Edit] I sort of lied. I didn't learn anything. I have no idea how that program works. Seriously. It does solve Wyb's problem though. That's nifty. Perhaps you'll take the time, as you did in writing that program, and as you did in responding to me, to break that down *line by line*. ;) I'd be interested in the lesson.


Sure.  First mental leap... don't think line-by-line.  Think a long stream of bytes.

  1 !/usr/bin/perl -i.orig
  2 
  3 undef $/;
  4 $_ = <>;
  5 
  6 s/\tmovl\t(\$[^,]*), +%eax\n\tmovl\t%eax, +(.*)/\tmovl\t$1, $2/g ;
  7 
  8 print "$_";


Line1:  Tells OS to use perl as the interpreter.  The -i flag indicates perl should overwrite files in place, maintaining a backup.  This is standard perl.

Line 3:  Undefined the End of Line sequence; undefining means Perl's STDIN operator <> will not break lines by their EOL char sequence.  Therefore, we will get a stream of bytes.

Line: 4:  Assign the default variable $_ to be the read bytes from the file. <> reads STDIN or each consecutive argv filename, and does it foreach and every file.  This is standard Perl.

Line 6: Matches the specified pattern (which is the specific movl instruction, followed by a newline followed by the next required pattern), and replacing those with just the second line with alterations required.  The ( ) parens capture and remember the matched pattern, so it can be used on the replacement side.  The 'g' flag at the end says do this substitution everywhere on a line (not just the first one).

Line 8: Prints out the line we've just modified.

That's it.  No magic, just standard Perl, as taught in intro Perl classes.

MrC

---

### Post by Mr. C. on 2007-03-06
> **pmasiar said:**
> Your solution might be shorter, but hardly anyone except hardcore perl hacker would call it elegant. Archetypical perl golf solution.

No offense, but this is silly.  I am by no means a "hardcore perl hacker"; there is nothing more complex in that code than what is taught in standard Perl courses.  Your lack of knowledge does not denigrate or diminish mine.

> **pmasiar said:**
> 
IMHO it is rather hard to develop (you cannot easy print parts of one-liner), maintain, non-obvious and chaotic - in sense that small changes in input can make dramatic changes in output Solution appreciated by old hackers, but definitely not intended for eyes of impressionable young beginners :-)

Untrue on all fronts.  Adding a diagnostic out is trivial.  What do you want printed out?  The Line numbers where changes are made?  Do you want the original pattern and the new pattern ?  Its trivial.

> **pmasiar said:**
> 
For me, "elagant" is defined not only and not mainly by legth of the solution, but most important it should be obvious and easy to explain. As short as it can be, but not shorter.


Again, "elagant" [sic] is using the tools as they are meant to be used, and the right tool for the job.  I just explained how easy the problem was in a previous post line by line.  Explanations of the tool and the code never accounts for one's lack of knowledge of the tool itself.  If you don't know the tool, of course this looks greek to you.  But anyone with a moderate understanding of Perl will know this. 

> 
IMHO, YMMV. I coded in Perl before, but i am recovering. :-)

Cute.  Learn as many tools as you can; you will be far more valuable, and find solutions come much more quickly.

MrC

---

### Post by Wybiral on 2007-03-06
Wow, it's always cool to see different solutions to the same problem. Mr.C, does yours also handle the pointer-to-pointer problem where this isn't allowed:

Right:
```

movl (%ebp), %eax
movl %eax, (%edx)

```

Wrong:
```

movl (%ebp), (%edx)

```

While it may be more optimized, unfortunately that isn't legal assembly (you can't move an address to an address, you can only move the value to a register then move the value of that register to an address).

BTW, Mr.C, I'm looking for more optimizations... If I find any more trends like this I'll post them. I do a lot of 3d graphic programming and CPU intensive stuff and I can't have all of these extra opcodes being executed (plus, they make the executables larger than they need to be).

Oh yeah... I like your solution. It's small, efficient... But I probably wouldn't call a one-line program that does this much elegant. But, who am I to say... If it works efficiently and you are able to manage it, then it's not that bad.

---

### Post by pmasiar on 2007-03-06
> **Mr. C. said:**
> No offense, but this is silly.  I am by no means a "hardcore perl hacker"; there is nothing more complex in that code than what is taught in standard Perl courses.  Your lack of knowledge does not denigrate or diminish mine.

In no way I wanted ever to diminish you. I admire your perl hacking skills.  For me, someone who can put all steps (thanks for step-by step explanation) together so they "click" and create that one-line regex, like you did, is experienced perl hacker.

> Untrue on all fronts.  Adding a diagnostic out is trivial.  What do you want printed out?  The Line numbers where changes are made?  Do you want the original pattern and the new pattern ?  Its trivial.

Ok. (1) How to print deleted lines? (2) How to process only every other pattern?

maybe Wybiral can suggest some variations which are more relevant to this problem.

> Again, "elegant" is using the tools as they are meant to be used, and the right tool for the job.  I just explained how easy the problem was in a previous post line by line.  Explanations of the tool and the code never accounts for one's lack of knowledge of the tool itself.  If you don't know the tool, of course this looks greek to you.  But anyone with a moderate understanding of Perl will know this. 

Again, I agree with you 100%. As you demonstrated so eloquently, Perl is excellent for one-line text file transformations, one-off scripts which are easier to write again than maintain.

I was commenting from POV of someone who uses Perl for 2 weeks twice a year, and for me it was far from obvious. I know enough Perl to follow your step-by-step explanation, but Perl has so many quirks I was never able to fit them all in my brain. Just too many different projects. Not all in Perl mind you.

> Cute.  Learn as many tools as you can; you will be far more valuable, and find solutions come much more quickly.

Your advice might not work for me: I am not trying to learn all tools I possibly can - my brains would explode I guess. Instead, I am trying to do just the opposite: I am trying to select subset of available tools, and become efficient enough using this subset, so I can solve problems I face fast enough. As I said, I am not leet hacker. Maybe my brains are not leet enough by your measure - but this is the only brains I have.

---

### Post by Mr. C. on 2007-03-06
Wybiral,

Give it a try.  It will only change movl lines that match "movl   $...", therefore, the answer is yes.

Please do post more optimizations.  We'll see how easily each of our programs can be modified to accommodate your needs.  For example, if you added a new requirement to change 

movl (%ebp), XYZ
movl XYZ, (%edx)

into:

movl (%ebp), XYZ

this would add the single line:

s/\tmovl\t\(%ebp\), +XYZ\n\tmovl\tXYZ, +%edx/\tmovl\t$1, $2/g ;

either before or after the existing pattern.  You can just stack them up.

Spend a little time learning RE's - they are fantastically powerful and will very useful tools.

> 
Oh yeah... I like your solution. It's small, efficient... But I probably wouldn't call a one-line program that does this much elegant. But, who am I to say... If it works efficiently and you are able to manage it, then it's not that bad.

Elegant:
	(of scientific, technical, or mathematical theories, solutions, etc.) gracefully concise and simple; admirably succinct.

MrC

---

### Post by Mr. C. on 2007-03-06
> **pmasiar said:**
> 
Ok. (1) How to print deleted lines? (2) How to process only every other pattern?


Let's see who can come up with the quickest (most elegant !) solution to your questions. I have them solved in my head already.

See my follow-up above as well.

MrC

---

### Post by pmasiar on 2007-03-06
> **Mr. C. said:**
> 
Elegant:
	(of scientific, technical, or mathematical theories, solutions, etc.) gracefully concise and simple; admirably succinct.

MrC

see also [cryptic](http://www.m-w.com/cgi-bin/dictionary?sourceid=Mozilla-search&va=cryptic): 
marked by an often perplexing brevity :-)

---

### Post by Wybiral on 2007-03-06
Some other optimizations that come to mind are very simple...

This:
```

	addl	$1, %eax

```
Should be replaced with:
```

	incl %eax

```

Likewise:
This:
```

	subl	$1, %eax

```
Should be replaced with:
```

	decl %eax

```

It may seem very obvious, but for some reason GCC does not always optimize these!!! (thats like an extra four bytes per occurrence)

This one will probably only show up with the %eax register, and it is NOT allowed for address pointers, so "x(%register)" must be ignored.

I'll see if I don't have any more, but this one and the first one are very common for GCC dumped assembly.

EDIT:

OK... this should make it a little more interesting.

"addl $x, %eax" is a five byte instruction.
"incl %eax" is only one byte.

So, if you're optimizing for size, if "x" is less than five, replacing that line with "incl %eax" * "x" will at least make every occurrence of that instruction between 1-4 bytes smaller, which accumulates when it occurs hundreds of times (such as in large projects) and it can make a big difference in hitting you goal in small projects (when that few bytes makes a big difference).

The only problem is that this is sortof iffy... I'm not sure if four "inc"s will be less operations than one "add", even though it will be smaller... I'll have to look that up. But, that doesn't matter if size is the goal, so maybe a commandline flag could be used...

Something like "-size" would mean that the program switches to size optimizing mode.

This not only applies to "inc" and "addl" but also to "dec" and "subl"

---

### Post by yaaarrrgg on 2007-03-06
> **Wybiral said:**
> 
It may seem very obvious, but for some reason GCC does not always optimize these!!! (thats like an extra four bytes per occurrence)


Oh, have you tested that these optimizations are actually faster?  

Size and speed are really two different optimizations.  Intel assembly is fairly confusing ... I could see longer byte sequences could actually be faster in some cases, with how they are cached and pipelined.  Many CISC sequences are probably emulated internally like RISC, so there might not be much savings in speed here either.   Just a thought... Otherwise, rather than manally patching these, you should patch the gcc compiler instead :)

---

### Post by Wybiral on 2007-03-06
> **yaaarrrgg said:**
> Oh, have you tested that these optimizations are actually faster?  

Size and speed are really two different optimizations.  Intel assembly is fairly confusing ... I could see longer byte sequences could actually be faster, with how they are cached and pipelined.  Many CISC sequences are probably emulated internally like RISC, so there might not be much savings in speed here either.   Just a thought... Otherwise, rather than manally patching these, you should patch the gcc compiler instead :)

lol, I actually just edited that into my post on the bottom.

---

### Post by Mr. C. on 2007-03-06
> **pmasiar said:**
> see also [cryptic](http://www.m-w.com/cgi-bin/dictionary?sourceid=Mozilla-search&va=cryptic): 
marked by an often perplexing brevity :-)

Swahili looks cryptic to you and me, but not to those who speak and write it.  Lesson?  Learn Swahili.

MrC

---

### Post by Mr. C. on 2007-03-06
This took less that one minute to add your new addl/subl -> incl/decl patterns.

#!/usr/bin/perl -i.orig

undef $/;
$_ = <>;

s/addl\t\$1, %eax\n/incl\t%eax\n/ ;
s/subl\t\$1, %eax\n/decl\t%eax\n/ ;
s/\tmovl\t(\$[^,]*), +%eax\n\tmovl\t%eax, +(.*)/\tmovl\t$1, $2/g ;

print "$_";

---

### Post by Wybiral on 2007-03-06
> **Mr. C. said:**
> This took less that one minute to add your new addl/subl -> incl/decl patterns.

#!/usr/bin/perl -i.orig

undef $/;
$_ = <>;

s/addl\t\$1, %eax\n/incl\t%eax\n/ ;
s/subl\t\$1, %eax\n/decl\t%eax\n/ ;
s/\tmovl\t(\$[^,]*), +%eax\n\tmovl\t%eax, +(.*)/\tmovl\t$1, $2/g ;

print "$_";

Awesome.

Does this only optimize the "$1" add/sub?
If it's possible, using the "anything less than 5 rule" would be even cooler.
Especially if you could control it with a command line flag.

```

addl $3, %eax"

```
 = 5 bytes

```

incl %eax
incl %eax
incl %eax

```
= 3 bytes

But as it's been mentioned... While it is smaller, it doesn't mean it's faster, so having it optional would be the best method.

---

### Post by Mr. C. on 2007-03-06
Yes, I only did $1.  If you want other values there, just define them, and the RE can be modifed.

Here's what the newest RE does.  I'll write it in English, uppercasing the things to note and expanding with spacing, and break it down, so you can see how trivial this is:

s/addl\t\$1, %eax\n/incl\t%eax\n/ ;

SUBSTITUTE the pattern inside the first / and /

which is

addl <TAB> <LITERAL $> 1,  <SPACE> %eax  <NEWLINE>

REPLACING with the pattern between the second and third / chars:

incl <TAB> %eax <NEWLINE>

pretty much comes out exactly how you described it.

To do your addl $3 replacement is just:

s/addl\t\$3, %eax\n/incl\t%eax\nincl\t%eax\nincl\t%eax\n/ ;

This could be parameterized, or optional via command line flags as well.  Let's see how others would implement that (eg. pass a command line switch and argument that indicates how much to unroll).

MrC

---

### Post by pmasiar on 2007-03-06
> **Mr. C. said:**
> Swahili looks cryptic to you and me, but not to those who speak and write it.  Lesson?  Learn Swahili.

MrC, you are smart guy, but for some reason you continue to pretend that you do not understand my POV, which is: 

Some solutions could be too much "concise and succinct" (== elegant?),  too brief to the point of being cryptic, and as such not suited to wide audience.

[APL](http://en.wikipedia.org/wiki/APL_%28programming_language%29) is even more "conscise" language than Perl, uses even more "line noise" characters as it's operators to pack even more expression power to even shorter programs. But it is in decline for a very long time. I wonder why?

Will you counter my example saying I should become expert in APL? to be able to - what? Surely for very small minority of the people it makes sense. For most people it does not. For some people (more than APL users) it makes sense to become expert in cryptic regex one-liners. For many people it does not make sense, and my POV is: there is nothing to be ashamed of.  [TIMTOWTDI](http://en.wikipedia.org/wiki/There_is_more_than_one_way_to_do_it) principle applied backwards :-) Perl regex magic is not always the best solution, even if it is more succint. For many people, more verbose solution is more adequate - if you can avoid verbosity of java of course! :-)

You just conceeded "my thing is bigger than yours" competition with some guy in some other thread. I guess you won this "mine is shorter than yours" :-) I conceede this one under condition I do not have to learn regex until I really, really need it.

 BTW I am looking for your solutions. You know your perl regex magic.

---

### Post by Mr. C. on 2007-03-06
I mean not to misunderstand you pmasiar.  I hear your points, and there are valid.

MrC

---

### Post by pmasiar on 2007-03-06
> **Mr. C. said:**
> I mean not to misunderstand you pmasiar.  I hear your points, and there are valid.

ahh thats good to know - but it was not obvious to me. I was almost afraid you will make to learn swahilli to better understand regex magic :-D

---

### Post by WW on 2007-03-06
There seem to be two issues being confounded in this discussion of 'concise vs. cryptic'.  One is the language, perl, and the other is the use of regular expressions.  Perl can do more than REs, and most any other popular language (Python, C, C++, Ruby, etc.) has RE functionality available (either built in, or in a readily available library).  My earlier post shows a Python example.

If a young programmer asked me "Should I learn perl?", I would answer, "You can live without it."  If that same young programmer asked me "Should I learn about regular expressions?", I would answer "Yes, of course."  Regular expressions are a powerful tool; it would be a shame to not have it in your toolbox.

---

### Post by phossal on 2007-03-06
I'm quite familiar and comfortable with every component - especially RE's - except line #3, I have never seen that before. I can't recall it being made obvious in either *Learning* or *Programming* Perl, which are the only two references I have available. It's *super* valuable though. That's a gem - one of the few I've picked up in six months of being a forum member. I consider myself lucky. Thanks.

---

### Post by WW on 2007-03-06
I had a similar reaction: "*undef $/;*? What does *that* do?"  Off to *Programming Perl*, check the index, flip back to page 113, and there it is: "... If $/ is undefined, no record separator is matched, and <FILEHANDLE> will read everything to the end of the current file."  In hindsight, it makes sense. Undefine the record separator, so  the records aren't separated.

---

### Post by Mr. C. on 2007-03-06
> **phossal said:**
> I'm quite familiar and comfortable with every component - especially RE's - except line #3, I have never seen that before. I can't recall it being made obvious in either *Learning* or *Programming* Perl, which are the only two references I have available. It's *super* valuable though. That's a gem - one of the few I've picked up in six months of being a forum member. I consider myself lucky. Thanks.

Happy to oblige! :-)

This is one of those areas, where I'm presuming I have the advantage, just due to having seen those tools come to fruition over the years.  Its where knowing the tools, and knowing that such functionality probably exists in newer, more advanced tools, works towards one's advantage.

I certainly didn't recall that variable name $/ (and it has a more readable form, $INPUT_RECORD_SEPARATOR, or $RS [same as awk's $RS]), but I *knew* perl, like many other line-oriented RE-based filter tools, would allow defining the End of Line sequence.

Page 108 of the Learning Perl book discusses the /s flag, which discusses matching embedded newlines, and then page 109 indicates there are more option in man perlop.  While not directly pointed out, this is a clue.  Few people sit down and *read* the man pages and documentation. 

Read the man page, you'll see it right there in an example.  The tool that I had was not $/ ... rather, it was knowing it must exist because perl is very much like awk, sed, ed, and other sophisticated RE programs that implement PCREs.

One thing we can all agree on, *nothing* in the massive Programing Perl tome is obvious!

Cheers,
MrC

---

### Post by phossal on 2007-03-06
> **WW said:**
> I had a similar reaction: "*undef $/;*? What does *that* do?"  Off to *Programming Perl*, check the index, flip back to page 113, and there it is: "... If $/ is undefined, no record separator is matched, and <FILEHANDLE> will read everything to the end of the current file."  In hindsight, it makes sense. Undefine the record separator, so  the records aren't separated.

Page 113. I can't wait to check that out. Which paragraph?

> **Mr. C. said:**
> Happy to oblige! :-) This is one of those areas, where ***I'm presuming I have the advantage***, just due to having seen those tools come to fruition over the years.

Certainly.

---

### Post by xtacocorex on 2007-03-06
Not to hijack the thread, but Wybiral, I decided to generate an assembly version of a C++ code I had and couldn't find anything similar to what you asked to be optimized. 

I did make it only 23% through the 10954 line file, so I could have missed something.

The only time I find $ characters is usually in a subl, movb, or addl line.

I've never bothered looking at assembly before, but I saw this a while back and got intrigued.  Will all programs have code similar to your example?  What causes the assembly to do that?

EDIT:
I did run phossal's code and it said it changed lines, but running vimdiff, it didn't change anything.

---

### Post by Wybiral on 2007-03-06
> **xtacocorex said:**
> Not to hijack the thread, but Wybiral, I decided to generate an assembly version of a C++ code I had and couldn't find anything similar to what you asked to be optimized. 

I did make it only 23% through the 10954 line file, so I could have missed something.

The only time I find $ characters is usually in a subl, movb, or addl line.

I've never bothered looking at assembly before, but I saw this a while back and got intrigued.  Will all programs have code similar to your example?  What causes the assembly to do that?

EDIT:
I did run phossal's code and it said it changed lines, but running vimdiff, it didn't change anything.

It happens a lot when you use floating point numbers. ESPECIALLY when you use constant values in place.

I find it a lot in 3d applications. Try compiling an OpenGL program in C or C++ and you will probable see it.

It just depends what types of data you are using, I think floats and long int's are the main cause.

---

### Post by Wybiral on 2007-03-06
Try this:
```

#include <iostream>

float addf(float a, float b)
{
   return a + b;
}

int main()
{
   std::cout << addf(100, 100);
}

```

For me it's on line 100:

```

	movl	$0x42c80000, %eax
	movl	%eax, 4(%esp)
	movl	$0x42c80000, %eax
	movl	%eax, (%esp)
	call	_Z4addfff

```

---

### Post by Mr. C. on 2007-03-07
> **phossal said:**
> Page 113. I can't wait to check that out. Which paragraph?

Different revisions are likely to have different page numbers.  Check the index under "records".

MrC

---

### Post by xtacocorex on 2007-03-07
> **Wybiral said:**
> Try this:
```

#include <iostream>

float addf(float a, float b)
{
   return a + b;
}

int main()
{
   std::cout << addf(100, 100);
}

```For me it's on line 100:

```

    movl    $0x42c80000, %eax
    movl    %eax, 4(%esp)
    movl    $0x42c80000, %eax
    movl    %eax, (%esp)
    call    _Z4addfff

```

Well I tested that code and I'm beginning to think that my dual core has a slightly different way it does assembly, if I had more time this morning before work, I'd test it out on my Ubuntu VM, but g++ should be very similar for OS X.
I ended up with nothing like what you had, maybe I'm compiling it wrong, but I used:
```
g++ -S test1.cpp
```

As for the program I tested last night, it used a lot of non-constant doubles and did a lot of math instead of graphics.

I'm going to keep investigating this because it's interesting and I don't want to pack up my apartment before I move into my new house.

---

### Post by Mr. C. on 2007-03-07
> **xtacocorex said:**
> ... I'm beginning to think that my dual core has a slightly different way it does assembly ...

The assembler doesn't care if the target platform is dual core.  This is the concern of the programmer and some optimizers.

---

### Post by Wybiral on 2007-03-07
> **xtacocorex said:**
> I'm going to keep investigating this because it's interesting and I don't want to pack up my apartment before I move into my new house.

Yeah, that wasn't a graphical program, just an example of what I mean. For me, it shows up on line 100 of the assembly dumped from that code.

---

### Post by Mr. C. on 2007-03-07
Ok, so we've had no takers of the earlier challenge to modify the "elegant" perl script I wrote to help our learned friend Wybiral in his quest to squeak out wasted cycles.

The modification he asked, was to allow an unrolling of a line of assembler code into the appropriate number of equivalent, but faster, lines of code.  The challenge was to allow for arbitrary constants in the addl/subl instructions.

Yesterday, I had sent the solution to Wybiral.  Here is that solution:

```

     1  #!/usr/bin/perl -i.orig
     2
     3  my $unrollrange = 5;
     4
     5  undef $/;
     6  $_ = <>;
     7
     8  s/\taddl\t\$([1-$unrollrange]), %eax\n/"\tincl\t%eax\n" x $1/ge ;
     9  s/\tsubl\t\$([1-$unrollrange]), %eax\n/"\tdecl\t%eax\n" x $1/ge ;
    10
    11  s/\tmovl\t(\$[^,]*), +%eax\n\tmovl\t%eax, +(.*)/\tmovl\t$1, $2/g ;
    12
    13  print "$_";
```

Thre  additional lines of code meet the requirements nicely.  Line 3 is obvious.  But lines 8 and 9 may require some perl review to understand.  Let's see who can explain whats going on.

I'll leave passing in the unrollrange parameter via command line to others.

Cheers,
MrC

---

### Post by phossal on 2007-03-07
> **xtacocorex said:**
> EDIT:
I did run phossal's code and it said it changed lines, but running vimdiff, it didn't change anything.

lol C'mon, *vimdiff*? That horrible mess I wrote *does* work. But why would you use that when there is a one-line version available? Perhaps you're not quite qualified to be optimizing any code. ;)

---

### Post by phossal on 2007-03-07
> **Mr. C. said:**
> Ok, so we've had no takers of the earlier challenge to modify the "elegant" perl script I wrote...

Couldn't this be done much *better* in python? No one uses perl anymore.

---

### Post by Mr. C. on 2007-03-07
> **phossal said:**
> Couldn't this be done much *better* in python? No one uses perl anymore.

Show proof of both points.

---

### Post by phossal on 2007-03-07
> **Mr. C. said:**
> Show proof of both points.
Nah.

---

### Post by xtacocorex on 2007-03-07
> **phossal said:**
> lol C'mon, *vimdiff*? That horrible mess I wrote *does* work. But why would you use that when there is a one-line version available? Perhaps you're not quite qualified to be optimizing any code. ;)
I used the tool I had access to when I needed it, wasn't sure if my default install of OS X had diff or something similar installed. 

You do bring up a good point, why am I wanting to optimize code.  Maybe I won't mess with it, since it's not that important to me. 

Maybe one day I'll be back on this optimization kick, otherwise it's back to numerical methods.

---

### Post by phossal on 2007-03-07
> **xtacocorex said:**
> I used the tool I had access to when I needed it, wasn't sure if my default install of OS X had diff or something similar installed. You do bring up a good point, why am I wanting to optimize code.  Maybe I won't mess with it, since it's not that important to me. Maybe one day I'll be back on this optimization kick, otherwise it's back to numerical methods.

Oh, I wasn't really trying to make any point. I just wanted to respond to your comment that my code didn't work. If you're having fun, you should probably keep at it.

---

### Post by pmasiar on 2007-03-08
> **phossal said:**
> Couldn't this be done much *better* in python? No one uses perl anymore.

> **Mr. C. said:**
> Show proof of both points.

re (1): just part of slurping whole input file into single string and making backup. Slurping might not be a problem for ASM source files, but still needs little warning light in back of my mind: don't use it on 1 GB file. 

```

for fileName in fileNames:
    os.rename(fileName, fileName+'.orig')
    fileInput = open(fileName+'.orig')
    fulltext = ''.join(fileInput.readlines())
    fileInput.close()
    fileOutput = open(fileInput, 'w')

```

It is longer than Perl - but still simpler than java :-)

Nice part is, I can write this code with *no* RTFM, it *just works* and is totally transparrent to any reader. I needed fileInput only to be able to close the file, new Python 2.6 has new 'with' keyword which will close it for me. 

re (2): MrC, you know that it was rhetorical answer :-) Possibly not 100% true today, but value coming closer to true over (long) time. Between dynamically typed languages, it is hard to deny that Perl is in decline - Perl 6 is not coming anytime soon, and when (and if) it will, it might be too little too late. 

MrC's solution was prime example how non-obvious is to be Perl expert: you need to know obscure tricks. Nice, conscise (and possibly elegant), but obscure for anyone expect devouted masters. Not for occasional visitors.

I prefer Python, but will take Perl over Java any day :-)

---

### Post by phossal on 2007-03-08
> **pmasiar said:**
> I prefer Python, but will take Perl over Java any day :-)
You're entitled to your opinion, and I respect yours. You received many negative comments for being a python sales person, but it seems as though you've improved the way you communicate. I enjoy it much more, and am much more likely to consider your opinion in the future. It's difficult to make such changes, and I respect your effort. 

Regards.

---

### Post by Mr. C. on 2007-03-08
These arguments about This is better than That really suit no purpose, solve no problem, and ultimately only creates a My Way's Better or More Correct Than Your Way paradigm.  As as suggested earlier, lets leave these gross generalizations to politicians and children.  They have no place in a Computer SCIENCE.

Solve problems!
MrC

---

### Post by phossal on 2007-03-08
> **Mr. C. said:**
> These arguments about This is better than That really suit no purpose, solve no problem, and ultimately only creates a My Way's Better or More Correct Than Your Way paradigm.  As as suggested earlier, lets leave these gross generalizations to politicians and children.  They have no place in a Computer SCIENCE.

Solve problems!
MrC

I dislike the My Way's Better or More Correct Than Your Way paradigm. However, I *do* prefer the "My Way's More *Elegant* thus Better Than Your Way" paradigm. Afterall, this thread would've been dead two weeks ago when I solved the problem, but thankfully it lives on due to the elegance of your solution and your message.

---

