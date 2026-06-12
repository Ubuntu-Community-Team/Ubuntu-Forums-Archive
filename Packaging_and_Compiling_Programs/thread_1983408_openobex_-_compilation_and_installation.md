---
title: "openobex - compilation and installation"
date: 2012-05-20
forum: Packaging and Compiling Programs
---

### Post by gr@ss_h@pper on 2012-05-20
Hi,

I am trying to compile and install openobex source. I am new to this (Both to the obex and cmake way of compilation). My intention is to add some logs and debug obex-client (ubuntu 10.04 has it in /usr/lib/obexd/obex-client).

I got the sources from openobex git. Then I followed the compilation steps provided in INSTALL.txt. I am able to compile it successfully.
(With the exception that in order to compile successfully, I had to replace bt_addr_t* to void* at a few places in lib/obex.c other wise I was getting some syntax errors. Hope this won't harm).

Now to install it the instructions are:
<snip>
[COLOR=RoyalBlue]3 Installation
==============

Then you can install the files by running the "install" make target.
When using CMake, the "package" make target will create a compressed tarball with the binaries.[/COLOR]
</snip>

I ran "install <path to my cmake binary> <target-name>" and it's creating a binary with the given target-name. Though I am not sure what this binary is. 
Also libopenobex.so.1.6 is getting created in openobex/mainline/build/lib directory.

[COLOR=DarkGreen]Query1: How can I make obex-client binary that ubuntu 10.04 is using in /usr/lib/obexd/

Query2: What is this binary that I got? I mean, is it the obex-client binary? Am I trying to create the final binary correctly?[/COLOR]

---

