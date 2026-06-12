---
title: "Ruby Problem"
date: 2007-05-11
forum: Programming Talk
---

### Post by Zacharias on 2007-05-11
$ sudo apt-get install ruby irb1.8 ri1.8 rdoc1.8 ruby1.8-dev build-essential
$ wget [http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz](http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz)
$ tar xzvf rubygems-0.9.0.tgz
$ cd rubygems-0.9.0
$ sudo ruby setup.rb
$ sudo gem install rails --include-dependencies

$ sudo apt-get install irb ri

********
i installed ruby by the codes above, but when i write ruby and enter on my shell prompt, it freezes, nothing happens. 

where is my mistake?

---

### Post by FuturePast on 2007-05-11
$ ruby is the "no-frills" interpreter. ( Ctrl+d to exit )

Try $ irb instead.

---

### Post by Zacharias on 2007-05-11
irb has worked thank you very much, but still when i coded for example d.rb and try to run, it says bash: ./d.rb: /usr/local/bin/ruby: bad interpreter: No such file or directory

---

### Post by FuturePast on 2007-05-11
The first line of the script should be 
```
#!/usr/bin/ruby 
```

---

### Post by Zacharias on 2007-05-11
thanks it also works, so i can start to learn ruby :)

---

### Post by Zacharias on 2007-05-12
```
#!/usr/bin/ruby

def fact(n)
  if n == 0
    1
  else
    n * fact(n–1)
  end
end
print fact(ARGV[0].to_i), "\n
```

guys when i try to run that codes it says 

./a.rb:7: Invalid char `\342' in expression
./a.rb:7: Invalid char `\200' in expression
./a.rb:7: Invalid char `\223' in expression
./a.rb:7: warning: parenthesize argument(s) for future version


where it the problem ? the other question is about IDE, could you offer me an IDE writing my ruby codes. and aldo when i try to run program, it tells me the problem more clearly?

---

### Post by FuturePast on 2007-05-12
```

#!/usr/bin/ruby

def fact(n)
  if n == 0
    1
  else
    n * fact(n-1)
  end
end
print fact(ARGV[0].to_i), "\n"
```

You've got some funny characters in there somehow. An IDE won't help you at this stage, just use a simple text editor like gedit or vi.

---

