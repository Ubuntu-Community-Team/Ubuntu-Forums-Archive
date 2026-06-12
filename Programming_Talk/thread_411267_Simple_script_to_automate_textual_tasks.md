---
title: "Simple script to automate textual tasks?"
date: 2007-04-16
forum: Programming Talk
---

### Post by rosslaird on 2007-04-16
I am not a programmer, but I do know that what I want to do should be very straightforward in various languages (perl, python, lisp even).

Here's what I want to do:

In emacs (ideally), I want to be prompted for a name. I enter the name, then I am prompted to choose from between four itemized blocks of text (each one can be numbered). The script will insert the name and the text into a buffer. This is kind of like a form letter. In the blocks of text there will be placeholders for <name>, which will be inserted when I choose the name (maybe I have to choose the text block then the name).

So we're talking about two fields, basically, and a function to match a given name with a given block of text. This must be very easy.

Ross

---

### Post by Arndt on 2007-04-17
> **rosslaird said:**
> I am not a programmer, but I do know that what I want to do should be very straightforward in various languages (perl, python, lisp even).

Here's what I want to do:

In emacs (ideally), I want to be prompted for a name. I enter the name, then I am prompted to choose from between four itemized blocks of text (each one can be numbered). The script will insert the name and the text into a buffer. This is kind of like a form letter. In the blocks of text there will be placeholders for <name>, which will be inserted when I choose the name (maybe I have to choose the text block then the name).

So we're talking about two fields, basically, and a function to match a given name with a given block of text. This must be very easy.

Ross

It would be a pity for no one at all to answer, but I won't write the whole function for you - it would take me too long to figure out all the details again, since I haven't written Elisp for a long time. Here's an Elisp function that does the prompting, and then inserts something trivial and the name:

```
(defun insert-template (name number)
  "Templates."
  (interactive "*sName: \nnNumber: ")
  (let ((s (nth (1- number)
		'("template1\n"
		  "template2\n"
		  "template3\n"
		  "template4\n"))))
    (insert s name)))
```

---

### Post by phossal on 2007-04-17
Here is an example. What else should it do?

```
#!/usr/bin/perl


# These templates could be read from a file instead with slight changes

@template = (
		"Welcome, <NAME>, to template block number 1.\n", 
		"Thank you, <NAME> for contacting our office.\n",
		"Dear <NAME>, you've won!\n",
		"Mr. or Mrs. <NAME>: Please call me as soon as possible\n"
);



#Prompt
system "clear";
print "Welcome to the template editor v1.\n";
print "Please choose a template:\n";
print "(1) $template[0]";
print "(2) $template[1]";
print "(3) $template[2]";
print "(4) $template[3]";

$tem = <STDIN>;
chomp($tem);

$no = $tem;
$tem -= 1;


print "Template $no selected. Enter name:\n";

$name = <STDIN>;
chomp($name);

print "Adding $name to template.\n\n";

print "Completed Template: \n";
$template[$tem] =~ s/<NAME>/$name/;
print $template[$tem]."\n";
```

---

### Post by rosslaird on 2007-04-17
Thanks for the help. This gives me an excellent start. It's really quite simple, and the above solutions will do nicely.

Cheers.

Ross

---

