---
title: "Installing Tor in Ubuntu 14.04"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by alex191 on 2014-05-02
Im having trouble installing Tor on Ubuntu 14.04. Do I need to type a command line?

---

### Post by oldrocker99 on 2014-05-02
[https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu)--You want Option Two.

You will need to open a terminal, yes. This page has complete instructions, and you can copy and paste each instruction, prefacing it with a 'sudo' (without apostrophes, of course) so that the commands will work, since they require superuser access.

You're taking a big first step. Enjoy the power!

---

### Post by alex191 on 2014-05-02
Im not sure but 
sudo [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <Trusty Tahr> main
for what i have to put on the terminal first?

---

### Post by alex191 on 2014-05-02
i think i got it. what i put on the terminal was 

1. Open a terminal window.
 2. Type in the following commands then hit Enter after each.
 sudo add-apt-repository ppa:webupd8team/tor-browser
sudo apt-get update
sudo apt-get install tor-browser

---

### Post by rburkartjo on 2014-05-03
or you could do this go to this link and download tor
[https://www.torproject.org/download/download.html.en](https://www.torproject.org/download/download.html.en)
(click on the gnu/linux,bsd and unix option) then download
then in whatever file you downloaded click the option extract here

then open the file click on start-tor-browser

you will get the the option to execute. click on execute NOT EXECUTE IN TERMINAL and it will start.
good luck

---

### Post by bniedem on 2014-05-30
> **alex191 said:**
> i think i got it. what i put on the terminal was 

1. Open a terminal window.
 2. Type in the following commands then hit Enter after each.
 sudo add-apt-repository ppa:webupd8team/tor-browser
sudo apt-get update
sudo apt-get install tor-browser

Thanks Alex191.  That was very easy to follow.

---

### Post by alex191 on 2014-06-09
when i click "start-tor-browser" i dont get the option to execute. All i get is a bunch of code. What i have to do is move the "start-tor-browser" to the terminal and then tor starts automatically. How do i go about making a tor button option on my menu so i dont have to copy it every time on the terminal?

---

### Post by Nobody Nessie on 2014-06-18
I give the same answer as another topic : Personnally, I just click [this link](https://www.torproject.org/dist/torbrowser/3.6.2/tor-browser-linux32-3.6.2_en-US.tar.xz) (_warning_ : this is the real Linux TBB package download link !)  I download it and extract it in my /home/ directory. Then just click on "start-tor-browser" in the /tor-browser_en-US/ directory and that's it !         _Another warning_ : I personnaly do not worry at all of using Tor as, firstly, I do nothing illegal with and, secondly, I am used to avoid Tor exit nodes (and Tor hidden services). When TorProject update their TBB, I delete the old one and install the new one in the same place !

---

### Post by cee2 on 2014-12-27
How come i cant get this to work?


> **alex191 said:**
> i think i got it. what i put on the terminal was 

1. Open a terminal window.
 2. Type in the following commands then hit Enter after each.
 sudo add-apt-repository ppa:webupd8team/tor-browser
sudo apt-get update
sudo apt-get install tor-browser

---

