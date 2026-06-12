---
title: "New guy learn Ruby in Eclipse"
date: 2007-05-08
forum: Programming Talk
---

### Post by tc101 on 2007-05-08
I am just learning Ruby.  I am a dot net programmer and have never used Eclipse or Java, just VB dot net.

I set up Eclipse to work with ruby.  I created a ruby project with one file in it.  The file contains one line:

"Hello World"

I ran it and I get this message:

:in `slice': no implicit conversion from nil to integer (TypeError)

What am I doing wrong?

---

### Post by finer recliner on 2007-05-08
use the keyword "puts" (print a string to the terminal followed by a newline char)

or use "print" for normal print functionality

```

puts "hello world"
print "hello world \n"

```

i <3 ruby
i hope you like it too ;)

---

### Post by tc101 on 2007-05-08
I still get the same error.  Do I have to put the code 

puts "hello world"

inside a module or a class?  I just have that one line of code in the file.

Here is everything I see in the console

/home/tomcarr/../../../home/tomcarr/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.rubypeople.rdt.testunit_0.9.0.200704141430RC1/ruby/RemoteTestRunner.rb:281:in `slice': no implicit conversion from nil to integer (TypeError)
from /home/tomcarr/../../../home/tomcarr/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.rubypeople.rdt.testunit_0.9.0.200704141430RC1/ruby/RemoteTestRunner.rb:281

---

### Post by skeeterbug on 2007-05-08
> **tc101 said:**
> I still get the same error.  Do I have to put the code 

puts "hello world"

inside a module or a class?  I just have that one line of code in the file.

Here is everything I see in the console

/home/tomcarr/../../../home/tomcarr/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.rubypeople.rdt.testunit_0.9.0.200704141430RC1/ruby/RemoteTestRunner.rb:281:in `slice': no implicit conversion from nil to integer (TypeError)
from /home/tomcarr/../../../home/tomcarr/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.rubypeople.rdt.testunit_0.9.0.200704141430RC1/ruby/RemoteTestRunner.rb:281

It looks like you are trying to run a unit test module or something. Go to the run configuration and make sure it is running your program with just the ruby interpreter. You can also try it from the command line:

```
ruby myprogram.rb
```

You can also mess around with ruby using its own interactive shell, called irb.

```
$>irb
irb(main):001:0> puts "Hello World!"
Hello World!
=> nil
irb(main):002:0> 
```

Notice how puts "Hello World!" is returning nil (Nothing, if you are coming from VB). The test fixture was trying to test for integer. "no implicit conversion from nil to integer (TypeError)".

---

### Post by tc101 on 2007-05-08
> You can also mess around with ruby using its own interactive shell, called irb.

Everything works fine from the irb shell.  It also works fine if I just run the ruby code in File1 from the command liine with:

ruby File1

So my problem is in eclipse 

> Go to the run configuration and make sure it is running your program with just the ruby interpreter. 

How do you do that?  I am hunting around and haven't figured it out yet.

---

### Post by skeeterbug on 2007-05-08
If you click the Run menu, there is a Run... option. Click that, and setup a new configuration. Usually this asks for the project and the file to execute.

---

### Post by tc101 on 2007-05-08
> If you click the Run menu, there is a Run... option. Click that, and setup a new configuration. Usually this asks for the project and the file to execute.

Thanks for your help.  I am moving in a positive direction and learning.  I see how to setup the new configuration.  Now I am getting an error 

:in `require': no such file to load -- file1 (LoadError)

However it runs just fine from the command line.

the whole contents of the console window is 

/home/tomcarr/../../../home/tomcarr/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.rubypeople.rdt.testunit_0.9.0.200704141430RC1/ruby/RemoteTestRunner.rb:287:in `require': no such file to load -- file1 (LoadError)
	from /home/tomcarr/../../../home/tomcarr/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.rubypeople.rdt.testunit_0.9.0.200704141430RC1/ruby/RemoteTestRunner.rb:287

---

### Post by tc101 on 2007-05-08
RemoteTestRunner.rb highlights this line:

require filename.gsub(/.+::/, '')

---

### Post by skeeterbug on 2007-05-09
> **tc101 said:**
> RemoteTestRunner.rb highlights this line:

require filename.gsub(/.+::/, '')

It still looks like it is hitting a unit test. Are you running the new configuration you setup? You can run the application using this new configuration through the Run menu as well or you can click the drop down arrow on the Green play button on the top toolbar(this lets you choose a run configuration to execute).

---

