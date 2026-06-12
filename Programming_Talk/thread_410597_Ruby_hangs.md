---
title: "Ruby hangs"
date: 2007-04-15
forum: Programming Talk
---

### Post by potterzot on 2007-04-15
I'm working through Programming Ruby, but whenever I try to run a ruby program, it just hangs.  This occurs even if I do something like type 'ruby' at the prompt.  The only way I can get it to run is by running it through irb, but then it prints out everything in the script, even the comments.

Is there something I'm not doing right here?

Thanks for your help

---

### Post by WW on 2007-04-16
I created the file hello.rb that contains just one line:
```

print "Hello, world!\n"

```
Then I gave the command **ruby hello.rb**:
```

$ ruby hello.rb
Hello, world!

```
Does that work for you?

Could you give a small example of a ruby program and the commands that you used that make it "just hang"?

By the way, if you type **ruby** with no arguments, it will read the program from the terminal. For example:
```

$ ruby
print "Hello, world!\n"   # I typed this and the next print statements.
print "How are you?\n"    # After I entered this print statement, I hit ctrl-D
Hello, world!
How are you?
$

```
After typing the second print statement and hitting Enter, I hit ctrl-D to end my input.  ruby then executed the two print statements.

---

### Post by potterzot on 2007-04-16
Hey thanks.  I had seen the Ctrl D somewhere else, but forgot about it.  And now I can't reproduce the other error.  I feel silly now.  Thanks for your help anyway.

---

