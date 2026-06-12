---
title: "shoes gui"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by jredkai on 2012-03-29
I'm sure this is already out there but for the love of all that is holy has anyone figured out how to get this gui working. evertime I try to run it I get " no such file to load -- rubygems " for an error. I've already " sudo apt-get install rubygems " and it is installed. even downloading the file from the [http://shoesrb.com/](http://shoesrb.com/) site I still end up with the errors. All I want to do is learn to make gui apps with Ruby..... Any help will be greatly appreciated.

Thanx

---

### Post by winh8r on 2012-03-29
According to the manual :

[http://shoesrb.com/manual/Installing.html]("http://shoesrb.com/manual/Installing.html")

there is nothing to do other than download a .run file and then double click it.
 But I have just tried to run it in virtual box and it seems to be looking for a directory "/shoes" which it cannot find.

probably an error in the script somewhere.


********EDIT********
There appears to be a conflicting set of  installation instructions here:
[https://github.com/shoes/shoes/wiki/Building-Shoes-on-Linux]("https://github.com/shoes/shoes/wiki/Building-Shoes-on-Linux")

looks like someone edited one and not the other.

---

### Post by jredkai on 2012-03-30
I don't know, I think I will give up with compiling it for now, I'm running into errors with Ruby, RVM, and a few other things....I guess I will just wait awhile and tinker with it some and see if I can't come up with something. If anyone has suggestions please let me know. More than anything right now I just want to learn Ruby not Ruby on Rails, I'm not interested in web development at this time.


Thank you!

---

### Post by jredkai on 2012-03-31
Ok, so I figured it out. If anyone else wants Shoes do not download it from the Ubuntu Software Center, go to the shoes website and open the link: [http://shoesrb.com/downloads](http://shoesrb.com/downloads) and open the file: **Shoes 2 (0.r1134)**, codenamed [I]&#8220;Raisins&#8221; for linux. Save that webpage as .run file, open properties for file (it is a script file) and mark as executable. Then open program, tell it to run and viola! I cannot remember the page I found the answer to this so I can't give props to the guy, so "Mr. Nameless" thank you!

Okay, so I found the link with the answer:
[http://stackoverflow.com/questions/857137/the-package-option-for-shoes-on-linux](http://stackoverflow.com/questions/857137/the-package-option-for-shoes-on-linux)

Thank you Johnny Panzer!

Now how do I mark this fraggin' thread closed?!?
[/I]

---

