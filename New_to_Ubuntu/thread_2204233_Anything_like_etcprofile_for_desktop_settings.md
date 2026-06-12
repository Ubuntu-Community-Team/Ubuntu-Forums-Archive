---
title: "Anything like /etc/profile for desktop settings?"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by getut2 on 2014-02-07
I am already aware of /etc/skel and use it, but I need something like /etc/profile that takes effect for users that have already signed in the first time that can push desktop settings, shortcuts, or other folders and files and enforce that they are there.

Is there anything like that or will I have to script and iterate through every already created user account?

---

### Post by theDaveTheRave on 2014-02-07
If they are standard things you could probably put them into the various relevent hidden directories for setup

so if everyone uses nautilus, and you have a set of preconfigures network drives they will always show up with the same name by setting the config in the
```

./nautilus

```
directory under the users home.

I suspect however that it will be neccessary to script it as part of your 
```

createNewUser.sh

```

You should also be able to use it to create the required menu items for the default software etc (which is what I often consider it for). Although I often don't bother as my users need the majority of the software that comes as standard.

I'm sure that there are other solutions though.

It's all going to come down to if you are setting up a new desktop for a new user (and adding that user to all the systems at the same time). In which case you may decide that you need to create your own distro image.

---

### Post by getut2 on 2014-02-07
Thanks for the reply.

I think that could work but I was looking for a quicker way because specifically this is a multi user RDP host and I need a quick all at once way to do something to ALL user profiles for users that have already had accounts and home folders created for a long time. Things like pushing and enforcing a program shortcut on everyones desktop and having it come back if deleted, or enforcing Firefox settings even if they are already set differently. Those types of things.

---

### Post by theDaveTheRave on 2014-02-07
So if I understand what you are after....

something like the idea of the htaccess file for the apache web server, where each 'site' on a server can have dedicated settings.

using your example of changing a setting in firefox.

You going to have to find a way of reading each users settings and 'overiding' thier preferences, if required, but leaving all the rest intact.
Unfortunately you are going to have to attach that problem on a software by software basis. I'm sure you'll be able to do, but I suspect that your work will be cut out for you. The main problem will be to ensure that if a user modifies an option that the option doesn't stay put (it will probably work during the current session though).

That said...

Sounds to me like you want to have a form of thin client set up, but with the advantages of each user having a localy installed os and hardware. so the config files will be read only.

---

