---
title: "How to install Red-hat?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2008-05-11
I'm sure I've seen this thread before but cant find it. I want to install Real Player but can only find it in Red-Hat install version and i dont know how to do it. I thought it was achieved by opening terminal and typing apt-get or something similar but that didnt work.I've tried downloading Helix player but the site I want to go on only seems to work with Real Player.

---

### Post by N.N. on 2008-05-11
RealPlayer is no longer in any of the common repositories, so you can't install it through Synaptic or by using apt-get. Instead you can download a Custom Binary Installer (.bin) from the official RealPlayer website and use it to install RealPlayer on your system:

[LIST=1]
[*]Go to [http://www.real.com/linux](http://www.real.com/linux) and click the big "Download RealPlayer" button. Save the file (RealPlayer11GOLD.bin) in your home directory, for instance (i.e. in /home/your_username/).
[*]Open a terminal and make the downloaded .bin file executable by typing the following command: ```
chmod a+x RealPlayer11GOLD.bin
```
[*]Run the .bin file by typing the following command: ```
./RealPlayer11GOLD.bin
```
[*]Follow the instructions in the installer.
[/LIST]

You might want to bookmark the guide on ["How to install ANYTHING in Ubuntu"]("http://monkeyblog.org/ubuntu/installing/") for future reference. It answers questions such as how you install .bin files and RedHat .rpm files. :)

---

### Post by SunnyRabbiera on 2008-05-11
OR, use this little guide:
[here]("http://ubuntuforums.org/showthread.php?p=4737528")

---

