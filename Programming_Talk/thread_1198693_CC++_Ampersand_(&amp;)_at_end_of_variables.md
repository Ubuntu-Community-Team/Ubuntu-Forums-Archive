---
title: "C/C++: Ampersand (&amp;) at end of variables"
date: 2009-06-27
forum: Programming Talk
---

### Post by JordyD on 2009-06-27
I see this a lot, and it's always confused me, so I figured I'd ask.

Why do people throw ampersands at the end of some of their variables? What does it mean? I've seen code with ampersands at the beginning of variables ("&myChar"), and I understand it, because that was what I was taught. But I was never taught what this meant: "myChar&". Is it the same thing?

Thanks,
Jordy

---

### Post by soltanis on 2009-06-27
I think this is a C++ thing, and has to do with references. The last time I did C++ was years ago, though, and now I've forgotten.

---

### Post by MadCow108 on 2009-06-27
i've never seen ampersands at the end of variables (and my tests of that syntax wont compile). Do you have an example?

do you perhaps mean ampersand behind the type in function headers?
funcion(int& var)

this means you pass var by reference and not by value so you can manipulate the value of var outside the function.
In C you would need to pass the pointer to var (which again is a kind of reference) by value.

---

### Post by JordyD on 2009-06-27
> **MadCow108 said:**
> i've never seen ampersands at the end of variables (and my tests of that syntax wont compile). Do you have an example?

do you perhaps mean ampersand behind the type in function headers?
funcion(int& var)

this means you pass var by reference and not by value so you can manipulate the value of var outside the function.
In C you would need to pass the pointer to var (which again is a kind of reference) by value.

Whoops! I feel foolish now. I had looked at exactly what you're describing, except the type was not a primitive (in fact a class), so I mistook it for a variable.

The example that spawned this post is this:
```
class MyPicture
{
public :

    // This is the copy constructor
    MyPicture(const MyPicture& Copy) : Image(Copy.Image), Sprite(Copy.Sprite)
    {
        // This is the trick : we setup the sprite
        // to use our image, instead of the one of Copy
        Sprite.SetImage(Image);
    }

    // ... a lot of useful functions ...

private :

    sf::Image  Image;
    sf::Sprite Sprite;
};

```

That is from the [SFML Tutorials]("http://www.sfml-dev.org/tutorials/1.4/graphics-sprite.php")

I guess I should mark this as solved.

---

### Post by jflaker on 2009-06-27
I don't use C variants, but program in RPG/RPGLE and CLP for the IBM AS/400....

I usually use an @ or # for similarly named vars so I can remember which is @lpha and which is #Numeric or Numeric#

An & could mean the variable is by reference instead of by value. 

OTHERWISE, I just use a long name so I know what it is...
ArrayVar
ArrayElem

---

