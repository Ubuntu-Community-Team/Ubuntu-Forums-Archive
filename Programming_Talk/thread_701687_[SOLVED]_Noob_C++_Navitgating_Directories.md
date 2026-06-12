---
title: "[SOLVED] Noob C++ Navitgating Directories"
date: 2008-02-19
forum: Programming Talk
---

### Post by ImALittleTeaPot on 2008-02-19
I'm new to programming in Linux. I'm using Eclipse downloaded from the repository.  I'm trying to write some basic c++ programs that require navigating through, and retrieving information from different directories.  

CODE: 

int main ()
{
	ifstream infile;
	ofstream outfile;
	MyClass AClass; 
	string name, fileWord; 
	
	 system("/home/XXXXX/Desktop/Folder"); 
  
	
	infile.open("thetext.txt"); 
	if (!infile)
	{	
		cout << "Failed to open file" << endl;
		return -1; 
	}
        return0;
}


I get the output error message: 
sh: /home/XXXX/Desktop/Folder: Permission denied
Failed to open file

I tried running the code as a root user, but I get the same 'Permission denied'.  I would appreciate it if someone could throw me a bone.

---

### Post by LaRoza on 2008-02-19
You are running the command:

```

/home/XXXXX/Desktop/Folder

```

Run that in the shell, and see what happens.

I think you want to "cd /home/XXXXX/Desktop/Folder".

Better yet, use the POSIX function for changing directories: [http://www.space.unibe.ch/comp_doc/c_manual/C/MAN/chdir.htm](http://www.space.unibe.ch/comp_doc/c_manual/C/MAN/chdir.htm)

---

### Post by ImALittleTeaPot on 2008-02-19
alright. Thanks for the resource page!

I included 'cd', and now I no longer get the 'Permission denied' error message, but it still fails to open the filestream. Any ideas? 
I really appreciate it, thanks for the help.

---

### Post by LaRoza on 2008-02-19
> **ImALittleTeaPot said:**
> alright. Thanks for the resource page!

I included 'cd', and now I no longer get the 'Permission denied' error message, but it still fails to open the filestream. Any ideas? 
I really appreciate it, thanks for the help.
Get rid of the system function, and use:

```

infile.open("/home/XXXXX/Desktop/Folder/thetext.txt");

```

---

### Post by ImALittleTeaPot on 2008-02-19
That works. 


Also, chdir ("filepath") while including the library '#include<unistd.h>'  from the webpage you suggested also worked.

Thanks a bundle!!

---

### Post by LaRoza on 2008-02-19
> **ImALittleTeaPot said:**
> That works. 

Also, chdir ("filepath") while including the library '#include<unistd.h>'  from the webpage you suggested also worked.

Thanks a bundle!!

No problem :-)

I get paid to help. (Well, not really. I just like to think I do)

---

### Post by slavik on 2008-02-19
#include <cunistd> NOT unistd.h ... this is C++, not C :) (LaRoza, shame on you for not catching it ...)

---

### Post by Jessehk on 2008-02-19
> **slavik said:**
> #include <cunistd> NOT unistd.h ... this is C++, not C :) (LaRoza, shame on you for not catching it ...)

AFAIK, the posix headers don't have C++ versions.

---

