---
title: "Regex SED Dilemma"
date: 2010-11-01
forum: Programming Talk
---

### Post by mistypotato on 2010-11-01
Hi,
Been trying to get this SED line to work and I'm getting nowhere.

I'm trying to replace all instances of text between two pound signs ## in a text file where the text begins with **[COLOR="Blue"]<cfqueryparam[/COLOR]** and ends with **[COLOR="Blue"]">[/COLOR]**

I'm using a colon : for my delimiter

The file in which to search is SendPassword.cfm

Here is one of the attempts that doesnt work... (this one says  "cfqueryparam*&#8221;: No such file or directory"....which baffles the heck out of me since the sed parameter in that position has nothing to do with a file or directory??

**[COLOR="DarkGreen"]sed s:#[^#]*#:<cfqueryparam*&#8221;>: <cfqueryparam cfsqltype=&#8221;CF_SQL_VARCHAR&#8221; maxlength=&#8221;50&#8243; value=&#8221;#\1#&#8221;> SendPassword2.cfm[/COLOR]**

Any of you SED and reges gurus out there ? :)

---

### Post by luvshines on 2010-11-01
Should not it be something like:
```

sed s:<search-for>:<replace-with>:<additional commands/scope> filename

```

Where for you case:
1. <search-for> is #<cfqueryparam.*">#
2. <replace-with> is <cfqueryparam cfsqltype=&#8221;CF_SQL_VARCHAR&#8221; maxlength=&#8221;50&#8243; value=&#8221;#\\1#&#8221;>

Complete command will look something like:
```

sed 's:#<cfqueryparam.*">#:#<cfqueryparam cfsqltype=&#8221;CF_SQL_VARCHAR&#8221; maxlength=&#8221;50&#8243; value=&#8221;#\\1#&#8221;>#:g' SendPassword2.cfm

```

Also, \1 has special meaning in sed. You want to put \1 as it is or use the first matched pattern ?

---

### Post by mistypotato on 2010-11-01
luvshines...thx for your help :KS

Your string resulted in this.......

sed: -e expression #1, char 106: unterminated `s' command

---

### Post by luvshines on 2010-11-01
> **mistypotato said:**
> luvshines...thx for your help :KS

Your string resulted in this.......

sed: -e expression #1, char 106: unterminated `s' command

Oh! That was due to an 'enter' which was unintentionally pressed, while writing in CODE :)
I have edited the earlier post now

---

### Post by mistypotato on 2010-11-01
It might help to see the actual context of the target

**This is the original text....**

<CFQUERY datasource="mydata" Name="MyQuery">
Select * from customers where email='#SendEmail#' 
</cfquery>

**but needs to be.....**

<CFQUERY datasource="mydata" Name="MyQuery">
**Select * from customers where email=[COLOR="MediumTurquoise"]<cfqueryparam[/COLOR] [COLOR="RoyalBlue"]value[/COLOR]='#SendEmail#' [COLOR="Magenta"][COLOR="MediumTurquoise"]cfsqltype[/COLOR][/COLOR]="[COLOR="Magenta"]cf_sql_varchar">[/COLOR]**
</cfquery>

**So I was hoping that this line.....**

sed -e 's:#[^#]*#:<cfquery*&#8221;>: <cfqueryparam cfsqltype=&#8221;cfF_sql_varchar&#8221; maxlength=&#8221;50&#8243; value=&#8221;#\1#&#8221;>' SendPassword2.cfm

**Would do that.....but I get this error.....**

sed: -e expression #1, char 22: unknown option to `s'


and the file never updates...
I'm working on this between posts :-)

---

### Post by luvshines on 2010-11-01
This one works somewhat similar to what you have mentioned:
```

sed "s:'#\(.*\)#':<cfqueryparam value='#\1#'cfsqltype="cf_sql_varchar">:g" SendPassword2.cfm

```

See if this is what you need

---

### Post by mistypotato on 2010-11-01
wow...that one actually DID something :KS:KS:KS:KS:KS

You apparently are quite knowledgeable with sed and regex :P


Is there a way to tell it to ONLY make changes in lines with the word Select at the beginning?  (select could be upper case, lower case or mixed case).

How did you learn these things?  Study or trial and error or both?

---

### Post by Vox754 on 2010-11-01
> **mistypotato said:**
> It might help to see the actual context of the target

**This is the original text....**

Heh, whenever working with sed, awk or regular expression it's always helpful if you post what you want before and after the transformation.
```

# before sed
Some line: original

# after sed
Same line: changed

```
What I mean is, you should have posted that in the first post of the thread. Also, use "code" tags, don't use colors.

To learn sed and regular expressions, you need to read the manuals and actually practice this stuff.

I suggest specially the Perl manuals, in the package "perl-doc". Read the beginning of "man perl", which lists the specific manual pages that deal with regexps: "perlrequick", "perlretut", "perlfaq6", etc. Although those manuals are for Perl, the basics apply to all programs which use regexps such as "sed", "awk", "grep", "rename", etc.

Those manuals are detailed and contain several examples. Usually they tell you which expressions are standardized by ISO or POSIX, and which constructs are specific to Perl.

Also, I suggest trying the regexp directly into the terminal so you can see changes on the fly. After you are satisfied, you can apply it to your file.
```

echo 'Some line' | sed 's:Some:Same:g'

sed -i 's:Some:Same:g' file.html

```

There are some programs out there that visually let you build the regexp, and you can enter a line and see the matches with that regexp. I once used a program called "kregexp" or something like that, but it doesn't appear anymore on the current repository. The repository has a package called "visual-regexp", perhaps that could be used.

---

### Post by mistypotato on 2010-11-01
LuvShines...

I'm at this website trying to understand what you did....
[http://www.regular-expressions.info/tutorialcnt.html]("http://www.regular-expressions.info/tutorialcnt.html")

sed "s:'#\(.*\)#':<cfqueryparam value='#\1#'cfsqltype="cf_sql_varchar">:g" SendPassword2.cfm

[SIZE="5"]**s**[/SIZE]
[2addr]s/regular expression/replacement/flags
    Substitute the replacement string for instances of the regular expression in the pattern space. Any character other than backslash or newline can be used instead of a slash to delimit the RE and the replacement. Within the RE and the replacement, the RE delimiter itself can be used as a literal character if it is preceded by a backslash. An ampersand (&) appearing in the replacement will be replaced by the string matching the RE. The special meaning of "&" in this context can be suppressed by preceding it by backslash. The characters \n, where n is a digit, will be replaced by the text matched by the corresponding backreference expression. For each backslash (\) encountered in scanning replacement from beginning to end, the following character loses its special meaning (if any). It is unspecified what special meaning is given to any character other than &, \ or digits. A line can be split by substituting a newline character into it. The application must escape the newline character in the replacement by preceding it by backslash. A substitution is considered to have been performed even if the replacement string is identical to the string that it replaces. The value of flags must be zero or more of: 

Doesn't tell me squat :-(

[SIZE="6"]**:**[/SIZE]
Used as the delimiter between arguments (I think I got that)


[SIZE="5"]**'#\(.*\)#'**[/SIZE]
Regex expession.
Search for.....# then use literal ( then . (dot) means Matches any single character except line break characters then * which means repeats the previous item zero or more times...(in this case..UNTIL the next "#")?..... Greedy, so as many items as possible will be matched before trying permutations with less matches of the preceding item, up to the point where the preceding item is not matched at all....then \) which is the literal paren closing then the last # which in summary means a pound sign then any character with another pound sign at the end.

So that concludes the regex part.

The next part is what to substitute when the regex expession is found....
<cfqueryparam value='#\1#'cfsqltype="cf_sql_varchar">
where value is replaced by the first stored variable????  Not sure how that worked?

Then finally [SIZE="5"]**:g**[/SIZE]
    Replace the contents of the pattern space by the contents of the hold space. 

Which I have no clue what that means or how it works

And last but not least the file we're working on
SendPassword.cfm

Piece of cake...childsplay  :P

Not actually expecting a reply...more for the benefit of someone coming along later with this issue...maybe me.

---

### Post by mistypotato on 2010-11-01
ok,

working on adding a prefix to Luvshines great work.....regex that limits it to looking only at lines that start with "select", "Select" or "SELECT"

I've tried this regex code....

sed "s:'^.*\b(select|Select|SELECT)\b.*#\(.*\)#':

but it doesn't seem to work.

I added this.........

:'^.*\b(select|Select|SELECT)\b.*

to this...

#\(.*\)#'

but now I get nothing.

is it not ok to add more regex onto existing regex?

thx....anyone...

---

### Post by Vox754 on 2010-11-01
> **mistypotato said:**
> ok,

working on adding a prefix to Luvshines great work.....regex that limits it to looking only at lines that start with "select", "Select" or "SELECT"

I've tried this regex code....

sed "s:'^.*\b(select|Select|SELECT)\b.*#\(.*\)#':

but it doesn't seem to work.

I added this.........

:'^.*\b(select|Select|SELECT)\b.*

to this...

#\(.*\)#'

but now I get nothing.

is it not ok to add more regex onto existing regex?

thx....anyone...

Mmm... that guide you are reading uses a strange syntax. It even says it's for Perl 5. It is, but you need to adapt some things, like the use of parentheses ( ) or brackets [ ], or escaping them like \( \).

I tell you, better to check the perl-doc manuals, and specifically "info sed", sections 3.3 Regular expressions and 4 Examples.

Use "code" tags
```

echo 'select some #bla with spaces#' | sed 's:^\(Select\|select\|SELECT\)\(.*\)#\(.*\)#:\1:g'

```

These parentheses \(.*\) save or "store" the matched characters, which later can be substituted by \1. More groups found in this way can be substituted by \2, \3, etc.

```

echo 'select some #bla with spaces#' | sed 's:^\(Select\|select\|SELECT\)\(.*\)#\(.*\)#:\1\2:g'

echo 'select some #bla with spaces#' | sed 's:^\(Select\|select\|SELECT\)\(.*\)#\(.*\)#:\1\2MORE TEXT #\3#:g'

```
The final :g is used to apply the transformation to all lines. If you remove it, it will only edit the first occurrence of the match.

Also, check your posts, it's not clear when you use different quotes, either single ', double ", or typographical “ ”, or unmatched quotes. It becomes difficult to understand if that is what you want or if it's an error on your part.

---

### Post by mistypotato on 2010-11-02
> **luvshines said:**
> This one works somewhat similar to what you have mentioned:
```

sed "s:'#\(.*\)#':<cfqueryparam value='#\1#'cfsqltype="cf_sql_varchar">:g" SendPassword2.cfm

```

See if this is what you need

What's killing me about all this is that this part....**'#\(.*\)#'** seems to work in a SED context but NOT as an independent REGEX filter alone :confused:

WHY ISSSSSSSSS THAT ??????

---

### Post by mistypotato on 2010-11-02
Thank you Vox.
I'm reading and studying your examples carefully :)

> **Vox754 said:**
> Mmm... that guide you are reading uses a strange syntax. It even says it's for Perl 5. It is, but you need to adapt some things, like the use of parentheses ( ) or brackets [ ], or escaping them like \( \).

I tell you, better to check the perl-doc manuals, and specifically "info sed", sections 3.3 Regular expressions and 4 Examples.

Use "code" tags
```

echo 'select some #bla with spaces#' | sed 's:^\(Select\|select\|SELECT\)\(.*\)#\(.*\)#:\1:g'

```

These parentheses \(.*\) save or "store" the matched characters, which later can be substituted by \1. More groups found in this way can be substituted by \2, \3, etc.

```

echo 'select some #bla with spaces#' | sed 's:^\(Select\|select\|SELECT\)\(.*\)#\(.*\)#:\1\2:g'

echo 'select some #bla with spaces#' | sed 's:^\(Select\|select\|SELECT\)\(.*\)#\(.*\)#:\1\2MORE TEXT #\3#:g'

```
The final :g is used to apply the transformation to all lines. If you remove it, it will only edit the first occurrence of the match.

Also, check your posts, it's not clear when you use different quotes, either single ', double ", or typographical “ ”, or unmatched quotes. It becomes difficult to understand if that is what you want or if it's an error on your part.

---

### Post by luvshines on 2010-11-02
> **mistypotato said:**
> What's killing me about all this is that this part....**'#\(.*\)#'** seems to work in a SED context but NOT as an independent REGEX filter alone :confused:

WHY ISSSSSSSSS THAT ??????

I guess it will not work in independent REGEX and is specific to sed command

---

### Post by mistypotato on 2010-11-02
I could see where it could take a VERY long time to absorb all this....
Not a problem if that's your sole life focus....I can't right now...don't have the time.

**[COLOR="Green"]Anyone care to take a $$ payment $$ in exchange for the answers I need?[/COLOR]**

It's not much but better than most here are paying.  If it takes a minute...that's a rate of $60/hr right?
I'll PayPal $10 per "CORRECT" answer / solution to your paypal account.

Please tell me how to get this to work.......
(The file containing the text to modify is SendPassword2.cfm)

[COLOR="Red"]sed "s:'^\(Select\|select\|SELECT\)\(.*\)#\(.*\)#':<cfqueryparam value='#\1#'cfsqltype="cf_sql_varchar">:g" SendPassword2.cfm[/COLOR]

against this text.....
[COLOR="Blue"]
<CFQUERY datasource="#SESSION.datasrc#" Name="SendPassword">
Select Count(*) As fnd_cnt from techs where email='#SendEmail#' 
</cfquery>
<CFQUERY Name="Logemail" Datasource="#SESSION.datasrc#">
Insert into sendtechlogin (date,email,lastname,firstname) VALUES (now(),'#SendEmail#','#sendlast#','#sendfirst#')
</CFQUERY>[/COLOR]

it should ONLY make a replacement in the line(s) that have the word "**Where**" (case insensitive) in them.


thx

---

### Post by luvshines on 2010-11-02
:lolflag:

Is this what you need ??
```

sed "s:^[[:space:]]*\(select .*\)'#\(.*\)#'$:\1<cf queryparam value='#\2#' cfsqltype="cf_sql_varchar">:gi" SendPassword2.cfm

```

I'll explain a bit (assuming you understood the earlier sed example):-

1. Since it was working fine for all '#...#', when you need to restrict it to lines containing SELECT in REGEX, introduce one in REGEX itself. I added```

**'^[[:space:]]*select .*'**
```
The ^[[:space:]]* thing takes care that line begins with select which may have any number of tabs, blanks in the beginning. An intentional blank space after select then followed by .* will select entire line untill it finds '#

2. For case insensitive, just added **'i'** along with **'g'** in SED itself, ie
```

## Towards end of sed
**:gi**
```

Let us know if it still doesn't work.

For REGEX, wikipedia link is good (to get to know the basics):
[http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)

For SED, I refer to this link all the time:
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

And one thing to remember is, SED works only with REGEX, not extended REGEX (you'll find what are those in wikipedia link)

---

### Post by mistypotato on 2010-11-02
Let me give it a try Luvshines
Actually it did....
But not what was expected....

Here's what it did.....

<CFQUERY datasource="#SESSION.datasrc#" Name="GotPassword">
<cf queryparam value='#SendEmail#'cfsqltype=cf_sql_varchar> 
</cfquery>

Looks like it replaced the ENTIRE line with the replacement string ?

Close...oh so close

---

### Post by Vox754 on 2010-11-02
> **mistypotato said:**
> I could see where it could take a VERY long time to absorb all this....
Not a problem if that's your sole life focus....I can't right now...don't have the time.

**[COLOR="Green"]Anyone care to take a $$ payment $$ in exchange for the answers I need?[/COLOR]**
...

Lol! First time I see someone so desperate to offer money.

I thought you wanted to learn this stuff, not just get the job done.

I guess I'm out. My final advice is use "code" tags to post code, and don't use colors.

---

### Post by luvshines on 2010-11-02
> **mistypotato said:**
> Let me give it a try Luvshines
Actually it did....
But not what was expected....

Here's what it did.....

<CFQUERY datasource="#SESSION.datasrc#" Name="GotPassword">
<cf queryparam value='#SendEmail#'cfsqltype=cf_sql_varchar> 
</cfquery>

Looks like it replaced the ENTIRE line with the replacement string ?

Close...oh so close

Of course it will, since I was stupid enuf to commit silly mistakes :)

I have edited my earlier post now. Check again

---

### Post by mistypotato on 2010-11-02
Luvshines...

Now it's not making any changes

I'm sure it's only an asterisk or dot away from the silver bullet

PLEASE don't quit on me now.

Luvshines...I dont think your "mistakes" are silly.
This is complex stuff and I'm making an uncommon request.
Thanks for your help.  As soon as it works I'll arrange to pay as I promised.

---

### Post by mistypotato on 2010-11-02
> **Vox754 said:**
> Lol! First time I see someone so desperate to offer money.
I thought you wanted to learn this stuff, not just get the job done.
I guess I'm out. My final advice is use "code" tags to post code, and don't use colors.

Vox,
At the moment, I have a security issue at stake with a client.

I certainly DO want to learn to use regex and I find it fascinating....but at this moment, my need is to correct a security problem.

Thank you for your help and I will come back to your posts ...you can believe that  :KS

---

### Post by DaithiF on 2010-11-02
haven't followed the whole thread, but if the requirement is:
on lines matching where (case insensitive) replace all occurrences of #blah# with <cf queryparam value='#blah#' cfsqltype='cf_sql_varchar'> then:

```
sed "/[wW][hH][eE][rR][eE]/s/#\([^#]\+\)#/<cf queryparam value='#\1#' cfsqltype='cf_sql_varchar'>/g"
```

---

### Post by mistypotato on 2010-11-02
Daith,

No changes with yours either ?

However, it "crunched" a lot longer...

---

### Post by DaithiF on 2010-11-02
you know that sed outputs to stdout rather than making changes in-place to the file, right?  So you would normally capture the output to a temporary file and if happy with the changes then rename it as the original.  Or there is the -i flag which does much the same thing.

---

### Post by mistypotato on 2010-11-02
Let me see if and where it may gave gone then....

I was expecting it to update the original file





The output in the terminal window does not show any changes either ?

---

### Post by mistypotato on 2010-11-02
Luvshines

I'm tinkering with your line to see if I can get it to work....

Hope to hear from you again.

---

### Post by DaithiF on 2010-11-02
```
$ cat SendPassword.cfm
<CFQUERY datasource="#SESSION.datasrc#" Name="SendPassword">
Select Count(*) As fnd_cnt from techs where email='#SendEmail#'
</cfquery>
<CFQUERY Name="Logemail" Datasource="#SESSION.datasrc#">
Insert into sendtechlogin (date,email,lastname,firstname) VALUES (now(),'#SendEmail#','#sendlast#','#sendfirst#')
</CFQUERY>

$ sed "/[wW][hH][eE][rR][eE]/s/#\([^#]\+\)#/<cf queryparam value='#\1#' cfsqltype='cf_sql_varchar'>/g" SendPassword.cfm > newfile

$ diff SendPassword.cfm newfile
2c2
< Select Count(*) As fnd_cnt from techs where email='#SendEmail#'
---
> Select Count(*) As fnd_cnt from techs where email='<cf queryparam value='#SendEmail#' cfsqltype='cf_sql_varchar'>'


```

---

### Post by mistypotato on 2010-11-02
Daith..

Are you showing successful results from your regex?

If so, is it the same or did you change it?

Is it possible where using different version or flavors of regex or something?

When I copy you code to a text file, then save it as a script and mark it as executable then run it I get this.....
(I named the script "sqlfix6"

[COLOR="Red"]./sqlfix6: 1: Syntax error: newline unexpected[/COLOR]

---

### Post by DaithiF on 2010-11-02
I just showed you in my last post what effect my regex has on the sample you provided:

```
$ diff SendPassword.cfm newfile
2c2
[COLOR=Red][COLOR=Black]< [/COLOR]Select Count(*) As fnd_cnt from techs where email='#SendEmail#'
[/COLOR]---
[COLOR=Green][COLOR=Black]> [/COLOR]Select Count(*) As fnd_cnt from techs where email='<cf queryparam value='#SendEmail#' cfsqltype='cf_sql_varchar'>'[/COLOR]

```

in case its not clear -- red was the line in the original file, green is the line after applying my sed command.

---

### Post by mistypotato on 2010-11-02
Is it possible we're using different version or flavors of regex or something?

When I copy your code to a text file, then save it as a script and mark it as executable then run it I get this.....


[COLOR="Red"]./sqlfix6: 1: Syntax error: newline unexpected[/COLOR]


(I named the script "sqlfix6")

Because I do not seem to be getting the exact same results as you.

---

### Post by mistypotato on 2010-11-02
Ok,
I fixed that because I had accidentally put an additional character at the end of the line.

But when I run the script from my Terminal window, the file I want to apply the changes to scrolls past in it's entirety.  But looking at the text in the terminal, nothing has changed.

When I look in the directory where the file is located, there are no new files there...

So is it possible it's outputting the result file elsewhere?  If so, where would it likely go?

I trust it is working on YOUR computer....but it has to work on mine.

thx

---

### Post by DaithiF on 2010-11-02
**step1:**
either run this command directly in the terminal (you can copy/paste it) or put it in a file and execute that file (your choice):

```
sed "/[wW][hH][eE][rR][eE]/s/#\([^#]\+\)#/<cf queryparam value='#\1#' cfsqltype='cf_sql_varchar'>/g" SendPassword2.cfm > SendPassword2.changed

```

**step2:**
inspect the file SendPassword2.changed to see what updates have been made.

**step3: **
if the changes are not what you expect, then post back 2 snippets:
(a) the original text
(b) what you want that original text to look like after the update

---

### Post by mistypotato on 2010-11-02
> **DaithiF said:**
> 
[COLOR=Red][COLOR=Black]< [/COLOR]Select Count(*) As fnd_cnt from techs where email='#SendEmail#'
[/COLOR]---
[COLOR=Green][COLOR=Black]> [/COLOR]Select Count(*) As fnd_cnt from techs where email='<cf queryparam value='#SendEmail#' cfsqltype='cf_sql_varchar'>'[/COLOR]
in case its not clear -- red was the line in the original file, green is the line after applying my sed command.

This is exactly what I want.

I am confused as to why it seems to be working on your machine and not mine.

For some reason, the file is not updating on my machine or it is outputting to a different location than I am expecting?  The output TEXT WITHIN the Terminal window from which I run the script file containing your regex line does not shoe any changes either.

I ask again...is it possible that we are running different version of regex or perl or something that might be causing my machine to interpret and parse your line of text differently ?

---

### Post by DaithiF on 2010-11-02
please read my last post and follow steps 1 and 2 exactly.  If you do as I have shown there won't be any terminal output.  the fact you mention terminal output makes me think you haven't followed the steps.

---

### Post by mistypotato on 2010-11-02
ok..

I am sure you know what you are talking about  :)

I will follow your steps PRECISELY

(and enjoy success)

thx

---

### Post by luvshines on 2010-11-02
> **mistypotato said:**
> Luvshines...

Now it's not making any changes

I'm sure it's only an asterisk or dot away from the silver bullet

PLEASE don't quit on me now.

Luvshines...I dont think your "mistakes" are silly.
This is complex stuff and I'm making an uncommon request.
Thanks for your help.  As soon as it works I'll arrange to pay as I promised.

An extra $ ruined all the fun, I was testing something else and this was added somehow :). I hope this one works
```

sed "s:^[[:space:]]*\(select .*\)'#\(.*\)#':\1<cf queryparam value='#\2#' cfsqltype="cf_sql_varchar">:gi" SendPassword.cfm

```

If this works, you can either redirect the output to another file with ```
> <file-name>
```
Or use, sed -i to replace the file inplace, **but take backup of original file**

---

### Post by mistypotato on 2010-11-02
ok...so where do I send your money?



[SIZE="7"]LOL[/SIZE]  :KS





Instead of using a script file, I issued the command directly from the terminal and it worked.

---

### Post by mistypotato on 2010-11-02
LuvShines !!

Daith JUST got it worked out 

Where WERE you for the last hour :confused:


No worries...if yours also works I'll pay you as well  :KS:KS:KS

---

### Post by DaithiF on 2010-11-02
> **mistypotato said:**
> ok...so where do I send your money?



[SIZE=7]LOL[/SIZE]  :KS





Instead of using a script file, I issued the command directly from the terminal and it worked.
great.  no need for money, i wasn't helping for the $10

---

### Post by mistypotato on 2010-11-02
Cool !

So if I need you again how do I get you  :P


This code will save me countless hours of grief and potentially more.

Would $25 be more appealing ?

(I do feel your efforts and time are valuable)  :KS:KS:KS:KS:KS

---

### Post by mistypotato on 2010-11-02
Now that I have this awesome regex that will do the grunt-work of what I need to do, the logical progression is to automate it so that I can apply it to a directory full of files that need changing rather than change the file name for each and every file.

So, how would this.....

sed "/[wW][hH][eE][rR][eE]/s/#\([^#]\+\)#/<cf queryparam value='#\1#' cfsqltype='cf_sql_varchar'>/g" SendPassword2.cfm >


be modified to automatically go through a directory full of files needing this applied to them all?

That's the million dollar question.....but paying only a fraction thereof unfortunately.  :P

I'm guessing a shell script that includes this command.............

I just might be able to figure this one out actually if so.

---

### Post by DaithiF on 2010-11-02
```
for file in *.cfm
do
  echo "processing $file"
  sed -i.bak "/[wW][hH][eE][rR][eE]/s/#\([^#]\+\)#/<cf queryparam value='#\1#' cfsqltype='cf_sql_varchar'>/g" "$file"
done
```

will process any .cfm files in the current directory, save a backup copy of the originals with an extension of .bak and apply the updates to the original files.

---

### Post by mistypotato on 2010-11-02
> **DaithiF said:**
> ```
for file in *.cfm
do
  echo "processing $file"
  sed -i.bak "/[wW][hH][eE][rR][eE]/s/#\([^#]\+\)#/<cf queryparam value='#\1#' cfsqltype='cf_sql_varchar'>/g" "$file"
done
```

will process any .cfm files in the current directory, save a backup copy of the originals with an extension of .bak and apply the updates to the original files.

**DAITHiF....YOU'RE HIRED !!**

I need you on the next flight from London to Florida, USA  :P

---

### Post by mistypotato on 2010-11-02
Where are the single quotes coming from before **<cf queryparam** and after** varchar'>** ?

They are not in the original text but are applied to each transformation.

They should not be added.

thx



> **DaithiF said:**
> I just showed you in my last post what effect my regex has on the sample you provided:

```
$ diff SendPassword.cfm newfile
2c2
[COLOR=Red][COLOR=Black]< [/COLOR]Select Count(*) As fnd_cnt from techs where email='#SendEmail#'
[/COLOR]---
[COLOR=Green][COLOR=Black]> [/COLOR]Select Count(*) As fnd_cnt from techs where email=[SIZE="5"]**[COLOR="RED"]'[/COLOR]**[/SIZE]<cf queryparam value='#SendEmail#' cfsqltype='cf_sql_varchar'>[SIZE="5"]**[COLOR="RED"]'[/COLOR]**[/SIZE][/COLOR]

```
.

---

### Post by luvshines on 2010-11-02
> **mistypotato said:**
> Where are the single quotes coming from before **<cf queryparam** and after** varchar'>** ?

They are not in the original text but are applied to each transformation.

They should not be added.

thx

This shud resolve that:
```

sed -i.bak "/[wW][hH][eE][rR][eE]/s/'#\([^#]\+\)#'/<cf queryparam value='#\1#' cfsqltype='cf_sql_varchar'>/g" "$file"

```

---

### Post by mistypotato on 2010-11-02
Thank you.

I'll give it a whirl.

Oddly, It doesn't "always" seem to add them.
Sometimes it does, other times it does not.

Haven't quite figured out the rhythm of it.

thank you again.

---

### Post by luvshines on 2010-11-02
> **mistypotato said:**
> Thank you.

I'll give it a whirl.

Oddly, It doesn't "always" seem to add them.
Sometimes it does, other times it does not.

Haven't quite figured out the rhythm of it.

thank you again.

The original REGEX was looking for #...# and replacing it with the new string.
Ie. email='#send...#' replaced with email='new-string'

Latest one(which I modified) looks for '#...#' and replaces it with new string
Ie. email='#send...#' replaced with email=new-string

Hence consistency is actually governed by the input strings :)
**And, the second one will fail if input string doesn't have '#...#'** ie # preceded and succeeded by single-quotes

---

