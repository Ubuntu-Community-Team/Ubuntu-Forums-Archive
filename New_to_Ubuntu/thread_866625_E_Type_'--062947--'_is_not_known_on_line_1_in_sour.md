---
title: "E: Type '--06:29:47--' is not known on line 1 in source list /etc/apt/sources.list.d/"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by thevoodooproject on 2008-07-22
i cannot use synaptics update manager anymore. error is shown as in the title.

the contents of my medibuntu.list is as below. please help.
thanx a ton. i am loving Ubuntu.


--06:29:47--  [http://www.medibuntu.org/sources.list.d/dapper.list](http://www.medibuntu.org/sources.list.d/dapper.list)
           => `dapper.list.1'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to [www.medibuntu.org|87.98.242.10|:80](www.medibuntu.org|87.98.242.10|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 229 [text/plain]

    0K                                                       100%    7.28 MB/s

06:29:48 (7.28 MB/s) - `dapper.list.1' saved [229/229]

---

### Post by Dark_Stang on 2008-07-22
Are you running dapper? Check out this thread...
[http://ubuntuforums.org/showthread.php?t=185758](http://ubuntuforums.org/showthread.php?t=185758)

---

### Post by wolfen69 on 2008-07-22
then do```
cat /etc/apt/sources.list
``` and show us the output.

---

### Post by RomeReactor on 2008-07-22
> **thevoodooproject said:**
> i cannot use synaptics update manager anymore. error is shown as in the title.

the contents of my medibuntu.list is as below. please help.
thanx a ton. i am loving Ubuntu.


--06:29:47--  [http://www.medibuntu.org/sources.list.d/dapper.list](http://www.medibuntu.org/sources.list.d/dapper.list)
           => `dapper.list.1'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to [www.medibuntu.org|87.98.242.10|:80](www.medibuntu.org|87.98.242.10|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 229 [text/plain]

    0K                                                       100%    7.28 MB/s

06:29:48 (7.28 MB/s) - `dapper.list.1' saved [229/229]

Hi. I'm guessing you somehow piped the output of wget to the file. The actual contents of the file should be:
```
## Medibuntu - Ubuntu 6.06 LTS "dapper drake"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ dapper free non-free
#deb-src http://packages.medibuntu.org/ dapper free non-free
```

You can open the file in gEdit:
```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```
erase what's there now and paste the correct contents. Save the file, close the text editor, and run this:
```
sudo aptitude update
```
to refresh the repository information; afterwards you should be able to use Synaptic.

---

