---
title: "Java execute shell commands?"
date: 2008-01-29
forum: Programming Talk
---

### Post by aktiwers on 2008-01-29
What is the simplest way I could run bash scripts or shell commands using Java?

I tried with exec, but it wont even accept the 'cd' command..  

Anyone know a simple way to do this? If I could just get it to run a bash script, I could put all my commands in there.

Thanks

---

### Post by popch on 2008-01-29
At a guess I would think that you execute the program 'bash' from java and pass it the commands you want executed in a file or pipe.

---

### Post by a9bejo on 2008-01-29
cd is not a separate program like ls or wc, but a command directly build into many command like interpreter (like bash).

So Runtime#exec  is the way to go, but you cannot change the working directory of the java process this way.  What you can do is to use Runtime#exec to call a script that opens a shell and then execute a set of commands in that shell, including cd.

---

### Post by kozmo on 2008-09-24
import java.lang.*    ;

public class MyJavaClass
{
   public void runCmd(String[] args)
   {
      String  cmd = "/home_dir/./my_shell_script.sh" ;
      Runtime run = Runtime.getRuntime() ;
      Process pr = run.exec(cmd) ;
      pr.waitFor() ;
      BufferedReader buf = new BufferedReader( new InputStreamReader( pr.getInputStream() ) ) ;

      while ( ( String line ; line = buf.readLine() ) != null ) 
      {
	 System.out.println(line) ;
      }

   }

}

---

### Post by tinny on 2008-09-25
Here is some code that does what you want

[http://ubuntuforums.org/showpost.php?p=5409831&postcount=19](http://ubuntuforums.org/showpost.php?p=5409831&postcount=19)

---

### Post by jespdj on 2008-09-25
A more flexible way than Runtime.exec(...) to do this is to use the class java.lang.ProcessBuilder. Look it up in the Java API documentation.

*edit* Oh wait, who are we fooling? This is a 9 month old thread...

---

### Post by tinny on 2008-09-25
> **jespdj said:**
> A more flexible way than Runtime.exec(...) to do this is to use the class java.lang.ProcessBuilder. Look it up in the Java API documentation.

*edit* Oh wait, who are we fooling? This is a 9 month old thread...

:lolflag:

oops

---

### Post by hoboy on 2008-09-25
Try this link maybe
[http://www.beanshell.org/docs.html](http://www.beanshell.org/docs.html)

---

