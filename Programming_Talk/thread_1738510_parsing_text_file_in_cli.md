---
title: "parsing text file in cli"
date: 2011-04-24
forum: Programming Talk
---

### Post by lsmobrian on 2011-04-24
I'd like to parse a text file and was hoping it could be just a line on the command line. Here is an example input


foo abcddefgh 123456
bar asdfasdfasdf 67676767676
!some other string
#some other stuff commented out
#foo wqerqwer 958686 
#bar lololol  3456345

Here is psuedo code for what i want

```

for line in file:
  if line.beginsWith("bar") OR line.beginsWith("foo"):
    line = line.split(' ')[0]+
      someexternalcommand(line.split(' ')[1])+
      line.split(' ')[2]
  print(line)

```

Was wondering what kind of magical cli command I could do instead.  awk or sed maybe?

---

### Post by kurum! on 2011-04-24
I don't even understand your pseudocode (which should be as english as possible) especially the someexternalcommand part. Show your desired output and describe clearly your problem again.

---

### Post by lsmobrian on 2011-04-24
Sorry, bit I think thats perfect pseudo code


But youre right i did leave out the end result.  If its a line that begins with foo or bar i want to pass the middle token to another program and replace it with that output. uppercase for example  `tr 'a-z' 'A-Z'`


foo ABCDDEFGH 123456
bar ASDFASDFASDF 67676767676
!some other string
#some other stuff commented out
#foo wqerqwer 958686
#bar lololol 3456345

---

### Post by d3v1150m471c on 2011-04-24
it'd be easier if you told us exactly what you're trying to accomplish.

edit, this should do the trick...
```

for i in `cat file`; do
 [[ $i == foo* ]] && echo $i | cut -d' ' -f2 >> newfile
 [[ $i == bar* ]] && echo $i | cut -d' ' -f2 >> newfile
done

```

---

### Post by Telengard C64 on 2011-04-24
I didn't understand your *perfect pseudo-code* either  :confused:

> **lsmobrian said:**
> If its a line that begins with foo or bar i want to pass the middle token to another program and replace it with that output. uppercase for example  `tr 'a-z' 'A-Z'`

Here is one possible AWK solution:
```
foo$ cat input_file
foo abcddefgh 123456
bar asdfasdfasdf 67676767676
!some other string
#some other stuff commented out
#foo wqerqwer 958686
#bar lololol  3456345
foo$ awk '/^(foo|bar)/ {$2 = toupper($2)} ; {print}' input_file
foo ABCDDEFGH 123456
bar ASDFASDFASDF 67676767676
!some other string
#some other stuff commented out
#foo wqerqwer 958686
#bar lololol  3456345
foo$
```

---

### Post by lsmobrian on 2011-04-24
Thanks for the reply, thats basically what im looking for, but i want to run $2 through an arbitrary command, not necessarily toupper().  I see awk has system() but I havent had any luck assigning the output of the command to $2, its always the return value of the exiting command

---

### Post by lsmobrian on 2011-04-24
Going with this

```
perl -e 'while($line=<STDIN>){chomp $line; if($line =~ m/(foo|bar) ([^ ]+) (.*)/){ print "$1 ", `echo -n $2 | tr [:lower:] [:upper:]`, " $3\n"}}else{ print "$line\n" }' < input.file >> output.file
```

---

### Post by kurum! on 2011-04-25
> **d3v1150m471c said:**
> it'd be easier if you told us exactly what you're trying to accomplish.

edit, this should do the trick...
```

for i in `cat file`; do
 [[ $i == foo* ]] && echo $i | cut -d' ' -f2 >> newfile
 [[ $i == bar* ]] && echo $i | cut -d' ' -f2 >> newfile
done

```
this would not really do the trick

---

### Post by kurum! on 2011-04-25
> **lsmobrian said:**
> Thanks for the reply, thats basically what im looking for, but i want to run $2 through an arbitrary command, not necessarily toupper().  I see awk has system() but I havent had any luck assigning the output of the command to $2, its always the return value of the exiting command

you can get the return output like this inside awk.
```

command="my command"
command |getline output
print output

```

---

### Post by Telengard C64 on 2011-04-25
> **lsmobrian said:**
> Thanks for the reply, thats basically what im looking for, but i want to run $2 through an arbitrary command, not necessarily toupper().  I see awk has system() but I havent had any luck assigning the output of the command to $2, its always the return value of the exiting command

I'd look into [gawk coprocesses](http://www.gnu.org/software/gawk/manual/gawk.html#Two_002dway-I_002fO)

---

### Post by kurum! on 2011-04-25
*duplicate*

---

### Post by kurum! on 2011-04-25
> **lsmobrian said:**
> Going with this

```
perl -e 'while($line=<STDIN>){chomp $line; if($line =~ m/(foo|bar) ([^ ]+) (.*)/){ print "$1 ", `echo -n $2 | tr [:lower:] [:upper:]`, " $3\n"}}else{ print "$line\n" }' < input.file >> output.file
```

you do know that Perl switch -n can simulate going through a file using a while loop right? Also, why the need to call external commands? If you want to use Perl, then use its features that are already available. lc() and uc() are the methods to change cases. There is also an inbuilt tr function. see the Perl doc for more information.

For the record, here's a Ruby alternative

```

$> ruby -ane '$F[1].upcase! if /^(foo|bar)/ ;puts $F.join(" ")' file
foo ABCDDEFGH 123456
bar ASDFASDFASDF 67676767676
!some other string
#some other stuff commented out
#foo wqerqwer 958686
#bar lololol 3456345


```

---

### Post by Telengard C64 on 2011-04-25
> **kurum! said:**
> ```
command="my command"
command |getline output
print output

```

Nice! This seems to work well enough for what I think OP wants.

```
foo$ awk 'BEGIN {cmd="tr a-z A-Z"} ; /^(foo|bar)/ {("echo "$2" | "cmd) | getline $2} ; {print}' input_file
foo ABCDDEFGH 123456
bar ASDFASDFASDF 67676767676
!some other string
#some other stuff commented out
#foo wqerqwer 958686
#bar lololol  3456345
foo$
```

All you need to do is put whatever command you want between the quotes in **cmd=""**. The command must accept data on its standard input and produce data on its standard output. So this also works.

```
foo$ awk 'BEGIN {cmd="sed s/d/./g"} ; /^(foo|bar)/ {("echo "$2" | "cmd) | getline $2} ; {print}' input_file
foo abc..efgh 123456
bar as.fas.fas.f 67676767676
!some other string
#some other stuff commented out
#foo wqerqwer 958686
#bar lololol  3456345
foo$
```

Rock on, AWK!
:guitar:

---

### Post by lsmobrian on 2011-04-25
OOOHHHH, I was so close, but gave up to early and settled for that perl. I do like your solution Telengard better and I'll use it instead.  Thanks a bunch.  Didn't know about the getline option, thats what was killing me.  

The external command is some string operation program that is internal to this project im working on.  so me using uppercase was a terrible example, sorry for that, i should have said something that was more complicated that a language woudln't support.

---

### Post by Telengard C64 on 2011-04-25
> **lsmobrian said:**
> The external command is some string operation program that is internal to this project im working on.  so me using uppercase was a terrible example, sorry for that, i should have said something that was more complicated that a language woudln't support.

In most cases if all you need is string transformations then you really ought to stick with pure AWK/SED/Bash or whatever. It is much more graceful, more efficient, and easier to maintain code in your language of choice than it is to pipe your data between multiple commands.

In the Gawk manual they use the example of a database server to explain the how and why of piping data into and out of external programs. A pre-existing database server is not something you might want to, or be able to, rewrite in AWK from scratch.

[3.8.7 Using getline from a Coprocess](http://www.gnu.org/software/gawk/manual/html_node/Getline_002fCoprocess.html#Getline_002fCoprocess)

By the way, I only recently began playing with AWK pipes myself. Don't trust my solution to be robust and scalable until you study and test it for yourself. (YMMV)  :popcorn:

One more thing in the way of disclaimers. I tested this in Mawk 1.3.3 and Gawk 3.1.6. Other implementations of AWK may behave differently.

---

