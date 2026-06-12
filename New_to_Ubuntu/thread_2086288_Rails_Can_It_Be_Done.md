---
title: "Rails: Can It Be Done?"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by bsalman on 2012-11-20
Hello Everyone,

I've just installed Ubuntu server 12.04 LTS for my first time, and it's my first experience with Linux.  For the most part, I'm enjoying it!  However, I'm having lots of trouble getting Ruby on Rails installed.  I've tried things like:

```
sudo apt-get install rails
```

which results in:

```
E: unable to locate package rails
```

I've looked in many places on the internet and have tried installing it via gems, rake, I've even tried yum just for the hell of it, and nothing works.  

And, I've done:

```
sudo apt-get update
```

Which returns:

```
Ign cdrom://Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise InRelease
Ign cdrom://Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main TranslationIndex
Ign cdrom://Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted TranslationIndex
Ign cdrom://Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main Translation-en_US
Ign cdrom://Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main Translation-en
Ign cdrom://Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted Translation-en_US
Ign cdrom://Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted Translation-en
```

If anyone has any help they can offer, I'd really appreciate it!

---

### Post by Tony Flury on 2012-11-20
[https://www.digitalocean.com/community/articles/how-to-install-ruby-on-rails-on-ubuntu-12-04-lts-precise-pangolin-with-rvm](https://www.digitalocean.com/community/articles/how-to-install-ruby-on-rails-on-ubuntu-12-04-lts-precise-pangolin-with-rvm)

Have you tried that

I used Google "Ruby on Rails Ubuntu" to find that one.

Anothe tutorial which might be useful : [http://coding.smashingmagazine.com/2011/06/21/set-up-an-ubuntu-local-development-machine-for-ruby-on-rails/](http://coding.smashingmagazine.com/2011/06/21/set-up-an-ubuntu-local-development-machine-for-ruby-on-rails/)

Which is about setting up a development environment.


P.S. The output you got from 
```

sudo apt-get update

```

Is exactly what i would expect - what it does is fetch the new package list from every repository - and the output is a list of all the repositories it got package lists from.

---

### Post by TheFu on 2012-11-20
Any software development environment should not be installed using apt-get or Synaptic or software center. You need to use the preferred method for the specific tool(s) involved.

For Ruby and Rails, that tool is **rvm**.  At the ruby group in my area, they used this "Gist" [https://gist.github.com/cajun-code](https://gist.github.com/cajun-code) to teach Ubuntu users how to install Ruby and Rails.  The entire "setup development environment" presentation covers Windows, OSX and Linux - most rubiest appear to use OSX for some reason.  Just to set your expectations, in a class of 20 people, 15 are using OSX.  2 or so use Linux and the other 3 are fighting to use Windows.

Here's a blog article [http://blog.jdpfu.com/2012/07/18/ruby-on-rails-environment-on-ubuntu-12-04](http://blog.jdpfu.com/2012/07/18/ruby-on-rails-environment-on-ubuntu-12-04)  on setting up a RoR dev environment on Ubuntu 12.04 that I wrote. I hope it helps someone.

So, you want to use **rvm **and **gem** to manage as much of your Ruby development environment as possible. This will prevent OS-Ruby dependency issues. For example, the ruby version needed for puppet will be different from what you probably want to run on your RoR environments or for development.  Avoid using the OS specific tools whenever possible.

This goes for Perl too. In perl, you want to use PerlBrew to maintain different perl installs outside the OS control.

Using these tools is a **best practice **for many good reasons.

---

### Post by slickymaster on 2012-11-20
Check out this tutorial:

[How to Install Ruby on Rails on Ubuntu 12.04 LTS (Precise Pangolin) with RVM]("https://www.digitalocean.com/community/articles/how-to-install-ruby-on-rails-on-ubuntu-12-04-lts-precise-pangolin-with-rvm")

---

### Post by bsalman on 2012-11-20
Hi All,

Thanks so much for your help!  I'll check out RVM and install it that way.  I appreciate it :)

---

