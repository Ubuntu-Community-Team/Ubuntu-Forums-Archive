---
title: "Beginners programming challenge #27"
date: 2012-07-08
forum: Programming Talk
---

### Post by cgroza on 2012-07-08
_[SIZE=4][COLOR=Red]Welcome to the 27th Beginners programming challenge.[/COLOR][/SIZE]_
[LEFT]Because I have a bit of free time, I decided to post this programming challenge early.
This means it will be a bit more complicated and will probably take more work to achieve.

_**Task**_
You will have to implement a small regular expression engine that imitates a small subset of the Perl style regular expressions. It will only have to do matching, no need for replace or other complicated features.
You will then use it in a program that will take input and print the text that was first matched by the regular expression. Hopefully, this will introduce you to regular expressions and understand how such an engine works.
These are the operators you will have to implement: *** . $ ^ ?** **+** and of course **normal letters**.

_**Cookie points**_

Cookie points will be awarded for the following extras:

[LIST=1]
[*]Implementing the **| **(or) operator.
[*]Implementing character classes (annotated with **[]**).
[*]Take input from stdin if a file is not supplied so piping is possible on the command line.
[*]Printing every match and not only the first one.
[/LIST]
[/LEFT]
_***Disqualified Entries:***_

Any overly obfuscated code will be immediately disqualified without     account for programmers skill. Please remember that these challenges are     for beginners and therefore the code should be easily readable and    well  commented.

Any non-beginner entries will not be judged. Please use common sense     when posting code examples. Please do not give beginners a copy paste     solution before they have had a chance to try this for themselves.


_***Assistance:***_

If you require any help with this challenge please do not hesitate to     come and chat to the development focus group. We have a channel on     irc.freenode.net #ubuntu-beginners-dev
Or you can pm me

Have fun,
Happy coding

cgroza

---

### Post by Tony Flury on 2012-07-09
Great Challenge - I am not a beginner but I might have a go at this, and see how i get on. Any submission from me will be in Python though - and i promise not to use the re module.

---

### Post by cgroza on 2012-07-09
> **Tony Flury said:**
> Great Challenge - I am not a beginner but I might have a go at this, and see how i get on. Any submission from me will be in Python though - and i promise not to use the re module.
If you think you are not a beginner and you think it would be unfair for other users, you could post your solution after the winner is announced. And yes, the users are not allowed to use libraries that are directly related with regular expression engines, the goal is to implement it themselves :D.

---

### Post by Tony Flury on 2012-07-09
No intention of posting my solution until the winner is announced - although right now I am stuck - so unless i can solve that - i wont be able to post anything.

---

### Post by Lux Perpetua on 2012-07-09
In my opinion, the level of this problem is more intermediate than beginner. I'd love to be pleasantly surprised by a bunch of beginners rising to the challenge, though.

---

### Post by CptPicard on 2012-07-09
Yeah, this really is more intermediate, although some undergrad CS education on grammars, formal languages and automata should provide one with references to literature where this is handled. Any *ad hoc* solutions are almost certainly wrong.

---

### Post by Odexios on 2012-07-10
Just to make sure I got the meaning of "it will print the text that was first matched by the regular expression".

1) If the regex is ".*", should it always match anything and print nothing?

2) If the regex is ".*at", and the string in input is "Matt is at the gym", it should match "Mat", right?

---

### Post by Tony Flury on 2012-07-10
> **Odexios said:**
> Just to make sure I got the meaning of "it will print the text that was first matched by the regular expression".

1) If the regex is ".*", should it always match anything and print nothing?

This should print the whole input string, as the whole string matches the regex.

> **Odexios said:**
> 
2) If the regex is ".*at", and the string in input is "Matt is at the gym", it should match "Mat", right?
I would have assumed that all quantifiers are greedy so in you example the matching string would be : "Matt is at" (as that is longer that "Mat"

---

### Post by Odexios on 2012-07-10
> **Tony Flury said:**
> This should print the whole input string, as the whole string matches the regex.


I would have assumed that all quantifiers are greedy so in you example the matching string would be : "Matt is at" (as that is longer that "Mat"Ok; so I guess that printing "the text that was first matched" means that when more than one line is found, the engine should work only on the first line with a match.

---

### Post by Barrucadu on 2012-07-10
> **Odexios said:**
> Ok; so I guess that printing "the text that was first matched" means that when more than one line is found, the engine should work only on the first line with a match.

"." does not match newlines, so running .* on "hello\nworld" will have two matches: ["hello", "world"], and so "hello" should be printed.

---

### Post by Odexios on 2012-07-10
> **Barrucadu said:**
> "." does not match newlines, so running .* on "hello\nworld" will have two matches: ["hello", "world"], and so "hello" should be printed.By the same reasoning, running "a*b" on "cbab" should return two matches: "b" and "ab", and so print "b". Is it right, or should I treat the newline as a special case?

Sorry for the questions, but though I've used regexps I never really studied them.

---

### Post by Barrucadu on 2012-07-10
It's not a special case, and that's right, "b" is the first match there.

---

### Post by Odexios on 2012-07-10
Ok, thanks.

I'm going to work on it when I'm done with my exams, it seems a nice one. Though I guess that in C it won't be pretty.

---

### Post by cgroza on 2012-07-10
> **Odexios said:**
> Just to make sure I got the meaning of "it will print the text that was first matched by the regular expression".

1) If the regex is ".*", should it always match anything and print nothing?

2) If the regex is ".*at", and the string in input is "Matt is at the gym", it should match "Mat", right?
The other users gave you the right answers :D. I am sorry if this challenge is too difficult, but since I posted it early, no need to rush. I won't judge this for the next 2 weeks.

---

### Post by Barrucadu on 2012-07-10
> **cgroza said:**
> Yes, you are correct.

Not "Matt is at"?

---

### Post by cgroza on 2012-07-10
> **Odexios said:**
> Ok, thanks.

I'm going to work on it when I'm done with my exams, it seems a nice one. Though I guess that in C it won't be pretty.
You could explore other languages that allow functions to be a first class citizen. I would imagine that a feature like that would greatly simplify your task.

---

### Post by cgroza on 2012-07-10
> **Barrucadu said:**
> Not "Matt is at"?
I edited my post, check again. :D

---

### Post by debd on 2012-08-22
What happened to this thread?

There are some problems with this challenge.
It asks only to match the first found match which arises some confusions.

for e.g.
if searched on 'sin' for 'n?',  it should match at 's' or, even 'l?' should match,  because it represents that 'n' or 'l' may or not be present. 
Is that expected?

---

### Post by trent.josephsen on 2012-08-22
Yes, a regex engine should allow /n?/ to match any string, even the empty string.

Assuming ? is greedy, that pattern will match 'n' in "nine" and '' in "line". (If it were non-greedy, it would never match anything but ''.)

---

### Post by debd on 2012-08-25
This is my entry in C.
It doesn't do much.
Inputs can only be taken from the terminal.
'.' '?' '+' and '^' '$' are implemented.
escaping isnt supported.

Only thing good I can tell about it is - its functional as a regex matching engine. Although not all asked are implemented, it does work, but has some bugs.

You can take a look at the code [here]("https://www.dropbox.com/s/ivmb5h6irm4hl8z/fool_regx.c") for easier reading.

```
/*
  fool_regx.c
  challenge #27 entry :: debd
  am literally laughing at me ...
  hope actual regex engines are never implemented like this.
  lots of ifs, 37 to be precise.
  $, ^, ?, ., and + are implemented. There are some bugs.
  escaping the metas aren't supported.
  ^ and $ if present anywhere except in the beggining and in the end respectively are treated as literals.
  Input is taken from commandline.
  Input terminates with a '\n'
  Output is in the form of the entire string given where matches are highlighted in red.
*/

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
  int str[500], i=0, k=0, w=0, wstart=0, q=0, p=0, chance=-1, wrd[200];
  int c, dummy=0, literals=0, bseek=0, metafound=0, char_dol=0;
  int match_from=0, match_start=0, match_done=0, s_before_plus=0;
  int last_whitesp=0;

  /* Variable descriptions::

  str[] :: holds the string to search in
  wrd[] :: stores the regex
  i :: count of input characters for string + 2
  k :: count of input characters for regex + 2
  p :: loop variable for looping through the string
  q :: loop variable for looping through the regex
  wstart :: stores position of last space found.
  chance :: if there is a match on progress
  literals :: count of everything except ^ and $ in the regex
  bseek :: last spcae position in case first char of the regex is a '.'
  metafound :: if any of '.' '+' '?' is found in regex
  char_dol :: if ^ or $ is present in regex in the first / last position
  match_from :: where to start searching for a match when ^ or $ is present
  match-start :: marks the start of a match for highlighting purpose
  match_done :: if a match has been found
  s_before_plus :: character prior to a '+'
  last_whitesp :: last white space in the input string
  dummy :: a dummy

  wstart and bseek were used in the 
  word version of the program i.e. the words where the matches were found were printed.
  Not necesssary now.
  
  */
  
  printf("Search in: ");
  do
  {
    c = getchar();
    if(c == ' ') last_whitesp = i;
    str[i++] = c;
  } while(c != '\n' && i < 500);

  printf("Regex: ");
  do
  {
    w = getchar();
    wrd[k++] = w;
    if(w == '.' || w == '?' || w == '+') metafound = 1;
  } while(w != '\n' && k < 200);

  literals = k-2; /* exclude the last newline and -1 more because k is increased after the last k++*/
  
  if(wrd[0] == '^')
    {
      q=1;
      literals = k-3; /* apparantly */
      char_dol = 1;
    }

  if(wrd[k-2] == '$')
    {
      literals = k-3;
      if(metafound) match_from = last_whitesp+1;  /* Entire word could match, not only the last chars */
      else match_from = (i-2) - (literals);       /* try for the last 'literal' number of chars of the string */
      if(metafound && wrd[k-3] == '.') match_from = (i-2) - (literals);  /* if last char of regex is '.' no need to try entire word */
      char_dol = 1;
      /*literals = k-3;*/
    }

  /*if(match_from > 0)  this portion is no more needed
  { 
    bseek = match_from;
    while(str[bseek] != str[0])
    {
      if(str[bseek] == ' ')
        {
          wstart = bseek+1;
          break;
        }
      bseek--;
    }
  }*/

  for(p=match_from; p<i-1; p++) /* start loop to find match */
  {
    /*printf("p:q=%i:%i", p,q);*/

    if(wrd[q] != str[p] && wrd[q] != '.' && wrd[q] != '?' && wrd[q] != '+') /* handles unmatch, index control for '?' */
      {
        if(wrd[q+1] == '?')
        {
          if(!q) match_start = p; /* mark start of match if next one is a '?' and regex is at begining */
          if(literals > q)
            q++, p--;             /* increase q but dont let p increase so we can check next in string with next in regex */
          continue;
        }
        q=0;
        chance = -1;
        if(literals > 0) p=match_start; /* after a match fails midway set p to previous start of match */
        match_start++;                  /* so it could be tried from on the next char in string */
        continue;
      }

    if(wrd[q] == str[p] || wrd[q] == '.' || wrd[q] == '?' || wrd[q] == '+')   /* this block holds most of the match logic and index control */
      {
        if(!q) match_start = p;
        if(wrd[q] == '?') p--;  /* we are at a ?. We dont care about chars preceding ? and the ? itself */
                                /* to check next in regex with present char at p, dont let p increase */
                                /* p--, p++ keeps it at same position */

        if(wrd[q] == '.' && wrd[q+1] == '+')  /* piece of cake */
          p=i-2, match_done=1;                /* p is also used to mark the end of match */

        if(wrd[q] == str[p] && wrd[q+1] == '+')   /* if next is a '+' remember what preceeds it */
          s_before_plus = wrd[q];

        if(wrd[q] == '+')
        {
          if(p == i-2) match_done = 1;      /* if p is already at the end, match is found */
          if (str[p] == s_before_plus) q--; /* if there are same chars as s_before_plus in the string increase p as */
           else p--;                        /* long as an unmatch is found. so keep q at same pos. otherwise decrease */
                                            /* p so we can check next in string with next in regex */
          
        }
        if(q == literals) match_done = 1;   /* if q is already == literals say match done. true only if regex contains no meta. */
        if(wrd[q] != '+' && char_dol)
        {
          if(char_dol && q == literals+1) match_done = 1;   /*  we took literals one less when a ^ / $ is present. */
        }
        else
        {
          if(char_dol) {      /* when + is present we stop when a unmatch is found after '+' */
            if(s_before_plus != str[p]) match_done = 1; }
        }
        
        if(q <= literals)
        { q++;
          chance = 1;
        }
      }

    if(str[p] == ' ')
    {
      if(chance == -1)
        wstart = p+1;  /* was used previously */
    }

    if(wrd[0] == '^' && p == literals+1)
      break;


    if(match_done)
    {
      printf("Match found : ");
      
      /*while(wstart <= p)  this portion is the code to output ib word mode.
      {
        if(wstart >= match_start)
          printf("\E[31m%c\E[0m\017", str[wstart++]);
        else
        printf("%c", str[wstart++]);
        if(wstart > p)
          {
            dummy = wstart;
            while(str[dummy] != ' ' && str[dummy] != '\n')
              printf("%c", str[dummy++]);
          }
      }*/
      wstart=0;   /* we nomore use wstart as a holder for last space position */
      while(wstart < i-1)
      {
        if(wstart >= match_start && wstart <= p)    /* color from match start up to latest p */
          printf("\E[31m%c\E[0m\017", str[wstart++]);
        else
          printf("%c", str[wstart++]);              /* else vanilla */
      }
      puts("");
      exit(0);
    }
  }

  printf("Match not found.\n");
  exit(1);
}
```Here are some example outputs:
[IMG]http://i.imgur.com/tFfZj.jpg[/IMG]

---

### Post by trent.josephsen on 2012-08-25
> **debd said:**
> ```

void main(void)
```

main() returns int.

---

### Post by debd on 2012-08-25
> **trent.josephsen said:**
> main() returns int.

yikes! corrected.

---

### Post by debd on 2012-08-26
what happened to these threads??
people dont code now!?

---

### Post by trent.josephsen on 2012-08-26
I can't speak for anyone else, but I wrote a mockup main() and did some basic program design and decided I don't have time to make the entire thing. Perhaps this "beginner's" challenge was a little overambitious.

---

### Post by debd on 2012-08-26
> **trent.josephsen said:**
> I can't speak for anyone else, but I wrote a mockup main() and did some basic program design and decided I don't have time to make the entire thing. Perhaps this "beginner's" challenge was a little overambitious.

That's alright..
We could could move on to the next..
Is there one going to be?

---

### Post by MG&amp;TL on 2012-08-27
> **trent.josephsen said:**
> I can't speak for anyone else, but I wrote a mockup main() and did some basic program design and decided I don't have time to make the entire thing. Perhaps this "beginner's" challenge was a little overambitious.

Yeah, I made one in python (which works-ish), but I had no idea how I was going to implement $ and ^.

If anyone's interested, this paper helped: [http://swtch.com/~rsc/regexp/regexp1.html]("http://swtch.com/%7Ersc/regexp/regexp1.html")

Next one please!

---

### Post by debd on 2012-08-27
@MG&TL
Actually implementing ^ and $ was easier IMO.
You only have to try to match the first/last 'n' chars (for ^ and $ respectively ) of the string with the regex in case no meta is present.
Else trying only the first/last word suffices.

---

### Post by MG&amp;TL on 2012-08-27
> **debd said:**
> @MG&TL
Actually implementing ^ and $ was easier IMO.
You only have to try to match the first/last 'n' chars (for ^ and $ respectively ) of the string with the regex in case no meta is present.
Else trying only the first/last word suffices.

That's true. I guess it's the way I implemented it. I'll post my (rubbish) solution this evening, I have a feeling it's bug-ridden though. :)

---

