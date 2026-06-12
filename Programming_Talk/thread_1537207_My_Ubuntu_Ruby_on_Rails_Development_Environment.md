---
title: "My Ubuntu Ruby on Rails Development Environment"
date: 2010-07-23
forum: Programming Talk
---

### Post by trivialpackets on 2010-07-23
I wanted to post this to get any advice on more things that would be useful, either as configuration settings, or to help someone else who is getting set up initially.  Any feedback is always welcome.

**Setting Up Rails Development Environment**

**Install Ubuntu 10.04**
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install ubuntu-restricted-extras ruby irb ri rdoc ruby1.8-dev libzlib-ruby libyaml-ruby libreadline-ruby libncurses-ruby libcurses-ruby libruby libruby-extras libfcgi-ruby1.8 build-essential libopenssl-ruby libdbm-ruby libdbi-ruby libdbd-sqlite3-ruby sqlite3 libsqlite3-dev libsqlite3-ruby libxml-ruby libxml2-dev ufw gedit-plugins git-core vim-gnome vim-rails workrave libnotify-bin

sudo ufw enable
sudo ufw default deny
```

**Download latest ruby gems and setup (as of 7/23/2010).**
```
wget http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz
tar –zxvf rubygems-1.3.7.tgz
cd rubygems-1.3.7
sudo ruby setup.rb
cd ..
rm –rf ruby-1.3.7*

sudo gem install rails mongrel rspec rspec-rails heroku autotest-rails redgreen
```

**CONFIGURING & USING AUTOTEST**
Create a file located in your home directory called .autotest
CONTENT:

```
#!/bin/ruby
require 'redgreen'
require 'autotest/timestamp'
 
module Autotest::GnomeNotify
  def self.notify title, msg, img
    system "notify-send '#{title}' '#{msg}' -i #{img} -t 3000"
  end
 
  Autotest.add_hook :ran_command do |at|
    image_root = "~/.autotest_images"
    results = [at.results].flatten.join("\n")
    results.gsub!(/\\e\[\d+m/,'')
    output = results.slice(/(\d+)\sexamples?,\s(\d+)\sfailures?/)
    puts output.inspect
    if output
      if $~[2].to_i > 0
        notify "FAIL", "#{output}", "#{image_root}/fail.png"
      else
        notify "Pass", "#{output}", "#{image_root}/pass.png"
      end
    end
  end 
end
```

Create directory in home folder called .autotest_images
put the attached pictures into that folder.

To use autotest, open a terminal window and navigate to the project root directory and type:

```
autospec
```
(autotest setup courtesy of: [http://automate-everything.com/lang/en/2009/08/gnome-and-autospec-notifications/](http://automate-everything.com/lang/en/2009/08/gnome-and-autospec-notifications/))

**OPTIONAL STEPS**
IF NEEDED (not needed for most development)
```
sudo apt-get install mysql-server mysql-client libdbd-mysql-ruby libmysqlclient-dev phpmyadmin
sudo gem install mysql
```

Install the following Firefox AddOns:
SQLite Manager
Adblock Plus
FireFTP
Total Validator
Firebug
Web Developer

**OPTIONAL APPLICATIONS**
Download netbeans & install
Download geany & install
Download komodo-edit & install 

```
cd ~/Pictures
wget http://www.startonrails.fr/wp-content/uploads/2009/08/ruby-on-rails1.jpg
wget http://capslog-informatique.fr/site_virtualrails//themes/magazeen/images/wallpaper_virtual_rails.jpg
```

Set your wallpaper and go to town!  (Wallpaper is obviously optional!  ;))

---

### Post by purvez on 2010-07-24
Hi Eric

Wow this is really fortunate as I'm about to start using Ruby on Rails on Ubuntu and your post gives me exactly what I need without all of the research!!  Please may I ask which version of Ubuntu you are using e.g. Desktop, Netbook or Server?  I plan to develop on my laptop and am unsure whether to load Desktop or Server?

Your guidance would be gratefully appreciated.

Thanks in advance.

Purvez Desai

---

### Post by trivialpackets on 2010-07-24
No reason to use anything other than desktop in my opinion.  I go further to enable mp3 and music and dvd's as my laptop has many uses.  When developing rails, you really don't need a server.  You can use the built in server for testing, and then when you want to test your code on other browsers, ie Internet Explorer, that's when Heroku comes in handy.

---

### Post by jryanitpro on 2010-08-10
Hello Eric

I was wondering if you happened to try Rails3 and Ruby 1.9.2 on Ubuntu 10.04. I tried to setup autotest as you have noted and I followed the link you provided but it seems this doesn't work with newer Rails/Ruby and different gems that I'm using.

The reason I am trying to setup with these versions is because I'm following the railstutorial.org/book and unfortunately most tutorials use Mac as the default environment and then basically we are stuck chasing down blog posts and such to try and get things working on ubuntu.

I really want to be able to have this stuff work because Ruby seems to be an awesome language that seems to fit my brain better then Python but it sucks feeling like Linux is a second class development environment in the newer Rails world. Rails seems to be a good way to get me programming in Ruby, real projects anyway. Not to mention I've had better luck understanding Rails architecture compared to my learning experiences with Django. Which I'll admit has more to do with the programming language then the framework itself.

Thanks for anything you can add

Joe Ryan
[http://joehacker72.wordpress.com](http://joehacker72.wordpress.com)

---

### Post by newb85 on 2010-11-02
> **jryanitpro said:**
> Hello Eric

I was wondering if you happened to try Rails3 and Ruby 1.9.2 on Ubuntu 10.04. I tried to setup autotest as you have noted and I followed the link you provided but it seems this doesn't work with newer Rails/Ruby and different gems that I'm using.


You need to "gem install test-unit".

> **jryanitpro said:**
> 
it sucks feeling like Linux is a second class development environment in the newer Rails world. 

AGREED!  If tutorials for Rails were as flexible and inclusive as those on the Django project website (i.e., versions for different versions of rails, complete instructions for each OS) that would be sweet.  Instead, most rails documentation reeks of the standard Mac elitism.  I do have to give Hartl props, though, for admitting that his tutorial is specifically written for Mac, and not assuming out-of-hand that everyone is using Mac.

---

### Post by newb85 on 2010-11-02
Well, I have autotest working...kind of.

It runs, and whenever I modify something in app/controllers/, it runs the tests in spec/.  However, when I modify something in app/views/, it only updates the timestamp ("# Waiting since...") and doesn't run the tests.  When I modify config/routes.rb, it doesn't even update the timestamp.

I can CTRL+C in the terminal running autotest, and that forces it to run the tests, but that kind of defeats the purpose.

Does anyone have suggestions on what could be failing?

---

### Post by trivialpackets on 2010-11-21
I thought the rails tutorial was pretty good, and I thought, this worked out ok with the railstutorial instructions.  Are you using the same Gemfile settings that are included in the railtutorial?

---

### Post by techrush on 2010-11-22
I too have noticed how Mac centric the Rails community seems to be. Good to see there is at least a small community of people using Linux for Rails dev. 

When I start exploring Ruby and Rails more I'll come back to this post for sure as it seems like a great resource. This type of workflow and requirement information is great to have when starting on a new framework or environment.

---

### Post by coldspring on 2011-01-24
This is only thread I found when searching the forum of GnomeNotify; I hope the ROR set up question is not too specific....


I am following the RoR Hartle tutorial and have reached the section on  setting up autotest notification when run into a problem.  In need to setup GnomeNotify such that a notify-send is sent to a client machine when a notification is generated on a server.

  I chose to set up my RoR development environment on Ubuntu 10.10 Server that does not have an X environment installed.  I did this for three reasons: 1) The server is in an equipment closest and not cluttering up my office, 2) The server is very old and I do not want a GUI eating up the limited resources of the machine, 3) I do not want to install a development environment on my office machine and run the risk of screwing up my main machines settings. 

When the tutorial calls for a GUI I just "ssh -X user@server application" into the server and use the X environment of office machine as a client for the Server. I do a direct ssh to the server for terminal commands.  

**[SIZE="3"]I would like to configure autotest  running on the server so that it sends a remote notification to GnomeNotifhy on my office laptop.[/SIZE]**

Any advice on how to achieve this would be appreciated!

---

### Post by trivialpackets on 2011-02-25
I wish I knew, but I'm not sure.  Sorry.  I tend to do my development work in one place, which is normally in a virtualbox.  If you've got the resources, then I would recommend it, otherwise, I'm not sure about passing the GnomeNotify from the server to your laptop.  Sorry.

In this case, I would probably just recommend having another ssh connection to your machine and running autotest on it and watching for the responses.  That's normally what I do when I'm ssh'd into my VM.

---

