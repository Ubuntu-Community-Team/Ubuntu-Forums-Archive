---
title: "Setting up apache with Ruby on Rails"
date: 2008-12-30
forum: Programming Talk
---

### Post by bungoman on 2008-12-30
I'm having a lot of trouble getting apache and Ruby on Rails working on my system for some reason. Mostly it's because I can't find a tutorial that explains all the steps in enough detail.

[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails) just isn't making any sense to me for some reason. I've tried some other tutorials and they're all either too vague or way outdated (vague in that they just say "edit your apache configuration to do so and so" instead of telling me the exact file and where in the file).

Can anyone please explain to me how I can make it so I can see my rails application? That's all I want to do, I know apache is working, when I go to [http://localhost](http://localhost) I see the default it works message in the /var/www folder. But I have no idea how to configure any of this.

I did this about two years ago on Fedora Core 4 and I don't remember it being nearly this frustrating. I'm using Ubunut 8.04 if that makes a difference. I've got the latest version of rails, apache, and gems all installed and working.

---

### Post by Gilabuugs on 2008-12-30
if you just want to see and create your apps, not go into putting them on the web

1: install ruby through apt
2: install rubygems from tar
3: install rails through gems
then just do:
```
$ rails mynewapp
$ cd mynewapp
$ ruby script/server

```

then it will be up and working on localhost:3000

you can open up a new terminal and run all your commands there and the server will update as you go

setting up an apache server or web server is a bit more complicated and maybe loook at the slicehost.com articles

---

