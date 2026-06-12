---
title: "Can´t locate the .pm file"
date: 2023-09-21
forum: New to Ubuntu
---

### Post by viola-ta on 2023-09-21
Hello all,

I'll try to describe my problem so that hopefully someone can help me in the end:

1. I have installed a program to analyse sequences on my linux. I did this with conda, the program ran without errors.

2. I installed another program, or rather a pipeline with several programs. One of the new programs in the pipeline is the one I had before and which also ran. I have installed the new program outside of conda (this was recommended by the creator).

3. now I have the following problem: when I want to run the old program alone, I now get an error code: Can't locate file.pm
Because the old program now tries to open the .pm file from the pipeline program. But this is wrong, the original .pm file should be used. 

Question: Can I somehow define which of the two files.pm should be used?

Is this understandable?

Does anyone have an idea what I mean and can help me?

That would be fantastic :)

Greetings

---

### Post by TheFu on 2023-09-21
What's the exact name of the file missing?  .pm usually means Perl Module, so it is likely a perl module that needs to be installed or the PERLLIB environment variable needs to be setup like it is for the more complex commands you are running.  Hard to tell with the massive amount of exact, specific, information provided.

I don't know anything about "conda". Sorry.  Is that a python thing?

---

### Post by viola-ta on 2023-09-21
Conda is a package and environment manager.
I have created my own environments for some tools, which should actually avoid the error described.

The full name is KronaTools.pm. The file is still there. And the old program was still running until I installed the new one. 

As I understand it, the old program conflicts with the new pipeline. The file KronaTools.pm now exists twice, and the old program cannot find the old KronaTool.pm file again. But it is definitely still there.

---

### Post by TheFu on 2023-09-21
> **viola-ta said:**
> Conda is a package and environment manager.
On Ubuntu, we use APT.  Simplify the tools to **apt** or **apt-get** as a way to rule out an extra layer of complexity.  I know you probably won't do this, but simplifying is step 1 for all troubleshooting.

Of course, python, ruby, perl, have their own packaging tools, so if you need something newer than what the distro-packagers decided, use those directly.  For perl, that would be be **cpanm**.  [https://github.com/marbl/Krona/wiki/Installing](https://github.com/marbl/Krona/wiki/Installing) says they haven't embraced "the perl way", which is unfortunate. CPAN is an elegant solution for ensuring perl modules and programs are fully tested across many different platforms, daily.

> **viola-ta said:**
> I have created my own environments for some tools, which should actually avoid the error described.
This is vague to me.  What is an "environment".  There are many, many, different ways to accomplish this.  Is is just a way to hide setting a few environment variables, place different PATHs are the beginning of existing variables or something more separated like a container or virtual machine?  Chances are you'll need someone familiar with the specific tool.  If that is just "conda", then it isn't me.

> **viola-ta said:**
> 
The full name is KronaTools.pm. The file is still there. And the old program was still running until I installed the new one. 
"There" is vague.  The location needs to be found by the programs that want to use it.  That would usually be managed by a few PERL environment variables.  PERL5LIB, for example.  Or there are specific places that the perl executable will look, but that depends on the exact version of perl used, how it was installed, and any environment wrappers, like perlbrew, wrapped around it.  For example, I have a number of different perl versions install, along with different versions of the modules needed.
```
$ which perl
/home/thefu/perl5/perlbrew/perls/perl-5.37.4/bin/perl

$ perlbrew list
* perl-5.37.4                               
  perl-5.36.0                               
  perl-5.35.5                

```

I use perlbrew to manage different perl environments.  The system perl is still in /usr/bin/perl
```
$ /usr/bin/perl --version

This is perl 5, version 30, subversion 0 (v5.30.0) built for x86_64-linux-gnu-thread-multi
(with 59 registered patches,
```
That's perl-5.30.59 ... meh.  NEVER, ever, touch the system perl, python, ruby, go, whatever.  Always setup a separate version, if you want/need it.  Seems that conda is doing this at a level above just the perl program version. In theory, that should be fine.

> **viola-ta said:**
> 
As I understand it, the old program conflicts with the new pipeline. The file KronaTools.pm now exists twice, and the old program cannot find the old KronaTool.pm file again. But it is definitely still there.

Perhaps if you post exactly the command being run AND the output/errors, someone would see the issue?  I suspect this question is too specialized and you'll need to get help from the KronaTools guys.  While you are there, ask them when they will be putting their code into CPAN.  [https://metacpan.org/search?q=KronaTools](https://metacpan.org/search?q=KronaTools)

---

### Post by viola-ta on 2023-09-22
> This is vague to me.  What is an "environment".  There are many, many, different ways to accomplish this.  Is is just a way to hide setting a few environment variables, place different PATHs are the beginning of existing variables or something more separated like a container or virtual machine?  Chances are you'll need someone familiar with the specific tool.  If that is just "conda", then it isn't me.

                        [COLOR=#000000][FONT=Lohit Tamil Classical]Unfortunately, I can't really answer that. I don't yet understand that much about the subject. And in general of the whole matter...[/FONT][/COLOR]
 [COLOR=#000000][FONT=Lohit Tamil Classical]According to my knowledge/understanding, it is like a container. But I could be wrong about that. But it is not a virtual machine. [/FONT][/COLOR] 


>  I suspect this question is too specialized and you'll need to get help from the KronaTools guys.

                        [COLOR=#000000][FONT=Lohit Tamil Classical]I have done the same today. I am now waiting for an answer. [/FONT][/COLOR] 

   

                        [COLOR=#000000][FONT=Lohit Tamil Classical]First of all, thank you for your help.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Lohit Tamil Classical]I'll keep thinking and trying things out. Somehow I will find a solution :)[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-09-24
This seems to be going in circles. I have a couple questions. I haven't used Perl in many years when I went back to college, so trying to jog my memory.

Where, including the specific path to, is the 'KronaTools.pm' file located? 

For Perl applications, a custom Perl Module file was usually located in a "lib" folder under the folder that the script was located... Even if under a different path, it was located in a folder named lib. (I didn't know why at first.)

What specifically, is the line in your Perl script that is importing the .pm file? Or how are you modifying @INC with the search path to find that?

Lets say my Application was named Sample, and that it's Perl Scripts are in /home/mafoelffen/Scripts/pl/Sample/... And my Perl Module (sample.pm) for it was located at /home/mafoelffen/Scripts/pl/Sample/lib/sample.pm... Then line to import my pm was usually something like this:
```

perl -I /home/mafoelffen/Scripts/pl/Sample

```
That adds the lib subfolder to that path and adds it to the @INC search path...right?

What was the specific error message again? Like I said, it's been years and I might not be remembering it right. And I remember there where about 3 other ways to do that differently, to do the same thing.

In the import process, Perl appends /lib to that @INC path reference. When I was learning that, I learned that the hard way. Because I thought it needed the"/lib" in the path, and it was appending "/lib" (again) to that and not finding my module file path... I didn't know that Perl did that at first. Some one had to tell me what I had wrong with that.

Is that what you are talking about?

EDIT --- (Looked it up, so I wasn't sending you on a goose chase)
re: man perl
```

        "@INC"                 locations of perl libraries

       "@INC" above is a reference to the built\u2010in variable of the same name; see perlvar
       for more information.

```
re: perl --help
```

 -I directory      specify @INC/#include directory (several -I's allowed)

```
So yes, like I said above, but it doesn't say that it appends "/lib" to that, and that was driving me crazy... because it couldn't find it. It's one of those things that is not well documented.

---

### Post by TheFu on 2023-09-25
Perl will check "expected" locations for modules.  Those are documented in the perldoc tool.  The FAQs are really helpful too.
```
$ perldoc perlfaq8
...
  How do I add the directory my program lives in to the module/library search path?
    (contributed by brian d foy)

    If you know the directory already, you can add it to @INC as you would
    for any other directory. You might "use lib" if you know the directory
    at compile time:

        use lib $directory;
...

```
It shows multiple methods/techniques.

I've never used the -I method with perl.

---

### Post by MAFoElffen on 2023-09-25
I used that... back in 2014? I went back to college to document my Computer Science skills in my my 50's, so that sounds about right.

Jeeze I'm feeling a bit old now.

---

### Post by viola-ta on 2023-09-28
I am impressed by how much input I get, thank you very much.

But I must confess, my head is spinning! #-o

I only understand a fraction of what is written here.  

I will remember some of the information and try to implement it, but it will take time.

---

### Post by TheFu on 2023-09-28
I suspect that all you need to do is correctly set the PER5LIB environment variable.  
[https://chestofbooks.com/computers/webservers/apache/Stas-Bekman/Practical-mod_perl/3-9-2-2-Using-the-PERL5LIB-environment-variable.html](https://chestofbooks.com/computers/webservers/apache/Stas-Bekman/Practical-mod_perl/3-9-2-2-Using-the-PERL5LIB-environment-variable.html) explains it and shows examples.

---

