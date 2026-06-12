---
title: "Simple program help"
date: 2010-12-16
forum: Programming Talk
---

### Post by RedSingularity on 2010-12-16
I have an assignment to write some programs.  I did most of them but there are a few that are stumping me.  Any help would be great as I am not a programming major.  Thanks!

1)  Write a program that will allow a user to input as many numbers as the user wants (use "q" as the choice that ends the user input).  The program will then respond:

Highest Number: Answer
Lowest Number: Answer
Sum of the numbers: Answer
Average of the numbers: Answer


2)  Write a program that will allow a user to type in a number, then the number will either count up to the number provided by the user or count down from that number.  In addition, create a menu that will let the user choose which counter they wish to use.  In both cases that counter will either count down to 0, or start counting from 0.

---

### Post by matt_symes on 2010-12-16
Hi

Is this school homework?

Kind regards

---

### Post by RedSingularity on 2010-12-16
> **matt_symes said:**
> Hi

Is this school homework?

Kind regards


Yes sir.

---

### Post by trent.josephsen on 2010-12-16
Well, the first one is easy:
```
#include <stdio.h>

int main(void)
{
        for(;;) {
                char c;
                printf("Enter a number: ");
                fflush(stdout);
                if ( (c = getchar()) == 'q' ) {
                        break;
                }
                while (c != '\n') {
                        c = getchar();
                }
        }
        printf("Highest Number: Answer\n"
                        "Lowest Number: Answer\n"
                        "Sum of the numbers: Answer\n"
                        "Average of the numbers: Answer\n");
        return 0;
}
```

Seriously, though, if you want any help, you need to show your code, that you wrote, with a specific question about why it behaves the way it does.  This isn't a free homework service.

---

### Post by r-senior on 2010-12-16
This covers #1 I think. Apart from the niceties like prompts ...

```
(>./,<./,+/,+/%#)
```

```
(>./,<./,+/,+/%#) 2 3 4 5
5 2 14 3.5
```

(It would be useful to know the language, because it's probably not this one).

---

### Post by matt_symes on 2010-12-16
Hi  

Sorry mate. It's against forum rules to help with homework. Maybe Trent did not realise this. 

From [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.Might i suggest you ask a teacher.

EDIT: I just don't want you getting into trouble.

Kind regards

---

### Post by RedSingularity on 2010-12-16
Wow i cant believe i forgot........this is in BASH.

---

### Post by RedSingularity on 2010-12-16
> **matt_symes said:**
> Hi  

Sorry mate. It's against forum rules to help with homework. Maybe Trent did not realise this. 

From [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)



Might i suggest you ask a teacher.

Kind regards


Oh boy......:(  Sorry.  My mistake everyone.  Disregard post.

---

### Post by trent.josephsen on 2010-12-16
> **matt_symes said:**
> Sorry mate. It's against forum rules to help with homework. Maybe Trent did not realise this.
Did you actually read my submission?  It was given in jest.

But yeah, that was out of line anyway.  Posting a program masquerading as help without making it clear that it was a joke was... actually quite thoughtless, in retrospect.  I won't make the same mistake again.

---

