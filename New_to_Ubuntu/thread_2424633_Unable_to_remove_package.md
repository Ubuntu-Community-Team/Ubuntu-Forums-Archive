---
title: "Unable to remove package"
date: 2019-08-12
forum: New to Ubuntu
---

### Post by mantas4682 on 2019-08-12
Hello,

So, I accidentally canceled the installation for 'soundKonverter' application from the Software Store. The Remove button gives me an error message -- Unable to remove soundKonverter.

apt-get remove gives me this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'soundkonverter' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```


I wish to remove the broken package and install the actual program.

Cheers.

---

### Post by deadflowr on 2019-08-12
Let's see what state it's in
```
dpkg -l soundkonverter
```
Note: no output would mean not installed, fyi.

Could also be that apt-get is right and the Software Store is erring.
Wouldn't be the first time Software Store did something weird.

---

### Post by Bashing-om on 2019-08-12
mantas4682 Hello -

See deadflowr's last
Or
Maybe this is a snap install ?

what shows:
```

snap list --all

```

[INDENT][INDENT]never can tell 'Til
[INDENT][INDENT]we look
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mantas4682 on 2019-08-12
Thank you so much for the responses.

```
dpkg -l soundkonverter
```

and

```
snap list --all
```

gave me nothing, but I've decided to scroll through the 'Installed' tab and clicking Remove there just kinda made it disappear? Searching for it again after restarting the Software Center allowed me to install it.

What I was doing previously is just looking up the program I want to install or remove and doing all my actions through that menu, but it kept giving me the error.

It seems to be functioning correctly, at least what I need it for. :)

---

### Post by Bashing-om on 2019-08-12
mantas4682; Good deal :)

Glad it worked out -

Mark it up to gremlins that a update squashed ?

[INDENT]put the blame on ......
[/INDENT]

---

