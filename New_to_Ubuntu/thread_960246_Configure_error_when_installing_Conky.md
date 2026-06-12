---
title: "Configure error when installing Conky"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by MrPatton84 on 2008-10-27
Hey everybody, 

I extracted the tar that I downloaded from the Conky SorceForge page, but then when I ran the ./configure command it went through a load of checks before returning this message

configure: error: Can't locate your X11 installation

Any thoughts? I have a feeling I saw this message recently when I tried to install something else, too. What is the X11?

Thanks in advance for all your help

Chris

---

### Post by reg4c on 2008-10-27
Hey, 

I am wandering why you tried to instal Conky from the download and not from the repos.

```

sudo apt-get install conky

```

And thats it. Worked for me. Give this a try and then report back.

Ow, and I really don't understand how you don't have X11, when that is the backbone for the X window system.

Cheerio

---

### Post by mcduck on 2008-10-27
errors when compiling are usually because you don't have the required development libraries installed. So in this case you'd need at leats the dev packages for X11.

But, just like reg4c said, conky is in Ubuntu's repositories and you should use Ubuntu's package management to install it instead of trying to compile it from the source code.

---

### Post by MrPatton84 on 2008-10-27
Ok...

I tried this - sudo apt-get install conky - and it seemed to work fine. 

But then I tried to run Conky from the Terminal and I got this message...

Conky: missing text block in configuration; exiting

Any thoughts?

Thanks again 

Chris

---

