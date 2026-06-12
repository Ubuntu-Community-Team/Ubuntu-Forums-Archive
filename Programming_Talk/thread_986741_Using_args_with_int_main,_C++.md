---
title: "Using args with int main, C++"
date: 2008-11-18
forum: Programming Talk
---

### Post by kachofool on 2008-11-18
Hey... I want to have a process call a program using execl. The process needs to send the program a couple of arguments...I don't really have a decent understanding of how this works. How am I supposed to compile the program that uses the arguments without the arguments in the first place?

Here's an example:

```

int main(int argc, char* argv[])

	/*	Get parent process ID and the file ID of the file
	 *  being used for shared memory	*/
	int PID=0;
	int inFile=0;
	sscanf (argv[1], "%d", &PID);
	sscanf (argv[2], "%d", &inputFile);

....
```

The above compiles fine but I get a segmentation fault upon execution. Is this because I'm not passing it anything? If I try to call it from the earlier process using execl would it work?... or am I just doing all this wrong?

---

### Post by slavik on 2008-11-18
you expect them ... if they are not there, that's your problem. that's why many programs do what is called input validation, where if the arguments aren't what you want, you complain about it and then exit(); :)

---

### Post by dribeas on 2008-11-19
> **kachofool said:**
> Hey... I want to have a process call a program using execl. The process needs to send the program a couple of arguments...I don't really have a decent understanding of how this works. How am I supposed to compile the program that uses the arguments without the arguments in the first place?
[...]
The above compiles fine but I get a segmentation fault upon execution. Is this because I'm not passing it anything? If I try to call it from the earlier process using execl would it work?... or am I just doing all this wrong?

You must check that the arguments are present before trying to process them. If no arguments are given to the program, argv[0] is 0 [*] and you will get a segmentation fault while trying to process the inexistent string.

[*] argv is an array of argc+1 elements, each of which is a pointer into a c string, with the very last one being 0, that is argv[argc] is a valid item in the array that has a guaranteed value of 0 (null pointer).

---

