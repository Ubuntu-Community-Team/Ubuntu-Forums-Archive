---
title: "Installing Ruby Rails"
date: 2007-12-11
forum: Programming Talk
---

### Post by delphiguy on 2007-12-11
Cheers,

I wanted to try out Ruby Rails so I followed the instructions from this site
[http://www.searchmarked.com/ubuntu/install-ruby-on-rails-in-ubuntu.php](http://www.searchmarked.com/ubuntu/install-ruby-on-rails-in-ubuntu.php)

But when I got to this part
sudo gem update --system

I get this error:
Updating RubyGems...
Attempting remote update of rubygems-update
ERROR:  While executing gem ... (Gem::Exception)
    SSL is not installed on this system


Any idea what this means?

Thanks.

---

### Post by ThinkBuntu on 2007-12-11
Sounds like a missing dependency, but there's pretty much no chance your computer's missing SSL. Clearly their style of installing RubyGems is incorrect, so do it the natural way:
```
$ sudo apt-get install rubygems
```
or whatever the package is called. I haven't been on a Linux box in a while. Then,
```
$ sudo gem update
$ sudo gem install rails
```
I've found that, for whatever reason, the "automatically install dependencies" option makes RubyGems fail the install, so just sit there for a few minutes and agree to install RDoc, ActiveRecord, etc.

---

### Post by hstagner on 2007-12-11
Hello Delphiguy,

I recently ran across this same error on one of my other Ubuntu boxes. 

You need to install "libopenssl-ruby"

```
sudo apt-get install libopenssl-ruby
```

That worked for me.

BTW- I wrote that tutorial that you followed at [Searchmarked.com]("http://www.searchmarked.com")

Thanks for reading!  I have also [updated the tutorial]("http://www.searchmarked.com/ubuntu/install-ruby-on-rails-in-ubuntu.php") to reflect the current version of ruby gems 0.9.5 and the error that you were having trouble with.

I am sorry that you ran into this problem. I hope this helps and I look forward to having you as a reader in the future.

Regards,

Harley Stagner
-[http://www.searchmarked.com]("http://www.searchmarked.com")

---

### Post by delphiguy on 2007-12-11
cool, thanks a lot, i'll give it another try when i get home from work.

---

### Post by delphiguy on 2007-12-12
Cheers, 

Ok new one... I got a new error when I do this:
**sudo gem install rails -y**

```

delphiguy@zion-laptop:~/rubygems-0.9.5$ sudo gem install rails -y
INFO:  `gem install -y` is now default and will be removed
INFO:  use --ignore-dependencies to install only the gems you list
ERROR:  While executing gem ... (Gem::RemoteFetcher::FetchError)
    OpenURI::HTTPError: 404 Not Found reading http://gems.rubyforge.org/gems/rails-2.0.1.gem

```

also when I did this:
**sudo gem install mysql**

I got this error
```
delphiguy@zion-laptop:~/rubygems-0.9.5$ sudo gem install mysql
Building native extensions.  This could take a while...
ERROR:  Error installing mysql:
        ERROR: Failed to build gem native extension.

/usr/bin/ruby1.8 extconf.rb install mysql
extconf.rb:1:in `require': no such file to load -- mkmf (LoadError)
        from extconf.rb:1


Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/mysql-2.7 for inspection.
Results logged to /usr/lib/ruby/gems/1.8/gems/mysql-2.7/gem_make.out
```

Any ideas?

Thanks.

---

### Post by hstagner on 2007-12-12
Hello delphiguy,

With the 404 error, trying the:

```
sudo gem install rails -y 
```

again usually gets you past the error.

Sometimes the server doesn't respond the first few times.

I haven't found the answer to the MySQL error yet. I hope this helps.

Regards,

Harley Stagner
[http://www.searchmarked.com]("http://www.searchmarked.com")

---

### Post by delphiguy on 2007-12-12
Cheers,

redoing the command 
```

sudo gem install rails -y 
```seems to have fixed it.

Although the the mySql issue is still there.

Now I have another one.  I installed Eclipse, but it says  that Ruby isnt installed and gives me 3 Options/Buttons.
[B]Download Ruby
Setup Preferences
Use Included JRuby[/B]
So which one of the 3 should I choose?

I wanted to learn Ruby first, and when I am versed enough with Ruby then I will learn Rails.
So can anyone here point me to some cool tutorials?

Thanks.

---

### Post by hstagner on 2007-12-12
Hello delphiguy,

I do not have any experience with Eclipse (I just use good 'ole nano or gedit)

However, if you are looking for Ruby Tutorials, then [Why's Poignant Guide to Ruby]("http://poignantguide.net/ruby/") is certainly the most entertaining one that I have seen.  It is definitely a cool tutorial.

I hope this helps.

Regards,

Harley Stagner
[http://www.searchmarked.com]("http://www.searchmarked.com")
"I search, I bookmark, I write, you learn."

---

### Post by delphiguy on 2007-12-12
Thanks I'll be checking on the link now.
This is really entertaining read.  Is there an Offline Copy of this?

---

### Post by keylife on 2007-12-14
hstagner--Thanks for writing that tutorial! Very helpful. I'm getting the same error as delphiguy when I enter the "sudo gem install mysql" command. I'd appreciate any ideas you might have on that. Thanks!

---

### Post by hstagner on 2007-12-14
Hello keylife,

Thanks for reading the tutorial and visiting [Searchmarked.com]("http://www.searchmarked.com")

I have done some research on this problem, but I have not experienced the problem so anything I say is simply a guesstimate :)

Have you installed "mysql-server"? Also you may need to install "libmysqlclient" for the mysql gem to work.

```
sudo apt-get install libmysqlclient
```

Please let me know if this helps.

---

### Post by revchris on 2007-12-16
that didn't work for me, got the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libmysqlclient

---

### Post by delphiguy on 2007-12-16
I tried doing it also but I got the same error as revchris.

---

### Post by keylife on 2007-12-16
I was able to install that by entering:
sudo apt-get install libmysqlclient15-dev

But it didn't solve the problem. I already had the newest version installed. I do have mysql-server installed, but I'm still getting the error "Error installing mysql: Error: failed to build gem native extension" when I attempt to enter sudo gem install mysql.

Thanks again for any ideas.

---

### Post by hstagner on 2007-12-16
Hello delphiguy and revchris,

I think I found the solution. mkmf.rb is part of the ruby1.8-dev package. Install it with the following:
```

sudo apt-get install ruby1.8-dev
```

```
sudo gem install mysql
```

worked like a champ after that! Let me know if this works for you. I am also going to update [my tutorial at Searchmarked.com]("http://www.searchmarked.com/ubuntu/install-ruby-on-rails-in-ubuntu.php").

---

### Post by keylife on 2007-12-16
That did it! Thanks for running that down so quickly. I was still researching when I got your update. Probably saved me the afternoon!

---

### Post by delphiguy on 2007-12-16
thanx hstagner, will try it out when I get home from work.

---

### Post by delphiguy on 2007-12-17
Hey that totally solved the issue, now on to learning more of my new favorite programming language.

Thanks a lot hstagner.

---

### Post by revchris on 2007-12-17
Thanks!!!! :guitar:

---

