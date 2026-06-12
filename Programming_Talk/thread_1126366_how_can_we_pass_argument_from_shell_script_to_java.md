---
title: "how can we pass argument from shell script to java program"
date: 2009-04-15
forum: Programming Talk
---

### Post by shishir_knit on 2009-04-15
how can we pass argument from shell script to java program

i have to send an array from shell script to java program

---

### Post by Arndt on 2009-04-15
> **shishir_knit said:**
> how can we pass argument from shell script to java program

i have to send an array from shell script to java program

The same way as with any program, I suppose. Each element in the array as one command line argument. Or perhaps the whole array as a string, as one argument, but that means more unpacking on the Java side.

What does your array look like?

---

### Post by shishir_knit on 2009-04-15
in shell script ihav got this

array=(`ls -B`)

now i hav to send this array to java code

---

### Post by Arndt on 2009-04-15
> **shishir_knit said:**
> in shell script ihav got this

array=(`ls -B`)

now i hav to send this array to java code

Does the Java code already exist, or are you to write it first?

---

### Post by shishir_knit on 2009-04-15
i hav already got java code on path

/Desktop/project/project/guip.class

please give shell code

as well as how to recieve the arguments in java code

---

### Post by Arndt on 2009-04-15
> **shishir_knit said:**
> i hav already got java code on path

/Desktop/project/project/guip.class

please give shell code

as well as how to recieve the arguments in java code

Now, I can't read your files, so it doesn't help to tell me what the file is called. In what form does that class want its input?

I suggest you read the section headed "Arrays" in the bash manual page.

A third way which occurred to me would be to pass the array to the Java program through a pipe, and it could read the data from stdin.

---

### Post by simeon87 on 2009-04-15
```
public static void main(String[] args) {}
```

args contains the command-line arguments.

---

### Post by Copernicus1234 on 2009-04-15
Hello,

Try this to understand it better.

Create bash script file with this content:

```

dirs=`ls -1B`

java JTest $dirs

```

Create java program named JTest.java with this and compile:

```

public class JTest
{
        public static void main( String[] args )
        {
                for (int i=0;i<args.length;i++)
                {
                System.out.println(args[i]);
                }
        }
}

```

Run the bash script file. The bash script file will do the ls -1B do get a list of all directories and you then send this list to the java program.

As you can see, the java program loops through the list of directories and prints out their names.

Good luck!

---

### Post by shishir_knit on 2009-04-15
thanks copernicus ur answer is really good
but don't want the java program to be executed while passing the argument

---

### Post by shishir_knit on 2009-04-15
i wan to run the shell script from java
and want the arguments throgh that script

which i can use in my java code

---

### Post by quaternion on 2009-04-15
You want to **exec**ute a shell command within a Java program and save the output for processing? 

Please see: [http://www.ensta.fr/~diam/java/online/io/javazine.html](http://www.ensta.fr/~diam/java/online/io/javazine.html)
For an explanation and example.
Now I am going to post a question about printing... if someone could help me that would be great =)

---

