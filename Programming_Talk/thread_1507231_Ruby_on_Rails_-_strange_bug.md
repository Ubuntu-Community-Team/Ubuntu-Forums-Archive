---
title: "Ruby on Rails - strange bug?"
date: 2010-06-11
forum: Programming Talk
---

### Post by FredDie3785 on 2010-06-11
Hello!
I want to progress as web developer and want learn Ruby on Rails. But got a strange bug after I've installed this enviroment.

First I've installed 'ruby' with a little help from terminal:
```
sudo apt-get install ruby
```

This package also installed 'libruby1.8' and 'ruby1.8'. Afterwards I installed 'irb' and 'rdoc'. Everything went fine.

Then I went to [http://rubyforge.org]("http://rubyforge.org/frs/?group_id=126") to download the lastest rubygems. The last version available is '1.3.7' which is newer than 'rubygems' package in the repos. 
I've unpacked the .tgz and installed with:
```
sudo ruby setup.rb
```
Terminal said it was installed without a problem. 
But when I want to check the 'rubygems' version with:
```
gem -v
```
The terminal says:
> "Gem" could be found in the following packages:
    * rubygems1.8
    * rubygems1.9.1
Try sudo apt-get install <choosen_package>

But I've installed it, yes? Should I install 'rails' with what I've got? Or maybe add the packages from repos and install it then. Will it collide with 'gems' that I installed from source?
I want to make my root filesystem clean as possible.

Thanks in advance.

PS. I'm using Ubuntu 10.04 Lucid Lynx 64bit.

---

### Post by ja660k on 2010-06-11
i tried to compile gems from source, it somehow gets confused.
```

apt-get [install rubygems

```

i suggest checkin this out:
[https://help.ubuntu.com/community/RubyOnRails#Intro%20Ubuntu%209.04%20...%20Apache2.2%20tested%20only](https://help.ubuntu.com/community/RubyOnRails#Intro%20Ubuntu%209.04%20...%20Apache2.2%20tested%20only)

follow that guide, its win.

---

### Post by FredDie3785 on 2010-06-11
Solved, thanks for the tip. But I didn't have to install ruby gems from repos, only to make link. After installing it from downloaded sources I typed in terminal:

```
sudo ln -s /usr/bin/gem1.8 /usr/bin/gem
```

And it worked.

---

