---
title: "creating new objects in ruby"
date: 2010-12-20
forum: Programming Talk
---

### Post by cybo on 2010-12-20
i'm somewhat new to rails, ruby on rails and webdevelpment. there is a piece of code that i cannot understand in ruby:

```

rating = Rating.new(:rating => params[:rating])

```

can anyone explain what does this code do? i do understand that i creates a new object but what does > :rating => params[:rating] do? Rating class doesn't have any attributes named :rating.

any help is appreciated

---

### Post by dv3500ea on 2010-12-21
You are calling the new method of the Rating class. This creates a new object of class Rating and calls the initialize method. The ```
:rating => params[:rating]
``` is passed as an argument to the initialize method.

':rating' is a Symbol, which is like a String but immutable and is only stored in memory once. params is a Hash (or, at least, an object that acts like a hash). In ```
params[:rating]
``` you are finding the value of the :rating key.

In ruby, you can use named arguments using the Hash literal notation eg.
```
{
    key => value,
    anotherkey => anothervalue,
   ...
}
``` but when passing as arguments, you can omit the curly brackets.

What you are really doing is:
```

Ratings.new({:rating => params[:rating]})

```

You could create a class that behaves like this using the following code:

```

class Rating
    def initialize opts={}
        @rating = opts[:rating] || 1.0
        @another_option = opts[:another_option] || 'default'
        @yet_another_option = opts[:yet_another_option] || 'another default'
    end
end

```

---

### Post by cybo on 2010-12-21
@dv3500ea

thanks. it really helped.

---

