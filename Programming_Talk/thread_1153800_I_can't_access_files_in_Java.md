---
title: "I can't access files in Java"
date: 2009-05-09
forum: Programming Talk
---

### Post by cobolt01 on 2009-05-09
I've moved my entire school project over from windows to linux, moved the database from access to MySQL and after hours of struggling to get the program to access MySQL, it not won't access my config files.
I have a line accessing the file, then on the following line where the file is read, there's a null pointer exception. It works under windows, so there's nothing wrong with my code.
I've tried changing permissions but im not sure if im doing it right.
The project is due for 20 July and moving it over to Linux has taken nearly a week out of my development time already.

---

### Post by cl333r on 2009-05-09
By not posting your project/code we can only guess what's the matter, so I would strongly recommend attaching your project or at least the files that matter.

---

### Post by cobolt01 on 2009-05-09
> **cl333r said:**
> By not posting your project/code we can only guess what's the matter, so I would strongly recommend attaching your project or at least the files that matter.

It's not really a Java coding problem though. But ok.

[PHP]
TextCommunicator sTC = new TextCommunicator("s_fullscreen.stmd");
		fullScreen = Integer.parseInt(sTC.readLine());
		dc.write("Fullscreen = "+fullScreen);
		
		sTC = new TextCommunicator("s_firstStart.stmd");
		firstStart = Integer.parseInt(sTC.readLine());
		dc.write("FirstStart = "+firstStart);
		
		sTC = new TextCommunicator("s_devConsole.stmd");
		devConsole = Integer.parseInt(sTC.readLine());
		dc.write("DevConsole = "+devConsole);
[/PHP]
TextCommunicator object constructor
[PHP]
	public TextCommunicator(String fName)
	{
		try
		{
			f = new File(fName);
			br = new BufferedReader(new FileReader(f));
		}
		catch(FileNotFoundException fnf)
		{
			JOptionPane.showMessageDialog(null, "Error. File not found.\nYou may have deleted a file essential for this program to operate");
		}
		
	}
[/PHP]
readLine() method
[PHP]
public String readLine()
	{
		try
		{
			br = new BufferedReader(new FileReader(f));
		}
		catch(FileNotFoundException f)
		{
			displayFileNotFoundException();
		}
		catch(IOException e)
		{
			displayIOException();
		}
		//------------------------
		String ret = "";
		try
		{
			ret = br.readLine();
		}
		catch(IOException w)
		{
			displayIOException();
		}
		//--------------------------
		try
		{
			br.close();
		}
		catch(IOException e)
		{
			displayIOException();
		}
		return ret;
	}
[/PHP]

That's basically the parts im using. But like I said, it works in windows. my files just cant be found/accessed in Linux.

---

### Post by cl333r on 2009-05-09
I'm almost sure the issue is with java's "current working directory" (CWD) because based on it java constructs the whole path to the file in cases like yours when you only feed the file name (without the path to it).

Thus, you need to check whether the CWD is not what you expect it to be.
If the error happens in the constructor, change the constructor:

```

 public TextCommunicator(String fName)
    {
        try
        {
            f = new File(fName);
            br = new BufferedReader(new FileReader(f));
        }
        catch(FileNotFoundException fnf)
        {
            JOptionPane.showMessageDialog(null, "No file at: " + f.getPath() );
        }
        
    }  

```
it will report the whole path to the file and will give you a good clue what's the matter.

PS:
"f = new File(fName)" - should be the source of troubles

PPS:
Sorry, replace f.getPath() with f.getAbsolutePath()

---

### Post by cobolt01 on 2009-05-09
Thanks for your reply.
f.getAbsolutePath() returns the correct path to where the file is. So I don't think its a pwd problem. It just seems like my app isn't allowed to access the file or there is something else preventing communication.

---

### Post by cl333r on 2009-05-09
> I have a line accessing the file, then on the following line where the file is read, there's a null pointer exception.
The stack trace could yield details (exc.printStackTrace()). But again, we can only guess since we can't reproduce it.

---

### Post by dwhitney67 on 2009-05-09
What are the permissions set on the file?  Can you open it from the terminal or file-browser?

---

### Post by cobolt01 on 2009-05-09
> **cl333r said:**
> The stack trace could yield details (exc.printStackTrace()). But again, we can only guess since we can't reproduce it.

Reproducing this would take ages, its not a simple compile and run. And once again, it's not a coding related problem as we've established.

I can open the files with kate and print them with cat from dolphin and the terminal.
The files have permissions -rwxrwxrwx
I don't really understand Linux permissions, so advice on this would be great. My Java classes have the permission -rw-rw-rw.

---

### Post by cl333r on 2009-05-09
I understand that. But a null pointer exception is thrown in your code, the stack trace should explain _why_ it is thrown. Regardless, neglecting the results of the stack trace isn't the best strategy to solve problems, that's usually the first thing a (Java) programmer examines.

> it's not a coding related problem as we've established.
It depends on how you look at it. For example, if something is written in Java and runs on windows it doesn't yet mean it's written correctly (in a cross-platform way).

---

### Post by cobolt01 on 2009-05-09
You make an excellent point. Do you think maybe you could write the simplest program that reads from a file as an example? Then maybe we can see the differences and understand if that's where i went wrong.

---

### Post by dwhitney67 on 2009-05-09
Here's a simple program:
```

import java.io.File;
import java.io.FileReader;
import java.io.BufferedReader;


class FileDisplayer
{
  public FileDisplayer() {}

  public void TextCommunicator(String fName)
  {
    try
    {
      File file = new File(fName);
      BufferedReader in = new BufferedReader(new FileReader(file));
      String line;

      while ((line = in.readLine()) != null)
      {
        System.out.println(line);
      }
    }
    catch (Exception e)
    {
      e.printStackTrace();
    }
  }

  public static void main(String[] args)
  {
    FileDisplayer fd = new FileDisplayer();
    fd.TextCommunicator(args[0]);
  }
}

```

To build/run:
```

javac FileDisplayer.java
java FileDisplayer <file>

```
where <file> is the file you want to open/read.

P.S.  Note that creating a File() object is an unnecessary step; one can just as easily pass the filename 'fName' to the FileReader() object that is created.

---

### Post by cl333r on 2009-05-09
If you need to display the stack trace in a dialog, you might use a helper method to extract the trace from the exception like this one:

```

public static final String getFormattedTrace(Exception exc) {
	StackTraceElement[] elems = exc.getStackTrace();
	StringBuilder sb = new StringBuilder("\n");

	for (StackTraceElement e : elems) {
		sb.append("at " + e.getClassName() + "." + e.getMethodName() +
				"()    Line: " + e.getLineNumber() + "\n");
	}

	return sb.toString();
}

```

and then like:
```

} catch (Exception exc) {
	JOptionPane.showMessageDialog(null, "Stack trace: " + getFormattedTrace(exc));
}

```

---

### Post by cobolt01 on 2009-05-09
I found the problem
[PHP]
TextCommunicator sTC = new TextCommunicator("s_fullscreen.stmd"); 
[/PHP]
the file is s_fullScreen.stmd not s_fullscreen.stmd

Windows is not case sensitive and Linux is. 
Small problem in the end.

---

