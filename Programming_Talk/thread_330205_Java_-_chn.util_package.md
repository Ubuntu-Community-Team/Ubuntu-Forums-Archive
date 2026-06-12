---
title: "Java - chn.util package"
date: 2007-01-02
forum: Programming Talk
---

### Post by crackling on 2007-01-02
How do I get the chn.util package and other java packages that I might need? I'm new to Ubuntu so thorough explainations please :]. Here's the code and errors I get if anyone is interested.

```
import chn.util.*;
public class test {
	public static void main (String args[]) {
		ConsoleIO kb = new ConsoleIO();
		System.out.println("Enter number.");
		int num = kb.readInt();
		System.out.println(num);
	}
}
```

```
test.java:1: package chn.util does not exist
import chn.util.*;
^
test.java:4: cannot find symbol
symbol  : class ConsoleIO
location: class test
                ConsoleIO kb = new ConsoleIO();
                ^
test.java:4: cannot find symbol
symbol  : class ConsoleIO
location: class test
                ConsoleIO kb = new ConsoleIO();
                                   ^
3 errors
```

Thanks in advanced.

---

### Post by welshboy on 2007-01-03
Firstly, you'll need to add the .jar file to the program's class path, you could do this by using:

javac -cp \[location of jar] classname.java and then run it using the same command (java -cp etc...)

However, you've not told me which editor you're using.  If you use Eclipse, then it's a bit easier, you add the .jar file to the project.

To do that, you right click on the project that you want to add the file to, and then select properties.

And then select build path, and add the jar there, using add external jar. [I've attached a screen shot]

Or I think, I may need to be corrected on this!!!!!  SO please check with someone else!!

you can edit the class path in /etc/environment to do that type in sudo gedit(or your choice of editor) /etc/environment, and then add the directory to the CLASSPATH descriptor.

Hope this helps.

You can message me if you have more hassles.

---

### Post by welshboy on 2007-01-03
I also learned another thing just now as a matter of fact.

According to a book I'm reading, you could put the .jar files into a folder called ext in your java folders, which will be here (if you installed from repos)

/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext$


According to my book at least, it means that the .jars will be found automatically by the compiler.  

However I think you'd need to be a super user to copy files to it

so you'd do
emyr@Wookie:~$sudo cp util.jar/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext$

And then that should prompt you for your password, and then copy the jar file to the folder.

Hope that helps a bit too :S

welshboy

Again, I'm going by what the book tells me.

---

### Post by crackling on 2007-01-03
I'm using gedit for programming right now. Also, I found chnutil.jar I just can't seem to move it into the right directory, it says I don't have the right permissions.

```
 sudo cp chnutil.jar/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext
cp: missing destination file operand after `chnutil.jar/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext'
Try `cp --help' for more information.

```

The line that you gave me doesn't seem to be working.

---

### Post by welshboy on 2007-01-04
> **crackling said:**
> I'm using gedit for programming right now. Also, I found chnutil.jar I just can't seem to move it into the right directory, it says I don't have the right permissions.

```
 sudo cp chnutil.jar/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext
cp: missing destination file operand after `chnutil.jar/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext'
Try `cp --help' for more information.

```

The line that you gave me doesn't seem to be working.

Sorry!  You need to have a space after the file name.

emyr@Wookie:~/dev/learning/java/ivor/TryGeometry/geometery$ sudo cp Geometry.jar /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/
Password:
emyr@Wookie:~/dev/learning/java/ivor/TryGeometry/geometery$ 

This worked fine on my machine.  Try it with the space, and let me know if it works or not :)

Many thanks.

---

### Post by crackling on 2007-01-04
It worked, thanks a bunch! By the way what does 'sudo cp' do? Copy and Paste?

---

### Post by Wybiral on 2007-01-04
"sudo" gives you superuser abilities so you can move things below your home folder, "cp" copies a file from one place to the next.

There's a couple of tutorials here:
[http://p13.wikispaces.com/Linux](http://p13.wikispaces.com/Linux)

"cp" is in the manipulating tutorial

And "sudo" is in the "permissions" tutorial

---

### Post by welshboy on 2007-01-04
I do appologise, I should have explained what the commands did!!

But Wybiral's explanation is spot on.  I'll be more mindful in future :s

welshboy

---

