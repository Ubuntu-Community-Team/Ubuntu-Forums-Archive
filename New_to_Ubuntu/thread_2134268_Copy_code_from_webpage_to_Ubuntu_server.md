---
title: "Copy code from webpage to Ubuntu server?"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by matphat on 2013-04-10
Completely new to Ubuntu and having several silly, new user, problems. This is the current one.

Situation:
I am installing and configuring Ubuntu Server 10.4 LTS for various test environments, and teaching myself the CLI. I am doing a lot of online learning and using a ton of tutorials, etc...
One of the things I am encountering is that a lot of the guides and tutorials suggest copying code (Often times a lot of code) from the webpage into terminal, or more frequently, into config files. Obviously this work is being done on another computer with a GUI so that I can actually see the embedded code. 

Question:
Since I'm using Server (For many reasons), and have no GUI (Nor want one), and have nothing but terminal web browsing, how should I go about getting my hands on the code copied and pasted in to the CLI or into nano and the like?

I have done this with Linux with GUI, and the obvious choice is a graphical web browser, but that would require a GUI, No?

Just really confused as to how server admins get their hands on code from places on the web (Like this site) without a GUI.

Help?

---

### Post by steeldriver on 2013-04-10
If you log into the server via ssh from your other (GUI) computer then you should be able to just copy-paste into the remote server CLI from the local browser

---

### Post by Derek Karpinski on 2013-04-10
use wget to download the page?

use lynx or w3m to browse in a terminal?

---

