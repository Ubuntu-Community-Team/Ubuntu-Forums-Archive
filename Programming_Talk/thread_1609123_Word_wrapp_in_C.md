---
title: "Word wrapp in C"
date: 2010-10-30
forum: Programming Talk
---

### Post by wasanzy on 2010-10-30
Hi Group,

I have been given a project to work on, and that is to write a C  (please not c++) to do word wraping. The user will enther the file through the key bord. Below is my code, but that is happening is, it is wrapping only one like leaving the rest. Please what is wrong in the code and how do I correct it,


#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>

FILE *finput=NULL, *foutput=NULL;

//char print_wrapped (char);

main()
{
         int i;
         int width = 50;
        int stringlengh;
        char filename[width];
        printf ("please enter ur filename:\n");
        fgets( filename,width,stdin);


        filename[strlen(filename) - 1] = '\0'; //remove newline
        for (; i < strlen(filename); i++) {

        printf("%c", filename[i]);
        }

        finput = fopen (filename, "r");
        if ( finput == NULL)
        {
                printf("Error opening input file\n");
                exit(1);
        }else{
                printf ("Input file open successfully\n");
        }
        if ( finput !=NULL )
        {
                char line[4500];
                while ( fgets (line, 4500, finput) !=NULL) //reading line
                {
                        stringlengh = strlen(line);
                        //fputs ( line, stdout ); //write the line

                        // open a new file to write to it
                        foutput = fopen("wrapped.txt", "w");
                        if (foutput ==NULL)
                        {
                                printf("Error opening file\n");
                        }
                        while ( width != 0)
                        {
                                if  ( isspace(line[width] ) )
                                {
                                        line[width] = '\n';
                                        break;
                                }
                                width++;

                        }
                                fprintf(foutput, "\n\t\t\t\t\t%s\n", line, '\n');

                }
                        printf("File written succesful\n");
        }


                fclose(foutput);
                fclose (finput);

}

---

### Post by Tony Flury on 2010-10-30
Your code would be more easily readable if you included them in CODE tags when you post to the forum.

Having said that, I would expect you to reset something after you do a line wrap.What exactly is "width" doing ?

I would also suggest that if your code is meant to be doing word wrap, then I would have expected it to be dealing with the input in terms of words, and not characters - the only algorithm I can think of (in my head) you would have to deal with words.

---

### Post by wasanzy on 2010-10-30
Thank you for your reply. the wdth in there sets the length of string that will be disply per like. And so if a line exceed that widh, the rest of the string will wrap to the next line. This is what I want to do. 
I hope you can help me.

---

### Post by GregBrannon on 2010-10-30
I think it will be easier to think it through in concept instead of jumping right to the code:

Assumptions (I think you've made so far or should make):

Input file contains only characters with one '\n' at the end.
(new?) The input file contains words separated by spaces.
The number of characters in the input file < 4501.
Line length <= 80 characters.
(new) Line breaks are made between words.
The line wrapped output is written to a new file.

Pseudo code:

get input filename from user
open input file for reading
read input file into a single character array
close input file
define output file
open output file for writing
loop:
find each space character, ' ', before multiples of 80
add a newline character, '\n', after the above spaces
end loop.
write modified character array to output file
close output file
end

Your code currently breaks the character array after the first 80 characters and then stops.  You need a loop that continues to add the breaks as outlined above.

Does that help?

---

### Post by Tony Flury on 2010-10-30
Is this a college assignment ? If so then maybe we have already helped too much.

---

### Post by dwhitney67 on 2010-10-30
Here's my $0.02 worth of advice...

Initialize this variable to a valid value *before* you actually attempt to use it:
```

int i;

```

Don't assume that there is a newline in the inputted filename string:
```

filename[strlen(filename) - 1] = '\0'; //remove newline

```

This is not needed (already been checked):
```

if ( finput !=NULL )

```

This should be done during initialization, not after you start processing the input file:
```

// open a new file to write to it
foutput = fopen("wrapped.txt", "w");

```

'width' should be treated as a fixed-constant, and is aptly set to 50.  What in pray tell are you doing mucking with it here, especially considering that it's use is out of "context" (width was defined to be the max-length of the input filename):
```

while ( width != 0)
{
   if ( isspace(line[width] ) )
   {
      line[width] = '\n';
      break;
   }
   width++;
}

```

Finally, declare main() to return an int.  Move the declaration of your FILE* variables inside the main function; there's no need for them to be globally declared.  Remove the include statement for stdlib.h; I don't believe it is required.

---

### Post by trent.josephsen on 2010-10-30
Points for style (and conformance):

- int main(void), not just main().  C99 did away with the implicit 'int'; you have to specify it.  If you're using C89, it's okay (though bad style), but...

- C89 doesn't support VLAs (variable length arrays), or arrays whose sizes are set at run time.  In other words, "int width=50; char filename[width]" is illegal in C89.  Use "filename[50]" instead.

- "fgets(filename, width, stdin)" and "fgets(line, 4500, finput)" could be more readably and robustly written with sizeof:  "fgets(filename, sizeof filename, stdin)"

- Check the result of fgets.

- "stringlength" is spelled with two T's.

- strlen() can take a long time to run.  It might be a good idea to create a variable to store the "actual length" of the string, given that it never changes after you've taken care of a terminating newline (if it exists).

- "please enter ur filename:" is an annoying prompt.

- Is there some reason your output is indented half way across the page?

- You can probably ignore this advice because it's probably a homework assignment with demented requirements, but it's conventional to read from standard input and write to standard output.  That's what they're there for, and why shells have redirection.

---

### Post by wasanzy on 2010-11-01
Have to thank you guys very much. I haven't had time to work on this but I will find some time to work on this and let you know if I have success or not.

---

