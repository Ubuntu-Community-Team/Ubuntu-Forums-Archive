---
title: "file in out tutorials [c]"
date: 2008-11-08
forum: Programming Talk
---

### Post by cmay on 2008-11-08
hi.
i am (still) learning c (by myself) and i am in need of a good tutorial on file handling. 
any pointers would by of great value.
thanks for the time.

---

### Post by LaRoza on 2008-11-08
> **cmay said:**
> 
any pointers would by of great value.


FILE * hereIsAFilePointer;

Ok, jokes aside, see my wiki. File handling is quite simple (which means, it isn't as convenient as other higher level languages). All the function are in stdio.h.

---

### Post by cmay on 2008-11-08
he. should have seen that coming. :)
what i am looking for is as example how to create a hidden folder or check if a folder exist. or see how many bytes there is in a file. and one more thing i really would like to know is how do i copy number of bytes to floppy only if floppy not already full ?
i been trying something to get the byte counts for the copying but...
i read the tutorials i could find on google . i think i may  found only the most basic file handling routines. 
i know this much already. but is there a already made function for this. 

[php]/* my copy_nbytes function ,can copy specified nr bytes from ->to file*/
#include <stdio.h>
int copy_nbytes(FILE *in,FILE *out,int max_bytes);
int main(int argc, char** argv)
{

    FILE *from=fopen(argv[1],"r");
    FILE *to=fopen(argv[2],"w");
        int byte_to_copy=502;
          if(argc != 3)
          {
              printf("print n_bytes from [file] to [file]\n");
              return 1;
        }
          if(from == NULL)
          {
            fprintf(stderr,"urggh opening %s failed",argv[1]);
           return 1;
            }else{
            fprintf(stdout,"%d bytes copied to %s\n",byte_to_copy,argv[2]);
                copy_nbytes(from,to,byte_to_copy);
            }

                fclose(from);
                 fclose(to);
    
    return 0;
}
int copy_nbytes(FILE *in,FILE *out,int max_bytes)
{
    int c;
    int nbyte=0;
 while((c=getc(in))!= EOF)
           {
                   nbyte++;
                   if(nbyte >= max_bytes)
                   {
                    c=EOF;
                }else{
                putc(c,out);
                }
            }
return 0;
}[/php]

---

### Post by dwhitney67 on 2008-11-08
You can use stat() or fstat() to get information about a file (or directory).

For example, to get the size of a file:
[php]
#include <sys/stat.h>
#include <stdio.h>


int main()
{
  const char* file = "/etc/hosts";
  struct stat buf;

  if (stat(file, &buf) == 0)
  {
    printf("file-size of %s is %u\n", file, (size_t)buf.st_size);
  }
  else
  {
    printf("error, cannot stat file %s\n", file);
  }

  return 0;
}
[/php]

Concerning the code you posted, if you already know the size of data you wish to read, don't waste CPU cycles reading the data one character at a time.  Use fread() to read in the data in one operation.  Then use fwrite() to write it to the other file.

P.S.  Hidden folders/files are named with a dot (.) in front of the name.  For example, .hidden.  You can create a directory using mkdir().

---

### Post by cmay on 2008-11-08
i do not know the size of the file(s) so i am very grateful for this information.
thanks.

---

### Post by cmay on 2008-11-09
[http://www.java2s.com/Code/C/CatalogC.htm](http://www.java2s.com/Code/C/CatalogC.htm)
i never seen the function mkdir anywhere so google found me this which is a good site with lots of examples i found i posted this for benefit of future readers of this tread.
however i see no mkdir() function in any headers anywhere. i found out that there is a rmdir also :) but i when i compile and run someting using mkdir or rmdir gcc complains  that "explicit declarition of funtion mkdir" on ubuntu 8,10 but not on open-solaris where gcc is  happy compiling using the funktions mkdir and rmdir in the programs. why is that .
sorry to bug you all again  i am just confused since i cant find these functions in any refences anywhere. 
thanks.

---

### Post by WW on 2008-11-09
For help with mkdir, check the manpage:
```

$ man 2 mkdir

```

---

### Post by cmay on 2008-11-09
thanks. this leaves me question if is the functions non standard. i use mostly books as reference since i do not see very well. i have a hard time reading from these man-pages in the terminal. so i may have avoided them :oops:. but i found the page. thanks. it helped a lot.

---

### Post by dwhitney67 on 2008-11-09
mkdir() is POSIX compliant.  I know that it is supported in *nix, and probably by Windoze.

---

### Post by cmay on 2008-11-09
thanks. i only have *nix or *nix-alikes so that is good to know.

---

### Post by WW on 2008-11-09
> **cmay said:**
> thanks. this leaves me question if is the functions non standard. i use mostly books as reference since i do not see very well. i have a hard time reading from these man-pages in the terminal.
Many manpages are also available on the web (e.g. [mkdir](http://unixhelp.ed.ac.uk/CGI/man-cgi?mkdir)), so you could adjust the font size in your browser to read them.

If you scroll down a ways in [this page](http://opengroup.org/onlinepubs/007908799/xsh/unistd.h.html), you can find a list of the functions declared in the standard header unistd.h, including, for example, rmdir() and chdir().  However, mkdir() is not there; I don't know the history of these functions, so I couldn't say why.

---

### Post by cmay on 2008-11-10
> **WW said:**
> Many manpages are also available on the web (e.g. [mkdir]("http://unixhelp.ed.ac.uk/CGI/man-cgi?mkdir")), so you could adjust the font size in your browser to read them.

If you scroll down a ways in [this page]("http://opengroup.org/onlinepubs/007908799/xsh/unistd.h.html"), you can find a list of the functions declared in the standard header unistd.h, including, for example, rmdir() and chdir().  However, mkdir() is not there; I don't know the history of these functions, so I couldn't say why.
thanks for all the help. i have just got a second hand copy of the book beginning linux programming 4 edition and i can see there is a lot about file handling  in that one. there is also the mkdir and rmdir functions explained .i am going to finish reading the k&r book first however. its not exactly a beginners book as far as i can tell. 
thanks a lot for your time.

---

### Post by dwhitney67 on 2008-11-10
Here's a link to the online manpages that I use on occasion:

[http://linuxmanpages.com/](http://linuxmanpages.com/)

If you visit the page and then click on System Calls, mkdir() is listed, along with the other system calls.

---

