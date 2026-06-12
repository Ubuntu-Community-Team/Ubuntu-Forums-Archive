---
title: "I'm another Kernighan &amp; Ritchie beginner. Help on 1.09, please."
date: 2010-01-15
forum: Programming Talk
---

### Post by justyellowboy on 2010-01-15
In the attachment of my post, I have a very-heavily documented version of Example 1.09 from the 2nd Edition C book.

I use Code::Blocks and a compressed ANSI "Open Code" style, with a standard XGA resolution, so if you have a smaller screen than a 15", you will probably see some line breaking. My apologies. The Coding style note is made because I sometimes close boxes of code to establish focus on figuring one part of it out. This is the first time a program has been so elaborate and connected together that some of my questions kind of get muddled in my train of thought.

The zip file only contains the C file, but it compiles and executes just fine. I'm only documenting it.

In there, I try to describe for myself how it works line-by-line, but some things have me concerned. The descriptions *and questions* are in there.

=====

In case you just want to crack open the book and answer the questions without downloading, here are my questions:

1) Since the lines containing void copy(et cetera et cetera) are both matching, I can infer that they are related because the first is when it is initialized (please correct me if I am using the wrong term. I want to totally understand), but when comparing the (apparently unnecessary, according to some online resources) custom getline function (in the downloaded application it has been shortened to getl) to its "initialization line," they do not match.

In said "initialization line," with "int getline(char line[], int maxline)" why are these arguments named this way when they don't match the function definition later on in the script? Furthermore, does the line array mentioned in the above sentence have any relation to its usage in the main[] function before and during the getline function call? The fact that another similar definition of this array appears below and is used in main() is throwing me off a little.

2. The for loop can easily cover for the if test with the change of a parameter, right?

---

### Post by denarced on 2010-01-16
yes, if in a c-program, the main-function is the last function in the file, there is no need to insert the function prototypes.
like this:
```

int get_integer()
{
[INDENT]return 3;[/INDENT]
}
int main(int argc,char **argv)
{
[INDENT]int a = get_integer();
return 0;[/INDENT]
}


```

But if main comes first, the prototypes must be inserted.
Like this:
```
int get_integer();

int main(int argc,char **argv)
{

    int a = get_integer(); return 0;

}

int get_integer()
{

    return 3;

}
```

Also, as I understand, the function argument-names don't have to match, only the types(int,long,char etc)

---

### Post by denarced on 2010-01-16
> **justyellowboy said:**
> Furthermore, does the line array mentioned in the above sentence have any relation to its usage in the main[] function before and during the getline function call? The fact that another similar definition of this array appears below and is used in main() is throwing me off a little.

No, they are both local variables. There is no relation. Anything that is declared between braces, exists only between those braces.

---

### Post by justyellowboy on 2010-01-16
Those three answers clarified much up for me. They don't have to match, local automatic variables aren't related, and main() thus should come last unless I want to initialize the function, first. Thanks!

---

