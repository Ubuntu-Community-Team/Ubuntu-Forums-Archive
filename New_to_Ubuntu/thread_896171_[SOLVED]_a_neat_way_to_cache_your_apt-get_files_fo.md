---
title: "[SOLVED] a neat way to cache your apt-get files for lan users"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by stinger30au on 2008-08-20
i have been hunting for a while to find a way to get one of my ubuntu machines to save the updates it gets on its hdd and any other machine on my lan running 8.04 to d/l it update from my local machine  and  it saves me d/l the same file for  3 of my pcs running  8.04

well, after much looking i have found this, it says it for 6.10 but i cant see why it wont work in 8.04

[http://ubuntu-tutorials.com/2007/01/08/save-bandwidth-during-updates-with-apt-cacher-ubuntu-610/](http://ubuntu-tutorials.com/2007/01/08/save-bandwidth-during-updates-with-apt-cacher-ubuntu-610/)

in one of the comments underneath it says some interesting comments like this

 
            EWB on                         January 29th, 2007 8:52 pm                           Rather than edit your sources.list, you can add
 Acquire::http::Proxy “[http://apt-cache-machine:3142&#8243;;]("http://apt-cache-machine:3142%E2%80%B3;")
 to your apt.conf. I think Synaptic has a dialog for this. If the apt-cacher machine is down, its easy to switch back to direct access.



             DNza on                         August 27th, 2007 3:13 am              
             Ubuntu Feisty Fawn install update from repository already downloaded:
Easier way - I’m a noob and tried all sorts of things. Could be wrong but without a whole bunch of tweaking this doesn’t seem to work with Feisty, so I tried a more straight forward way - simply copy the package files into /var/cache/apt/archives/ !
I Installed Feisty and fiddled so much I broke it & fixed it several times. Then I installed it again, same disk, new partition, clean install. But I didn’t want to download the updates again (”broad”band in S.A. is a p of beyond belief!), so I simply copied all the packages from the /var/cache/apt/archives/ on the first install to /var/cache/apt/archives/ on the second.
NB: I had to do so as root or the copy/paste wasn’t possible.
(To log in as root, System>Administration>Users and Groups; select root, click Properties, type & confirm a password, presto! Log out, log in as root, do your magic!) Good luck!



i must try this out and see if it works

---

### Post by stinger30au on 2008-08-20
more handy info

[http://www.zyxware.com/articles/2008/01/18/use-apt-cacher-to-save-bandwidth-multiple-pcs](http://www.zyxware.com/articles/2008/01/18/use-apt-cacher-to-save-bandwidth-multiple-pcs)

plus how to support multiple versions using just one pc

       Hi,
 This seems to be very promising.... Would save me a lot of headache :). What i am wondering though is whether apt-cacher supports multiple versions. I have a few machines running gutsy and while others run feisty. Are there any special configurations to support multiple versions???
     
            
[LIST]
[*][reply]("http://www.zyxware.com/comment/reply/132/1402")
[/LIST]

                May 1, 2008 - 03:56 — webmaster              **[All ubuntu releases on one apt-cacher]("http://www.zyxware.com/articles/2008/01/18/use-apt-cacher-to-save-bandwidth-multiple-pcs#comment-1642")**

             Yes. You can use one installation of apt-cacher for all the releases of Ubuntu. In our office we have releases from 6.06 to 8.04 running smoothly on one apt-cacher. When you set the configuration in the apt-cacher just remember to not use the release names as part of the urls. You can just pass them via the deb line in the sources.list. For example in the apt-cacher.conf set the path map as
archives.ubuntu.com ubuntu; security.ubuntu.com ubuntu-security
and then in the sources.list set of a hardy machine
deb [http://192.168.1.10/ubuntu](http://192.168.1.10/ubuntu) hardy main restricted universe
deb [http://192.168.1.10/ubuntu-security](http://192.168.1.10/ubuntu-security) hardy main restricted universe
while for a gutsy machine you can use
deb [http://192.168.1.10/ubuntu](http://192.168.1.10/ubuntu) gutsy main restricted universe
deb [http://192.168.1.10/ubuntu-security](http://192.168.1.10/ubuntu-security) gutsy main restricted universe
Cheers
[Anoop John]("http://anoopjohn.com/")
Team Zyxware

---

