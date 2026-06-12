---
title: "no idea"
date: 2013-12-23
forum: Programming Talk
---

### Post by wingnut2626 on 2013-12-23
```
#include <stdio.h>
#include <string.h>


int main(int argc, char *argv[])
{


  int argument, letter_position, number_of_characters;
  char current_character;


  for(argument = 1; argument <= argc; argument++){
    number_of_characters = strlen(argv[argument]);
    printf("%d number of characters debug", number_of_characters);
    getchar();
    for(letter_position = 0; argv[argument][letter_position] != '\0'; letter_position++){
      printf("starting loop, position %d", letter_position + 1);
      getchar();
      current_character = argv[argument][letter_position];
      if(current_character == 'A' || 'a'){
	printf("%d letter of %d argument is A\n", letter_position + 1, argument);
      }
      else if(current_character == 'E' || 'e'){
	printf("%d letter of %d argument is E\n", letter_position + 1, argument);
      }
      else if(current_character == 'I' || 'i'){
	printf("%d letter of %d argument is I\n", letter_position + 1, argument);
      }
      else if(current_character == 'O' || 'o'){
	printf("%d letter of %d argument is O\n", letter_position + 1, argument);
      }
      else if(current_character =='U' || 'u'){
	printf("%d letter of %d argument is U\n", letter_position + 1, argument);
      }
    }
  }
       


  return 0;
}



```

Basically im trying to filter through each letter of each argument and spit out the vowels.  I even included debug statements, cannot for the life of me understand why this is the output:

```
./test13 this is a string
4 number of characters debug
starting loop, position 1
1 letter of 1 argument is A
starting loop, position 2
2 letter of 1 argument is A
starting loop, position 3
3 letter of 1 argument is A
starting loop, position 4
4 letter of 1 argument is A
2 number of characters debug
starting loop, position 1
1 letter of 2 argument is A
starting loop, position 2
2 letter of 2 argument is A
1 number of characters debug
starting loop, position 1
1 letter of 3 argument is A
6 number of characters debug
starting loop, position 1
1 letter of 4 argument is A
starting loop, position 2
2 letter of 4 argument is A
starting loop, position 3
3 letter of 4 argument is A
starting loop, position 4
4 letter of 4 argument is A
starting loop, position 5
5 letter of 4 argument is A
starting loop, position 6
6 letter of 4 argument is A
zsh: segmentation fault  ./test13 this is a string



```

what is going on?

---

### Post by steeldriver on 2013-12-23
```
current_character == 'A' || 'a'
```

... does not mean what you think it means (HINT: is the value of 'a' true or false?)

---

### Post by wingnut2626 on 2013-12-23
Here i added more debugging:

```
#include <stdio.h>
#include <string.h>


int main(int argc, char *argv[])
{


  int argument, letter_position, number_of_characters;
  char current_character;


  for(argument = 1; argument <= argc; argument++){
    number_of_characters = strlen(argv[argument]);
    printf("%d number of characters debug", number_of_characters);
    getchar();
    for(letter_position = 0; argv[argument][letter_position] != '\0'; letter_position++){
      printf("starting loop, position %d", letter_position + 1);
      getchar();
      current_character = argv[argument][letter_position];
**      printf("%c", current_character);**
**      getchar();**
      if(current_character == 'A' || 'a'){
	printf("%d letter of %d argument is A\n", letter_position + 1, argument);
      }
      else if(current_character == 'E' || 'e'){
	printf("%d letter of %d argument is E\n", letter_position + 1, argument);
      }
      else if(current_character == 'I' || 'i'){
	printf("%d letter of %d argument is I\n", letter_position + 1, argument);
      }
      else if(current_character == 'O' || 'o'){
	printf("%d letter of %d argument is O\n", letter_position + 1, argument);
      }
      else if(current_character =='U' || 'u'){
	printf("%d letter of %d argument is U\n", letter_position + 1, argument);
      }
    }
  }
       


  return 0;
}

```

here is the output:

```
./test13 this is a string
4 number of characters debug
starting loop, position 1
t
1 letter of 1 argument is A
starting loop, position 2
h
2 letter of 1 argument is A
starting loop, position 3
i
3 letter of 1 argument is A
starting loop, position 4
s
4 letter of 1 argument is A
2 number of characters debug
starting loop, position 1
i
1 letter of 2 argument is A
starting loop, position 2
s
2 letter of 2 argument is A
1 number of characters debug
starting loop, position 1
a
1 letter of 3 argument is A
6 number of characters debug
starting loop, position 1
s
1 letter of 4 argument is A
starting loop, position 2
t
2 letter of 4 argument is A
starting loop, position 3
r
3 letter of 4 argument is A
starting loop, position 4
i
4 letter of 4 argument is A
starting loop, position 5
n
5 letter of 4 argument is A
starting loop, position 6
g
6 letter of 4 argument is A
zsh: segmentation fault  ./test13 this is a string

```
everything is going as expected, except each current_char is interpreted as an A or a....

---

### Post by wingnut2626 on 2013-12-23
oh i think i know what you are getting at....

---

### Post by wingnut2626 on 2013-12-23
Thought i did but i didnt.  I tried putting the characters in double quotes.  wont compile...
how come this works?

```
include <stdio.h>


int main(int argc, char *argv[])
{
  if(argc !=  2){
    printf("ERROR : You need one argument.\n");
    return 1;
  }


  int i = 0;
  for(i = 0; argv[1][i] != '\0'; i++){
    char letter = argv[1][i];
    
    switch(letter){
    case 'a':
    case 'A':
      printf("%d: 'A'\n", i);
      break;  


    case 'e':
    case 'E':
      printf("%d: 'E'\n", i);
      break;


    case 'i':
    case 'I':
      printf("%d: 'I'\n", i);
      break;


    case 'o':
    case 'O':
      printf("%d: 'O'\n", i);
      break;


    case 'u':
    case 'U':
      printf("%d: 'U'\n", i);
      break;


    case 'y':
    case 'Y':
      if(i > 2){
	printf("%d: 'Y'\n", i);
      }
      break;
      
    default:
      printf("%d: %c is not a vowel\n", i , letter);
    }
  }
  return 0;
}



```

That one does the job but the other one does not.....

---

### Post by wingnut2626 on 2013-12-23
I GOT IT.  needed to do some research.  looks like i needed

if(current_character == 'A' || current_character == 'a')

going to try this then either mark it as solved or whine some more

---

### Post by wingnut2626 on 2013-12-23
ok i got it to do what i wanted, however there is still a segmentation fault at the end....any hints?

---

### Post by steeldriver on 2013-12-23
at a guess, because argv is indexed from 0 (the name by which the program was invoked) to argc**-1** - so your outermost loop likely needs to run from 1 to argument**<**argc (rather than argument**<[COLOR=#ff0000]=[/COLOR]**argc)

---

### Post by wingnut2626 on 2013-12-23
let me digest that...

---

### Post by wingnut2626 on 2013-12-23
solved.  I am going to try to understand what you said steeldriver

---

### Post by steeldriver on 2013-12-23
well if you start counting your fingers starting from 0 what number to you end with? how many fingers do you have?

---

