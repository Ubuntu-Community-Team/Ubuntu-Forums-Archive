---
title: "[SOLVED] Wrong Current Directory"
date: 2008-04-24
forum: Programming Talk
---

### Post by WitchCraft on 2008-04-24
Hi, i have a question:

The subject: 
I have a wxWidgets GUI program, which works just fine on Windows and Linux. Now I added a help menu, and if it is selected, i want to launch the default browser to open a HTML page, which works fine, too.

But unforunately, I cannot use relative paths to the main index.htm file.

So I need to get the current working directory of the executable, add /help/index.htm, and then pass this to the browser call.

Now, this works well on Windows, and on Linux under Gnome, but it doesn't work on KDE...

My current working directory is: /root/Desktop/myprogam/
but getcwd always returns /root/ only...

Why is that?
I can use the wxWidgets getcwd function, or the C++ STL one, but they always return /root/. In a normal program, at least C++ STL returns /root/Desktop/myprogram, but that doesn't seem to be the case in my wxWidgets application... 

Why is that? Bug in KDE?

---

### Post by dwhitney67 on 2008-04-24
I just wrote a simple program to test the getcwd() library call.  It works like a charm.  Since you did not post any code, I cannot comment on what you may have done to derive incorrect results.

Here's the code I tested with:
[PHP]#include <iostream>
#include <unistd.h>

using namespace std;

int main()
{
  char cwd[256] = {0};
  getcwd( cwd, sizeof cwd );
  cout << "cwd = " << cwd << endl;
  return 0;
}[/PHP]

Btw, why are developing software under the root-account???  You should consider developing s/w apps under a user-account.

---

### Post by lnostdal on 2008-04-24
yeah, you could potentially screw up your entire system when doing development as root

if you need to be root i'd strongly consider using qemu or virtualbox or somethinglikethat

how do you start your program? do you start it from the terminal so you are sure it actually is executed in or from the directory you think?

---

### Post by WitchCraft on 2008-04-24
> **dwhitney67 said:**
> I just wrote a simple program to test the getcwd() library call.  It works like a charm.  Since you did not post any code, I cannot comment on what you may have done to derive incorrect results.

Here's the code I tested with:
[PHP]#include <iostream>
#include <unistd.h>

using namespace std;

int main()
{
  char cwd[256] = {0};
  getcwd( cwd, sizeof cwd );
  cout << "cwd = " << cwd << endl;
  return 0;
}[/PHP]

Btw, why are developing software under the root-account???  You should consider developing s/w apps under a user-account.

Yes, that's the STL way. I already tried this before, and it works if you do it in a separate program, but not when I include it in my program. But i do not change the execution directory...



actually my version is this one:
```

#include <iostream>

int main()
{
	std::string strCurrentDirectory = getcwd(NULL, 0) ;
	strCurrentDirectory += "/" ;
	printf("Current Directory: %s\n", strCurrentDirectory.c_str()) ;
	return EXIT_SUCCESS ;
} 

```
This allows just about any size for the current directory.
And unistd.h is not needed, as it is alread in iostream.

and neither works:
wxString wxstrCurrentWorkingDirectory = wxGetCwd() ;

But only in KDE. It works fine with GNOME and Windows...

> **lnostdal said:**
> 
yeah, you could potentially screw up your entire system when doing development as root

if you need to be root i'd strongly consider using qemu or virtualbox or somethinglikethat

how do you start your program? do you start it from the terminal so you are sure it actually is executed in or from the directory you think?



Leave me my root acount. 
I know what I do, and I know that sudo and gksudo exist.
It works fine for more then 2 years already, and I don't usually screw it up.

Why should i start it from console? 
It's a graphical program, and execution shouldn't be in another folder if I double-click on it... 
and besides, any user will double click, and not start it from console...


Hmmm, looks like this is a KDE 'Feature' ...


I think I prefer this:

[PHP]
#elif ( defined(__linux__) || defined(__linux) || defined(_linux) || defined(linux) || defined(__unix__) || defined(__unix) || defined(_unix) || defined(unix) )
	char chrarry_ReadLinkFormat[256] ;
	sprintf(chrarry_ReadLinkFormat, "/proc/%d/exe", (int) getpid());

	int  intBufferLength = readlink(chrarry_ReadLinkFormat, chrarray_Buffer, PATH_MAXLEN) ;
	if 	(intBufferLength < 0)
	{
		perror("readlink()") ;
		exit(EXIT_FAILURE) ;
	}
#endif
[/PHP]


And all this just because of KDE... i already hate KDE, but now I hate it even more...

---

### Post by dwhitney67 on 2008-04-24
This is a snip from the getcwd() man-page:
```
NAME
       getcwd, get_current_dir_name, getwd - Get current working directory

SYNOPSIS
       #include <unistd.h>

       char *getcwd(char *buf, size_t size);

       ...

       If buf is NULL, the behavior of getcwd() is undefined.
```

P.S.  The code you supplied works under Gnome; as for KDE, I can't test because I do not use that window manager.

---

### Post by lnostdal on 2008-04-24
> 
Why should i start it from console?

i would think the reason for me asking would be pretty darn obvius .. but never mind

[http://www.flipcode.com/archives/Path_To_Executable_On_Linux.shtml](http://www.flipcode.com/archives/Path_To_Executable_On_Linux.shtml)

..there might be easier ways, but i wouldn't bet on it

---

### Post by lnostdal on 2008-04-24
actually .. that code could be simplified somewhat .. /proc/self/exe .. as in, "self", will always refer to the "right thing"

so just open the file, read, and you're done .. that's it

edit:
you can check
```

rs@ibmr52:~/programming/lisp/symbolicweb$ file /proc/self/exe 
/proc/self/exe: symbolic link to `/usr/bin/file'

```

..so yeah, you need to use readlink.. i think you get it

---

### Post by stroyan on 2008-04-24
getcwd is telling you the current working directory.
That is not necessarily the directory your executable is in.

Here is an example using readlink of /proc/self/exe.
```

#include <limits.h>
#include <errno.h>
#include <string.h>
#include <stdio.h>
#include <unistd.h>

int main(int argc, char *argv)
{
    char buf[_POSIX_PATH_MAX];
    ssize_t result;
    char *last_slash;

    result = readlink("/proc/self/exe", buf, _POSIX_PATH_MAX);
    if (result == -1) {
	perror("readlink");
	return 1;
    }
    last_slash = strrchr(buf,'/');
    *last_slash = 0; /* Drop program name */
    printf("program is in directory %s\n", buf);
    return 0;
}

```

---

### Post by WitchCraft on 2008-04-24
> **stroyan said:**
> 
getcwd is telling you the current working directory.
That is not necessarily the directory your executable is in.

Usually, if you don't specify anything else, the current working directory is the directory of your executable, that's why it is called like this. But as said, while this is true for Windows, Mac and Gnome - which is unusual, it is therefore obvious that KDE needs to do it in another way...


> **stroyan said:**
> 
Here is an example using readlink of /proc/self/exe.
```

#include <limits.h>
#include <errno.h>
#include <string.h>
#include <stdio.h>
#include <unistd.h>

int main(int argc, char *argv)
{
    char buf[_POSIX_PATH_MAX];
    ssize_t result;
    char *last_slash;

    result = readlink("/proc/self/exe", buf, _POSIX_PATH_MAX);
    if (result == -1) {
	perror("readlink");
	return 1;
    }
    last_slash = strrchr(buf,'/');
    *last_slash = 0; /* Drop program name */
    printf("program is in directory %s\n", buf);
    return 0;
}

```


You didn't zero terminate the string before you strrchr... that's not a good idea (in case there is a '/' before there is a 0 in memory, additionally you could strrchr over a million chars, if you have bad luck) ...
But nice, strrchr is new to me ;-)

Here is the proper way:

```


#if ( defined(__linux__) || defined(__linux) || defined(_linux) || defined(linux) || \
      defined(__unix__) || defined(__unix) || defined(_unix) || defined(unix) )

	#define PATH_MAXLEN 0x1000

	std::wstring GetCurrentWorkingDirectory()
	{
		char chrarry_ReadLinkFormat[30]  ;
		char chrarray_Buffer[PATH_MAXLEN] ;
		unsigned int uintCurrentPosition  ;
		sprintf(chrarry_ReadLinkFormat, "/proc/%d/exe", (int) getpid());

		int  intBufferLength = readlink(chrarry_ReadLinkFormat, chrarray_Buffer, PATH_MAXLEN) ;
		if 	(intBufferLength < 0)
		{
			perror("readlink()") ;
			exit(EXIT_FAILURE) ;
		}
		chrarray_Buffer[intBufferLength] = '\0';

		for(uintCurrentPosition = strlen(chrarray_Buffer)-1; uintCurrentPosition > 0; --uintCurrentPosition) 
		{
			if(chrarray_Buffer[uintCurrentPosition] == '/') 
			{
				chrarray_Buffer[uintCurrentPosition + 1] = '\0' ;
				break;
			}
		}

		wxString wxstrCurrentWorkingDirectory = wxString::FromAscii( chrarray_Buffer ) ; // Dirty way to convert to Unicode...
		std::wstring wstrReturnValue = wxstrCurrentWorkingDirectory.wc_str() ;
		return wstrReturnValue ;
	}
#else
	std::wstring GetCurrentWorkingDirectory()
	{
		wxString wxstrCurrentWorkingDirectory = wxGetCwd() ; // returns incorrect directory for KDE
		std::wstring wstrReturnValue = wxstrCurrentWorkingDirectory.wc_str() ;
		wstrReturnValue += wxT(DIRECTORY_SEPARATOR) ;
		return wstrReturnValue ;
	}
#endif

```

I know that on Linux there is proc/self/exe as a substitute for /proc/<PID>/exe

But then, on FreeBSD it will be:
/proc/curproc/file
while /proc/self/exe doesn't exist...


So you need /proc/<PID>/exe because only this is universal, afaik

---

### Post by WitchCraft on 2008-04-24
Oh, it's now solved. I developed a more decent version:

KISS, KEEP IT SHORT AND SIMPLE
```

std::wstring GetCurrentWorkingDirectory() 
{ 
    wxString wxstrCurrentWorkingDirectory = wxStandardPaths::Get().GetExecutablePath()  ; 
    std::wstring wstrReturnValue = wxstrCurrentWorkingDirectory.wc_str() ; 
    wstrReturnValue = wstrReturnValue.erase(wstrReturnValue.find_last_of(wxT(DIRECTORY_SEPARATOR))+1 , wstrReturnValue.length() - ( wstrReturnValue.find_last_of(wxT(DIRECTORY_SEPARATOR))+1)) ; 
        
    return wstrReturnValue ; 
}

```

---

