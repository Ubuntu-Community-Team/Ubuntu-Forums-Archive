---
title: "C help"
date: 2006-09-27
forum: Programming Talk
---

### Post by grimx on 2006-09-27
The problem is get this
----------------
Bounds 0 - 100
Value[0]? Bounds 84 - 100
Value[1]?
-------------------- ](*,) 
when answer == 'y'

What i want is this
----------------
Bounds 0 - 100
Value[0]?
----------------

```

#include <stdio.h>
#include <stdlib.h>

int number_to_guess;
int low_limit;
int high_limit;
int guess_count;
int player_number;
int answer;
char line[80];


int main()
{
	
	while(1)
	{
	  number_to_guess = rand() % 100 + 1;
	  low_limit = 0;
	  high_limit = 100;
	  guess_count = 0;
		
	  while(1)
	  {
			
            printf("Bounds %d - %d\n", low_limit, high_limit);
            printf("Value[%d]? ", guess_count);
		
            fgets(line, sizeof(line), stdin);
	    sscanf(line, "%d", &player_number);
		  
            guess_count++;
			
            if(player_number == number_to_guess)
		break;
		
	    if(player_number < number_to_guess)
	    {
		low_limit = player_number;
	    }
	    else
	    {
	        high_limit = player_number;
	    }
	  }
		
	  printf("Bingo\n");
	  printf("To Quit type 'n' Or 'y' To Continue\n");
	  printf("Play Again?: ");
		
	  answer = getchar();
	  if(answer == 'n')
	  {
             break;
	  } 
          else if(answer == 'y')
	  {
	     continue;
	  }
		
	}
	
	printf("GOODBYE\n");
	return 0;
}


```

---

### Post by neouser99 on 2006-09-28
i don't really understand your question...

-neo

---

### Post by grimx on 2006-09-28
run the code and after you guessed the number
it then ask if you want to continue
type y for yes 
and insted of just showing 

Bounds 0 - 100  <----------:KS I Want This
Value[0]?:   
---------------------------------------  
it shows 
                                         
Bounds 0 -100
Value[0]?: Bounds 84 - 100  <-------](*,) I Don't Want This

I don't want Bounds showing twice after answering y
it should be 

Bounds 0 - 100
Value[0]?:

---

### Post by Houman on 2006-09-28
try this, replace:

```

answer = getchar();

```

with 

```

fgets(line, sizeof(line), stdin);
sscanf(line, "%c", &answer);

```

regards

Houman

---

### Post by grimx on 2006-09-29
Thanx HOUMAN  :-D

---

