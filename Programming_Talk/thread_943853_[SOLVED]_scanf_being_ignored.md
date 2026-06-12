---
title: "[SOLVED] scanf being ignored"
date: 2008-10-10
forum: Programming Talk
---

### Post by Absorbed on 2008-10-10
I'm making a little program that plays a game. During the game I use scanf to take integers, and that works fine. However, when I use scanf to take a char, to ask the user if they want to play again, the call just gets ignored. Here's the relevant code:

```
int main(void) {

  int wanttoplay = 1;
  int numWins = 0;

  while(wanttoplay) {
    numWins = game(numWins);
    char choice;
    printf("You've won %d times.\n", numWins);
    printf("Do you want to play another game? (y/n)\n");
    scanf("%c", &choice);
    if(choice != 'y')
      wanttoplay = 0;
  }
  printf("\n");
  return 0;
}

```

Here's what happens when I finish playing a game:
```
You lost!
You've won 0 times.
Do you want to play another game? (y/n)

absorbed@absorbedscomputer:~$ 
```

It doesn't pause to let me type y or n. Help!

---

### Post by dribeas on 2008-10-10
> **Absorbed said:**
> 
Here's what happens when I finish playing a game:
```
You lost!
You've won 0 times.
Do you want to play another game? (y/n)

absorbed@absorbedscomputer:~$ 
```

It doesn't pause to let me type y or n. Help!

Test the value read by scanf. You will probably find '\n' or some other space (if you inputted your last digit followed by a space). I have not programmed C for a long time, but the first thing that comes to mind is ignoring spaces:

```

char choice = ' ';
while ( isspace(choice) )
	scanf( "%c", &choice );
if ( choice == 'y' )
	wanttoplay = 0;

```

---

### Post by snova on 2008-10-10
That's what I thought, too- spaces.

I've nothing to add to this yet except perhaps replacing the example isspace() loop with a do...while() loop.

---

### Post by Absorbed on 2008-10-10
> **dribeas said:**
> Test the value read by scanf. You will probably find '\n' or some other space (if you inputted your last digit followed by a space). I have not programmed C for a long time, but the first thing that comes to mind is ignoring spaces:

```

char choice = ' ';
while ( isspace(choice) )
	scanf( "%c", &choice );
if ( choice == 'y' )
	wanttoplay = 0;

```

Thanks, that solves it. I also found this, if anyone is interested: [http://groups.google.com/group/comp.lang.c/browse_frm/thread/eb422b3c4ca00ee7](http://groups.google.com/group/comp.lang.c/browse_frm/thread/eb422b3c4ca00ee7) It seems the problem was the "\n" to enter the integers was kept in stdin. Presumably when scanf is searching for an integer it ignores them, but accepts them as input for a char.

---

### Post by mike_g on 2008-10-10
For single character input I prefer using getchar. IE:
```
do{
    input = toupper(getchar());
}while(input != "Y" && input != "N"); 

if(input == "N") 
    wanttoplay = 0;
```

---

