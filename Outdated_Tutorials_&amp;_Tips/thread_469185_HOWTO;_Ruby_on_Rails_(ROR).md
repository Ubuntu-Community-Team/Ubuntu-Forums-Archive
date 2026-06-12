---
title: "HOWTO; Ruby on Rails (ROR)"
date: 2007-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Eric_Jardas on 2007-06-09
I know there is already a how to about ruby on rails but there are some things that arent really good and some stuff is missing so here is my version:

**1. What is Rails ?**

Rails is a full-stack framework for developing database-backed web applications according to the Model-View-Control pattern. From the Ajax in the view, to the request and response in the controller, to the domain model wrapping the database, Rails gives you a pure-Ruby development environment. To go live, all you need to add is a database and a web server.

**2. How to Install it on Ubuntu ?**

  **2.1** First we need to install Ruby and irb (Interactive ruby shell) and we'll add ri and rdoc. The recommended Ruby version for rails is 1.8.5.
Open your terminal and type:
```
sudo apt-get install ruby irb ri rdoc ruby1.8-dev
```

  **2.2** Then we need to install RubyGems. In the [[COLOR="Blue"]other howto[/COLOR]]("http://ubuntuforums.org/showthread.php?t=233338") RubyGems is installed from tgz file. It installs RubyGems and thats OK but the problem is when we want to uninstall it. We can't go into synaptic and remove RubyGems thats why we'll do it the other way.
We are going to install RubyGems with the following command:
```
sudo apt-get install rubygems
```

Then we'll update RubyGems with command:
```
sudo gem update --system
```

Now we have the correct version, and best of all when we want to uninstall it we can just do it with synaptic.

  **2.3** Now we will install rails with command:
```
sudo gem install rails --include-dependencies
```

**And we are done !! You have successfully installed Ruby on Rails.**

To create new project type:
```
rails name_of_app
```

** 3.How to uninstall all ?**

To uninstall all I suggest you first remove rails gem:
```
sudo gem uninstall rails
```

and then uninstall rubygems and ruby:
```
sudo apt-get remove rubygems ruby irb ri rdoc ruby1.8-dev
```

I hope you will find this HOWTO useful ! 
Enjoy railing :)

---

### Post by Druke on 2007-07-19
thanks for the quick and easy :popcorn:

thinking about dropping php for this for my future projects , we'll see.

---

### Post by Druke on 2007-12-28
this no longer works, all sources ay compile and install everything yourself for now (debian's install is broked)

---

### Post by biodiesel-bri on 2008-07-19
This blog post indicates that it can be done easier:
[http://www.rubyhead.com/2008/04/25/installing-ruby-rails-on-ubuntu-804-hardy-heron/](http://www.rubyhead.com/2008/04/25/installing-ruby-rails-on-ubuntu-804-hardy-heron/)

It worked for me.

---

### Post by celafon on 2008-07-21
The problem with uninstalling remains...

I was thinking that if rubygems is using /usr/lib/ruby/gems as a package install dir, then maybe it would be possible to create gems admin user, change permissions and see if installing gems would be possible. That would at least ensure there's no mess anywhere outside this dir...

Anyone knows what extra files are copied on the LFS by manual rubygems install + packages (gems) install via rubygems? From what I see rubygems got installed in /usr/local and the packages are being installed to above mentioned ruby package dir...

Is it possible that a package (gem) requests to be installed (via rubygems) in some other place than the package dir? If not -- then I believe it is quite easy to do uninstall manually...

EDIT>

ok, just figured out that gems do contain things that are being installed to the filesystem (e.g. 'passanger' have few files installed in /usr/bin).

so there's probably easier way than the one above. just remove all the packages installed with rubygems using rubygems (it's a package manager, right?). I don't know if there's an option similar to apt's --purge that would ensure ALL files go, but it would be useful here. As for rubygems -- it is in /usr/local, so if it's the only package there, removing is easy...

---

