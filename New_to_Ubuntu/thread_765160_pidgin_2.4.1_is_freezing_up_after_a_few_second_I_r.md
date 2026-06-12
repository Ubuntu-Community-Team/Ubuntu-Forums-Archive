---
title: "pidgin 2.4.1 is freezing up after a few second I ran it"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Vicfred on 2008-04-24
topic, any ideas what is this happening? :confused:

---

### Post by gaffurabi on 2008-04-24
you could try to install **amsn** :(

which works fine on my system and is better than pidgin in my opinion.

---

### Post by Vicfred on 2008-04-24
sorry i like pidgin, amsn is not my type =x. pidgin was running perfectly on the RC but when i upgraded it stopped to work.

---

### Post by billgoldberg on 2008-04-24
open a terminal and type

```
pidgin
```

then post the error the terminal gives.

note: asmn sucks and is ugly. emesene is a much better alternative (use it myself) but you'll need a deb, it's not in the repo's (at least not in gutsy).

---

### Post by Vicfred on 2008-04-24
```
vicfred@maggie:~$ pidgin
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!

```

where can i get that deb, do you have any screenshot?

---

### Post by billgoldberg on 2008-04-24
> **Vicfred said:**
> ```
vicfred@maggie:~$ pidgin
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!

```

where can i get that deb, do you have any screenshot?

sure, the deb is here:

[http://packages.ubuntu.com/hardy/all/emesene/download](http://packages.ubuntu.com/hardy/all/emesene/download)

it looks good, gtk.

---

### Post by Vicfred on 2008-04-24
> **billgoldberg said:**
> sure, the deb is here:

[http://packages.ubuntu.com/hardy/all/emesene/download](http://packages.ubuntu.com/hardy/all/emesene/download)

it looks good, gtk.

ok, but how do i fix that error displayed on the console? ><

---

### Post by billgoldberg on 2008-04-24
I have no clue,

did you try reinstalling it?

(deleting the hidden folder and all?)

---

### Post by mister_pink on 2008-04-24
emesene seems to be in the hardy repos so you dont need to download a deb. You don't have any extra plugins installed in pidgin do you? Skype for example?

---

