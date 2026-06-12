---
title: "Unity GUI not loading on bootup"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by pras8421 on 2012-12-23
Hi, . . .

I have upgraded Ubuntu 12.04 to 12.10 as 12.10 has newly been released. I installed compiz-config-settings-manager later.

Once I started ccsm, unity got kinda frozen and no GUI was loaded ever after. I tried removing and reinstalling it, but it didn't work :(

I removed now, unity and ccsm completely as per the best of my knowledge. I did janitor by Ubuntu-Tweak also.
However, when I type "sudo apt-get install unity" or "sudo apt-get install --reinstall unity" there is an error saying you have held broken packages.

Any suggestions please?

Sorry for my poor English.

Thanks :)

---

### Post by grahammechanical on 2012-12-23
> I removed now, unity and ccsm completely as per the best of my knowledge.

If you removed Unity, as you say, then you do not have a User Interface any more. Unless, you previously installed another User Interface as an alternative. Did you?

You can try

```
sudo apt-get install ubuntu-desktop
```

to re-install the complete Ubuntu User Interface including Unity

and/or

```
sudo apt-get -f install
```

to fix broken packages.

Regards.

---

### Post by pras8421 on 2012-12-23
I got this when I tried to install ubuntu-desktop using the first command

[sudo] password for prasanna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-desktop : Depends: unity but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by GameX2 on 2012-12-23
I had a similar problem about a conflict with Unity and CCSM/Compiz.  Unity failed to load and I got multiple terminal errors.

I doubt that will work, but have you tried:

```
unity --reset
```

If you say you have removed Unity, probably that wouldn't work, but you might want to give it a try anyways.

Good luck.

---

### Post by pras8421 on 2012-12-23
To run the "unity --reset", I don't first have unity installed. I'm struggling to install it.

Moreover, I know that "unity --reset" and "unity --replace" don't work in 12.10. You get a message saying the command has been depricated.

---

### Post by pras8421 on 2012-12-24
I could solve the problem with the following command

sudo aptitude install unity

Hope this works. Though you can't get all the effects, you can have a 2d- unity :)

Thanks :)

---

