---
title: "Go - Trouble getting started"
date: 2011-11-03
forum: Programming Talk
---

### Post by Athefre on 2011-11-03
I've followed most of the steps from the following three pages:

[http://www.jeremymorgan.com/blog/linux/how-to-install-the-google-go-compiler-on-ubuntu-linux/](http://www.jeremymorgan.com/blog/linux/how-to-install-the-google-go-compiler-on-ubuntu-linux/)
[http://golang.org/doc/install.html](http://golang.org/doc/install.html)
[http://maketecheasier.com/install-google-go-in-ubuntu/2010/04/15](http://maketecheasier.com/install-google-go-in-ubuntu/2010/04/15)

When I get to the part where I create a simple code file and test it using "6g First.go", I get the error message:

First.go:3: can't find import: fmt

I've looked at many guides and forum posts about this problem, and I can't get the answers I find to work.  The problem seems to be the lines I add to the .bashrc file.  What I have added, after many edits after google searches, is:

export GOROOT=$HOME/usr/lib/go/src
export GOARCH=386
export GOOS=linux
export GOBIN=$HOME/usr/bin
export PATH=$PATH:$HOME/usr/bin

---

### Post by gsmanners on 2011-11-03
You can't install "golang"? How new is that package?

EDIT: Looks like you need 11.10 or newer to have that in the repos.

---

### Post by Athefre on 2011-11-03
> **gsmanners said:**
> You can't install "golang"? How new is that package?

EDIT: Looks like you need 11.10 or newer to have that in the repos.

I'm sorry, I don't understand.  I'm very new to Ubuntu.  What are you suggesting I do?

---

### Post by gsmanners on 2011-11-03
If you have 11.10 installed, you can simply type "golang" into a package manager (Software Center or Synaptic) and that should give you the option of installing straight from a repository. If you have 11.04 or older, then never mind. :D

---

### Post by Athefre on 2011-11-03
I'm on 11.04 :(

I keep considering an update but each time I try it gives me a message similar to "This number of files will be removed and the installation will take hours."  I'm not sure if any of those files it wants to remove are important to me, so I back out.

---

### Post by Majorix on 2011-11-03
There seems to be a ppa just for Go. Copy and paste these lines ONE-BY-ONE to the terminal:
```
sudo add-apt-repository ppa:gophers/go
sudo apt-get update
sudo apt-get install golang
```
Try this and let us know if it works.

---

### Post by Athefre on 2011-11-03
That worked, thanks :)

I had tried that before from _[this site](http://maketecheasier.com/install-google-go-in-ubuntu/2010/04/15)_.  I don't know why it worked this time.

---

