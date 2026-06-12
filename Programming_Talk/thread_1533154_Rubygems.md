---
title: "Rubygems?"
date: 2010-07-17
forum: Programming Talk
---

### Post by kotakotakota on 2010-07-17
Hello,

I am brand new to Ruby (I was sucked in looking at Ruby on Rails and now Gosu...) and am stuck with trying to compile an application with the Gosu Rubygem.  The following is the code I have (straight from the Gosu tutorial):
```
require 'rubygems'
require 'gosu'

class GameWindow < Gosu::Window
  def initialize
    super(640, 480, false)
    self.caption = "Gosu Tutorial Game"
  end

  def update
  end

  def draw
  end
end

window = GameWindow.new
window.show
```
and the output that I get when I try to run it:
```

/home/kota/.gem/ruby/1.8/gems/gosu-0.7.22/lib/gosu.so: /home/kota/.gem/ruby/1.8/gems/gosu-0.7.22/lib/gosu.so: undefined symbol: _ZTVN10__cxxabiv121__vmi_class_type_infoE - /home/kota/.gem/ruby/1.8/gems/gosu-0.7.22/lib/gosu.so (LoadError)
        from /usr/lib64/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:31:in `require'
        from /home/kota/.gem/ruby/1.8/gems/gosu-0.7.22/lib/gosu.rb:12
        from /usr/lib64/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `gem_original_require'
        from /usr/lib64/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `require'
        from /home/kota/NetBeansProjects/HelloGosu/lib/main.rb:2

```

The file exists as shown here:
```

kota@linux-ydzd:~/.gem/ruby/1.8/gems/gosu-0.7.22/lib> ls
gosu  gosu.rb  gosu.so

```

I am using Ruby 1.8.7 for 64 bit Linux.

If anyone could give me a clue as to what I am doing wrong, I would appreciate it greatly!  Thanks!

---

### Post by dv3500ea on 2010-07-17
> **kotakotakota said:**
> Hello,

I am brand new to Ruby (I was sucked in looking at Ruby on Rails and now Gosu...) and am stuck with trying to compile an application with the Gosu Rubygem.

This looks like a bug in the gem itself so its not your fault. 
Try reinstalling, and if that doesn't work file a bug here: [http://code.google.com/p/gosu/issues/list]("http://code.google.com/p/gosu/issues/list")

Meanwhile, try an alternative such as [RubyGame]("http://rubygame.org/").

btw. ruby programs are interpreted not compiled.

---

### Post by kotakotakota on 2010-07-17
> **dv3500ea said:**
> This looks like a bug in the gem itself so its not your fault. 
Try reinstalling, and if that doesn't work file a bug here: [http://code.google.com/p/gosu/issues/list](http://code.google.com/p/gosu/issues/list)

Meanwhile, try an alternative such as [RubyGame]("http://rubygame.org/").


Ah ok, thank you, I will try giving that a whirl.

> **dv3500ea said:**
> 
btw. ruby programs are interpreted not compiled.
Oh whoops, I meant to write "run"... A habit from writing too much C++/Java (compiled into bytecode before interpreted)/C# I suppose...

Either way, thank you very much for the speedy reply.

---

