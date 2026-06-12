---
title: "ruby blocks"
date: 2008-08-20
forum: Programming Talk
---

### Post by rye_ on 2008-08-20
Hi,

On occasion when I do a little ruby and I notice blocks statements like the following;  (Tk springs to mind, maybe ruby-gnuplot also)

```

object.method {parameter "value"}

```

Can anyone help me understand what is going on internally here. e.g.

```

def parameter (value)
  @parameter = value
end

Class OBJECT    
  def initialize
    @parameter = nil
      if block_given?
        yield 
      end
  end
end


```

I believe this works as expected but I would be amazed that any real ruby code would call a method not contained within a class.

Thanks,

Ryan

---

### Post by jespdj on 2008-08-20
The block is a [closure](http://en.wikipedia.org/wiki/Closure_%28computer_science%29). It's just a block of code that is passed to the method, and the method can execute the block by calling **yield**.

It's a very powerful and useful way of programming that is not unique to Ruby; many other languages have something similar.

For more info, see [Containers, Blocks, and Iterators](http://www.rubycentral.com/book/tut_containers.html).

---

### Post by mike_g on 2008-08-20
Wow I always wondered how they limited the class scopes in OOP.

---

### Post by rye_ on 2008-08-20
thanks for the replies, but I was wondering how exactly this particular form of block is working on the inside.

The only way I can get it work is if 'param' is a function defined outside of a class or module.  I'm sure this isn't being done internally.

{param "value"}

---

### Post by mssever on 2008-08-20
> **rye_ said:**
> I believe this works as expected but I would be amazed that any real ruby code would call a method not contained within a class.
It isn't doing that. If you define a method outside a class definition, the method becomes part of the class Object. And since Ruby assumes self when no receiver is implicitly named, and since Object is the base class for all objects, you can call that method pretending it's not part of a class. Calling [FONT=Courier New]parameter(value)[/FONT] is equivalent to calling [FONT=Courier New]self.parameter(value)[/FONT].

If I understand your question properly, I think that you're missing the special scope rules that apply to Ruby blocks. Blocks and procs inherit the scope where they're DEFINED, not where they're CALLED. So when you yield to a block, the scope has nothing to do with the method in which you're calling [FONT=Courier New]yield[/FONT]. Anything currently in scope at the beginning of the block's definition is in scope in the block, and any changes to those objects are visible outside the block. Anything created within the block goes out of scope when the block terminates.

---

### Post by jespdj on 2008-08-20
You can put any code in the block, method calls, or whatever you like. There's nothing special with "parameter" and "value". You can ofcourse also call methods that are not defined in global scope.

Silly example:
[php]class Hello
	def sayhello
		puts "Hello!"
	end

	def something
		puts "Output: "
		yield
	end
end

h = Hello.new
h.something { h.sayhello() }[/php]

---

### Post by rye_ on 2008-10-17
hi,

Thanks for all the replies.  Apologies for the lack of clarity in my question also.

gnuplot's ruby binding seems to work such that when blocks are passed to the first function declared, self in no longer 'main',  this puzzled me.
I've just found the perfect example of how this works, [ruby shoes]("http://help.shoooes.net/Rules.html").

Apparently, the method instance_eval can be used to change 'self' as recognised by the block, presumably how ruby-gnuplot works.

Thanks again,

Ryan

---

### Post by mssever on 2008-10-17
I've never played with shoes, but it looks interesting.

I think this highlights one of the differences between the Ruby style and the Python style. Shoes, Rails, etc. in a way change the Ruby language itself to suit their purposes. I guess that shows some Lisp heritage. And Ruby is very easy to modify--even the core.

---

