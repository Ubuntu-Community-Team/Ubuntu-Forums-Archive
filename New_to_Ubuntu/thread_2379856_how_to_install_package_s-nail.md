---
title: "how to install package s-nail"
date: 2017-12-10
forum: New to Ubuntu
---

### Post by micahpage on 2017-12-10
I am trying to install package s-nail on Ubuntu 14.04 but it is not in the repos, but is in the repos of 16.04.

```
metulburr ~ $ sudo apt-get install s-nail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package s-nail



```

If i add Xenial to my source list i get this error
```
[COLOR=#333333][FONT=Monaco]metulburr ~ $ sudo apt-get install s-nail[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]Building dependency tree       [/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]Reading state information... Done[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]Some packages could not be installed. This may mean that you have[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]requested an impossible situation or if you are using the unstable[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]distribution that some required packages have not yet been created[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]or been moved out of Incoming.[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]The following information may help to resolve the situation:[/FONT][/COLOR]

[COLOR=#333333][FONT=Monaco]The following packages have unmet dependencies:[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]s-nail : Depends: libssl1.0.0 (>= 1.0.2~beta3) but 1.0.1f-1ubuntu2.23 is to be installed[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]         Depends: libtinfo5 (>= 6) but 5.9+20140118-1ubuntu1 is to be installed[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]E: Unable to correct problems, you have held broken packages.[/FONT][/COLOR]
```

---

### Post by ian-weisser on 2017-12-10
Do NOT add Xenial (16.04) sources to a 14.04 system. Doing so is likely to beak your system quite horribly.

If you *must* have s-nail, and only s-nail, then either upgrade to 16.04 (or newer) or install from source.
Alternately, many more-or-less nail-like programs are available in the 14.04 repositories.

---

### Post by micahpage on 2017-12-10
i was going through this tutorial and got blocked by the s-nail package
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-on-ubuntu-16-04)

Is there an alternative to this or just install from source?

---

### Post by ian-weisser on 2017-12-10
Of course there are alternatives to s-nail. Plenty of them...though it depends upon which features you want.
One is right there in the same paragraph, just an "apt-get search" away,

I'm not a fan of that tutorial. It makes assumptions (s-nail, ufw) that make things more bloaty than needed.
I gently suggest [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto) instead...which will work on 14,04.

---

