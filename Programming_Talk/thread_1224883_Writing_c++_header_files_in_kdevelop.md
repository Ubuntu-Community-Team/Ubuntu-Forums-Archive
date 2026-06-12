---
title: "Writing c++ header files in kdevelop"
date: 2009-07-27
forum: Programming Talk
---

### Post by infinital on 2009-07-27
I'm a new programmer trying to write my own header file to store some of the useful functions i've created.  Unfortunately, I'm also very new to Linux.  I am currently running Kubuntu.
I have a couple questions:
1. How do I make this header available as a library to other programs I create?  Currently it only saves it in the project folder that I created it in.
2. Why does it throw out this when I try and compile it?
```
../libtool: line 2429: mkdir /.libs: No such file or directory
```
This is my header file's code (for just one function, the function I'm trying to call when it throws out the compile error
```

#include <cstdlib>
#include <iostream>

unsigned long fibonaccisequence(unsigned int);

using namespace std;

unsigned long fibonaccisequence (unsigned int limit) //This function returns a certain number in the fibonacci sequence, as defined by the variable limit
{
	unsigned long nextnum;
	unsigned long lastnum0;
	unsigned long lastnum1;
	unsigned int x;
	if( limit = 1 )
	{
		nextnum = 0;
	}
	else if( limit = 2 )
	{
		nextnum = 1;
	}
	else
	{
	for(x=0; x < limit-2 ; x++)
	{
		nextnum = lastnum0+lastnum1;
		lastnum0=lastnum1;
		lastnum1=nextnum;

	}
	}
return nextnum;
}

```

and this is the test program I was trying to use to test the header file:

```

#include "famousmath.h" //custom math library contains fibonaccisequence
#include <cstdlib>
#include <iostream>

using namespace std;

int main ()
{
	unsigned long nextnum;
	fibonaccisequence(5);
	cout << nextnum;
	return 0;
}
```

Please help me, I would really like to completely move over from Visual Studio 08 on XP to kdevelop with kubuntu.

---

### Post by JordyD on 2009-07-27
> **infinital said:**
> 1. How do I make this header available as a library to other programs I create?  Currently it only saves it in the project folder that I created it in.

Know where you've put it. If your project is in /home/yourusername/projects/libs, then just copy the contents to your new projects when you want to use them.

> **infinital said:**
> 2. Why does it throw out this when I try and compile it?
```
../libtool: line 2429: mkdir /.libs: No such file or directory
```

In relation to Linux filesystems, '/' means 'root', so it's the base of the file system. So /.libs is a folder called .libs at the base of the filesystem. You most likely don't have it there, so you probably want to get rid of the '/' prefix.

Hope that helps. Tell me if it doesn't, I could have misinterpreted.

Also, you may want to become familiar with how to do things *without* an IDE (like KDevelop or VS), so that you understand better how things work. It really helps, even when it comes to the code that you're writing. You don't need to learn it immediately, but take some time to become familiar with the command line, being familiar erases a lot of fog that you may not know that you had. Trust me, I've experienced it.

---

### Post by infinital on 2009-07-27
How do I change that, then?  I don't know how it got set to that in the first place.

---

### Post by JordyD on 2009-07-28
> **infinital said:**
> How do I change that, then?  I don't know how it got set to that in the first place.

It looks to me like this is a [problem (bug) in autotool]("https://bugs.launchpad.net/ubuntu/+source/libtool/+bug/285841") that was in Intrepid (I don't know if in Jaunty), what version of Kubuntu and KDevelop are you using? If Intrepid, you may want to consider getting the newest version from [their site]("http://www.kdevelop.org/"). It looks to me like they have Ubuntu/Kubuntu packages there, so it should be an easy install. As far as I'm aware, it should take care of getting rid of the old version for you.

Do tell if you have any problems.

**EDIT:** It may take a while for me to respond, since it's about time I go to bed.

---

### Post by infinital on 2009-07-28
I am using Kubuntu 9.04 and I used ```
apt-get install kdevelop
```
to get/download KDevelop.. So I am running whatever the newest version is.  On their website, they only have support up to 8.10.. Should I consider moving to another IDE for 9.04 support?
Thank you for the help Jordy

---

### Post by JordyD on 2009-07-28
> **infinital said:**
> I am using Kubuntu 9.04 and I used ```
apt-get install kdevelop
```
to get/download KDevelop.. So I am running whatever the newest version is.  On their website, they only have support up to 8.10.. Should I consider moving to another IDE for 9.04 support?
Thank you for the help Jordy

apt-get install kdevelop would install whatever is the newest version in the Ubuntu repos, not the newest version of the app. It's generally better to use them, because the Ubuntu repos versions have less bugs... normally.

You could move to another IDE, it will mean less trouble :). [Here is a list of IDEs and comparisons]("http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B") if you intend to go that route.

If not, you could try installing a newer KDevelop, but it might not fix the problem. In any case, if you download the Ubuntu package from the KDevelop site, uninstalling the package is as easy as uninstalling any other peice of software, so no problem if it turns out not to work.

---

### Post by dwhitney67 on 2009-07-28
You may also want to fix the bugs in your program.  There is a difference between the assignment operator "=" and the equality comparison operator "==".  Fix your code where appropriate.

Also, you did not initialize the variable in your main() function.  Did you intend to, and perhaps pass it to your function?

As for the result that is returned by the function, what did you want to do with it?  It seems reasonable that you would want to print the result, but you are not.

In the file containing your fibonaccisequence() function, you do not require the function declaration in this particular case because you are implementing the function a few lines down in the same file.  You also do not require the "using namespace std" statement, much less the need to include any header files.

If your goal is to create a library for that function, I would recommend that you create a separate header file and implementation file.  In such case, the header file would contain the function declaration, and the implementation file would have the function's implementation as you currently have.  The implementation file would need to include your library's header file, as would the file containing your main() function.

---

### Post by infinital on 2009-07-28
> **dwhitney67 said:**
> You may also want to fix the bugs in your program.  There is a difference between the assignment operator "=" and the equality comparison operator "==".  Fix your code where appropriate.

Also, you did not initialize the variable in your main() function.  Did you intend to, and perhaps pass it to your function?

As for the result that is returned by the function, what did you want to do with it?  It seems reasonable that you would want to print the result, but you are not.

In the file containing your fibonaccisequence() function, you do not require the function declaration in this particular case because you are implementing the function a few lines down in the same file.  You also do not require the "using namespace std" statement, much less the need to include any header files.

If your goal is to create a library for that function, I would recommend that you create a separate header file and implementation file.  In such case, the header file would contain the function declaration, and the implementation file would have the function's implementation as you currently have.  The implementation file would need to include your library's header file, as would the file containing your main() function.

This was honestly just a stab in the dark. I had already written a simple program output the fibonacci sequence and I thought to myself "Hey, that's kind of useful, I'll use that later possibly".  So there are obviously some quirks/bugs in it, as I haven't gotten to compile it in this form yet.  Thank you for the advice though, I'll be sure to fix though.  
For future reference, can you tell me the difference between == and =?

---

### Post by Mirge on 2009-07-28
= is used for assignment. == is used for comparison.

int apple = 5; // assign the value 5 to the int variable apple.

if(apple == 5) { ... } // true, because apple does have a value of 5.

P.S. This toothache SUCKS...

---

### Post by infinital on 2009-07-28
Thank you all for the help.

So, to be clear, to make a real library I should put all of my function prototypes in a header file that includes an implementation file that has all of my definitions in it?

---

### Post by infinital on 2009-07-28
I installed eclipse in hopes of easing my growing pangs - no such luck.
Eclipse won't even compile anything and when I point G++ at the file it says it doesn't exist.  I thought Linux would be a bit easier of a switch than this, I suppose not.

---

### Post by JordyD on 2009-07-28
> **infinital said:**
> I installed eclipse in hopes of easing my growing pangs - no such luck.
Eclipse won't even compile anything and when I point G++ at the file it says it doesn't exist.  I thought Linux would be a bit easier of a switch than this, I suppose not.

What is the command you're using to compile?

And what error is Eclipse giving you?

And you do *not* want to install Eclipse from the repos. The repo version is really slow.

---

### Post by infinital on 2009-07-28
> **JordyD said:**
> What is the command you're using to compile?

And what error is Eclipse giving you?

And you do *not* want to install Eclipse from the repos. The repo version is really slow.

I was just clicking the build button and nothing was happening.  When I tried to run it, it said I was missing binaries. So I tried the G++ through terminal route to make it work.  Still no dice.  I just switched to NetBeans, and it worked on the first time, and I like it more than Eclipse or KDevelop (For now at least).

Problem solved. Thank you for the help

---

### Post by Mirge on 2009-07-28
> **infinital said:**
> I was just clicking the build button and nothing was happening.  When I tried to run it, it said I was missing binaries. So I tried the G++ through terminal route to make it work.  Still no dice.  I just switched to NetBeans, and it worked on the first time, and I like it more than Eclipse or KDevelop (For now at least).

Problem solved. Thank you for the help

At least you can run NetBeans.. I tried a few times, but it would _always_ crash/vanish. Eclipse CDT for me :).

---

### Post by JordyD on 2009-07-28
> **Mirge said:**
> At least you can run NetBeans.. I tried a few times, but it would _always_ crash/vanish. Eclipse CDT for me :).

I got a MacBook recently, and now I'm addicted to XCode. I still use vim for c, though.

---

