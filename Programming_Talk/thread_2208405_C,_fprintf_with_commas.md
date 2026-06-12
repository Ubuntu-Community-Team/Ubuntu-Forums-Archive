---
title: "C, fprintf with commas"
date: 2014-02-28
forum: Programming Talk
---

### Post by squakie on 2014-02-28
I need to write a "record" to a file that is in this syntax"

var1,var2,var3,var4

I literally need the commas in the file.

I've tried strcat with ",", but when I printf the resulting string for testing I get:

var1var2var3var4

I've tried fprintf with "%s%s%s%s%s%s%s\n" and var1, ",", var2, ",", var3, ",", var4, but then it's like there is a newline between each variable and no commas print:
var1
var2
var3
var4

I'm not the sharpest knife in the drawer, and especilly when it comes to C.  But surely there has to be a way for me to write to a file as:

var1,var2,var3,var4 and newline

I have no clue how to do it and could really use some help.  I'm back to being a novice at this so try to be gentle ;)

---

### Post by ofnuts on 2014-02-28
And 

```

fprintf(file,"%s,%s,%s,%s\n",var1,var2,var3,var4)

```

Doesn't work (assuming your variables are strings)?

---

### Post by squakie on 2014-02-28
the variables are string arrays, if that makes any difference.  If I want to trim traling spaces, how do I do the compare of var[x] to space?  I've tried ' ' and decrement "x" but it seems to go forever until I get a segment overflow ("x" has gone to a large negative number).

I *used* to know C - that was over 20 years ago.  I don't know squat now, so I'm really starting over completely from scratch.

Thanks!

---

### Post by trent.josephsen on 2014-02-28
In that case it might be good to post the actual code you're working on. It's hard to say what you might be doing wrong otherwise, since both strcat and fprintf will work if used correctly.

Here's a snippet that will chop off the end of a string starting at the **first** space -- i.e. it transforms "hello, world " into "hello,". I'm lazy, so I won't do the whole "go to the end of the string, then go back to the last space following a non-space" algorithm to do space-trimming the right way, but it's a start:
```
str s[] = "hello, world ";
int i = 0;
//puts(s);
while (s[i] != ' ') {
    i++;
}
s[i] = '\0';
//puts(s);
```

And for good measure, here's an oddly specific function borrowed from Perl that removes the last character (and only the last) from a string only if that character is a newline. It often comes in handy when using fgets(), but I post it here just for illustrative purposes -- it uses both pointer arithmetic and indexing. I'm not sure what I should try to explain about this code, but if you post questions I'll try to answer them when I can. Hope it helps.
```
int chomp(char *s)
{
    if (s == NULL || *s == '\0') {
        /* this is here to prevent bad stuff if someone calls chomp("") or chomp(NULL) */
        return 0;
    }
    while (*s) {
        s++;
    }
    if (s[-1] == '\n') {
        s[-1] = '\0';
        return 1;
    }
    return 0;
}
```

---

### Post by squakie on 2014-02-28
given:

   ```
wrk_string1 = csv_last_name;
   strcat(wrk_string1,  "    ");
   strcat(wrk_string1, csv_first_name);

   fprintf(outfile,"%s,%s,%s,%s\n",wrk_string1,csv_last_name, csv_first_name, csv_email );
```

I get:

```
lname    fname
,lname    fname
,lname
,fname
,email
```

I should be getting:

```
lname    fname,lname,fname,email
```

I use functions pretty much the same as this to load the variables:
```
oid type_Name()
{

   memset(csv_name, '\0', my_size);
   memset(csv_last_name, '\0', my_size);
   memset(csv_first_name, '\0', my_size);
   ++wrk1;
   wrk2 = strlen(my_input_string);
   wrk3 = wrk2 - wrk1;
   if ( wrk3 > 0)
      {
          memcpy(csv_name, my_input_string + wrk1, wrk3);
          wrk1 = strcspn(csv_name, ",");
          wrk2 = strlen(csv_name);
          memcpy(csv_last_name, csv_name, wrk1);
          wrk3 = wrk2 - wrk1;
          if ( wrk3 > 2)
            {
                wrk1 = wrk1 + 2;
                memcpy(csv_first_name,csv_name + wrk1, wrk3);
            }
      }
wrk1 = strlen(csv_last_name);
wrk2 = strlen(csv_first_name);
printf("lname length: %d, fname length: %d\n",wrk1, wrk2);


}
```

where the variables are defined as:```
char csv_email[my_size];
char csv_alias[my_size];
char csv_name[my_size];
char csv_last_name[my_size];
char csv_first_name[my_size];
char csv_primary_phone[my_size];
char csv_address[my_size];
char csv_birth[my_size];
char csv_deleted[my_size];
```

When I look at the output file in gedit and click beyond the last character in a line it goes back to right after the last character, so there are no trailing spaces that I can tell.

Sorry this is so long, but if I can get this part working I'll be able to convert my brother in-law's Juno address book to a comma sepearate values file I can then use to import the converted address book to another email program.

Thanks for your patience, and thanks for understanding I'm just very green on this now.

---

### Post by squakie on 2014-02-28
BTW - thanks so much for the help.  I'm head off to bed now as I've been up all night trying to figure this out, and it's now 7:30 a.m. and I need to get at least a little sleep ;)

---

### Post by trent.josephsen on 2014-02-28
(Are you sure that output comes from that code? The code prints 3 commas, the output has 4. If that's right, it means your data has commas in it.)

I'm a bit occupied today as well, so I can't give it my full attention, but it looks like at least some of your strings have newlines in them. Maybe that chomp() function I wrote up above could be useful to you after all. Try putting calls to chomp(csv_whatever) at the bottom of type_Name(), before you do any processing, and see how it affects the output.

Declarations and initialization code for wrk1, wrk2, wrk3 and my_input_string would be helpful as well.

Ok, now one thing you should realize about this code:
```
   wrk_string1 = csv_last_name;
   strcat(wrk_string1,  "    ");
   strcat(wrk_string1, csv_first_name);
```
is that the assignment doesn't copy the string; it merely copies a pointer to its first character. (I'm assuming wrk_string1 is of type char *, because that's the only thing that makes sense here.) After the first line, wrk_string1 and csv_last_name refer to the same string, and strcat() doesn't know the difference, so you change both at once. If you printf("csv_last_name: <%s>\n", csv_last_name) after this point, you'll see csv_last_name now contains csv_first_name as well.

To avoid this, you can allocate a new buffer and strcpy the old string into it, but I'd instead use sprintf in a manner similar to the following:
```
char wrk_string1[1500]; /* make it big, it ain't 1990 anymore */
sprintf(wrk_string1, "%s    %s", csv_last_name, csv_first_name);
```

(Actually, I would use snprintf for safety, but that's ok, this is a one-off, right?)

In fact, if that's all you're doing to generate wrk_string1, just wrap it into your fprintf string:
```
fprintf(outfile, "%s    %s,%s,%s,%s\n", csv_last_name, csv_first_name, csv_last_name, csv_first_name, csv_email);
```

---

### Post by ofnuts on 2014-02-28
> **squakie said:**
> given:

   ```
wrk_string1 = csv_last_name;
   strcat(wrk_string1,  "    ");
   strcat(wrk_string1, csv_first_name);

   fprintf(outfile,"%s,%s,%s,%s\n",wrk_string1,csv_last_name, csv_first_name, csv_email );
```

I get:

```
lname    fname
,lname    fname
,lname
,fname
,email
```

I should be getting:

```
lname    fname,lname,fname,email
```


If you get this, it means you have remaining linefeeds in your data...

---

### Post by squakie on 2014-02-28
Well, I tried creating just a test file for input via gedit so I know where everything terminates: ```
Type:Entry 
Email:myemal@mine.com 
Alias: 
Name:last name   first name 
Primary Phone:my phone 
Birth:my birth 
Address:my address 
Deleted:0 
Time:1300446059 
 

``` and that's a copy/paste from the editor.

I ran the program with a printf to echo what it's picking up and generating for the name:```

/**************************************************
*   Process "Name:"
**************************************************/

void type_Name()
{

   memset(csv_name, '\0', my_size);
   memset(csv_last_name, '\0', my_size);
   memset(csv_first_name, '\0', my_size);
   ++wrk1;
   wrk2 = strlen(my_input_string);
   wrk3 = wrk2 - wrk1;
printf("\nat name, %s, start: %d, length: %d, num to copy: %d\n\n",my_input_string, wrk1, wrk2, wrk3);
   if ( wrk3 > 0)
      {
          memcpy(csv_name, my_input_string + wrk1, wrk3);
          wrk1 = strcspn(csv_name, ",");
          wrk2 = strlen(csv_name);
          memcpy(csv_last_name, csv_name, wrk1);
          wrk3 = wrk2 - wrk1;
          if ( wrk3 > 2)
            {
                wrk1 = wrk1 + 2;
                memcpy(csv_first_name,csv_name + wrk1, wrk3);
            }
      }


}
```

This is the output from the printf:```
at name, Name:last name   first name
, start: 5, length: 29, num to copy: 24
```

Note how right there the name string is goofed all ready - there shouldn't be a newline after "first name".  The length of the entire string (29, the value of wrk2 in the code) is correct.  Where I want to start (5, the value of wrk1 in the code) is correct.  The number of characters I want to move (24, wrk3 in the code) is correct.  It is starting at 5 since the input line that gets to here is:```
Name:last name   first name 
```.  I parse until the first ":" to know the statement it found, then execute the code based on that string, in this case "Name:".  Coming into the name function, wrk1 is at 4, indicating where it found the ":", so it is incremented to get past the ":".

I don't know if that helps or not.  I've got to be doing something extremely stupid wrong, but I just don't know.

If you would prefer I not ask this in the forum (perhaps it's meant for people who actually know what they are doing first ;) ) just let me know.

Thanks again SO much!





This is the output file:```
Name,EmailAddress,FirstName,LastName
last name   first name 
    ,myemal@mine.com 
,
```

And finally, the output was generated by this code, which I had commented out while testing the fprintf as per above:```

/************************************************
*   Create CSV entry    
************************************************/

void create_CSV()
{

/*  Format:  Name,EmailAddress,FirstName,LastName  */


   wrk1 = 0;
   wrk2 = strlen(csv_last_name);
   while( wrk1 < wrk2)
      {
         fputc(csv_last_name[wrk1],outfile);
         ++wrk1;
      }
   wrk1 = 0;
   while (wrk1 < 4)
      {
         fputc(' ',outfile);
         ++wrk1;
      }
   wrk1 = 0;
   wrk2 = strlen(csv_first_name);
   while (wrk1 < wrk2)
      {
         fputc(csv_first_name[wrk1], outfile);
         ++wrk1;
      }
   fputc(',',outfile);

   wrk1 = 0;
   wrk2 = strlen(csv_email);
   while (wrk1 < wrk2)
      {
         fputc(csv_email[wrk1], outfile);
         ++wrk1;
      }
   fputc(',',outfile);    


}
```


EDIT:  I just noticed, by doing some more testing, that all of the generated strings appear to be having the same problem, as can be witnessed by the email address, an apparently long string so it does a newline, followed by it's terminating comma.  Perhaps I'm doing something wrong with the memcpy statements?  My understanding was that it would only copy the number of characters (wrk3 in the code) from the input string to the output string.  Since I memset each output string to all '\0' before doing the memcpy, I assumed i would end up with a string output after the memcpy - if memcpy just copies that number of character the "preloaded" '\0' should terminate the output right after the number of characters are moved.  Least wise I hope so.  There can't be any extra newlines in the input as I created it right in gedit.

---

### Post by steeldriver on 2014-02-28
What exactly are you trying to do? If you are just wanting to read and tokenize lines of input based on a colon separator your code seems unnecessarily obfuscated. Or am I misunderstanding the point  of the exercise?

---

### Post by squakie on 2014-02-28
Okay I did a dump of the input file:```
dave@davePC:~/juno-address-book$ hexdump -C test-addrbook.nv
00000000  54 79 70 65 3a 45 6e 74  72 79 0d 0a 45 6d 61 69  |Type:Entry..Emai|
00000010  6c 3a 6d 79 65 6d 61 6c  40 6d 69 6e 65 2e 63 6f  |l:myemal@mine.co|
00000020  6d 0d 0a 41 6c 69 61 73  3a 0d 0a 4e 61 6d 65 3a  |m..Alias:..Name:|
00000030  6c 61 73 74 20 6e 61 6d  65 2c 20 66 69 72 73 74  |last name, first|
00000040  20 6e 61 6d 65 0d 0a 50  72 69 6d 61 72 79 20 50  | name..Primary P|
00000050  68 6f 6e 65 3a 6d 79 20  70 68 6f 6e 65 0d 0a 42  |hone:my phone..B|
00000060  69 72 74 68 3a 6d 79 20  62 69 72 74 68 0d 0a 41  |irth:my birth..A|
00000070  64 64 72 65 73 73 3a 6d  79 20 61 64 64 72 65 73  |ddress:my addres|
00000080  73 0d 0a 44 65 6c 65 74  65 64 3a 30 0d 0a 54 69  |s..Deleted:0..Ti|
00000090  6d 65 3a 31 33 30 30 34  34 36 30 35 39 0d 0a 0d  |me:1300446059...|
000000a0  0a 0d 0a                                          |...|
000000a3
dave@davePC:~/juno-address-book$ 
```

Obviously the input "lines" are terminated by newlines since they came from the editor.


And a dump of the output file:```
dave@davePC:~/juno-address-book$ hexdump -C test-addr-book.txt
00000000  4e 61 6d 65 2c 45 6d 61  69 6c 41 64 64 72 65 73  |Name,EmailAddres|
00000010  73 2c 46 69 72 73 74 4e  61 6d 65 2c 4c 61 73 74  |s,FirstName,Last|
00000020  4e 61 6d 65 0a 6c 61 73  74 20 6e 61 6d 65 20 20  |Name.last name  |
00000030  20 20 66 69 72 73 74 20  6e 61 6d 65 0d 0a 2c 6d  |  first name..,m|
00000040  79 65 6d 61 6c 40 6d 69  6e 65 2e 63 6f 6d 0d 0a  |yemal@mine.com..|
00000050  2c                                                |,|
00000051
dave@davePC:~/juno-address-book$ 
```
There are newlines (the 0d 0a in the dump) at the end of the first name and the email address, indicating to me, since I use pretty much the same code to generate all the string, that somehow I am adding the newlines to the output.  Since the 0d 0a are not '\0', they are included in the input string, so the length I calculate (wrk2 in the code) should actually be the strlen of the string minus 2.  I'll be making those changes to my code.  Someone mentioned this earlier and I should have dumped the files then so I could have verified it then.


EDIT:  made the changes in the code - IT WORK!!

Thanks SO much to everyone!!

---

### Post by ofnuts on 2014-02-28
Blindly removing 2 is fraught with peril. You get this because the file comes from a Windows system, but any kind of edit on a Linux may replace the line ends with just '\n' (and maybe '\r' on OSX). Either make your code more careful, or run the "fromdos" command on the file when you import it, it will convert the line ends to the Linux convention.

---

### Post by dwhitney67 on 2014-02-28
> **squakie said:**
> 
EDIT:  I just noticed, by doing some more testing, that all of the generated strings appear to be having the same problem, as can be witnessed by the email address, an apparently long string so it does a newline, followed by it's terminating comma.  Perhaps I'm doing something wrong with the memcpy statements?  My understanding was that it would only copy the number of characters (wrk3 in the code) from the input string to the output string.  Since I memset each output string to all '\0' before doing the memcpy, I assumed i would end up with a string output after the memcpy - if memcpy just copies that number of character the "preloaded" '\0' should terminate the output right after the number of characters are moved.  Least wise I hope so.  There can't be any extra newlines in the input as I created it right in gedit.

I understood from your earlier post that you are re-learning C.  You should stick to simple string manipulator functions rather than fiddle with memcpy() or even print out individual characters using fputc().

Make these functions your friends:  strncpy(), sscanf(), fgets(), and strchr().

Here's a program that ingests a simple data file (similar to the one you presented in the post that I'm quoting above), and prints to standard-out a CSV representation of the data.

```

#include <string.h>
#include <stdio.h>

void extract_data_str(FILE* file, char* data, int data_len);
void extract_data_val(FILE* file, int* data);

void get_data_str(char* line, char* data, int max_len);
void get_data_val(char* line, int* data);

void remove_newline(char* line);


int main(int argc, char** argv)
{
	if (argc != 2)
	{
		fprintf(stderr, "Usage: %s <data file>\n", argv[0]);
		return -1;
	}

	FILE* file = fopen(argv[1], "r");

	if (file)
	{
		char type[80]  = {0};
		char email[80] = {0};
		char alias[80] = {0};
		char name[80]  = {0};
		char phone[80] = {0};
		char birth[80] = {0};
		char addr[80]  = {0};
		int  deleted;
		int  time;

		extract_data_str(file, type,  sizeof(type));
		extract_data_str(file, email, sizeof(email));
		extract_data_str(file, alias, sizeof(alias));
		extract_data_str(file, name,  sizeof(name));
		extract_data_str(file, phone, sizeof(phone));
		extract_data_str(file, birth, sizeof(birth));
		extract_data_str(file, addr,  sizeof(addr));

		extract_data_val(file, &deleted);
		extract_data_val(file, &time);

		fprintf(stdout, "%s,%s,%s,%s,%s,%s,%s,%d,%d\n",
		        type, email, alias, name, phone, birth, addr, deleted, time);

		fclose(file);
	}
	else
	{
		fprintf(stderr, "Cannot open file %s.\n", argv[1]);
		return -1;
	}
	return 0;
}

void extract_data_str(FILE* file, char* data, int data_len)
{
	char line[data_len * 2];
	fgets(line, sizeof(line), file);
	remove_newline(line);
	get_data_str(line, data, data_len);

}

void extract_data_val(FILE* file, int* data)
{
	char line[64];
	fgets(line, sizeof(line), file);
	remove_newline(line);
	get_data_val(line, data);
}

void get_data_str(char* line, char* str, int max_len)
{
	char* colon = strchr(line, ':');
	if (colon)
	{
		strncpy(str, colon + 1, max_len);
	}
	else
	{
		strncpy(str, line, max_len);
	}
}

void get_data_val(char* line, int* val)
{
	char* colon = strchr(line, ':');
	if (colon)
	{
		sscanf(colon + 1, "%d", val);
	}
	else
	{
		sscanf(line, "%d", val);
	}
}

void remove_newline(char* line)
{
	char* nl = strchr(line, '\n');
	if (nl)
	{
		*nl = '\0';
	}
}

```

Note: The program above assumes that if there are newlines in the file, that they are Linux-style newlines.

---

### Post by squakie on 2014-02-28
Well, I'll have to modify some code so I check for all 4 posdibilities at the end and back up accordingly.  

As far as memcpy goes, I didn't use strncpy as what I read on the net sounded like it didn't null terminate the string.  So first I initialize the string to all nulls (at least I'm assuming that's what I'm doing), then when I used the memcpy I know what ever I copy in will be followed by a null, so there will be a string terminate, and so I can then access the output as a string.

It *was* working just fine.  Then I tried to add an fprintf in place of my output code, and everything went "wacky".  I'm getting so many errors in compilation now that don't even make sense - it's saying things about the code that aren't there, things like multiple definitions of a string or function.  So now I really don't understand what I've done.  I've got to go back and reset all the code I *think* I changed.  I was relying on the backup file from gedit (the ~ file), but I forgot to save a copy somewhere along the line before starting the changes so now I don't have a copy before all the changes.  I'm stupid.

---

### Post by squakie on 2014-02-28
I'm just trying to read the file one "line" at a time, parse it, format the output strings, then write out a record.

At first I wasn't sure if "my_input_string" is actually null terminated, so I used the "move this many characters" thing via memcpy and made sure it was null terminated after.

I'm starting to think now that it might be null terminated, which would make my life easier indeed.

However, before I can go back and test that, I need to find out what the heck errors like the following mean.  They are coming from things that aren't in my code - I assume in some intermediary file(s) the compiler generates:
```
dave@davePC:~/juno-address-book$ gcc nvconvert.c nvconvert
nvconvert: In function `type_Email':
(.text+0x2fd): multiple definition of `type_Email'
/tmp/cchG0agW.o:nvconvert.c:(.text+0x203): first defined here
nvconvert: In function `type_Primary_Phone':
(.text+0x579): multiple definition of `type_Primary_Phone'
/tmp/cchG0agW.o:nvconvert.c:(.text+0x44f): first defined here
nvconvert: In function `type_Deleted':
(.text+0x705): multiple definition of `type_Deleted'
/tmp/cchG0agW.o:nvconvert.c:(.text+0x5db): first defined here
nvconvert: In function `type_Time':
(.text+0x789): multiple definition of `type_Time'
/tmp/cchG0agW.o:nvconvert.c:(.text+0x65f): first defined here
nvconvert: In function `type_Address':
(.text+0x681): multiple definition of `type_Address'
/tmp/cchG0agW.o:nvconvert.c:(.text+0x557): first defined here
nvconvert:(.bss+0x10): multiple definition of `wrk4'
/tmp/cchG0agW.o:(.bss+0xc): first defined here
nvconvert:(.bss+0x8): multiple definition of `wrk2'
/tmp/cchG0agW.o:(.bss+0x4): first defined here
nvconvert: In function `_fini':
(.fini+0x0): multiple definition of `_fini'

```

I don't understand what I did to make all of that come up.  There is a LOT more listed after the above, but I suspect if I can find out what the heck caused the above and correct it that the rest will follow suit.

As you can tell, I'm really lost now.

---

### Post by steeldriver on 2014-02-28
Did you perhaps mean

```
gcc nconvert.c **-o** nconvert
```

---

### Post by squakie on 2014-02-28
That's what I *thought* I was doing, but you never know.....so, I went back, cleared the screen, did the gcc as shown and still get these odd errors.  The source looks fine.  The errors are coming from things not directly in my program.  I can't even test until I can get rid of those.

You know, it's been 20 years since I used C  except for a few projects here and there.  I've obviously forgotten more than I ever knew, and I sometimes get the feeling that what I *think* is right is something getting scrambled up with something from 20 years ago and it ends up a mess.

I'm so sorry that I am so stupid on all of this.  As I mentioned before, since I am starting over "green", if this isn't the correct place to post this please let me know.

Again, thanks everyone!

---

### Post by squakie on 2014-02-28
stelldriver you were 100% correct on the gcc line.  I *still* made that mistake and didn't catch it.  So I went back and checked again, and indeed I didn't include the "-o ".  It compiles now, and everything I've done so far is working, except that I need to do the truncation of the end-of-line character(s).  I'm going to try that now.

THANKS!!!

---

### Post by squakie on 2014-02-28
Okay, I think that's got is for now.  I'm okay backing up 2 characters on the end of line because the input file is a Juno address book file, and Juno (in this case) is running on a Windows box, so when I copied the file to flash and brought it to my linux box to try to do this the file is still in dos format with the cr/lf's at the end of the line.

I'm not sure how you code something to where you can say if the string contains 1 of these characters (the various end of line characters) then give me an index to it.  To make the code more adaptable for others I should probably do that.

I also don't remember squat about getting and using command line variables, so I've got to work on that as well.

So, everything is "okay" to the best I can tell right now - I just need to do some more work!

Thanks!

---

### Post by squakie on 2014-02-28
BTW - does anyone know where I can find a definition of all the tags the online gmail expects in an impor?  I know the first line of the file has to contain those names in a comma-seperated format - I just don't know what all of those field names are.

---

### Post by squakie on 2014-02-28
Well, stupid me.  All I had to do was go to my gmail account an export my address book.  That gave me the initial string showing the field names so now I can build the entire thing for my brother in-law.

---

### Post by squakie on 2014-03-01
1 more question:

how do I output a single comma to a file?

I've tried:

fprintf(outfile,",");

but the compiler flags it as an error at the first quote.

So I tried:

fputc(',',outfile);

but the compiler gets upset a the first single quote.

I tried:

char my_comma[] = ",";

then using:

fputc(my_comma[0], outfile);

but the compile gets upset at the "m" of my_comma[0].

This seems like it should be the simplest thing to do, but I can figure it out.

Any help would be GREATLY appreciated!

---

### Post by squakie on 2014-03-01
Found a stray "}" in the middle of the code - removed that and don't have any problem fprintf'ing the commas.

In fact, the entire thing seems to be working right now - I limported the output to my "testing" gmail account contacts and it appears to be want I think my brother in-law wants.  It's a little strange - gmail contacts main screen only shows the last name followed by the email address.  When there is a name like "Ibe Me" it only showed up as "Me".  I had to combine the first name and last name from the input to make the output - so it at least shows "Ibe Me" followed by the email address.  The actual contact card obviously looks really strange.

So, for the limited number of fields that show in my brother in-law's Juno address book of type .nv, I can read it, partse it, and create output that can be imported to the gmail contacts list.  That's doing what I need it to do.

If anyone wants a copy of it to expand it to include the possible fields from a full Juno address entry, or to add other formats for other email clients someone may wish to "import" their Juno address book to, etc..

If not, well it worked for what I needed.

I want to thank everyone SO much for putting up with a "re-born" green-horn! ;)

---

