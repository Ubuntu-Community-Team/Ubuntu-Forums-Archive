---
title: "Installing rails gives error: cannot load such file — zlib"
date: 2013-02-06
forum: Programming Talk
---

### Post by adige72 on 2013-02-06
When i try to install rails in Ubuntu 12.10 i get this error:

```
    $ gem install rails
    ERROR: Loading command: install (LoadError)
    cannot load such file -- zlib
    ERROR: While executing gem ... (NameError)
    uninitialized constant Gem::Commands::InstallCommand
```So i completely removed rvm:

    ```
rvm implode
    sudo rm -rf ~/.rvm
```removed the script calls in my .bashrc and .bash_profile

and checked if they're really removed:

    ```
env | grep rvm #no output, so rvm is removed
    ruby -v #The program 'ruby' can be found in the following packages: blabla
```I already have these via sudo apt-get install:

    ```
curl zlib1g-dev zlib1g libssl-dev build-essential openssl libreadline6 libreadline6-dev curl git-core libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion pkg-config
```Then proceed to install from scratch

    ```
curl -L [https://get.rvm.io](https://get.rvm.io) | bash -s stable --ruby --auto-dotfiles
```then run that line and restarted terminal regard to this message:
    
      ```
* To start using RVM you need to run `source /home/adige/.rvm/scripts/rvm`
        in all your open shell windows, in rare cases you need to reopen all shell windows.
```Then ```
rvm pkg install readline
``` but completed with error:

    ```
...
    Error running 'autoreconf -is --force', please read /home/adige/.rvm/log/readline/autoreconf.log
    ...
    Please note that it's required to reinstall all rubies:
    
        rvm reinstall all --force
```I think it's installed anyway, right? Before reinstall all rubies, i installed zlib of course:

    ```
# w/out verify, it gives checksum error
    rvm pkg install zlib --verify-downloads 1
```Then run ```
rvm reinstall all --force
``` and completed with error again:

    ```
...
    Install of ruby-1.9.3-p374 - #complete 
    Making gemset ruby-1.9.3-p374 pristine.
    Error running '' under ,
    please read /home/adige/.rvm/log/ruby-1.9.3-p374/gemset.pristine.log
    Making gemset ruby-1.9.3-p374@global pristine.
```**[gemset.pristine.log]("http://pastebin.com/ZrmWStNB")**

Then reinstall ruby with zlib support:

    ```
rvm reinstall 1.9.3-p374 --with-zlib-dir=$rvm_path/usr
```which returned same error and **[same log]("http://pastebin.com/ZrmWStNB")** but completed anyway.

Finally i tried to install rails gem again but ```
cannot load such file -- zlib !
```Here is the **[rvm info]("http://pastebin.com/08fp9PVW")**

What am i doing wrong?

---

### Post by Mikeb85 on 2013-02-06
Are you sure you're not missing a zlib library?  On openSUSE (what I'm running) there's one called only 'zlib', which doesn't appear in your apt-get install bit...

---

### Post by adige72 on 2013-02-06
There is no such package

```
adige@adige-LG:~$ sudo apt-get install zlib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package zlib
```

---

### Post by spjackson on 2013-02-06
I think that should be
```

sudo apt-get install zlib1g

```

---

### Post by adige72 on 2013-02-06
> **spjackson said:**
> I think that should be
```

sudo apt-get install zlib1g

```

That's already installed.

---

