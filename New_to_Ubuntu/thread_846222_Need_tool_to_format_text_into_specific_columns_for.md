---
title: "Need tool to format text into specific columns for Mainframe"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by cwmoser on 2008-07-01
Need tool to format text into specific columns for Mainframe

I am looking for a tool that will format data into a column specific format like old time Mainframe programming.

Is there a Linux tool or utility you can recommend for this?

I can format the input data in comma delimited or tab delimited format and would like to get the Linux tool or utility to place the data in specified columns.

Thanks

Carl

---

### Post by HalPomeranz on 2008-07-01
I don't know of a specific "off the shelf" tool that does this in Unix (because column-oriented data is not the "Unix Way").  But it would be easy enough to write a script in bash, Perl, Python, etc to format the data any way you want to.  If you don't know how to program, then describe what the input format looks like and what you want it to be transformed into I'm sure I or somebody else could whip up some sample code.

---

### Post by cwmoser on 2008-07-01
Thanks.  I can write a program to place each data element in a specified record column.  Instead of writing a program, I was wondering if there was a tool to do it.  I work for a bank and they still have a lot of mainframes and their programmers want me to input data fielded.  Reminds me of my old Cobol days.  

How about a utility in Windows that will take data and put in specified columns?  Something like an editor where you can specify tab stops.

Thanks

Carl

---

### Post by HalPomeranz on 2008-07-02
> **cwmoser said:**
> 
How about a utility in Windows that will take data and put in specified columns?  Something like an editor where you can specify tab stops.


Dunno.  Can Excel output fixed-width data?  Could you do it with Open Office?

---

### Post by ghostdog74 on 2008-07-02
how does your data look like and how do you want it to look like?

---

### Post by cwmoser on 2008-07-02
> **ghostdog74 said:**
> how does your data look like and how do you want it to look like?


The data is currently in ASCII format consisting of text and numbers and each line uses commas to separate each field.  Each line is terminated with CRLF.  

The output I want is lines and each line is exactly 1,000 characters long terminated with CRLF and uses spaces to pad to make up the exact 1,000 character width.  Within each line, are designated positions for data - for example column 12 contains the first name, column 44 contains the last name, column 250 contains birth date, etc.  Old time "Cobol-like" programming but requirements like this still exists.

I can envision that there is some tool that would take an input like a comma separated file (like say Excel or Open Office Spreadsheet) and allow for one to grab a vertical line and slide the data to an appropriate column.  Then, a Save As to save as a text file padded with spaces.  I can't figure out how to do this in Excel or Open Office Spreadsheet.

Any ideas before I have to go out and write a program?  Is there a market for a freeware/shareware utility that does this?

Carl

---

### Post by ghostdog74 on 2008-07-02
Its sad to say that what you want can be done by simple script/programming. no third party tools needed. If you want, post a sample of input, a sample of output here.

---

### Post by cwmoser on 2008-07-02
> **ghostdog74 said:**
> Its sad to say that what you want can be done by simple script/programming. no third party tools needed. If you want, post a sample of input, a sample of output here.

If I were to program it, I would do it in VB.NET as I know it better than any other programming technique.  How would you do it using a script under Linux?

If I can see a pattern, I think I can figure the rest out.  Say we start with a CSV file like this:
Firstname, Lastname, SSN, Addr1, Addr2, City, State, Zip

and we want it to be formatted like this:

column
1          Lastname
20         Firstname
35         Addr1
50         Addr2
65         City
80         State
82         Zip
100        SSN

and the output is to have fixed width records 200 characters in length padded out with spaces.

What technique would you use to create a script to do this?

Thanks for the help,

Carl

---

### Post by HalPomeranz on 2008-07-02
In awk it would be something like:

```

awk -F, '{ printf "%-19s%-15s%-15s%-15s%-15s%-2s%-9s%-100s\n", $1, $2, $3, $4, $5, $6, $7, $8 }'

```

---

### Post by cwmoser on 2008-07-02
> **HalPomeranz said:**
> In awk it would be something like:

```

awk -F, '{ printf "%-19s%-15s%-15s%-15s%-15s%-2s%-9s%-100s\n", $1, $2, $3, $4, $5, $6, $7, $8 }'

```

Now that is interesting.  When I man awk, I learned that the -F, means that the field separator is a comma.  I assume this works by piping the stdin?

 
Thanks

Carl

---

### Post by ghostdog74 on 2008-07-02
what do mean by piping the stdin?
-F is an option passed to awk. inside awk code (C code), most probably some getopt function is doing the job of parsing options.

---

### Post by HalPomeranz on 2008-07-03
> **cwmoser said:**
> I assume this works by piping the stdin?

You could do it that way.  Or you could specify the input file on the command-line like so:

```

awk -F, '{ printf "%-19s%-15s%-15s%-15s%-15s%-2s%-9s%-100s\n", $1, $2, $3, $4, $5, $6, $7, $8 }' inputfile

```

Sorry, I should have written it that way in the first place.

---

### Post by cwmoser on 2008-07-09
awk was a good heads up.  Looks like it will do exactly what I need.  Thanks.

One more question -- assume I have a 7 to 8 digit number and I wanted to split it into two values and place them in separate columns.  Specifically, I need the right-most 6 digits to be say $1 and the remaining digits to be $2.  How can you use awk to peel off these parts?  In VB.NET, I would use the MID or RIGHT statement to do this.  How about the Linux cut command???

Thanks for the help

Carl

---

### Post by HalPomeranz on 2008-07-09
awk does have a substr() operator that you can use for this.  

I'm assuming the field you want to split is one of the comma-separated fields in your input file.  Let's assume you want to split the zip+4 code in field #7 for purposes of this example:

```

awk -F, '{ zip = substr($7, 1, 5); plusfour = substr($7, 6);
           printf "%-19s%-15s%-15s%-15s%-15s%-2s%-5s+%-4s%-100s\n", $1, $2, $3, $4, $5, $6, zip, plusfour, $8 }' inputfile

```

That would give you output where the second-to-last column would be "<zip>+<plusfour>".

---

### Post by cwmoser on 2008-07-10
You have been a tremendous help - I have a new perception of awk.

How would you handle the situation when you have a variable length field of numbers such as:

3778899
4667788
5009989
9225566
10664499
20112233
55998877
63887766

where the right most 6 digits are an account number and the left most one or two digits are say a branch number.

I can see where the substr can get the account number, but how would you extract the branch number when it varies in length?

Thanks

Carl

---

### Post by HalPomeranz on 2008-07-10
I should have been more explicit in my previous example.  The neat thing about awk's substr() operator is that if you leave off the third parameter (the length of the substring you want to chop out), then the substr() routine will just grab everything from your offset onwards.  So "substr($0, 1, 6)" would pull the first six characters out of $0 (which is the entire line as read in by awk btw) and "substr($0, 7)" would take everything from character 7 onwards.

awk is a pretty powerful programming language, and good for "quick and dirty" solutions to data (re-)formatting problems.  But at some point the problems get complex enough that I tend to switch over to using a different scripting language (I prefer Perl, others like Python).  I find that complex programs in Perl are easier to maintain than complex programs in awk.  Your mileage, as always, may vary.

---

### Post by ghostdog74 on 2008-07-10
> **HalPomeranz said:**
> 
awk is a pretty powerful programming language, and good for "quick and dirty" solutions to data (re-)formatting problems.
plus lots more

---

### Post by ghostdog74 on 2008-07-10
> **cwmoser said:**
> You have been a tremendous help - I have a new perception of awk.

How would you handle the situation when you have a variable length field of numbers such as:

3778899
4667788
5009989
9225566
10664499
20112233
55998877
63887766

where the right most 6 digits are an account number and the left most one or two digits are say a branch number.

I can see where the substr can get the account number, but how would you extract the branch number when it varies in length?

Thanks

Carl

```

awk 'BEGIN{FS=""}
{ 
    for(i=1;i<=NF-6;i++) { 
      printf $(i)
    }
      print ""  
}' file 

```

---

### Post by cwmoser on 2008-07-10
> **cwmoser said:**
> You have been a tremendous help - I have a new perception of awk.

How would you handle the situation when you have a variable length field of numbers such as:

3778899
4667788
5009989
9225566
10664499
20112233
55998877
63887766

where the right most 6 digits are an account number and the left most one or two digits are say a branch number.

I can see where the substr can get the account number, but how would you extract the branch number when it varies in length?

Thanks

Carl


Assuming if and strlen are legal with awk, could I do this? 
Something like:
[COLOR="Blue"]
[B]awk -F, '{  
if (strlen($7) <= 7)  
{acct = substr($7, 1, 6);  branch = substr($7, 0, 1); } 
else 
{ acct = substr($7, 2, 6);  branch = substr($7, 0, 2) }
printf "%-10s%-10s\n", acct, branch}' inputfile
[/B]
[/COLOR]
Would that work?

Carl

---

### Post by ghostdog74 on 2008-07-10
> **cwmoser said:**
> Assuming if and strlen are legal with awk, could I do this? 
Something like:

awk -F, '{  
if (strlen($7) <= 7)  
{acct = substr($7, 1, 6);  branch = substr($7, 0, 1); } 
else 
{ acct = substr($7, 2, 6);  branch = substr($7, 0, 2) }
printf "%-10s%-10s\n", acct, branch}' inputfile


Would that work?

Carl

it doesn't take you much time to just run it through your terminal to find out. checking for length of string is length(), not strlen()
Please do read up the GNU awk manual to get some basic understanding of awk

---

### Post by HalPomeranz on 2008-07-10
> **cwmoser said:**
> Assuming if and strlen are legal with awk, could I do this? 
Something like:
[COLOR="Blue"]
[B]awk -F, '{  
if (strlen($7) <= 7)  
{acct = substr($7, 1, 6);  branch = substr($7, 0, 1); } 
else 
{ acct = substr($7, 2, 6);  branch = substr($7, 0, 2) }
printf "%-10s%-10s\n", acct, branch}' inputfile
[/B]
[/COLOR]
Would that work?


It's length() in awk, not strlen(), but yes that's the right idea.  

Sorry, I misunderstood where the variable length field was in your input-- I thought it was at the end not the beginning.  Doh!

---

### Post by cwmoser on 2008-07-10
I figured out the answer to my last question -- see below:

awk -F, '{
if (length($1) <= 7)
{acct = substr($1, 2, 6); branch = substr($1, 1, 1); }
else
{ acct = substr($1, 3, 6); branch = substr($1, 1, 2) }
printf "%-10s%-10s\n", acct, branch}'  ./Suzuki.csv  > ./Suzuki2.out



One thing I learned is that substr is 1-based rather than 0-based.  I had assumed that it was more conventional in C-language that indexes were 0-based and wondered why not here too.


Thanks to you guys for introducing me to AWK and getting me started using this.  I'm the only one on staff that uses Linux and under Windows we don't have tools like this.  Converting data for input to our partners who require it to be in "mainframe" column specific format should be much easier now.

Carl

---

### Post by ghostdog74 on 2008-07-10
> **cwmoser said:**
> I figured out the answer to my last question -- see below:

awk -F, '{
if (length($1) <= 7)
{acct = substr($1, 2, 6); branch = substr($1, 1, 1); }
else
{ acct = substr($1, 3, 6); branch = substr($1, 1, 2) }
printf "%-10s%-10s\n", acct, branch}'  ./Suzuki.csv  > ./Suzuki2.out



awk's construct allows you to have an "implicit" if/else . see this
```

awk -F, 'length($1) <= 7{ acct = substr($1, 2, 6);  branch = substr($1, 1, 1)}
length($1) > 7 {  acct = substr($1, 3, 6); branch = substr($1, 1, 2) }
printf "%-10s%-10s\n", acct, branch}'  ./Suzuki.csv  > ./Suzuki2.out

```
therefore, sometimes there's no need to use if/else.

---

### Post by cwmoser on 2008-07-18
Something unusual happens with I use the statement:
{MODEL = $27;}

Seems that AWK looses track of the field when it executes.
It
Perhaps MODEL = $27; is not a valid statement?

Any insight?

Below is the entire awk statement I was using this with:

awk -F, '{
if (length($2) <= 7)
{acct = substr($2, 2, 6); branch = substr($2, 1, 1); }
else
{ acct = substr($2, 3, 6); branch = substr($2, 1, 2) }
if (substr($27, 1, 7) == "SUZUKI ")
{MODEL = substr($27, 8, 10);}
else
{MODEL = $27;}
printf "%-20s%-2s%-20s%-16s%-30s%-30s%-30s%-20s%-2s%-5s%-4s%-9s%-20s%-3s%15s%15s%-20s%-3s%-6s%-5s%-4s%-10s%-25s%-25s\n", 
acct, branch, $5, $4, $6, " ", " ",$7, $8, $9, $10, $23, $20, "   ", $24, $13, $12, "   ", $22, $15, $26, $1, MODEL, $18 }'  ./lots_07102008.csv  > ./Suzuki2.txt

---

### Post by ghostdog74 on 2008-07-18
put your code in code tags. you could have debugged your script and see if there's anything for field 27. what does this say?
```

awk '{print $27}' file

```

---

### Post by cwmoser on 2008-07-22
I'm still new to awk but I think there might be something quirky with a statement like:  MODEL = $27;

I played with this line of code for some time and modified the input file so that it would not get executed so I could go ahead and get the job done.

Sometimes walking away for a while makes an unsolvable issue become obvious.

Still, is the statement MODEL = $27; a legal assignment operation for awk language?

Carl



> **cwmoser said:**
> Something unusual happens with I use the statement:
{MODEL = $27;}

Seems that AWK looses track of the field when it executes.
It
Perhaps MODEL = $27; is not a valid statement?

Any insight?

Below is the entire awk statement I was using this with:

awk -F, '{
if (length($2) <= 7)
{acct = substr($2, 2, 6); branch = substr($2, 1, 1); }
else
{ acct = substr($2, 3, 6); branch = substr($2, 1, 2) }
if (substr($27, 1, 7) == "SUZUKI ")
{MODEL = substr($27, 8, 10);}
else
{MODEL = $27;}
printf "%-20s%-2s%-20s%-16s%-30s%-30s%-30s%-20s%-2s%-5s%-4s%-9s%-20s%-3s%15s%15s%-20s%-3s%-6s%-5s%-4s%-10s%-25s%-25s\n", 
acct, branch, $5, $4, $6, " ", " ",$7, $8, $9, $10, $23, $20, "   ", $24, $13, $12, "   ", $22, $15, $26, $1, MODEL, $18 }'  ./lots_07102008.csv  > ./Suzuki2.txt

---

### Post by cwmoser on 2008-07-22
I'm still new to awk but I think there might be something quirky with a statement like:  MODEL = $27;

I played with this line of code for some time and modified the input file so that it would not get executed so I could go ahead and get the job done.

Sometimes walking away for a while makes an unsolvable issue become obvious.

Still, is the statement MODEL = $27; a legal assignment operation for awk language?

Carl



> **cwmoser said:**
> Something unusual happens with I use the statement:
{MODEL = $27;}

Seems that AWK looses track of the field when it executes.
It
Perhaps MODEL = $27; is not a valid statement?

Any insight?

Below is the entire awk statement I was using this with:

awk -F, '{
if (length($2) <= 7)
{acct = substr($2, 2, 6); branch = substr($2, 1, 1); }
else
{ acct = substr($2, 3, 6); branch = substr($2, 1, 2) }
if (substr($27, 1, 7) == "SUZUKI ")
{MODEL = substr($27, 8, 10);}
else
{MODEL = $27;}
printf "%-20s%-2s%-20s%-16s%-30s%-30s%-30s%-20s%-2s%-5s%-4s%-9s%-20s%-3s%15s%15s%-20s%-3s%-6s%-5s%-4s%-10s%-25s%-25s\n", 
acct, branch, $5, $4, $6, " ", " ",$7, $8, $9, $10, $23, $20, "   ", $24, $13, $12, "   ", $22, $15, $26, $1, MODEL, $18 }'  ./lots_07102008.csv  > ./Suzuki2.txt

---

### Post by ghostdog74 on 2008-07-22
what errors are you encountering?

---

