---
title: "Diving into ruby, question about the require method"
date: 2007-05-26
forum: Programming Talk
---

### Post by maniacmusician on 2007-05-26
As the title says.

I just started looking at ruby yesterday, and this is really my first serious attempt at learning anything coding-related (other than html/css). 

So, I've learned that you can "load" certain files into a script, like you would load a CSS file from an html document, and this is done with the **require 'script'** method. 

For some reason, this isn't working for me. it allows me to load things, but it doesn't recognize anything from the loaded content. For example, I wanted to do some file manipulation with my first ruby script. So, I looked in the documentation and found that the FileUtils class would be best suited for this. So, at the beginning of the script, I added
```
require 'fileutils'
```
which is supposed to load fileutils.rb. It seems to have worked in the sense that it doesn't return any errors (like it does when you try to load something that does not exist) but none of the methods work either. I have mkdir, cd, and cp in there. If I try, it gives me this feedback:
```
undefined method `cd' for main:Object (NoMethodError)
```
Which I find weird, because cd should be defined in FileUtils. 

I've been following Why's poignant guide (I'm halfway through chapter 4), and when he used the wordlist.rb example and imported that, that didn't work for me either. I had to paste the code_words variable right into the main script to get it to recognize the variables.

So, what am I doing wrong?

Thanks.

edit: **NEVERMIND** I got it sorted out.

---

### Post by finer recliner on 2007-05-26
without having tried it myself, it appears you have to tell ruby what object the method is defined in:

```

FileUtils.cd('/', :verbose => true)   # chdir and report it

```
source: [http://www.ruby-doc.org/core/classes/FileUtils.html](http://www.ruby-doc.org/core/classes/FileUtils.html)

also try:
```

require 'fileutils.rb'

```
instead of just require 'fileutils'

---

### Post by maniacmusician on 2007-05-26
> **finer recliner said:**
> without having tried it myself, it appears you have to tell ruby what object the method is defined in:

```

FileUtils.cd('/', :verbose => true)   # chdir and report it

```
source: [http://www.ruby-doc.org/core/classes/FileUtils.html](http://www.ruby-doc.org/core/classes/FileUtils.html)

also try:
```

require 'fileutils.rb'

```
instead of just require 'fileutils'
Yeah I figured it out. It was the former. I assumed that after loading the file, I wouldn't have to specify what class  the method was in. 

On a side note, I'm really loving ruby. It's quite nice.

---

### Post by FuriousLettuce on 2007-05-27
You're not specifying the class, it's all to do with namespaces. For instance, if you are writing a game which has a function 'returnResult', but you find an external library, game.rb, that includes a function 'returnResult', you want to be able to use that library without either renaming the function in the library or one of the functions overriding the other. Namespaces allows you to do this. You can have an unlimited number of modules, all with functions of the same name, but as long as you don't import them into the global namespace (so that you only have to reference 'returnResult' rather than 'game.returnResult'), then you have access to all of those functions. See [http://en.wikipedia.org/wiki/Namespace_%28computer_science%29](http://en.wikipedia.org/wiki/Namespace_%28computer_science%29) for more info

---

### Post by Jessehk on 2007-05-27
The advice you are getting is not entirely accurate. The reason why in this case you have to specify the class name first is that those functions are class methods (or in this case, module methods). i.e., they not do operate on objects.

For example, here is an example of a method:
```

# create a new object -- a number.
n = -14

# Call the Integer#abs method on our number
# and print the result.
puts n.abs

```

And here is an example of a module Method:
```

# These methods do not work 
# on objects. Instead, they are
# sort-of "utility" methods that are associated
# with a certain class (or module).

# For example, Math.sqrt
n = 25

puts Math.sqrt( n )

```

I hope that was clear. :)

---

### Post by winch on 2007-05-27
> **Jessehk said:**
> The advice you are getting is not entirely accurate. The reason why in this case you have to specify the class name first is that those functions are class methods (or in this case, module methods). i.e., they not do operate on objects.

It's as FuriousLettuce said, modules each have their own namspace. So when you require a file containing methods in a module the methods are in the modules namespace not the namespace of the class that required the file.

You can use include to make a reference from a class to a module so you can call the modules methods without using the module name.

```

irb(main):001:0> Math.sqrt(25)
=> 5.0
irb(main):002:0> include Math
=> Object
irb(main):003:0> sqrt(25)
=> 5.0


```

---

