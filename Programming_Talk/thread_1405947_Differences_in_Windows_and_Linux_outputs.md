---
title: "Differences in Windows and Linux outputs"
date: 2010-02-13
forum: Programming Talk
---

### Post by vgokul on 2010-02-13
Hello all,
            I have a bunch of files using which I create an exe in Windows (VC++ 2005 express) and also an exe in Linux(gcc - 4.2.4). I provide the same dat file input to both the executables. 
             I log the inputs and outputs from both the exe and while the inputs are matching there are differences in the outputs. In general are differences in outputs in Windows and Linux expected? Are there any specific options that can reduce these differences?
 
Regards
V.Gokul

---

### Post by Jonas thomas on 2010-02-13
I'm by no means an expert,  one issue is that you need to pause the output in VC terminal session which is not the case in Gnu g++.

---

### Post by vgokul on 2010-02-13
Just to clarify "differences" - In both cases I write (using fprintf) mostly datatype double outputs to a file and then compare the results at each timestep. Their I see differences between the values from Windows and Linux at the same time step and same inputs

---

### Post by Zugzwang on 2010-02-13
There are some differences you have to expect:

[LIST]
[*]Note that the line break character is different ("\r\n" vs. "\n")
[*]The default precision for printing out double values might be different on both platforms. Also, values might be rounded when reading them from file. Rounding might go into the other direction.
[*]The compilers might perform different optimizations, which might influence the numerical stability of the algorithms you implemented.
[*] Of course, if you use random numbers and similar stuff, results will differ.
[/LIST]

---

### Post by Enrui on 2010-02-13
> **Zugzwang said:**
> There are some differences you have to expect:

[LIST]
[*]Note that the line break character is different ("\r\n" vs. "\n")
[/LIST]


Please note this isn't always the case. I've used \n on numerous operating systems. (MS 98, MS XP, MS Vista, Linux Ubuntu) and it's always done the same thing. 

"data\nmoredata"

shows as

data
moredata 

I believe it operates differently on a mac however, the one brand I've sworn never to use. Usually its the compiler/ide that has the problem depending on the operating system rather than the operating system itself. 

Just my opinion and my experience.

---

### Post by LKjell on 2010-02-13
> **Enrui said:**
> Please note this isn't always the case. I've used \n on numerous operating systems. (MS 98, MS XP, MS Vista, Linux Ubuntu) and it's always done the same thing. 

"data\nmoredata"

shows as

data
moredata 

I believe it operates differently on a mac however, the one brand I've sworn never to use. Usually its the compiler/ide that has the problem depending on the operating system rather than the operating system itself. 

Just my opinion and my experience.

The compiler might be smart enought to map \n to the right line break format. However if you read from files it might be different. You might have to read in '10' for \n

---

### Post by vgokul on 2010-02-15
Thank you all
 
> **Zugzwang said:**
> There are some differences you have to expect:

[LIST]
[*]Note that the line break character is different ("\r\n" vs. "\n")
[*]The default precision for printing out double values might be different on both platforms. Also, values might be rounded when reading them from file. Rounding might go into the other direction.
[*]The compilers might perform different optimizations, which might influence the numerical stability of the algorithms you implemented.
[*]Of course, if you use random numbers and similar stuff, results will differ.
[/LIST]
Neither do I use any random numbers nor default precision for printing. The break characters are also not a problem with the dat files. But the output values printed out in both cases are different(inputs are ok). Do you have any suggestions that I should try out , perhaps some compiler switches?

---

### Post by mdurham on 2010-02-15
> **vgokul said:**
> Thank you all
 

Neither do I use any random numbers nor default precision for printing. The break characters are also not a problem with the dat files. But the output values printed out in both cases are different(inputs are ok). Do you have any suggestions that I should try out , perhaps some compiler switches?
Why don't you show an example, then people will know what you are talking about.

---

### Post by Zugzwang on 2010-02-15
> **vgokul said:**
> Neither do I use any random numbers nor default precision for printing. The break characters are also not a problem with the dat files. But the output values printed out in both cases are different(inputs are ok). Do you have any suggestions that I should try out , perhaps some compiler switches?

What about the numerical stability of the algorithms you used?

---

### Post by Ferrat on 2010-02-15
In theory it could be due to some optimization that alters something, but really hard to tell without any real code or even information about what goes in and what comes out etc

It's like calling a doctor and asking why your leg hurts and asking what to do without really explaining the symptoms or what happened, might be a broken leg, might just be a twisted ankle or an infection etc, not really possible to tell before you git the doctor more information.

---

### Post by pbrane on 2010-02-15
What you seem to have is the defference between the GNU standard math library and the Microsoft standard math library. The base algorithms for floating point math are going to be different. I have seen this even between different compilers on the same platform. The differences are going to be cumulative as well. Also you need to take into account that the GNU compiler is probably the best in the world and is used and tested world wide as well.

The other issue is default compiler options. Does VC++ do certain types of optimizations by default? 

One more issue is your code. How are the floating point numbers handled? Are they all doubles? Will the results ALWAYS fit in a double. What are the ranges of numbers? Different compilers will handle this stuff differently.

One more thing. The '\n' vs '\r\n' is a file system issue. In a *nix OS the new lines in a TEXT file are '\n' (LF, line feed), in Windows, DOS, etc, the new line is '\r\n' CR+LF
The computer language (C/C++) will *translate* the new line to the native new line sequence used by the host system. Binary files usually don't use a LF or CR.

---

### Post by Krupski on 2010-02-15
> **vgokul said:**
> Just to clarify "differences" - In both cases I write (using fprintf) mostly datatype double outputs to a file and then compare the results at each timestep. Their I see differences between the values from Windows and Linux at the same time step and same inputs

I don't know if this applies to your problem, but a while back I had a heck of a time with a data conversion program that I wrote (and wanted to run under both Windows console mode and Linux).

The problem came from the fact that the INPUT files may have either CR/LF ending each line, or just LF.

To make the code portable between platforms, I had to make the input (READLN) function that I wrote independent of line endings.

So, what I did was strip EVERYTHING from the end of the line (CR, LF, newline, whatever) and then just null terminate the string.

Now, the program was independent of the format of the input file.

This is what I did:

```

int readln(FILE *fp, char *str)
{
	char buf[BUFSIZ];
	int len;

	buf[0] = 0;
	fgets(buf, BUFSIZ, fp);
	len = strlen(buf);

	while (len >= 0) {
		if (buf[len] <= 0x20) { buf[len] = 0; len--; }
		else { break; }
	}

	len++;
	buf[len] = 0;
	strncpy(str, buf, BUFSIZ);

	return len;
}

```

That code will read any text file correctly, no matter what it's format.

For example, LINUX "This is a line",0x0A,0

...and Windows "This is a line",0x0D,0x0A,0

...and Macintosh "This is a line",0x0D,0

All read in as "This is a line",0

To use it, of course:

```

        char buffer[BUFSIZ];
        int line_length;

        line_length = readln(stdin, buffer);

```

(edit): I used *fp so that "readln" could read stdin or an opened file equally easily.

Hope this helps...

-- Roger

---

### Post by vgokul on 2010-02-16
Thank you all for your suggestions and comments. I do understand that without some code or output it is not easy to help but unfortunately I am not in a position to provide both.  I will search through the source codes to see if there are any Windows/Linux specific implementation compiler switches used.
 
Regards
V.Gokul

---

### Post by Zugzwang on 2010-02-16
> **vgokul said:**
> Thank you all for your suggestions and comments. I do understand that without some code or output it is not easy to help but unfortunately I am not in a position to provide both.  I will search through the source codes to see if there are any Windows/Linux specific implementation compiler switches used.


Don't forget to check for numerical stability of the algorithms used! You somewhat ignored this possibility in your posts so far.

---

### Post by vgokul on 2010-02-19
I will check that also. Thanks. If I find something that is shareable I will update
 
Nice weekend to all
V.Gokul

---

