---
title: "[SOLVED] GCC C++ Sometimes Problem"
date: 2008-04-03
forum: Programming Talk
---

### Post by 71fnRVVm on 2008-04-03
Hi everyone,

What I've found is apparently a bug in the GCC compiler, but here's the story and why I can't fix it:

I'm developing a C++ Program, which right now just reads a file, that is to run on a CentOS5 server, but I'm writing it locally where possible.

Current code:```

#include <iostream>
#include <fstream>
#include <string>
#include <cmath>
using namespace std;

int main() {
	string buffer, temp, to[500], title[500], body[500];
	int pos1, pos2, count, rCount;
	FILE * inUse;
	
	// Create "locking file"
        inUse = fopen("/home/osadmin/data/jabberInUse", "w");
	fclose(inUse);

	// Read file into buffer
	ifstream jabberQueue;
	jabberQueue.open("/home/osadmin/data/jabberQueue", ios::in);
        if (jabberQueue.is_open()) {
		rCount = 0;
		while (!jabberQueue.eof()) {
			count = 1;
			pos2 = 0;
			
			getline(jabberQueue,buffer, '\n');
			
			while (count <= 3) {
				pos1 = pos2 + 2;		
				pos2 = buffer.find("~|",pos1);
				temp = buffer.substr(pos1,pos2 - pos1);
				if (count == 1) {
					to[rCount] = temp;
				} else if (count == 2) {
					title[rCount] = temp;
				} else if (count == 3) {
					body[rCount] = temp;
				}
				count++;
			}
		}
		jabberQueue.close();
	}
        
        remove("/home/osadmin/data/jabberInUse");
        return 0;
}
```

The error (originally seen on the server at compiling):```

root@host [/home/osadmin/libc/source/jabberQueue]# /usr/local/gcc-4-2/bin/g++4.2 main.cpp -o main
root@host [/home/osadmin/libc/source/jabberQueue]# ./main
terminate called after throwing an instance of 'std::out_of_range'
what(): basic_string::substr
Aborted
```

On my system, using "gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)" I don't have any errors in compiling or at runtime.

On the server, which was upgraded to "gcc4.2 (GCC) 4.2.0" after finding this problem, it still returns the same error... but this time at runtime, and *not* at compiling.

The hosts have thrown in the towel on this one for support, saying it's now a code problem.  But in doing some poking around the internet, it's supposed to be a bug... but 4.2 is causing problems, where 4.1.3 isn't?  

Any ideas/help are appreciated.

Thanks

---

### Post by heikaman on 2008-04-03
> **71fnRVVm said:**
> 
terminate called after throwing an instance of 'std::out_of_range'
what(): basic_string::substr
Aborted


what bug ? it's an exception ! without looking at the code, you exceeded the range of the string when you called substr :)

---

### Post by 71fnRVVm on 2008-04-03
I thought of that when I first saw this, and checked.

But I just checked again.  Here's the output of "pos1:pos2":
```

1:21
22:28
29:37
1:18
19:25
26:30

```

And here's what the file looks like:
```

~|71fnRVVm%40gmail.com~|hello~|yourmom~|
~|tester%40mom.com~|bragh~|dah~|
```

If you do the math, you'll see that it does *not* go out of bounds.  For example, the first line contains 39 characters...

---

### Post by WW on 2008-04-03
You will get the error if the last character of your input file is \n.  In this case, getline discards the \n, but the loop runs once more.  On the last iteration, buffer has length 0 after getline.

Either fix your input file, or fix your code to handle this case.


EDIT: For example,
```

            getline(jabberQueue,buffer, '\n');
            if (buffer.size() > 0)
                while (count <= 3) {
                // etc...
                }

```

---

### Post by 71fnRVVm on 2008-04-04
WW:  Beautiful!  

I didn't know it ignored end of line characters.

Thanks!

---

### Post by Jessehk on 2008-04-04
In 99.99% of cases people think they've found a bug in GCC (which I've learned is inevitable), their code is at fault.

---

### Post by Tuna-Fish on 2008-04-04
Yes to Jessekh. Remember, gcc is used by a ridiculous amount of people. While there are bugs, and while they are constantly being found, the chance that **you** run into a new one in your entire programming career is very small, and the chance that a compiler bug is causing whatever problem you are having **now** is so vanishingly small that it's generally not worth considering. If your code doesn't work, there's something wrong with it, and if you blame the compiler for it, there's something wrong with **you**.

Remember the first rule of programming: [It's Always Your Fault.]("http://www.codinghorror.com/blog/archives/001079.html")

Like now, simply running the offending parts trough a debugger could have saved the original poster lots of time and embarrassment.

---

### Post by 71fnRVVm on 2008-04-04
I know, I agree.

The only reason I mentioned it in this case was because my host pointed me to this: [http://www.dribin.org/dave/blog/archives/2006/02/](http://www.dribin.org/dave/blog/archives/2006/02/)

It seemed to match what we thought was my problem... and, of course, it would mean it wasn't my fault!

Anyways, just want to point out that I only brought it up because *someone else* had suggested it, and not me ;-)

---

### Post by webofunni on 2008-04-04
Hi All,

  One more doubt on this .............. This cpp program runs fine on ubuntu machine but it failed on centos with almost all the version of GCC. Why there is no error incase of ubuntu machine . 

  Any idea

---

### Post by WW on 2008-04-04
webofunni:  My guess was (and still is) that on the server, the input file had a newline at the end, but 71fnRVVm's local input file (perhaps a test file created by hand with an editor?) did not have a final newline.  That's why the code worked on his local machine but failed on the server.

---

### Post by webofunni on 2008-04-05
Hi WW,

  Thanks for the info :-)

---

