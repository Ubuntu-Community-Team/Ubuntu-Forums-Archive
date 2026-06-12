---
title: "How to install/use pre-compiled program"
date: 2020-12-06
forum: New to Ubuntu
---

### Post by jaoc12 on 2020-12-06
Dear Ubuntu community,

First, apologies in advance for my novice-type question.

I´m trying to install & use Peter Erwin´s IMFIT software.
- I´ve downloaded and uncompressed it:
- I´ve moved to a IMFIT directory I´ve created in /home/<user>/IMFIT
- When I  ove where the "executable" IMFIT resides (/home/usr/IMFIT/imfit-1.8.0-linux64/imfit-1.8.0/), if I type "./imfit" seems to show basic info, so al OK so far
- However, if I try to run the command "imfit" from any other folder .... "bash: ./imfit: No such file or directory"

software is available here [https://www.mpe.mpg.de/~erwin/code/imfit/](https://www.mpe.mpg.de/~erwin/code/imfit/)

there´s an easy to run example in "examples" folder (but if I move there and I execute a basic imfit command ...., I get above error)

i guess i need to add sth to my ./bashrc or ./bash_profile. If so, please advice what and how

Needless to say many thanks in advance

Kind Rgds
Jose

---

### Post by mikewhatever on 2020-12-06
Try something like the following:
```

export PATH=$PATH:/home/usr/IMFIT/imfit-1.8.0-linux64/imfit-1.8.0

```

Don't forget to run <source .bashrc> after editing.

---

