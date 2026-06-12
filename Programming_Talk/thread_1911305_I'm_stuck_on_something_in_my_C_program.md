---
title: "I'm stuck on something in my C program"
date: 2012-01-18
forum: Programming Talk
---

### Post by ClientAlive on 2012-01-18
I thought everything should work correctly the way I have it. There's information in the comments regarding the current status. It's starts just under the program description in the comments. The first thing I think of is that something about my function definition (lines 114 - 128) makes it always false - idk. In my comments on the test I did (in the comments at the top) I mentioned that I tried entering the first selection and got the same response. It was, in fact, a lower case d I had entered. Line 47 shows a lower case d is the first item in the first element of the array. One of the things that comes to my mind is that I'm not entirely comfortable with my understanding of passing an array into a function like this and I'm not too sure about my syntax in that area.

Any help would be appreciated.

Thanks

---

### Post by Bachstelze on 2012-01-18
getchar() returns an int. Never convert it to char before making sure the value will actually fit in a char (isascii()...).

```
int ValidSelection (int Selection, const char *SelectionCtrl)  {

   int i;

      for (i = 0; i < 6; i++) {

         if (Selection ==  SelectionCtrl[i]) {
            return 1;
         } //end if

         else  {
            return 0;
         } //end else
      } //end for
} //end function

```

should be

```
int ValidSelection (int Selection, const char *SelectionCtrl)  {

   int i;

      for (i = 0; i < 6; i++) {

         if (Selection ==  SelectionCtrl[i]) {
            return 1;
         } //end if
      } //end for
      return 0;
} //end function
```

There would be A LOT to say about your coding style. I assume you are using Emacs?

---

### Post by Arndt on 2012-01-19
> **Bachstelze said:**
> 
There would be A LOT to say about your coding style. I assume you are using Emacs?

From the way it looks, I would assume he is using something else. I judge from the indentation alone, which seems random to me, and Emacs makes it very easy to indent systematically.

---

### Post by ClientAlive on 2012-01-25
Sorry for going mia for a while. I got that thing to work (with a little help) and that getchar returns int was one of the things. I usually use geany (real simple to use). I've messed around w/ code::blocks a bit from time to time. I keep hearing that about my indenting and I keep trying to improve it but I really don't get what people are saying is off. I thought it was pretty consistent (even if it's consistently wrong).

Anyhow, thanks for the help. I attached the finished program in case anyone wanted to take a peek. Not that it's really very interesting; but, of course, anyone is welcome to use it/ play with it if they wanted.
-----------------

Edit: I feel kinda bad. I got really busy (I was freaking out is the truth) trying to get that thing working before the deadline. When I finally did it was just under the wire (one hr. before the deadline).

---

### Post by Bachstelze on 2012-01-25
Just in the bit of code I posted, you have:

* You seem to be using 3 spaces as indentation, this is very unusual. Generally it's 2 (emacs), 4 (K&R) or 8 (Linus). Make your pick.
* You have 2 spaces before the opening brace on line 1, after == and after else when you should have 1
* The for block is indented 2 levels when it should be 1
* Overcommenting, the //end comments are useless here, the blocks are small
* Blank lines for no real reason

---

### Post by GeneralZod on 2012-01-25
In addition to Bachstelze's comments, I'd personally add:

- Ctr1, Ctr2 & Ctr3 are cryptic, non-descriptive names: give them sufficiently descriptive names that you can remove the comment where they are declared.

- I personally don't like the names Player1 and Player2: maybe Player1Move/ Player1Choice/ Player1Selection ... ?

- What happens if Player2 chooses "q"? (Hint: compile with -Wall [you should always do this] and look at the warning for PlayResult).

- The code would be cleaner if you would normalise the case of the player's selection when it is read e.g. immediately convert it to uppercase.  Then code like

```

Selection ==  'r' || Selection == 'R' 

``` 

could be cut down to just

```

Selection == 'R' 

``` 

As an additional bonus, the test for ties in PlayResult would reduce to just checking if Player1 and Player2 made the same selection, which cuts out quite a few lines of code.

- The "Please select one of the following:" and preceding line is duplicated: not the end of the world, but might be nicer to tuck it into a function somewhere.

- It might be nicer to immediately break out of the loop when Player 1 chooses "Q", rather than having the "if (Player1 != 'q' && Player1 != 'Q')" test, although this would render the "while ((Player1 != 'q' && Player1 != 'Q')" bit redundant.

- Result might be better as an enum with descriptive names (that is, PlayResult should return a Result enum, and DisplayResult should take a Result enum as its argument)

- The substantial block:

```

if ((Player1 = getchar()) == EOF) exit(EXIT_FAILURE); {

				int c;

				while ((c = getchar()) != '\n' && c != EOF) ; if (c == EOF) exit(EXIT_FAILURE);

			}

```

is repeated with minor variations: would be better to tuck most of this away into a function.

- Now that I come to think about it: it might be nicer to use an enum for Player1/2 selection (enum Selection { Rock, Paper, Scissors, Quit }) instead of treating it as a char all over the place, which is really an "accidental" implementation detail.  For such a small example (which is unlikely to change further), it's probably not worth it, though - but imagine if you wanted to make a localised version for different languages!

- Real nitpicky: DisplayResult displays the result *and* has an important side-effect that one would not expect from reading the name of the function (it also tallies the scores!).  It's probably fine to leave it as is, though, as the "cure" (adding a separate "TallyResult" function) would complicate things further.  Makes me a little queasy, though ;)

Mostly nitpicks, really :)

Edit:

There's always a big dollop of subjectively in code design, but I've attached a version showing how I would re-write it.  It's not been well tested, though!

---

### Post by ClientAlive on 2012-01-25
> **Bachstelze said:**
> Just in the bit of code I posted, you have:

* You seem to be using 3 spaces as indentation, this is very unusual. Generally it's 2 (emacs), 4 (K&R) or 8 (Linus). Make your pick.
* You have 2 spaces before the opening brace on line 1, after == and after else when you should have 1
* The for block is indented 2 levels when it should be 1
* Overcommenting, the //end comments are useless here, the blocks are small
* Blank lines for no real reason


Thanks for the expanation. I didn't know that. I had heard you choose either 2 or 3 spaces (or was that either 3 or 4?) but I hadn't heard there was a connection between the style you choose and the number of spaces. I'll go back through that code to put my finger on all the places you mentioned. I think that will help me identify what I'm doing wrong here and fix it in the future.

> **GeneralZod said:**
> In addition to Bachstelze's comments, I'd personally add:

- Ctr1, Ctr2 & Ctr3 are cryptic, non-descriptive names: give them sufficiently descriptive names that you can remove the comment where they are declared.

- I personally don't like the names Player1 and Player2: maybe Player1Move/ Player1Choice/ Player1Selection ... ?

- What happens if Player2 chooses "q"? (Hint: compile with -Wall [you should always do this] and look at the warning for PlayResult).

- The code would be cleaner if you would normalise the case of the player's selection when it is read e.g. immediately convert it to uppercase.  Then code like

```

Selection ==  'r' || Selection == 'R' 

``` 

could be cut down to just

```

Selection == 'R' 

``` 

As an additional bonus, the test for ties in PlayResult would reduce to just checking if Player1 and Player2 made the same selection, which cuts out quite a few lines of code.

- The "Please select one of the following:" and preceding line is duplicated: not the end of the world, but might be nicer to tuck it into a function somewhere.

- It might be nicer to immediately break out of the loop when Player 1 chooses "Q", rather than having the "if (Player1 != 'q' && Player1 != 'Q')" test, although this would render the "while ((Player1 != 'q' && Player1 != 'Q')" bit redundant.

- Result might be better as an enum with descriptive names (that is, PlayResult should return a Result enum, and DisplayResult should take a Result enum as its argument)

- The substantial block:

```

if ((Player1 = getchar()) == EOF) exit(EXIT_FAILURE); {

				int c;

				while ((c = getchar()) != '\n' && c != EOF) ; if (c == EOF) exit(EXIT_FAILURE);

			}

```

is repeated with minor variations: would be better to tuck most of this away into a function.

- Now that I come to think about it: it might be nicer to use an enum for Player1/2 selection (enum Selection { Rock, Paper, Scissors, Quit }) instead of treating it as a char all over the place, which is really an "accidental" implementation detail.  For such a small example (which is unlikely to change further), it's probably not worth it, though - but imagine if you wanted to make a localised version for different languages!

- Real nitpicky: DisplayResult displays the result *and* has an important side-effect that one would not expect from reading the name of the function (it also tallies the scores!).  It's probably fine to leave it as is, though, as the "cure" (adding a separate "TallyResult" function) would complicate things further.  Makes me a little queasy, though ;)

Mostly nitpicks, really :)

Edit:

There's always a big dollop of subjectively in code design, but I've attached a version showing how I would re-write it.  It's not been well tested, though!


Thanks for the feedback. Much appreciated. You really made me laugh when you said, "Makes me a little **queasy**..." by the way.  :p

There's two things I saw that I'm unfamiliar with. I'll put them on my list to look up/ learn about. They were:

"normalize" and "enum" (just never come across it yet).

I'm also not certain the implications of using enum as it may relate to [not] "...using char all over the place." Unfortunately I was constrianed by the assignment spec to use getchar and char menu selections. Probably doesn't make much sense for me to talk about it before learning what enum is. That requrement was just something that came to mind when I read that in your post.

Thanks again for the help. It's really great to have a chance to talk with you guys that have more experience at this.

Have a great day guys.

Jake

---

### Post by Vaphell on 2012-01-25
normalization is a process that transforms/organizes wider array of data into some narrower defined range considered standard.
When you support rRpPsSqQ you have 8 distinct chars to test but rR is the same choice so you can normalize user input to 'capital letters only' and test only against standard RPSQ, cutting the number of tests in half.
Another example would be angles: in geometry 450deg is pretty much the same as 90deg and 1080deg is pretty much the same as 360deg, so more often than not you can normalize tho whole range of possibilities from -infinity to +infinity into the 0-360 range thus making the data handling much easier.

enum is a structure that defines valid values that the variable can have. These values are named so you can use them instead of their true values (enum internally is indexed with integers usually starting from 0)
In your case you can go from characters to enum values that describe selected option immediately after the user input. Only the function responsible for input handling needs to know the meaning of physical characters used, but the rest of program operates on more descriptive enum values {Rock,Paper,Scissors} returned by said input handling function. Such an approach is cleaner and more elegant because the core of your program is not tainted by physical user input and deals only with abstract concepts that represent the logic of the game.

---

### Post by ClientAlive on 2012-01-26
> **Vaphell said:**
> normalization is a process that transforms/organizes wider array of data into some narrower defined range considered standard.
When you support rRpPsSqQ you have 8 distinct chars to test but rR is the same choice so you can normalize user input to 'capital letters only' and test only against standard RPSQ, cutting the number of tests in half.
Another example would be angles: in geometry 450deg is pretty much the same as 90deg and 1080deg is pretty much the same as 360deg, so more often than not you can normalize tho whole range of possibilities from -infinity to +infinity into the 0-360 range thus making the data handling much easier.

array is a structure that defines valid values that the variable can have. These values are named so you can use them instead of their true values (enum internally is indexed with integers usually starting from 0)
In your case you can go from characters to enum values that describe selected option immediately after the user input. Only the function responsible for input handling needs to know the meaning of physical characters used, but the rest of program operates on more descriptive enum values {Rock,Paper,Scissors} returned by said input handling function. Such an approach is cleaner and more elegant because the core of your program is not tainted by physical user input and deals only with abstract concepts that represent the logic of the game.


Well that's cool. Thanks for explaining that.

---

