---
title: "Vim, ruby... and code completion?"
date: 2007-06-16
forum: Programming Talk
---

### Post by apoth on 2007-06-16
Does anyone know how to get code completion working for ruby in vim?

Thanks

---

### Post by Modred on 2007-06-16
Are you getting the error that "Ruby#omnicomplete function not found" or "not compiled with +ruby" or something along those lines?

You can check to see if it was compiled with Ruby by running *vim --version* or using the :version command inside a buffer.  If the version reports -ruby, then you'll need to either find a binary compiled for Ruby or compile one yourself.

If VIM is compiled with +ruby, then make sure first that you have Ruby installed, and second that you're using the right VIM commands. ^X^O for omni-completion.

---

### Post by apoth on 2007-06-16
+ruby is in vim --version

I'm not getting any errors, I don't know how to use it - what keys are ^X^O? I've never looked into the vi shortcut commands in enough depth to remember the shorthands.

---

### Post by Modred on 2007-06-16
> **apoth said:**
> +ruby is in vim --version

I'm not getting any errors, I don't know how to use it - what keys are ^X^O? I've never looked into the vi shortcut commands in enough depth to remember the shorthands.

By that I meant press Control+X.  So ^X^O would be Ctrl+X then Ctrl+O.  Here's an example to show you how it works:

```

class C
  def hello
    puts "Hello World"
  end
  def goodbye
    puts "Goodbye, cruel world"
  end
end

x = C.new

```
Now, when you get here, type **x.** and then press ^X^O.  It should give you a little box to select from hello and goodbye methods.  And that's all there is to it.  I normally use an example like this to test the completion since it will limit the number of options presented, but you could just as easily assign a string to **x** and then use ^X^O to choose from the methods.

You can also use ^N^P (or either of them separate, as ^N or ^P will shortcut to ^N^P) to do a general word completion.  Useful for typing long variable or function names.  There are several other types of auto completion, but omnicompletion (^X^O) and keyword completion (^N^P) are what you'll probably use the most.

You might also find the **gf** command useful.  If you have separate class files (or are using some built in packages), you can put the cursor on the class name and then, in command mode, type **gf**.  It will then replace your current buffer with the file that defines that class.

---

### Post by apoth on 2007-06-17
Fantastic. Thanks a lot, hugely valuable post. :)

---

