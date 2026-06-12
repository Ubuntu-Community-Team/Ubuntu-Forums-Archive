---
title: "autologin with lighdm/V16.04"
date: 2017-09-29
forum: New to Ubuntu
---

### Post by saeed-saeb on 2017-09-29
Hi everyone

i installed a minimal ISO of Ubuntu 16.04 (54 MG) on my virtual machine . after done installing the OS , i installed these programs :
```
open-box
lightdm
Qt
dokey
and some related libraries like libgl1
```
everything works fine but when i did try to do the auto login ,i got stuck 

. i have read many forums and watched a lot of videos,consequently found ways but none of them seems to work for me .
the one which i'm eager to work with is lightdm.conf file :
```
sudo nano /etc/lightdm/lightdm.conf
```
in the file first thing i did was to delete the guess and it worked fine but the rest of the code dose not work at all
i double checked my username using "whoami"
```
[SeatDefaults] 
allow-guest=false
autologin-user=saeed
autologin-user-timeout=0
user-session=ubuntu
```
since i am not using unity i did not write(but i did try the code before) this code:
```
greeter-session=unity-greeter
```
saeed is my only user now , however i did try making another and do the auto login with it, but the result was unsatisfying.
it's been around 12 hours of searching and trying ,it seems that everybody are getting the result by above method ,but i keep getting the login screen ,i am afraid i might be short on some LIB or something .
since i am working on an embedded device(Intel based CPU,not ARM) it is crucial to get rid of the login in the main device(server) for the user behind LCD, nevertheless i do need the password for SSH connections security .
your help is appreciated in advance

---

### Post by deadflowr on 2017-09-29
> since i am not using unity i did not write(but i did try the code before) this code:
You didn't install ubuntu-desktop either, so change user session to whatever the openbox session is.
Try looking in /usr/share/xsessions for the session names.

---

### Post by saeed-saeb on 2017-09-29
Thank you for your reply

I did get ls from xsessions ,These are 2 desktops i have

```

openbox.desktop
openbox-gnome.desktop

```
using the login screen , i always go with openbox not openbox-gnome
i tried these codes but none worked 
code 1:
```

[SeatDefaults]
allow-guest=false
autologin-user=saeed
autologin-user-timeout=0
user-session=openbox.desktop

```
code 2:
```

[SeatDefaults]
allow-guest=false
autologin-user=saeed
autologin-user-timeout=0
user-session=openbox

```
code 3:
```

[SeatDefaults]
allow-guest=false
autologin-user=saeed
autologin-user-timeout=0
user-session=openbox-gnome.desktop

```
code 4:
```

[SeatDefaults]
allow-guest=false
autologin-user=saeed
autologin-user-timeout=0
user-session=openbox-gnome

```

I'm still getting login screen

---

### Post by deadflowr on 2017-09-29
Try looking at what Name= says for the openbox.desktop
```
grep Name /usr/share/xsessions/openbox.desktop
```
It's probably Openbox, with a capital.

---

### Post by saeed-saeb on 2017-09-29
grab the name :
```
Name=Openbox
```
didn't work 
```
user-session=Openbox
```
the Gnome/openbox name:
```
Name=GNOME/Openbox
user-session=GNOME/Openbox
```
didn't work too
here is an image you might find something that i didn't got:

[IMG]http://www.mediafire.com/convkey/b30a/96biii1893jpbt6zg.jpg[/IMG]

[IMG]http://www.mediafire.com/convkey/daa4/kljik5ve9dc1psvzg.jpg[/IMG]

I do have an fully desktop Ubuntu on another VM . I am gonna test this on that


[B]EDIT: I did test this method on an Ubuntu , didn't work there too,even the guest session which was working on minimal dose not work on full ubuntu . it seems it dose not use lightmd


EDIT 2: ok i didi change SeatDefault to [Seaat:*] and give delay 1 and delete the user session 
now the login screen is ***** . every second it crashes and resets a gain . so i can not even open the terminal using alt+ctrl+f1 . i think i have to start all over again . i wish i did get some backup . this is really annoying


EDIT 3: ok i did replace lightdm with slim
the problem now [/B]**is **[B]that in login screen slim can't recognize openbox 
i have to push F1 once so that "session : openbox" text appear on the screen otherwise i get fail and slim will reset no matter how many times i try, base on what i said the auto-login will fail , how can i make the openbox my default session for slim ? i have seen some videos in youtube , it seems that slim can recognize openbox in full version ubuntu [/B]

---

### Post by again? on 2017-09-30
In my 16.04 install, if I set autologin in user accounts, the resulting /etc/lightdm/lightdm.conf file looks like...
```
**[Seat:*]**
autologin-user=glen
```

Don't think it's necessary to set the user-session or an autologin delay if not actually using a delay.
Note the heading... **[Seat:*]**
[https://wiki.archlinux.org/index.php/LightDM#Enabling_autologin](https://wiki.archlinux.org/index.php/LightDM#Enabling_autologin)

---

