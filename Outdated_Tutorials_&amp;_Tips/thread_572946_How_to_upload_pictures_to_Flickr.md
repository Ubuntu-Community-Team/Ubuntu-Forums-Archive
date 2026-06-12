---
title: "How to: upload pictures to Flickr"
date: 2007-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by michael37 on 2007-10-11
Say you want to upload pictures to Flickr and you are using Ubuntu.  You know how to do it on Windows, but Flickr Uploader is Windows only.

Well, don't despair!  There is a software which allows bulk uploads of pictures from your hard drive to Flickr service.

1.  If you don't have Java installed, install package sun-java6-jre.
For example,
```

sudo apt-get install sun-java6-jre

```
2.  Go to [http://juploadr.org/download_linux.php](http://juploadr.org/download_linux.php)
3.  Download the file jUploadr-1.1.2-linuxGTK-i386.tar.gz and open it in Archive Manager.
4.  Unarchive into your home directory:  
Right click on  jUploadr-1.1.2-linuxGTK-i386 and select Extract
Click on your name (should be the third icon down on the left panel)
Click on Extract.
5.  Open a terminal and run
```

exec ~/jUploadr-1.1.2-linuxGTK-i386/jUploadr

```
A window opens up with an offer to "drag and drop photos"
6. Select Edit->Accounts->Flickr account
A new Web browser window will open, or a new Firefox tab will open with Flickr login and/or instructions.  Log into your Flickr account and follow the instructions to give jUploadr authorization to upload to Flickr.
7. Drag and drop pictures and click on Upload

This is fun, huh? :)
6.

---

### Post by Fuzz on 2007-12-29
is there any way to make this launch from a launcher?

---

### Post by burneverything on 2008-03-12
There is a Flikr Uploader available in the "add/remove applications" in the graphics section, It's a python script so no need for java for it to work.

Tip for it:
if you have multiple accounts you can delete the login to get to another account by deleting the content of:
~/.flickr
with the uploader closed and it will ask you to login again next time you start it.

---

### Post by atoc on 2008-03-12
[FlickrEdit]("http://sunkencity.org/flickredit")

---

### Post by Tobywuk on 2009-06-03
I have also been looking for a flickr uploader to use with ubuntu. I tried the jUploader recommended but I had some problems getting it to run - it would run the bash script but would do nothing. The terminal output would flash and close to quickly for me to read it.

I did a search for 'flickr' in the package manager and there is an upload program called 'postr' which I believe is the python unloader mentioned above. Installed and works great. Also has a built in option to send your images to a group wich the flickr uploader for windows/osx does not have! great stuff :)

The Picasa port for linux also seems to be faster and work better than the windows version, good times.

---

### Post by woodorw on 2009-10-01
postr is great&#65292;i have installed it and it works very well:guitar:

---

### Post by e.m.fields on 2010-01-31
I've installed jUploadr on Ubuntu Jaunty and Karmic 32 and 64 bit with no success.

I click upload, and it simply doesn't do anything.  USELESS and very frustrating. 

Flickr needs to get Flickr uploader working for Linux, or open up FTP access.

!@#%

- PS: Postr seems to be working, though there's no progress bar while uploading - and had the same problem! Nothing happened when clicking upload button.  However, got it to work after clicking Upload from the File menu. WTF??

---

### Post by davebgimp on 2010-03-01
I have the same issue and I notice on the jUploadr main page that as of 1.2 "*[jUploadr now requires Java 1.5 (java 5.0)]("http://juploadr.org/2007/07/12/say-hello-to-juploadr-12/")"*. I can tell you that running 1.6+, I have the same issue. Everything works, but upload.

> **e.m.fields said:**
> I've installed jUploadr on Ubuntu Jaunty and Karmic 32 and 64 bit with no success.

I click upload, and it simply doesn't do anything.  USELESS and very frustrating. 

Flickr needs to get Flickr uploader working for Linux, or open up FTP access.

!@#%

- PS: Postr seems to be working, though there's no progress bar while uploading - and had the same problem! Nothing happened when clicking upload button.  However, got it to work after clicking Upload from the File menu. WTF??

---

### Post by swaprava on 2010-04-11
> **woodorw said:**
> postr is great&#65292;i have installed it and it works very well:guitar:
  
But it seems there is a problem with postr in Ubuntu Karmic. I installed it but it gives the following error with traceback:

```
/usr/lib/pymodules/python2.6/postr/flickrest.py:18: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import logging, md5, os, mimetools, urllib
Traceback (most recent call last):
  File "/usr/bin/postr", line 34, in <module>
    p = postr.Postr()
  File "/usr/lib/pymodules/python2.6/postr/postr.py", line 162, in __init__
    self.flickr.authenticate_1().addCallbacks(self.auth_open_url, self.twisted_error)
  File "/usr/lib/pymodules/python2.6/postr/flickrest.py", line 274, in authenticate_1
    return self.__get_frob()
  File "/usr/lib/pymodules/python2.6/postr/flickrest.py", line 240, in __get_frob
    return self.auth_getFrob().addCallback(gotFrob)
  File "/usr/lib/pymodules/python2.6/postr/flickrest.py", line 126, in proxy
    return self.__call(method, kwargs).addCallback(self.__cb, method)
  File "/usr/lib/pymodules/python2.6/postr/flickrest.py", line 108, in __call
    postdata=urllib.urlencode(kwargs))
  File "/usr/lib/pymodules/python2.6/postr/proxyclient.py", line 400, in getPage
    scheme, host, port, path = _parse(proxy)
  File "/usr/lib/pymodules/python2.6/postr/proxyclient.py", line 384, in _parse
    host, port = host.split(':')
ValueError: too many values to unpack

```

Any workarounds? :confused:

---

### Post by tzoom84 on 2010-11-28
I'm looking for a solution that "auto-syncs" with Flickr. For example, I provide a list of photo/video directories, and in the background (or as a daily cronjob more likely) it looks for changes to that directory. If a change occurs, it syncs/uploads to Flickr automatically. 

Will any current software do that (FlickrEdit, postr)? Or is my best best just writing a bash script that runs daily?

---

### Post by quinnanya on 2011-03-02
I highly recommend [Frogr]("http://live.gnome.org/Frogr") for uploading to Ubuntu. Its 0.4 release, which came out just a month ago, works just as reliably and well as the official Flickr Uploadr for Mac and Windows. It also includes tag auto-completion. 

I tried Postr, but it kept crashing on all my machines; Frogr has been both stable and easy-to-use ever since I've installed it.

---

### Post by tzoom84 on 2011-03-02
Frogr seems to only have GUI interface from what I see. Still looking for a good auto-mount like solution.

---

### Post by quinnanya on 2011-03-03
> **tzoom84 said:**
> Still looking for a good auto-mount like solution.

Have you tried [Conduit]("https://launchpad.net/ubuntu/+source/conduit")? It sounds like it might do what you need. I was able to install and configure it on Maverick without a problem, but I stopped short of attempting a sync, since I don't have a directory that has all my photos in it and didn't want to risk deleting anything.

---

### Post by tzoom84 on 2011-03-03
hmm. conduit seems pretty slick and easy to use. the big downside for me is I can't find a way to have it run recursively on a pictures directory. 

For example I may have a folder /media/pictures, with dozens of subdirectories from different events. When I create a sync in conduit, it forces me to select an album. Then all the files are uploaded flatly to that one directory. Perhaps I'm missing something or there's a workaround ...

---

### Post by quinnanya on 2011-03-04
Unfortunately, from what I can tell, it looks like you'd have to set up each folder separately in Conduit to get the effect you're looking for. The folks who provide support for Conduit might have some ideas for how to automate it; the [Conduit page]("http://live.gnome.org/Conduit") on GNOME live has info about the IRC channel, mailing list, Google Group, etc.

---

### Post by tzoom84 on 2011-03-04
Thanks. I contacted the devs and they said it USED to work and that they'll look into it

---

