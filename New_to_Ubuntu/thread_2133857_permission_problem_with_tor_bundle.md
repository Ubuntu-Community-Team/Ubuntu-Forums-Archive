---
title: "permission problem with tor bundle"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by some1at127001 on 2013-04-09
Hello!

I've just downloaded the Tor Bundle ([https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-i686-2.3.25-6-dev-en-US.tar.gz](https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-i686-2.3.25-6-dev-en-US.tar.gz)) and tried to fire it up, but it doesn't run properly.

Downloaded it on the desktop, then:

```


~/Desktop$ sudo cp tor-browser-gnu-linux-i686-2.3.25-6-dev-en-US.tar.gz /opt/
/opt$ sudo tar -xzvf tor-browser-gnu-linux-i686-2.3.25-6-dev-en-US.tar.gz
/opt$ sudo rm -rf tor-browser-gnu-linux-i686-2.3.25-6-dev-en-US.tar.gz
/opt$ sudo chmod 777 tor-browser_en-US/
/opt$ sudo ln -s /opt/tor-browser_en-US/start-tor-browser /usr/bin/tor-browser


```

I started a Terminal session and ran

```
tor-browser
```

The program starts with an error: *"Unable to open configuration file /opt/tor-browser-en-US/App/.../Tor/torrc".*

It seems to be a permission problem (with the files copied to /opt and /usr/bin) because if I leave the program on my desktop I get no errors and the program runs perfectly!

On Tor's website they say: "Do not unpack or run TBB as root", which I think I didn't. The only thing that I don't like is to keep the entire Tor folder and program on my desktop or in my /home/user. Is there any way to make it run from /opt or /usr/bin?

Thank you!

**UPDATE: **

I checked the permissions and the only difference is this:

```

/opt$ ls -al
drwxr-xr-x 10 root root 4096 Apr  9 19:57 tor-browser_en-US

/opt$ ls -al ~/Desktop/tor-browser_en-US
drwxr-xr-x 10 machine machine 4096 Apr  9 19:43 tor-browser_en-US
```

All files have the same permissions in both folders, what is different is that folder "root root" vs "machine machine" permission.

Any ideas?

**UPDATE 2. PROBLEM SOLVED!**

```

sudo chown -R machine:machine /opt/tor-browser_en-US/

```

where the first *machine* is my user and the second *machine* is my group (they replaced root:root, because the program doesn't accept to run as root)

The program is running perfectly, actually I'm using it right now.

This post could be mark as SOLVED.

---

