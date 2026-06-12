---
title: "Musing on the limit of class hierarchy size in Java"
date: 2009-01-20
forum: Programming Talk
---

### Post by stairwayoflight on 2009-01-20
Hi everyone.

I'm playing with Java right now, and I wondered about a way to time inherited method execution. So I wrote a bash script that generated a 1,000,000 class hierarchy (.java files only). Compiling the first one took over 3 seconds, so I decided to compile as I go. Each class simply "extends" the previous one. The first class has one dummy method, "frobnicate," which does--you guessed it--nothing.The classes are all named Progger1, Progger2, Progger3...Progger1000000.

When I started the script, it took ~.5s to compile a Progger[n].java file. Now its taking ~13s for files ~Progger17000.java.
I found even executing
```
Progger4096 progger = new Progger4096();
progger.frobnicate();
```
gives me a stack overflow. I'm not sure what the theoretical limits are for these things, but my bash script is running right now and seems like it has gotten no errors. I have compiled every class up to 17000 so far. But trying to compile Progger16384.java from the command line gave me a stack overflow also.

Any comments on Java, the Java compiler, or my <egad!> Bash script are welcome.

Progger1.java:
```
class Progger1
{
  public void frobnicate()
  {
  }
}
```

progger.bash:
```
#!/bin/bash
# Progger.bash -- test theory about Java hierarchy and performance, ie. see
#	long it takes to traverse up the hierarchy to find a method and
#	execute it.

PART1="class Progger"
PART2=" extends Progger"
PART3="{\n}"
NUMCLASSES=1000000

# Copy the Progger1.java file to tmp/.
mkdir 'tmp/'
`cp Progger1.java tmp/`

for ((filenum=1;filenum<=NUMCLASSES+1;filenum+=1))
do
  echo "filenum: $filenum"
  # Generate the Java file, and compile.
  case $filenum in
    $NUMCLASSES+1)
      ;;
    $NUMCLASSES)
      ;;
    *)
      filenum2=$(( filenum + 1 ))
      echo -n $PART1 > "tmp/Progger$filenum2.java"
      echo -n $filenum2 >> "tmp/Progger$filenum2.java"
      echo -n "$PART2" >> "tmp/Progger$filenum2.java"
      echo $filenum >> "tmp/Progger$filenum2.java"
      echo "{" >> "tmp/Progger$filenum2.java"
      echo "}" >> "tmp/Progger$filenum2.java"
      cd 'tmp/'
      echo "compiling Progger$filenum.java!"
      echo -n "javac Progger$filenum.java: " >> time.log
      { time javac "Progger$filenum.java"; } >> time.log
      cd '..'
  esac

  # Move everything back. Note the java file being compiled and the previous
  # one must be in the tmp/ folder to compile properly.
  case $filenum in
    1)
      ;;
    2)
      ;;
    *)
        #mv "tmp/Progger$((filenum - 2)).java" './'
        #mv "tmp/Progger$((filenum - 2)).class" './'
  esac
done
```

---

