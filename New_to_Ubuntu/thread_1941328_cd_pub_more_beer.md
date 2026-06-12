---
title: "cd pub more beer"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by avnd on 2012-03-15
Hello!

Can anyone enlighten me on what the following lines mean?

$ cd /pub
$ more beer

Thanks.

---

### Post by nothingspecial on 2012-03-15
Well the first one will take you to the directory /pub and the second bit will open the file beer with the program more....

... but it is just a joke.

---

### Post by grahammechanical on 2012-03-15
I think that it is a joke. What was the context? I guess that someone was leaving a forum or chat session and was making a joke that he was going to a public house for a drink.

CD = Change Directory or folder. Move the command line cursor from its present directory to the one given. In this case it is the pub directory. Which is an abbreviation for Public House.

more beer = a command to be run or executed. In this case it is to provide more beer.

Similar to

$cd fridge
$ eat pizza

Regards.

---

### Post by avnd on 2012-03-15
@nothingspecial & grahammechanical: Thanks for your replies, guys. 

It WAS in a humorous context, only that I did not know enough Linux to get the humor. :)

---

### Post by Mark Phelps on 2012-03-15
To add a little more info ...

Back in the days of CLI-only, the cat command was used to list out the contents of files.  Because that scrolls lines very quickly and doesn't stop until it lists the entire file, the "more" command was used to halt the listing process so that it paused when the screen filled.  

Typically, the syntax was "cat <filename" | more "  which meant, run the cat command on a file and pipe the output through more so that the listing stopped when the screen was full.

So, unless you actually had a file named "beer" with contents that could be listed, if you tried this, you would probably just get an error message indicating "beer not found".

---

### Post by jerome1232 on 2012-03-15
> **Mark Phelps said:**
>  "beer not found".

oh noes

```
make beer
```

---

### Post by redmk2 on 2012-03-15
> **Mark Phelps said:**
> To add a little more info ...

Back in the days of CLI-only, the cat command was used to list out the contents of files.  Because that scrolls lines very quickly and doesn't stop until it lists the entire file, the "more" command was used to halt the listing process so that it paused when the screen filled.  

Typically, the syntax was "cat <filename" | more "  which meant, run the cat command on a file and pipe the output through more so that the listing stopped when the screen was full.

So, unless you actually had a file named "beer" with contents that could be listed, if you tried this, you would probably just get an error message indicating "beer not found".

To add even more info...

The original command was ***less *** but it was very basic, so it was improved upon with the command ***more ***.  Then there was a final improvement called ***most ***.  So even the tool names have humor (less, more, most).

---

### Post by blackmonday on 2012-12-06
Hey, I know this is an old-ish thread but thought I should try here first rather than start another one.

How would you code something like this in C+? 
I am making a couple of t-shirts for a mate's birthday.

:D

---

### Post by zombifier25 on 2012-12-06
> **blackmonday said:**
> Hey, I know this is an old-ish thread but thought I should try here first rather than start another one.

How would you code something like this in C+? 
I am making a couple of t-shirts for a mate's birthday.

:D

I'm going to presume you posted in the wrong thread.

---

### Post by CaptainMark on 2012-12-06
No I'm going to assume he wants to know the C programming equivalent to the above statement, or at least something humorous relating to beer written in C syntax to go on a tshirt, something like```
#include <stdio.h>

main() {

    int beers;
    while ( standing ) {   
        beers++;
        if ( too_drunk ) {
            exit 2;
        }
    }
}

```My C is extremely rusty so you might want to wait for someone to clean up this code and correct probable errors

---

### Post by zombifier25 on 2012-12-06
> **CaptainMark said:**
> No I'm going to assume he wants to know the C programming equivalent to the above statement, or at least something humorous relating to beer written in C syntax to go on a tshirt, something like```
#include <stdio.h>

main() {

    int beers;
    while ( standing ) {   
        beers++;
        if ( too_drunk ) {
            exit 2;
        }
    }
}

```My C is extremely rusty so you might want to wait for someone to clean up this code and correct probable errors

Oh :P

I did notice some errors there. main() should have a type:
```
int main() {
```
Also, the "exit" function is a function found in stdlib.h, and unless I'm missing something (I do C++), "exit" is not a statement in C. Do this:
```
exit (2)
```
There are many ways that your code can be improved, but enough said, it's only a joke. :P


There's my version, which only contains a C++ class, since writing the main code would kill the joke:
[php]
class Male : public Human
{
    public:
        Man();
        std::string name;
        int age;
    private:
        std::vector<std::string> girlfriends;
        int booze;
        void more_booze();
        bool under_influence_of_booze;
        bool knocked_out_by_booze;
        bool about_to_burf_because_of_booze;
        bool unable_to_get_to_work_tomorrow_because_of_booze;
        bool have_sworn_to_never_drink_booze_ever_again;
};
[/php]

---

### Post by CaptainMark on 2012-12-06
> **zombifier25 said:**
> "exit" is not a statement in C
Well you learn something every day, I never really got into C enough, I dabbled in a different language every week for about 3 months trying to find my favourite, I fell in love with bash scripting and been addicted since :D

---

