---
title: "problems with radrails"
date: 2006-04-30
forum: Programming Talk
---

### Post by ecentinela on 2006-04-30
I'm having problems with radrails. When I create a new project, the skeleton is not created. Outside of radrails, in a ubuntu console, if I make "rails test1", the project skeleton is created correctly, so the rails installation is good.
What can I make?
Someone can post the steps to install radrails from the begining (with a "virgin" system)?

Thanks in advance.

---

### Post by asimon on 2006-05-01
The same here with radrails 0.6.2. Absolutely annoying.
At upstream this is ticket [#821](http://dev.radrails.org/trac/ticket/821).

---

### Post by kassetra on 2006-05-02
0.6.2 has a giant bug that isn't allowing people to create skeletons, along with a number of other bugs.

0.5.3 works just fine and although it doesn't have all the added new features, it works like it is supposed to.

---

### Post by dhpeterson on 2006-05-03
I also have the same problem, running radrails 0.6.2 on dapper.

Does anyone know what I should put in the Window > Preferences > Rails > Rails Installs entry? By default it is empty.

Dave

---

### Post by ecentinela on 2006-05-04
At last, I get radrails working like a charm!

My procedure:
1 - Install ruby with synaptic
2 - Download rubygems and unpack it.
3 - Open a terminal, go to the rubygems directory and type "sudo ruby setup.rb"
4.- Again, in terminal, type "gem install rails --include-dependencies"
5.- Download radrails and unpack it
6.- Execute radrails. At this moment, If a new project is created, the skeleton is created as well. Only there is a problem... the webbrick don't start!
7.- Go to the ruby path on the preferences and change it to the correct path (the default, at least in ubuntu dapper, is incorrect)  "/etc/bin/ruby"
8.- Try to start the webbrick server and now it works... I hope :)

---

### Post by dudus on 2006-05-13
[QUOTE=ecentinela]At last, I get radrails working like a charm!

My procedure:
1 - Install ruby with synaptic
2 - Download rubygems and unpack it.
3 - Open a terminal, go to the rubygems directory and type "sudo ruby setup.rb"
4.- Again, in terminal, type "gem install rails --include-dependencies"
5.- Download radrails and unpack it
6.- Execute radrails. At this moment, If a new project is created, the skeleton is created as well. Only there is a problem... the webbrick don't start!
7.- Go to the ruby path on the preferences and change it to the correct path (the default, at least in ubuntu dapper, is incorrect)  "/etc/bin/ruby"
8.- Try to start the webbrick server and now it works... I hope :)[/QUOTE]
This was very usefull for me but I have some corrections...
you need sudo to install rails gems:
```
sudo gem install rails --include-dependencies
```
And the default path for ruby on dapper is /usr/bin/ruby

Webrick works but I can't open radrails' browser.
Is there a workaround fo this one?

---

### Post by dudus on 2006-05-13
I think I'm using gcj I'll try sun's java and then post the results here.

---

### Post by asimon on 2006-05-16
Looks like this bug is still unfixed in the new radrails 0.6.3, maybe in they fix it in 0.6.4...

---

### Post by adam.skinner on 2006-06-18
[QUOTE=asimon]Looks like this bug is still unfixed in the new radrails 0.6.3, maybe in they fix it in 0.6.4...[/QUOTE]

This isn't a bug, but a configuration issue.

```
cmdsList.add(ri.getLocation().toOSString() + sep + "bin" + sep + "rails");
```

So the "Rails Location", if your /bin/rails is found in /usr (as it is when installing via Gems on Ubuntu) would be "/usr".  This rails file is simply a ruby script that requires and loads rails.

Pretty messed up, and they know it.  There's an [issue in their track]("http://trac.radrails.org/trac/changeset/1306") depreciating this usage and relying on the gem.

Making this configuration change will allow rails to kick off when creating a new project, and the directory structure will be created (as it should be).  If you created a project and no application skeleton was created for you, this misconfiguration is likely your issue.

---

### Post by asimon on 2006-06-18
[QUOTE=adam.skinner]
Making this configuration change will allow rails to kick off when creating a new project, and the directory structure will be created (as it should be).  If you created a project and no application skeleton was created for you, this misconfiguration is likely your issue.[/QUOTE]
Thanks, but changing the rails location doesn't work for me. The rail skeleton still isn't created. (My rails is in /opt/ruby/bin/rails, thus I defined /opt/ruby as location).

---

### Post by D0c on 2006-07-25
The internal browser for radrails is not showing the .rhtml that i create in the views. What could be the problem?:confused:

---

### Post by jimcooncat on 2006-07-29
What I was hoping for a way to quickly make data driven websites has turned into a little nightmare for me with incompatibilities and conflicting advice. No one seems to be helping out at #radrails on freenode. 

I've tried all I can think of and can't make it work. But apparently its working for someone, because the videos on the website are so nice. But I see they're using Macs.

And what's up with this railsgems distribution that the environment seems to need? Debian says it can break things?

I even installed Eclipse thinking it was a way to do something similar to RadRails (well they look similar), and also saw it was recommended in one of the rails tutorials. Well it's a great environment -- for Java! 

It looks to me like we have a product made by a team that thinks it's found its silver bullet, and looks no further at the world around it.

Unless someone can post a marvelous fix, I think I'm giving up on this one.

---

### Post by asimon on 2006-07-29
> **jimcooncat said:**
> I've tried all I can think of and can't make it work. But apparently its working for someone, because the videos on the website are so nice. But I see they're using Macs.
My expieriences with radrails are also not the best. It has some really annoying bugs.

> **jimcooncat said:**
> 
And what's up with this railsgems distribution that the environment seems to need? Debian says it can break things?

I use gem without problems. I have installed all the standard ruby debian packages, but everything else - including rails - comes from gems. Never had any problem with this.

> **jimcooncat said:**
> 
Unless someone can post a marvelous fix, I think I'm giving up on this one.
For ruby (and C++ too, Eclipse's CDT didn't impress me at all) I am back to vim. But I will give RadRails an other try when it got some more bugfixing.

---

### Post by jimcooncat on 2006-07-29
thanks, asimon. I appreciate the validation here. 

I'm going to try Kassetra's suggestion and see what radrails 0.5.3 is like.

It seems like rails is worth exploring even without the whizbang IDE though. I'm still a bit scared with the whole Debian warning though about gem, but I've reinstalled several times before ...

---

### Post by bigfleet on 2006-08-02
jimcooncat, you may look into [RDT]("http://rubyeclipse.sourceforge.net/").  That's what I use on top of an Eclipse install from Eclipse.org to do my Rails programming.

---

### Post by boredandblogging.com on 2006-08-09
Under RadRails .7, in the Windows > Preferences > Ruby > Installed Interpreters, set the location of the ruby executable. That took care of my problem of just .project being created for new Rail projects.

---

