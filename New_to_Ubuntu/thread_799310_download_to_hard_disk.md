---
title: "download to hard disk"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by rraj.be on 2008-05-18
we are installing some packages in terminal via apt-get install....

where these files will be temporarily cached in the system.

can i save a copy of downloaded debain packages for my future use because my net connection is dead slow that when i download its speed is around 2- 3 kbps........

else could i download and save debain packages directly for internet......just like downloading exe files in windows

---

### Post by spiderbatdad on 2008-05-18
check the file /var/cache/apt/archives in hardy.

---

### Post by Bakon Jarser on 2008-05-18
look in

/var/cache/apt/archives

---

### Post by sdennie on 2008-05-18
The files should be cached in /var/cache/apt/archives.  You can download individual debs but, you are probably better of using:

```

sudo apt-get install -d some_package

```

That will insure that you get all the dependencies that the package you want to install also get downloaded into /var/cache/apt/archives.

---

### Post by wpshooter on 2008-05-18
> **rraj.be said:**
> we are installing some packages in terminal via apt-get install....

where these files will be temporarily cached in the system.

can i save a copy of downloaded debain packages for my future use because my net connection is dead slow that when i download its speed is around 2- 3 kbps........

else could i download and save debain packages directly for internet......just like downloading exe files in windows

My question for you would be WHY is your connection speed so slow ?

What type of connection is this, is it DSL, Cable, or dial-up.  If it is either of the first 2, my first task would be to trouble shoot why these are so slow.   Have you tried to discover the cause of this ?

---

### Post by rraj.be on 2008-05-18
thanks vor..

i used to install using suo apt-get install..

but if i get download website or link then i can download  individual debian packages so that there is no need for me to download each time i wana2 install these packages......


and regarding caching i could not find any debian package files in /var/cache

---

### Post by rraj.be on 2008-05-18
thanks vor..

i used to install using suo apt-get install..

but if i get download website or link then i can download  individual debian packages so that there is no need for me to download each time i wana2 install these packages......


and regarding caching i could  find  debian package files in /var/cache

---

### Post by rraj.be on 2008-05-18
> **wpshooter said:**
> My question for you would be WHY is your connection speed so slow ?

What type of connection is this, is it DSL, Cable, or dial-up.  If it is either of the first 2, my first task would be to trouble shoot why these are so slow.   Have you tried to discover the cause of this ?



i am using just GPRS connection along with my sony ericsson W200I mobile for internet connection...

i am from a very rural area i India...

its horrible to learn something through this slow internet connections

i dont have any other go except GPRS

---

### Post by sdennie on 2008-05-18
I'm not sure why /var/cache/apt/archives isn't working for you.  What happens if you type:

```

locate *.deb

```

I'm also not completely sure what you are trying to accomplish.  It sounds like you want to download .debs from a single machine and use them on multiple machines.  That should work fine but, a lot of .debs will have dependencies which is why I recommended the "install -d" option to download things that you may not want to install on the local machine but want to be able to install on another machine.

---

### Post by rraj.be on 2008-05-18
sorry vor its a typographical mistake..

i could find every package here.

then just c my post regarding ghost like package  for back up entire installation


please help me if u can

---

### Post by sam_delta on 2008-05-18
you can also download .deb packages from ubuntu repositories @
packages.ubuntu.com/
or
archive.ubuntu.com/ubuntu/

sam

---

### Post by Bakon Jarser on 2008-05-19
It sounds like this might be what you want to do.

[How To Make A Live CD From Your Install]("http://ubuntuforums.org/showthread.php?t=688872&highlight=make+live+cd")

---

### Post by rraj.be on 2008-05-20
Thanks Bakon...

This is the thing that im searching.

---

### Post by rraj.be on 2008-05-21
> **Bakon Jarser said:**
> 

[How ]("http://ubuntuforums.org/showthread.php?t=688872&highlight=make+live+cd")

I done whats in the above link.

but when i booted from that live cd only the shell is appearing and no other login screen is getting open

any one can solve this

---

### Post by Bakon Jarser on 2008-05-21
I'm planning on doing the same thing you're trying to do once I do a fresh install (just got a new hard drive today).  Remastersys looks like it does this a lot easier and faster.

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by rraj.be on 2008-05-21
yes i have tried with many other solutions like reconstructor, the way that used without software etc and i found that remastersys is the perfect easy and  efficient method in time consumption.

---

### Post by bodhi.zazen on 2008-05-21
Just a passing tip :

You can download packages and dependencies with apt-get :

apt-get -d package

I would think that is faster then finding packages and downloading and installing dependencies manually.

You can also install a single package with dpkg

dpkg -i package.deb

You can then install dependencies with apt-get

apt-get install -f

See man apt-get : [http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

---

### Post by rraj.be on 2008-05-21
My internet connectionis very slow that it will take around  hour to download  MB file.

so only i'm asking how to save all my debian packages to my hard disk.

---

### Post by bodhi.zazen on 2008-05-21
I understand, however your question is a little cryptic.

If your problem is a slow internet connection, how does saving .deb to hard drive help ? That is the question. Using apt-get to at least resolve dependencies will save you the hassle of manually resolving dependencies.

The advice to use aptonCD is also good advice. This will resolve dependencies as well.

One other thought, if you are running on a LAN and planning to share .deb, set up a local repository.

download the files to a central location, install lightttpd, and share the deb over your lan.

Say you have all the .deb in /var/www/repo

Add :

deb [http://server/var/www](http://server/var/www) repo/

to /etc/apt/sources.list on your clients.

The you can install over your LAN with :

apt-get update 
apt-get install package

If you want to set up a local repository, and need additional help, let me know. It may sound complicated at first, but it is quite easy. Your initial download time may be slow, but uploading to clients will be quite fast.

I guess it all depends not on saving .deb to hard drive, but what are you going to do with the .deb once they are downloaded to save time ?

---

### Post by rraj.be on 2008-05-21
if i have .deb packages in a cd then for each of my reinstalation i can install my required packages without internet connection.

rather i could get what you are saying about local repositry but it will also take some downloading no?


if this will be more helpfull then could you help me in stetting up local repo.

i have created the live cd.

but  when i boot into it its taking me to shell.
not geting me to login screen.

---

### Post by bodhi.zazen on 2008-05-21
To set up a local repository see this thread :

[http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862)

next install lighttpd to serve the files. lighttpd is lighter then apache.

To install :

```
sudo apt get install lighttpd
```

To configure, see this link :

[http://www.cyberciti.biz/tips/installing-and-configuring-lighttpd-webserver-howto.html](http://www.cyberciti.biz/tips/installing-and-configuring-lighttpd-webserver-howto.html)

The majority of that link is installing from source, which you can skip. Look at the bottom section to configure lighttpd.

---

### Post by rraj.be on 2008-05-22
This is waht happened for me when did as in the post you said  [[http://ubuntuforums.org/showthread.php?t=42862]](http://ubuntuforums.org/showthread.php?t=42862])

```
root@raj-dworkstation:~# mkdir /home/rajrepo/    
mkdir: cannot create directory `/home/rajrepo/': File exists
root@raj-dworkstation:~# cd /bin/
root@raj-dworkstation:/bin# sudo nano autorepo
root@raj-dworkstation:/bin# sudo chmod +x autorepo
root@raj-dworkstation:/bin# cd /home/rajrepo/
root@raj-dworkstation:/home/rajrepo# autorepo
 Wrote 0 entries to output Packages file.
```

whats the problem.

---

### Post by rraj.be on 2008-05-22
any one there please help me

whats the mistake that i have done

---

### Post by bodhi.zazen on 2008-05-22
Looks like the repo is set up, next download some deb.

---

### Post by rraj.be on 2008-05-25
I have already downloaded all my required packages and got installed on my system.
now what can i do.

i have copies of /var/cache/apt/archives in one cd.

i tried to set it as a cd repository but it displayed that its not a Ubuntu package cd.

how to make my DVD to be a package DVD that could be identified by my synaptic packet manager.

---

