---
title: "BASH scripting question this is driving me nuts, well kinda"
date: 2007-03-02
forum: Programming Talk
---

### Post by statictonic on 2007-03-02
#!/bin/bash
MESSAGES=$(awk -F'from | port....' '/Invalid user/{printf $2 "\n" }' messages.htm)
echo -e $MESSAGES

Alright so the problem I have is I need that to output as a list(one IP address per line).  However instead it throws all the IP address's it pulls out of a file into a space separated mess.  If I run that awk command normally without assigning it to a variable it works perfectly fine and they each get their own line.

Anyways I need it to show one item per line, so that this will in theory work with it as well.

#!/bin/bash
MESSAGES=$(awk -F'from | port....' '/Invalid user/{printf $2 "\n" }' messages.htm)
DONE=$(echo -e $MESSAGES | sort -u )

So it will sort them and remove duplicates.

Any help would be greatly appreciated :)

---

### Post by Mr. C. on 2007-03-02
The shell converts each newline into a single space when assigned to a variable:

# cat x
1
2
# a=`cat x`
# echo $a  
1 2

You're going about the problem the wrong way.  Use pipelines instead of assigning to a variable.

  x | y | z

---

### Post by s1ightcrazed on 2007-03-02
Mr. C is correct - any reason why this can't be done one at a time in a loop?

Here's the other option:

$ echo $TEST
1 2 3

$ echo $TEST | sed 's/ /\n/g'
1
2
3

When you use the variable, if you need the output at that point to be line by line, just replace the blanks with newline characters by piping it through sed. It's U G L Y and I wouldn't really recommend it, unless for some reason you absolutely need to do it this way. It's not bad, per se, it's just that there is probably a better way to do what you are trying to do without resorting to sed. 

Enjoy.

---

### Post by Mr. C. on 2007-03-02
Again, lets be careful to clarify for everyone that as a general solution, this shortcut won't work:

# cat anddog
this is line 1
line 2
this is the line called 3

# test=`cat anddog`
# echo $test | sed 's/ /\n/g'
this
is
line
1
line
2
this
is
the
line
called
3

---

### Post by statictonic on 2007-03-02
Thanks a ton for the help so far, I've got another question though.  I'm trying to use comm -32, to compare the output of a command with a file, and whatever is in that file needs to be deleted from the output of the original awk command.  Now comm seems ideal to do such a thing, comm -3 will supress lines that appear in both files, which is good and -2 will supress the second file which is also good.  Works perfect if I simply use two files, now how would I get it to work from the results of an awk command.  I can't seem to pipe to it..

---

### Post by mynamewastaken on 2007-03-03
statictonic fails at bash.

---

### Post by Mr. C. on 2007-03-03
> **statictonic said:**
> Thanks a ton for the help so far, I've got another question though.  I'm trying to use comm -32, to compare the output of a command with a file, and whatever is in that file needs to be deleted from the output of the original awk command.  Now comm seems ideal to do such a thing, comm -3 will supress lines that appear in both files, which is good and -2 will supress the second file which is also good.  Works perfect if I simply use two files, now how would I get it to work from the results of an awk command.  I can't seem to pipe to it..

These sound like homework questions.  Show what you have thus far.

---

### Post by statictonic on 2007-03-03
MESSAGES=$(comm -32 "awk -F'from | port....' '/invalid user/{printf $2 "\n" }' messages2.htm | sort -ub" /etc/firewall/whitelist )
comm -32 $MESSAGES /etc/firewall/whitelist

where I'm at as of now, is there a way I can pipe the output of MESSAGES=$ to comm or is there something better than comm I can use to do the same thing.

---

### Post by Mr. C. on 2007-03-03
I'm not understanding what you are really trying to do.  Perhaps it would be best to show some sample input, and sample output of what you'd like.  Then we can discuss the best tools for the job.

---

### Post by statictonic on 2007-03-03
> **Mr. C. said:**
> I'm not understanding what you are really trying to do.  Perhaps it would be best to show some sample input, and sample output of what you'd like.  Then we can discuss the best tools for the job.
awk -F'from | port....' '/invalid user/{printf $2 "\n" }' messages2.htm | sort -ub"
comm -32 $MESSAGES /etc/firewall/whitelist


Alright, I'm trying to take the output of that, and compare it against another file.  Any lines that are in both files need to be deleted.  The second file also does not need to be displayed at all.

Note these are condensed examples so it's not a giant mess on the forum.
I just made a few files to test this out this would be the file that it will be comparing against(this would be an actual text file):
192.168.1.1
192.168.1.8
192.168.0.10

Against the output of awk -F'from | port....' '/invalid user/{printf $2 "\n" }' messages2.htm | sort -ub
The output is 
127.0.0.1
192.168.0.12
192.168.0.9
192.168.1.1

Now what I would like to achieve would be that after running comm or whatever I'd need to is that 192.168.1.1 is no longer in the bottom list since it's displayed in the top one.  The output of the command must not display any of the top list, but only use it to choose what to delete in the bottom list.

If these were both text files all I would have to do would be run a command such as: comm -31 file1 file2 to achieve results that I need.  I can't find a way to use comm in a script though.

Any suggestions on how to pipe to comm or another way to go about doing this would be awesome, thanks for the help so far.

---

### Post by Mr. C. on 2007-03-03
You cannot use comm on the receiving end of a pipeline.  It doesn't take STDIN; it requires two files.

Place your output into two temporary files and run comm with the correct arguments.

MrC

---

