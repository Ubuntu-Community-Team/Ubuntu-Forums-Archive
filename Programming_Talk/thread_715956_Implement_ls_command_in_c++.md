---
title: "Implement ls command in c++"
date: 2008-03-05
forum: Programming Talk
---

### Post by adityakavoor on 2008-03-05
I wrote a C++ code for implementing ls command.

```

#include<sys/types.h>
#include<dirent.h>
#include<unistd.h>
#include<iostream.h>

int main(int argc, char *argv[])
{
	DIR *dp;
	dirent *d;

	if(dp = opendir(argv[1]) != NULL)
		perror("opendir");

	while(d = readdir(dp) != NULL)
	{
		if(!strcmp(d->d_name,".") || !strcmp(d->d_name,".."))
			continue;

		cout << d->d_name << endl;
	}
}

```

I get the following error

```

aditya@ubuntu:~$ g++ lsr.cpp -Wno-deprecated

lsr.cpp: In function ‘int main(int, char**)’:

lsr.cpp:11: error: cannot convert ‘bool’ to ‘DIR*’ in assignment

lsr.cpp:14: error: cannot convert ‘bool’ to ‘dirent*’ in assignment

```

Any Idea ??

---

### Post by WW on 2008-03-05
!= has higher [precedence](http://www.cppreference.com/operator_precedence.html) than =.  Put parentheses around the assignment, then compare to NULL.

---

### Post by adityakavoor on 2008-03-05
Thanks WW. :popcorn:

---

### Post by adityakavoor on 2008-03-05
**Problem Implementing Recursive listing (ls -r)**

```


#include<sys/types.h>
#include<dirent.h>
#include<unistd.h>
#include<iostream.h>



void recursive_listing(char *ptr)
{

        DIR *dp;
        dirent *d;

	if((dp = opendir(ptr)) == NULL)
		perror("opendir");

	while((d = readdir(dp)) != NULL)
	{
		if(!strcmp(d->d_name,".") || !strcmp(d->d_name,".."))
			continue;
		
		if (d->d_type && DT_DIR)
		{
			cout << d->d_name << ":" << endl;
			recursive_listing(d->d_name);	
		}
		else
			cout << d->d_name << endl;
	}
	return;
}

int main(int argc, char *argv[])
{
	recursive_listing(argv[1]);
}	


```

I dont get any errors.

Program doesnt work. :(

Any Idea ??

---

### Post by WW on 2008-03-05
The variables dp and d are global, so your function is not reentrant; the variables get initialized with each call to recursive_listing().  Try making them local in recursive_listing().

P.S. You should also call **closedir(dp)** before you return from recursive_listing.

---

### Post by adityakavoor on 2008-03-05
Yep, I tried doing that.

No change in output.

Only the first entry in the directory is listed. Not all.

---

### Post by adityakavoor on 2008-03-05
**closedir(dp)** didnt work either.

Is the condition for checking for the Directory file type correct ??

```

if ( d->d_type && DT_DIR )

```

Also the output : The inner directories are not opened 

```

aditya@ubuntu:~$ ./a.out Desktop/
cars:
opendir: No such file or directory
Segmentation fault (core dumped)

```

I have a "cars" directory in Desktop

---

### Post by WW on 2008-03-05
Change **&&** to **&**.

---

### Post by adityakavoor on 2008-03-05
Still no :( :(

btw what is the difference between & and && ??

---

### Post by WW on 2008-03-05
Also, you need to pass the full path name when you recurse.  As it is, opendir tries to open all the files in the current working directory.

---

### Post by WW on 2008-03-05
> **adityakavoor said:**
> 
btw what is the difference between & and && ??

[http://cboard.cprogramming.com/showthread.php?t=85130](http://cboard.cprogramming.com/showthread.php?t=85130)

---

### Post by adityakavoor on 2008-03-05
> Also, you need to pass the full path name when you recurse. As it is, opendir tries to open all the files in the current working directory.

Oh yes.

What is the solution for that ?

EDIT : but in argv[1] I just gave Desktop and not /home/aditya/Desktop :confused:

---

### Post by WW on 2008-03-05
Sorry, I shouldn't have said *full*.  You can give a path relative to the current directory when you recurse.  For example, Desktop/cars.

---

### Post by adityakavoor on 2008-03-05
Even then, when I recurse, "cars" is passed as an argument to opendir( ) and not Desktop/cars.
Correct me if I am wrong.

---

### Post by WW on 2008-03-05
EDIT:
opendir should be given "Desktop/cars".  You have to modify your program to pass the correct name.

---

### Post by adityakavoor on 2008-03-05
OK. I'l be back with the modified code. Thanks for now

---

### Post by adityakavoor on 2008-03-06
Finally It worked. Here is the modified code.

```


if (d->d_type & DT_DIR)
		{
			cout << d->d_name << ":" << endl;

			strcpy(temp,ptr);
			strcat(temp,"/");
			strcat(temp,d->d_name);
			recursive_listing(temp);	
		}


```

---

### Post by the_unforgiven on 2008-03-06
> **adityakavoor said:**
> Finally It worked. Here is the modified code.

```


if (d->d_type & DT_DIR)
		{
			cout << d->d_name << ":" << endl;

			strcpy(temp,ptr);
			strcat(temp,"/");
			strcat(temp,d->d_name);
			recursive_listing(temp);	
		}


```
The code is not C++ at all - except for using cout and endl - it's just C with syntactic sugar of C++.

You might as well use printf() and '\n' for them.

I could understand if you were using std::string for handling all the string manipulation - in fact, that would've been much simpler too.

---

### Post by dwhitney67 on 2008-03-06
> **the_unforgiven said:**
> The code is not C++ at all - except for using cout and endl - it's just C with syntactic sugar of C++.

You might as well use printf() and '\n' for them.

I could understand if you were using std::string for handling all the string manipulation - in fact, that would've been much simpler too.
I agree 100%.

Here's a simple C++ implementation I came up with long ago:
[PHP]void listAllFiles( const std::string &dirName )
{
  DIR *dirp = opendir( dirName.c_str() );

  if ( dirp )
  {
    struct dirent *dp = NULL;

    while ( (dp = readdir( dirp )) != NULL )
    {
        std::string file( dp->d_name );

        if ( file == "." || file == ".." )    // skip these
          continue;

        if ( dp->d_type & DT_DIR )
        {
          // found a directory; recurse into it.
          string filePath = dirName + "/" + file;

          listAllFiles( filePath );
        }
        else
        {
          // regular file found
          std::cout << "filename is: " << file << std::endl;
        }
    }

    closedir( dirp );
  }
}[/PHP]

---

### Post by adityakavoor on 2008-03-06
Thanks dwhitney67 and the_unforgiven for your comments.

---

