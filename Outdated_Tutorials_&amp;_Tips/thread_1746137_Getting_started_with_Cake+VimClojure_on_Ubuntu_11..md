---
title: "Getting started with Cake+VimClojure on Ubuntu 11.04"
date: 2011-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by doubleagent03 on 2011-05-01
I'm fairly new to Ubuntu, and writing 'tip' posts, but if this can help anyone, I'm game.

We're going to get the following things up-and-running, because Clojure is perfect, and even more perfect if you've got good tools, which means we've got to totally restructure our existing language to discuss it, but whatever.

Opening links.

Clojure - [http://clojure.org/](http://clojure.org/)
VimClojure - [http://www.vim.org/scripts/script.php?script_id=2501](http://www.vim.org/scripts/script.php?script_id=2501)
Cake - [https://github.com/ninjudd/cake](https://github.com/ninjudd/cake)


[CENTER]Prerequisitues[/CENTER]

First things first.  VimClojure is 'bootstrapped' on top of Ruby, and Clojure, of course, needs Java (jdk6 atm).  Go ahead and install Ruby the typical way through the Software Center (I also select the Interactive reference, Header files, and Examples).

The central repository currently only contains the jdk6 runtime, so we've got to get jdk6 from a different repo.  [This](http://ubuntuguide.net/install-sun-java-6-jrejdk-from-ppa-in-ubuntu-11-04) page tells us how.*

```

sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk
```


[CENTER]Get Cake[/CENTER]

The simplest way to grab Cake is to just use Gem, the Ruby package manager.  Luckily that's installed with the Ruby package.  Before we do that there's something to understand about Cake.  Cake executes using Env, and expects the Ruby executable to be called...'ruby'.  It's probably just an oversight on the part of the Ubuntu devs that they called these package ruby1.9.1, etc., but luckily it's easily fixed for the case of applications executing in a different environment.  Pick a directory, make symlinks with sane names to the ruby executables, add the dir to your path, restart your session, and you're good to go.

```
mkdir ~/BinLinks
ln -s /usr/bin/ruby1.9.1 ~/BinLinks/ruby
// whatever other symlinks you want
vim ~/.bashrc
// add the following to your .bashrc
#doubleagent's additions....
PATH=$PATH:~/BinLinks/
```

Now we can install cake.

```
gem1.9.1 install cake
```

Take note of the directory it's installed in and add that to your path as well.

```
sudo updatedb
locate cake
vim ~/.bashrc
// add this to your .bashrc
PATH=$PATH:~/BinLinks/:/var/lib/gems/1.9.1/gems/cake-0.6.3/bin/
```

Remember that anytime you update your .bashrc, you should source and export it to push the updates into your new session.  Or you can just open a new terminal, but at the moment that can't be done through the launch bar b/c it's retarded in Unity.**

Go ahead and run `cake help` just to ensure everything's working correctly, then we'll install VimClojure.


[CENTER]VimClojure, wherein we insult dragons and run an IDE in an editor[/CENTER]

First make sure you have Vim and are familiar with it ([http://www.google.com/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=vim+cheatsheet](http://www.google.com/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=vim+cheatsheet))

```
sudo apt-get install vim
```

Make sure you have a ~/.vim directory.  If you don't then create it.  Download version 2.2.0 from the link at the top of this tutorial and unzip it there.

Following the Readme and Docs we put the following lines in our ~/.vimrc***

```

set nocompatible
filetype plugin indent on
syntax on

```

Next, install the nailgun client so you can do things like omnicomplete, repl buffers, evaluation, etc.

```
cd ~/.vim
mkdir nailgunclient
cd nailgunclient
wget http://kotka.de/projects/vimclojure/vimclojure-nailgun-client-2.2.0.zip
unzip vimclojure-nailgun-client-2.2.0.zip
cd vimclojure-nailgun-client
make
```

If there were no errors, go ahead and add the following lines to your .vimrc

```
let vimclojure#NailgunClient = "~/.vim/nailgunclient/vimclojure-nailgun-client/ng"
let vimclojure#WantNailgun = 1

```


[CENTER]Bask in the awesomeness[/CENTER]

If all went well, everything Clojure should now magically materialize as if out of nothing.  Let's write 'Hello, World!'

```
mkdir ~/Programming
mkdir ~/Programming/Clojure
cd ~/Programming/Clojure
cake new HelloWorld
cd HelloWorld
```

Make project.clj look like this.****

```

(defproject HelloWorld "0.0.1-SNAPSHOT"
  :description "TODO: add summary of your project"
  :dependencies [[clojure "1.2.0"]]
  :dev-dependencies [[vimclojure/server "2.2.0"]])

```

Save it and a new cake command will expose itself

```
cake help | fgrep nailgun
cake ng        ;; Start the nailgun server.

```

Run that and now you'll be able to develop & deploy Clojure applications in an extraordinarily rich environment, all from the command line.

A few VimClojure shortcuts to get you started

```
C-xC-o ; omnicomplete
\ef ; evaluate file
\sr ; open repl in new buffer
,close ; close repl
\p ; close buffer
```


Happy Hacking!  {=:popcorn:



*Apparently you can find jdk6 in other repos.  I can't imagine what the differences would be, so use whatever.
**[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/741081](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/741081)
***One very annoying side effect is that the alternate page up and page down bash bindings get screwed up by one of these settings.  If anyone has a solution, please let me know. :)
****VimClojure will always complain initially.  This is OKAY.  You haven't started the server yet.  Just '\p' out and edit the file as normal.

---

### Post by cmnorton on 2011-07-27
I've got cake 0.6.3 and new is not a command. Any ideas?
Edit:
-------
cake new does work. I had run this having previously run cake, so things were screwed up.

---

