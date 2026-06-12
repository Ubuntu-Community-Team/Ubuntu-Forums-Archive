---
title: "HOWTO: Install Ruby On Rails For Your Ubuntu Box"
date: 2006-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by gorilla_king on 2006-08-10
**PriceChild: I suggest you follow [http://ubuntuforums.org/showthread.php?t=469185](http://ubuntuforums.org/showthread.php?t=469185) for several benefits explained in the thread.**

This is a easy and simplified way to install [ruby on rails]("http://rubyonrails.org/") to your ubuntu system.
I promise even though this looks really long, it's not, i just broke everything up so maybe, some weird change (considernig i didn't explain myself) someone will learn from this. At the end of this post i add some great tutorial links for the road after the install, and i also added the entire code required to do this into a box by itself.
Let's stop all the talk and get started....

Open a terminal and type
```
sudo apt-get install ruby1.8 ruby1.8-dev irb
```That was to install ruby it's self

Next let's install sqlite3
```
sudo apt-get install sqlite3
```You can also use just about any other database

Now lets get our rubygems tgz
```
wget http://rubyforge.org/frs/download.php/5207/rubygems-0.8.11.tgz
```of course we need to etract it
```
tar -zxvf rubygems-0.8.11.tgz
```now we have to cd to it
```
cd rubygems-0.8.11
```lets run the setup and save us many hours of work
```
sudo ruby ./setup.rb
```It seems based on some systems we need to go to the home dir before we do the next step so go
```
cd
```since we already installed ruby, we need to install rails or else it wouldn't be ruby on rails
```
sudo gem install rails --include-dependencies
```Now everything should be installed and setup if we didn't have any errors

Lets create a test app to see if it was a success
```
rails my_app_test
```we need to cd into that directory
```
cd my_app_test
```now we need to start the server
```
ruby script/server
```Now go to your browser of choice and go to [http://localhost:3000](http://localhost:3000) and see if you get a page saying your riding the rails. If so then you can continue to write your code and create an awesome app. 

Leave a comment if there are any problems.


In summary your doing this
```
sudo apt-get install ruby1.8 ruby1.8-dev irb
sudo apt-get install sqlite3
wget http://rubyforge.org/frs/download.php/5207/rubygems-0.8.11.tgz
tar -zxvf rubygems-0.8.11.tgz
cd rubygems-0.8.11
sudo ruby setup.rb
sudo gem install rails --include-dependencies
rails my_app_test
cd my_app_test
ruby script/server
```After you successfully install it and want to know the basics and beginnings on ruby then i suggest these tutorials
[A Video on How to create blog in 15 minutes]("http://media.rubyonrails.org/video/rails_take2_with_sound.mov") (very basic, good beginner stuff)
[Creating test apps so you can test]("http://www.onlamp.com/pub/a/onlamp/2005/01/20/rails.html") (very basic, great beginner stuff, ignore the install and the windows stuff, and jump to creating apps.)

Well, i hope this helps someone out there.

If you have any problems, of course post here, or if you need immediate help you can contact me on aim at iplayguitar214

I included soem screenshots so you would see what the page would look like after install and you navigate to, localhost:3000 and the other one is it working with the test hello world :cool:

---

### Post by exaulz on 2006-08-10
Very nice tutorial. Extremely helpful!

---

### Post by srb715 on 2006-08-10
Everything's fine up until the part where you try to run the setup.rb file.  At that point it says:

```
sudo: ruby: command not found
```

Could you give me some direction from here?

Following the install procedure of another site, I ran this and it worked.

```
sudo apt-get install ruby ri rdoc mysql-server libmysql-ruby 
```

Heh, the next step also gave me a problem.

```
matt@matt-desktop:~/rubygems-0.8.11$ sudo gem install rails --include-dependencies
Attempting local installation of 'rails'
Local gem file not found: rails*.gem
Attempting remote installation of 'rails'
ERROR:  While executing gem ... (OpenURI::HTTPError)
    404 Not Found

```

---

### Post by gorilla_king on 2006-08-10
> **srb715 said:**
> Everything's fine up until the part where you try to run the setup.rb file.  At that point it says:

```
sudo: ruby: command not found
```

Could you give me some direction from here?
Well, try running sudo ruby ./setup.rb
(i had that same problem originally, and i forgot about it)
> **srb715 said:**
> 
Heh, the next step also gave me a problem.

```
matt@matt-desktop:~/rubygems-0.8.11$ sudo gem install rails --include-dependencies
Attempting local installation of 'rails'
Local gem file not found: rails*.gem
Attempting remote installation of 'rails'
ERROR:  While executing gem ... (OpenURI::HTTPError)
    404 Not Found

```
I'm pretty sure this happened because you didn't do the ruby setup.rb file before. So try the setup.rb file (like i said above) and then run this again and you should have it working. Let me know though.

---

### Post by srb715 on 2006-08-10
Still a no-go.

```
matt@matt-desktop:~/rubygems-0.8.11$ sudo ruby ./setup.rb
Password:
---> bin
<--- bin
---> lib
---> lib/rubygems
<--- lib/rubygems
<--- lib
---> bin
<--- bin
---> lib
---> lib/rubygems
<--- lib/rubygems
<--- lib
rm -f InstalledFiles
---> bin
mkdir -p /usr/bin/
install gemwhich /usr/bin/
install gem /usr/bin/
install gem_server /usr/bin/
install generate_yaml_index.rb /usr/bin/
install update_rubygems /usr/bin/
install gem_mirror /usr/bin/
<--- bin
---> lib
mkdir -p /usr/local/lib/site_ruby/1.8/
install ubygems.rb /usr/local/lib/site_ruby/1.8/
install rubygems.rb /usr/local/lib/site_ruby/1.8/
install gemconfigure.rb /usr/local/lib/site_ruby/1.8/
---> lib/rubygems
mkdir -p /usr/local/lib/site_ruby/1.8/rubygems
install specification.rb /usr/local/lib/site_ruby/1.8/rubygems
install builder.rb /usr/local/lib/site_ruby/1.8/rubygems
install command.rb /usr/local/lib/site_ruby/1.8/rubygems
install config_file.rb /usr/local/lib/site_ruby/1.8/rubygems
install custom_require.rb /usr/local/lib/site_ruby/1.8/rubygems
install doc_manager.rb /usr/local/lib/site_ruby/1.8/rubygems
install format.rb /usr/local/lib/site_ruby/1.8/rubygems
install cmd_manager.rb /usr/local/lib/site_ruby/1.8/rubygems
install gem_runner.rb /usr/local/lib/site_ruby/1.8/rubygems
install installer.rb /usr/local/lib/site_ruby/1.8/rubygems
install loadpath_manager.rb /usr/local/lib/site_ruby/1.8/rubygems
install old_format.rb /usr/local/lib/site_ruby/1.8/rubygems
install open-uri.rb /usr/local/lib/site_ruby/1.8/rubygems
install package.rb /usr/local/lib/site_ruby/1.8/rubygems
install remote_installer.rb /usr/local/lib/site_ruby/1.8/rubygems
install rubygems_version.rb /usr/local/lib/site_ruby/1.8/rubygems
install source_index.rb /usr/local/lib/site_ruby/1.8/rubygems
install deployment.rb /usr/local/lib/site_ruby/1.8/rubygems
install timer.rb /usr/local/lib/site_ruby/1.8/rubygems
install user_interaction.rb /usr/local/lib/site_ruby/1.8/rubygems
install validator.rb /usr/local/lib/site_ruby/1.8/rubygems
install version.rb /usr/local/lib/site_ruby/1.8/rubygems
install gem_commands.rb /usr/local/lib/site_ruby/1.8/rubygems
install dependency_list.rb /usr/local/lib/site_ruby/1.8/rubygems
install security.rb /usr/local/lib/site_ruby/1.8/rubygems
install gem_openssl.rb /usr/local/lib/site_ruby/1.8/rubygems
<--- lib/rubygems
<--- lib

As of RubyGems 0.8.0, library stubs are no longer needed.
Searching $LOAD_PATH for stubs to optionally delete (may take a while)...
...done.
No library stubs found.

  Successfully built RubyGem
  Name: sources
  Version: 0.0.1
  File: sources-0.0.1.gem
matt@matt-desktop:~/rubygems-0.8.11$ sudo gem install rails --include-dependencies
Attempting local installation of 'rails'
Local gem file not found: rails*.gem
Attempting remote installation of 'rails'
Updating Gem source index for: http://gems.rubyforge.org
ERROR:  While executing gem ... (OpenURI::HTTPError)
    404 Not Found

```

---

### Post by gorilla_king on 2006-08-10
well, ok, so i fixed the setup.rb problem. Now on the the install rails issue.

I tried to replicate the problem you were having and it wasn't to much success, it just wouldn't not work for me, but i did get this error 
```
thomas@joey:~$ sudo gem install rails --include-dependencies
Attempting local installation of 'rails'
Local gem file not found: rails*.gem
Attempting remote installation of 'rails'
```
But after that it just went into the normal install and was fine.

So cd into your home directory
```
cd
```

then try it again
```
sudo gem install rails --include-dependencies
```
If it gives you there error i posted above then just ignor it, and it will probably stop after the error for like five minutes, just go get some lunch or something and let it sit, it took me nearly ten minutes to reinstall it for somereason. If that doesn't work then let me know, but here is my terminal after i tried to install it.
```
thomas@joey:~$ sudo gem install rails --include-dependencies
Attempting local installation of 'rails'
Local gem file not found: rails*.gem
Attempting remote installation of 'rails'
Successfully installed rails-1.1.6
Successfully installed activerecord-1.14.4
Successfully installed actionpack-1.12.5
Successfully installed actionmailer-1.2.5
Successfully installed actionwebservice-1.1.6
Installing RDoc documentation for activerecord-1.14.4...
Installing RDoc documentation for actionpack-1.12.5...
Installing RDoc documentation for actionmailer-1.2.5...
Installing RDoc documentation for actionwebservice-1.1.6...
thomas@joey:~$
```

---

### Post by srb715 on 2006-08-10
Running that from the parent directory worked.  Thanks a lot, and sorry for being slow.

---

### Post by gorilla_king on 2006-08-10
> **srb715 said:**
> Running that from the parent directory worked.  Thanks a lot, and sorry for being slow.
oh, its no problem at all, i'll update my guide, thanks you for helping me figure out the problem.

---

### Post by Ali_Taimur on 2006-08-10
:cool: :cool: 
thank you so much. i was looking for this for dayss:KS :KS

---

### Post by gorilla_king on 2006-08-11
> **Ali_Taimur said:**
> :cool: :cool: 
thank you so much. i was looking for this for dayss:KS :KS
no problem, i'm glad it helped.

---

### Post by Burgresso on 2006-08-15
Great howto...but some questions:

How do you stop the Ruby server from running ROR?
What if you want to work in a different ROR application than the one you where working on?
How do I "start" the Ruby server so I can work on app again?

Again, great tutorial, made it easy to set up ROR!

---

### Post by Opally on 2006-08-18
Hello!

I'm a raw newbie, but very excited about Ubuntu. My goal is to set up an Ubuntu server where I can do RoR development.

I have gotten as far as downloading and extracting rubygems-0.9.0. I'm using Ubuntu 6.06 "LAMP" on a .386 machine (it installed beautifully.) I have Kubuntu desktop installed, too.

However, I can't run setup.rb because... ruby has no interpreter.

When I run 
```
sudo ruby ./setup.rb
```
I get 
```
sudo: ruby: command not found
```

Also, I'm wondering whether I will be able to determine that Ruby should be available to all users on the computer. Right now the setup files are sitting in my user directory, that's probably not the right place for the installation.

I did ```
sudo apt-get install ruby rdoc1.8 irb libyam1-ruby libzlib-ruby
``` but this returns
```
Reading package lists ... Done
Building a dependency tree ... Done
Package rdoc1.8 is not available but is referred to by another package...
E: Package rdoc1.8 has no installation candidate
```

thanks in advance!!!

---

### Post by Opally on 2006-08-18
Ah...

I think I did it.

```
sudo apt-get install ruby
```

without all the rdoc1.8 stuff worked.

And then, at last, ```
sudo ruby ./setup.rb
``` worked, per your instruction above.

And I got Rails.

Now I need to haunt the newbie forums some more, to understand the file system better.

---

### Post by gorilla_king on 2006-08-18
wonderful  i'm glad you got it working, and for multiple users to use it, i'd suggest you move all fils into a root owndership dir, like /usr/bin or /opt/
it's all up to you and where you really want it to run, because with a root password it can be installed and run from anywhere.

---

### Post by jallen7usa on 2006-08-21
Thanks for this!  I had to do a fresh OS install and wasn't looking forward to re-installing Rails (last time was painful for some reason).

I to had to run:
```
sudo apt-get install ruby
```

You may want to consider adding that to your tutorial.  

Also, for newbies that are used to developing in an IDE, I'd like to suggest [RadRails](http://www.radrails.org/).

---

### Post by hirotani on 2006-10-19
great tutorial, worked just as set out.  many thanks.

---

### Post by dpcamp on 2007-05-31
When I run this:
```
ruby script/server
```
I get this
```
./script/../config/boot.rb:29: undefined method `gem' for main:Object (NoMethodError)
        from script/server:2:in `require'
        from script/server:2

```

---

### Post by Eric_Jardas on 2007-06-09
@Burgresso: you stop server by pressing** CTRL+C**

@dpcamp: try updating RubyGems with:
```
 sudo gem update --system
```

---

### Post by vvangelovski on 2007-08-03
Thanx!
Spent the whole night trying to figure this out. My problem was the same as dpcamp's. Updating gems solves it.

---

### Post by qnub on 2008-11-30
> sudo gem update --system
in my system (Ubuntu server 8.10 amd64) say:
```
ERROR:  While executing gem ... (RuntimeError)
    gem update --system is disabled on Debian. RubyGems can be updated using the official Debian repositories by aptitude or apt-get.
```

---

