---
title: "Need help with bundler and ruby!"
date: 2018-02-08
forum: New to Ubuntu
---

### Post by eldarele on 2018-02-08
I'm trying to install Gitlab from source following these steps: [https://docs.gitlab.com/ce/install/installation.html](https://docs.gitlab.com/ce/install/installation.html). I've been following these steps but got stuck on the part where I need to install gems. The bundler requires version 1.5.2 but my bundler is still on 1.16.1. I've tried installing and uninstalling bundler and running bundle install, but this gives me an error. I'm running on Ubuntu 16.04 LTS.

These are the steps that I did to install Ruby:

```
sudo apt-get remove ruby1.8
mkdir /tmp/ruby && cd /tmp/ruby
curl --remote-name --progress [https://cache.ruby-lang.org/pub/ruby/2.3/ruby-2.3.6.tar.gz](https://cache.ruby-lang.org/pub/ruby/2.3/ruby-2.3.6.tar.gz)
echo '4e6a0f828819e15d274ae58485585fc8b7caace0  ruby-2.3.6.tar.gz' | shasum -c - && tar xzf ruby-2.3.6.tar.gz
cd ruby-2.3.6
./configure --disable-install-rdoc
make
sudo make install
```

[FONT=&amp]Then I installed the Bundler Gem:
[/FONT]```
sudo gem install bundler --no-ri --no-rdoc
```

[FONT=&amp]When I run bundle -v the output is: Bundler version 1.16.1

When I try to run the following command from the root directory, I get: Could not locate Gemfile

[/FONT]```
sudo -u git -H bundle install --deployment --without development test mysql aws kerberos
```

[FONT=&amp]When go I into the gitlab directory where I cloned the repository: cd /home/git/gitlab and then run the above command again, It seems to try to install the bundle but then I get the following error, followed by a long list of memory map and other information:
[/FONT]
*** Error in `/usr/local/bin/ruby': munmap_chunk(): invalid pointer: 0x000055c7996a5120 ***

[FONT=&amp]When I type in bundle env, I get the following:
[/FONT]
Bundler       1.16.1
  Platforms   ruby, x86_64-linux
Ruby          2.3.6p384 (2017-12-14 revision 61254) [x86_64-linux]
  Full Path   /usr/local/bin/ruby
  Config Dir  /usr/local/etc
RubyGems      2.5.2.2
  Gem Home    /usr/local/lib/ruby/gems/2.3.0
  Gem Path    /home/eldarele/.gem/ruby/2.3.0:/usr/local/lib/ruby/gems/2.3.0
  User Path   /home/eldarele/.gem/ruby/2.3.0
  Bin Dir     /usr/local/bin
Tools
  Git         2.14.3
  RVM         not installed
  rbenv       not installed
  chruby      not installed
[FONT=&amp]
I have no clue if these paths are correct or if this environment is correct. [/FONT][FONT=&amp]Could anyone please help me?[/FONT]

---

### Post by TheFu on 2018-02-08
Don't touch the system versions of tools like ruby. It will break system tools.

Use rbenv or rvm to manage the specific ruby setups you need.  Each ruby version would have their own libraries, gems, bundler, and webapps.

Plus, this way, you don't need to use sudo for anything, which is much more secure.

Also, v1.16.1 is newer than v1.5.x.

---

### Post by eldarele on 2018-02-08
Oh I didn't know that v1.16.1 was newer than v1.5.2. Thank you for the info! So how should I solve this? Should I remove ruby entirely? Because it seems ruby is installed all over the place, so I have no idea where to start. And what are the steps I should take to setup ruby correctly? Would you recommend rbenv or rvm?

---

### Post by TheFu on 2018-02-08
You should restore from the backup you did prior to screwing around that puts the system ruby back and all libraries that might have been modified as a result.  If you don't have a backup (bad programmer!!!!), then attempting to reverse the commands that altered the package management would be the next thing.  Appears the ruby you pulled the source for installed into /usr/local/bin/ - which is fine and shouldn't impact the system ruby, unless you changed environment variables for system accounts to find /usr/local/bin before the system ruby.

Then you should pick a ruby environment management tool. I've only used rvm and it has been a few years. I learned in a free ruby-on-rails class put on by the local Ruby meetup group here.  They are very active and have many sessions monthly.  Back when I learned, it was 3 hrs every Saturday morning for 6 months using a book that had step-by-step instructions for using rvm, rails, ruby, TDD, lead by a professional team of rubyists.  They posted videos online so people who didn't make the meetings could catch up by watching.  Sadly, ruby versions change too much every 2 yrs to make those videos or the book good enough for today.  When first learning, exactly, correct, instructions are important.  Those videos would only be close, but there will definitely be problems as ruby, rails and the build tools have moved forward.  

BTW, getting a ruby environment working took 2 sessions for most people.  That was because they came from Windows and were learning Linux at the same time.  The people using Macs had it easier in the beginning because the core ruby people are extremely Mac-centric.  I've never seen a Mac production environment, just sayin'.

Sorry. I'm not any more help.

---

### Post by eldarele on 2018-02-08
Unfortunately I don't have a backup. As far as I know I didn't change any environment variables for ruby. I'm going to try to follow the steps in trying to install ruby with RVM and see how that goes. I hope this doesn't conflict with my Gitlab installation. Because Gitlab is cloned under a git user which was created with --disable-login, while I'm signed in with a user that has sudo rights. How would I install ruby for my git user? Because RVM will install for each user right?

 I am coming from a Windows environment, so I'm jumping right into the deep setting up a Ubuntu server with Gitlab with no previous linux experience. I only need ruby to setup Gitlab, I'm not planning on developing for ruby. And you have been a great help! Any help is welcome.

Edit: I've installed RVM for multi-users adding both the git and my user to the rvm group, so that all users will have access to ruby and I have installed ruby 2.3.6. It seems when I try to run bundle install in my Gitlab repository I get the following:

<internal:gem_prelude>:4:in `require': cannot load such file -- rubygems.rb (LoadError)
        from <internal:gem_prelude>:4:in `<internal:gem_prelude>'

Do you know what might be the problem?

---

### Post by TheFu on 2018-02-08
Sorry.  I assumed your were doing ruby development. 

[https://docs.gitlab.com/ce/install/installation.html](https://docs.gitlab.com/ce/install/installation.html) shows that setting this stuff up is non-trivial, especially for someone new to Linux.  Learning linux, coming from a non-Unix background, is very hard.  The instructions from gitlab specifically say that using rvm/rbenv aren't supported, so that was bad advice I gave.  Sorry.
> 
The use of Ruby version managers such as RVM, rbenv or chruby with GitLab in production, frequently leads to hard to diagnose problems. For example, GitLab Shell is called from OpenSSH, and having a version manager can prevent pushing and pulling over SSH. Version managers are not supported and we strongly advise everyone to follow the instructions below to use a system Ruby.

---

