---
title: "Server vs Desktop."
date: 2013-06-06
forum: New to Ubuntu
---

### Post by avsksan on 2013-06-06
Hello Everybody,
                     I have IBM x3400 M3 Server. I need to install Ubuntu and run OpenFoam for computation. Can you Please Help me with selecting the ubuntu version and advice to effectively use the hardware. My hard ware specifications are as follows:
[COLOR=#000000][FONT=verdana]* Intel(R) Xeon(R) CPU E5507 2.27 GHz 2.26 GHz (2 Processors)[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]* 12 GB RAM[/FONT][/COLOR]
 Please advice.
Thank You.

---

### Post by Lars Noodén on 2013-06-06
Well, there is the server disc image for servers.  That installs a fairly bare-bones set up to which you can add just those pieces that you plan on using.  OpenFOAM seems to be text based so you could log in from your deskop using ssh and run it there.  For that you would only need to add the package openssh-server to the OpenFOAM machine.  

From what I read, there is also a graphical interface called ParaView.  You can also run that on the remote server but have the UI displayed on your desktop by enabling X11 forwarding with ssh with the -X option.

---

### Post by Frogs Hair on 2013-06-06
The following are requirements for 12.04 server from the canonical store. The ram  requirements increase greatly for a desktop installation.            [http://shop.canonical.com/product_info.php?products_id=981](http://shop.canonical.com/product_info.php?products_id=981)

[B]System requirements: Your server must have at least 128 MB of RAM and 1 GB of disk space. This 64-bit edition will run on AMD64 and Intel x64-based computers. 

[/B]

---

