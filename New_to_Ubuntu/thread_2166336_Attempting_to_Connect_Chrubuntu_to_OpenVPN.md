---
title: "Attempting to Connect Chrubuntu to OpenVPN"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by andy15 on 2013-08-08
First post, so please bear with me.

I'd like to connect Chrubuntu (12.04) Samsung ARM Chromebook to OpenVPN. But when I

> sudo apt-get install network-manager-openvpn

it returns

> E: Package 'network-manager-openvpn' has no installation candidate

I added > deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe to /etc/apt/sources.list, did > sudo apt-get update and again tried > sudo apt-get install network-manager-openvpn Got the same error.

I would attempt to manually install the network-manager package, but don't know where to begin (all I see are options for i386 and amd64).

My last effort (admittedly above my limited experience) was:

> sudo openvpn IPredator-Ubuntu-Password.ovpn

It returned

> Thu Aug  8 22:31:04 2013 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Thu Aug  8 22:31:04 2013 Cannot load CA certificate file /path/to/openvpn/config/keys/IPredator.se.ca.crt path (null) (SSL_CTX_load_verify_locations): error:02001002:system library:fopen:No such file or directory: error:2006D080:BIO routines:BIO_new_file:no such file: error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib
Thu Aug  8 22:31:04 2013 Exiting

So (again, idk what I'm doing here) I edited the .ovpn to include accurate paths to CA certificate and ta.key files. Again tried:

> sudo openvpn IPredator-Ubuntu-Password.ovpn

Got a bunch of output. Not sure if I should include it here. Ended up with a Swedish IP and thought everything was gravy until I checked for DNS leaks. Found multiple DNS servers, all from my ISP : (

I've been searching two weeks for an answer but clearly am not asking Google the right questions. Feels like I'm missing something simple.

Any help is greatly appreciated. Much love to the community!

---

### Post by oldrocker99 on 2013-08-15
You might be best served by downloading the source code and compiling it yourself. You need the build-essential package to do that. There are some source packages available here: [https://launchpad.net/ubuntu/+source/openvpn](https://launchpad.net/ubuntu/+source/openvpn).

For unknown reasons, there are no openvpn packages in the Ubuntu repositories. Download the openvpn_2.2.1.orig.tar.gz archive, then extract it and CD to that directory. Then:

$ ./configure
(If there are missing dependencies, make note of the missing libraries, then install the libwhatever-**dev** packages)
$ make
$ sudo make install

And good luck.

---

### Post by andy15 on 2013-08-16
In short: Success! Thank you so very much, oldrocker99 :D

For others who may encounter the same problem: When ./configure-ing, I had a problem with "lzo headers". So I just did
> ./configure –disable-lzo

Then there was some kind of crypto headers issue. So I did
> sudo apt-get install libcurl4-openssl-dev

Not sure I did it correctly, but at least the make/make install was then able to complete. Idk why, but after that I was able to successfully do
> sudo apt-get install network-manager-openvpn-gnome

No longer got
> E: Package 'network-manager-openvpn' has no installation candidate

(If anyone cares to explain, I'd love to know why compiling from source would effect my ability to apt-get a package. I always thought the two actions were, like, separate) 

So from there, I could then use network manager to add my openvpn connection.

This may not seem like a big deal, but I've never asked for help online before. Suddenly I feel better about the world and less newbish. Thanks again, oldrocker99.

---

### Post by oldrocker99 on 2013-08-16
You are MOST welcome! You asked a question, and you got a useful answer. **This** is what Ubuntu Forums is for!

And don't quit asking questions, and offering help when you can. Welcome to the community!

Oh, yes: edit your post to add [SOLVED] to it; that's part of the etiquette here.

---

