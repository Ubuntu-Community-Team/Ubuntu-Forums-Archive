---
title: "Arrays in awk, simple issue?"
date: 2009-10-07
forum: Programming Talk
---

### Post by Snowmirage on 2009-10-07
ISSUE #1

inside my awk script I have a variable that contains

"Lastname, Firstname M"  (minus the quotes)  I'll call it VAR1

in my awk script I do..

t=" ";
split($VAR1,ARRAY,t);

print length(ARRAY[1]); #This prints say 6 when run
n=length(ARRAY[1]); #Should assign the 6 from above to n
print "n = " $n; # n doesn't contain anything when the script is run

Been searching and fumbling around for hours here and Im at a loss





ISSUE #2

The above is my attempted work around for this issue...

I have a file format similar to this, with multiple lines

"Lastname, Firstname M" 00-1111 x123 Deptname

I need to parse out Lastname and Firstname and M and so forth

All values are tab seperated (except those in the quotes Lname Fname ect)

I tried using an awk script as follows and passing it the input file

BEGIN { FS="\t" }
{
#This should take the $1 (which should be "Lastname, Firstname M") and substitute the quotes with nothing

namesegment=sub("\"","",$1);
namesegment2=sub("\"","",namesegment);

#printing namesegment2 at this point returns Lastname, Firstname M with out the quotes as intended

#This should parse namesegment2 based on a space delim
t=" ";
split($namesegment2,ARRAY,t);
print ARRAY[1]; #This prints Lastname,   which is fine
lastname=ARRAY[1];
print $lastname; # HERE IS THE ISSUE, this spits out the entire line originally read by awk (what should be $0) something to the effect of...    "Lastname, Firstname M" 00-1111 x123 Deptname  if i recall the quotes where gone, but it shouldnt have the other data Deptname xnumber ect

}
END{ }


I cant begin to explain how thats possible....


Any guidance / thoughts would be very helpful and appreciated

---

### Post by ghostdog74 on 2009-10-07
if you have same format, use FS to be " instead of \t. then second field will be your last name,firstname M. For the third field, you can do a split on \t .

---

### Post by stoneguy on 2009-10-07
You're on the right track. AWK was really neat in its day. PERL and Python are a lot more powerful though, but AWK has what it takes for something this simple.

Be careful that the character following the comma is NEVER a tab. Otherwise you'll get 5 elements instead of 4. split returns the number of elements, so you can sanity check your input records, and cat the 1st 2 elements together with an intervening blank if your count is 5. Might not be right, but it's a good guess.

If you take the whole string and split initially on tab, then take the 1st element and gsub out the doublequotes, you should get what you want.

---

### Post by Snowmirage on 2009-10-08
After another 4hrs of troubleshooting I finnaly found my error.  This is what I get for having not done any scripting in 6 months...

In awk when you reference variables you DO NOT use $VARNAME

Example

VAR1="String of stuff";
print VAR1

^ CORRECT!!!!

print $VAR1

^ WRONG!!

It seems that if you try to do print $VAR1 or $anything for that matter it treats your "$anything" as it would $0 which is the entire line that was fed to awk....  Thus my crazy output.

Hope this helps someone someday.

---

