---
title: "C++ Tags"
date: 2013-02-17
forum: Programming Talk
---

### Post by lolabunnyA on 2013-02-17
Hello!

C/C++ has various tags, that are used like this: **/** @blabla */** . For example:

/** **@brief** Sums up you and me.
    **@param** you - It is you.
    **@param** me - And that is me.
    **@return** Us.
*/
int
veryGoodFunction ( int you, int me ) {
    return you + me;
} 


The questions are:

1. There are many tags like these: @version, @see, @enum, @struct, @name, @class and so on. **Where can I read about all of them?** Sadly, I could find only small different pieces of information about that. I need a huge manual on this theme; like, what does every tag mean, how and when do you use it, and so on. Can you please advice something?

2. As far as I understand, these tags are used to create a hover tooltips in certain programs. What program can I use on Ubuntu 12.10 to see these hovers? My Kate and Gedit do not show any hover tooltips.

Thank you!

---

### Post by r-senior on 2013-02-17
These aren't C++ tags. They are document comment tags as used in [Javadoc]("http://en.wikipedia.org/wiki/Javadoc") for Java but also becoming something of a standard for other languages through support by Doxygen.

[Doxygen - Documenting the Code]("http://www.stack.nl/~dimitri/doxygen/manual/docblocks.html#specialblock")

The idea is to comment your code with specially formatted comments and run it through a documentation generator to produce HTML pages or other formats. As you say, some of the more sophisticated IDEs, e.g. Eclipse, will show tooltips based on these.

---

### Post by lolabunnyA on 2013-02-17
Ah, I see, so these tags are mainly for programs like Doxygen.. I guess I don't have to add them then, since these tags makes my code significantly larger, while not everyone will be able to see tooltips; there is no point in adding them if only Eclipse users will see them..

---

### Post by r-senior on 2013-02-17
You don't have to add them, but tagged documentation can save a huge amount of time for very little effort. Documenting functions is a good habit and the tags take virtually no extra time to add.

I've got a project that's been on the back burner since November, but I know that when I go back to it, I have a full documentation set waiting for me that will automatically update via Doxygen as I resume coding. I'll be glad I spent an hour setting that up.

---

### Post by trent.josephsen on 2013-02-17
You don't *have* to add them, or any comments at all, but many of those tags are for documenting things that really should be documented, at least in some cases. Doxygen may have its limitations, but you should be in the habit of commenting every function and non-trivial variable anyway, so the tags are just a way of making those comments more structured so that they can be automatically compiled into an API reference of sorts. [Here's](http://docs.oracle.com/javase/6/docs/api/java/util/Scanner.html) an example of documentation generated from javadoc; scroll down to Method Detail and you can see how it formats @param, @throws, etc.

What should be documented is really up to your judgment; just because Doxygen provides a tag doesn't mean you should use it, but they generally are provided for a reason. Like, it's not a bad idea to put the author's name at the top, but you don't have to add an @author tag every time someone new changes one line of the file. You're not writing a book ;)

tl;dr - You don't have to use Doxygen, but don't neglect to document your code.

Edit: Looks like r-senior beat me to it.

---

### Post by lolabunnyA on 2013-02-17
**r-senior** and **trent.josephsen**
Thank you for the explanation!

Then I have the last question: where exactly should I put this, mm, document comment tags? Are there some rules?

1. If I have a library, shoud I put these tags in **.h** file or in **.cpp** file?
2. If I have multiple functions, should I write something like

/** @Tags_for_foo */
void foo1() {..}

/** @Tags_for_bar */
int bar() {..}

**OR**

void foo1() {..}
int bar() {..}

/** @Tags_for_foo */
/** @Tags_for_bar */

---

### Post by r-senior on 2013-02-18
I agree with what trent.josephson says -- use your judgement and make them work for you.

I've not done enough C++ to make a good recommendation but my inclination would be to put them in the .cpp file as the .h/.hpp is mostly forward declarations. For processing with a tool, I don't think you want to duplicate in both files but anything that's just in the header might also benefit from a comment, e.g. enums and classes.

The comments should go with the methods rather than collected together in one place. A simple, if slightly contrived, example:

```
/**
 * Check if a password is a good password. A good password is
 * one that contains at least one upper case character, at least
 * one lower case character and at least one numeric digit. No
 * check is made on the length of the password.
 * 
 * @see http://en.wikipedia.org/wiki/Password_strength
 *
 * @param password the password to check
 * @return true if the password is good, false otherwise
 */
bool good_password(const string& password)
{
    ...
}

```

You might choose not to document private methods, or getters and setters. It's what you want to make of it really -- the key question being "what would I like to know about this method or function in six months time when I come back to it?".

---

