---
title: "Python interpretor in Kdevelop"
date: 2007-11-21
forum: Programming Talk
---

### Post by Clarke on 2007-11-21
Hello, I've decided to start learning python and use Kdevelop as IDE.
When I use use the expression raw_input and try to execute the programm inside Kdevelop, it writes:
```
EOFError: EOF when reading a line
``` 
Though the same script can be successfully executed in gnome terminal. 
So how to make Kdevelop execute python scripts right?

---

### Post by Clarke on 2007-11-21
.

---

### Post by LaRoza on 2007-11-21
If you want an IDE, IDLE might be what you want. I never use IDE's so can't help directly.

---

### Post by tyoc on 2007-11-21
I recommend SPE (it has his things), also there is IDLE and more simple there is geany.


Offtopic: I have watched this day oa anterior to much post with only a point in them?? or Im crazy?? why is that?

---

### Post by smartbei on 2007-11-22
I highly recommend Geany - as for me it turned out much more lightweight and stable than SPE. [Is the OP even asking for recommendations? - This is why you don't drastically edit/delete posts in the middle of a thread]

The posts with the period are when people edit their post to have only a period, probably because vB does not allow empty posts.

---

### Post by ankursethi on 2007-11-22
AFAIK, Python support in KDevelop is still in it's infancy. I remember reading an interview of the guy working on this in the Linux For You magazine.

---

### Post by Kadrus on 2007-11-22
The best Integrated Development Environment for Python is IDLE
You can install it by typing this:
```
sudo apt-get install idle

```
It's really really good..trust me..

---

### Post by Clarke on 2007-11-22
Thanks, IDLE seems to be good so far. 
[Sry for that blank post, I must be missclicked or something]

---

### Post by LaRoza on 2007-11-22
> **Clarke said:**
> Thanks, IDLE seems to be good so far. 
[Sry for that blank post, I must be missclicked or something]

No problem, I or the internet connection has resulted in a few odd posts for me as well.

---

### Post by Xbehave on 2008-05-18
same problem still seams to be around but you can always use the konsole kpart to manually launch the program from within kdevelop

---

### Post by rye_ on 2008-05-18
**_EDIT: i DIDN'T REALISE HOW OLD THIS THREAD WAS!_**


try gedit with plugins...

with the 'external tools' plugin create a new shortcut command to interpret python code, e.g. control+f8; then assign code within the shortcut capable of interpreting a python file.

if you install ruby, you can use my code below, which interprets python, ruby, and perl, depending on the file type (e.g. '.py') you are intepretting.

```


#!/usr/bin/ruby

#(0...ENV.length).each {|x| puts "#{ENV.keys[x]} : #{ENV.values[x]}"} #useful environment variables

#check that the input file is appropriate
raise "not a ruby, python or perl file"  unless  ENV['GEDIT_CURRENT_DOCUMENT_NAME'] =~ /\.(rb|p(y|l))/

#use the appropriate interpreter
interpreter_hash = {'.rb' => 'ruby', '.py' => 'python', '.pl' => 'perl'}
interpreter = nil
interpreter_hash.keys.each {|x|  interpreter = interpreter_hash[x]; break if x == $& }

puts  `#{interpreter} #{ENV['GEDIT_CURRENT_DOCUMENT_PATH']}`


```

side browser, snap open, class browser plugins etc really make gedit an excellent text editor.

Ryan

---

### Post by ingo on 2008-10-14
Yep, old thread, but I'd recommend Eric4.

Having said that, maybe Kdevelop supports python these days...

---

