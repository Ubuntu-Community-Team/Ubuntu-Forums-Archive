---
title: "Graphics driver for ubuntu"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by krstekrste on 2011-11-15
I installed 11 04 and I have a graphics driver named like this

"vga palit gf pci-e 6200 le mb 64 bit ddr"

but I do not know how to install a driver for it.

I my system info it says Graphics driver Unknown and specifications standard...

Thanks

---

### Post by khelben1979 on 2011-11-15
There are different methods for fixing this issue. The recommended one if you're less experienced Ubuntu user is to [start Ubuntu Software Center]("http://en.wikipedia.org/wiki/Ubuntu_Software_Center"). Make a search for nVidia in there. Now choose the nVidia driver where you can see in the description text that it works for your graphics card/chip.

The second option is to enter [www.nvidia.com](www.nvidia.com) and search for an nVidia driver [there]("http://www.nvidia.com/Download/index.aspx?lang=en-us"), choose your model from the list menu and pick the right one.

The second option here is a bit trickier, since you need to use the sudo command to execute the shell script which starts the installer. It's not too hard, but I would suggest using the first method, since it's also a graphics driver which have been tested and approved by the Ubuntu distribution, only for maximum performance you should do otherwise.

---

### Post by grahammechanical on 2011-11-15
Do not see problems where there are none.

I do not remember seeing System Info in 11.04. It first appeared in 11.10. My System Info also says "Driver Unknown" and "Experience Standard." And it has done so since I first installed 11.10 alpha 2 some months ago.

I actually have an Nvidia driver that I installed through Additional Drivers.

The key question here, is: Can you run Unity 3D? When you log in is it Ubuntu that you load or is it Ubuntu 2D? What does the Additional Drivers utility say about your video driver?

Clearly the development of the System Info utility is not yet complete. At least it now says Ubuntu 11.10 and not Ubuntu 11.04 as it did four months ago and it is able to give the size of the disk, which it could not do.

Regards.

---

### Post by 3rdalbum on 2011-11-15
Click on the Ubuntu logo near the top-left corner. Type 'drivers' and the first result will be a program called Additional Drivers. Click on it and you'll be offered an appropriate download for your card. After it's finished downloading and installing the driver, reboot.

---

### Post by ritchiewall on 2011-11-28
> **3rdalbum said:**
> Click on the Ubuntu logo near the top-left corner. Type 'drivers' and the first result will be a program called Additional Drivers. Click on it and you'll be offered an appropriate download for your card. After it's finished downloading and installing the driver, reboot.

Hey.. I am having a similar problem.. when I look at additional drivers there is no option at all for me and also when I have looked at my system it says my graphics card is unknown but looking through terminal it shows as VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller. Any ideas as to how to update the driver?

I am hoping this will speed the system as upgrading from 11.04 to 11.10 has killed it slowly...

Thanks!

---

### Post by crazy bird on 2011-11-28
try this:
- Open a terminal and type in: **LSPCI**.

In the output look voor a line which contains this: VGA compatible controller:
Whatever the output is after this, that is the video-card you currently have in your system. Is it a Nvidia video-card? Then type this is the temrinal :**sudo apt-get install nvidia-current**.

When i google on this: vga palit gf pci-e 6200 le mb 64 bit ddr, i realy don't get any results, except your post..

---

### Post by ritchiewall on 2011-11-29
Hi there Crazy Bird

No, my video card is the Intel N10... and it doesn't appear to be any more drivers for it.

---

### Post by crazy bird on 2011-11-29
Okay, check in synaptic if you have this installed: **xserver-xorg-video-intel**.

If you have this installed, then maybe the xserver-xorg-intel driver needs to be updated.

Execute the following commands in a terminal (the terminal does not have to be closed after each command):

**sudo add-apt-repository [B]ppa:glasen/intel-drive**[/B]

**sudo apt-get update**

**sudo apt-get upgrade**

Then just to be sure, reboot your system, what happens after the reboot?

---

### Post by ritchiewall on 2011-11-29
Hey, thanks for messaging me!

This is what happens:


ritchiewall@ritchiewall-EB1007:~$ sudo add-apt-repository ppa:glasen/intel-drive[sudo] password for ritchiewall: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 88, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 65, in get_ppa_info_from_lp
    lp_page = urlopen(req).read()
  File "/usr/lib/python2.7/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 400, in open
    response = meth(req, response)
  File "/usr/lib/python2.7/urllib2.py", line 513, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.7/urllib2.py", line 432, in error
    result = self._call_chain(*args)
  File "/usr/lib/python2.7/urllib2.py", line 372, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 619, in http_error_302
    return self.parent.open(new, timeout=req.timeout)
  File "/usr/lib/python2.7/urllib2.py", line 400, in open
    response = meth(req, response)
  File "/usr/lib/python2.7/urllib2.py", line 513, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.7/urllib2.py", line 438, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.7/urllib2.py", line 372, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 521, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 404: Not Found


However I did check synaptic and indeed that driver was there. There is an option to re-install but not upgrade when I right click on them. The above means nothing to me though.

---

