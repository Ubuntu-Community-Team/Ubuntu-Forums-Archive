---
title: "Get size of file using C"
date: 2006-03-07
forum: Programming Talk
---

### Post by zootreeves on 2006-03-07
Is there an easy way to get the size of a file, using C. Here is what i have got so far:

	int filesize;
	struct stat file_status;
	stat("./tmp.xml", &file_status);
	printf("%d", file_status.st_size);
	printf("<B>Written file</B> ./tmp.xml - <B>File Size:</B> %d<BR>", filesize);

But this always returns 0 bytes because st_size is not an int.

&#8216;crawler.c:120: warning: format &#8216;%llu&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 2 has type &#8216;__off_t&#8217;


How can I print type '__off_t'

---

### Post by thumper on 2006-03-07
Not an answer I'm afraid, but this sort of issue is one of the reasons I love C++ :)

---

### Post by thumper on 2006-03-07
Are you sure you're showing us the correct line?

The compiler shouldn't be changing your %d to a %llu

Just a guess, but perhaps the offset is just an unsigned long int, not an unsigned long long int.  Try %lu.

---

### Post by rydow on 2006-03-07
This works
File main.c looks like:
/************************************/
#include <stdio.h>
#include <sys/stat.h>
int main(){
   struct stat file_status;
   if(stat("main.c", &file_status) != 0){
     perror("could not stat");
   }
   printf("%d\n", file_status.st_size);
}
/************************************/
Are you sure that you actually get the file_status filled, you don't check the return of stat? 

/J

---

### Post by zootreeves on 2006-03-07
found the solution:

```
	 stat("./tmp.xml", &file_status);
	 printf("<BR><B>Written file</B> ./tmp.xml - <B>File Size:</B>%9jd Kb<BR><BR>", ((intmax_t)file_status.st_size) / 1024); 
```

I've got a new question now. Is is possible to run a shell command within a C program? I want to run curl (without using libcurl).

---

### Post by fct on 2006-03-07
man 3 exec (if you have manpages-dev installed)

---

### Post by zootreeves on 2006-03-07
Thanks that was just what i was looking for. One more question tho, i promise it will be the last one :)

How can i stop libcurl printing the result to screen, I would like it in a string instead.

```

  CURL *curl;

  curl = curl_easy_init();
  if(curl) {
    curl_easy_setopt(curl, CURLOPT_URL, "http://url.com");
    curl_easy_setopt(curl, CURLOPT_POST, 1);
    curl_easy_setopt(curl, CURLOPT_TRANSFERTEXT, 0);
    curl_easy_setopt(curl, CURLOPT_POSTFIELDS, data_forcurl);
    curl_easy_setopt(curl, CURLOPT_HEADER, 0);
    curl_easy_perform(curl);

    /* always cleanup */
    curl_easy_cleanup(curl);
  }

```

---

### Post by Codecaine_21 on 2010-11-14
.

---

### Post by worksofcraft on 2010-11-14
The following code
[LIST]
[*] opens a file
[*] determines it's size
[*] allocates memory for it
[*] reads the file to memory
[*] closes the file
[/LIST]

[php]
	char *AllData = NULL;
	int FD = open(FileName, O_RDONLY);
	if (FD < 0) {
		fprintf(stderr, "file %s open failed\n", FileName);
		return;
	}
	struct stat StatBuf;
	fstat(FD, &StatBuf);
	AllData = (char *) malloc(StatBuf.st_size+1); // + null terminator

	if (!read(FD, AllData, StatBuf.st_size)) {
		fprintf(stderr, "file read error\n");
	}
	AllData[StatBuf.st_size] = '\0';
	close(FD);
[/php]

p.s. with 20/20 hind-sight I see you should really check that malloc succeeded ;)

---

### Post by bouncingwilf on 2010-11-14
Try this bit of code, I googled this one as it was quicker than finding my own implementation!

/*
**  FLENGTH.C - a simple function using all ANSI-standard functions
**              to determine the size of a file.
**
**  Public domain by Bob Jarvis.
*/

#include <stdio.h>
#include <io.h>

long flength(char *fname)
{
      FILE *fptr;
      long length = 0L;

      fptr = fopen(fname, "rb");
      if(fptr != NULL)
      {
            fseek(fptr, 0L, SEEK_END);
            length = ftell(fptr);
            fclose(fptr);
      }

      return length;
}

#ifdef TEST

void main(int argc, char *argv[])
{
      printf("Length of %s = %ld\n", argv[0], flength(argv[0]));
}

#endif /* TEST */

---

