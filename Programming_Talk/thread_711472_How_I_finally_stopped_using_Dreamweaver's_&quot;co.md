---
title: "How I finally stopped using Dreamweaver's &quot;code view&quot;"
date: 2008-02-29
forum: Programming Talk
---

### Post by lotsofish on 2008-02-29
I like Dreamweaver. It's a nice app and it's what I use at work under Windoze. (I don't use the WYSIWYG editor, almost never, because I like my own code better, plus I am doing a lot of PHP development.)

Since I switched to Ubuntu on my home computer back in November, I've tried several different web IDE's but as you know nothing really competes with what Dreamweaver has to offer in terms of site management, code completion, etc. 

I tried:
Quanta - It's buggy and clumsy, but the FTP site management is ok if you can get it configured right.
Kompozer - Not really what I was looking for.
Gedit+gFTP - Works, but switching back and forth between programs to upload is unintuitive.
GPHPEdit - Doesn't really do anything that GEdit doesn't do and less.
Bluefish - This is a pretty good editor actually. Will work on remote files and remote projects if the settings are right, but still not exactly what I wanted.
Komodo Edit - While I liked the program, I didn't give it enough of a trial the first time I tried it. I was thinking the IDE (big bucks version) might give me what I was looking for but I wasn't looking for a big bucks solution so I never tried the trial period. Wasn't super impressed with the FTP project support again.

For the past few months I have been using Dreamweaver with Wine. It does work, but running under Wine isn't perfect or what I really wanted to be doing.

Well, I've finally found my solution and it is Open Komodo + curlftpfs!

Open Komodo is basically Komodo Edit, but they open sourced it just a couple months ago. Right now they are on version 4.3 beta2. You can install it by downloading the nightly build from [http://openkomodo.com](http://openkomodo.com) . I had no problems installing the linux-libcpp6-x86 version. (I do have the 32 bit libraries installed on my AMD64 install.)

I really like Komodo the more I use it. It is based on Mozilla code. I've only used it for PHP/HTML/CSS so far, but the color coding and auto completion support is really good. Stability is great, I've never had a crash.

The other part of my solution is to install curlftpfs.
```

sudo apt-get install curlftpfs

```

What this will allow you to do is mount an ftp connection in linux. So you can set up a directory like /home/lotsofish/ftp/mysite and access that directory just like any other, only the files inside will automatically be transferred to and from your ftp account.

The meaning of this? You can set up a new project in Komodo, save the project file (.kpf) and all your FTP site gets added automatically to your project. You can work on your site files and when you save them they automatically get uploaded to your site.

Komodo does have built in FTP and it does work well, but right now it doesn't work the way I like it. You have to save the .kpf file in a blank directory, add a new "folder" to your project and import the remote files. If you use the built in Komodo ftp manager there is no way to copy files from the FTP server to your hard drive. If you use curlftpfs you can use your file manger (Nautilus) to copy the files.


--
Side note: The way I have been working lately.... 
For new sites I create I am creating them by saving them on the hard drive and using Xampp to preview in the browser.I will copy over the changed files through Nautilus on my curlftpfs mounts when I have a good update to push.

For existing sites where I don't have all the source files on my hard drive, I set up the Komodo project directly to the curlftpfs mount.


Komodo Snapdragon.
There is talk about forking the Open Komodo project into a new project called Komodo Snapdragon. Since it is based on Mozilla, they are talking about including some kind of Firefox display mode. Not necessarily WYGIWYG, more like update the HTML or CSS source, automatically see what happens in Firefox. Similar to what you get when you have the Firebug extension installed and edit the CSS. It sounds cool, but I have no idea how long into the future that will be.

---

### Post by scruff on 2008-02-29
Cheers! I have been using Komodo ("the big bucks version") for a couple of years now and really dig it. I use it for Perl/Python development at work. I did begin using VIM, but when you get into really large projects Komodo is a nice IDE for the task :)

---

