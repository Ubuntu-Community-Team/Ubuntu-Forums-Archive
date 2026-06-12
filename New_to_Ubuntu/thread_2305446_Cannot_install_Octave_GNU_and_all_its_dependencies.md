---
title: "Cannot install Octave GNU and all its dependencies on Kylin"
date: 2015-12-06
forum: New to Ubuntu
---

### Post by jon80 on 2015-12-06
I ran into a lot of trouble trying to install Octave on Unix using apt-get, tips anyone?

I read [http://www.gnu.org/software/octave/doc/interpreter/Installation.html#Installation](http://www.gnu.org/software/octave/doc/interpreter/Installation.html#Installation).  I am not sure if I need to install a C++ compiler and evidently I have some corrupt package that has to do with a dependency essentially a unix issue.  This is a package originally written in the open source community - [http://www.gnu.org/software/octave/support.html](http://www.gnu.org/software/octave/support.html).

There is some hope but none seems to stick to my mind for the time being - [http://www.computerhope.com/unix/apt-get.htm](http://www.computerhope.com/unix/apt-get.htm).

I am using Oracle VM Virtual Box ([https://www.virtualbox.org/](https://www.virtualbox.org/)) with Ubuntu Kylin ([http://www.ubuntu.com/desktop/ubuntu-kylin](http://www.ubuntu.com/desktop/ubuntu-kylin)) running on the virtual machine, it is a bit slow as well, sometimes it hangs up and does not allow me to post log files, they take too long and I cannot figure out a way to post screenshots or log files here, unfortunately there needs to be a process that enables interprocess communication between the operating system and the bug trackers.  

I had some problems with the translation of UI elements being in Chinese (which unfortunately I cannot read so I prefer that this issue is somehow resolved translating the elements to English or Maltese or some other language I am familiar with).

How does Linux Mint compare to Ubuntu - [http://www.linuxmint.com/?](http://www.linuxmint.com/?)

Why does this forum not allow me to post images to the forum is this a disk space saving functionality that enables only URLs to be linked?
It just makes life a bit complicated for me as I need to upload screenshots and videos.

Jon
[https://delicious.com/jon80](https://delicious.com/jon80) 
[http://mt.linkedin.com/in/jonathancamilleri](http://mt.linkedin.com/in/jonathancamilleri)

---

### Post by matt_symes on 2015-12-06
Hi

> 
Why does this forum not allow me to post images to the forum is this a disk space saving functionality that enables only URLs to be linked?
It just makes life a bit complicated for me as I need to upload screenshots and videos.

Images have size and dimension restrictions but you can copy and paste text from a terminal into your posts and visa-versa.

> 
I ran into a lot of trouble trying to install Octave on Unix using apt-get, tips anyone?

I read [http://www.gnu.org/software/octave/d...l#Installation](http://www.gnu.org/software/octave/d...l#Installation). I am not sure if I need to install a C++ compiler and evidently I have some corrupt package that has to do with a dependency essentially a unix issue. This is a package originally written in the open source community - [http://www.gnu.org/software/octave/support.html](http://www.gnu.org/software/octave/support.html).

I don't know a thing about Octave as I've never used it but it's in the repositories (for 16.04 dev at least).

Here's the first 5 packages and there is a total of 62 packages that match octave.

```

matthew-xu-16-04:/home/matthew:1 % acse ^octave | tee >(head -n5) | wc -l
cantor-backend-octave - Octave backend for Cantor
mwrap - Octave/MATLAB mex generator
octave - GNU Octave language for numerical computations
octave-bim - PDE solver using a finite element/volume approach in Octave
octave-biosig - Octave bindings for BioSig library
**62**
matthew-xu-16-04:/home/matthew:1 % 
```

You may want to post any errors (copy and paste from the terminal) into your next post.

```
sudo apt-get install octave
```

> How does Linux Mint compare to Ubuntu - [http://www.linuxmint.com/?](http://www.linuxmint.com/?)

Try it :) All you will get with a question like that is opinions. You will need to try it to see if the desktop suits your work flow. Under the hood it's Ubuntu.
> 
I am using Oracle VM Virtual Box ([https://www.virtualbox.org/](https://www.virtualbox.org/)) with Ubuntu Kylin ([http://www.ubuntu.com/desktop/ubuntu-kylin](http://www.ubuntu.com/desktop/ubuntu-kylin)) running on the virtual machine, it is a bit slow as well, sometimes it hangs up and does not allow me to post log files, they take too long and I cannot figure out a way to post screenshots or log files here, unfortunately there needs to be a process that enables interprocess communication between the operating system and the bug trackers.

I had some problems with the translation of UI elements being in Chinese (which unfortunately I cannot read so I prefer that this issue is somehow resolved translating the elements to English or Maltese or some other language I am familiar with).

Start a thread in the visualisation forum for help with that.

Kind regards

---

