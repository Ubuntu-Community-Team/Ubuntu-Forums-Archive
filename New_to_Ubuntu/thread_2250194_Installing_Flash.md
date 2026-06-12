---
title: "Installing Flash"
date: 2014-10-27
forum: New to Ubuntu
---

### Post by flex567 on 2014-10-27
I have this instructions for installing flash: 

```
Installation instructions
-------------------------

Installing using the plugin tar.gz:
    o Unpack the plugin tar.gz and copy the files to the appropriate location.  
    o Save the plugin tar.gz locally and note the location the file was saved to.
    o Launch terminal and change directories to the location the file was saved to.
    o Unpack the tar.gz file.  Once unpacked you will see the following:
        + libflashplayer.so
        + /usr
    o Identify the location of the browser plugins directory, based on your Linux distribution and Firefox version
    o Copy libflashplayer.so to the appropriate browser plugins directory.  At the prompt type:
        + cp libflashlayer.so <BrowserPluginsLocation>
    o Copy the Flash Player Local Settings configurations files to the /usr directory.  At the prompt type:
        + sudo cp -r usr/* /usr

```

I don't know where is the location of the browser plugin directory ?

---

### Post by Bucky Ball on 2014-10-27
What you do is install flashplugin-installer from the repos (Software Centre).

Make sure you have the multiverse repository enabled in your Software Sources and install ubuntu-restricted-extras from Software Centre. You don't need to manually install flash.

After all this, do an update and reboot.

(PS: Installing ubuntu-restricted-extras may drag in flash and that's all you'll need to do, don't remember off-hand. Try that first.)

---

### Post by flex567 on 2014-10-27
Where exactly can I enble multiverse repository because I didn't find this setting?

---

### Post by Bucky Ball on 2014-10-27
In Ubuntu I think it is in Software Sources or something like that in the menu. I don't use Unity so not sure. You should be able to find it, though. One way is to open Software Updater>Settings in the bottom left corner and you'll find it on the first tab there.

Install ubuntu-restricted-extras then.

---

### Post by nerdtron on 2014-10-27
Isn't ubuntu-restricted-extras available by default. I don't recall adding/activating repositories on my last install of Ubuntu. If I remember correctly just searched ubuntu restricted extras on the software center and installed it.

---

### Post by Bucky Ball on 2014-10-27
> **nerdtron said:**
> Isn't ubuntu-restricted-extras available by default. I don't recall adding/activating repositories on my last install of Ubuntu. If I remember correctly just searched ubuntu restricted extras on the software center and installed it.

Should do it. Mentioned earlier. ;)

Give it a go.

---

### Post by Impavidus on 2014-10-27
One thing to note though, if you install flash by installing restricted-extras, you may draw in some microsoft fonts too. These will prompt you to accept an EULA, which is know to sometimes appear behind the software centre. So if it seems to hang, make the window small and look for a dialogue box.

---

