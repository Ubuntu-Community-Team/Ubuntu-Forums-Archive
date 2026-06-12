---
title: "File system gui"
date: 2009-03-02
forum: Programming Talk
---

### Post by ashwinkumar18 on 2009-03-02
hi


Is it possible to create a gui for the ubuntu file system like a file browser?? if so where do i begin?

---

### Post by roshanjose on 2009-03-02
ohhhh you dont have to create anything. You just open you web browser and open a perticular location....and lo you get your directory of files

---

### Post by Simian Man on 2009-03-02
A *lot* of file browsers already exist.  What do you want to accomplish?

---

### Post by ashwinkumar18 on 2009-03-02
i am trying to use an alternative mode of input ....i need to operate on the gui of the file browser with the help of the inputs which i give rather than the keyboard and mouse...

---

### Post by Simian Man on 2009-03-02
Well, to create a file browser from scratch, you would need to know a programming language and a toolkit such as GTK for the GUI.  It's probably not as simple as you imagine.  I'm curious, however, what kind of input methods are you talking about?

---

### Post by ashwinkumar18 on 2009-03-02
am sorry for the incomplete info i have given... i need to develop it using java ..i mean i want to know if its possible ...iam new to linux and further my inputs would be the co ordinates i get from screen ....

---

### Post by ashwinkumar18 on 2009-03-02
if its probably tuf as u say suggest me an open source browser which i can modify easily...

---

### Post by bobmatino17 on 2009-03-02
just type in 
```
nautilus
```
from the terminal
or use sudo if you a gui adminastrative file browser

---

### Post by ashwinkumar18 on 2009-03-02
k wil try..thanks for the reply!!

---

### Post by cph05a on 2009-03-02
If you really wanted to build your own GUI File browser (for the educational benefit) it's really not that hard. Your program can navigate files in your computer the same way you navigate them from your terminal. Here is a simple program which reads the contents of its present working directory and prints them in stdio:

```
#include <stdlib.h>
#include <stdio.h>

int main()
{
	char str[128];
	FILE *tempfile;

	(void)system("ls -1 ./ > tempfile.txt");
	tempfile = fopen ("tempfile.txt","r+");

	while (!feof(tempfile))
	{
		fscanf(tempfile, "%s", str);
		printf("In this dir: %s\n", str);
	}

	(void)system("rm tempfile.txt");
}

```

You can navigate, launch programs, or anything else you can do from the terminal in this way. Just add your GUI code. It shouldn't be too difficult.

---

### Post by cph05a on 2009-03-02
here's the java version:

```
import java.io.*;
import java.util.Scanner;

public class PrintDir 
{
	public static void main(String[] args)
	{
		Runtime rt = Runtime.getRuntime();
		
		try
		{
			Process process = rt.exec("ls -1 ./");
			BufferedReader input = new BufferedReader(new InputStreamReader(process.getInputStream()));
			 
                        String line=null;
            
                        while((line=input.readLine()) != null) 
                        {
                               System.out.println("In this dir: " + line);
                        }

		}
		catch (Exception e)
		{
			e.printStackTrace();
		}
	}
}
```

---

