---
title: "Am i doing something wrong?"
date: 2008-01-08
forum: Programming Talk
---

### Post by crashovaride on 2008-01-08
Hi all, 

I'm writing up an application to scan a file. Yet, i have checked (manually) and with grep to check for "ServerTokens" in my /etc/apache2/apache2.conf file; and my application returns 4 additional lines. Yet, when the counter returns the amount of occurrences it too, reports that there are 2. Can someone tell me if there is anything wrong with this block of code? Thanks.

main()
{

        FILE *f;
        f = fopen("/root/Desktop/test.txt","w+");
                fprintf(f, "Files found which Will be Scanned:\n");
        fclose(f);
        char buffer[256];
        FILE * readfile;
    printf("- Reading file /etc/apache2/apache2.conf\n");
    printf("* Scanning for banner grabbing information...\n");
        readfile = fopen("/etc/apache2/apache2.conf", "r");
                while (!feof(readfile))
                {
//        printf(strcmp("%sbuffer", "ServerTokens")==1);
                if (readfile == NULL,255);
                {
            int apache_count;
            apache_count = 1;
if (strcmp(buffer, "ServerTokens OS") ==1 || strcmp(buffer,"ServerTokens Full") ==1 || strcmp(buffer,"ServerTokens OS") ==1 || strcmp(buffer,"ServerTokens Minor") ==1 || strcmp(buffer, "ServerTokens Minimal") ==1 || strcmp(buffer,"ServerTokens Major") ==1 )
                        {
                apache_count++;
                printf("! Apache Configuration Error - Banner Data Available\n");
                        f = fopen("/root/Desktop/test.txt","a+");
fprintf(f, "! Apache2.conf not properly conigured for banner grabbing.\nPlease see: Site.com\n");
                        fclose(f);
            fflush(f);
                printf("Number of Apache Occurances: %d\n", apache_count);

                        }
                }
                        fgets(buffer, 256,readfile);
                }
        fclose(readfile);
        return 0;
}

I've tried pulling and making sense of EVERY post for strcmp, and file reading. And, from the mangled examples i've messed around with code until i got something to work. However, what is it that i'm seriously doing wrong? (when i created this post the text was formatted. I don't know what's going on.)

Thank you.

---

### Post by LaRoza on 2008-01-08
Use PHP or CODE tags when posting code...

---

### Post by xlinuks on 2008-01-08
LaRoza means you should always put the source code between the [code] .. [ /code] tags, otherwise it shows up on the page like spaghetti, thus being hard to be read/understood by those willing to help.

---

### Post by fyplinux on 2008-01-08
If you post the file that would be read, I think it would be better to understand the code,And  if you are willing to count some string using strcmp, the return value is** zero** if the two strings are equal.

---

### Post by Can+~ on 2008-01-08
> **crashovaride said:**
> Hi all, 

I'm writing up an application to scan a file. Yet, i have checked (manually) and with grep to check for "ServerTokens" in my /etc/apache2/apache2.conf file; and my application returns 4 additional lines. Yet, when the counter returns the amount of occurrences it too, reports that there are 2. Can someone tell me if there is anything wrong with this block of code? Thanks.

```
main()
{

        FILE *f;
        f = fopen("/root/Desktop/test.txt","w+");
                fprintf(f, "Files found which Will be Scanned:\n");
        fclose(f);
        char buffer[256];
        FILE * readfile;
    printf("- Reading file /etc/apache2/apache2.conf\n");
    printf("* Scanning for banner grabbing information...\n");
        readfile = fopen("/etc/apache2/apache2.conf", "r");
                while (!feof(readfile))
                {
//        printf(strcmp("%sbuffer", "ServerTokens")==1);
                **if (readfile == NULL,255);**
                {
            int apache_count;
            apache_count = 1;
if (strcmp(buffer, "ServerTokens OS") ==1 || strcmp(buffer,"ServerTokens Full") ==1 || strcmp(buffer,"ServerTokens OS") ==1 || strcmp(buffer,"ServerTokens Minor") ==1 || strcmp(buffer, "ServerTokens Minimal") ==1 || strcmp(buffer,"ServerTokens Major") ==1 )
                        {
                apache_count++;
                printf("! Apache Configuration Error - Banner Data Available\n");
                        f = fopen("/root/Desktop/test.txt","a+");
fprintf(f, "! Apache2.conf not properly conigured for banner grabbing.\nPlease see: Site.com\n");
                        fclose(f);
            fflush(f);
                printf("Number of Apache Occurances: %d\n", apache_count);

                        }
                }
                        fgets(buffer, 256,readfile);
                }
        fclose(readfile);
        return 0;
}
```

I've tried pulling and making sense of EVERY post for strcmp, and file reading. And, from the mangled examples i've messed around with code until i got something to work. However, what is it that i'm seriously doing wrong? (when i created this post the text was formatted. I don't know what's going on.)

Thank you.

Details:
1. For starters. main()?
int main(), specially, since you're returning a 0 in the end, but I guess you just miss-copied.

2. When loading a file, ALWAYS check if the file exists first, *f is a pointer to the file, if there's no file, *f is NULL.

3. You don't need strcmp(...) == 1, you can omit the == 1 to save some space.

4. When you get to the section "strcmp" and stuff, the variable named "buffer" has nothing on it, you should move the section where you do the fgets before the if, 

5. "if (readfile == NULL,255);". I'm guessing that you want to do this if readfile is different from NULL, so it must be:
if (readfile != NULL). Also, you added an extra ";" which.. basically skipped the { }.

6. I know what you want to do, you want to copy a portion of the file into a variable named buffer, to check for it's content. First of all, you should NOT use "strcmp", There's another function in string.h, which is "strstr" which looks for substrings. Here is the documentation: [http://www.acm.uiuc.edu/webmonkeys/book/c_guide/2.14.html#strstr](http://www.acm.uiuc.edu/webmonkeys/book/c_guide/2.14.html#strstr)

7. Do not open and close a file each time do you find a new string, Instead, save the counter, and in the end, write the file with the information, saving some speed.

8. When comparing strings is always good idea to throw everything into lowercase, use this function I made:

```
void stolower(char *str) //Convert strings to lowercase
{
	int l=strlen(str), i;
	for (i=0; i<l; i++)
		str[i] = tolower(str[i]);
}
```

---

### Post by Wybiral on 2008-01-08
I know it's commented out, but I'm really curious where this came from:
```

printf(strcmp("%sbuffer", "ServerTokens")==1);

```
BTW, I agree with the others, if you post your code between the code tags it will preserve your indentation and make it easier for us to read.

---

### Post by crashovaride on 2008-01-08
Whoa, i didn't know it was going to have so many posts. And, i really appreciate it =). I shall address as much of this post as i most possibly can. 

**fyplinux**
> If you post the file that would be read, I think it would be better to understand the code,And if you are willing to count some string using strcmp, the return value is zero if the two strings are equal.

*What i'm attempting to accomplish is that, any time a string is found matching the "ServerTokens" where too much information about the underlaying system can be exposed, display it; and count the occurrences. However, not only applying this to server tokens; but also applying it to following dangerous symbolic links, and other server side inconsistencies. =)*

**Can+~**
*I will try all the information in which you have posted to help better my source code; and i will most definitely respond with some information. As, i cannot perform these functions as of yet. However, i do have functions which kick off before the scanning of etc/apache2/apache2.conf file to see which apache is installed, and which file needs to be open. I use markers in the source code to determine which files to scan ;-) I will soon post the FULL code when ready. It's just a huge mess as of now and i didn't want to complicate the situation.*

**Wybiral**
> printf(strcmp("%sbuffer", "ServerTokens")==1);
*As i am new to C/C++ this was an experimental line to see if i can print the line where i found the inconsistency. Which, i'm still trying to figure out how to do in the console. lol. But, i'm getting close (i think...) If i got this far in writing the code blocks i'm pretty sure i can figure this out with a little blood and sweat, mental anxiety and break down. It's just the Ubuntu forums which help me along the way with little things like this. I know this line of code is wrong on so many levels, i hope i can figure it out.*

Anyway, once i finish the full application i will come back here and post it's code, and post the binary for everyone to use, modify and pass along; as this is what the open-source tradition is all about; and i want to keep this going. 

Thank you for all your help and support.

---

