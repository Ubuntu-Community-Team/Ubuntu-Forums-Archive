---
title: "How to delete all numbers from a text file - C"
date: 2011-07-26
forum: Programming Talk
---

### Post by stamatiou on 2011-07-26
Hey guys,
is there a way to have a text file in C and create a clone of that file but without the numbers?

---

### Post by ratcheer on 2011-07-26
Sure, but it would be a lot easier with any of several built-in commands, such as sed or tr.

Tim

---

### Post by stamatiou on 2011-07-26
> **ratcheer said:**
> Sure, but it would be a lot easier with any of several built-in commands, such as sed or tr.

Tim
How can I use theme? Can I have an example?

---

### Post by MadCow108 on 2011-07-26
if it really has to be C ;)
```
#include <stdlib.h>

int main(int argc, const char *argv[])
{
  system("sed \"s/[0-9]//g; w output-file\" input-file");
  return 0;
}

```
(no this is not how you should do it in C, but this is a task faster done using different tools like the used sed, google sed, stream-editor and regular expressions for more info)

---

### Post by stamatiou on 2011-07-26
Thank you very much! :p 
But does anyone know how to do it in C without the built-in commnads??

---

### Post by dwhitney67 on 2011-07-26
Yes, I know how to do it using C.  However I do not think that it would be appropriate for me to do your school work.

---

### Post by stamatiou on 2011-07-26
It is not my school work, I am just doing it for a hobby.:) Do you teach C at that early education?

---

### Post by Bachstelze on 2011-07-26
If you really want to...

```
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>

void remove_numbers(const char *ibuf, char* obuf)
{
        while (*ibuf != 0) {
                if (!isdigit(*ibuf)) {
                        *obuf = *ibuf;
                        obuf++;
                }
                ibuf++;
        }
        *obuf = 0;
}

void usage(char *s) {
        fprintf(stderr, "Usage: %s <filename>\n", s);
        exit(EXIT_FAILURE);
}

int main(int argc, char **argv)
{
        if (argc != 2) {
                usage(argv[0]);
        }

        FILE *ifile = fopen(argv[1], "r");
        if (ifile == NULL) {
                perror("Could not open input file");
                exit(EXIT_FAILURE);
        }

        char buf1[256];
        char buf2[256];
        while (fgets(buf1, 256, ifile) != NULL) {
                remove_numbers(buf1, buf2);
                fputs(buf2, stdout);
        }
        fclose(ifile);

        return EXIT_SUCCESS;
}

```

Reads the file and dumps it to stdout with all numbers removed:

```
firas@aoba ~ % cat foo.txt 
-----BEGIN RSA PRIVATE KEY-----
MIICXAIBAAKBgQDWkO0wwfo3n+8anMW4hCIGLM8wif6VRBfdxzbbe1RMBxEnWLrG
uV5jKL/uW7jc0nyarouJJLZEIQ3sWQiGwOoLfHZSSTelDwCbdpFExoc+uPU87Wpb
aipwKaDmlZXkwwSrWxMOav5AQENwOiQkG3veeo1npHWD479Lj9KIrZj3uwIDAQAB
AoGAGSkTd0U31y/89MzvboyoBLtabGGyJcS/W7VRnHkg0G1/uHJyLH1uMQiFQSkm
S1avX+AZ4rIYYXLS1CU4l7yldQ5aGsfaAqA2tSSpr1ZmLMVv2R73Pbq9YtA8yP9m
OW4Domt0MwiH3iijjdAX0YFOUiqt34hTXlCReJv6cmvS77kCQQDy0dYhluSASWzM
+BmAwdENkkqz2OVxUTouOJ1DTBwHQe6qMJvodOmJsCLgis/hTzKA4gX/gTtO+amd
/leHcp61AkEA4jZ8ShzJ8aPZgW4hYE2zXtDSnkpiSRem2r30xTS8oiRTY9Bo00D/
BSJCvD88AWrQyN3XbX5fTUJP6pkvCpbSrwJAHhuCj3ukLXvtL6T7lIlzoFkpRg94
s4o8yopehX+kYgn8y8FnM3V7l4TtbiYIDInDW1OrJrkhX3N5Yous0rCVmQJBAN+e
4Qsann9jbBbI2fGrng+y+yJDghmjaex/L8LrOTZIFq9rTNTZQcC/d51EHXuBLlgD
BX1WGbv0O7A8MgaTxj0CQENsQoirOUnnfgSF0Elhz7ZiAWf6tw8/p31BTSeC/Rnf
Zc8WnB/V3eyzfeZa09ABTGqcSFMzV7klCfSiKP6VA4c=
-----END RSA PRIVATE KEY-----
firas@aoba ~ % ./test foo.txt 
-----BEGIN RSA PRIVATE KEY-----
MIICXAIBAAKBgQDWkOwwfon+anMWhCIGLMwifVRBfdxzbbeRMBxEnWLrG
uVjKL/uWjcnyarouJJLZEIQsWQiGwOoLfHZSSTelDwCbdpFExoc+uPUWpb
aipwKaDmlZXkwwSrWxMOavAQENwOiQkGveeonpHWDLjKIrZjuwIDAQAB
AoGAGSkTdUy/MzvboyoBLtabGGyJcS/WVRnHkgG/uHJyLHuMQiFQSkm
SavX+AZrIYYXLSCUlyldQaGsfaAqAtSSprZmLMVvRPbqYtAyPm
OWDomtMwiHiijjdAXYFOUiqthTXlCReJvcmvSkCQQDydYhluSASWzM
+BmAwdENkkqzOVxUTouOJDTBwHQeqMJvodOmJsCLgis/hTzKAgX/gTtO+amd
/leHcpAkEAjZShzJaPZgWhYEzXtDSnkpiSRemrxTSoiRTYBoD/
BSJCvDAWrQyNXbXfTUJPpkvCpbSrwJAHhuCjukLXvtLTlIlzoFkpRg
soyopehX+kYgnyFnMVlTtbiYIDInDWOrJrkhXNYousrCVmQJBAN+e
QsannjbBbIfGrng+y+yJDghmjaex/LLrOTZIFqrTNTZQcC/dEHXuBLlgD
BXWGbvOAMgaTxjCQENsQoirOUnnfgSFElhzZiAWftw/pBTSeC/Rnf
ZcWnB/VeyzfeZaABTGqcSFMzVklCfSiKPVAc=
-----END RSA PRIVATE KEY-----

```

---

### Post by nvteighen on 2011-07-26
> **Bachstelze said:**
> 
```
firas@aoba ~ % cat foo.txt 
-----BEGIN RSA PRIVATE KEY-----
MIICXAIBAAKBgQDWkO0wwfo3n+8anMW4hCIGLM8wif6VRBfdxzbbe1RMBxEnWLrG
uV5jKL/uW7jc0nyarouJJLZEIQ3sWQiGwOoLfHZSSTelDwCbdpFExoc+uPU87Wpb
aipwKaDmlZXkwwSrWxMOav5AQENwOiQkG3veeo1npHWD479Lj9KIrZj3uwIDAQAB
AoGAGSkTd0U31y/89MzvboyoBLtabGGyJcS/W7VRnHkg0G1/uHJyLH1uMQiFQSkm
S1avX+AZ4rIYYXLS1CU4l7yldQ5aGsfaAqA2tSSpr1ZmLMVv2R73Pbq9YtA8yP9m
OW4Domt0MwiH3iijjdAX0YFOUiqt34hTXlCReJv6cmvS77kCQQDy0dYhluSASWzM
+BmAwdENkkqz2OVxUTouOJ1DTBwHQe6qMJvodOmJsCLgis/hTzKA4gX/gTtO+amd
/leHcp61AkEA4jZ8ShzJ8aPZgW4hYE2zXtDSnkpiSRem2r30xTS8oiRTY9Bo00D/
BSJCvD88AWrQyN3XbX5fTUJP6pkvCpbSrwJAHhuCj3ukLXvtL6T7lIlzoFkpRg94
s4o8yopehX+kYgn8y8FnM3V7l4TtbiYIDInDW1OrJrkhX3N5Yous0rCVmQJBAN+e
4Qsann9jbBbI2fGrng+y+yJDghmjaex/L8LrOTZIFq9rTNTZQcC/d51EHXuBLlgD
BX1WGbv0O7A8MgaTxj0CQENsQoirOUnnfgSF0Elhz7ZiAWf6tw8/p31BTSeC/Rnf
Zc8WnB/V3eyzfeZa09ABTGqcSFMzV7klCfSiKP6VA4c=
-----END RSA PRIVATE KEY-----

```

But... you've posted... an RSA **private** key!!??

Please tell me that this key was generated solely for this example.

---

### Post by Bachstelze on 2011-07-26
> **nvteighen said:**
> 
Please tell me that this key was generated solely for this example.

Why, no, I always keep my private key in a file named foo.txt and post it on forums, no one would think I am actually using it! Clever, no?

Seriously, yes, it's the quickest way I know to generate a large chunk of random ASCII.

---

### Post by nvteighen on 2011-07-26
> **Bachstelze said:**
> Why, no, I always keep my private key in a file named foo.txt and post it on forums, no one would think I am actually using it! Clever, no?

Seriously, yes, it's the quickest way I know to generate a large chunk of random ASCII.

Heh... ok... I've overreacted a bit :lolflag:

---

### Post by mikejonesey on 2011-07-26
trivial post but had to "lol" this

---

### Post by stamatiou on 2011-07-27
Thanks vary much!
But wouldn't this work? I mean the part that deletes from the file.
```
#include <stdio.h>

int delete(FILE *file,int a)    {
    int *ch,*temp;
    while(((char *)ch = fgetc(file)) != EOF)   {
        if((*ch) == a)    {
                temp = ch+1;
                ch = temp;
        }
        ch++;
    }
    return 0;
}

int main(void)    {
    FILE *file = fopen("file.txt","r+");
    delete(file,'\n');
    fclose(file);
    return 0;

```

---

### Post by Bachstelze on 2011-07-27
> **stamatiou said:**
> Thanks vary much!
But wouldn't this work? I mean the part that deletes from the file.
```
#include <stdio.h>

int delete(FILE *file,int a)    {
    int *ch,*temp;
    while(((char *)ch = fgetc(file)) != EOF)   {
        if((*ch) == a)    {
                temp = ch+1;
                ch = temp;
        }
        ch++;
    }
    return 0;
}

int main(void)    {
    FILE *file = fopen("file.txt","r+");
    delete(file,'\n');
    fclose(file);
    return 0;

```

fgetc() returns an int. You are assigning the return value to a char*. So I'd say that no, it would not work.

---

### Post by stamatiou on 2011-07-27
> **Bachstelze said:**
> fgetc() returns an int. You are assigning the return value to a char*. So I'd say that no, it would not work.
So it would be better like this?
```
#include <stdio.h>

int delete(FILE *file,int a)    {
    int *ch,*temp;
    while((ch = fgetc(file)) != EOF)   {
        if((*ch) == a)    {
                temp = ch+1;
                ch = temp;
        }
        ch++;
    }
    return 0;
}

int main(void)    {
    FILE *file = fopen("file.txt","r+");
    delete(file,'\n');
    fclose(file);
    return 0;
}

```
But this way I have some warnings:
```

del_from_file.c:5:12: warning: assignment makes pointer from integer without a cast
del_from_file.c:5:27: warning: comparison between pointer and integer

```

---

### Post by Bachstelze on 2011-07-27
No, now you are assigning the value to an int*.

---

### Post by stamatiou on 2011-07-27
Should it be with char like this?
```
#include <stdio.h>

int delete(FILE *file,int a)    {
    char *ch,*temp;
    while((ch = fgetc(file)) != EOF)   {
        if((*ch) == a)    {
                temp = ch+1;
                ch = temp;
        }
        ch++;
    }
    return 0;
}

int main(void)    {
    FILE *file = fopen("file.txt","r+");
    delete(file,'\n');
    fclose(file);
    return 0;
}

```
But the errors continue:
```

del_from_file.c:5:12: warning: assignment makes pointer from integer without a cast
del_from_file.c:5:27: warning: comparison between pointer and integer

```

---

### Post by Bachstelze on 2011-07-27
No, now you are assigning the value to a char*. ;) Why are you insisting on declaring your variables as pointers?

---

### Post by dwhitney67 on 2011-07-27
Something like:
```

int ch;
ch = fgetc(file);

```

What is your intent for the delete() function?  I see that you want to read each character from the file, and compare it to a certain character.  When there's a match, then you do something that baffles me.  What is it that you are trying to do?

---

### Post by Bachstelze on 2011-07-27
> **dwhitney67 said:**
> Something like:
```

int ch;
ch = fgetc(file);

```

What is your intent for the delete() function?  I see that you want to read each character from the file, and compare it to a certain character.  When there's a match, then you do something that baffles me.  What is it that you are trying to do?

He's probably trying to paraphrase the code I posted earlier, bur there seems to be a lot of confusion about how pointers work...

---

### Post by stamatiou on 2011-07-27
I would like if it finds the number to skip it. :confused:

---

### Post by Bachstelze on 2011-07-27
> **stamatiou said:**
> I would like if it finds the number to skip it. :confused:

You can't delete data from a file like that. If you want to modify the file in-place, you must first load the entire file into a memory buffer, delete the desired characters from the buffer and then write it to disk in place of the old file.

---

### Post by stamatiou on 2011-07-27
> **Bachstelze said:**
> He's probably trying to paraphrase the code I posted earlier, bur there seems to be a lot of confusion about how pointers work...
And the only way to do that is with the way you showed me?

---

### Post by Bachstelze on 2011-07-27
> **stamatiou said:**
> And the only way to do that is with the way you showed me?

No, the code I showed you works differently because it writes to the standard output, not back to the input file.

---

### Post by stamatiou on 2011-07-27
How can I load it to buffer and delete the characters?

---

### Post by Bachstelze on 2011-07-27
How about you try it by yourself, for a change? You know how to read data from disk and how to write it, that's all you need.

---

### Post by stamatiou on 2011-07-27
> **Bachstelze said:**
> How about you try it by yourself, for a change? You know how to read data from disk and how to write it, that's all you need.
Yes but the way I did it was wrong. And when you are telling buffer you mean text file or stdin or stddout? How will I delete the character?

---

### Post by dwhitney67 on 2011-07-27
The word buffer typically implies a storage area; for example an array.

A file stream can be standard-in, -out, -error, or even an actual file.

The point of your exercise is to open a file, read it (whether character by character or into a buffer), and then to commit each character in this file to another *file*, with the exception of characters found to be representative of a numeric character (0-9).

Bachstelze has already shown you how to do this, with the output *file* being standard-out.  If your intent is to replace the original file, then I would suggest that you create a temporary file, write to it only the characters have any interest to you, and then when done, overwrite the original file with the temporary file.

It is impractical to consider allocating a buffer to store the entire file, unless you know that the file is below a certain size.  Obviously a 4GB file would exceed the capabilities of the typical/average systems available today.

Personally, I would open two files, one containing the source information, the other for writing the reduced information set.

---

### Post by Bachstelze on 2011-07-27
A "buffer" in programming generally means an area of memory where data is stored for manipulation after being read and/or before being written. Basically what you want to do is:

1. Allocate one memory area (buffer) as large as the input file
2. Read the data form the file into the buffer
3. Read characters from the buffer: if a character matches what you want to keep, write it to the file, otherwise skip it

*EDIT:* Of course if the file is very large or there are other hurdles, adapt as appropritate. In general, though, the standard way is really to write to stdout: if you want to write to a file, you use the stream redirection facilities of your shell.

---

