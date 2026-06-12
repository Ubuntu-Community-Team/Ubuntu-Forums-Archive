---
title: "Installing Ruby on Rails"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by David Miller on 2008-04-24
I've been attempting to install ruby on rails, by following the instructions at [http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu](http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu)

This hasn't worked, and I'm unsure why. I am new to installing anything on Ubuntu, and using the terminal, which i don't really understand. 

I got as far as 

  ~$ cd rubygems-1.1.0.tgz

in the following sequence

  ~$ wget
"http://rubyforge.org/frs/download.php/34638/rubygems-1.1.0.tgz" 
  ~$ tar -xvzf rubygems-1.1.0.tgz
  ~$ rm rubygems-1.1.0.tgz
  ~$ cd rubygems-1.1.0.tgz
  ~$ sudo ruby setup.rb
  ~$ sudo rm -rf rubygems-1.1.0/

only to be told that there is no such file or directory. I attempted to continue with the rest of the instructions, but it's clearly going nowhere for me. 

Any help would be much appreciated

---

### Post by philphil on 2008-04-26
> **David Miller said:**
> 
  ~$ wget
"http://rubyforge.org/frs/download.php/34638/rubygems-1.1.0.tgz" 
  ~$ tar -xvzf rubygems-1.1.0.tgz
  ~$ rm rubygems-1.1.0.tgz
  ~$ cd rubygems-1.1.0.tgz
  ~$ sudo ruby setup.rb
  ~$ sudo rm -rf rubygems-1.1.0/

only to be told that there is no such file or directory. I attempted to continue with the rest of the instructions, but it's clearly going nowhere for me. 

Any help would be much appreciated

Try skipping the line "rm rubygems-1.1.0.tgz"

---

### Post by todderick on 2008-04-27
> **David Miller said:**
> I've been attempting to install ruby on rails, by following the instructions at [http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu](http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu)

This hasn't worked, and I'm unsure why. I am new to installing anything on Ubuntu, and using the terminal, which i don't really understand. 

I got as far as 

  ~$ cd rubygems-1.1.0.tgz

in the following sequence

  ~$ wget
"http://rubyforge.org/frs/download.php/34638/rubygems-1.1.0.tgz" 
  ~$ tar -xvzf rubygems-1.1.0.tgz
  ~$ rm rubygems-1.1.0.tgz
  ~$ cd rubygems-1.1.0.tgz
  ~$ sudo ruby setup.rb
  ~$ sudo rm -rf rubygems-1.1.0/

only to be told that there is no such file or directory. I attempted to continue with the rest of the instructions, but it's clearly going nowhere for me. 

Any help would be much appreciated


Remove .tgz from the cd line....  should work like a charm.

so it should be:
 ~$ cd rubygems-1.1.0

---

### Post by David Miller on 2008-04-28
Thanks, I removed the .tgz and it was fine. And now I feel slightly silly for not having realised what it meant by no such directory!

But at least the only thing I have to worry about now is learning to use rails.

---

