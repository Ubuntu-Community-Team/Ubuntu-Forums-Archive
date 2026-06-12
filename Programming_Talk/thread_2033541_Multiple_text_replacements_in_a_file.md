---
title: "Multiple text replacements in a file"
date: 2012-07-26
forum: Programming Talk
---

### Post by thombark on 2012-07-26
I have an input text file that needs a lot of conversion to an output text file.

I would like to specify a sequence of replacement commands inside a  script file, where each command would do its particular replacement  throughout the text file. This script will contain possibly hundreds of  replacement commands. The commands themselves can be simple replacement  commands (e.g. replace all { with [) or more complex regular  expressions. The order of replacements must match the script file order.

This script would need to be run against various input files.

What is the best program to use to automate this process?

Thanks.

---

### Post by trent.josephsen on 2012-07-26
sed, probably

```
% cat >script
s/hello/hi/g
s/world/everybody/g
% echo "hello, world" | sed -f script
hi, everybody
```

---

### Post by donsy on 2012-07-26
> **thombark said:**
> I have an input text file that needs a lot of conversion to an output text file.
... This script will contain possibly hundreds of  replacement commands. ...
This script would need to be run against various input files.
What is the best program to use to automate this process?

Perl
```
#!/usr/bin/perl 

$^I = ".bak";   # Save originals as backups with extension .bak

while(<>) {
    # insert your regex patterns here as needed
    print;
}
```Run the above program with one or more filenames as command line arguments. You can use filename globbing, for example: *.txt

---

### Post by trent.josephsen on 2012-07-27
> **donsy said:**
> Perl
```
#!/usr/bin/perl 

$^I = ".bak";   # Save originals as backups with extension .bak

while(<>) {
    # insert your regex patterns here as needed
    print;
}
```Run the above program with one or more filenames as command line arguments. You can use filename globbing, for example: *.txt

Never done any one-liners?

```
#!/usr/bin/perl -i.bak -wp
# insert regex patterns here
```

Much simpler, don't you think?

---

### Post by TheFu on 2012-07-27
There are lots of programming languages and tools that do what you are describing, so the answer for "best" really depends on your skillset.

If you know perl, then you'd already have this done.  Since you don't know **perl**, the easiest tool to understand quickly is probably a mix of** sed** and **cut**.  **Ruby **and **python **can handle it too, plus we shouldn't forget **awk**.

If I was just starting out and realized a need to learn a scripting language, then I'd spend the time to learn python. That effort will pay you back over the years.

BTW, you can try out all these languages to see which makes the most sense to you. Something might "click" for you in one of those languages.

BTW, I modified a 200 line perl script this morning to add a complex rename function for files. Took about 10 minutes and it will be used for many years to come.  The modified script was written 2 yrs ago and gets run 3+ times every day.  Renaming the files will save me lots of manual labor.

Personally, I use perl for this stuff - it was the python of the 1990s  and an old sysadmin recommended that I learn it over awk.  ***Looking back,  I must say that was some of the best advice I've ever been given.  ***In  the same vein, I recommend that you learn **Python**. Trust me.

---

### Post by donsy on 2012-07-27
> **trent.josephsen said:**
> Never done any one-liners?

```
#!/usr/bin/perl -i.bak -wp
# insert regex patterns here
```Much simpler, don't you think?

Agreed
**

---

### Post by Vaphell on 2012-07-27
> BTW, I modified a 200 line perl script this morning to add a complex rename function for files. Took about 10 minutes and it will be used for many years to come. The modified script was written 2 yrs ago and gets run 3+ times every day. Renaming the files will save me lots of manual labor.

does it do more that the perl-based *rename*?

---

### Post by trent.josephsen on 2012-07-27
> **Vaphell said:**
> does it do more that the perl-based *rename*?
At 200 lines, it had darn well better.

Edit: oh wait, I didn't realize the rename function was only part of the program. Never mind.

---

### Post by Hetepeperfan on 2012-07-27
> **thombark said:**
> I have an input text file that needs a lot of conversion to an output text file.

I would like to specify a sequence of replacement commands inside a  script file, where each command would do its particular replacement  throughout the text file. This script will contain possibly hundreds of  replacement commands. The commands themselves can be simple replacement  commands (e.g. replace all { with [) or more complex regular  expressions. The order of replacements must match the script file order.

This script would need to be run against various input files.

What is the best program to use to automate this process?

Thanks.

I also depends on the difficulty of of your string processing the next command pretty much replace every lower case vowel for a vowel in the gcc  manual which is several thousands lines of documentation in an instance.

```
 man gcc | sed -e 's/[aeoiuy]/./g
```this does  a lot of conversions in  "no" time.
but since you want to do a lot of different kind of string processing I must say perl is probably the best tool for the job. Personally I think perl is best suited for string processing, Python is more a general type of tool. However, python has a very well documented regular expression library as wel and will probably do the job, but I think perl would do it faster. Perl has really build regular expression into their syntax, whereas python has it build in to a separate module. Although since python supports raw strings ( print r"\\" really prints two backslashes. ) which make regex a joyful tool, I must say python is pretty good at it, but perl is build for it.

cheers, 

cheers

---

### Post by trent.josephsen on 2012-07-27
As a rule of thumb I would use Python over Perl for anything I anticipated growing beyond a few hundred lines, **unless** its primary role was text manipulation. Renaming files, editing files, text analysis -- that's Perl's domain and Perl does an incredible job at making it fast and easy. But when the intrinsic complexity of the task surpasses a certain threshold, Python's advantages do begin to look more attractive.

---

