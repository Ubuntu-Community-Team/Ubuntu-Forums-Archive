---
title: "[C] How much of a character is '\b'? An experiment"
date: 2010-04-05
forum: Programming Talk
---

### Post by nvteighen on 2010-04-05
Hi there!

As we all know, all input and output is character-based. This may seem obvious and natural, but it has some counter-intuitive consequences like the fact that the "newline" concept is also abstracted as a character ('\n') and that even the "backspacing" and "carriage return" concepts also are ('\b' and '\r', respectively). Examples of their counter-intuitiveness are the many times we see people in these forums wondering why getchar() is also reading the '\n'...

So, as '\b' (backspace) is also a character, I asked myself at what extent the act of deleting a character is itself represented as a character. In other words, is backspace really the '\b' character all the time? If it was, then there'd be the possibility to overflow an input buffer by hitting backspace repeatedly.

With that idea in mind, I wrote the following test unit in C. I did it in C because it's the lowest-level language I know and because this is essentially a low-level issue.

```

#include <stdio.h>
#include <string.h>

int main(void)
{
    const char *string_1 = "hello?";
    const char *string_2 = "hello!\b?";

    printf("%d\n", strcmp(string_1, string_2));
    printf("\"hello?\": %s\n", string_1);
    printf("'hello!\\b?': %s\n", string_2); /* The \b is 'shown'. */

    return 0;
}

```

If you run the program, you'll pretty much see that '\b' is a character like any other one present in the string such as the strcmp() call will effectively return that string_1 and string_2 are different. They're printed in the "same" way just because of '\b' "illusion". But you could say that the absence of '!' in string_2's output is the mark for the presence of '\b'.

So, the next step was to test input. Here's the test unit:
```

#include <stdio.h>
#include <string.h>

int main(void)
{
    const char *test1 = "hello?\n";
    const char *test2 = "hello!\b?\n";

    char input[10];
    memset(input, '\0', sizeof(input));

    printf("Input \"hello!\\b?\\n\": ");
    fgets(input, sizeof(input), stdin);

    printf("input: %s\n", input);

    printf("test 1 (= \"hello?\\n\"): %d\n", strcmp(test1, input));
    printf("test 2 (= \"hello!\\b?\\n\"): %d\n", strcmp(test2, input));

    return 0;
}

```

The idea is to compare the user's input with two different tests, in order to observe how a 'hello!\b?\n' input is compared to a 'hello!\b?\n' string variable. The result is strikingly odd... the input is equal to 'hello?\n'. The '\b' "illusion" happening in output doesn't exist during input: The character previous to the backspace is actually deleted, not just hidden from screen, and therefore, never saved into the input variable in the program. 

This makes it clear there's no chance to overflow a text buffer with '\b', but means a quite big inconsistency with, say, '\n', which is recorded from input when present. This means that having backspace abstracted as '\b' proves to be unsecure/useless/inappropriate and instead of having another approach, someone just implemented a "half-baked" solution... which is good, but that leads to this weird result of having two expectedly equal strings to be unequal.

Thoughts?

---

### Post by wmcbrine on 2010-04-05
You're not low-level enough. You're doing line-oriented input, with only the finished, edited lines being returned to the program. But the '\b' is handled as a character on the level below that, the level of the TTY. If it were just a little dumber, it would record the backspace and send it on to your test program, instead of recognizing it and modifying the buffer accordingly.

---

### Post by nvteighen on 2010-04-05
> **wmcbrine said:**
> You're not low-level enough. You're doing line-oriented input, with only the finished, edited lines being returned to the program. But the '\b' is handled as a character on the level below that, the level of the TTY. If it were just a little dumber, it would record the backspace and send it on to your test program, instead of recognizing it and modifying the buffer accordingly.

I see. Thanks for the information.

The issue I see, however, is that there's a kind of assymetry between the character's output and input behaivor which is a bit odd seen from the particular level of abstraction C provides.

---

### Post by LKjell on 2010-04-05
If you want to test then print out to stderr and pipe the output to a file and to hd directly

---

### Post by wmcbrine on 2010-04-05
...and pull it back in the same way (from a file, not a TTY). You'll certainly see a '\b' then.

Sorry, I don't agree at all with your perception of asymmetry here.

---

### Post by nvteighen on 2010-04-06
Ok, I see what you mean and yes, there it appears '\b'. Here's the test suit... Maybe this should have been one single program, but I just modified the snippets from above.. Ok, at least having them separated shows it clearly that no cheating is done :P

1. Outputs a '\b' to a file called "b_test". The '\b' is shown as the control character ASCII 0x08.
```

#include <stdio.h>
#include <string.h>

int main(void)
{
    const char *string_2 = "hello!\b?";

    FILE *file = fopen("b_test", "w");
    if(file == NULL)
    {
        printf("Error while creating file!");
        return 1;
    }

    fprintf(file, "%s", string_2);

    fclose(file);

    return 0;
}

```

2. Takes the "b_test" file generated by the program above as input and then outputs to stderr to prove nothing occurs either when '\b' is used as input from file.
```

#include <stdio.h>
#include <string.h>

int main(void)
{
    FILE *file = fopen("b_test", "r");
    if(file == NULL)
    {
        printf("Error while opening file!");
        return 1;
    }

    char input[10];
    memset(input, '\0', sizeof(input));

    fgets(input, sizeof(input), file);

    fclose(file);

    fprintf(stderr, "%s", input);

    return 0;
}

```

So, the conclusion, as wmcbrine pointed out, is that TTY plays a major rule in interpreting '\b'.

---

### Post by Compyx on 2010-04-06
What you're looking at is 'cooked' mode versus 'raw' mode: [http://en.wikipedia.org/wiki/Cooked_mode]("http://en.wikipedia.org/wiki/Cooked_mode"). I remember an excellent post a few years back in the newgroup comp.lang.c about cooked, rare and raw mode. But unfortunately I can't find it right now.

You can control and examine all terminal device characteristics through <termios.h>, `man termios.h' should give you some idea of what kind of translations can occur with terminal I/O. It ain't pretty ;)

---

### Post by nvteighen on 2010-04-06
> **Compyx said:**
> What you're looking at is 'cooked' mode versus 'raw' mode: [http://en.wikipedia.org/wiki/Cooked_mode]("http://en.wikipedia.org/wiki/Cooked_mode"). I remember an excellent post a few years back in the newgroup comp.lang.c about cooked, rare and raw mode. But unfortunately I can't find it right now.

You can control and examine all terminal device characteristics through <termios.h>, `man termios.h' should give you some idea of what kind of translations can occur with terminal I/O. It ain't pretty ;)

Hm... lots of ncurses raw/cooked mode experiments in the past and now I haven't thought on looking at termios??? Thanks for refreshing my mind :P

And I can see how unpretty it is... that's why ncurses was created... Anyway, I'll take a look on it.

---

