---
title: "Unable to install tor"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by Gopi26 on 2013-06-10
Hello guys

I am new to ubuntu and I am trying to install tor. (the tor browser to be specific)
I am using ubuntu 12.04

So far I have done the following.
I installed the tor browser bundle from: 'https://www.torproject.org/download/download'
Added 'http://deb.torproject.org/torproject.org precise main' to my source list and updated.

I also did
$ sudo apt-get install tor
$ sudo apt-get install vidalia

But when I try to execute the start-tor-browser file in the downloaded folder, I get
$ ./start-tor-browser 

Launching Tor Browser Bundle for Linux in /home/gsn/Downloads/tor-browser_en-US
./App/vidalia: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
Vidalia exited abnormally.  Exit code: 127

but when I used 
$ sudo find / -iname 'libstdc*'

I found 
/usr/share/doc/libstdc++6
/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
/usr/lib/x86_64-linux-gnu/libstdc++.so.6
/var/lib/dpkg/info/libstdc++6:amd64.postinst
/var/lib/dpkg/info/libstdc++6:amd64.list
/var/lib/dpkg/info/libstdc++6:amd64.md5sums
/var/lib/dpkg/info/libstdc++6:amd64.symbols
/var/lib/dpkg/info/libstdc++6:amd64.shlibs
/var/lib/dpkg/info/libstdc++6:amd64.postrm

So what should I do?

Thanks in advance.

---

### Post by Lars Noodén on 2013-06-10
You don't need or want Tor from the repository if you have installed it via the Tor Browser Bundle.  The Bundle includes pre-configured Tor so if you also installed it from the repository, you can and should uninstall it.  

About the error trying to run Tor from the bundle, are you sure that it downloaded properly?  You might try getting it again to be sure.

---

### Post by d4m1r on 2013-06-10
Go to the Tor website, download the "browser bundle" for linux (32 or 64 bit depending on your OS). It will be a tar.gz file which you can extract using the default archiving application. Put the TOR folder somewhere (home directory?) and just launch the "start-tor" script....

Names might not be exact as I'm working from memory here....There is no manually instead necessary however and no need to use the command line either.

---

### Post by Gopi26 on 2013-06-11
Thanks

When I downloaded the bundle again it worked.
Can you please tell me how to uninstall the repositories?

---

### Post by mexican.ades on 2013-10-27
Hi,

I'm an Ubuntu newbie and suffering the exact same problem with the libstdc error as detailed above. Tried re-installing Tor a couple of times though and still doesn't work. 

Any ideas? 

Thanks

---

### Post by Lars Noodén on 2013-10-27
If you are planning on just using it through the browser, then the Tor Browser Bundle is the easier option.

---

### Post by mexican.ades on 2013-10-27
That is trying to run it through the browser bundle. The preceding steps of adding tor to the source list etc. are the directions from the tor website.

---

### Post by firedoglake on 2013-11-11
I've downloaded the browser bundle several times, and each time I get an error message of "no application avalilable to open" Vidalia or Tor.  Any suggestions?

---

### Post by Lars Noodén on 2013-11-11
Welcome.

To use the TBB you have to 'untar' it after it is downloaded.  You'll need to open a terminal and then run tar on the file that you downloaded.

```

cd ~/Downloads/
ls *.tar.gz
tar zxf tor-browser-gnu-linux-x86_64-2.3.25-14-dev-en-US.tar.gz

```

(The unpacking above only needs to be done once per download.  The actual filename will vary depending on what you downloaded.  You'll have to do it again when it is time to update TBB.)

That will give you a folder "tor-browser_en-US" or something like that which you can move where you want.  Inside that, there is a script "start-tor-browser" which you can launch to start the TBB.  

The Dash does not seem to search local folders for apps, not even ~/bin/ so you'll have to make your own shortcut icon if you want an easy way to launch it.  Otherwise you can always launch it from the terminal.

---

