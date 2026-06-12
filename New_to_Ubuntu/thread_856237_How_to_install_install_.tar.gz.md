---
title: "How to install install .tar.gz ???"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by SeriousTom on 2008-07-11
I'm trying to get my Soundblaster X-Fi to work. I am using this guide [http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2) and am on the Addendum : Volume Control Patch
Trying to install gstreamer-ossv4-amd64.tar.gz I've unpacked on the Desktop :-({|=and I get this : ```
serioustom@serioustom-desktop:~$ gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
gzip: /usr/lib/gstreamer-0.10/libgstossaudio.so.gz: Permission denied
serioustom@serioustom-desktop:~$ mv libgstossaudio.so /usr/lib/gstreamer-0.10/sudo
mv: cannot stat `libgstossaudio.so': No such file or directory
serioustom@serioustom-desktop:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
serioustom@serioustom-desktop:~$ sudo -i gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
/bin/gzip: /bin/gzip: cannot execute binary file
serioustom@serioustom-desktop:~$ mv libgstossaudio.so /usr/lib/gstreamer-0.10/

```

---

### Post by Troll_the_Great on 2008-07-11
You downloaded a source file.It is pretty difficult for a beginner to install it but have a look at this links:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
You should look in the package for a readme file or something.
Hope this helps.
Cheers!

---

### Post by aimpau on 2008-07-11
Remember:

1. When installing a program, go to Applications>>>System>>>Add/Remove
2. Another way is through Synaptic
3. To make sure you get the updated list of available programs open up a terminal and type:
```

sudo apt-get update

```

---

