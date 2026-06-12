---
title: "Is the following WordPress installation tutorial good?"
date: 2016-09-19
forum: New to Ubuntu
---

### Post by tonma on 2016-09-19
Hello,

I'm new to Ubuntu, and realized that many goals can be achieved in many ways, and every way is doing different things, that may not be visible, but may affect security / system performance.
I wanted to install WordPress on Ubuntu 16.04, and found this guide:
[https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lamp-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lamp-on-ubuntu-16-04)

Now I have WordPress running, but since it took about 30 minutes to follow this guide, with installing many things on the way, rather than simple Next button like on Windows, do you think that if I followed this tutorial, I should be good? Or you would change things?

Ty!

---

### Post by PartisanEntity on 2016-09-19
This is a perfectly fine tutorial to follow.

I am a web developer and work daily with Wordpress. I also have experience with setting up LAMP stacks. The tutorial walks you nicely through all the requirements you need to run Wordpress on your Ubuntu machine.

Out of interest, is this an internal machine or an internet facing server?

---

### Post by tonma on 2016-09-19
Thank you!

It is for my localhost testing. You ask because it should matter on some steps on the tutorial? By the way, I tried to create internet facing server, but just couldn't find any tutorial to follow. Maybe you have a link on how to do that? But won't that be slow using my home network?

---

### Post by Habitual on 2016-09-19
Looks familiar! :)
See also [https://codex.wordpress.org/Hardening_WordPress](https://codex.wordpress.org/Hardening_WordPress)

---

### Post by PartisanEntity on 2016-09-20
> **tonma said:**
> Thank you!

It is for my localhost testing. You ask because it should matter on some steps on the tutorial? By the way, I tried to create internet facing server, but just couldn't find any tutorial to follow. Maybe you have a link on how to do that? But won't that be slow using my home network?

In my personal opinion, if it is a home server, and you also have other computers on the network, I would refrain from making an internet facing server. You would be exposing too much attack surface to the internet and this could be a risk to your entire home network and files.

If you can afford it, I would recommend renting hosted web space. Safer.

If you still want to go ahead with that, to expose your home server to the internet, you require the following:

- a static public IP number (or dynamic dns service)
- a router that allows you to forward requests on port 80 of your public IP to your servers local IP address
- a properly configured firewall on your server

---

### Post by mastablasta on 2016-09-20
aside from the advice given above, for testing purposes one can use virtualbox and add a virtual image. Bitnami has such images : [SIZE=2]https://bitnami.com/stack/wordpress
link to virtualbox image: 
[SIZE=2][https://bitnami.com/stack/wordpress/virtual-machine](https://bitnami.com/stack/wordpress/virtual-machine)

a similar one is Turnkey linux but they use Debian under it.

[/SIZE]

[/SIZE]
you just load this image into virtual box, start up the "appliance" and it will only ask to change the password and all will be just working. no install needed. 

the good think about virtualbox (or similar) is that you can just create a snapshot, then mess everything up and then just restore the snapshot, and in a few seconds you will be right back where you started.

if you need to you can also "safely" expose the virtualbox to outer internet (by opening the port to it). if the image in virtualbox get's hacked it should influence other parts of the system. besides it is not available unless you are running it. server images need abotu 400-500 MB ram to run well.

having installed wordpress on windows (XAMPP) as well i am not sure there are any more or less steps in linux. expand wordpress, create & prepare database, connect via browser and do the install.

---

### Post by Habitual on 2016-09-20
A router would help keep things "tighter".
Do you have one?
[https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lemp-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lemp-on-ubuntu-16-04)

meh, I'd first refer to [https://wordpress.org/support/topic/5-minute-install/](https://wordpress.org/support/topic/5-minute-install/)

---

