---
title: "calling menu problem"
date: 2013-03-07
forum: Programming Talk
---

### Post by tomzie on 2013-03-07
Hi, I have the following code. What is wrong with my declaration. 

I am getting deprecated conversion from string constant to char *

int getchoice(char *greet, char *choices[]);

char *main_menu[] = {
"Choice 1",
"Choice 2",
"Choice 3",
0,
}; // i get the error here...

int main()
{
int choice;
choice = getchoice("Options: ", main_menu);


return 0;
}

int getchoice(char *greet, char *choices[])
{
// function codes here...
}

---

### Post by dwhitney67 on 2013-03-07
Here's some suggestions:
```

...

int getchoice(**const** char *greet, **const** char *choices[]);

**const** char *main_menu[] = {
...
};

int getchoice(**const** char *greet, **const** char *choices[])
{
// function codes here...
}

```

---

### Post by tomzie on 2013-03-07
Thanks.

---

