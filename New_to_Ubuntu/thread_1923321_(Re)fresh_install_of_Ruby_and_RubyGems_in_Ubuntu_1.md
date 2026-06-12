---
title: "(Re)fresh install of Ruby and RubyGems in Ubuntu 11.10"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by frogo on 2012-02-10
Hi, 

I recently installed 11.10. I had tried to install Ruby and RubyGems but was unable to use them in 10.10. This time around I am trying again to install Ruby and RubyGems. It looks like I have messed things up badly in no time. I am wondering whether there is an easy and proven way of either correcting the broken installs or redoing a clean install of Ruby and RubyGems in Ubuntu 11.10 

To be very clear: I am not a Ruby developer, I know nothing about it. I just need to use a couple of gems. I have little more than monkey abilities managing my system... I'm sorry, I really need "install Ruby and RubyGems on Ubuntu 11.10 for dummies" 

Some details below.

Many thanks,
f


What I did, vaguely: 

I have tried a few different things over the past two weeks but it seems utterly broken or I have no clue what I have done wrong. I am completely lost because I keep finding contradicting advices on the recommended way of installing R&RG (including in this forums). Some claim RVM is recommended, some claim Iit is not the Debian/Ubuntu way. 

I think over time, I followed a number of conflicting advices, installed Rubys (some variant of 1.9.2) and RubyGems, although I can't recall how. I also installed RVM. I have never managed to make use any other version of Ruby than the default 1.8(.7?) from Ubuntu. 

I have (or have had) a number of problems which superficially show as errors in the command line. 

i) Bad gemspecs (minor, I guess):

- Invoking gem lists various errors, lately things of the sort:

```
Invalid gemspec in [/var/lib/gems/1.8/specifications/railties-3.2.0.gemspec]: Illformed requirement ["#<YAML::Syck::DefaultKey:0xb5f6cc40> 3.2.0"]

```

- Also, in the past I had errors in some gemspecs related to date formats. I fixed them editing as prescribed somewhere (lost the link, sorry). Maybe I messed things up.


ii) Permission errors (embarrassing): 

I also seem to have officially entered permission hell. I think I did all my installs with sudo, as prescribed somewhere (again, lost track of the link, sorry).

If I try to install a gem, this is what I get (after the illformed errors exemplified above):

```
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions into the /var/lib/gems/1.8 directory.

```

---

### Post by Ms. Daisy on 2012-02-10
First the disclaimer: I'm probably about as noob with Ruby as you, so take my advice accordingly.
 
I successfully installed Ruby on 11.10 in the last month.  I followed the installation directions from the Ruby webpage: [http://www.ruby-lang.org/en/downloads/](http://www.ruby-lang.org/en/downloads/). I'm pretty sure I followed the "package management systems" directions. Did you try that guide?
 
I'm ***guessing*** that you want to get Ruby installed first, then install the gems.

---

### Post by frogo on 2012-02-10
Thanks, I'm lost and ready to try anything :) 

> **Ms. Daisy said:**
> 
 I successfully installed Ruby on 11.10 in the last month.  I followed the installation directions from the Ruby webpage: [http://www.ruby-lang.org/en/downloads/](http://www.ruby-lang.org/en/downloads/). I'm pretty sure I followed the "package management systems" directions. Did you try that guide?
 

Can't recall honestly, but apparently I did; trying it gave as follows:

```
> sudo apt-get install ruby1.9.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ruby1.9.1 is already the newest version.
ruby1.9.1 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 69 not upgraded.

```

Odd, I thought I had installed a 1.9.2 as well...

> I'm ***guessing*** that you want to get Ruby installed first, then install the gems.

Yeah, I think I did that. 

Apparently, both Ruby (Rubies, actually) and RubyGems are installed. They just seem to be broken installs. 

thanks for your suggestion

---

### Post by frogo on 2012-02-10
> **frogo said:**
> 
Apparently, both Ruby (Rubies, actually) and RubyGems are installed. They just seem to be broken installs. 


on second thoughts, the installs may not have been broken. It's more likely I'm just entirely clueless..  ](*,)

I've done a number of 
```

apt-get updates
apt-get install ruby-full
``` and whatnots. There's only one paragraph that seems advisable to follow from [http://docs.rubygems.org/read/chapter/3](http://docs.rubygems.org/read/chapter/3)

I know RVM is installed (though I didn't touch it this time), but I can't seem to be able to use anything but the 1.8 Ruby that came with the distribution. I have a hunch this is because I'm inept. 

I finally managed installing a gem and have it run... It was useful to have come across a mention of a problem with certain date formats in gemspecs on Ubuntu. Here's a link among others: 
[http://stackoverflow.com/a/8030586](http://stackoverflow.com/a/8030586)

---

