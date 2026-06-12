---
title: "java install error"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by davies86 on 2008-11-10
ive recently downloaded ubuntu as i am required to do things for my uni course that can only run on a linux based operating system. I dual boot with windows xp. I am trying to install java on to linux. Its a bin file which i have tried to install i can get opening it and starting to install java then i get this error message

Unpacking...
Checksumming...
Extracting...
./jdk-6-linux-i586.bin: 342: ./install.sfx.9006: not found
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.
 
And now i have no idea what to do can anybody help?

so far i have put...

sudo chmod +x *.bin
./jdk-6u10-linux-i586.bin

many thanks in advance

Chris

---

### Post by w4ett on 2008-11-10
There is a far easier way to install Java...the packages are located in the Multiverse repository.  Use Synaptic to install Or, from the terminal:
> 
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by Leggs79 on 2009-04-14
I continue to get this error when attempting to install Java via the sudo command listed in the previous post.


Error: Could not open input file: /usr/java/jrel.6.0.12/lib/rt.packjsse.jar...
Error: Could not open input file: /usr/java/jrel.6.0.12/lib/jsse.packcharsets.jar...
Error: Could not open input file: /usr/java/jrel.6.0.12/lib/charsets.packlocaledata.jar...
Error: Could not open input file: /usr/java/jrel.6.0.12/lib/ext/localedata.packplugin.jar...
Error: Could not open input file: /usr/java/jrel.6.0.12/lib/plugin.packjavaws.jar...
Error: Could not open input file: /usr/java/jrel.6.0.12/lib/javaws.packdeploy.jar...
Error: Could not open input file: /usr/java/jrel.6.0.12/lib/deploy.pack
[: 927:  ==: unexpected operator
[: 927:  ==: unexpected operator
dpkg: error processing jre (--configure):
subprocess post-installation script returned error exit status 156
Setting up sun-java6-fonts (6-10-0ubuntu2) ...
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-lucida

Erros were encountered while processing:
 jre
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any suggestions? When asked to report this error to Ubuntu I get the message that this is not a genuine Ubuntu package and the error cannot be reported.

---

