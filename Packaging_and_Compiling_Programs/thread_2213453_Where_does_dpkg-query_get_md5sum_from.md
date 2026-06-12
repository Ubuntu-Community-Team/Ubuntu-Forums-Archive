---
title: "Where does dpkg-query get md5sum from?"
date: 2014-03-26
forum: Packaging and Compiling Programs
---

### Post by lordkom on 2014-03-26
I have riak installed from Basho's upstream apt repository. Basho is the developer of riak. 


I made a modification to /etc/riak.app.config to change the storage backend.
```

$ md5sum /etc/riak/app.config
11b3024959bd79c7f7f724d3eabd0881  /etc/riak/app.config

```

Using dpkg-query, I can get the md5sum of the file when the deb was installed.
```

$ dpkg-query --showformat='${Conffiles}' --show riak
 /etc/riak/vm.args b2514f80e91e62ff89f726b8694b5375
 /etc/riak/app.config a61d139c1b0596ca8e3d19e44a34f401
 /etc/riak/key.pem 7806b231b13676ea2fc7bcdc831f7d94
 /etc/riak/cert.pem 471a7452c0b80e42b37122156f2195df
 /etc/init.d/riak b34dd7a93743aa70821c3856b9ae58b0k

```

If I don't have any files in /var/lib/dpkg/info, such as /var/lib/dpkg/info/riak.md5sums, where does dpkg-query get the md5 digest for the particular files I have interest in? Without digging apart the dpkg-query code, can someone clue me in where these values are stored or how they are obtained?

Verification that the dpkg-query output is the original md5sum when the deb was installed:
```

$ ar vx riak_1.4.8-1_amd64.deb
x - debian-binary
x - control.tar.gz
x - data.tar.gz

$ tar xf data.tar.gz 

$ md5sum etc/riak/app.config 
a61d139c1b0596ca8e3d19e44a34f401  etc/riak/app.config

```

The app.config md5sum matches the output from dpkg-query.

---

