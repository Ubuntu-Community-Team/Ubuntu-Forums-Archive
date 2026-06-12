---
title: "xemacs and java question"
date: 2007-02-07
forum: Programming Talk
---

### Post by soapytheclown on 2007-02-07
okay well it seems a long shot, but im not sure where else to ask, but i got xemacs from the repos, as this is what im programming in at uni. and whenever i try to compile java it says that 

"the JDE does no recognize JDK 1.5 javac. Assume 1.4 javac?" 

which to be honest, i dont know what differences there are between the two, apart from 1.5 is obviously newer. 

If i choose yes, then apparently nothing happens and no kind of compilation box comes up and no class file is made. 

im guessing if i have 1.5 this will be solved, and after looking through what i can understand of xemacs, the compiler code is actually javac so im kinda stumped. 

can someone help pleaseee

thanks

---

### Post by phossal on 2007-02-08
I'm not sure what your question is exactly. If you're certain you have the JDK installed, and not just the JRE, you simply need to include the path to the JDK in the $PATH environment variable. Without knowing for certain that you have a JDK installed, and without knowing *where* you installed it, it's tough to give you the exact commands needed to correct the problem. 

The command *javac -version* gives output showing which version of javac (effectively the JDK) you're using. 

For more help, you need to confirm you've installed the JDK, and tell us where it's installed.

---

### Post by maxamillion on 2007-02-08
I am assuming you simply missed one of the steps listed here [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0)

But I could very well be incorrect.

---

### Post by phossal on 2007-02-08
Rather than downloading the OOD JDK 5.0 package, if he's going to have to go through a similar series of steps anyway, why not recommend that he grab version 6 right from SUN?

---

### Post by soapytheclown on 2007-02-08
okay the command...

nash@Dragon:~$ javac -version
javac 1.5.0_08

I installed the Java JDK and JRE from automatix, so im assuming that my java is installed under

/usr/lib/jvm/java-1.5.0-sun

any help :S ?

---

### Post by phossal on 2007-02-08
I don't understand the question. If you can call javac -version from the command line, why aren't you able to compile anything? The second question is why aren't you using an IDE?

---

### Post by soapytheclown on 2007-02-08
im not entirely sure, i can compile fine from terminal, but its a lot less hassle doing it in xemacs, so my actual question is, how do i set up xemacs with java? because from what i was informed of (from my lecturers) was that install java JDK and install xemacs from the repos and it works.

obviously the interface looks exactly the same but im guessing that theres something ive missed while setting it up?

any more help (im a noob as you can tell) would be appreciated

---

### Post by lnostdal on 2007-02-08
i've done very little java, but for the little i've done i've used scons to call javac and in general handle compilation

in `ubuntu-programming2.pdf' i've described how to set up emacs and scons for C programming:
[http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/)

the same will work for java, only the SConstruct-file must be a bit different.. a SConstruct-file like this will compile each .java-file in your directory:
```

Java('.', '.')

```

if i after saving this SConstruct file add a file Hello.java in the same directory with the following code in it:
```

class Hello {
  public static void main(String args[]) {
    System.out.println("Hello World!");
  }
}

```

..then press F5 while in the buffer-- i'll end up with a Hello.class file which i can execute:

```

lars@ibmr52:~/programming/java$ java Hello 
Hello World!

```

..so it's basically exactly the same setup as i use when compiling C programs as described in the short tut i link to above - except some changes in the SConstruct file ...... easy :)

for more details about the scons/SConstruct -stuff (if you want to compile more complicated java-projects) you'll probably find good info in the scons-manual

---

