---
title: "websites with video ads will not open"
date: 2015-11-01
forum: New to Ubuntu
---

### Post by lauriehurman on 2015-11-01
I'm afraid I'm a very ignorant old person, so ...

I was using Ubuntu 12. All of a sudden the homepage ([www.bbc.co.uk](www.bbc.co.uk)) would not start. I then discovered that any website which contained video, such as adverts etc, would not open. I upgraded to Ubuntu 14 thinking that would solve the problem. It didn't.

Could any kind person tell me what the problem is likely to be so that i know what to read up on and learn. At the moment I have no idea where to start.

Thanks for taking the time.
Laurie

---

### Post by Sweet_Baby_Jamie on 2015-11-01
Have you installed the "restricted-extras" packages?  Those are codecs and other "non-free" softwares that enable video and multimedia stuff.  "Non-free" doesn't mean you have to pay for it, it just means that it can't be copied and distributed with Ubuntu because of licensing.  Sometimes updating changes them, too.  Open software center or Synaptic Package Manager and double check to see if you have ubuntu-restricted-extras.  If not, installing them is quick and easy (you will need your root password).

---

### Post by Vladlenin5000 on 2015-11-01
> **Sweet_Baby_Jamie said:**
> Have you installed the "restricted-extras" packages?  Those are codecs and other "non-free" softwares that enable video and multimedia stuff.  "Non-free" doesn't mean you have to pay for it, it just means that it can't be copied and distributed with Ubuntu because of licensing.

^^^^
This. And here's why: BBC still requires the (almost) obsolete Adobe Flash which is bundled in the restricted extras packages you were suggested to install.
Youtube and all other major streaming video services already moved to a newer, better and open-source technology: HTML5.

That said, here's the problem with Flash: Adobe stopped to support it for Linux some time ago. Only security fixes for a very old version are provided and it doesn't work already in some websites (BBC works fine).
For better results you can install and use Google Chrome which comes with an updated (and exclusive) Flash version thanks to a special agreement between the two companies.

---

### Post by kostkon on 2015-11-01
> **Vladlenin5000 said:**
> ^^^^
This. And here's why: BBC still requires the (almost) obsolete Adobe Flash which is bundled in the restricted extras packages you were suggested to install.
Actually BBC is converting to HTML5 and you can already enable the (still) beta HTML5 player [here]("http://www.bbc.co.uk/html5").

---

### Post by Vladlenin5000 on 2015-11-01
> **kostkon said:**
> Actually BBC is converting to HTML5 and you can already enable the (still) beta HTML5 player [here]("http://www.bbc.co.uk/html5").

Very good news indeed.

---

### Post by Sweet_Baby_Jamie on 2015-11-02
> **Vladlenin5000 said:**
> 
For better results you can install and use Google Chrome which comes with an updated (and exclusive) Flash version thanks to a special agreement between the two companies.

Can we use Chromium (the unbranded FOSS version) or does it have to be Google Chrome to use their new Flash thing?  Just curious.

---

### Post by Vladlenin5000 on 2015-11-02
> **Sweet_Baby_Jamie said:**
> Can we use Chromium (the unbranded FOSS version) or does it have to be Google Chrome to use their new Flash thing?  Just curious.

Yes, for the purpose it must be Chrome, not Chromium. The latter doesn't include the updated Flash version the former has.

---

### Post by yetimon_64 on 2015-11-02
> **Vladlenin5000 said:**
> Yes, for the purpose it **must** be Chrome, not Chromium. The latter doesn't include the updated Flash version the former has.

I have chromium only installed and am using the flash package from the pepperflashplugin-nonfree package (downloads google chrome but only installs the pepperflash plugin from it), so it is possible to do; but there is one catch in that my version of flash as supplied by the plugin must be regularly checked and updated manually from terminal. **Edit**: It may be possible with a bash script and the pepperflash commands to write a script for checking and updating regularly via a cron entry for more experienced users etc ... I :-k I'll have a go to see what I can get working for this, bash scripting a task like this could get interesting.

Some users may find using the pepperflash-plugin OK, _*but I would suggest the OP follow your advice*_ and install google chome for ease of management if not comfortable with manual checking and updating such a package.
Cheers, yeti.

---

### Post by lauriehurman on 2015-11-02
Ahh that explains why installing Chromium browser didn't solve my problem :-)

First I tried loading the restricted extras package as advised by Jamie. At first I thought it had failed but later it said that it was installed. Anyway the problem with opening website remain the same so then I installed Chromium, thinking that's what Vlad meant. Predictably that made no difference either.

I'll try Google Chrome. As Yeti says; manually doing just about anything is beyond my paygrade.

Thakns to all for your time and trouble.
Laurie
flashplugin-installer11.2.202.540ubuntu0.14.04.2
firefox41.0.2+build2-0ubuntu0.14.04.1

---

### Post by Vladlenin5000 on 2015-11-02
[https://www.google.com/chrome/](https://www.google.com/chrome/)

Click Download and select Debian/Ubuntu and your architecture.

---

### Post by lauriehurman on 2015-11-04
Thank you  all.

Unfortunately I'm stuck with a catch 22. [https://www.google.com/chrome/](https://www.google.com/chrome/) is an example of a site that will not open (I'm assuming that that is because it contains video but that is only an assumption).

I can't think of a way round this at the moment.
Laurie

---

### Post by Vladlenin5000 on 2015-11-04
You have another problem then...

Anyway, try downloading from the Copy shares below. Please choose according to your architecture:

Google Chrome 32-bit -> [https://copy.com/d13TjbuKoXgw3JVI](https://copy.com/d13TjbuKoXgw3JVI)
Google Chrome 64-bit -> [https://copy.com/lxXuNnuwpUgXJ2Wo](https://copy.com/lxXuNnuwpUgXJ2Wo)

---

### Post by Sweet_Baby_Jamie on 2015-11-04
After downloading, you can use **Gdebi** package installer to install it.

---

### Post by SeijiSensei on 2015-11-04
Are you using an ad blocker or an add-on like Ghostery?  Often those will block pieces of the site like Javascripts and cause problems during loading. Try turning off any blocking add-ons in Firefox and reload the site.  Any better?

---

### Post by lauriehurman on 2015-11-04
Doooohhhh

In a frenzy of trying anything I disconnected the ethernet cable and turned on the Wifi. Suddenly everything works, I have no idea why but it does.

Thank you very much for all the time adn trouble you have all taken to help me.

Laurie

---

