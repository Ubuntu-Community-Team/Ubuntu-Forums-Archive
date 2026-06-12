---
title: "running ruby in eclipse"
date: 2009-09-12
forum: Programming Talk
---

### Post by cybo on 2009-09-12
I was trying to learn more of ruby syntax but I'm unable to run the code for it. I have created a class and wanted to write a simple program using it. But for some reason it didn't work for me. Whenever I compile it I get the following error:
cash_register_test.rb:1: uninitialized constant CashRegister (NameError)

Can you explain what is the problem with this code:

cash_register.rb
```

class CashRegister
  def initialize
    @purchase = 0;
    @payment = 0;
  end

  def record_purchase(amount)
    @purchase += amount
  end
end

```

cash_register_test.rb
```

reg = CashRegister.new

```

---

### Post by falconindy on 2009-09-12
You need to make sure you 'require' your class file. Put this at the top of cash_register_test.rb:
```
require 'cash_register.rb'
```
Provided of course, that both files are in the same directory.

---

### Post by cybo on 2009-09-12
thanks for the reply.

what do i need to do if they are in different folders? it doesn't work if i just use require. it still gives me errors

---

### Post by falconindy on 2009-09-12
If they're in separate folders, then you'll need to provide an absolute or relative path to the library.

Alternatively, you could put the library in a place that's accessible via the $PATH variable.

---

### Post by cybo on 2009-09-12
i'm new to eclipse and ruby. falconindy can you tell me how would i provide a relative path to the folder where my code is

---

### Post by falconindy on 2009-09-12
> **cybo said:**
> i'm new to eclipse and ruby. falconindy can you tell me how would i provide a relative path to the folder where my code is
A relative path defines the location of a file based on where you currently are. Relative paths will **never** start with a '/'. An absolute path defines the location of a file starting from root. Absolute paths will **always** start with a '/' or '~/'.

Suppose your cash_register_test.rb file resides in "~/dev/ruby/", and then your cash_register.rb file is in "~/dev/ruby/cash", you would need one of the following (they're equivalent as long as cash_register_test.rb never moves)
```
require 'cash/cash_register.rb'
require '~/dev/ruby/cash/cash_register.rb'
```...at the top of your cash_register_test.rb file. However, suppose you moved your cash_register.rb file to a generic includes directory that was at "~/includes". With your test file in the same place, you'd need one of these:
```
require '../../includes/cash_register.rb'
require '~/includes/cash_register.rb'
```In both these cases, the first path given is the relative path. The second path is the absolute. Both have their uses.

---

### Post by cybo on 2009-09-12
one thing i forgot to mention is that i currently run eclipse and ruby under winows platform :(

here is what i get when i use
```

require '../../lib/cash_register.rb'

```

C:/Ruby/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require': no such file to load -- ../lib/cash_register.rb (LoadError)
	from C:/Ruby/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
	from test/cash_register_test.rb:2

do you know what the problem might be?

---

### Post by falconindy on 2009-09-12
Hmm, looks like it's trying to use the relative path based on the location of Ruby. Better just go with an absolute. You may also want to use a double backslash ( \\ ) in place of each slash ( / ).

---

### Post by cybo on 2009-09-12
falonindy thanks for your help. 

it turns out that in windows it won't accept a relative path. only absolute worked for me. i figured that it was something to do with the environment variable settings. so i went to the project propteries->ruby load path->source tab->add foldter button and added my source code directory. reran the code and it worked. 

again thanks for all the help.

---

