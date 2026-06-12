---
title: "How to use Ruby"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by SyntheticShield on 2008-06-12
I assume this will be the typical noob question, but I gotta ask.  I installed Ruby from synaptic, but how do I launch it.  Im still very much in the infancy of learning, but in windows you could launch and IDE I guess it would be called and start programming, practicing and so on.

How do I do all that in Ubuntu so I can test scripts create and compile and so on?

---

### Post by MmmmJoel on 2008-06-12
> **SyntheticShield said:**
> I assume this will be the typical noob question, but I gotta ask.  I installed Ruby from synaptic, but how do I launch it.  Im still very much in the infancy of learning, but in windows you could launch and IDE I guess it would be called and start programming, practicing and so on.

How do I do all that in Ubuntu so I can test scripts create and compile and so on?
To start, you can use Ruby in the [interactive mode]("http://en.wikibooks.org/wiki/Ruby_Programming/Interactive_Ruby"). Then find a good beginner's guide on the Internet and follow along.

---

### Post by SyntheticShield on 2008-06-12
Okay, I got the interactive mode.  But how do I go about writing practice scrips and so on?  Can I just use a regular text editor and save them with a ruby language extension?

---

### Post by gr4nf on 2008-06-12
You don't even need an extension. Simply write a text document full of Ruby, and use the command "ruby", where the argument is the file.

---

### Post by MmmmJoel on 2008-06-12
It's best to start learning [here]("http://www.ruby-lang.org/en/documentation/"). You can also follow [this guide]("http://tryruby.hobix.com/") which uses the irb in your web browser for your convenience.

---

### Post by SyntheticShield on 2008-06-12
Okay, I apologize, I may have not worded thing in the best way.  I have been studying ruby so I know about the guides and the site and so forth.  I was more after how do I start ruby on Linux.

When I was working with it in Windows, ruby had a one click install program that included ruby but also the environment in which to write your code and save it.  So I wasnt so much after how do I use or code ruby, but more so how do I use ruby in Linux in such a way that I can write code and run the programs and so forth.

But I think gr4nf gave me part of the answer I was looking for.  I assume ruby can read the code in the text document and it doesnt have to have a particular extension?  If so, do I have to put the files in a particular location or folder to run them from the IRB?  Or do I just make the argument the path to file with the file name?

---

### Post by MmmmJoel on 2008-06-12
You do not need to use any particular IDE or editor to write Ruby applications. A text editor like gedit will work fine.

Nor does it matter where you save the file. Nor does it matter what you call it, though Ruby files conventionally use the .rb extension.

You can run the file by typing the following in a terminal window.
```
ruby filename.rb
```

---

### Post by sam_delta on 2008-06-12
you can also make the file executable, and just double click it to run it.
to make it executable: (assuming your the owner of the file)
```
chmod u+x filename.rb
```

EDIT. if your the owner of the file you do not need 'sudo' to make it executable
sam

---

### Post by cmay on 2008-06-12
hi.
if you want a editor whit highlighting i suggest geany.
there is more editors in the repos but geany 
seems very simple to use and still its pretty handy for many things. 
i use it myselve. 
there is a nice push compile button and see results in shell 
right away function like other windows 
editors may have. its reminds me of devc++.
easy to use also.

---

### Post by arist0tle on 2008-06-12
I recommend Geany as well. It's great....but I also recommend perl or python instead of ruby

---

### Post by SyntheticShield on 2008-06-14
Sorry its taken me so long to get back to this, I had a few things going on that took me away from working on this.

When Im in irb, how do I point it to a file Ive saved on the desktop?  I made a test file and when I try to run it by typing in 'ruby test.rb', I get the following:

ArgumentError: wrong number of arguments
	from (irb):1:in `test'
	from (irb):1


Im assuming it cannot find the file?

---

### Post by sam_delta on 2008-06-14
yes, it found the file, but its telling you that the file/code has a syntax error, the code is not well written and therefore, it will not execute,

post your code

sam

---

### Post by SyntheticShield on 2008-06-14
If that is the case, then I know whats wrong.  It was just a simple math equation apparently I need to read a bit more.

---

### Post by SyntheticShield on 2008-06-14
Okay, it doesnt seem like anything wants to run.  Here is the code Im using now:

```

print "Hello Ruby!\n"

```

Just something simple to make sure I was doing things right with the file.  That was saved as test.rb and in the irb I type in 'ruby test.rb' and Im still getting:

```

ArgumentError: wrong number of arguments
	from (irb):16:in `test'
	from (irb):16
	from :0

```

---

### Post by sam_delta on 2008-06-14
i dont know if "print" is a ruby function...

try ```
puts "Hello world"
```

sam

---

