---
title: "Find all instances of search string in text file and export to new file?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by 655 on 2008-09-13
Hi,

I have the address book from an old mobile phone saved as a plaintext file, and I'd like to extract the e-mail addresses of my contacts in a more efficient way than by hand.  The file contains a lot of other useless information, though, so I want to extract only the lines containing the addresses.

The addresses are the only text in the file that contain the @ sign, and they take up a single line each, so I just want to execute something that finds all instances of lines containing @, and exports the text from those lines to a new file, one per line.

How can I do this?

---

### Post by skippuff54 on 2008-09-13
you should be able to do this with a combination of the awk and cat commands. do man awk and man cat to read more about them.

i forget the exact syntax to be honest but it's basically awk file (search_string) > cat (new_file)

you can do this in terminal by the way 

awk and cat are OG aka original gangsta unix commands, and the process i just described was what the original unix developers referred to as using pipes...thought i'd throw in that bit of history :)

---

### Post by Mornedhel on 2008-09-13
Oh c'mon, throwing awk into that is a bit overkill.

grep '@' all_your_files > your_new_file

grep is just "output line if matches regex".

AWK is an entire language.

Edit : Also, ">" is not a pipe, it's a redirection. And since when are pipes a bit of history ?... You youngsters and your newfangled graphical user interfaces. Feh.

---

### Post by skippuff54 on 2008-09-13
> **Mornedhel said:**
> Oh c'mon, throwing awk into that is a bit overkill.

grep '@' all_your_files > your_new_file

grep is just "output line if contains regex".

AWK is an entire language.

now it is, but at its simplest form it is a utility command. the language is built on a series of awk commands

---

### Post by 655 on 2008-09-13
Thanks to you both... for some reason I was having a lapse and didn't realize that grep prints a line, not justa single character.

That worked well, but there are a few other hitches I ran into that I'd like to be educated about:

The lines with the e-mails in them, it turns out, contained a little prefix, depending on whether it was home, work, cell, etc.  It looked like EMAIL;HOME:foo@bar.com.
So, I was able to find the lines containing the @, but I couldn't think of an ingenious, one-line way of stripping out the preceding EMAIL;HOME: or EMAIL;WORK: prefix while retaining the address, and outputting all of that.

I ended up having to use sed about three times to find and replace those prefixes with a blank, then grepped it and redirected to a clean file.  Is there a way I could have done all of that within grep or awk, or even within sed, without having to execute the line in triplicate?

I used &&, of course, but it still seemed grossly inelegant.

---

### Post by skippuff54 on 2008-09-13
the short answer is yes. done those kinds of things with awk before. the longer answer is yes but i don't know how exactly. i think you can use a combination of single and double quotes (' and ") as well as the wildcard character (*) and a couple of other simple arguments....if you're interested, i would advise looking up the awk command - try "man awk" at the terminal - or even "whatis awk" at the terminal - and look to see exactly what kinds of searches you can perform

then you can use the pipes feature via the cat command to output those results into a clean file

---

### Post by 655 on 2008-09-13
Yeah, I did have a look at the man and info pages for awk, but this is one of those cases where the man page is insanely verbose and technical.  I'll have to read some tutorials on the net.

Thanks!

---

### Post by Mornedhel on 2008-09-13
Within grep, I don't think so (at least not easily). grep is really great for matching regexes against lines, but that's about all it does (of course, there still are enough options to make man grep a nice long read). Most probably doable with awk (which IS a programming language and has been since 1977, despite what skippuff54 said), but I'm not experienced enough with it. Entirely doable with sed, but whatever sed skills I had I lost ever since I started using Perl.

In Perl, though :

```

#!/usr/bin/perl

while (<>) {
    
    # from 'EMAIL;HOME:foo@bar.com' to 'foo@bar.com'
    next unless m/@/; # skip to next line unless looks like an address
    s/^.*://; # not likely to have a ":" in a legal email address
    print;
    
}

```Use as cat all_your_files | perl script.pl > your_output . Not tested, but should work.

---

### Post by 655 on 2008-09-13
That worked beautifully!  I didn't have the original anymore, but I created a test file to give it a go.  

That's very nice.  I wish I knew more, but I'm not a programmer, so learning deep scripting languages is not on my short list...but it does help to learn about the rudiments.

---

### Post by skippuff54 on 2008-09-13
ok ok i'll concede it's a language, fine but it's like few others and i'm stickin to it.


more info here: [http://www.softpanorama.org/Tools/awk.shtml]("http://www.softpanorama.org/Tools/awk.shtml")

> Like PERL and TCL, most prefer to view it as a "scripting language."  It has no objects; it is not functional; it does no built-in logic programming. -Ronald Loui, Wasington University in St. Louis

and here: [http://www.softpanorama.org/People/Shell_giants/introduction.shtml]("http://www.softpanorama.org/People/Shell_giants/introduction.shtml")

---

### Post by Mornedhel on 2008-09-13
> **skippuff54 said:**
> it's like few others and i'm stickin to it.

Hey, I never said awk sucked... I only said it was a programming language (which includes scripting languages) and thus overkill for what the OP needed. Then when the requirements changed I pointed out awk had become a viable choice, but as I know Perl much better than I do awk or sed, the solution I presented used Perl.

655 : glad to know the script worked for you. I was a bit afraid I could have let an error slip, as I never ran it before posting.

---

### Post by skippuff54 on 2008-09-13
no doubt, i appreciate your clarification and now i think i'm gonna expand my Perl know-how :)

true to the core concepts of unix the simplest solutions tend to be the most useful

---

