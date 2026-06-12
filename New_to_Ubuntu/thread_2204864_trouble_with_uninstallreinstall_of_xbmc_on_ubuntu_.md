---
title: "trouble with uninstall/reinstall of xbmc on ubuntu 13.10"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by ccdavis77 on 2014-02-10
Hello--
Run into a conundrum and can't seem to figure this out...

Wanted to revert to the currently beta stable release of XBMC 12.3 from 13.0 alpha I am currently running until the latter is approved for beta status and a bit more stable.  However, I am totally unable.  

I have deleted userdata folder and also the parent xbmc folder as directed first, followed by the terminal commands:

sudo apt-get remove xbmc

sudo apt-get autoremove 

sudo apt-get purge xbmc

The above seems to delete XBMC from the system; however, when I type the following which SHOULD install the latest stable release which should be 12.3 (frodo) from my understanding...

sudo apt-get install python-software-properties pkg-config
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install xbmc

The XBMC version is still 13.0 alpha when I reboot.

What am I doing wrong??

thanks for any help!!!

---

### Post by monkeybrain20122 on 2014-02-10
Well that is because you installed xbmc 13.0 from the unstable ppa which is still on your sources.list, therefore xbmc 13.0 is the highest version in your repositories (higher than the version in the stable ppa you just added) so it will be installed if you install xbmc. You have to first remove the unstable ppa

```
sudo apt-add-repository --remove ppa:team-xbmc/unstable
sudo apt-get update
sudo apt-get install xbmc
```

I am assuming that you got 13.0 alpha from the xbmc unstable ppa, if you got it somewhere else just change the first line to the appropriate ppa.

BTW, if you have installed synaptic you can  check, add/remove, enable/disable ppas with just a few clicks (Settings > Repositories > Other Software)

---

### Post by ccdavis77 on 2014-02-10
Cool,looks good so far. Thanks! Do you know if I can copy back in my userdata folder I was using from the nightly build into the 12.3 frodo xbmc and have it work, addons folder too?

---

### Post by monkeybrain20122 on 2014-02-10
Those folders are in your /home directory. As long as the two versions should use the same data and configuration files so normally you don't need to change anything. Since you said you have "deleted" them that depends on what you mean. If they are in the trash folder then you can simply restore them. If you really deleted them then they are gone. In the future if you want to experiment with deleting those files (they get regenerated when you start the program) Instead of deleting them you can simply rename them to something else,--like 'foo' to 'foo-old',-- if restarting the program and everything works then you can delete them, otherwise delete the new folders generated since the renaming, and then rename your old folders to their old names.

---

### Post by ccdavis77 on 2014-02-11
Okay, a million thanks again...you got me back up and running!!!  I backed up the userdata folder on another hard drive and then deleted it along with the "xbmc" parent folder because I had read that it was necessary to do so to reinstall frodo 12.x when gotham 13.0 was in place. Basically just rebuilt everything in my userdata folder manually because I wasn't sure whether I could just re-add that folder to frodo build and have it not screw things up...

---

