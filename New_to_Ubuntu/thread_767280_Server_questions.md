---
title: "Server questions"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-04-25
I'm looking to set up a server for myself, but I've never done it before. I use Ubuntu exclusively for desktop applications, so I figured I'd try it in a server. The problem is, I have absolutely no clue how to do anything with the command line, other than simple 'terminal' things that I do in Gnome. Ubuntu server comes without a GUI, and frankly, that scares me. What's more, I find very little helpful information on navigating U Server CLI, other than initial installation. The attitude seems to be "Learn the command line or give up and go away." Example: I was reading threads on here; one in particular was from someone who was searching for a GUI for a server deployment. He was comfy with CLI, but his coworkers are afraid of it, and he wanted to help them. One particular response to his query struck me:

"Yikes. If they're not comfortable using the command-line...well, whatever."

As I said, this seems to be the general attitude, and it's not very encouraging. Kinda bursts the adventurous bubble!

Anyway, enough blathering. What I want is to host my own website (because my current host sucks), have an email server, and also have an inventory control server for my business, and I want to do all of that on one machine. I know Ubuntu Server CAN do it, I just don't know how to GET it to do that stuff without pointing-and-clicking. I have a copy of Windows Server, but I want that to remain a last resort.

So, where do I turn? Should I try to install a GUI? If so, how is that done with the least amount of snags? If I stick with the command line, where are all the helpful tutorials about how to get it to do what you want (in a server environment, not a desktop one)? Am I out of my league here, and should go limping back to Windows to take care of this for me?

Any and all help is very appreciated!

---

### Post by Oak37 on 2008-04-25
Most tutorial or how-tos will have full instructions that can be achieved through the CLI. The installation for Ubuntu server makes it very easy to setup a mail/LAMP/DNS/SSH etc. server from the beginning. For further configuration of the features you want there are plenty of how-tos available in the community documentation.

If you feel the need to install a GUI it's not a big deal, whatever you feel most comfortable with. There are great instructions [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems#head-013d87a964541617a35fb741ed30ce5ec628013a") for installing a GUI, window managers, login managers etc.

edit: [Webmin]("http://www.webmin.com/") is great for administering a server with no GUI.

---

### Post by doctorbighands on 2008-04-25
That's more along the lines of what I would expect from the Ubuntu community. Very helpful reply - thank you!! =D>=D>

Webmin looks really cool.

---

### Post by doctorbighands on 2008-04-25
So, another thing, only this time it's to do with hardware:

I have, in my shop, two servers. One is a single-CPU (800MHz Celeron), and one has a pair of Xeon chips in it at 550MHz apiece. For my web server needs, which configuration would be best? Yes, I know they're both beasts, but I don't see that I have a need for anything more. No matter what, the machine I pick will have 1GB RAM in it, so that will help a bit.

---

### Post by Oak37 on 2008-04-26
> **doctorbighands said:**
> So, another thing, only this time it's to do with hardware:

I have, in my shop, two servers. One is a single-CPU (800MHz Celeron), and one has a pair of Xeon chips in it at 550MHz apiece. For my web server needs, which configuration would be best? Yes, I know they're both beasts, but I don't see that I have a need for anything more. No matter what, the machine I pick will have 1GB RAM in it, so that will help a bit.

Personally I'd go with the pair of Xeons, depending on how busy your server will be two CPUs might be better than one. I think the biggest considerations for servers are RAM and disk space/disk speed. Since either will have 1Gb of RAM it doesn't matter which you choose and generally the faster the drives the better, but it's important to tailor it for your needs. If your website and mail needs aren't through the roof then the hardware you've got will do pretty well.

There's a server section in the community documentation [here]("https://help.ubuntu.com/community/Servers"). Some of them are easier to read than others but like I said before, all good guides should give instructions on how to set services up through the command line without the need for a GUI. It's always handy to google what you're trying to install as well to see if there are other guides so you can compare and spot mistakes if there are any!

---

