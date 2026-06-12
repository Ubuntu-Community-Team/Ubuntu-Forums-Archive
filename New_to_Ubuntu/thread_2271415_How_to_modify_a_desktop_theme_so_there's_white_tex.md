---
title: "How to modify a desktop theme so there's white text on black background?"
date: 2015-03-30
forum: New to Ubuntu
---

### Post by Moonswick on 2015-03-30
Hello,

How do I modify a theme so that it has white text on a black background? It is easier to see, but I'm unsure how to do this.

---

### Post by CantankRus on 2015-03-30
Rather than modify, try some of the themes available in this ppa.
```
sudo add-apt-repository ppa:noobslab/themes
sudo apt-get update
```

The Mediterranean theme pack contains a dark theme 
```
sudo apt-get install mediterranean-theme
```

Then use something like unity-tweak-tool to change themes.

---

