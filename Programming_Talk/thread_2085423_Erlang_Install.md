---
title: "Erlang Install"
date: 2012-11-18
forum: Programming Talk
---

### Post by rajames429 on 2012-11-18
I am using Ubunut Precise (12.04 LTS) in VMWare (for months)

I had Erlang R14B04 installed. 

I used the commands (below) to install R15B 

everything went fine, but when I run erl at the command prompt, I get the R14B04 shell 

I cannot locate the activate command (listed on another post) 

**How do I set erl to the new R15 version ? **




The commands I used were: 

apt-get -y install build-essential m4 libncurses5-dev libssh-dev unixodbc-dev libgmp3-dev libwxgtk2.8-dev libglu1-mesa-dev fop xsltproc default-jdk

mkdir -p /src/erlang

cd /src/erlang

wget [http://www.erlang.org/download/otp_src_R15B.tar.gz](http://www.erlang.org/download/otp_src_R15B.tar.gz)

tar -xvzf otp_src_R15B.tar.gz

chmod -R 777 otp_src_R15B

cd otp_src_R15B

./configure

make

make install

NOTE: I used sudo where appropriate and I got no install errors!!

---

### Post by lykeion on 2012-11-18
A simple solution would be to add the erlang path to the PATH variable in ~/.bashrc file. Something like this:
1. edit ~/.bashrc with a text editor (vim or other)
```
vim ~/.bashrc
```
2. add these lines (change path to your real erlang path)
```
ERLANG_HOME=/path/to/erlang15b
export PATH=$PATH:$ERLANG_HOME/bin
```
3. save and quit
4. load ~/.bashrc
```
source ~/.bashrc
```
5. try the erl command
```
erl
```

Another solution would be to install Erlang 15B via a PPA repository, like this one: [https://launchpad.net/~scattino/+archive/ppa](https://launchpad.net/~scattino/+archive/ppa)

---

### Post by rajames429 on 2012-11-18
Thank you. I located erlang (R15B) in /usr/local/lib/erlang. 

I added the information to my .basrc as you suggested and it worked (will wonders ever cease ?!?!)

---

