---
title: "naming convention for child's version of a function"
date: 2011-07-15
forum: Programming Talk
---

### Post by jmartrican on 2011-07-15
Hello,

Lets say I have a parent class named UpgradableAbility.  And it has an abstract function named upgradeToNextLevel.  This function has to check if the max level has been reached, if so it returns false.  

Well I figured it would be cool if the parent function would do the max-level check so that the children do not have to do it.  So the parent would have a non-abstract version of the function that would do the check, and if the check passes, would then call the abstract function.  The children then do not have to implement this check

So my question is what should I name the child's version of the function (the abstract one) if the parent one is called "upgradeToNextLevel"?  Is there a naming convention?

I was thinking of naming the abstract version "_upgradeToNextLevel" or "upgradeToNextLevelAbstract".

This is really not a big deal I just want to know if there is a naming convention that covers this.

thanks
jose

---

### Post by ve4cib on 2011-07-15
One possible way of doing this would be as follows:

```

abstract class Parent
{
    public boolean upgradeToNextLevel()
    {
        if (level < MAX_LEVEL)
        {
            level++;
            return true;
        }
        return false;
    }

    ...
}

class Child extends Parent
{
    public boolean upgradeToNextLevel()
    {
        if(super.upgradeToNextLevel())
        {
            // do whatever needs to be done when the level was gained
        }
        else
        {
            // we were already at max level
        }
    }
}
```

You keep the standard behaviour in the superclass, and use polymorphism and inheritance to make use of it in the child classes.

Not sure if that answers the question, but it might give you something to think about as an alternative.

---

### Post by GeneralZod on 2011-07-16
Prefixing with "do" is a common naming convention for this situation:

[http://www.oodesign.com/template-method-pattern.html](http://www.oodesign.com/template-method-pattern.html)

---

### Post by PaulM1985 on 2011-07-16
Since the child functions are virtual functions, I have seen these prefixed with "V" or "Vf" before.

Paul

---

### Post by jmartrican on 2011-07-16
Wow three valid answers.  Thanks guys.  

ve4cib, pretty slick man.  I think I even did this before.... duh.


thanks
jose

---

