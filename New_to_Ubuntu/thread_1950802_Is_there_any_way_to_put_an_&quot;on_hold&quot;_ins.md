---
title: "Is there any way to put an &quot;on hold&quot; install of several packages?"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by Lucypie on 2012-04-01
This will be one of the weirdest questions you've ever heard.

Here's the deal: I have a bit of an internet limit and I let my dad do all the downloading for stuff. So I wait until I have a chance for free Internet (hotel or something) to do all my updates and such. Well, my mother is going somewhere with Internet but I cannot go with her. She knows NOTHING of ubuntu and knows not how to update it or install the 50 some programs I wish to install (this is a fresh install :/) 

With that said, is there any way to like click the programs I want and the extras (like you find in the package manager) and make it where she can simply click install or update (like system update) and install all of them? :) Thank you!!

PS -- Using Ubuntu 11.10 64bit near-fresh install :) Thanks.

---

### Post by santosh83 on 2012-04-01
> **Lucypie said:**
> This will be one of the weirdest questions you've ever heard.

Here's the deal: I have a bit of an internet limit and I let my dad do all the downloading for stuff. So I wait until I have a chance for free Internet (hotel or something) to do all my updates and such. Well, my mother is going somewhere with Internet but I cannot go with her. She knows NOTHING of ubuntu and knows not how to update it or install the 50 some programs I wish to install (this is a fresh install :/) 

With that said, is there any way to like click the programs I want and the extras (like you find in the package manager) and make it where she can simply click install or update (like system update) and install all of them? :) Thank you!!

PS -- Using Ubuntu 11.10 64bit near-fresh install :) Thanks.

I'm not sure, but I think you can do this with Synaptic. You can mark all the packages you need to install and save the markings to a file. Then your mother simply has to load the file into Synaptic (File->Read Markings), and click the Apply button to install them all.

I think you can also save the
```
sudo apt-get install pkg1, pkg2, pkg3, ...
```
command-line to a bash script, and simply tell her to invoke the script.
Hope this helps.

---

### Post by cmcanulty on 2012-04-01
most libraries have fast connections try yours

---

