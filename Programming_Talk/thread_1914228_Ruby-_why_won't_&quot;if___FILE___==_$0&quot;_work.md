---
title: "Ruby- why won't &quot;if __FILE__ == $0&quot; work?"
date: 2012-01-23
forum: Programming Talk
---

### Post by Ms. Daisy on 2012-01-23
I'm playing around with Ruby for the first time & I just did a [tutorial]("http://www.ruby-lang.org/en/documentation/quickstart/").  I copied the  script shown below.  I saved it as a .rb file, then I called it in  terminal. 
It pukes at
```
if __FILE__ == $0
``` When I remove that line (and the "end") the script runs fine. 

Can anyone tell me why the line isn't working?

Here's the script.  The lines I have to delete in order for it to run are shown in bold.
```
#!/usr/bin/env ruby

class MegaGreeter
    attr_accessor :names

    #Create the object
    def initialize(names = "World")
        @names = names
    end

    #say hi to everybody
    def say_hi
        if @names.nil?
            puts "..."
        elsif @names.respond_to?("each")

            # @names is a list of some kind, iterate!
            @names.each do |name|
                puts "Hello #{name}!"
            end
        else
            puts "Hello #{@names}!"    
        end
    end

    #say bye to everybody
    def say_bye
        if @names.nil?
            puts "..."
        elsif @names.respond_to?("join")
            #join the list elements with commas
            puts "Goodbye #{@names.join(", ")}. Come back soon!"
        else
            puts "Goodbye #{@names}. Come back soon!"
        end
    end
end

**if __FILE__ == $0**
    mg = MegaGreeter.new
    mg.say_hi
    mg.say_bye

    #change name to be zeke
    mg.names = "Zeke"
    mg.say_hi
    mg.say_bye

    #change name to an array of names
    mg.names = ["Albert", "Brenda", "Charles", "Dave", "Englebert"]
    mg.say_hi
    mg.say_bye


    #Change to nil
    mg.names = nil
    mg.say_hi
    mg.say_bye
**end**

```

---

### Post by Vaphell on 2012-01-23
i copypasted the code and it works fine

---

### Post by cgroza on 2012-01-24
How do you run the file?

---

### Post by Ms. Daisy on 2012-01-24
I saved it as a .rb file, then I called it in  terminal by typing 
```
ruby filename.rb
```
But now it's inexplicably working.  Apparently I had to just publicly ask the question in order for it to work.
Thanks anyway.

---

