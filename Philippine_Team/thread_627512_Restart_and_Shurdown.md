---
title: "Restart and Shurdown"
date: 2007-11-30
forum: Philippine Team
---

### Post by dareymon on 2007-11-30
help. pag pag nag rerestart po ako or shutdown using the bottons sa may login window eh hindi talaga nag rerestart or nag shushutdown. kaya nag lolog in muna talaga ako saka ko i shushutdown. ano po kaya ang gagawin ko para ma shitdown ko or restart using the buttons sa login window?

---

### Post by wilvyrux on 2007-11-30
bro na try q na yang problem na yan...try u mag palit ng GDM themes mo yung logon screen...i think yun ang nag cacause kaya hindi u sya ma shutdown or marestart...

kc sometimes yung na download u na skins kung meron nga u na  download...possible na cra yung codes nun...

default ba ang gamit u na GDM themes yung logon screen?

---

### Post by dareymon on 2007-11-30
opo default po yung gamit ko.

---

### Post by wilvyrux on 2007-11-30
ganun...bro try u mag palit ng ibang design sa logon screen..check u kung ganun parin ang effect...

---

### Post by dareymon on 2007-12-01
na try ko na po mag iba ng login window pero hindi parin po ma shutdown at restart pag sa login window ako nag shushutdown or restart.

---

### Post by raxso on 2007-12-01
Tanong: ano pong video card ang gamit mo, and can you also try to reboot in terminal mode.

sudo shutdown - r now ---- to reboot
sudo shutdown -h now ---- to shutdown completely

para ma check kung saan banda mag hang or mag stop.

you can also try this.

sudo gedit /etc/modules. Add the following line, then save:
apm power_off=1

---

### Post by dareymon on 2007-12-02
ge cube 9550 xtreme edition 128 mb ati

---

### Post by raxso on 2007-12-02
After you login open terminal and type the following:

sudo gedit /etc/modules. Add the following line, then save:
apm power_off=1

then type 

sudo shutdown - r now (---- to reboot)

or 

sudo shutdown -h now (---- to shutdown completely)

---

