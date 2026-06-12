---
title: "Ruby question on 'self'"
date: 2006-09-14
forum: Programming Talk
---

### Post by mdurham on 2006-09-14
Here is an extract from some code that I was looking through.
Can anyone tell me what is the purpose of "self" in:

  "def self.help(...)"
and
  "def self.parse(...)"

What difference would it make if "self" were not used?

```
  class CLIOpts 
    def self.help( options, opts )
      puts "ERROR: #{options.helpMsg}" if options.helpMsg
      puts opts
      exit
    end

    # Return a structure describing the options.
    def self.parse( args, options )
      opts = OptionParser.new do |opts|
        opts.banner = blah-blah-blah
      end
<----- cut ----->

```
Thanks, Mike

---

### Post by Jessehk on 2006-09-14
If I remember correctly (haven't done Ruby in a while), self or the name of the class in front of a method name makes it a class method.

For example:
```

class Person
    def initialize( name, age )
        @name, @age = name, age
    end

    def self.valid_age?( age )
        age > 0 and age < 200
    end

    attr_accessor :name, :age
end

person = Person.new( "Joe", 126 )
puts "#{ person.name } is #{ person.age }"

puts Person.valid_age?( 10 ) #=> true
puts Person.valid_age?( -200 ) #=> fals

```

---

### Post by mdurham on 2006-09-15
Jessehk, are you saying that if you didn't put "self.' in front of "valid_age?" it wouln't be a class method? What would it be then?
Mike

---

### Post by DeadEyes on 2006-09-15
An instance method i.e you would have to create the class before you could use it.
```

p = Person.new("bob",12)
p.valid_age?(12)
#couldn't say
Person.valid_age?(12)

```

---

### Post by mdurham on 2006-09-15
Ok I see, thanks guys. If you know C++ it would be like a class with a static method, it has no data associated with it (I guess?)
Thanks again, Mike

---

