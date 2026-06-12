---
title: "ns2 installation error"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by hms2 on 2014-02-17
I am trying to install ns-allinone-2.35 on the latest ubuntu x64. Already installed all the updates for ubuntu.
successfully unziped
Ran the following commands
```
 $ sudo apt-get install build-essential autoconf automake libxmu-dev
sudo apt-get install xorg-dev g++ xgraph

```

 But when trying to install ns2 getting this error at end. Anyone else here installed ns2 successfully?


```
In file included from linkstate/ls.cc:67:0:
linkstate/ls.h: In instantiation of &#8216;void LsMap<Key, T>::eraseAll() [with Key = int; T = LsIdSeq]&#8217;:
linkstate/ls.cc:396:28:   required from here
linkstate/ls.h:137:58: error: &#8216;erase&#8217; was not declared in this scope, and no declarations were found by argument-dependent lookup at the point of instantiation [-fpermissive]
  void eraseAll() { erase(baseMap::begin(), baseMap::end()); }
                                                          ^
linkstate/ls.h:137:58: note: declarations in dependent base &#8216;std::map<int, LsIdSeq, std::less<int>, std::allocator<std::pair<const int, LsIdSeq> > >&#8217; are not found by unqualified lookup
linkstate/ls.h:137:58: note: use &#8216;this->erase&#8217; instead
make: *** [linkstate/ls.o] Error 1
Ns make failed!
See http://www.isi.edu/nsnam/ns/ns-problems.html for problems


```

I am absolute beginer, so please be patient.

---

### Post by hms2 on 2014-02-17
Seems to have done it with a bit of help from google.
For anyone interested [http://www.nsnam.com/2013/10/installing-network-simulator-2-ns-235.html](http://www.nsnam.com/2013/10/installing-network-simulator-2-ns-235.html)
Some of the validation tests failed but overall ok.

---

### Post by deepakdeeppanwar on 2014-03-23
change following line in ns-2.35/linkstate/ls.h file.

Line No.: 138
Change
        > void eraseAll() {erase(baseMap::begin(), baseMap::end()); }
With
        > void eraseAll() { [COLOR=#ff0000]**baseMap::**[/COLOR]erase(baseMap::begin(), baseMap::end()); }

and run ./install from all-in-one folder.

---

### Post by yaseen2 on 2014-05-22
Very thanks [**[COLOR=#000000]deepakdeeppanwar[/COLOR]**]("http://ubuntuforums.org/member.php?u=1912542") for your reply, I am faced the same problem( "std::map<int, LsIdSeq, std::less<int>, std::allocator<std::pair<const int, LsIdSeq") while installing ns2.35 in ubuntu 14.04 LTS 64 bit and solved it using your advice.

---

### Post by pon2 on 2014-08-09
thanks it was very useful

---

