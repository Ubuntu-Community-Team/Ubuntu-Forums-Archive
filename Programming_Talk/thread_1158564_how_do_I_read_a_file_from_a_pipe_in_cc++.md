---
title: "how do I read a file from a pipe in c/c++"
date: 2009-05-13
forum: Programming Talk
---

### Post by monkeyking on 2009-05-13
Alot of sys program allows you to use pipe your output to input in another program.
How do i implement this in my own program.

I've read on the net something like, but it doesn't really work

thanks in advance

[PHP]
#include <iostream>
#include <map>
#include <cstring>
#include <unistd.h>

#define LENS 1000

int main(){
  
  int pfds[2];
  char buf[LENS];
  pipe(pfds);
  int stop=0;
  while(stop++<5){
    read(pfds[1],buf,LENS);
    printf("%s\n",buf);
  }
}
[/PHP]

---

### Post by Zugzwang on 2009-05-14
You just read your data from "stdin" and print your stuff out to "stdout". That's it! Most programs do this only when there is not input/output filename given as parameter to the program, respectively.

---

### Post by Joeb454 on 2009-05-14
bash should implement the redirecting for you, as long as you read your data from stdin, then it should work

---

### Post by monkeyking on 2009-05-26
I find an extreme time difference using stdin and a file,
less that 5 sec vs almost 2 minutes.
This can't be the way to do it,
does anyone know how to speed up the process?

```

time ./a.out 59846/59846.txt
#       59846/59846.txt
18255221

real    0m4.321s
user    0m2.884s
sys     0m1.424s
time ./a.out <59846/59846.txt
18255221

real    1m56.544s
user    1m55.043s
sys     0m1.512s

```





[PHP]
/*
  if a argument is supplied it will use the file
  otherwise stdin
*/

#include <iostream>
#include <fstream>


#define LENS 10000

int main(int argc, char **argv){
  std::istream *pFile;

  if(argc==2)//ifargument supplied
    pFile = new std::ifstream(argv[1],std::ios::in);
  else //if we want to use stdin
    pFile = &std::cin;

  char line[LENS];
  if(argc==2) //if we are using a filename, print it.
    printf("#\t%s\n",argv[1]);

  if(!pFile){
    printf("Do you have permission to open file?\n");
    return 0;
  }

  int numRow=0;
  while(!pFile->eof()) {
    numRow++;
    pFile->getline(line,LENS);
  }
  if(argc==2)
    delete pFile;
  printf("%d\n",numRow);
  return 0;
}
[/PHP]

---

### Post by ibuclaw on 2009-05-26
Actually there is not much you can do on optimising that.

When you read from a file from disk, Linux caches the file, so next time it is read, you are reading from RAM instead of disk, which ultimately improves access/read speed.

This is contrary to reading from stdin as you cannot cache a stream.

ie:
```

iain@jstdio:~$ time ./a.out testfile
#	testfile
235152

real	0m1.215s
user	0m0.168s
sys	0m0.140s
iain@jstdio:~$ time ./a.out testfile
#	testfile
235152

real	0m0.192s
user	0m0.144s
sys	0m0.044s
iain@jstdio:~$ time ./a.out < testfile
235152

real	0m2.766s
user	0m2.736s
sys	0m0.012s
iain@jstdio:~$ time ./a.out < testfile
235152

real	0m2.742s
user	0m2.700s
sys	0m0.032s

```

Although, looking at similar implementations of "line counting" applications (wc, written in C). I may just conclude that either std::istream or getline() are extremely sub-optimal altogether, and you should just read it a character at a time manually, rather than rely on high-end functions.

Regards
Iain

---

### Post by monkeyking on 2009-05-26
Thanks,
I'll look at the single char reading.

---

### Post by soltanis on 2009-05-26
You also cannot seek in pipes.

This is why a lot of programs have the option of "I'll read from a file, or if you don't specify one, I'll read from stdin."

I suggest you write your application like that, since it offers the most flexibility.

As for speeding up the I/O process, not much you can really do about that.

---

### Post by ibuclaw on 2009-05-27
I dusted down my C skills, and came up with this:
[PHP]
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>

#define BUFFER_SIZE (16 * 1024)

extern int optind;

static int read_stream(int fd)
{
    size_t bytes_read;
    char buf[BUFFER_SIZE + 1];
    int lines = 0;

    while((bytes_read = read(fd, buf, BUFFER_SIZE)) > 0)
    {
        const char *p = buf;
        do
        {
            if(*p++ == '\n')
                lines++;
        } while(--bytes_read);
    }
    return lines;
}

int main (int argc, char **argv)
{
    if(optind == argc)
        /* Read from stdin */
        printf("%d\n", read_stream(0));
    else
        /* Read from file */
        for(; optind < argc; optind++)
        {
            int fd = open(argv[optind], O_RDONLY);
            printf("#\t%s\n%d\n", argv[optind], read_stream(fd));
            close(fd);
        }
    return 0;
}
[/PHP]

Increasing the BUFFER_SIZE saw improvements in stdin read speed.
```

iain@jstdio:~$ time ./a.out testfile 
#	testfile
235151

real	0m0.168s
user	0m0.132s
sys	0m0.024s
iain@jstdio:~$ time ./a.out testfile 
#	testfile
235151

real	0m0.147s
user	0m0.128s
sys	0m0.008s
iain@jstdio:~$ time ./a.out < testfile
235151

real	0m0.186s
user	0m0.152s
sys	0m0.020s
iain@jstdio:~$ time ./a.out < testfile 
235151

real	0m0.170s
user	0m0.132s
sys	0m0.024s

```

If you have any question, just ask.

Regards
Iain

---

