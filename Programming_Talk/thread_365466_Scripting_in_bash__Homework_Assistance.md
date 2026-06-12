---
title: "Scripting in bash : Homework Assistance"
date: 2007-02-19
forum: Programming Talk
---

### Post by The Tronyx on 2007-02-19
Hello everyone.  Before I get to the problem, it might help if I gave you a bit of a background  on my problem(s).

I'm pretty new to nix, and taking an into to UNIX class at my college and it operates on the principle of learning UNIX with linux.  Aside from the fact that my professor is a mad-woman and arguably incapeable of teaching (I asked her a question earlier via e-mail and she told me to wait 24 hours and if I couldn't find the answer to e-mail her again >.<).  So here we are, unit 6, talking about X windows, GNOME & KDE and out of nowhere comes an assignment to write a batch file so I'm at somewhat of a loss, especially since asking the instructor is somewhat out of the question.:( 

And we are not using our own machines but rather using SSH to connect to a college UNIX machine to work off of, that might be of some relevance too.

So the assignment is oddly themed to break a code, we have a main file to work off of, call it file1, and file2 and file3 to incorperate into it.  File 1 is jumble and we use sed commands to change things in it and cat, sed, tr and what not to insert file2 and file 3 to hopefully have it make sense in the end.

The actual assignment description is:
> Create a batch set of sed commands (i.e., a repeatable script) to make the following changes to blue_bird_of_paradise.txt 

And here is a sample of the actions we need to perform:
> Change all occurrences of  * to t
Capitalize the first t in lines 5 and 11
Change all occurrences of 5 to dd
Change all occurrences of 4 to n
Change all occurrences of 2 to o
Change the first occurrence of o in lines 1, 2, and 6 to O.


I can understand how to issue the commands as needed with sed to perform the actions requested with replacement but as far as a repeatable script, I am at a complete loss.  I've tried working off a few basic tutorials but it seems as though I can't even begin to write the script as I get:

 #!/bin/bash
bash: !/bin/bash: event not found

or 

#!/usr/bin/bash
bash: !/usr/bin/bash: event not found

If anyone has time could the point me in the right direction please?  

Thank you all for your help ahead of time.:)

---

### Post by LotsOfPhil on 2007-02-19
Not to put too fine a point on it, but your assignment is not very complex. Every one of those changes can be made with a single call of sed. Do you have any experience with sed?

As far as #!/bin/bash not working, type "whereis bash" on the machine. You'll get the path as output. If that doesn't work the computer doesn't have bash. Since your script is going to be simple, there will be no difference in your finished product.

Here's a great resource: [http://tinyurl.com/22nlqu](http://tinyurl.com/22nlqu)

---

### Post by The Tronyx on 2007-02-19
> **LotsOfPhil said:**
> Not to put too fine a point on it, but your assignment is not very complex. Every one of those changes can be made with a single call of sed. Do you have any experience with sed?

Here's a great resource: [http://tinyurl.com/22nlqu](http://tinyurl.com/22nlqu)

We haven't done anything with sed until this assignment was given to us so figuring out the syntax is problematic enough, let alone the fact that we haven't discussed scripting until this assignment as well.

Thanks for the link and "whereis bash". :)

---

### Post by IYY on 2007-02-19
> Change all occurrences of 2 to o


These types of things are particularly easy. It can just be something like

```
sed -i s/2/o/g yourfile.txt
```

All you need to do to make a batch file of such operations is to stick them in a text file, one operation per line, and make the file executable. Something like #!/bin/bash can be used, but is not really necessarily since the commands are so simple. 

That is if you want to make all the changes to the file itself. If you want your command to output the new file to the screen, or to a new file, you should not use the -i argument but instead do something like this:

 ```
sed  s/2/o/g yourfile.txt | sed s/4/6/g | sed s/x/y/g 
```

---

### Post by Arndt on 2007-02-20
> **2point0 said:**
> 
I can understand how to issue the commands as needed with sed to perform the actions requested with replacement but as far as a repeatable script, I am at a complete loss.  I've tried working off a few basic tutorials but it seems as though I can't even begin to write the script as I get:

 #!/bin/bash
bash: !/bin/bash: event not found



Are you given no directions at all as to how to what a script is and how to make one? From the above error message, I deduce that you have entered

!/bin/bash

at the prompt, and then your command shell, which is bash, complains that /bin/bash is not an event, because it takes commands starting with an exclamation point as references to previous events (see the manual for that).

A script is a file, with a particular kind of first line in it, and then made executable. The first line says which program is to be run and given the script as input. That line should indeed be #!/bin/bash in this case. After that line, enter all the commands you want the script to run.

---

### Post by LotsOfPhil on 2007-02-20
I wouldn't do what IVY suggested with the pipes.

I think what your prof is looking for is a file that says:
```

#!/bin/bash

sed -i operation1
sed -i operation2
...
sed -i operation_last

```

Then she can just take your script, run it and look at the output. If it matches, it's an A. If not, it's an F :)

---

### Post by Ramses de Norre on 2007-02-20
> **LotsOfPhil said:**
> I wouldn't do what IVY suggested with the pipes.

I think what your prof is looking for is a file that says:
```

#!/bin/bash

sed -i operation1
sed -i operation2
...
sed -i operation_last

```

Then she can just take your script, run it and look at the output. If it matches, it's an A. If not, it's an F :)

You'll have to specify the file in that script, so look for command line arguments with bash, I'd do it like this:

```
#!/bin/bash
sed -e 's/2/o/g' -i $1
sed -e 'operation2' -i $1
...
exit 0
```

The first has the command that was allready given as example as operator and $1 is a variable holding the first command line argument (which has to be the filename).
You could make the script faster with only one sed invocation as sed takes multiple operations too like this: ```
sed -e 'operation1' -e 'operation2' ... -i file
```
But make sure you comprehend the first version first.

---

### Post by The Tronyx on 2007-02-21
Thanks a lot for all the suggestions!  As of now I believe LotsOfPhil was correct with just what the professor is looking for.  Also since I'm not terribly advanced with this yet (as if you couldn't tell :)) I think i'll keep it as simple as I can, even though it may not be the quickest.

---

