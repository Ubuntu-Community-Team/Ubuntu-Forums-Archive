---
title: "Terminal freezes and times out while trying to &quot;add-apt-repository&quot;"
date: 2022-08-18
forum: New to Ubuntu
---

### Post by pcrigotto on 2022-08-18
While trying to add a repository on a new Ubuntu installation I get a timeout error after a while, and the repository isn't added. I installed all the default sources when asked. This is the message I get:

```

$ sudo add-apt-repository ppa:danielrichter2007/grub-customizer
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 364, in <module>
    sys.exit(0 if addaptrepo.main() else 1)
  File "/usr/bin/add-apt-repository", line 347, in main
    shortcut = handler(source, **shortcut_params)
  File "/usr/lib/python3/dist-packages/softwareproperties/shortcuts.py", line 40, in shortcut_handler
    return handler(shortcut, **kwargs)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 82, in __init__
    if self.lpppa.publish_debug_symbols:
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 120, in lpppa
    self._lpppa = self.lpteam.getPPAByName(name=self.ppaname)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in lpteam
    self._lpteam = self.lp.people(self.teamname)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 98, in lp
    self._lp = login_func("%s.%s" % (self.__module__, self.__class__.__name__),
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 494, in login_anonymously
    return cls(
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 230, in __init__
    super(Launchpad, self).__init__(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/resource.py", line 472, in __init__
    self._wadl = self._browser.get_wadl_application(self._root_uri)
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 447, in get_wadl_application
    response, content = self._request(url, media_type=wadl_type)
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 389, in _request
    response, content = self._request_and_retry(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 359, in _request_and_retry
    response, content = self._connection.request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1725, in request
    (response, content) = self._request(
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 144, in _request
    response, content = super(LaunchpadOAuthAwareHttp, self)._request(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 184, in _request
    return super(RestfulHttp, self)._request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1441, in _request
    (response, content) = self._conn_request(conn, request_uri, method, body, headers)
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1363, in _conn_request
    conn.connect()
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1153, in connect
    sock.connect((self.host, self.port))
TimeoutError: [Errno 110] Connection timed out

```

What can be done to help fix this? I tried adding the repository to the sources.list file but I couldn't find what the link and type should be.

---

### Post by grahammechanical on 2022-08-18
If we are using Ubuntu 20.04 we can install grub-customizer from the Ubuntu Software application. But when using Ubuntu 22.04 grub-customizer is not in Ubuntu Software. So, we have to add a Personal Package Archive (PPA) to our list of software sources or repositories. There are two ways to do this. We can open Software & Updates>Other Software and click Add. Or, add the repository by using the terminal.

If we are using Software & Updates>Other Software - Add then this is the address we must put into the panel:

> deb [https://ppa.launchpadcontent.net/danielrichter2007/grub-customizer/ubuntu/](https://ppa.launchpadcontent.net/danielrichter2007/grub-customizer/ubuntu/) jammy main

It is also the address we want to have in our etc/apt/sources.list file. You are using the terminal. The word "sudo" should prompt a request for your password. Yet the printout you have provided does not show this request. Why? I do not know.

This link might help you.

[https://itsfoss.com/install-grub-customizer-ubuntu/](https://itsfoss.com/install-grub-customizer-ubuntu/)

Regards

---

### Post by pcrigotto on 2022-08-18
Adding that line to the Software & Updates page worked, thank you.

The terminal didn't request my password because that was my second attempt at running the command. It prompted me the first time.

The issue has been solved and the software has been properly installed.

---

### Post by ActionParsnip on 2022-08-19
Do you have a dual boot and want Windows to be default, by any chance?

---

### Post by pcrigotto on 2022-08-22
Yes, that would be nice. I had to unmount my Windows drive when installing Ubuntu because the installation was freezing at one point, and now the boot loader doesn't ask me which system I want to boot. I have to select the boot drive manually by pressing F12 on the boot screen. Should I make a new thread about this?

---

### Post by ajgreeny on 2022-08-22
Double check if you have the package ***software-properties-common*** installed with command which should show output similar to 
```
ii  software-properties-common 0.99.22.3    all          manage the repositories that you install software from (common)
```
If you see something else let us know or simply run command ```
sudo apt install  software-properties-common
```

---

### Post by pcrigotto on 2022-08-22
I do have the software-properties-common package installed. Running "apt list --installed" gives me this line:
```
software-properties-common/jammy-updates,jammy-updates,now 0.99.22.3 all [installed]

```
I already tried running "sudo update-grub", and changing a configuration so the os-prober would detect other bootable partitions, but no luck. That might have something to do with the fact that my Windows boot loader is on a different drive from the actual OS, due to some weirdness during the Windows installation. I'm not sure.

---

