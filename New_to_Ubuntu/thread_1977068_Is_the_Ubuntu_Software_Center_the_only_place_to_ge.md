---
title: "Is the Ubuntu Software Center the only place to get applications?"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by TheGuyWithTheFace on 2012-05-09
So, I'm considering learning how to program applications, and was wondering if the Ubuntu Software center was the only place to upload applications. ...is it?

---

### Post by wilee-nilee on 2012-05-09
> **TheGuyWithTheFace said:**
> So, I'm considering learning how to program applications, and was wondering if the Ubuntu Software center was the only place to upload applications. ...is it?

You also have synaptic which must be installed and apt-get, an apt get command would be this.

```
sudo apt-get install package name
```You can also remove and purge packages with apt-get as well.

```
sudo apt-get remove package name
``````
sudo apt-get purge package name
```

So if you want to install synaptic run.

```
sudo apt-get install synaptic
```

---

### Post by Paqman on 2012-05-09
If you're writing your own programs you'll want to register a Launchpad account and open a PPA (Personal Package Archive). That will give you somewhere you can upload your work to and people can subscribe to it to test your stuff for you. If you're using something like Quickly it'll automatically upload to your PPA.

To get stuff into Software Centre means getting it into the official repositories, which means your code has to have achieved a certain level of polish and testing. The place for works-in-progress is a PPA.

---

### Post by David Andersson on 2012-05-09
You normally download/install using the Ubuntu Software Center. You can also download/install packages using Synaptic or apt-get.

If you make a package and want others to be able to install it in Ubuntu, you can make a .deb-file, put it in your blog where others can download it and double click it and it will be installed. Or you can create a PPA (Personal Package Archives), that is a software repository that you control. Then you ask others to add your PPA to their package managers (In Software Center>Edit>Software Sources>Other Software>Add). After that your packages will show up amongst all other packages when they search for software in Software Center or in Synaptic.

---

### Post by papibe on 2012-05-09
Hi TheGuyWithTheFace.

You can get software from other sources too. One of the usual way people can get bleeding edge software versions is through a Personal Package Archive or ppa. For example: the well-know Mediainfo can be found [here]("https://launchpad.net/~shiki/+archive/mediainfo").

There are places where you can buy games and software: [Linux Commercial Applications]("http://lin-app.com/").

Be sure to download your software from reputable web sites.

One of the option you have for learning how to develop applications is to download the source code of an app. Most (if not all) of the what you find on the Software Center, has a source package available. Browse this site to get the links to software sources: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

I hope that points you in the right direction.
Regards.

---

### Post by TheGuyWithTheFace on 2012-05-09
Thanks for the quick response, guys. Also, this'll sound a bit dumb, but what exactly is launchpad? Just a website for software downloads, or what?

---

### Post by alphacrucis2 on 2012-05-09
> **TheGuyWithTheFace said:**
> Thanks for the quick response, guys. Also, this'll sound a bit dumb, but what exactly is launchpad? Just a website for software downloads, or what?

It is a website that hosts ubuntu ppa's, the ubuntu bug tracker and other stuff.

---

### Post by Paqman on 2012-05-09
> **TheGuyWithTheFace said:**
> Thanks for the quick response, guys. Also, this'll sound a bit dumb, but what exactly is launchpad? Just a website for software downloads, or what?

Sorry, should have linked you up: 
[Launchpad]("https://launchpad.net/").
[About Launchpad]("http://en.wikipedia.org/wiki/Launchpad_(website)")

---

### Post by TheGuyWithTheFace on 2012-05-09
Thank you very much!

---

