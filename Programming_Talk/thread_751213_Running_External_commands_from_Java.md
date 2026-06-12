---
title: "Running External commands from Java"
date: 2008-04-10
forum: Programming Talk
---

### Post by brennydoogles on 2008-04-10
I am a very new Java Programmer (in my first semester Java class at the University), and I am looking to expand upon What I am able to do with Java, by combining my knowledge of BASH with Java. I would like to do this by learning to run terminal commands from my Java Methods, but I have no idea how to start with that, and it could very well be beyond my grasp with what I know right now. As an Idea about what I would like to do, I want to convert [THIS]("http://brennydoogles.pastebin.com/fc1fdf91") BASH script I wrote into Java, and from there add functionality based upon new things I learn. Any help would be greatly appreciated!!!

---

### Post by samjh on 2008-04-10
You'll need to look at the Runtime class: [http://java.sun.com/javase/6/docs/api/java/lang/Runtime.html](http://java.sun.com/javase/6/docs/api/java/lang/Runtime.html)

Pay particular attention to the exec() methods.

This might be particularly useful for you if you have problems with using Runtime.exec(): [http://www.javaworld.com/javaworld/jw-12-2000/jw-1229-traps.html?page=1](http://www.javaworld.com/javaworld/jw-12-2000/jw-1229-traps.html?page=1)

---

### Post by brennydoogles on 2008-04-10
So using the exec() function, would it be best to run the command and all arguments as one string, or should I use an array? I haven't used arrays yet (although I have a little bit of experience with them from a few PHP tutorials), but I am a pretty fast learner. Thanks!

---

### Post by heikaman on 2008-04-10
here's an example:

[PHP]
import java.io.IOException;
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class test{
	public static void main(String[] args){
		Process ls=null;
		BufferedReader input=null;
		String line=null;
		
		    try {

		           ls= Runtime.getRuntime().exec(new String[]{"ls", "-l"});
		           input = new BufferedReader(new InputStreamReader(ls.getInputStream()));

		        } catch (IOException e1) {
		            e1.printStackTrace();  
		            System.exit(1);
		        }
		        
		       
		       try {
		       		while( (line=input.readLine())!=null)
		        		System.out.println(line);

		        } catch (IOException e1) {
		            e1.printStackTrace();  
		            System.exit(0);
		        }        
	}
	
}
[/PHP]

---

### Post by brennydoogles on 2008-04-10
Hmmm..... is it a bad sign that most of that is over my head?

---

### Post by heikaman on 2008-04-10
> **brennydoogles said:**
> Hmmm..... is it a bad sign that most of that is over my head?

no, it's a sign that you need to read a Java book :mrgreen:

BTW: close this thread :
[http://ubuntuforums.org/showthread.php?t=741104](http://ubuntuforums.org/showthread.php?t=741104)

---

### Post by brennydoogles on 2008-04-10
> **heikaman said:**
> no, it's a sign that you need to read a Java book :mrgreen:

BTW: close this thread :
[http://ubuntuforums.org/showthread.php?t=741104](http://ubuntuforums.org/showthread.php?t=741104)

Thanks, I had forgotten to mark that one!! 

Since I have only had one semester of Java (my only formal experience with programming) I realize that there is still soooo much to learn, but it's sometimes a good Idea to get exposure to things that are over your head so that they are not completely foreign when you go to learn them the correct way. Thanks all for your help!

---

### Post by samjh on 2008-04-10
> **brennydoogles said:**
> So using the exec() function, would it be best to run the command and all arguments as one string, or should I use an array? I haven't used arrays yet (although I have a little bit of experience with them from a few PHP tutorials), but I am a pretty fast learner. Thanks!

If you look at heikaman's example, he uses a String array to pass the "ln -l" command to exec():```
ls= Runtime.getRuntime().exec(new String[]{"ls", "-l"});
```This part is the String array:
new String[] {"ls", "-l"}

But he's made it slightly difficult to read by creating a new String object within the exec() method call itself.

A clearer snippet might be:
```

String [] mycommand = {"ls", "-l"};
...
blah
...
ls = Runtime.getRuntime().exec(mycommand);
```

I've only ever used exec() with single commands, not commands and their arguments.  Can't be bothered to install the JDK to experiment, unfortunately. ;)

---

### Post by pmasiar on 2008-04-10
Of course it might be interesting to run bash from Java, but Java was not designed to be used that way, IMHO. Java was designed to be OS by itself, so simpler is from java to read/write files and script the rest by scripting language, like bash or Python.

Best tool for the job: combine multiple tools to accomplish task in a simplest way. If you have only hammer, everything looks like a nail. Of course you may have legitimate task to do it that way, and it is good learning experience, but don;t expect that any single language will solve all your problems all the time.

---

### Post by heikaman on 2008-04-10
> **samjh said:**
> 
I've only ever used exec() with single commands, not commands and their arguments.  Can't be bothered to install the JDK to experiment, unfortunately. ;)

I found a JDK laying around :) so i've tested it before posting, works fine. It seems that exec() searches the standard PATH.

---

### Post by samjh on 2008-04-10
> **pmasiar said:**
> Of course it might be interesting to run bash from Java, but Java was not designed to be used that way, IMHO. Java was designed to be OS by itself, so simpler is from java to read/write files and script the rest by scripting language, like bash or Python.

Best tool for the job: combine multiple tools to accomplish task in a simplest way. If you have only hammer, everything looks like a nail. Of course you may have legitimate task to do it that way, and it is good learning experience, but don;t expect that any single language will solve all your problems all the time.
The OP has already stated he wishes to "expand upon what I [he] is able to do with Java", and that he is taking his "first semester Java class at University".  Using a language other than Java, is not going to help him achieve the former or latter.  Just a quick glance at his post already shows he is familiar with bash scripting.

---

### Post by ghostdog74 on 2008-04-12
after you had learnt how to run external commands, in the future, unless the external command you want to call is proprietary, otherwise, try not  to call external commands unnecessarily. It leads to portability issues. just for your case, if you want to get directory listings, use Java's own methods . [An example ]("http://exampledepot.com/egs/java.io/GetFiles.html")

---

