---
title: "HOWTO: Make google talk voice calls"
date: 2006-02-08
forum: Outdated Tutorials &amp; Tips
---

### Post by chiefofthejojos on 2006-02-08
This post will show you how to install a program on ubuntu which can actually make voice calls to other google talk users. Unfortunately, it's not in a stable version yet so we will have to compile the source. This is a development branch of the psi jabber client, being called psi-jingle.

First, lets satisfy some dependancies.  NOTE: The universe repository needs to be enabled.

```

sudo apt-get install darcs speex libspeex-dev libqt3-mt-dev qt3-dev-tools qca-tls qca-dev libqca1c2 libasound2-dev libglib2.0-dev build-essential
``` 
There's one more that needs to be compiled and installed by hand. NOTE: currently you must use version 0.7.1 of libortp or it won't work.

```
wget http://linphone.org/ortp/sources/ortp-0.7.1.tar.gz
tar zxvf ortp-0.7.1.tar.gz && rm ortp-0.7.1.tar.gz
cd ortp-0.7.1
./configure
make
sudo make install
sudo ln -s /usr/local/lib/libortp.so.0 /usr/lib/libortp.so.0
``` 
Now, get and compile psi-jingle.  NOTE: The --enable-jingle option must be present if you want to make voice calls.

```
darcs get --partial --set-scripts-executable http://dev.psi-im.org/darcs/psi-jingle
cd psi-jingle
./configure --with-ortp-inc=/usr/local/include/ --enable-jingle
make
sudo make install
``` 
Good luck!

---

### Post by sriram.vr on 2008-11-10
Here is a workaround for having voice chat with google talk users.

[http://sriramblox.blogspot.com/2008/08/making-voice-call-to-google-contact.html](http://sriramblox.blogspot.com/2008/08/making-voice-call-to-google-contact.html)

[http://sriramblox.blogspot.com/2008/10/voice-chat-with-google-talk-user-using.html](http://sriramblox.blogspot.com/2008/10/voice-chat-with-google-talk-user-using.html)

I hope this helps.

---

