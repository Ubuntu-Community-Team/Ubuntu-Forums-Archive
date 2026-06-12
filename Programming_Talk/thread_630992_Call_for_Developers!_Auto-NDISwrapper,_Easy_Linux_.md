---
title: "Call for Developers! Auto-NDISwrapper, Easy Linux wifi for noobs"
date: 2007-12-03
forum: Programming Talk
---

### Post by climatewarrior on 2007-12-03
I am thinking of developing (with a couple of friends and maybe you ;) ) a version of NDISwrapper that comes with all Windows drivers included (or fetches the needed one from the Internet or includes the most common ones like mintwifi) for the cards that are listed as supported with NDISwrapper. It automatically detects the wifi card you have, blacklists any open source driver currently active ( lets face it ,with some cards they are almost unusable although they sometimes work great and in this case the user wont look for this tool) and then automatically installs the proper windows drivers with NDISwrapper. This would be a GUI tool developed on Python and it will be released under the GPL license (except the drivers of course). I'm thinking on hosting it on Launchpad and plan on developing it this Christmas and having an alpha release by January (The semester begins on January). I am accepting any kind of help as I really don't have any programming experience at all except the classes I have taken(C programming, I'm learning Python now). I think this would be a great tool for noobs that are scared away from Ubuntu and Linux in general because they can't setup their wireless cards or they have to use the command line(NDISgtk doesn't always work propely) to set them up. If you are interested in helping me out send me an email to gabrieljoel (at) gmail.com or leave a post here. Also if anyone has any suggestions or if anyone knows if this has already been made or if you think it is too complex please feel free to tell me.

---

### Post by Sparragus on 2007-12-05
I'm in. Definitely looking to implement this into some future release of Ubuntu. I wonder why haven't this been done before, it would be so helpful. I'm also learning Python so we'll probably make a great learning team. :)

Later.

---

### Post by bfhicks on 2007-12-06
I have to say, at least you are honest. Taking one class in programming in college and writing driver installs and device setups on linux are quite different.

I'm going to be pessimistic and party crasher and say that new developers are not going to solve this problem. If it could be solved that easily, it would be done.

Device drivers are tough to deal with in linux, even automating which to install. That's why linux struggles to become mainstream...it doesn't just "work" all the time with off the shelf hardware. Nice idea, try it out, but dealing with version control, patches, and such are out of your league. Most projects like this are usually already underway, and then people start to contribute.

Anyhow, goodluck.

---

