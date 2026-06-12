---
title: "Dnscrypt installation"
date: 2013-11-11
forum: New to Ubuntu
---

### Post by ido555333 on 2013-11-11
hi

i try to follow this tutorial but i am new to linux,
i need some help here

tutorial:
[http://jeremywc.blogspot.co.il/2013/07/setting-up-dnscrypt-proxy-on-ubuntu-1304.html](http://jeremywc.blogspot.co.il/2013/07/setting-up-dnscrypt-proxy-on-ubuntu-1304.html)


**[Setting up dnscrypt-proxy on Ubuntu 13.04]("http://jeremywc.blogspot.com/2013/07/setting-up-dnscrypt-proxy-on-ubuntu-1304.html")**


i download :
git clone [URL]https://github.com/jedisct1/dnscrypt-proxy.git
git clone [URL]https://github.com/jedisct1/libsodium.git  



and now he ask for me to install them in their respective directories
where it is?

i try to do something like that
sudo find / -name libsodium -type d

he gave me
/root/libsodium 
[he gave me 2 more option but this is more likey to be the 1]

so i did 
cd /root/libsodium
and than:
./autogen.sh
./configure
make -j2
sudo make install

but it didnt work some1 know where the directories he intend?

maybe some1 can make this tutorial to beginners step by step?

thx for the help

sorry for my English.

---

### Post by oldos2er on 2013-11-11
Moved to Absolute Beginners.

Edit: Please use the default font and font color. Parts of your post were unreadable to me, which is why I edited it.

---

