---
title: "Ruby Loadpath"
date: 2010-10-22
forum: Programming Talk
---

### Post by nova47 on 2010-10-22
I'm attempting to require a class in a separate class. However, I have found that Ruby requires me to hardcode the address of the file I'm requiring. EG: I have to type require '/home/grant/...blank.rb' rather than just blank.rb to actually get the file to be properly included in the code. The issue is that this is a school project that will be turned into a grader who's path will obviously not be identical to mine. How do I make it so the class path does not have to be hardcoded in order to work?

Code:

[PHP]
require 'F:\Programming\eclipseWorkspace\CSE_655\file_handler.rb'


class Main
  
  print "Enter file path: "
  
  #Get the file name from the user and open the file.
  file = FileHandler.new(gets)
  
end
[/PHP]

FileHandler Class:

[PHP]
class FileHandler
  
  def initialize(fileToParse)
    @fileToParse = fileToParse
  end
  
  
end
[/PHP]

---

### Post by dv3500ea on 2010-10-23
You can add paths to the require search path like this:

```

[color=blue]$:[/color]<< **ENV**[[color=green]'HOME'[/color]] [color=grey]#add user's home directory to search paths[/color]
[color=blue]$:[/color]<< [color=green]"[/color]#{**ENV**[[color=green]'HOME'[/color]}[color=green]/another_folder" [/color][color=grey]#add users ~/another_folder to search paths[/color]

```

---

### Post by nova47 on 2010-10-23
You'll have to bare with me, I'm really new to Ruby, but how do I make it work just like Java where all I do is make sure the user keeps everything in the same folder and it will still run? The grader isn't going to want to have to manually input the path.

---

### Post by dv3500ea on 2010-10-23
If everything is in one folder, you can use relative paths. You can replace ```
**ENV**[[color=green]'HOME'[/color]]
``` with ```
**Dir**.[color=purple]pwd[/color]
``` in the example above.

---

### Post by gmargo on 2010-10-23
> **nova47 said:**
> How do I make it so the class path does not have to be hardcoded in order to work?

There are a number of environment variables that Ruby is supposed to use; RUBYLIB is probably what you're looking for.

[http://www.ruby-doc.org/docs/ProgrammingRuby/html/rubyworld.html#S3](http://www.ruby-doc.org/docs/ProgrammingRuby/html/rubyworld.html#S3)

---

### Post by nova47 on 2010-11-02
Is there no way to just say the current working path? What if he doesn't put it in the folder that I add to path etc? Basically I want it to do exactly what Java does. I don't want to have to hardcode the path in any way. I just want to say keep it all in the same folder and run it.

---

### Post by dv3500ea on 2010-11-02
You can get the directory the file you are running is in with:

```

File.dirname(__FILE__)

```

You can require relative paths from there:

```

require "#{File.dirname(__FILE__)}/../../lib/something.rb"

```
That example would require the ruby file that is called 'something.rb' and in the 'lib' folder of the folder 2 folders above the folder that the ruby program is in.

---

### Post by nova47 on 2010-11-02
Where is the .basedir method defined? When I tried to put it in my code I got the error

[PHP]
	F:\Programming\655\655\main.rb:11
	F:/devtools/ruby187/lib/ruby/gems/1.8/gems/ruby-debug-ide-0.4.5/lib/ruby-debug.rb:101:in `debug_load'
	F:/devtools/ruby187/lib/ruby/gems/1.8/gems/ruby-debug-ide-0.4.5/lib/ruby-debug.rb:101:in `debug_program'
	F:/devtools/ruby187/lib/ruby/gems/1.8/gems/ruby-debug-ide-0.4.5/bin/rdebug-ide:82
	F:/devtools/ruby187/bin/rdebug-ide:19:in `load'
	F:/devtools/ruby187/bin/rdebug-ide:19
Uncaught exception: undefined method `basedir' for File:Class
[/PHP]

I went and looked up the File class at [http://ruby-doc.org/docs/ProgrammingRuby/](http://ruby-doc.org/docs/ProgrammingRuby/) and I don't see it there either. There's a basename method though. That's the closest I found. But it returns the last component of the filename given in fileName which would just be the name of the class.

---

### Post by dv3500ea on 2010-11-02
Sorry, it is ```
dirname
``` (I was mixing it up with basename that gives you just the file name without the full directory path.)

---

### Post by nova47 on 2010-11-02
I just figured it out. Thanks dv3500ea. There wasn't a basedir method but I just figured out what you meant by relative paths. I just used Dir.pwd. When you originally posted I didn't know where to put it. (I hadn't yet discovered the pragmatic programmers guide so I didn't know what Dir.pwd did. :-D) I looked up the Dir class and discovered what it did and how to use it lol

---

### Post by nova47 on 2010-11-02
Next question how do you get it into the requires statement?

I tried:

require 'Dir.pwd\file_handler.rb'

require "Dir.pwd\file_handler.rb"

require Dir.pwd\file_handler.rb

None of which it liked :-(

---

### Post by dv3500ea on 2010-11-02
String interpolation:

```

require "#{Dir.pwd}/file_handler.rb"

```

---

### Post by nova47 on 2010-11-02
Ya I feel a bit foolish (again) I just read your old posts and came up with:

$:<< Dir.pwd

require 'file_handler.rb'
require 'tokenizer.rb'

And got it to work. I'll use your code to make it a little more clean. Thanks for all the help. It hasn't been an easy switch from Java, C++/C# to something like Ruby lol. Just out of curiosity what function do the brackets add?

---

