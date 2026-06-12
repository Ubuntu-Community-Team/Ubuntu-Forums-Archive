---
title: "how i can execute bash commands in java?"
date: 2006-12-16
forum: Programming Talk
---

### Post by Arppa on 2006-12-16
ok.. i tried executing like this:

try {
        String command = "ls -al";
        Process perkele = Runtime.getRuntime().exec(command);
} catch (IOException e) {
}

compiler warns that local variable perkele is never read and compiles the code to bytecode.
when i execute bash command doesn't work ](*,)

---

### Post by kaamos on 2006-12-16
Great variable names. ;)

Try this: [http://www.java2s.com/Code/Java/Development-Class/Howtoexecuteanexternalprogram.htm](http://www.java2s.com/Code/Java/Development-Class/Howtoexecuteanexternalprogram.htm)

---

### Post by marco.catunda on 2006-12-16
I've used it
Runtime.getRuntime().exec( "comand" ).waitFor();

If you command is bash environment, not script. You have to prefix
with "/bin/bash -c comando".

--
Marco Catunda

---

### Post by Arppa on 2006-12-16
i can't understand what i do wrong.

import java.io.*;

class execute
{
	public static void main(String[] args) throws IOException
	{
		try {
		Runtime.getRuntime().exec("/bin/bash -c ls -al").waitFor();
		} catch (InterruptedException e) {}
	}
}

---

### Post by Ramses de Norre on 2006-12-16
To get the output you'll need to create a Reader to read the InputStream from the process, like this for example:
```

import java.io.*;

public class List
{
	public static void main(String[] args)
	{
		try
		{
			Process proc=Runtime.getRuntime().exec("ls -al /");
			BufferedReader read=new BufferedReader(new InputStreamReader(proc.getInputStream()));
			
			while(read.ready())
			{
				System.out.println(read.readLine());
			}
		}
		catch(IOException e)
		{
			System.out.println(e.getMessage());
		}
	}
}

```

---

### Post by lloyd mcclendon on 2006-12-16
^ wow that is a pain in the ***

don't get me wrong i might be the biggest java zealot on here, but sometimes it's just rediculous to do simple common things.  i don't care for python but they've definately got a leg up on java in stuff like this, x = os.popen('ls -l')

if all you're doing is trying to get a directory listing, using java's file api would be much much easier.  also that bash stuff isn't portable either but you probably don't care about that

---

### Post by Ramses de Norre on 2006-12-16
In fact there are only a few really important lines, the rest is only there to make it a real program. This is enough in a method:

```
Process proc=Runtime.getRuntime().exec("ls -al /");
BufferedReader read=new BufferedReader(new InputStreamReader(proc.getInputStream()));
while(read.ready())
{
	System.out.println(read.readLine());
}


```

And the fact that you use a Reader to parse the output gives you a lot more options to process it than the python method does.

If you don't need output it's even simpler: ```
Runtime.getRuntime().exec("command");
```

And for listing there are indeed better builtins:
```
File file=new File("/home/");
String[] str=file.list();
for(int i=0;i<str.length;i++)
{
    System.out.println(str[i]);
}
```

---

### Post by Arppa on 2006-12-16
i need more than basic file listing. for example i need somehow to clean screen using clear -command. but if somebody knows a better way to clean screen that would help me very much.. :-k

---

### Post by Ramses de Norre on 2006-12-16
You can't really clear a terminal, even bash' clear just moves all previous lines outside the terminal window, but they are still visible when you scroll.

So you've got to either reset the terminal (which would kill the java app) or print newlines or something.. It's not a very clean solution but that's how terminals work I guess.

---

### Post by maddog39 on 2006-12-16
Well, you could probably just truncate the string buffer, cant you?

---

### Post by tommmmmm on 2011-10-05
this is a top notch result from google and after 5 years it has no definite working solution on how to do it !!! Shame on you forum users !

```

 public static void bashTest() 
    {
        try
        {
            Process proc = Runtime.getRuntime().exec("/home/bartosz/test.sh /");
            BufferedReader read = new BufferedReader(new InputStreamReader(proc.getInputStream()));
            try
            {
                proc.waitFor();
            }
            catch(InterruptedException e) {
                System.out.println(e.getMessage());
            }
            while(read.ready())
            {
                System.out.println(read.readLine());
            }
        }
        catch(IOException e)
        {
            System.out.println(e.getMessage());
        }
    }

```

now... that ! works like a charm

---

### Post by ofnuts on 2011-10-05
> **tommmmmm said:**
> this is a top notch result from google and after 5 years it has no definite working solution on how to do it !!! Shame on you forum users !

```

 public static void bashTest() 
    {
        try
        {
            Process proc = Runtime.getRuntime().exec("/home/bartosz/test.sh /");
            BufferedReader read = new BufferedReader(new InputStreamReader(proc.getInputStream()));
            try
            {
                proc.waitFor();
            }
            catch(InterruptedException e) {
                System.out.println(e.getMessage());
            }
            while(read.ready())
            {
                System.out.println(read.readLine());
            }
        }
        catch(IOException e)
        {
            System.out.println(e.getMessage());
        }
    }

```now... that ! works like a charm

Actually, this code won't work if the process produces more than 4K of outpu (not speaking of stderr output...). You have to be able to read the output while the process is running (ie, use a thread for stdout, one for stderr, and one for waitFor()).

---

### Post by tommmmmm on 2011-10-07
> **ofnuts said:**
> Actually, this code won't work if the process produces more than 4K of outpu (not speaking of stderr output...). You have to be able to read the output while the process is running (ie, use a thread for stdout, one for stderr, and one for waitFor()).

You are (probably right). There are 2 other reasons why this won't work:
1. stderr is misplaced than stdout. You either read one first then the other. Normal bash script produces errors when it sees them not at the beginning/end of the script
2. You absolutely CAN'T parse spaced arguments to get opts. Like this:
script.sh -f "super cool"
won't work. Java sends it always as script.sh -f \"super cool\" 
which doesn't work at all.

So.... the topic is still open?
 ANyone can help? I've been fighting this for over last 4 hours with no results

---

### Post by karlson on 2011-10-07
> **tommmmmm said:**
> 
 ANyone can help? I've been fighting this for over last 4 hours with no results

I am rather curious as to why would one want to run BASH script from Java rather then just rewriting the BASH script into native Java code.

But if you are so hellbent on doing this take a look at ProcessBuilder and Process classes in Java.

[http://download.oracle.com/javase/1.5.0/docs/api/java/lang/ProcessBuilder.html](http://download.oracle.com/javase/1.5.0/docs/api/java/lang/ProcessBuilder.html)

---

### Post by ofnuts on 2011-10-07
Hazy memory, but:

> **tommmmmm said:**
> You are (probably right). There are 2 other reasons why this won't work:
1. stderr is misplaced than stdout. You either read one first then the other. Normal bash script produces errors when it sees them not at the beginning/end of the script
If you use threads to start read loops on both outputs it should work.
> **tommmmmm said:**
> 2. You absolutely CAN'T parse spaced arguments to get opts. Like this:
script.sh -f "super cool"
won't work. Java sends it always as script.sh -f \"super cool\" 
which doesn't work at all.
Use **[%29"]exec]("http://download.oracle.com/javase/6/docs/api/java/lang/Runtime.html#exec%28java.lang.String[)**([String]("http://download.oracle.com/javase/6/docs/api/java/lang/String.html")[] cmdarray)  with one argument per array element. No need to further quote/escape arguments with spaces or special characters.

---

