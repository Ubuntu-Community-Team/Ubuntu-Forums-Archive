---
title: "Learning scripting and need help with commands"
date: 2007-12-04
forum: Programming Talk
---

### Post by thenetduck on 2007-12-04
Hi I am learning scripting (like everyone else on the planet that doesn't all ready know) and need to do a simple script. 

The script needs to open a file, search for a term change the term from "False" to "True" and save the file again in sudo mode. I think I can use grep to do this but I cam confused on how I can edit the file. What I mean is with grep I can search the file but I would like to edit the file Anyone know what kind of comand I should use to edit a file? 

Thanks!

The Net Duck

---

### Post by LaRoza on 2007-12-05
What language are you using?

---

### Post by davidgarcin on 2007-12-05
Wow, I'm on here too much.....

Anyway.  Have a look at gawk (GNU awk) in combination with the gsub function.  It's a little complicated, but it will do the trick.

---

### Post by LaRoza on 2007-12-05
<snip />

---

### Post by PointyWombat on 2007-12-05
Like most things *nix, there are many ways to skin the cat.. 

I recommend using sed. Here's an example something which will do what you're looking for, excluding running it as sudo.

You have a file named foo which contains the text:

```
The rain in Spain falls mainly on the plains.
It is true that the quick brown fox jumps over the lazy dogs back.
Now is the time for all good men to come to the aide of thier country.
```

But you want to change true to false in the second line, Using sed, this would be done with:

```
sed 's/true/false/' foo
```

This looks for all instances of the string 'true' and substitutes it with 'false'.

But what if you had two lines with the word true in it, but you only wanted to change the line with the word 'lazy' in it?

You search for the word 'lazy' in the file, then perform the substitution, such as with this sed command:

```
sed '/lazy/s/true/false/' foo
```

I would consider sed a must know for unix/linux users, you don't need to be an expert, just familiar with it. It is one of the most handy file manipulation tools available, along with awk.

If you have any questions, don't hesitate to ask.

---

### Post by thenetduck on 2007-12-05
Hey thanks. What does 's' mean in your command above? 

The Net Duck

---

### Post by thenetduck on 2007-12-05
nm, I think I understand it stands for search :)

Oops sorry for the double post

Also, PointyWombat thank you a bunch!

The Net Duck

---

### Post by PointyWombat on 2007-12-05
Not exactly. The 's' is for substitute. The first string "/lazy/" is what is searched for in the file. So with this:

```
sed '/lazy/s/true/false/' foo
```

means SEARCH for the string "lazy" in all lines of the file "foo", and if you find a line with the string 'lazy' in a line, SUBSTITUTE on that line the string 'true' with the string 'false'.

---

### Post by thenetduck on 2007-12-05
Ok did this ....

Saved as EditGrub.sh
```

sed '/s/alternative=true/alternative=false info.txt'

```

info.txt looks like this (this is a test file before I try it on grub)

```

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

```

Saved it and ran it sh EditGrub.sh 

This started to run, and didn't finish. Just stopped in the terminal. Did I do anything wrong? Do I need to call sed from a different directory? 

Thanks 

The Net Duck

=================================================

OK This is an update... I was able to get it to run (it outputs information? didn't know what) with this reversion of the script. Problem is, it didn't replace what I wanted. Maybe I wasn't specific enough.

```

#!/bin/bash
sed 's/alternative=true/alternative=false/' info.txt

```

===================================================
Update: 

Woot I got it to work! 
with this one ....

```

#!/bin/bash
sed 's/# alternative=true/# alternative=false/' info.txt
echo ' \n File Finished \n'

```

Ooo this is fun. I will read up. Thanks a million.. OH btw.. do you know how I might be able to edit a file that nees sudo rights to edit?

---

### Post by thenetduck on 2007-12-05
Dang it ... I lied. That output prints out the correct file I want but when I checked my info.txt it didnt' write it to the file. How can I take what I just made and write it back to the file? 

Thanks!

The Net Duck

============================
Update .. Figured it out

I needed to do

```

sed -i 'rest of the stuff' file 

```

to get things to work. Glorious. Now to get it to work in a sudo environment. hum....

======================
solution is just to type sudo infront of the command and run the sh script as sudo. 

The Net Duck

---

### Post by PointyWombat on 2007-12-05
Ok, so what I gave you was just a bit of what you need to do..

The sed statement just handles the text manipulation, you still need to take the manipulated text and save it to the file.. this also needs to happen in your EditGrub.sh script.

In order to change your file info.txt, you need to save the new output. We can do this with a redirection (**>**) to a new file, then copy that file into place. So with this in mind, your EditGrub.sh script could be something like:

```

#!/bin/sh
# Script to falsify alternative
#make a backup of the orig file
cp info.txt info.txt.orig

#modify the file and write output to new file
sed '/^alternative/s/true/false/' info.txt >info.txt.new

#rename new file to the original
mv info.txt.new info.txt

```

Now note here that this script expects that info.txt is in the same directory as the script itself. If it is not, you will need to fully path every file.

Also note that "# alternative=true" in your example  is only a comment, so it means nothing to grub. The example above expects that 'alternative' is not a comment and it at the very beginning of the line.

Finally, notice that the syntax of your sed statement is incorrect with the placement of the final **'** in that is needs to go before the filename.

---

### Post by stroyan on 2007-12-05
Adding a -i or --in-place option will cause sed to replace the original file contents
with the new file contents after substitution
```
#!/bin/bash
sudo sed -i 's/# alternative=true/# alternative=false/' info.txt
echo ' \n File Finished \n'
```

The "man sed" command will tell you about -i and other options.

---

### Post by PointyWombat on 2007-12-05
Ah, right stroyan, I'm old school.. I wish Solaris sed had the -i option... 


> **stroyan said:**
> Adding a -i or --in-place option will cause sed to replace the original file contents
with the new file contents after substitution
```
#!/bin/bash
sudo sed -i 's/# alternative=true/# alternative=false/' info.txt
echo ' \n File Finished \n'
```

The "man sed" command will tell you about -i and other options.

---

### Post by ghostdog74 on 2007-12-05
> **LaRoza said:**
> It would be much easier in Python or Perl.
that would be very subjective. A person who has been using Python/Perl most of  the time might find it easier. A person who shell script most of the time will find shell scripting easier..

---

### Post by PointyWombat on 2007-12-05
> ... do you know how I might be able to edit a file that needs sudo rights to edit?

as far as this goes, it depends. Is this something you are going to run manually and can be prompted by a password? In that case, simply run your script with sudo ( sudo EditGrub.sh )

If you need this to run without intervention, that's different. There may be a way to do it using sudo, but I'm not aware of it. The way I know is to run it as root in either a startup script or perhaps something else. Depends on what you're trying to solve for. Which is what, by the way?

---

### Post by pmasiar on 2007-12-05
> **ghostdog74 said:**
> that would be very subjective. A person who has been using Python/Perl most of  the time might find it easier. A person who shell script most of the time will find shell scripting easier..

Most beginners have hard time to wrap head around couple different languages. So doing it in universal language Python is almost as simple as sed, but without actual need to learn sed. Something like:

[php]
infile = open('foo.txt')
outfile = open('foo_replaced.txt', 'w')
for line in infile:
    line.replace('true', 'false')
    outfile.write(line)
infile.close()
outfile.close()
[/php]

This solution is also scalable: if I need to add more tricky logic. I can just do it instead of trying to trick sed doing it. 

If person is not full time sysadmin, and tasks like this are rare, her time is IMHO much better spend mastering single universal flexible ("scripting") language, than trying to be 'jack of all trades' (but master of none). IMHO, YMMV.

---

### Post by ghostdog74 on 2007-12-05
> **pmasiar said:**
> Most beginners have hard time to wrap head around couple different languages. So doing it in universal language Python is almost as simple as sed, but without actual need to learn sed. Something like:

[php]
infile = open('foo.txt')
outfile = open('foo_replaced.txt', 'w')
for line in infile:
    line.replace('true', 'false')
    outfile.write(line)
infile.close()
outfile.close()
[/php]

This solution is also scalable: if I need to add more tricky logic. I can just do it instead of trying to trick sed doing it. 

If person is not full time sysadmin, and tasks like this are rare, her time is IMHO much better spend mastering single universal flexible ("scripting") language, than trying to be 'jack of all trades' (but master of none). IMHO, YMMV.
I was contemplating on whether to post, since you are an avid Python fan and  almost nothing else, so even if i say you are not entirely right, it will be a waste of time. However I still want to express my views, that a good programmer learns to be adaptive and bends according to his/her environment.  If he/she is stuck with an environment that is Python-less, he/she can still survive, because he knows other tools that can also do the job as easily. Its a harsh world out there, still.  Whether or not a person becomes a sysadmin some day is not something one can foresee. Its still best to learn as much as possible, at the same time, strive to be a master of all trades, however daunting it may be.

---

### Post by thenetduck on 2007-12-05
> **PointyWombat said:**
>  Depends on what you're trying to solve for. Which is what, by the way?

I am creating this script for my old high school they just switch from Windows to Ubuntu for their computers (got rid of their former more expensive network man, and didn't want the kids installing Windows games). I was at work and being stupid, told one of the kinds how he could change the root password via Recovery mode or boot into rocovery mode from grub. I felt bad and am now repenting by making these scripts to prevent anyone from getting into the system  and changing the root passwd. I don't want them to have a bad first experience. Personally they should be using Edubuntu (seems easier out of the box for a school that should be using thin/fat server/client). 

So will now incorporate a password enabling script. 

That should do the trip. 

The Net Duck

---

### Post by lswest on 2007-12-05
you can probably write the script, and then just execute it with sudo?

---

### Post by pmasiar on 2007-12-05
> **ghostdog74 said:**
> I was contemplating on whether to post,

Please don't hesitate to post. I do have strong opinions - but (I hope) based on facts, and I am willing (eager) to learn new facts and adjust my opinion. But facts is what I want, no FUD or whining as in recent flamewar. 

> since you are an avid Python fan and  almost nothing else, 

I wish it was true!

I have to use Java and (gasp) ASP+VB at work. Python is only for my pet projects or if I behave! :-)

I also started programming way before Python, and used many many other languages. And my favorite pet "fun to use" language is Forth (and its recent reincarnation, Factor). Python is just my preferred daily tool, in no way the only tool I use.

> a good programmer learns to be adaptive and bends according to his/her environment.  

Nah, everybody knows that progress depends on people who **refuse** to adapt to environment, and change environment instead! </joke>


> If he/she is stuck with an environment that is Python-less, 

Of course do whatever works. 
But if you don't have Python, what are the chances you have sed?

I posted my example because IMHO for a beginner is better to become competent user of one universal tool, than half-learn dozen of specialized tools. Of course, if one kind of task will occupy 30% of your time, learning more specialized tool is in place - but not for one-off tasks.

> he/she can still survive, because he knows other tools that can also do the job as easily. Its a harsh world out there, still.  

Yup, only the most productive will survive. This is exactly why I love Python: I can go on solving problems without need to learn specialized tools. It fits my brain without need to constantly check manuals.

> Its still best to learn as much as possible, at the same time, strive to be a master of all trades, however daunting it may be.

Learning more - yes, daily, all the time.
Mastering it all - not for me, I gave up long time ago. Even with specialization, it still feels like drinking from a firehose. I try carefully distinguish between areas which I need to master, and which I can safely skip over without hurting my career.

Do whatever works for you. Python works for me. Writing above code sample took me less than reading sed manual, and I can enhance it easily if needed. 

Before you ask: yes, I know about sed - back in days I wrote my first trojan using bash and sed :-)

---

### Post by thenetduck on 2007-12-05
I tried the python but it does write the file corrently for me. I am using test files to make sure things work .Here is my code.

p.s. I as going to just us us sed for changing the password but I can't figure out how to set variables in shell... weird....

```

inputFile = open('testinfo.txt')
outputFile = open('testinfo_output.txt', 'w')
for line in inputFile:
	if line.replace('# password here', 'password there') :
		print "Line copied over"
	outputFile.write(line)
inputFile.close()
outputFile.close()	


```

this is what testinfo.txt looks like

```

## password here
password here
# password here

Try to change the password here to there

```

The Net Duck

---

### Post by pmasiar on 2007-12-05
my bad. line.replace() returns changed string, it does not update it in place... as we talked recently, strings are immutable! :-) doh!

you need instead: 

line = line.replace('old', 'new')

---

### Post by thenetduck on 2007-12-05
> **pmasiar said:**
> my bad. line.replace() returns changed string, it does not update it in place... as we talked recently, strings are immutable! :-) doh!

you need instead: 

line = line.replace('old', 'new')


many thanks to you and your leader!

Works like charm. I think I will give Python a go so I can see how everything works. 

Thanks!

The Net Duck

---

### Post by ghostdog74 on 2007-12-05
> **pmasiar said:**
> 
But if you don't have Python, what are the chances you have sed?

This will depend on the environment one is in. sed is installed by default in almost any *nix, at least more chances of it getting installed by default. However Python may not. It may come with the distribution, or be bundled in a companion CD , or may not at all.

---

### Post by PointyWombat on 2007-12-06
FWIW, I'm just gonna say that i've been employed as a unix (IRIX, HP-UX, Solaris) admin for 12+  years and no system I manage today has python installed on it, but every one of them has sed and awk.  I won't argure the merits of Python, but its definately not as ubiquitous as these native utils.

---

### Post by LaRoza on 2007-12-06
> **PointyWombat said:**
> FWIW, I'm just gonna say that i've been employed as a unix (IRIX, HP-UX, Solaris) admin for 12+  years and no system I manage today has python installed on it, but every one of them has sed and awk.  I won't argure the merits of Python, but its definately not as ubiquitous as these native utils.

sed is an editor, awk is for manipulating text. These would be useful for an admin, in the course of a job, but they are hardly useful for other things.

Python can be used for the same things, which may be easily done in other languages, and things that are impossible for those languages.

Is Perl on the systems you manage?

---

### Post by ghostdog74 on 2007-12-06
> **LaRoza said:**
> sed is an editor, awk is for manipulating text. These would be useful for an admin, in the course of a job, but they are hardly useful for other things.

you might want to rethink that concept.

> 
Python can be used for the same things, which may be easily done in other languages, and things that are impossible for those languages.

how about trying to list the processes on a system,  in the Python way, without the use of external modules like enumprocess or PSI ... simple job for Python?,right?

---

### Post by LaRoza on 2007-12-06
> **ghostdog74 said:**
> you might want to rethink that concept.


how about trying to list the processes on a system,  in the Python way, without the use of external modules like enumprocess or PSI ... simple job for Python?,right?

By "other things" I mean other things. Python can do a lot that they can't do.

I don't understand, Python is extensible, that is what makes it powerful. One can make a server with it easily using its modules. If you want to strictly compare Python and something else that has a highly specific purpose, Python would loose because Python doesn't have a specific purpose.

I always try to use the best tool for the task, and that means I am constantly learning new things, Python is the most useful tool for general tasks and I use other tools for what they are good at.

---

### Post by ghostdog74 on 2007-12-06
> **LaRoza said:**
> By "other things" I mean other things. Python can do a lot that they can't do.

what other things? maybe you can name a few?

---

### Post by pmasiar on 2007-12-06
> **PointyWombat said:**
> FWIW, I'm just gonna say that i've been employed as a unix (IRIX, HP-UX, Solaris) admin for 12+  years and no system I manage today has python installed on it, but every one of them has sed and awk.  I won't argure the merits of Python, but its definately not as ubiquitous as these native utils.

I see, you are one of non-PC unix sysadmins. I doubt it is more than 1% of total Linux/Unix market (and declining), and **not** something accessible for a beginner.

For a beginner, every PC-based Linux box **DOES** have a Python on it. When beginners becomes expert, and will shoot for a position of old Unix admin, can learn awk, sed etc. But why waste time on them before?

---

### Post by ghostdog74 on 2007-12-06
> **pmasiar said:**
> 
For a beginner, every PC-based Linux box **DOES** have a Python on it. When beginners becomes expert, and will shoot for a position of old Unix admin, can learn awk, sed etc. But why waste time on them before?

no its not a waste of time, because if that beginner  who knows shell scripts is so lucky as to take over as Unix admin  one day and have to maintain shell scripts written by people long ago before Python even existed, we will have a survivor here. again, you have a pretty "flawed" concept.  Again , not every situation is the same as yours, so please do not say its a waste of time.

---

### Post by LaRoza on 2007-12-06
> **ghostdog74 said:**
> no its not a waste of time, because if that beginner  who knows shell scripts is so lucky as to take over as Unix admin  one day and have to maintain shell scripts written by people long ago before Python even existed, we will have a survivor here. again, you have a pretty "flawed" concept.  Again , not every situation is the same as yours, so please do not say its a waste of time.

The average person doesn't become a Unix admin, by accident.

Not every situation is the same as yours....

---

### Post by ghostdog74 on 2007-12-06
> **LaRoza said:**
> The average person doesn't become a Unix admin, by accident.

The average person will become a *nix admin (eventually, if not)  when that person uses *nix. Whether he's *nix administrator by job nature, or using *nix at home as his OS of choice, or for whatever reasons. He will need to learn how to administrator that machine, somehow or rather.

---

### Post by pmasiar on 2007-12-06
> **ghostdog74 said:**
> Again , not every situation is the same as yours, so please do not say its a waste of time.

Well, I am part-time ubuntu user (and freely admit NOT experienced admin) and I do not plan to learn awk or sed, ever. And I think my situation is like 80% of other Linux users/developers: learn little bit of bash, ask for command tricks from old hands as you go, and program applications. At work, we have admin who knows what he does, but I do not plan to take over his responsibilities, and he does not want mine.

I gave up on learning every technology what flies around long time ago, now I try to select what I stuff  into my brains. 

I know not everyone is in situation like I am, but quite a lot of people are. And not everyone is in situation like you are either.

Unix collected a lot of tool during its long life (it is older than many of Linux users) and not all of them are worth using anymore. It is called "progress" :-)

I have no problem if you advise learn bash. But IMHO (YMMV) learning sed and awk before learning universal scripting language like Python (which can replace them) is waste of time - and even becoming deep expert of bash is waste for me. For me (YMMV) is simpler to manage files etc in Python than in bash.

BTW, I would recommend everyone struggling with commandline tools to learn mc (midnight commander) instead. With mc, one can do visually many many administration task which old-timers do in command line. Replaces many commandline tricks and tools, and is IMHO easy enough to learn. Of course weaseling out by mc will put on your head even more wrath of old-time *nix admins. :-) Also, without mc installed you will be even more lost :-)

---

### Post by slavik on 2007-12-07
> **pmasiar said:**
> I have no problem if you advise learn bash. But IMHO (YMMV) learning sed and awk before learning universal scripting language like Python (which can replace them) is waste of time - and even becoming deep expert of bash is waste for me. For me (YMMV) is simpler to manage files etc in Python than in bash.

I used to ask the same thing in my UNIX Shell Programming class. (except I used Perl).

The answer from the professor was "Don't use a sledgehammer to hammer in a small nail." I also believe that you agree to the "right tool for the right job." No?

slavik@slavik-desktop:~$ which sed; which python
/bin/sed
/usr/bin/python

ask your admin the difference between /bin and /usr/bin. :)

---

### Post by thenetduck on 2007-12-07
LOL you guys are funny I am actually enjoying reading this. It almost make's my day. Hum.... 

The Net Duck

---

### Post by pmasiar on 2007-12-07
> **slavik said:**
> 
ask your admin the difference between /bin and /usr/bin. :)

My guess is that difference between /bin/sed and /usr/bin/python is about 30 years? :-)

---

### Post by Wybiral on 2007-12-07
> **slavik said:**
> I used to ask the same thing in my UNIX Shell Programming class. (except I used Perl).

The answer from the professor was "Don't use a sledgehammer to hammer in a small nail." I also believe that you agree to the "right tool for the right job." No?

slavik@slavik-desktop:~$ which sed; which python
/bin/sed
/usr/bin/python

ask your admin the difference between /bin and /usr/bin. :)

I think the "right tool for the right job" concept is just to avoid having to hack things together or write code that's already written. In this case, Python has plenty of awesome file system and string manipulation tools, so you aren't doing any extra work.

It's "use right tool for the right job", not "use the tool whose only purpose is that job"... Big difference. As far as the sledge hammer analogy, I'd rather carry around a swiss army knife than a screwdriver, a compass, a file, and a knife :)

---

### Post by slavik on 2007-12-07
> **Wybiral said:**
> I think the "right tool for the right job" concept is just to avoid having to hack things together or write code that's already written. In this case, Python has plenty of awesome file system and string manipulation tools, so you aren't doing any extra work.

It's "use right tool for the right job", not "use the tool whose only purpose is that job"... Big difference. As far as the sledge hammer analogy, I'd rather carry around a swiss army knife than a screwdriver, a compass, a file, and a knife :)
Then I can argue that Perl is a better swiss army knife than Python, but we don't want that, trust me.

as to educate to the difference of /bin and /usr/bin ...

/bin is required to be there when your system starts /usr/bin is stuff that is not essential to the system which was installed with the system (/usr/local/bin contains non-essential stuff that was installed after the system was installed).

---

### Post by Wybiral on 2007-12-07
> **slavik said:**
> Then I can argue that Perl is a better swiss army knife than Python, but we don't want that, trust me.

I never said it was or wasn't. I was talking multiple independent programs vs a more complete package like Python. If you're good at Perl, I bet it is better than using all those little programs. But the Python vs Perl debate isn't necessary... Again...

---

### Post by slavik on 2007-12-07
good and
ps aux | grep -i username

is better than using Perl or Python to list all processes run by the user 'username'

---

