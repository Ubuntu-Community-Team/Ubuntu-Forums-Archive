---
title: "Slooks Programming Challen"
date: 2012-09-16
forum: Programming Talk
---

### Post by slooksterpsv on 2012-09-16
All,

I've had to make a few programs for work and was thinking, I wonder what others could come up with if I explain the program, what it's supposed to do, and that.

So here's one I'd like to see if you guys can make, please post the source, you can use any toolkits, etc. that you need, but I'm curious to see how you guys do it and if it's closely related to how I'm making the program(s).

Let's start!:

Program 1:

Make a program that goes through a CSV file that looks something similar to this:
```

2xHamsters,3
3xCats,5
9xDogs,2
Dogs,7
Cats,2
...

```

What the program needs to do is check and see if the first alphanumeric character in the first column is a number (e.g. 2 on 2xHamsters); take that number (e.g. 2) and multiply it by the second column for that same row (e.g. 2 * 3 = 6).
It should go through all the lines. Afterwards it should create a new file that looks like so:

```

Hamsters,6
Cats,15
Dogs,18
Dogs,7
Cats,2
...

```

So when the program goes through, it removes the 2x, 3x, 5x, 9x, etc. and multiplies it by the number in the second column. To create said number.

I wrote mine in python but feel free to use what you would like. I may port it to PHP for our web server.

Let's see what you guys come up with.

---

### Post by Some Penguin on 2012-09-16
It'd be simple with Perl, Text::CSV to properly handle quoted characters rather than pointlessly rolling your own CSV parser, and regular expressions.

A silly approach would be to naively split on commas -- which fails on input like

"4x Giant, Hairy, but Wonderfully Delicious Tarantulas", 100
   

```

# STDIN -> STDOUT
use Text::CSV;
use strict;

my $csv = Text::CSV->new( { binary => 1 });
my $lref= undef;
while (defined($lref = $csv->getline(\*STDIN))) {
   my $part1 = $lref->[0];
   my $part2 = $lref->[1];

   if ($part1 =~ /^(\d)x/) {
       $part2 *= $1;
       $part1 = substr $part1, 2;
   }
   $csv->print(\*STDOUT, +[ $part1, $part2 ]);
}

```

---

### Post by Odexios on 2012-09-17
I was kind of bored...

```
prog_name input_file output_file
(input_file and output_file can be the same)
```
[php]#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/*macro constants definitions*/

#define EXTRA_CHECK

#define SK_ERROR 1
#define SK_EOL 2
#define SK_EOF 4

#define SK_END 1
#define SK_START 2

#define SK_CHUNK 50
#define SEPARATOR ','
#define SEPARATOR_STRING ","
#define FACTOR_SEPARATOR 'x'

/*macro functions definitions*/

#define sk_is_num(c) ((c) >= '0' && (c) <= '9')

/*prototypes*/
int sk_get_line(FILE *file, char **string);
int sk_number_of_lines(FILE *file);
int sk_find_separator(char c, char *string, int where_from);
int sk_number_of_digits(int number);

/*main*/

int main(int argc, char *argv[])
{
  int number_of_lines;
  int line;
  char **lines_array = NULL;
  FILE *file;
  int i;
  int pos;
  int dim;
  int retval;
  char *string_name = NULL;
  char *string_number = NULL;
  char *string_factor = NULL;
  int factor;
  int number;

  if (argc != 3)
  {
    printf("Please specify input and output files:\n");
    printf("%s input output\n", argv[0]);
    printf("%d\n", argc);
    return 1;
  }

  file = fopen(argv[1], "r");
  if (file == NULL)
  {
    return 2;
  }

  number_of_lines = sk_number_of_lines(file);
  lines_array = malloc(sizeof(char *) * number_of_lines);
  if (lines_array == NULL)
  {
    return 3;
  }

  retval = SK_EOL;

  for (line = 0; line < number_of_lines && retval != SK_EOF; line++)
  {
    retval = sk_get_line(file, &(lines_array[line]));
    if (retval == SK_ERROR)
    {
      return 4;
    }
  }

  fclose(file);

  file = fopen(argv[2], "w");
  if (file == NULL)
  {
    return 5;
  }

  for (line = 0; line < number_of_lines; line++)
  {
    if (!sk_is_num(lines_array[line][0]))
    {
      continue;
    }

    /*should get here only if the first character is numeric*/
#ifdef EXTRA_CHECK
    pos = sk_find_separator(FACTOR_SEPARATOR, lines_array[line], SK_START);
    if (pos != -1)
    {
      for (i = 0; i < pos && pos != -1; i++)
      {
        if (!sk_is_num(lines_array[line][i]))
        {
          pos = -1;
        }
      }
    }
#else
    for (pos = 0; sk_is_num(lines_array[line][pos]); pos++)
    {
    }
#endif
    if (pos <= 0)
    {
      string_factor = NULL;
      pos = 0;
    }
    else
    {
      dim = pos;
      string_factor = malloc(sizeof(char) * (dim + 1));
      if (string_factor == NULL)
      {
        return 6;
      }
      strncpy(string_factor, lines_array[line], dim);
      string_factor[dim] = '\0';
      if (lines_array[line][pos] == FACTOR_SEPARATOR)
      {
        pos++;
      }
    }

    i = pos;
    pos = sk_find_separator(SEPARATOR, lines_array[line], SK_END);
    if (pos == -1)
    {
      return 7;
    }
    dim = pos - i;
    if (dim <= 0)
    {
      return 8;
    }
    string_name = malloc(sizeof(char) * (dim + 1));
    if (string_name == NULL)
    {
      return 9;
    }
    strncpy(string_name, lines_array[line] + i, dim);
    string_name[dim] = '\0';
    pos++;

    dim = 0;
    for (i = pos; sk_is_num(lines_array[line][i]); i++)
    {
      dim++;
    }
    if (dim <= 0)
    {
      return 10;
    }
    string_number = malloc(sizeof(char) * (dim + 1));
    if (string_number == NULL)
    {
      return 11;
    }
    strncpy(string_number, lines_array[line] + pos, dim);
    string_number[dim] = '\0';

    if (string_factor == NULL)
    {
      factor = 1;
    }
    else
    {
      factor = atoi(string_factor);
      free(string_factor);
      string_factor = NULL;
    }

    number = atoi(string_number);
    free(string_number);
    string_number = NULL;

    number *= factor;

    dim = sk_number_of_digits(number);
    string_number = malloc(sizeof(char) * (dim + 1));
    if (string_number == NULL)
    {
      return 12;
    }
    string_number[dim] = '\0';
    for (i = dim - 1; i >= 0; i--)
    {
      string_number[i] = (number % 10) + '0';
      number /= 10;
    }

    dim = strlen(string_name) + 1 + strlen(string_number);
    free(lines_array[line]);
    lines_array[line] = malloc(sizeof(char) * (dim + 1));
    lines_array[line][0] = '\0';

    strcat(lines_array[line], string_name);
    strcat(lines_array[line], SEPARATOR_STRING);
    strcat(lines_array[line], string_number);

    free(string_name);
    string_name = NULL;
    free(string_number);
    string_name = NULL;
  }

  for (line = 0; line < number_of_lines; line++)
  {
    fprintf(file, "%s\n", lines_array[line]);
    free(lines_array[line]);
  }

  free(lines_array);

  return 0;

}


/*definitions*/

int sk_get_line(FILE *file, char **string)
{
  int c;
  char *temp_string;
  char *retval;
  int dim;
  int i;

  dim = SK_CHUNK;

  temp_string = malloc(sizeof(char) * dim);
  if (temp_string == NULL)
  {
    return SK_ERROR;
  }

  i = 0;

  while (((c = getc(file)) != EOF) && (c != '\n'))
  {
    if (i >= dim - 1)
    {
      retval = realloc(temp_string, sizeof(char) * dim * 2);
      if (retval == NULL)
      {
        free(temp_string);
        return SK_ERROR;
      }
      dim *= 2;
      temp_string = retval;
    }
    temp_string[i] = c;
    i++;
  }
  temp_string[i] = '\0';

  *string = temp_string;

  if (c == EOF)
  {
    return SK_EOF;
  }
  else if (c == '\n')
  {
    return SK_EOL;
  }

  free(temp_string);
  return SK_ERROR;

}

int sk_number_of_lines(FILE *file)
{
  int lines;
  int c;

  rewind(file);

  lines = 0;

  while ((c = getc(file)) != EOF)
  {
    if (c == '\n')
    {
      lines++;
    }
  }

  rewind(file);

  return lines;
}

int sk_find_separator(char c, char *string, int where_from)
{
  int i;
  int dim;

  dim = strlen(string);
  
  if (where_from == SK_START)
  {
    i = 0;
  }
  else
  {
    i = dim;
  }

  while ((where_from == SK_END && i > 0)
         ||
         (where_from == SK_START && i < dim))
  {
    if (string[i] == c)
    {
      break;
    }
    if (where_from == SK_END)
    {
      i--;
    }
    else if (where_from == SK_START)
    {
      i++;
    }
  } 

  if (string[i] != c)
  {
    return -1;
  }

  return i;

}

int sk_number_of_digits(int number)
{
  int i;

  for (i = 0; number != 0; i++)
  {
    number /= 10;
  }
  
  return i;

}

[/php]

Just checked if it compiled and if everything worked with the sample input you gave, nothing more; no guarantee I thought of every pitfall.

If an input line of
```
2Hamster,3
```
must be transformed in
```
Hamster,6
```
undefine EXTRA_CHECK.

I'm pretty sure it could have been more compact, but I'm still trying to get the hang of C.

---

### Post by slooksterpsv on 2012-09-19
I like how you did yours in C++, but it should check for 2x; the reason it can't be 2 or that is cause the program I made some items we have at work start with numbers. e.g. 3.5HF

I still like it though.

The above one, Perl was it? that one's neat too; very few lines.

---

### Post by Odexios on 2012-09-19
> **slooksterpsv said:**
> I like how you did yours in C++, but it should check for 2x; the reason it can't be 2 or that is cause the program I made some items we have at work start with numbers. e.g. 3.5HF

I still like it though.

The above one, Perl was it? that one's neat too; very few lines.It should work fine, then, as long as EXTRA_CHECK is defined.

Thanks. My greatest issue right now is that I'm not really sure the way I code is the usual or recommended way; I'm completely self-taught.

---

### Post by Stovey on 2012-09-19
Hi.  Here's my code in Python3.  I am a beginner (I started learning Python 9 weeks ago), so I would very much appreciate any comments on my code.

I understand the folly with splitting on the comma, so I suppose you could use "rfind" to find the index of the comma in the last column.  I see that a more elegant solution is provided by PERL and maybe regular expressions would help, but I don't know that stuff (yet!!).

```
# animals.py

def main():
    in_file, out_file = setup_files()
    process_file(in_file, out_file)

def setup_files():
    in_filename = input("Please enter input filename: ")
    out_filename = input("Please enter output filename: ")
    in_file = open(in_filename, 'r')
    out_file = open(out_filename, 'w')
    return in_file, out_file

def process_file(in_file, out_file):
    for line in in_file:
        first_chr = ord(line[0])
        if first_chr >= 48 and first_chr <= 57: # is the first character a number?
            num = get_number(line)
            split_line = line.split(",")
            column = eval(split_line[1])
            new_num = num * column
            new_text = split_line[0]
            new_text = new_text[line.find("x") + 1:]
            new_line = new_text + "," + str(new_num)
        else:
            new_line = line.rstrip()
        print(new_line, file=out_file)

def get_number(line):
    num_list = ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "."]
    index = 0
    num_str = ""
    while line[index] in num_list:
        num_str = num_str + line[index]
        index = index + 1
    num = eval(num_str)
    return num

main()
```

---

### Post by Majorix on 2012-09-19
Most languages have a CSV library, should not prove too difficult using that.

PS @slook: Your avatar!!! :D

---

