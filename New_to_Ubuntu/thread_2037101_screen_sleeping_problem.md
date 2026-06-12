---
title: "screen sleeping problem"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by mick_86 on 2012-08-03
i've just installed 12.04 and having a problem when the screen sleeps. when i leave the laptop running and the screen sleeps it disconects from the internet and when i unlock the screen to get back in it is trying to connect to every wifi signal it can find. the popup box asking for a password won't close no matter what way i try and the only way i can use my laptop again is by restarting! could someone tell me how to make sure that my laptop stays connected when the screen sleeps?

---

### Post by cogier on 2012-08-03
Have you setup your computer to boot up without the need to enter a password?

You could try right clicking on the Wireless icon, select settings>Wireless and select your Wireless name. In the options section "Check" of "Tick" the box marked "Available to all users". You may be asked for your password - Enter if necessary.

Another dialogue box may also appear asking for a password. If you are booting up without having to enter a password and you do not want this box requesting a password every time do not put anything in it - Press [OK] and when it asks if you want to use this in unsafe mode click [OK].

I hope that helps.

---

### Post by mick_86 on 2012-08-03
> **cogier said:**
> Have you setup your computer to boot up without the need to enter a password?

You could try right clicking on the Wireless icon, select settings>Wireless and select your Wireless name. In the options section "Check" of "Tick" the box marked "Available to all users". You may be asked for your password - Enter if necessary.

Another dialogue box may also appear asking for a password. If you are booting up without having to enter a password and you do not want this box requesting a password every time do not put anything in it - Press [OK] and when it asks if you want to use this in unsafe mode click [OK].

I hope that helps.

 i do not require a password and when i went to those options "available to all users" was already checked!

---

### Post by matt_symes on 2012-08-03
Hi

It sounds like your laptop is suspending not just the screen blanking, hence the disconnection from the network.

Select the network manager applet->Edit connections. 

Select your preferred wireless network and ensure "connect automatically" is selected.

Select the other networks and ensure "connect automatically" is not selected.

That should just connect to your favourite network when surrounded by known networks. 

Does this help ?

Kind regards

---

### Post by mick_86 on 2012-08-03
> **matt_symes said:**
> Hi

It sounds like your laptop is suspending not just the screen blanking, hence the disconnection from the network.

Select the network manager applet->Edit connections. 

Select your preferred wireless network and ensure "connect automatically" is selected.

Select the other networks and ensure "connect automatically" is not selected.

That should just connect to your favourite network when surrounded by known networks. 

Does this help ?

Kind regards

thanks for the reply, yeah that's helped as it had other connections marked as connect automatically. but is there any way to stop it disconnecting at all? I like to leave my laptop on overnight for downloading and at the moment I'm not getting much downloading done!

---

