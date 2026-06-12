---
title: "Magic Numbers"
date: 2009-08-13
forum: Programming Talk
---

### Post by pepperphd on 2009-08-13
Hi.  I'm teaching myself C++. It is my first language (second if you count the C basics I at first focused on).  Since I'm teaching myself, I don't have a professor to yell at me when I'm doing things wrong.  Magic numbers are one subject I'm sometimes confused about.  I've heard (or read) people say that I should never have an integer constant appear in code, outside of a const definition, unless its 0. And even 0 when it's called for.  Then I write a function like this.

```

        void render_hearts()
        {
            unsigned int i;

            for(i = 0; i < player.get_current_health(); i++)
                apply_surface((15 * i) + 450, 25, hearts_i, screen, &clip_hearts[0]);
            
            for(; i < player.get_max_health(); i++)
                apply_surface((15 * i) + 450, 25, hearts_i, screen, &clip_hearts[1]);
        }

```Now this is just one example but it happens all the time.  With the rest of my code in hand it should be pretty obvious that this renders the players current health on the screen, starting at 450 and increasing by 15 (the width of each "heart") per each unit of health remaining. The problem is that it is so obvious what this does I have trouble justifying a waste of 3 lines to define three constants with long names that are only used here and for very obvious reasons.  In the opinions of the experienced programmers here, is it justifiable to leave those out, or should I, as I sometimes hear, always always always define integer constants?

Here is another example:
```
 
class Key : public Env_var
{
        void action();

        void show() { if(status == ACTIVE) apply_surface(hit_box.x, hit_box.y, sprite, screen, NULL); }

    public:

        Key(int x = 0, int y = 0, int w = 16, int h = 30) : Env_var(x, y, w, h) { sprite = little_key_i; }

};

```In this class declaration, I define the width and height of the keys hit box.  It seems somewhat ridiculous to me to define 16 and 30 elsewhere when it is so unbelievably obvious what they do.  Would some say that I should anyway?

---

### Post by myrtle1908 on 2009-08-13
There really is no rule that says you "should never have an integer constant appear in code".  Like many rules, application is emotive ie. entirely up to you.  However, there are benefits to declaring "magic" numbers, strings etc. as variables or constants.  Maintenance for one.  What may appear obvious to you may not for the reader/maintainer.

In you first example it would be beneficial to declare 15, 450 and 25 as constants, if for no other reason than if you decide to change these numbers you only need do so in one place.  Giving these constants meaningful names is also beneficial as if done right they become self documenting.

A good rule of thumb is if you use a constant value more than once, then you probably should make it a true constant by declaring it as such.

In your second example it is less important as you only use the numbers once and it is quite obvious what they are (as you pointed out).

---

### Post by jtrulen on 2009-08-13
One other thing to consider when using magic numbers is for future readability as well as for others who may need to modify your code at a later date. By using constants with meaningful names, others can easily see what it is that you are trying to accomplish even if it is painfully obvious you you.

I have fallen into that pitfall many times before where my code was not documented enough and I was using magic numbers. The person who took over the project I was working on was constantly asking me what I was doing at a particular point in the code.

Just a couple things to think about, but as myrtle1908 has said, it is your own decision if you want to use magic numbers or not. From personal experience, and that isn't much mind you, I would recommend getting in the habit of not using magic numbers.

---

### Post by matcatc on 2009-08-13
I would replace the numbers 15, 450, and 25 in your first example with macros/constants.

  As for choosing between the two, macros are typically grouped together at the top of some header file, which makes them easy to find, but hard to differentiate (if you have a lot of them). I don't use constants that much, but if the above example was the only place in the code where those magic numbers were being used, then it might be worthwhile to declare them as constants in the function or class (depending on how you're designing the program overall).

---

### Post by Can+~ on 2009-08-13
> Now this is just one example but it happens all the time. With the rest of my code in hand it should be pretty obvious that this renders the players current health on the screen, starting at 450 and increasing by 15 (the width of each "heart") per each unit of health remaining

So let's say, for a second, that you keep the hard-coded constants of the "hearts", and you're working on a real game that will hit the shelves.

Say that, a day later, the designer who drew the life bar hearts says: "After checking the game on high resolutions, the hearts seem rather small, we should make them bigger, and probably move them a little to the left, where they don't interfere with the view".

What could've easily be a swap-the-image and a constant thing, now involves opening the code and seeking that particular line where the size is hard coded.

This is a small example of what it could grow intro major trouble. The only reason this one is small-scaled, is that it pretty much involves graphics. If it were, say, a business application that calculates multiple values depending on a constant, and you make a wrong assumption and leave it as a magic number, oh it could hit you very hard.

Another advantage of Constants, is that you can, eventually, move them to a file outside, something like a configuration file. You could simply change the rules of a game or program by changing values on a .txt file.

---

