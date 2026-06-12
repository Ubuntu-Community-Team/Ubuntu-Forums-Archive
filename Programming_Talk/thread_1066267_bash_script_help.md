---
title: "bash script help"
date: 2009-02-10
forum: Programming Talk
---

### Post by andrewoftheelves on 2009-02-10
Hello, 
First of all, let me say that I am inexperienced. I am making a bash script to create makefiles to compile .java files to .class files, as a  means of convenience, and to show my stupid teacher that ides are stupid(vim for life) haha. I am having trouble with the for loop, so any help would be appreciated. And I would love any suggestions to make it better.

[PHP]#!/bin/bash
#accepts the argument of the directory that your files are in
#creates a simple java makefile and exectues that file

cd $1 # change into directory
> makefile # start with new makefile

echo "JFLAGS = -g" >> makefile
echo "JC = javac" >> makefile
echo ".SUFFIXES: .java .class" >> makefile
echo ".java.class:"  >> makefile
echo -e "	\$(JC) \$(JFLAGS) \$*.java" >> makefile
echo "" >> makefile
echo "CLASSES = \ " >> makefile
index = 0
for myfile in *.java

do
	if[$index -eq 0]
	then
		echo "	$myfile \\" >> makefile
	else
		index = $index+1
		echo "$myfile \\" >> makefile
	fi
done
echo "" >> makefile
echo "default: classes" >> makefile

echo -e "classes: \$(CLASSES:.java=.class)" >> makefile

echo "clean:" >> makefile
echo -e "	\$(RM) *.class" >> makefile

make
[/PHP]

---

### Post by eightmillion on 2009-02-10
I see a couple of problems here. You brackets can't be up against your conditional statement. Also, that's not the way to increment a variable in bash. You need to use something like ((index++)) or index=$((index+1)) and you can't have spaces around the equals sign in a bash variable assignment, so "index = 0" needs to be "index=0". Try this:
```

index=0 
for myfile in *.java

do 
    if [ $index -eq 0 ] 
    then 
        echo "    $myfile \\" >> makefile 
    else 
        ((index++)) 
        echo "$myfile \\" >> makefile 
    fi 
done

```

---

### Post by lloyd_b on 2009-02-10
(Other than issues already noted by eightmillion)

One thing I really don't understand:
```
index = 0
for myfile in *.java

do
    if[$index -eq 0]
    then
        echo "    $myfile \\" >> makefile
    else
        index = $index+1
        echo "$myfile \\" >> makefile
    fi
done
```exactly when is $index *not* going to equal 0?  From what I can tell, the only thing that can change this value from 0 is the else clause, which will never be executed...

Also, the exlicit "> makefile" to create an empty makefile really isn't required - just change the "echo "JFLAGS = -g" >> makefile" to "echo "JFLAGS = -g" > makefile", and you'll be guaranteed to wipe out any existing makefile.

Lloyd B.

---

### Post by jpkotta on 2009-02-11
This looks like a job for here documents.

[http://www.gnu.org/software/bash/manual/bashref.html#Redirections](http://www.gnu.org/software/bash/manual/bashref.html#Redirections)
[http://tldp.org/LDP/abs/html/here-docs.html](http://tldp.org/LDP/abs/html/here-docs.html)

---

### Post by geirha on 2009-02-11
Does the makefile have to look "good"?. Instead of looping through all the java-files, why not just [php]echo "CLASSES =" *.java >> Makefile[/php]

The makefile should have a captial 'M' btw.

---

### Post by andrewoftheelves on 2009-02-18
Thanks everyone for your help, especially geirha. Here is the script if anyone is interested. 
[PHP]#!/bin/bash
#accepts the argument of the directory that your files are in
#creates a simple java makefile and exectues that file

cd $1 # change into directory

echo "JFLAGS = -g" > Makefile
echo "JC = javac" >> Makefile
echo ".SUFFIXES: .java .class" >> Makefile
echo ".java.class:"  >> Makefile
echo -e "       \$(JC) \$(JFLAGS) \$*.java" >> Makefile
echo "" >> Makefile
echo "CLASSES = " *.java >> Makefile

echo "" >> Makefile
echo "default: classes" >> Makefile

echo -e "classes: \$(CLASSES:.java=.class)" >> Makefile

echo "clean:" >> Makefile
echo -e "       \$(RM) *.class" >> Makefile

make
[/PHP]

---

