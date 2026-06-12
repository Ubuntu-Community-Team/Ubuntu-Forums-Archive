---
title: "A small problem with if condition"
date: 2015-07-16
forum: Programming Talk
---

### Post by NoWeDoR on 2015-07-16
```
#include <stdio.h>
int main()
{
    int value;
    printf("Enter a number value: ");
    scanf("%d", &value);
    if (value)
    {
        do
        {
            printf("Please enter a number value: ");
            scanf("%d", &value);
        } while (value);
        printf("You entered a number value.\n");
        return 0;
    }
    else
    {
        printf("You entered a number value.\n");
    }
    return 0;
}

```



Hello friends. As you see I want to a number value from user but let's assume the user is entering character value (like * , a d . ; .) perseveringly.
I want to correct this exactly from user and at every turn I warn the user if the value isn't number.
However, although I have tried to use ascii table and dealt with it, as you see again I couldn't tell the program in if(value) and while(value) statements what I mean.

How can this program be writtten?

---

### Post by trent.josephsen on 2015-07-16
scanf returns an int, which is the number of %-conversions in the format string that were successfully matched. You should always check the return value of scanf to determine whether it was successful or not. This will work:

```
int main(void)
{
    printf("Enter a number: ");
    fflush(stdout);
    if (scanf("%d", &value)) {
        printf("You entered %d.\n", value);
        return 0;
    } else {
        puts("That wasn't a number!");
        return 1;
    }
}
```

I added fflush(stdout) because sometimes if you leave it off the prompt will not be printed immediately. This is because of [line buffering]("https://stackoverflow.com/questions/1716296/why-does-printf-not-flush-after-the-call-unless-a-newline-is-in-the-format-strin") on stdout and is a common source of confusion. To be safe, you should always call fflush(stdout) after prompting for input.

If the user types something that isn't a number, [scanf will leave it in the input stream]("http://c-faq.com/stdio/scanfjam.html"). This is a problem if you keep trying to read numbers, because scanf will keep failing in an infinite loop -- similar to the situation in your [other thread](http://ubuntuforums.org/showthread.php?t=2286883). You need to get rid of the non-numeric input before you can try to read a number again; [here's one suggestion](http://c-faq.com/stdio/stdinflush2.html).

---

