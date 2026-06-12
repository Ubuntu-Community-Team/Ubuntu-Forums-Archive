---
title: "Create file via eval and read via cat"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by HeXor0815 on 2011-11-14
Hello everyone!

I am having some problems using some BASH commands...

As far as I understood, the function cat is used to split a string into its components, also reading a file.

Using a file test.txt with the content
```
This is a test file
with 2 lines
```The following code produces:
```

for word in `cat test.txt`; do
  echo $word
done

This
is
a
test
file
with
2 
lines
```I now have a more complex example, where I create a string, and evaluate this one using the eval function. This command returns output, which I want to save in a logfile, so I pipe the output into a file named log.txt using the > operator.

```

cmd="some command text, and this commands returns output"

eval $cmd > log.txt

for word in `cat log.txt`; do
  echo $word
done
```The problem I have here is, that the cat command does not split my output file log.txt into the different words, but generates one BIG output of the whole file content. So it somehow simply displays the output, but does not split it up. 

If I move the for loop into a separate bash file and evaluate this one after the creation of the file, it works fine. But I need to create several of these files, so I need to combine these steps...
I really don't see the mistake here, can you help me, please?

---

### Post by WasMeHere on 2011-11-14
Hi HeXor0815,

Welcome to the Ubuntu Forums!

I think you should browse for bash tutorials on the internet and do some basic exercises. It is not that difficult. After a while you will even be able to stand the manual ```
man bash
```. For one particular bash command you can type for example ```
help read
```

But you may still need to ask questions here ;-)

Back to your specific question:

***cat*** is actually copying the content of file(s) to the standard output. If there are many files they are put directly after each other, i.e con***cat***enated.

***tr*** can be used to change all instances of one character to another.

Try the following command to break lines of several words into a column with one word in each line
```
cat test.txt |tr '\ ' '\n'
```
```
tr '\ ' '\n' < test.txt
```
Have fun finding out :-)
Olle

---

### Post by HeXor0815 on 2011-11-14
Actually I have quite some experience with bash, but I put this in this section, because I hope (and think) that it's a quite simple problem, which I am just too blind at the moment to find a solution for.

I know I could also read different lines and then split these up into different words, but actuallay cat offers exactly the functionality which I need, as stated in the simple example.

I just don't understand or don't see why it doesn't work in the second case, where I just pipe the output of the command into a textfile, and then try to read this textfile.

The textfile exists, and is fine, and as stated a simple for loop with cat works perfectly on this one, but it DOESN'T work if it is put together in the same script with the creation of the textfile.


Might there be some connection with the eval function!?

---

### Post by WasMeHere on 2011-11-14
Let us analyze```
for word in `cat test.txt`; do
  echo $word
done
```
1. [FONT="Courier New"][SIZE="3"]cat test.txt[/SIZE][/FONT] creates a list of words with several spaces and one newline.

2. The ***for-loop*** picks one word each time and echoes it to the terminal. Each echo output ends with a newline. Cat does ***not*** do it.

[I]Edit: It is good practice to use citation marks "" around the variable, e.g.
"$cmd", in order to avoid surprises due to spaces in the string. The different behaviour in your examples could be due to that. Looking at the two files
[FONT="Courier New"]test.txt[/FONT] and
[FONT="Courier New"]log.txt[/FONT]
with a hex editor may disclose a 'hidden' difference[/I]

---

### Post by WasMeHere on 2011-11-14
> **HeXor0815 said:**
> ...
Might there be some connection with the eval function!?

***eval*** is executing its argument(s) as a shell command. It is combining all the arguments to one single string (instead of several separate arguments).

Is that what you want? Please explain what you want to do, then it will be easier to help.

---

### Post by dave0109 on 2011-11-14
Why are you using eval?

Is there a reason why you can't just run the command as is?

```

cmd="some command text, and this commands returns output"
$cmd > log.txt

```

---

### Post by HeXor0815 on 2011-11-14
Well it is a bit more complicated...


I create a CMD string, which then is evaluated. This string calls a  function foo with some parameters added using --option strings.

```

CMD="foo --option1 value1"
CMD=$CMD" --option2 value2"
CMD=$CMD" --option3 value3"
(and so on)
```Then I move to another directory

```

cd another/directory/somewhere/
```And then comes the evaluation and the readout

```

eval "$CMD" > log.txt

for word in `cat log.txt`; do
  echo "$word"
done
```And that's it. The output generated by the function is something like:

```
param1 : value1
param2 : value2
param3 : value3
(and so on)
```Using the cat I want to read in these parameter values  again, but as I said, the cat in the for-loop with the echo $word  simply gives me one output with all the parameters NOT split up. Calling  the for loop in a another file using the same log.txt works fine.



> **dave0109 said:**
> Why are you using eval?
Is there a reason why you can't just run the command as is?
```

cmd="some command text, and this commands returns output"
$cmd > log.txt

```

I also tried this, but it seems cause of the complextiy of the function call with so many parameters ,this doesn't work. At least it didn't when I tested it.

---

### Post by WasMeHere on 2011-11-14
Maybe this link will help you
[[COLOR="RoyalBlue"]_http://www.linuxjournal.com/content/bash-preserving-whitespace-using-set-and-eval_[/COLOR]]("http://www.linuxjournal.com/content/bash-preserving-whitespace-using-set-and-eval")
If no luck there, you will find other links describing how to use ***eval***.

---

### Post by HeXor0815 on 2011-11-15
Hm.. this doesn't really solve it either...
The commaned is evaluated fine, thats not the problem.

Maybe I should be more specific with the output:
```

  skip ['.o', '.a', '.so'] ./main.o
  (more lines like this)
  skip large file ./aff23508-3329-48ec-8479-e4732e1ccafd/sources.361fca69-e903-4cbc-915f-3326f519fbb2.tar:15349760B>1048576B
  (also such long lines)
===================
 JobsetID  : 5XX
 JobID  : 5XX
 Status : 0
  > build
    PandaID=135XXXX043
  > run
    PandaID=135XXXX044-135XXXX119
```Might there be any character combination causing problems?

---

### Post by WasMeHere on 2011-11-15
```
grep -e " : \|ID=\| > " test.txt
```
gives me the following output (from a file with your code from the previous post)
```
 JobsetID  : 5XX
 JobID  : 5XX
 Status : 0
  > build
    PandaID=135XXXX043
  > run
    PandaID=135XXXX044-135XXXX119
```
Is that what you want?

Explanation: [FONT="Courier New"]" : \|ID=\| > "[/FONT] is a regular expression to find lines with
[I]space-colon-space
ID=
space-greaterthan-space[/I]
So you can change the output by changing the regular expression to what you want (as long as you want the whole lines)

---

### Post by HeXor0815 on 2011-11-15
In particular I need the JobSetID 5XX.

So you think I should somehow use grep and not cat ?

---

### Post by WasMeHere on 2011-11-15
> Re: Create file via eval and read via cat
In particular I need the JobSetID 5XX.

So you think I should somehow use grep and not cat ?
```
grep -e "JobSetID" test.txt
``` will give you that information, at least from your file. Try it :-)

---

### Post by HeXor0815 on 2011-11-15
This doesn't work either...

If I use this small script just with the line you posted and use it on my outputfile it works fine, as already stated. But it doesn't work in the script where I create the outputfile, here it creates a blank line and doesn't grep anything.

Is there any issue with the log.txt being busy or something? I just create it in the script, so it may not be properly closed or anything like this? Thats the only thing I can think of...

---

### Post by dave0109 on 2011-11-15
Does the test.txt file reside on local disc, or is it some remote filesystem?

---

### Post by HeXor0815 on 2011-11-15
It is a remote system.

I am sitting at a university, logging in on a terminal, connecting to the local working grid, and there perform my jobs.

---

### Post by WasMeHere on 2011-11-15
0. Insert the command ***sync*** to your script between writing the file and reading from it. Maybe it helps.

I can think of two different routes to a solution.

1. To modify as little as possible in your original script.

2. To do the job in a different way, for example by several scripts working along side by side using the time-sharing or multi-thread capability of the computer.

---

### Post by sisco311 on 2011-11-15
Check out: [http://mywiki.wooledge.org/DontReadLinesWithFor](http://mywiki.wooledge.org/DontReadLinesWithFor)
and BashFAQ 001, 048 and 050 (link in my signature)

'eval' is a common misspelling of 'evil'. :evil:

---

### Post by HeXor0815 on 2011-11-16
First of all, sisco311, awesome BashFAQ. It answers many questions and is easy to understand, great job!

Finally one of your workarounds did the job for me:

```

  while IFS= read -r line; do 
    if [[ $line =~ "JobsetID" ]]; then
      JobSetID=${line:13:5}
      break
    fi
  done < log.txt
```Although the procedure of preparing the function arguments in an array and hand these to the function foo didn't work out for me:

```
  
args=()
args+=("--option1 value1")
args+=("--option2 value2")
args+=("--option3 value3")

foo "${args[@]}" > log.txt
```The resulting string is correct, but somehow the function doesn't properly recognize these arguments anymore. Strange behaviour...

Thank you very much, both sisco311 and Olle Wiklund. Great and very helpful support, go on with it! I surely will come back for it ;-)

---

