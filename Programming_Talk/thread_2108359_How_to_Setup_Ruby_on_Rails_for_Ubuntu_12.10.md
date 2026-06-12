---
title: "How to Setup Ruby on Rails for Ubuntu 12.10?"
date: 2013-01-24
forum: Programming Talk
---

### Post by rich1939 on 2013-01-24
I need to install Ruby & Rails and all of the other components needed for complete development using Ruby on Rails. I see that Ruby is already installed (version 1.9.3) and I installed "git", but I don't have Rails and believe that there is probably a "sudo apt-get" command that will get it and any supporting packages.

Although I have been programming for over 40 years and have lots of experience with object-oriented languages, I have never used Ruby and understand that it is good for creating dynamic web pages, when coupled with the Rails framework, RubyGems, Sqlite, etc.

Any help in getting all of the components (and their documentation) would be greatly appreciated.

Thanks,

Rich

---

### Post by Mikeb85 on 2013-01-24
The command is "sudo **gem** install rails".

You install Ruby libraries (or gems as they're known) with a tool called Rubygems (command is "gem") which is included as part of 1.9.3.  It's really incredibly easy, Ruby has by far the easiest package management of any programming language.

Rubygems automatically installs documentation (accessed by the command "ri", or by typing "help" when you're in an "irb" session).  Ruby is a great language, and it's worthwhile to learn some of it on it's own, Rubymonk.com is a great place to learn the basics of it for free.  (not trying to sell you on any service, but I'm a newbie to programming, picked up Ruby, love it, so I am a little passionate about how great it is :) )

---

### Post by rich1939 on 2013-01-24
> **Mikeb85 said:**
> The command is "sudo **gem** install rails".

You install Ruby libraries (or gems as they're known) with a tool called Rubygems (command is "gem") which is included as part of 1.9.3.  It's really incredibly easy, Ruby has by far the easiest package management of any programming language.

Rubygems automatically installs documentation (accessed by the command "ri", or by typing "help" when you're in an "irb" session).  Ruby is a great language, and it's worthwhile to learn some of it on it's own, Rubymonk.com is a great place to learn the basics of it for free.  (not trying to sell you on any service, but I'm a newbie to programming, picked up Ruby, love it, so I am a little passionate about how great it is :) )

Thank you very much for your reply. Even though I have many years of programming experience, I continue to want to learn new languages (at least, new to me).

I really appreciate your thoughtful response.

HOWEVER:

when executing the "sudo gem install rails" command, I get the following error:

	ERROR: Failed to build gem native extension.

        /usr/bin/ruby1.9.1 extconf.rb
/usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require': cannot load such file -- mkmf (LoadError)
	from /usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
	from extconf.rb:1:in `<main>'

Could you please shed some light on how I need to proceed with this?

Thanks again.

Rich

---

### Post by Mikeb85 on 2013-01-24
> **rich1939 said:**
> Thank you very much for your reply. Even though I have many years of programming experience, I continue to want to learn new languages (at least, new to me).

I really appreciate your thoughtful response.

HOWEVER:

when executing the "sudo gem install rails" command, I get the following error:

	ERROR: Failed to build gem native extension.

        /usr/bin/ruby1.9.1 extconf.rb
/usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require': cannot load such file -- mkmf (LoadError)
	from /usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
	from extconf.rb:1:in `<main>'

Could you please shed some light on how I need to proceed with this?

Thanks again.

Rich

Make sure you have the -dev package for the Ruby version you have (I believe it's ruby1.9.1-dev) - it's required to build Ruby gems that are written in native code.  

Also make sure you have things like GCC, G++, make, etc...  The usual C development type libraries.  There's a few other random dependencies you'll need after Rails is installed, a Javascript compiler, SQL, etc...  They're all pretty easy to find in synaptic, and if you need an additional Ruby gem, the error message will tell you.

---

### Post by akgulem on 2013-01-28
I advice you to check this link:
[http://blog.sudobits.com/2012/05/02/how-to-install-ruby-on-rails-in-ubuntu-12-04-lts/](http://blog.sudobits.com/2012/05/02/how-to-install-ruby-on-rails-in-ubuntu-12-04-lts/)
Everything is included there.You have two options,you may install everything by just executing script or install everything by hand.I recommend you to watch the video and complete the job.It is so easy :)

---

### Post by rich1939 on 2013-02-01
> **akgulem said:**
> I advice you to check this link:
[http://blog.sudobits.com/2012/05/02/how-to-install-ruby-on-rails-in-ubuntu-12-04-lts/](http://blog.sudobits.com/2012/05/02/how-to-install-ruby-on-rails-in-ubuntu-12-04-lts/)
Everything is included there.You have two options,you may install everything by just executing script or install everything by hand.I recommend you to watch the video and complete the job.It is so easy :)

Sorry for not responding earlier. I got caught up in another issue and haven't been back 'til now. I get a blank page when I click the link you indicated (on Windows). I'll try it with Ubuntu, and thanks for the suggestion.

-Rich

---

### Post by rich1939 on 2013-02-01
> **Mikeb85 said:**
> Make sure you have the -dev package for the Ruby version you have (I believe it's ruby1.9.1-dev) - it's required to build Ruby gems that are written in native code.  

Also make sure you have things like GCC, G++, make, etc...  The usual C development type libraries.  There's a few other random dependencies you'll need after Rails is installed, a Javascript compiler, SQL, etc...  They're all pretty easy to find in synaptic, and if you need an additional Ruby gem, the error message will tell you.

I confess to not being back up to speed on how to get all of the Dev tools & libs. I recall something about ```
sudo apt-get install Devtools
```, or something like that in the past, but I just don't recall. Also, how to get Javascript compiler, SQL, etc. ??

It all seems quite difficult to get going with **Ruby on Rails**.

-rich

---

### Post by Mikeb85 on 2013-02-01
> **rich1939 said:**
> I confess to not being back up to speed on how to get all of the Dev tools & libs. I recall something about ```
sudo apt-get install Devtools
```, or something like that in the past, but I just don't recall. Also, how to get Javascript compiler, SQL, etc. ??

It all seems quite difficult to get going with **Ruby on Rails**.

-rich

Install Synaptic Package manager (sudo apt-get install synaptic), it makes life alot easier - you can simply search for the packages you need without knowing the exact name, and install them from an easy to use GUI.  

Search for 'ruby-dev' and 'sql', and you'll get a bunch of options.  Sqlite3 is the default for rails btw, and I find Node.js (V8) nice for Javascript.  A rubygem called 'therubyracer' interfaces with V8, and the gem 'sqlite3' with Sqlite3 on your system.

---

