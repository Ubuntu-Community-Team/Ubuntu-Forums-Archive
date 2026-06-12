---
title: "help understanding C code"
date: 2012-09-29
forum: Programming Talk
---

### Post by snowlizard31 on 2012-09-29
I'm learning C from K&R's book. I've come across some code I don't completely understand and I would like to before moving on.
```

#define IN 1   /* inside a word  */
#define OUT 0 /* outside a word */

/* count lines, words, and characters in input */

main()
{
    int c, nl, nw, nc, state;
    
    state = OUT;
    nl = nw = nc = 0;
    while((c = getchar()) != EOF) {
        ++nc;
        if (c == '\n')
            ++nl;
        if ( c == ' ' || c == '\n' || c == '\t')
            state = OUT;
        else if (state == OUT) {
            state = IN;
            ++nw;
        }
    }
    printf("%d %d %d\n",nl, nw, nc);
}

```what I don't get is the second if statement and else if below are two example of the code being run the first code excludes state = IN in the else if statement. my question whats the importance of state = IN if everytime it loops back state gets back the value of OUT which is zero. How does state = IN affect the code.
```

$ ./cpl
hello
    
    
3 5 10

``````

$ ./cpl
hello
    
    
3 1 10

```

---

### Post by satsujinka on 2012-09-29
The second if would be better done using isspace(c), in other words, it just tests to see if c is white space.

The "else if" is used to figure out if we're entering a word. If we were just in whitespace (i.e. we were OUTside of a word) and the current character is alphanumeric (!isspace, this is what the else insures) then we're starting a new word (meaning we're INside a word, also increment nw.)

---

### Post by snowlizard31 on 2012-09-29
But if the second if statement test's for white space then how come on the second output (the one with state = IN not commented out) nw is only equal to 1 in the output when I entered two spaces. So the else if statement counts all spaces and returns them??

---

### Post by satsujinka on 2012-09-29
That's the correct behavior. The else if doesn't count spaces, it counts non-space characters that are either the first character or that follow a space character. So:
"  hello"
"hello"
"   hello   "

All have a word count of 1 (nw == 1,) because only the 'h' causes nw++ to occur.

---

### Post by Ryan Dwyer on 2012-09-29
nl is num lines. nw is num words. nc is num characters.

The first time it hits a whitespace, the state becomes OUT (ie. outside a word). If it hits another whitespace immediately, it matches the ( c == ' ' || c == '\n' || c == '\t' ) condition and does nothing because state is already OUT.

The else if statement knows that we've entered a non-whitespace character (it would have matched the previous condition otherwise) and that the previous character was a whitespace (state == OUT), so what it's counting is the number of words.

---

### Post by ofnuts on 2012-09-30
> **snowlizard31 said:**
> I'm learning C from K&R's book. I've come across some code I don't completely understand and I would like to before moving on.
```

#define IN 1   /* inside a word  */
#define OUT 0 /* outside a word */

/* count lines, words, and characters in input */

main()
{
    int c, nl, nw, nc, state;
    
    state = OUT;
    nl = nw = nc = 0;
    while((c = getchar()) != EOF) {
        ++nc;
        if (c == '\n')
            ++nl;
        if ( c == ' ' || c == '\n' || c == '\t')
            state = OUT;
        else if (state == OUT) {
            state = IN;
            ++nw;
        }
    }
    printf("%d %d %d\n",nl, nw, nc);
}

```what I don't get is the second if statement and else if below are two example of the code being run the first code excludes state = IN in the else if statement. my question whats the importance of state = IN if everytime it loops back state gets back the value of OUT which is zero. How does state = IN affect the code.
```

$ ./cpl
hello
    
    
3 5 10

``````

$ ./cpl
hello
    
    
3 1 10

```

Actually this code implements a very simple Finite State Machine with two states: IN (in a word) and OUT (not in a word). 

In OUT state, "space-like" characters cause a transition back to OUT (and the transition on '\n' counts the lines). Non-space characters cause a transition to IN state (and are counted to count the words). Both types of transitions are counted (count of characters...).

In IN state, non-space characters cause a transition to IN, and space characters cause a transition to OUT (and \n transitions are counted for lines).  Both types of transitions are counted (count of characters...).

Now, some optimizations are done:

- since all transitions are done on characters the count of characters can be "extracted" and done at the beginning
- similarly the count of linefeeds is done in all transitions (on Windows, counting "CRLF"  would be more difficult) and can be extracted and done at the beginning
- space-like characters transitions lead to OUT state whatever the current state
- only non-space characters transitions are really dependent on current state.

---

### Post by snowlizard31 on 2012-09-30
OH! so the reason my out was 3, 1 , 10 is because it counted 3 newlines , 1 word and 10 characters? How it get 10 characters though was it because when the loop iterated it counted hello 2 times?

---

### Post by Tony Flury on 2012-09-30
> **snowlizard31 said:**
> OH! so the reason my out was 3, 1 , 10 is because it counted 3 newlines , 1 word and 10 characters? How it get 10 characters though was it because when the loop iterated it counted hello 2 times?

No - it counted 10 because you have 6 characters on your first line "hello" + "/n", and then presumably your 2nd and third lines both have a space and then the "/"n - and that makes ten.

that explains the 3,1,10 answer - i am not sure how you got 3,5,10 answer with the input you gave - as there is only one word.

---

### Post by JKyleOKC on 2012-09-30
> **Tony Flury said:**
> i am not sure how you got 3,5,10 answer with the input you gave - as there is only one word.When he commented out the IN setting in the else clause, that made the program count each letter in "hello" as a separate word because it never changed to IN state.

---

### Post by snowlizard31 on 2012-10-01
Oh thanks that make sense it really help me out and I got 3 5 10 because I commented out state = IN in the else if statement. Thanks Guys!!:D

---

