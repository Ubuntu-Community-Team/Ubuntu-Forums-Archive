---
title: "File rename with memory"
date: 2008-09-05
forum: Programming Talk
---

### Post by Neon612 on 2008-09-05
I have a bunch of files {mainly jpg, png, and gif (wallpaper)} that I want to rename. Since, they all end up having the same name, eg, 1.jpg, 2.jpg..... for each pack that I download, and right now I have to rename them by hand. A true pain when you need to do that to over 100 files.

I have a C++ program that will come up with a random filename of 20 characters, rename a file, and output that same filename to a text file.

What I want to be able to do is rename 100 files, then down the road when I get more wallpapers run the program again but if the random generator comes up with a filename that is already used it will skip over it. I just don't have any idea of how to go about this.

Here is the code I have so far:
[php]#include <stdio.h>
#include <dirent.h>
#include <string>
#include <iostream>
#include <fstream>
#include <time.h>

using namespace std;

int filefilter(const struct dirent *dir)         
{
  	const char *s = dir->d_name;
  	int len = strlen(s) - 4;            
  	if(len >= 0)
    	{
      		if (strncmp(s + len, ".jpg", 4) == 0)
    		{
      			return 1;
    		}
    	}
  	return 0;
}

string make_string (unsigned int n)
{
	string chars = "0123456789abcdefghijklmnopqrstuvwxyz";
	int c = chars.length();
	int randChar = rand() % chars.length();
	//string s;
	char s[20];
	
	for (int i = 19; i >= 0; i--)
	{
		s[i] = chars[randChar];      //chars[n % c];
		n = n /c;
		randChar = rand() % chars.length();
	}
	
	return string(s); 
}

int main ()
{
	srand(time(NULL));
	
	string strTemp;
  	struct dirent **eps;
  	int n;
  	
  	ofstream myfile;
  	myfile.open ("Used.txt");
  	
  	n = scandir ("./", &eps, filefilter, alphasort);
  	if (n >= 0)
    	{
      		int cnt;
      		string outstring, fileoutstring;
      		for (cnt = 0; cnt < n; ++cnt)
      		{
    			strTemp = (eps[cnt]->d_name);
    			
    			outstring = make_string(0);
    			fileoutstring = outstring;
    			fileoutstring.append(".jpg");
    			
    			rename(strTemp.c_str(), fileoutstring.c_str());
    			myfile << outstring << endl;
    			
    			
    			
    		}
    	}
  	else
  	{
  		perror ("Couldn't open the directory");
  	}
  	
  	myfile.close();

  	return 0;
}[/php]

---

### Post by ghostdog74 on 2008-09-05
this is not in C/C++, but an Awk script.
```

#!/bin/bash
awk 'BEGIN{
    srand()
    MAX=1000
    q="\047" #code for single quote
    #  iterate jpg file
    while (( "ls *jpg" | getline jpgfile ) > 0 ) {        
        while ( 1 ) { 
            #generate random number until satisfied
            num=int(rand() * MAX) +  1    #generate random num
            newfile = num".jpg"
            if ( (getline dummy < newfile) >=0 ) continue #check if it exists already and continue generate number
            break
        }        
        renamecmd = "mv "q jpgfile  q" "newfile
        #system(renamecmd) #rename the file.
    }
}'


```
you can follow the flow and adapt to C/C++.

---

### Post by doas777 on 2008-09-05
after you gen the filename, you check whether it already exists, as ghostdog74 showed. if you want to do c++ check out this page: [Check if a file exists using C++]("http://www.techbytes.ca/techbyte103.html") .

or you could just use ghostdog's script. 

your right, organizing a large 'wallpaper' library can be a pain can't it.

have fun,
Frank

---

### Post by Neon612 on 2008-09-05
Correct me if I'm wrong but wouldn't that only work for the file I happen to be looking at at a particular instance not the entire list of what has been used?

---

### Post by ghostdog74 on 2008-09-05
> **Neon612 said:**
> Correct me if I'm wrong but wouldn't that only work for the file I happen to be looking at at a particular instance not the entire list of what has been used?

in my script, i use the while loop to iterate the jpg files using the ls command. So therefore, it process every jpg file as it reads them, not a single jpg file. You can adapt it to your C/C++ program. There are ways to list out files in C/C++. you have to do the research.

---

### Post by DavidBell on 2008-09-06
Why are you using random fileanmes, it's just asking for problems. Come up with a consistent but non-repeating pattern and your problem is gone. 

EG rename to YYYY_MM_DD_#####.jpg

---

### Post by Neon612 on 2008-09-06
I want it random mainly because I don't want the date in the filename, and What else could I use? Every jpg is in the same folder. So sorting them by wallpaper type will become a pain, which is what I'm trying to avoid.

---

### Post by doas777 on 2008-09-07
> **Neon612 said:**
> I want it random mainly because I don't want the date in the filename, and What else could I use? Every jpg is in the same folder. So sorting them by wallpaper type will become a pain, which is what I'm trying to avoid.


well if you take it to milliseconds, it should workout.

however I have to ask, does the name need to be unique in it's folder, or do you want it unique in the universe? if you want global uniqueitude, then look into creating a [guid]("http://www.developerfusion.co.uk/show/2122/").

---

### Post by mssever on 2008-09-07
> **ghostdog74 said:**
> in my script, i use the while loop to iterate the jpg files using the ls command.Parsing the output of ls will fail in some corner cases. They might not apply to the OP's situation, but it's better to use the language's method of listing files (I don't know awk's).

> **Neon612 said:**
> I want it random mainly because I don't want the date in the filename, and What else could I use? Every jpg is in the same folder. So sorting them by wallpaper type will become a pain, which is what I'm trying to avoid.
How about something like this? ```
#!/bin/bash
for file in "$@"; do # loop over files named in ARGV
  mv -i "$i" "$(uuidgen -t).jpg"
done
```The chance of uuidgen producing a collision is nearly nil. In the very unlikely event that such a collision happens, the -i argument to mv will cause it to prompt you.

---

### Post by DavidBell on 2008-09-07
I think you would need to be a little bit careful with milliseconds and guids (which are partially based on millsecs IIRC), because I would have thought a rename operation would take way less than a millisecond which would mean lot's of overwrites or warnings.

Why not just number them incrementally?

    > Do first run renaming N*.* to _N*.*
    > Second run renames everything to N########.*

where the #s are incrementing number.

HTH DB

---

### Post by ghostdog74 on 2008-09-07
> **mssever said:**
> Parsing the output of ls will fail in some corner cases. They might not apply to the OP's situation, but it's better to use the language's method of listing files (I don't know awk's).

corner cases? an example? file names with spaces?? Its perfectly fine for ls *.jpg 
```

# ls * | awk '{print "file: "$0}'
file: file with spaces
file: file~
file: jpg with spaces
file: jpg with spaces.jpg

``` 

and 
```

# awk 'BEGIN {while (( "ls *jpg" | getline jpgfile ) > 0 ) {  print jpgfile}}'
jpg with spaces.jpg


```
if ls is used with the for loop like this:
```

for files in `ls *`

```
then files with spaces will break.

---

### Post by mssever on 2008-09-07
> **DavidBell said:**
> I think you would need to be a little bit careful with milliseconds and guids (which are partially based on millsecs IIRC), because I would have thought a rename operation would take way less than a millisecond which would mean lot's of overwrites or warnings.
Try this: ```
for i in `seq 1 30`; do uuidgen -t; done
``` and notice that there are no collisions. Presumably, this loop is faster than one that involves renaming.

---

### Post by mssever on 2008-09-07
> **ghostdog74 said:**
> corner cases? an example?How about filenames with newlines? The point is, it's impossible to reliably parse the output of ls for all valid filenames. That's why you do ```
for i in *.jpg
``` not ```
for i in `ls *.jpg`
```

---

### Post by ghostdog74 on 2008-09-07
> **mssever said:**
> Try this: ```
for i in `seq 1 30`; do uuidgen -t; done
``` and notice that there are no collisions. Presumably, this loop is faster than one that involves renaming.

in bash, {1..30} is used to generate sequence from 1 to 30.
```

for i in {1..30}

```

---

### Post by mssever on 2008-09-07
> **ghostdog74 said:**
> in bash, {1..30} is used to generate sequence from 1 to 30.
I didn't know that. Thanks.

---

### Post by ghostdog74 on 2008-09-07
> **mssever said:**
> How about filenames with newlines? 

with good policies in file name creation, this should not happen. But if insisted, using the for loop you mentioned or options from ls could be used.

> 
The point is, it's impossible to reliably parse the output of ls for all valid filenames. That's why you do ```
for i in *.jpg
``` not ```
for i in `ls *.jpg`
```
a workaround if using ls is insisted, could be :

ls --quoting-style="shell"  (or --show-control-chars)

---

### Post by Neon612 on 2008-09-08
Thanks guys for all the help but I think we may be straying from the point.

I've been working with it a bit trying my best to impliment what was shown here and here is what I have so far:
[php]#include <stdio.h>
#include <dirent.h>
#include <string>
#include <iostream>
#include <fstream>
#include <time.h>

using namespace std;

int filefilter(const struct dirent *dir)
{
  	const char *s = dir->d_name;
  	int len = strlen(s) - 4;            
  	if(len >= 0)
    	{
      		if (strncmp(s + len, ".jpg", 4) == 0)
    		{
      			return 1;
    		}
    	}
  	return 0;
}

string make_string (unsigned int n)
{
	string chars = "0123456789abcdefghijklmnopqrstuvwxyz";
	int c = chars.length();
	int randChar = rand() % chars.length();
	//string s;
	char s[20];
	
	for (int i = 19; i >= 0; i--)
	{
		s[i] = chars[randChar];
		n = n /c;
		randChar = rand() % chars.length();
	}
	
	return string(s); 
}

int main ()
{
	srand(time(NULL));
	
	string strTemp, line;
  	struct dirent **eps;
  	int n, i=0;
  	string strFile[10000], strFileExt[10000];
  	
  	ifstream file;
  	file.open ("Used.txt");
  	if (file.is_open())
  	{
  		while (! file.eof())
  		{
  			getline (file,line);
  			strFile[i] = line;
  			//cout << strFile[i] << endl;
  			i++;
  		}
  	}
  	file.close();

	ofstream myfile;
	myfile.open ("Used.txt", ios::app);
	
	  	
  	n = scandir ("./", &eps, filefilter, alphasort);
  	if (n >= 0)
    	{
      		int cnt;
      		string outstring, fileoutstring;
      		for (cnt = 0; cnt < n; ++cnt)
      		{
    			strTemp = (eps[cnt]->d_name);
    			
    			cout << strFile[cnt] << endl;
    			
    		REDO:			
    			outstring = make_string(0);
    			
    			if (outstring == strFile[cnt])
    			{
    				goto REDO;
    			}
    			    			
    			fileoutstring = outstring;
    			fileoutstring.append(".jpg");
    			
    			if (fileoutstring == strTemp)
    			{
    				continue;
    			}
    			
    			strFileExt[cnt] = strFile[cnt];
    			strFileExt[cnt].append(".jpg");
    			
    			if (strFileExt[cnt] == strTemp)
    			{
    				continue;
    			}
    			
    			rename(strTemp.c_str(), fileoutstring.c_str());
    			myfile << outstring << endl;
    			
    			
    			
    		}
    	}
  	else
  	{
  		perror ("Couldn't open the directory");
  	}
  	
  	myfile.close();

  	return 0;
}[/php]


I can get it to output the filenames, but it will not remember them. If I were to run this again the same files would be renamed along with any new ones. I'd like to set it up so that the old ones keep their present filename and only the new ones that don't match anything in Used.txt to change.

---

### Post by doas777 on 2008-09-09
if you really really really want to memorize the names you have used, just store them in a file. you will find a thousand tutorials on file IO in whatever language you choose.

but keep in mind, your program is going to be really slow. for each file you will have to:
1) open names file. 
2) read every line in names file.
3) compare current file name and decide whether the name is in the list. if so go on to next file. else ...
4) generate a new name. 
5) check the name against the list again to ensure it has not been used. if so, regen the name. repeat until name is not in list.
6)rename file.
7)re-open the names file for write access (meaning app cannot be multithreaded), and write the new name to the end. save file, close.
8) start over with the next file.

perhaps instead of storing the names you should move them to another location, so that you know everything in tha tlocation is already renamed. or just deal with it renaming files that are already renamed.

one other idea is to name them with a pattern you can recognize by matching to a regular expression. that way you can ignore already named files because they match the regex.

good luck

---

### Post by mssever on 2008-09-09
> **doas777 said:**
> for each file you will have to:
1) open names file. 
2) read every line in names file.
3) compare current file name and decide whether the name is in the list. if so go on to next file. else ...
4) generate a new name. 
5) check the name against the list again to ensure it has not been used. if so, regen the name. repeat until name is not in list.
6)rename file.
7)re-open the names file for write access (meaning app cannot be multithreaded), and write the new name to the end. save file, close.
8) start over with the next file.It's not that difficult. If you take that approach, there's no reason to read the names file for every file. Just read it once when the program starts, modify the list in memory, and write it once when the program finishes. Reading and writing the names file for every input file is just plain silly.

---

### Post by doas777 on 2008-09-09
> **Neon612 said:**
> Thanks guys for all the help but I think we may be straying from the point.

I've been working with it a bit trying my best to impliment what was shown here and here is what I have so far:
[php]#include <stdio.h>
#include <dirent.h>
#include <string>
#include <iostream>
#include <fstream>
#include <time.h>

using namespace std;

int filefilter(const struct dirent *dir)
{
  	const char *s = dir->d_name;
  	int len = strlen(s) - 4;            
  	if(len >= 0)
    	{
      		if (strncmp(s + len, ".jpg", 4) == 0)
    		{
      			return 1;
    		}
    	}
  	return 0;
}

string make_string (unsigned int n)
{
	string chars = "0123456789abcdefghijklmnopqrstuvwxyz";
	int c = chars.length();
	int randChar = rand() % chars.length();
	//string s;
	char s[20];
	
	for (int i = 19; i >= 0; i--)
	{
		s[i] = chars[randChar];
		n = n /c;
		randChar = rand() % chars.length();
	}
	
	return string(s); 
}

int main ()
{
	srand(time(NULL));
	
	string strTemp, line;
  	struct dirent **eps;
  	int n, i=0;
  	string strFile[10000], strFileExt[10000];
  	
  	ifstream file;
  	file.open ("Used.txt");
  	if (file.is_open())
  	{
  		while (! file.eof())
  		{
  			getline (file,line);
  			strFile[i] = line;
  			//cout << strFile[i] << endl;
  			i++;
  		}
  	}
  	file.close();

	ofstream myfile;
	myfile.open ("Used.txt", ios::app);
	
	  	
  	n = scandir ("./", &eps, filefilter, alphasort);
  	if (n >= 0)
    	{
      		int cnt;
      		string outstring, fileoutstring;
      		for (cnt = 0; cnt < n; ++cnt)
      		{
    			strTemp = (eps[cnt]->d_name);
    			
    			cout << strFile[cnt] << endl;
    			
    		REDO:			
    			outstring = make_string(0);
    			
    			if (outstring == strFile[cnt])
    			{
    				goto REDO;
    			}
    			    			
    			fileoutstring = outstring;
    			fileoutstring.append(".jpg");
    			
    			if (fileoutstring == strTemp)
    			{
    				continue;
    			}
    			
    			strFileExt[cnt] = strFile[cnt];
    			strFileExt[cnt].append(".jpg");
    			
    			if (strFileExt[cnt] == strTemp)
    			{
    				continue;
    			}
    			
    			rename(strTemp.c_str(), fileoutstring.c_str());
    			myfile << outstring << endl;
    			
    			
    			
    		}
    	}
  	else
  	{
  		perror ("Couldn't open the directory");
  	}
  	
  	myfile.close();

  	return 0;
}[/php]


I can get it to output the filenames, but it will not remember them. If I were to run this again the same files would be renamed along with any new ones. I'd like to set it up so that the old ones keep their present filename and only the new ones that don't match anything in Used.txt to change.


I'm not a c guy, but I am noticing a few logic issues. first, it doesn't look like you are comparing each file you want to rename to every name in the used array (or everyone past the last one noticed, if the both the used and input lists are sorted.) unless you have sorted I/O, your task requires O(N^2 + N) operations. I would also recomend that instead of leaving your output filestream open through the process, add the newly used name to your used array. at the end of execution, simply truncate your names file, and write out the array to your names file.

your algorithm would be:

```

read your file into used[]
for each file in directory
   for each name in used[]
      if file name = current used
          exit to next file loop //file already renamed
   rof 
   //file is not renamed yet
   generate new random name  
   for each name in used[] //check name for uniqueness
      if file name = current used //not unique
          return to generate new random name and repeat //try again
   rof //new name is unique 
   rename file
   add name to used[]
rof
//all files renamed
truncate used file
write array to used file

```


I can't say i would do it this way, but there it is.

have fun,
franklin

---

### Post by mssever on 2008-09-09
> **Neon612 said:**
> Thanks guys for all the help but I think we may be straying from the point.Not really, you've been presented with several solutions that do exactly what you asked.

> [php]             REDO:            
                outstring = make_string(0);
                
                if (outstring == strFile[cnt])
                {
                    goto REDO;
                }[/php]
Goto statements are evil, unless you're Linus Torvalds. You don't need goto. Forget it exists.

Also, your code is hard to parse because it's improperly indented. Incorrect indentation makes the code look like it does something other than what it does. If you format it properly, more people might be willing to look at it and help.
> I can get it to output the filenames, but it will not remember them.So store the filenames somewhere.

---

### Post by doas777 on 2008-09-09
> **mssever said:**
> It's not that difficult. If you take that approach, there's no reason to read the names file for every file. Just read it once when the program starts, modify the list in memory, and write it once when the program finishes. Reading and writing the names file for every input file is just plain silly.

ahh just a symantic misunderstanding,. I meant read out of a buffer, not back from storage. He need only check each file against every entry in the used list. sorry for any confusion.

---

