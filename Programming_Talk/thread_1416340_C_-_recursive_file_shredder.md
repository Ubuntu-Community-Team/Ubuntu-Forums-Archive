---
title: "C - recursive file shredder"
date: 2010-02-26
forum: Programming Talk
---

### Post by ApEkV2 on 2010-02-26
Hello, I was bored and decided to make a recursive file shredder and am having trouble with getting the full pathnames.
EDIT

It seems the first call to readdir() in my main loop returns two periods. 
Here is what I have, (I haven't dealt with sub-folders yet)
```
look below
```

---

### Post by PmDematagoda on 2010-02-26
About the two periods you are getting, they are the directory entries for the current directory(the ".") and the top-level directory(the ".."), in your case, I would skip them for obvious reasons. :)

About the full path names, you could probably get them by concatenating the following strings:-
1) Output of getenv("PWD")
2) Contents of argv[1]
3) Contents of ent->d_name
or, you could just tell the user to provide the full path and simplify things a bit.

A few things about your program I would like to point out:-

1) I would recommend against mixing upper and lower case letters in function names.

2) Using memset to reset the path and name arrays is just unnecessary, strcpy will automatically copy the nul-byte to the end of the string, which is what you need(consider using strncpy by the way for security reasons, atleast for when filling the name array).

3) You run Fclose() on the file right after the first iteration instead of doing that after both iterations of shredding have occurred, which I think kind of defeats the purpose of the program slightly.

4) Please do _not_ use capitals in variable names. Frankly I almost mistook the second parameter in the Get_size function for a preprocessor macro.

5) You aren't differentiating between directories and files given by readdir(), so who knows what might happen, unless the directory you are working on is made up of files only.

6) I don't think using function names like "Fclose" is a good idea because of their similarity to the ISO C standard specified functions. Something like "delete_file_at_path" might be easier to understand and better.

---

### Post by ApEkV2 on 2010-02-27
Thanks for the reply PmDematagoda.  

I will have to skip the first two results of readdir().
However, in my OP I believe I already said I haven't dealt with subfolders.
Shouldn't fopen() fail if it tries to open a directory?
And I always capitalize the first letter of functions. (imo this isn't a problem)

The problem I'm having now is that the file path isn't surrounded by quotes. fopen() fails
EDIT: the problem is actually missing a forward slash. that's easy, but will the lack of quotes?
EDIT: fopen fails even though the file path looks correct.

```
look below
```

---

### Post by PmDematagoda on 2010-02-27
> **ApEkV2 said:**
> Thanks for the reply PmDematagoda.  

I will have to skip the first two results of readdir().
However, in my OP I believe I already said I haven't dealt with subfolders.
Shouldn't fopen() fail if it tries to open a directory?
And I always capitalize the first letter of functions. (imo this isn't a problem)

The problem I'm having now is that the file path isn't surrounded by quotes. fopen() fails
EDIT: the problem is actually missing a forward slash. that's easy, but will the lack of quotes?

Yes, you are right, fopen() does fail, my mistake. :)

About your capitalizing of the first letter in functions, it's your personal choice really, but since most people don't really do that(atleast that's what I think :P), you might have problems with people trying to adjust to your coding style when trying to contribute or help.

About the quotes thing, that is unnecessary, just consider this:-
1) fopen("test", "r+");

2) test_path = "test";
fopen(test_path, "r+");

Both of the above are the same, but the important thing to remember is, that the quotes are there to mark the word "test" as a string, because if it wasn't quoted the compiler would consider that as a variable and try to assign the address of variable test to test_path, most importantly(in your case), the test_path variable actually points to the word "test" without quotes. So quotes in the path itself aren't necessary(in fact they would cause problems).

Edit:- What on earth are you doing above? You do know that the array buffer is freed right after the function finishes execution? Even the prototype is all wrong. Why not allocate an array dynamically to fit the size of the path and return it(it should be freed after usage)? Or, you could provide an array when calling the function for the Put_path function to write the path in to.

---

### Post by ApEkV2 on 2010-02-27
> Edit:- What on earth are you doing above? You do know that the array buffer is freed right after the function finishes execution? Even the prototype is all wrong. Why not allocate an array dynamically to fit the size of the path and return it(it should be freed after usage)? Or, you could provide an array when calling the function for the Put_path function to write the path in to.

The way I'm using Path_put() shouldn't matter if the buffer is closed after it is finished.
Shouldn't the function return a string? I already know the answer as it works now (kinda).

Now I'm back to having problems with the dot, dot-dot crap thing again (why are they even there?)
I was thinking about creating an array of pointers to the full path names.

---

### Post by PmDematagoda on 2010-02-27
> **ApEkV2 said:**
> The way I'm using Path_put() shouldn't matter if the buffer is closed after it is finished.
Shouldn't the function return a string? I already know the answer as it works now (kinda).

Now I'm back to having problems with the dot, dot-dot crap thing again (why are they even there?)
I was thinking about creating an array of pointers to the full path names instead of guessing.

The function returns an address to the location of an array of characters(string), the problem with yours is that you are returning an address that might not be valid because the variable buffer is non-existent as soon as you return from the function.

About the dots, use strcmp and just skip them.

Edit:- Why don't you read the warnings GCC is spewing out when it's compiling your program? There are lots of them and I would be inclined to think that all of them are relevant with the problems you are having.

---

### Post by dwhitney67 on 2010-02-27
> 
Think carefully before executing commands containing "rm", especially "sudo rm -rf "

Also think carefully before trying to run the code that the OP has provided.  Aside from the fact that it has bugs, if you test it, be wary that it's intent is to replace the characters in all files within a specified directory with nulls and a "1" (0x31).

The OP has a "first-grade" education with respect to programming in C.  There are too many mistakes and inefficiencies in the code to comment on.

PmDematagoda, he's all yours!

---

### Post by ApEkV2 on 2010-02-28
> **dwhitney67 said:**
> 

The OP has a "first-grade" education with respect to programming in C.  There are too many mistakes and inefficiencies in the code to comment on.

PmDematagoda, he's all yours!

I don't even have a "first grade" education in any programming language, I'm 19 and have been teaching myself for the past couple months.
My first "official" class in C is next semester.

BTW I don't think anyone here knows what a recursive file shredder is dwhit

---

### Post by PmDematagoda on 2010-02-28
> **ApEkV2 said:**
> I don't even have a "first grade" education in any programming language, I'm 19 and have been teaching myself for the past couple months.
My first "official" class in C is next semester.

BTW I don't think anyone here knows what a recursive file shredder is dwhit

You're talking about me. :)

All I had to teach me was a C reference book, and the internet. Granted I did know VB first(horror! :P).

My suggestion to you is to start small(a file shredder is not small), make some string changers, finders, or whatever. Make your mistakes, listen to what the other people are trying to tell you(you are not doing that). C is not a programming language you can master all at once, so don't be scared if you don't. :)

Also, you might be better off learning python first, I rarely say this to anyone because of my personal experiences, but for you, I think learning python first will be a good thing. :)

---

### Post by ApEkV2 on 2010-02-28
> **PmDematagoda said:**
> You're talking about me. :)

All I had to teach me was a C reference book, and the internet. Granted I did know VB first(horror! :P).

My suggestion to you is to start small(a file shredder is not small), make some string changers, finders, or whatever. Make your mistakes, listen to what the other people are trying to tell you(you are not doing that). C is not a programming language you can master all at once, so don't be scared if you don't. :)

Also, you might be better off learning python first, I rarely say this to anyone because of my personal experiences, but for you, I think learning python first will be a good thing. :)


It's not like I don't listen, most of the time I can't understand people's solution to my problems.
But IMHO my code gets a little less worse each time someone replies and painfully criticizes.
Python was almost what I decided, but I decided to start C before my classes started up.

there are no warnings from gcc anymore.

EDIT: it seems to be segfaulting in the main loop when there are no files in the folder. [color=red]FIXED[/color]
EDIT: recursion seems to be broken, dang it bob saget!

[color=red]EDIT: this the old non-recursive crappy code, next page has the final[/color]
```
/*//////////////////////////////////////////////////*/
#include <dirent.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
/*//////////////////////////////////////////////////*/
int Find_size(FILE* n);
int Fclose(FILE* n, char *p);
int Get_size(DIR* p);
int KO_file(struct dirent *ent);
void Put_path(char* argv, struct dirent *ent);
/*//////////////////////////////////////////////////*/

int main(int argc, char *argv[])
{
	if (argv[1] == NULL) {	
		printf("\nUsage: [command] [path]\n\n");
		return -1;
	}

	DIR *dir = opendir(argv[1]);
	
	if (dir == NULL) {
		printf("\n[FAIL] opendir()\n\n");
		return -1;
	}

	struct dirent *ent;
	int inc, files = Get_size(dir);
	
	for (inc = 0; inc <= files; ++inc)
	{	
		if ((ent = readdir(dir)) == NULL) break;
		
		if ((strcmp(".", ent->d_name)) != 0 && 
		    (strcmp("..", ent->d_name)) != 0)
		{
			Put_path(argv[1], ent);
			
			if ((KO_file(ent)) != 0) {
				printf("\n[FAIL] KO_file()\n\n");
				return -1;
			}
		}
	}

	closedir(dir);
	rmdir(argv[1]);
	return 0;
}

/*//////////////////////////////////////////////////*/

int Find_size(FILE* n)
{
	if ((fseek(n, 0, SEEK_END)) != 0)
		printf("\n[FAIL] fseek()\n");
		
	int length = ftell(n); 
	rewind(n);
	
	return length;
}

/*//////////////////////////////////////////////////*/

int Fclose(FILE* n, char *p)
{
	if ((fclose(n) != 0)) return -1;
	if ((unlink(p) != 0)) return -1;
	return 0;
}

/*//////////////////////////////////////////////////*/

int Get_size(DIR* p)
{
	int count = 0;
	
	while (readdir(p) != NULL)
		++count;

	rewinddir(p);
	return count;
}

/*//////////////////////////////////////////////////*/

int KO_file(struct dirent *ent)
{
	FILE* ptr = fopen(ent->d_name,"r+");

	if (ptr == NULL) {
		printf("\n[FAIL] fopen()\n\n");
		return -1;
	}
	
	int count = 1;
	int limit = Find_size(ptr)-1;
	
	for (; count <= limit; ++count)
	{
		if (count%2 == 0) fputc('\0', ptr);
			else fputc('1', ptr);
	}
	
	if ((Fclose(ptr, ent->d_name)) != 0) {
		printf("\n[FAIL] Fclose()\n\n");
		return -1;
	}
	
	return 0;
}

/*//////////////////////////////////////////////////*/

void Put_path(char* argv, struct dirent *ent)
{
	char buffer[256];
	strcpy(buffer, argv);
	strcat(buffer, "/");
	strcat(buffer, ent->d_name);
	strcpy(ent->d_name, buffer);

	return;
}

/*//////////////////////////////////////////////////*/
```

---

### Post by dwhitney67 on 2010-02-28
Here's the simplest way I could figure out how to do the task you're trying to accomplish:
```

#include <dirent.h>
#include <string.h>
#include <stdlib.h>
#include <sys/stat.h>
#include <stdio.h>

void findFiles(const char* directory);
void killFile(const char* filename);

int main(int argc, char** argv)
{
   if (argc != 2)
   {
      fprintf(stderr, "Usage: %s <dir>\n", argv[0]);
      return -1;
   }

   findFiles(argv[1]);

   return 0;
}


void findFiles(const char* directory)
{
   DIR* dir = opendir(directory);

   if (dir)
   {
      struct dirent* de = 0;

      while ((de = readdir(dir)) != 0)
      {
         if (strcmp(de->d_name, ".") == 0 || strcmp(de->d_name, "..") == 0)
            continue;

         char* filePath = malloc(strlen(directory) + 1 + strlen(de->d_name) + 1);
         sprintf(filePath, "%s/%s", directory, de->d_name);

         if (de->d_type == DT_DIR)
         {
            // recurse into sub-directory
            findFiles(filePath);
         }
         else if (de->d_type == DT_REG)
         {
            // kill regular file
            killFile(filePath);
         }

         free(filePath);
      }

      closedir(dir);
   }
}

void killFile(const char* filename)
{
   FILE* file = fopen(filename, "rb+");

   if (file)
   {
      struct stat buf;
      stat(filename, &buf);

      for (int i = 0; i < buf.st_size; ++i)
      {
         (i % 2) ? fputc(0x01, file) : fputc(0x00, file);
      }
      
      fclose(file);
   }
   else
   {
      fprintf(stderr, "Error: Unable to open %s; permission problem?\n", filename);
   }
}

```

This example actually uses recursion.  Use this application at your own risk!

---

### Post by ApEkV2 on 2010-02-28
Thanks for the reply and the code dwhitney, that is probably the simplest.
Here is my final code, got a lot from yours, but in my style.
I don't know why I didn't use stat, I'm retarded. 
The one thing that doesn't work in this code is using a single file as an argument.

EDIT: it seems the code segfaults if it encounters a file with higher privileges.
[color=red]EDIT: the code in this post doesn't deal with single files as an argument - fix below[/color]

```
/*//////////////////////////////////////////////////*/
#include <dirent.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/stat.h>
#include <unistd.h>
/*//////////////////////////////////////////////////*/
void Finagle(char *argv);
void KO_file(char *path);
/*//////////////////////////////////////////////////*/

int main(int argc, char *argv[])
{
	if (argv[1] == NULL) {	
		printf("\nUsage: [command] [path]\n\n");
		return -1;
	}

	Finagle(argv[1]);
	return 0;
}

/*//////////////////////////////////////////////////*/

void Finagle(char *argv)
{
	DIR *dir = opendir(argv);
	if (dir == NULL) exit -1;
	
	struct dirent *dep;
	
	while ((dep = readdir(dir)) != NULL)
	{
		if (strcmp(".",dep->d_name) == 0 || strcmp("..",dep->d_name) == 0)
			continue;
			
		char *path = malloc(strlen(argv) + strlen(dep->d_name) + 2);
		sprintf(path, "%s/%s", argv, dep->d_name);
		
		if (dep->d_type == DT_DIR) {
			Finagle(path);
		}
		else if (dep->d_type == DT_REG) {
			KO_file(path);
		}
		
                free(path);
		usleep(500);
	}
	
	closedir(dir);
	rmdir(argv);
}

/*//////////////////////////////////////////////////*/

void KO_file(char *path)
{
	FILE* fp1 = fopen(path,"rb+");
	if (fp1 == NULL) exit -1;
	
	struct stat buf;
	stat(path, &buf);
	int count = 1;
	
	while (count <= buf.st_size)
	{
		if (count%2 == 0) fputc(0x00, fp1);
			else fputc(0x01, fp1);
			
		++count;
	}
	
	fclose(fp1);
	unlink(path);
}
	
/*//////////////////////////////////////////////////*/
```

---

### Post by ApEkV2 on 2010-03-01
Ok this is final, seriously. Single files as well as humongous directories are able to be used as arguments.
However, if it encounters any file with higher privileges, it will segfault (that's probably a good thing)
I've tested this code in a directory containing over 15,000 files with a total size of 420mb. No errors.

I changed the structs around, and added a test in main with the macro S_ISDIR(mode). Solved. Thanks dwhitney.
```
/*//////////////////////////////////////////////////*/
#include <dirent.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/stat.h>
#include <unistd.h>
/*//////////////////////////////////////////////////*/

struct dirent *dep;
struct stat buf;
void Finagle(char *argv);
void KO_file(char *path);

int main(int argc, char *argv[])
{
	if (argv[1] == NULL) {	
		printf("\nUsage: [command] [path]\n\n");
		return -1;
	}
	
	stat(argv[1], &buf);
	if (!S_ISDIR(buf.st_mode)) {
		KO_file(argv[1]);
	}
		else Finagle(argv[1]);
		
	return 0;
}

/*//////////////////////////////////////////////////*/

void Finagle(char *argv)
{
	DIR *dir = opendir(argv);
	if (dir == NULL) return;  [color=blue]// not skip -1;[/color]
	
	while ((dep = readdir(dir)) != NULL)
	{
		if (strcmp(".",dep->d_name) == 0 || strcmp("..",dep->d_name) == 0)
			continue;
			
		char *path = malloc(strlen(argv) + strlen(dep->d_name) + 2);
		sprintf(path, "%s/%s", argv, dep->d_name);
		
		if (dep->d_type == DT_DIR) {
			Finagle(path);
		}
		else if (dep->d_type == DT_REG) {
			KO_file(path);
		}
		
		free(path);
		usleep(500);
	}
	
	closedir(dir);
	rmdir(argv);
}

/*//////////////////////////////////////////////////*/

void KO_file(char *path)
{
	FILE* fp1 = fopen(path,"rb+");
	if (fp1 == NULL) return;  [color=blue]// not skip -1;[/color]
	
	stat(path, &buf);
	int count = 1;
	
	while (count <= buf.st_size)
	{
		if (count%2 == 0) fputc(0x00, fp1);
			else fputc(0x01, fp1);
			
		++count;
	}
	
	fclose(fp1);
	unlink(path);
}
	
/*//////////////////////////////////////////////////*/
```

Again this code shreds and deletes **all** the directories and files in the specified directory.
As far as I've tested this code, the possibility of damage caused by misuse is out of my control.

---

### Post by dwhitney67 on 2010-03-01
You should not call "exit -1" when a function encounters an error; merely return from the function, thus allowing for other files/directories to be processed.

Of course, if you do not have permissions to open/read/write to a file, then ultimately the file cannot be unlinked (removed).  Subsequently, you will not be able to remove the directory containing the file.

In your main() function, check to see if the argv[1] is a "regular" file, similar to what you did in Finagle().  There is no need to KO character-block files, symbolic links, etc.


P.S.  I could see nothing in your code that would cause a segmentation violation (segfault).

---

### Post by ApEkV2 on 2010-03-01
Thanks again dwhitney, That was causing the segfault.
Using exit instead of return caused it somehow.
Changed them and now it just skips them like you said.

---

