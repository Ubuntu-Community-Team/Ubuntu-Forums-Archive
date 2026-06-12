---
title: "ruby, method_missing, and &lt;array&gt;.send"
date: 2010-09-14
forum: Programming Talk
---

### Post by cybo on 2010-09-14
i'm trying to learn ruby and ruby on rails from a book called 'Ruby for Rails' it is a good book (at least for me) but below is a piece of code i don't understand:

```

#!/usr/bin/ruby
class Recipe
  attr_accessor :main_ingredient
end

class Cookbook
  attr_accessor :title, :author

  def initialize
    @recipes = []
  end

  def method_missing(m, *args, &block)
    @recipes.send(m, *args, &block)
  end
end

recipe_for_stew = Recipe.new
recipe_for_stew.main_ingredient = 'beef'
recipe_for_cake = Recipe.new
cb = Cookbook.new
cb << recipe_for_stew
cb << recipe_for_cake
beef_dishes = cb.find_all {|recipe| recipe.main_ingredient == 'beef'}
puts beef_dishes

```

i understand that when i call '<<' and 'find_all' methods, method_missing is called from the cookbook.  i just don't understand what happens after that. 
1) what are m, *args, and &block are set to in each case and why
2) what does <array>.send do with those arguments.

help is greatly appreciated.

---

### Post by dv3500ea on 2010-09-14
1) m is set to the method you called (eg. '<<')
   *args contains a list of the arguments passed to that method
   &block is the block that was passed (if any) (eg. {|recipe| recipe.main_ingredient == 'beef'})

2) The send method of any object calls the method m with argument *args and a block &block on that method. Basically what is being done here is the method called on the Cookbook instance is being called on the @recipes array instead.

---

### Post by dwhitney67 on 2010-09-14
Or to deduce what is actually being passed:
```

...

def method_missing(m, *args, &block)
   puts "method: #{m}"
   puts "args  : #{args}"
   puts "block : #{block}"

   @recipes.send(m, *args, &block)
end

...

```

---

