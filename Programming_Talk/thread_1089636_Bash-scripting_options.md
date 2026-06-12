---
title: "Bash-scripting options"
date: 2009-03-07
forum: Programming Talk
---

### Post by SakJur on 2009-03-07
In a script named coconut.sh I've made I want to be able to use flags á la --help, --version, --quiet and --url=http://canonical.com etc.

This flags are btw. going to link to variables :D
How do I do this?

Thanks for any reply
Your Sincerly
Emil

---

### Post by the_unforgiven on 2009-03-07
You use [getopt]("http://linux.die.net/man/1/getopt").
Here is how you use it:
[http://www.linuxlaboratory.org/?q=node/4](http://www.linuxlaboratory.org/?q=node/4)

HTH ;)

---

