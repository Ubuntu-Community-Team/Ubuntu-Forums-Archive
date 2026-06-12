---
title: "weird path issue with certain commands"
date: 2015-03-10
forum: New to Ubuntu
---

### Post by sam120 on 2015-03-10
hi! i installed the nodejs library, and wish to utilize things such as [jade]("http://jade-lang.com") in my programming. however, when i go to call the jade command from the terminal, nothing is done (similar to the [rule of silence]("http://www.linfo.org/rule_of_silence.html")). 

```
sam@sam-AY747AA-ABA-p6310y:/$ jade
sam@sam-AY747AA-ABA-p6310y:/$ 
```

as you can see, it recognizes that the module is present and doesn't display any error messages when the command is called, but does not respond to any of it's intended commands (such as -V or the compile command). i have a feeling this is a path issue with node, but i'm not too sure as i have a very bare-bones knowledge of unix. (currently running ubuntu 14.10).

if i could get any help or pointers on the matter, that would be much appreciated!

---

### Post by sandyd on 2015-03-11
Hi, I have a few questions
Did you install NPM locally or globally? (See [http://blog.nodejs.org/2011/03/23/npm-1-0-global-vs-local-installation](http://blog.nodejs.org/2011/03/23/npm-1-0-global-vs-local-installation))
How did you install it? Ubuntu has npm in its repos.

If your wanting to install nodejs globally, try
```

sudo apt-get install npm
```

after removing the npm you installed.

This will automatically install npm and jade on your system globally.

Side note:
Jade can be installed either using NPM (prefered):
```

sudo npm install jade --global
```
Or by package
```

sudo apt-get install node-jade
```

---

### Post by sam120 on 2015-03-11
ah, guess i just had to reinstall NPM! thanks for the info, will be sure to take this into account if i run into any more errors like this.

---

