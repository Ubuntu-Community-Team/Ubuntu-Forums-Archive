---
title: "better ways ?"
date: 2009-02-24
forum: Programming Talk
---

### Post by thirddeep on 2009-02-24
I am writing a bit of code that generates a config file.

Data is read from command arguments like (using optparse) : 

```
./my_script.py --build=a --ip=b --netmask=c ...
```

And the bit inside the script that writes this to file :

```
my_file = file("test", 'w')
print >> my_file, "# Lost of text describing this thing."
print >> my_file, "BUILD=%s" % (options.build_type)
print >> my_file, "IP=%s" % (options.ip_address)
... 15 more things to write to file ...
my_file.close()
```

Now, this works without problem.  But I am wondering, is there a better way writing all the argument variable to a file and include some explanation text above it ?

I have read a bit on configparser, but that seems mostly for reading config files.  Unless of course, I missed the crucial part :-)

Thd.

---

### Post by nvteighen on 2009-02-24
Why not just file.write() and similar methods?

---

### Post by thirddeep on 2009-02-24
How do I get the variable in (and without a space in front of it) with file.write() ?

Thd.

---

### Post by nvteighen on 2009-02-24
> **thirddeep said:**
> How do I get the variable in (and without a space in front of it) with file.write() ?

Thd.
Just do file.write(your-string)... Of course, you have to open the file for writing.

---

### Post by Can+~ on 2009-02-24
[PHP]my_file = file("test", 'w')

my_file.write("""# Lost of text describing this thing.
BUILD=%s
IP=%s
""" % (options.build_type, options.ip_address, ...))

my_file.close()[/PHP]

You could also use a dictionary and fill in the blanks with it. Maybe using the options.__dict__? Long time without pythonic love.

To use a dictionary as a string-filler:

[PHP]some_dict = {"key":"value", "location":"world", "meaning of life":42}

print "Hello %(location)s" % some_dict

#Or shorter version

print "Hello %(location)s" % {"location":"world"}[/PHP]
(python 2.5)

---

### Post by dwhitney67 on 2009-02-24
If you have the energy to type in the many parameters to pass to your py-script, you might as well type them manually into the config file you are trying to create.

I'd be more focused on writing a parser for the config file, rather than a script that creates it.

---

### Post by Can+~ on 2009-02-24
> **thirddeep said:**
> I have read a bit on configparser, but that seems mostly for reading config files.  Unless of course, I missed the crucial part :-)

[http://docs.python.org/library/configparser.html#examples](http://docs.python.org/library/configparser.html#examples)

See the first example.

---

### Post by Martin Witte on 2009-02-24
withdrawn - Can~+ wrote the same thing - I missed that ....

---

### Post by thirddeep on 2009-02-25
Thanks for all the replies, that helps a lot :-)

Can~+ gave me exactly what I was looking for.

Like I said, it was working, but I am trying to learn the "better" ways :-)

Thd.

---

