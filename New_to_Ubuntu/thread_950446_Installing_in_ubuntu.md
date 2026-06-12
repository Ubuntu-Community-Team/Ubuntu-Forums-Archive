---
title: "Installing in ubuntu"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by saadia on 2008-10-17
hi guys,
I am a newbie. And would like to know how to install stuff onto ubuntu.

---

### Post by billgoldberg on 2008-10-17
> **saadia said:**
> hi guys,
I am a newbie. And would like to know how to install stuff onto ubuntu.

There are lots of ways.

First go to system -> administration -> software sources.

In the first tab make sure the first 4 are tagged.

In the second tab, tag the first.

Close the app and reload when you are prompted.

Now go to applications -> add/remove.

In the dropdown menu on the top select "all availabele sources".

Now just search for something (use generic words) tag the app, press apply.

--

You can also go to system -> administration -> synaptic for a more advanced search.

--

If you need codecs, if you're new you'll want them, look at the link in my signature.

--

Other ways:

1. Some websites (adobe, opera, getdeb, ...) offer .deb files for Ubuntu.

You just download those and double click them to install.

2. Archives (.tar.gz, .tar.bz, ...)

Those should either be compiled in the terminal or you should launch a file inside of the archive which will launch the app.

3. apturl

Some website have links, when you click it you will get a prompt asking you if you want to install the application.

(despite what you think, this is safe as it can only install stuff from the repository)

4. from other repositories

You can add repositories that have other software in them.

Add it the second tab in "software soucres", reload and then use either add/remove or synaptic to install the application.

5. apt or aptitude

Those use the same repositories as synaptic or add/remove but are used from the terminal.

Type in

sudo apt-get install applicationx 

or

sudo aptitude install applicationx

to install the software.

---

### Post by Ryadt on 2008-10-17
Have a look at this site: [http://vitalbodies.wordpress.com/2008/07/18/how-to-install-programs-in-ubuntu-hardy-heron/](http://vitalbodies.wordpress.com/2008/07/18/how-to-install-programs-in-ubuntu-hardy-heron/)

---

### Post by Paqman on 2008-10-17
To start out, i'd highly recommend using Applications > Add/Remove. It'll install anything you want automatically.

Software on Linux is downloaded from centralised repositories. Add/Remove (and it's more powerful cousin Synaptic) are the way that you interface with the repos.

---

