---
title: "How should I lay out doxygen documentation?"
date: 2010-06-12
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2010-06-12
Hi,

I have finally made a requirement for myself to document every new function that I write and it's parameters. I have decided to use Doxygen for that. Since it is my first time doing documentation, I have some questions.

What is the tradition? Should I write the documentation in the function definitions or in the declaration? Should I write it above the fucntion definition/declaration or below?

ps. I am not good with these two terms. function declaration == the one put in a .h file && function definition == the one that is put in a .cpp file and 'expands' the ones in the .h file. Right?

---

### Post by tookyourtime on 2010-06-12
With C++ I document the variables in the .h file like:

```
float x;     ///< X variable
```

And the functions in the .cpp file:
```

/**
*   \brief  What it does
*
*   Other things.
*   Other things.
*
*   @param   float x    The x value
*
*   @return   Something.
**/

float Function(float x)
{

    return Something;
}
```

---

### Post by Compyx on 2010-06-14
> **SledgeHammer_999 said:**
> Hi,

I have finally made a requirement for myself to document every new function that I write and it's parameters. I have decided to use Doxygen for that. Since it is my first time doing documentation, I have some questions.

What is the tradition? Should I write the documentation in the function definitions or in the declaration? Should I write it above the fucntion definition/declaration or below?

Doxygen expects a documentation block to belong to whatever comes after it, so the documentation goes before the function definition. There are exceptions though: preprocessor conditionals. Doxygen tries to do preprocessing by default, but cannot handle conditionals that depend on external defines/compiler settings.
Consider this fragment:
```

#if defined(__STDC_VERSION__) && __STDC_VERSION__
    #define FOO BAR
#else
    #define FOO BAZ
#endif

```
Doxygen cannot preprocess this properly, since the compiler will set __STDC_VERSION__ based on the C standard used: the definition of __STDC_VERSION__ won't appear anywhere in the source. This has the nasty side-effect that Doxygen will require you to write two documentation blocks for FOO. The workaround for this is to provide a separate docblock with the special '@def' command, like so:
```

/**
 * @def   FOO
 * @brief Blabla
 *
 * More blabla
 */

```
This docblock can go anywhere, but I prefer to keep it close to the thing it documents.

You can also 'inline' docblocks, which I find useful in enum's; in stead of this:
```

enum Foo {
   /**
     * blabla
     */
   FOO_OK = 0,

   /**
     * more blabla
     */
   FOO_FAILED = 1
}

```
you can do this:
```

enum Foo {
    FOO_OK = 0,      /**< blabla */
    FOO_FAILED = 1   /**< more blabla */
}

```
This helps in keeping stuff compact and readable, in my opinion.


Another special docblock is the file docblock: the very first docblock Doxygen encounters is expected to contain documentation on the source file, this docblock can contain commands like @author and @file. Doxygen will warn if such a docblock isn't found.

Documentation can also be grouped together with @defgroup/@ingroup commands, this will provide structure in the generated documentation by generating 'modules' of related documentation. In my opinion this helps a lot in keeping documentation of larger projects readable.

> **SledgeHammer_999 said:**
> 
ps. I am not good with these two terms. function declaration == the one put in a .h file && function definition == the one that is put in a .cpp file and 'expands' the ones in the .h file. Right?

You can have multiple declarations of something, but only one definition. A declaration declares the existence of something, while a definition provides the actual code for that something:
```

int the_answer(void);     /* declaration: there is a function the_answer,
                           * its body is defined somewhere else */

int the_answer(void)      /* definition: we provide the body of the function
                           * here */
{
    return 42;
}

```

Since there can be only one definition, it makes sense to use that as the place for the Doxygen docblock. Its also easier to alter the documentation when your code changes, since the docblock will be right above the code you altered.

Hope this helps clarify things a bit.


PS: If you happen to use Vim, you can use Vim's Doxygen syntax highlighting: :set syn=c.doxygen OR :set syn=cpp.doxygen, this makes Doxygen docblocks stand out more and makes it easier to spot errors in your docblocks.

---

### Post by SledgeHammer_999 on 2010-06-14
Thanks. Quite useful insight.

---

