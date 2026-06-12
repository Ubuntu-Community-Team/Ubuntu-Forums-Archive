---
title: "minitube"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by HappyAsHellas on 2014-03-26
Any way to get mintube without having to sign up to ubuntu 1 ? It seems a bit like google or something, give us all your details and you can have.......
Or am I just being paranoid?

---

### Post by Kestreln8144 on 2014-03-26
I'm not sure what you're referring to. I just installed minitube and I didn't need to use Ubuntu One.

---

### Post by scollar1971 on 2014-03-26
And the problem with signing up for ubunto one is?

---

### Post by HappyAsHellas on 2014-03-27
The problem seemed to be that in order to get something free, you have to subscribe for something you didn't ask for. In windows land this is quite normal and you end up with all sorts of unwanted crap on your computer, hence the suspicion concerning ubuntu 1.

---

### Post by monkeybrain20122 on 2014-03-27
You can compile from source. It takes only a few minutes.
Download tarball from [http://flavio.tordini.org/minitube/minitube-sources](http://flavio.tordini.org/minitube/minitube-sources)
Extract tarball by right click, extract here.

Install the dependencies
```
sudo apt-get install build-essential qt4-dev-tools libphonon-dev phonon-backend-vlc
```

Now  say you extracted the tarball to the folder minitube in Downloads, in the terminal
```
cd Downloads/minitube
qmake-qt4
make
```

That's it. The binary is now in the folder /Downloads/minitbe/build/target/
click the file minitube inside and it will start.

Edited: if during compiling you get missing translations errors, consult this thread [http://flavio.tordini.org/forums/topic/cant-build-2-1-4-missing-translations](http://flavio.tordini.org/forums/topic/cant-build-2-1-4-missing-translations)

---

### Post by coffeecat on 2014-03-28
Why do think that you need Ubuntu One for minitube? Minitube is in the repository -  you simply install it from the Software Centre or Synaptic or using apt-get in the terminal, and then use it.

Kestreln8144 has already stated this in post #2, yet you did not respond to them but continued to make complaints about Ubuntu One.

---

### Post by mc4man on 2014-03-28
minitube from the normal repo is old & won't work on some vids. The version from the partner (private) repo is more up to date though currently the source is latest.
(That reflects a slight change from recent where the private repo was latest & source lagged slightly behind
normal repo - 2.0-1
partner - 2.1.5
source - 2.1.6

signing on to ubuntuone is only a matter of your email/password, no different than what you've already done to post here. you're not "subscribing" to anything other than you can use the  free 5GB cloud storage or not use it.

---

