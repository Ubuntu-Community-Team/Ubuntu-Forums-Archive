---
title: "which ruby/rails ?"
date: 2008-01-10
forum: Programming Talk
---

### Post by stairwayoflight on 2008-01-10
Hello,

I've started fussing with ROR recently. I went purely with ubuntu packes for ruby (ruby-full I believe) but installed ruby gems from the last stable download on the web, and rails from ruby gems. I ran into an issue (on rails > 2.0) with a "nomethoderror" for the scaffold method called in my application controller file, so I'm reinstalling partially to rule out a dependency/incompatibility issue.

Here is my question, expressed in the general sense:

When working with a given language, and libraries and dependencies and such, when is it appropriate to use the latest snapshots, latest stable releases from product teams, etc, and when is it appropriate to use the packages in the repos?

Specifically with Ruby, many libs are installed via rubygems. Is it good to mix and match them with stuff from the repos, or if one is going to use rubygems to install software is it best to let rubygems install everything?

I know the obvious thing is to make sure dep's aren't broken, eg. rails wants ruby 1.8.6 but not 1.8.2, etc. I have read various opinions either way. For some lang's some say if you have a problem people will simply tell you to reproduce it with the latest stable release anyways, so you might as well have it from the start.

Is this also true of debian/ubuntu developers, or are there generally enough people using using eg. the repo rails version to get help from ?

Stwy

---

### Post by achron on 2008-01-10
I just went the route of apt-get for most of my components loading RoR onto an Ubuntu 7.10 Server install.

Gems/Rails went pretty easily, along the lines of:

sudo apt-get install ruby   (got the 1.8.6 version)
sudo apt-get install ri
sudo apt-get install rdoc
sudo apt-get install libmysql-ruby
sudo wget [http://rubyforge.org/frs/download.php/20989/rubygems-0.9.4.tgz](http://rubyforge.org/frs/download.php/20989/rubygems-0.9.4.tgz)
tar -xvzf rubygems-0.9.4
cd rubygems-0.9.4
sudo ruby setup.rb
sudo gem update
sudo gem install rails --include-dependencies

Whenever I look at loading a component/widget, I'll first refer to the source to see if they mention any issues among versions, but its generally just apt-get, or wget from rubyforge.

---

### Post by stairwayoflight on 2008-01-10
Thanks for the advice. It still seems a little ambiguous to me, so you will always install the repo version, unless there is a conflict mentioned between the versions of ubuntu packages?

On another note, (in a minor key) I have apparently borked my ruby installation. I had packages originally, uninstalled everything, then installed sources but after unpacking the ruby tarball it wouldn't install. I did the './configure && make && make install' and it failed, something about zlib not found. I tried compiling that seperately but it didn't seem to work. So I decided to delete everything and go back to packages for ruby, then the tarballed ruby gems and use ruby gems to install from there.

Things didn't go well. I ran into problems again. I uninstalled ruby, rdoc, ri, irb, ruby-dev, and ruby* from synaptic, then deleted all files I found in /usr/bin, /usr/lib, etc., and started over (same install process).

Ok, the $2 million question: "How do I delete everything left over from my ruby and gems installation?" I believe that is the source of my problems, maybe its not but at least I can start fresh and eliminate that possibility.

---

### Post by achron on 2008-01-11
Well, the ambiguous nature of the response comes from a combination of a mix of: 1) relatively new to Linux/Ubuntu, 2) relatively new to Ruby/Rails, 3) cautious nature. 

Being an old dog at development, I have wasted far too much time in the past bandaging due to that bleeding edge effect. 

I just want my tools to work, so I can get on with what I want to do, hence I do try to stay more mainstream and stick to repositories. Someone else, hopefully more knowledgeable than I, should have packaged and tested the contents before it makes it to the repo.

I also do try to research anything that isn't mainstream before planning to use it in my apps.  I also use imagemagick, filecolumn, and pdfwriter in my RoR application., and I'm trying to get mongrel_cluster and Apache to behave on my server.

Hopefully what I've said is somehow useful to you... but I won't say "Do this, or do that," because the one thing I do know is how much I don't know...

---

### Post by stairwayoflight on 2008-01-11
Ahh,

Well thank you for your thoughts. I went through and deleted everything I could find (find /usr/ iname 'ruby' etc) and reinstalled following your idea pretty much and it seems things are working.

I had a number of errors that came up, the last one being a NoMethodError for method 'scaffold' of my controller class in a rails project. It took a little while for me to figure out this wasn't another manifestation of daemons chewing on the wires somewhere but a result of dynamic scaffolding having been removed from rails!

I see a number of people have installed ruby from packages and gems from source, its what I ended up doing and its working so far.

:guitar:

EDIT: **problem with scaffolding solved, see [http://ubuntuforums.org/showpost.php?p=4286963&postcount=11]("http://ubuntuforums.org/showpost.php?p=4286963&postcount=11")**

---

### Post by Tillmo on 2008-01-14
Hi,

on [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails), it is recommended to install gem 1.0.1 from the sources. Is there a reason why you recommend 0.94 instead?

---

### Post by achron on 2008-01-29
Sorry, been away a bit.  When I started Rails development on my XP machine, 0.94 was what was out.

When going to Ubuntu, I stuck with the same revs of components on both machines to eliminate potential issues. I find it always better to stick with known entities when possible.  You know, alter only 1 parameter at a time.  Windows to Linux was a big enough change.

Now working on upgrading to Rails 2.0.2, and the bug/compatibility demons are out in full force.  Hasn't been very "RESTful" development yet...

UPDATE:

So I updated RubyGems to 1.0.1 (rubyforge.org/frs/download.php/29548/rubygems-1.0.1)

Loads okay, then try a "gem update"
Okay, gem is hosed...

Scrounge on the web, then find that in the /usr/bin/gem file, you need to add a require for a new component gem_runner, so right after the existing line requiring rubygems, you need to add another for gem_runner

require 'rubygems'
require 'rubygems/gem_runner'

Since I'm updating all over the place anyway, I updated rake to version 0.8.1

sudo gem install rake

Redid the Rails update to 2.0.2

sudo gem install rails --include-dependencies

Generated a new rails app to run parallel my existing rails app
edited the database.yml, and ran my initial rake task

Doh! file not found...

More web scrounging, and saw that I next needed to add libopenssl for ruby after getting barked at when trying to run my initial rake db:migrate

sudo apt-get install libopenssl-ruby1.8

Then a "rake db:migrate" and we seem to be on level ground again...

Checked in MySQL and there is the ever-present 'schema-info' table... cool.

Now to port up to Rails 2.0.2 (I'm also moving to attachment_fu, so I was going to have alot of rewrite anyhow).  I'm going to collapse all my previous revisions of migrations for a table into a single instance, and point 2.0.2 at the same database as 1.2.6, so I can bootstrap my spiffy new 2.0.2 app at the same time my other users are running the old app. With record ownership in place, we shouldn't have any data collisions.

---

### Post by Goliath! on 2008-01-29
I am just starting with Ruby and I'm trying to figure out how to install Mongrel.

All the instructions I find say to install it using gems.

However, I also find lots of warnings that say gems is bad because it can hose the dependencies used by apt-get.

So my questions are:

1. Is it really safe to use gems?

2. How can install Mongrel not using gems?

Thanks for your thoughts.

---

### Post by achron on 2008-01-30
For the layman (which is definitely me), I used the simple 

sudo gem install mongrel --include-dependencies

chose the mongrel for ruby (1.1.1 at the time), and fastthread for ruby (1.0.1) and haven't had any issues.

I also loaded mongrel_cluster via gem if I recall correctly (can't find my notes on that install), and that's worked fine as well, with mongrels running on ports 8000, 8001, 8002.

Now if I could just get apache and the proxy balancer to behave properly as the front-end, I'd be happy, but I'm a total Apache novice.

I'm tempted, since I have to learn something, to choose nginx, which seems to have good press, and looks initially like it is lighter-weight, and the easier configuration.

There are a bazillion different examples that folks have posted about using mongrel:

The mongrel How-To

Coda Hale also has a good article "Time For A Grown-Up Server: Rails, Mongrel, Apache, Capistrano and You"

Austin Godber also has an article out called "Using Mongrel Cluster" which I found helpful as well.

Good Luck!

---

### Post by davidomundo on 2008-01-30
I use gems exclusively for my Ruby packages. This is because I want to have only ONE package manager have control of my Ruby gems, and the Ubuntu/Debian package lists do not have all gems, nor the latest versions of the gems it does have.

What I usually do is install only ruby and ruby-dev packages, and then install everything else through rubygems.

It's best to bootstrap rubygems afterwards (install rubygems through rubygems) so that it can be maintained by gem update.

The reason why I suggest the bootstrapped rubygems version is because ubuntu packages currently only has rubygems version 0.9.4. This has memory issues, and can probably stall your computer if you have less than 300MB of memory.

Also, you might consider using Thin instead of Mongrel.
[http://www.wikivs.com/wiki/Mongrel_vs_Thin]("http://www.wikivs.com/wiki/Mongrel_vs_Thin")
Thin is a new web server for ruby that's supposedly faster than mongrel.

---

### Post by stairwayoflight on 2008-02-07
Hey people,

Sounds like we've been having some fun in here since I started this thread, but some folks may find themselves in the same boat as me, being a newcomer to Rails.

My original problem with the NoMethodError on :scaffold was because Rails (as of 2.0, I suppose) no longer supports dynamic scaffolding (eg. generate a model, create an admin interface, and one line telling rails to make a scaffold for the model), and the static or generated scaffolding has changed also.

I have two books including Agile Web Development with Rails, and they both rely on scaffolding in the tutorials.

Therefore, I plan on installing everything for ruby and rails directly from the ubuntu repos, because:

1. It should work
2. It should be compatible with the books

Once I have some practise I plan on switching to the newer versions.

---

### Post by cipher999 on 2008-05-03
Hey people, I'm in the same boat. I would like to use rails 1.2.6 or earlier since my web host sticks to 1.2.3.
But I'm running Hardy Heron and the default ruby is 2.0.2....
I've been trying to install an older version with no success so far. How do I install an earlier Rails ?

---

### Post by elithrar on 2008-05-05
```

$ sudo gem install -v 1.2.6 rails

```

---

